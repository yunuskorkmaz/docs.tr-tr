---
title: Tanımlama grubu türleri - C# Kılavuzu
description: C# adsız ve adlandırılmış bir tanımlama grubu türleri hakkında bilgi edinin
ms.date: 05/15/2018
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
ms.openlocfilehash: b0c838791e640c9813005b8a32d009153a794c14
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404320"
---
# <a name="c-tuple-types"></a>C# demet türleri #

C# diziler basit bir söz dizimi kullanılarak tanımladığınız türleridir. Avantajları, daha basit bir sözdizimi, dönüştürmeleri (kardinalite adlandırılır) sayısını ve türlerini öğeleri ve tutarlı kuralları kopyalar, eşitlik testleri ve atamaları göre kurallarını içerir. Bir tradeoff diziler bazı devralma ile ilişkili nesne yönelimli deyimlerini desteklemez. Bir genel bakış bölümünde alma [C# 7.0 yenilikleri içindeki diziler](whats-new/csharp-7.md#tuples) makalesi.

Bu makalede, C# 7.0 ve üzeri sürümler tanımlama grupları ile çalışma hakkında onlara ve Başlangıç Kılavuzu kullanmak için farklı yollar diziler dil kuralları öğreneceksiniz.

> [!NOTE]
> Yeni diziler işlevleri <xref:System.ValueTuple> türleri.
> NuGet paketini eklemeniz gerekir [ `System.ValueTuple` ](https://www.nuget.org/packages/System.ValueTuple/) türlerini içermez platformlarda kullanmak için.
>
> Bu çerçevede teslim türleri kullanan diğer dil özellikleri benzer. Örnekler `async` ve `await` güvenmek `INotifyCompletion` arabirimi ve bağlı LINQ `IEnumerable<T>`. Ancak, .NET, daha fazla platform bağımsız olma gibi teslim mekanizması değişiyor. .NET Framework her zaman aynı temposu dil derleyicisi olarak yükleyeceğiniz değil. Yeni dil özellikleri üzerinde yeni türler kullanan, dil başlayamıyorsunuz türlerine NuGet paketleri olarak kullanılabilir. Bu yeni türleri ve .NET standart API için eklenen framework'ün bir parçası olarak sunulan NuGet paketini gereksinim kaldırılacak.

Yeni bir tanımlama grubu desteği ekleme nedenleri başlayalım. Yöntemler, tek bir nesne döndürür. Diziler, daha kolay, tek bir nesnede birden çok değer paketi sağlar.

.NET Framework genel zaten `Tuple` sınıfları. Bu sınıfların ancak iki önemli sınırlamalarını vardı. Biri, `Tuple` sınıflar adlandırılan özelliklerini `Item1`, `Item2`ve benzeri. Bu adları anlamsal bilgi taşır. Bunları kullanarak `Tuple` türleri özelliklerin her birini anlamını iletişim sağlamaz. Yeni dil özellikleri bildirme ve bir grup içinde öğeler için anlamsal olarak anlamlı adlar kullanın olanak sağlar.

`Tuple` Sınıfları neden daha fazla performans endişelerini çünkü bunlar başvuru türleri. Aşağıdakilerden birini kullanarak `Tuple` türleri nesneleri ayırma anlamına gelir. Etkin yolları üzerinde çok sayıda küçük nesne ayırma, uygulamanızın performans üzerinde ölçülebilir bir etkisi olabilir. Bu nedenle, diziler için dil desteği yeni yararlanır `ValueTuple` yapılar.

Bu eksiklikleri önlemek için aşağıdakileri oluşturabilirsiniz bir `class` veya `struct` birden çok öğe yürütmek için. Ne yazık ki sizin için daha fazla iş olduğunu ve tasarım amacınızla gizler. Yapmadan bir `struct` veya `class` hem verileri hem de davranışı ile bir tür tanımlama anlamına gelir. Çoğu zaman, yalnızca birden çok değeri tek bir nesnede depolamak istediğiniz.

Dil özellikleri ve `ValueTuple` genel yapılar bu demet türleri için herhangi bir davranış (yöntem) ekleyemezsiniz kuralı uygular.
Tüm `ValueTuple` türleridir *değişebilir yapılar*. Her üye alan genel bir alandır. Bunları çok basit hale getirir. Ancak, diziler, değiştirilemezlik önemli olduğu kullanılmamalıdır anlamına gelir.

Diziler, hem daha basit ve daha esnek veri kapsayıcılardır daha `class` ve `struct` türleri. Bu farklar araştıralım.

## <a name="named-and-unnamed-tuples"></a>Adlandırılmış ve adlandırılmamış diziler

`ValueTuple` Yapı sahip alanları adlı `Item1`, `Item2`, `Item3`ve benzeri varolan tanımlanan özelliklere benzer `Tuple` türleri.
Bu adlar için kullanabileceğiniz adlar şunlardır *diziler adlandırılmamış*. Bir demet için herhangi bir diğer alan adı belirtmezseniz, adlandırılmamış bir tanımlama grubu oluşturdunuz:

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#01_UnNamedTuple "Unnamed tuple")]

Önceki örnekte demet sabit değeri sabitler kullanılarak başlatıldı ve öğe adları kullanılarak oluşturulan sahip olmaz *demet alan adı projeksiyonlar* C# 7.1 içinde.

Ancak, bir tanımlama grubu başlattığınızda her alan için daha iyi adlar vermek yeni dil özelliklerini kullanabilirsiniz. Bunun yapılması oluşturur bir *demet adlı*.
Adlandırılmış diziler adlı öğe çözümlenmedi `Item1`, `Item2`, `Item3` ve benzeri.
Ancak herhangi biri söz konusu öğelerin adlı için eş anlamlı sözcükler de sahiptir.
Adlandırılmış bir tanımlama grubu, her öğe için bir ad belirterek oluşturun. Dizi başlatma bir parçası olarak adlarını belirtin bir yoludur:

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#02_NamedTuple "Named tuple")]

Bu eş anlamlıların derleyici tarafından işlenir ve dil etkili bir şekilde adlandırılmış'u diziler böylece kullanabilirsiniz. Roslyn API'leri kullanılarak bu anlamsal adları IDE'ler ve düzenleyicilerden okuyabilirsiniz. Adlandırılmış bir tanımlama grubu öğelerinin aynı derlemenin başka bir yerindeki bu anlamsal adlarıyla başvurabilirsiniz. Derleyici ile tanımladığınız adlarını değiştirir `Item*` derlenen Çıkışta oluştururken eşdeğerleri. Derlenmiş Microsoft Ara dil (MSIL) bu öğeleri tanıdığımıza adları içermez.

C# 7.1 ile başlayarak, alan adları bir demet için demet başlatmak için kullanılan değişkenleri sağlanabilir. Bu olarak adlandırılır  **[demet projeksiyon başlatıcılar](#tuple-projection-initializers)**. Aşağıdaki kod adlı bir kayıt düzeni oluşturur `accumulation` öğelerle `count` (tamsayı), ve `sum` (çift).

[!code-csharp[ProjectedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectedTupleNames "Named tuple")]

Derleyici, genel yöntemleri veya özellikleri döndürülen diziler için oluşturulan bu adları iletişim kurması gerekir. Bu gibi durumlarda, derleyicinin ekler bir <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> yöntemi özniteliği. Bu öznitelik içeren bir <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> dizideki öğelerin her biri için verilen adları içeren özellik listesi.

> [!NOTE]
> Visual Studio gibi geliştirme araçları da bu meta verileri okuyun ve IntelliSense ve meta verileri alan adları kullanarak diğer özellikleri sağlar.

Bu yeni diziler temelleri temel anlamak önemlidir ve `ValueTuple` atama kurallarını anlamak için türü adlı birbirine tanımlama grubu.

## <a name="tuple-projection-initializers"></a>Tanımlama grubu projeksiyon başlatıcıları

Genel olarak, bir dizi başlatma ifadesinin sağ tarafı değişken veya alan adları kullanarak demet projeksiyon başlatıcılar çalışır.
Açık bir ad belirtilmezse, öngörülen herhangi bir ad öncelik kazanır. Örneğin, aşağıdaki başlatıcısında öğeleridir `explicitFieldOne` ve `explicitFieldTwo`değil `localVariableOne` ve `localVariableTwo`:

[!code-csharp[ExplicitNamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectionExample_Explicit "Explicitly named tuple")]

Burada açık bir ad sağlanmazsa herhangi bir alan için geçerli bir örtük adı yansıtılır. Anlam adları açıkça veya örtülü olarak sağlamak için bir gereksinim değildir. Aşağıdaki Başlatıcı alan adlarını sahip `Item1`, değeri olan `42` ve `stringContent`, "Her şey için yanıt" değeri olan:

[!code-csharp[MixedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#MixedTuple "mixed tuple")]

Burada aday alan adları demet alan yansıtılan değil iki koşul vardır:

1. Aday adı ayrılmış demet adını olduğunda. Örnekler `Item3`, `ToString`. veya `Rest`.
1. Ne zaman aday adı açık veya örtülü başka bir tanımlama grubu alan adı yineleniyor.

Bu koşullar belirsizlik kaçının. Bu adlar, tanımlama grubu alanın alan adları olarak kullanıldıysa belirsizliğe neden olur. Bu koşulların hiçbiri, derleme zamanı hatalarına neden. Bunun yerine, öğeler olmadan öngörülen adları bunlar için öngörülen anlam adları yok.  Aşağıdaki örnekler, bu koşullar göstermektedir:

[!code-csharp[Ambiguity](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectionAmbiguities "tuples where projections are not performed")]

Bu durumlarda, bir dizi alan adı projeksiyonlar kullanılabilir değil, C# 7.0 ile yazılan kod için değişiklik olacağından derleyici hataları neden olmaz.

## <a name="equality-and-tuples"></a>Eşitlik ve diziler

C# 7.3 ile başlayarak, tanımlama grubu türleri desteği `==` ve `!=` işleçleri. Bu işleçler sırayla sağ bağımsız değişkeni her üyesi sol bağımsız değişkeni her üyesi karşılaştırarak çalışır. Bu karşılaştırmalar kısa devre oluşturur. `==` İşleci durdurur üyeleri bir çifti eşit değil olarak değerlendiriliyor. `!=` İşleci durdurur üyeleri bir çifti eşit olarak değerlendiriliyor. Aşağıdaki kod örnekleri kullan `==`, ancak tüm uygulamak için karşılaştırma kurallarını `!=`. Aşağıdaki kod örneği, iki tamsayı çiftleri için bir eşitlik karşılaştırması gösterir:

[!code-csharp[TupleEquality](../../samples/snippets/csharp/tuples/tuples/program.cs#Equality "Testing tuples for equality")]

Tanımlama grubu eşitliği testleri daha kullanışlı hale çeşitli kurallar vardır. Tanımlama grubu eşitliği gerçekleştirir [dönüştürmeler yükseltilmiş](language-reference/language-specification/index.md) diziler biri aşağıdaki kodda gösterildiği gibi boş değer atanabilir bir tanımlama grubu ise:


[!code-csharp[NullableTupleEquality](../../samples/snippets/csharp/tuples/tuples/program.cs#NullableEquality "Comparing Tuples and nullable tuples")]

Tanımlama grubu eşitliği, ayrıca hem de tanımlama gruplarının her üye üzerinde örtük dönüştürmeleri gerçekleştirir. Bunlar, dönüştürme, yükseltilmiş dönüştürmeler ve diğer örtük dönüştürmeleri genişletme içerir. Aşağıdaki örnekler bir tamsayı 2 bölütlü uzun bir 2-demet tamsayıya örtülü dönüştürme nedeniyle karşılaştırılabilir uzun:

[!code-csharp[SnippetMemberConversions](../../samples/snippets/csharp/tuples/tuples/program.cs#SnippetMemberConversions "converting tuples for equality tests")]

Tanımlama grubu üyelerinin adları eşitliği testleri katılmaz. Ancak, biri açık adlar ile sabit tanımlama grubu ise, bu adlar diğer işlenen adları eşleşmiyorsa derleyici uyarı CS8383 oluşturur.
Her iki işlenen demet sabit olduğu durumda, uyarıyı sağ işlenen üzerinde aşağıdaki örnekte gösterildiği gibi verilmiştir:

[!code-csharp[MemberNames](../../samples/snippets/csharp/tuples/tuples/program.cs#SnippetMemberNames "Tuple member names do not participate in equality tests")]

Son olarak, diziler, iç içe geçmiş bir tanımlama grubu içerebilir. Tanımlama grubu eşitliği "aşağıdaki örnekte gösterilen şeklini" iç içe geçmiş tanımlama grupları halinde aracılığıyla her işlenen karşılaştırılır:

[!code-csharp[NestedTuples](../../samples/snippets/csharp/tuples/tuples/program.cs#SnippetNestedTuples "Tuples may contain nested tuples that participate in tuple equality.")]

## <a name="assignment-and-tuples"></a>Atama ve diziler

Burada her sağ tarafı öğe örtük karşılık gelen sol tarafı öğesine dönüştürülebilir aynı sayıda öğe olan tanımlama grubu türleri arasında atama dili destekler. Diğer dönüştürme atamalarını kabul edilmez. Tanımlama grubu türleri arasında izin atamaları türlerini bakalım.

Aşağıdaki örneklerde kullanılan bu değişkenleri göz önünde bulundurun:

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/tuples/program.cs#03_VariableCreation "Variable creation")]

İlk iki değişken `unnamed` ve `anonymous` olmayan öğeler için sağlanan anlam adlarına sahip. Alan adları `Item1` ve `Item2`.
Son iki değişken `named` ve `differentName` öğeleri için verilen anlam adlarına sahip. Bu iki diziler öğeler için farklı adlara sahip.

Dört bu tanımlama grubu aynı sayıda öğe ('önem' adlandırılır) varsa ve söz konusu öğelerin türleri aynı. Bu nedenle, tüm bu atamaları çalışır:

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/tuples/program.cs#04_VariableAssignment "Variable assignment")]

Tanımlama grubu adlarını atanmamış dikkat edin. Dizideki öğelerin sırasını aşağıdaki öğelerin değerlerinin atanır.

Farklı türler veya öğeleri sayıda tanımlama atanabilir değil:

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a>Yöntemin dönüş değeri olarak diziler

Demetler en yaygın kullanımlarından biri, yöntemi dönüş değeridir. Bir örnek atalım. Bir sayı dizisi üzerinde için standart sapmayı hesaplar. Bu yöntem göz önünde bulundurun:

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/tuples/statistics.cs#05_StandardDeviation "Compute Standard Deviation")]

> [!NOTE]
> Bu örnekler düzeltilemeyen örnek standart sapma hesaplaması.
> Düzeltilmiş örnek standart sapma formülü (N-1) tarafından N yerine mean squared fark toplamı olarak çizilmesini sağlıyordu `Average` uzantı yöntemi yapar. Standart sapma bu formülleri arasındaki farklar hakkında daha fazla ayrıntı için istatistikleri metin başvurun.

Yukarıdaki kod Ders Kitabı standart sapma formülü aşağıdadır. Doğru yanıtı oluşturur, ancak bu verimsiz bir uygulaması. Bu yöntem dizisi iki kez numaralandırır: ortalama üretmek için bir kez ve ortalama farkı karesini ortalamasını üretmek için bir kez.
(Ortalama fark hesaplama ve bu farklar ortalaması yalnızca bir sabit listesi yapsak LINQ sorguları gevşek, değerlendirildiğini unutmayın.)

Standart sapma yalnızca bir sabit listesi sırası kullanarak hesaplar alternatif bir formül yoktur.  Sıralı listeler gibi bu hesaplama iki değer üretir: dizisindeki tüm öğelerin toplamının yanı sıra, her bir değerin toplamını kare:

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/tuples/statistics.cs#06_SumOfSquaresFormula "Compute Standard Deviation using the sum of squares")]

Bu sürümü tam bir kez sırasını numaralandırır. Ancak, yeniden kullanılabilir kod değil. Çalışmaya devam gibi birçok farklı istatistiksel hesaplamalar öğe dizisi, dizinin toplamı ve dizinin kareler toplamı kullanmak bulabilirsiniz. Şimdi bu yöntem yeniden düzenleyin ve üçünü de bu değerleri üreten bir yardımcı yöntemi yazın. Bir tanımlama grubu olarak, tüm üç değer döndürülebilir.

Numaralandırma sırasında hesaplanan üç değerden bir grup içinde depolanır. böylece bu yöntem güncelleştirelim. Bu sürümü oluşturan:

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#07_TupleVersion "Refactor to use tuples")]

Visual Studio'nun yeniden düzenleme desteği, özel bir yöntem işlevselliği temel istatistikleri için ayıklamak üzere kolaylaştırır. Size bir `private static` demet türü ile üç değerden döndüren yöntem `Sum`, `SumOfSquares`, ve `Count`:

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#08_TupleMethodVersion "After extracting utility method")]
 
Birkaç hızlı düzenlemeler el ile yapmak istiyorsanız dil kullanabilirsiniz, daha fazla birkaç seçeneği sağlar. İlk olarak kullanabileceğiniz `var` demet sonuçtan başlatmak için bildirimi `ComputeSumAndSumOfSquares` yöntem çağrısı. İçinde üç ayrık değişkeni de oluşturabilirsiniz `ComputeSumAndSumOfSquares` yöntemi. Son sürümü, aşağıdaki kodda gösterilmiştir:

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#09_CleanedTupleVersion "After final cleanup")]

Bu son sürümü, üç değerlerin veya bunların herhangi bir alt gereken herhangi bir yöntem için kullanılabilir.

Dil, bu kayıt döndüren yöntemler öğelerin adlarını yönetilmesindeki diğer seçeneklerini destekler.

Dönüş değeri bildirimden alan adlarını kaldırın ve adlandırılmamış bir tanımlama grubu döndürür:

```csharp
private static (double, double, int) ComputeSumAndSumOfSquares(IEnumerable<double> sequence)
{
    double sum = 0;
    double sumOfSquares = 0;
    int count = 0;

    foreach (var item in sequence)
    {
        count++;
        sum += item;
        sumOfSquares += item * item;
    }

    return (sum, sumOfSquares, count);
}
```

Bu dizi alanları adlı `Item1`, `Item2`, ve `Item3`.
Anlam yöntemlerinden döndürülen tanımlama grubu öğelerinin adlarını sağlamanız önerilir.

Başka bir deyim burada diziler yararlı olabilir, LINQ sorguları geliştirmekte olduğunuz durumdur. Öngörülen sonucunu bazı, tümü değil, genellikle seçili nesnelerin özelliklerini içerir.

Geleneksel olarak anonim bir tür olan nesneleri dizisine sorgunun sonuçlarının proje. Öncelikle anonim türler rahatça dönüş türünü bir yöntem için adlandırılabilir değildir çünkü, çok sayıda sınırlamaya sunulur. Kullanarak alternatifleri `object` veya `dynamic` sonuç türü önemli performans maliyetleri ile birlikte gelen gibi.

Bir demet dizisi döndürme türü kolaydır ve adlarını ve türlerini öğelerin derleme zamanında ve IDE araçları aracılığıyla kullanılabilir.
Örneğin, bir ToDo uygulaması göz önünde bulundurun. Yapılacaklar listesindeki tek bir giriş temsil etmek için aşağıdakine benzer bir sınıf tanımlayabilir:

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#14_ToDoItem "To Do Item")]

Mobil uygulamalarınızı, yalnızca bir başlık görüntüler compact geçerli Yapılacaklar öğelerine biçiminin destekleyebilir. LINQ sorgusu bir projeksiyon, yapacağınız, yalnızca ID ve başlık içerir. Diziler bir dizi döndüren bir yöntem de bu tasarım ifade eder:

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#15_QueryReturningTuple "Query returning a tuple")]

> [!NOTE]
> C# 7.1, demet projeksiyonlar adlandırılmış diziler özellik adlarının anonim türleri benzer bir şekilde öğelerini kullanarak oluşturmanızı sağlar. Yukarıdaki kodda, `select` sorgu projeksiyon deyiminde öğeleri olan tanımlama grubu oluşturur `ID` ve `Title`.

Adlandırılmış demet imzasının bir parçası olabilir. Derleyici sağlar ve IDE araçları statik sonucu doğru kullanıyorsanız denetimi sağlar. Sonuçları ile çalışmak için pahalı çalışma zamanı özellikleri yansıma veya dinamik bağlama gibi kullanılması gerekmez bu nedenle adlandırılmış demet ayrıca statik tür bilgilerini taşır.

## <a name="deconstruction"></a>Ayrıştırma

Tarafından bir tanımlama grubu içindeki tüm öğeler Sunu paketini *ayrıştırma* yöntemi tarafından döndürülen dizi. Diziler ayrıştırma için üç farklı yaklaşım vardır.  İlk olarak, dizideki öğelerin her biri için ayrık değişkenlerinin parantez içinde her alanın türünü açıkça bildirebilirsiniz:

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/tuples/statistics.cs#10_Deconstruct "Deconstruct")]

Kullanarak bir tanımlama grubu içindeki her alan için örtük olarak yazılan değişkenleri bildirebilirsiniz `var` anahtar sözcüğü parantezler dışında:

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/tuples/statistics.cs#11_DeconstructToVar "Deconstruct to Var")]

Kullanılacak yasaldır `var` anahtar sözcüğü, bir bölümünü veya tamamını parantez içinde değişken bildirimleri ile. 

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```

Dizideki her alan aynı türde olsa bile, belirli bir tür parantez dışında kullanamazsınız.

Varolan bildirimler ile tanımlama grubu Ayrıştır:

```csharp
public class Point
{
    public int X { get; set; }
    public int Y { get; set; }

    public Point(int x, int y) => (X, Y) = (x, y);
}
```

> [!WARNING]
>  Varolan bildirimler bildirimi parantez içinde ile karıştırılamaz. Örneğin, aşağıdaki izin verilmiyor: `(var x, y) = MyMethod();`. Bu hata CS8184 çünkü oluşturur *x* parantez içinde bildirilir ve *y* daha önce başka bir yerde bildirilmiş.

### <a name="deconstructing-user-defined-types"></a>Kullanıcı tanımlı türleri ayrıştırma

Yukarıda da gösterildiği gibi herhangi bir demet türü ayrıştırılabilir. Ayrıştırma (sınıflar, yapılar veya hatta arabirimleri) kullanıcı tanımlı tür üzerinde etkinleştirmek çok kolaydır.

Türü yazarı, bir veya daha fazla tanımlayabilirsiniz `Deconstruct` dilediğiniz sayıda atayabilmeniz yöntemleri `out` türünü oluşturan veri öğelerini temsil eden değişken. Örneğin, aşağıdaki `Person` türünü tanımlayan bir `Deconstruct` ad ve soyadı temsil eden öğeyi bir kişi nesnesinin deconstructs yöntemi:

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#12_TypeWithDeconstructMethod "Type with a deconstruct method")]

Atamadan deconstruct yöntemi sağlayan bir `Person` temsil eden iki dizelere `FirstName` ve `LastName` özellikleri:

[!code-csharp[Deconstruct Type](../../samples/snippets/csharp/tuples/tuples/program.cs#12A_DeconstructType "Deconstruct a class type")]

Ayrıştırma deyiminin bile değil Yazar türleri için etkinleştirebilirsiniz.
`Deconstruct` Yöntemi, bir nesnenin erişilebilir veri üyelerine tutucusu paketten çıkarır bir genişletme yöntemi olabilir. Gösterir aşağıdaki örnekte bir `Student` türetilen tür, `Person` türü ve deconstructs bir genişletme yöntemi bir `Student` temsil eden üç değişkenin içine `FirstName`, `LastName`ve `GPA`:

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#13_ExtensionDeconstructMethod "Type with a deconstruct extension method")]

A `Student` nesne artık sahip iki erişilebilir `Deconstruct` yöntemleri: genişletme yöntemi için bildirilen `Student` türleri ve üyesi `Person` türü. Her ikisi de kapsamındaki ve sağlayan bir `Student` iki değişkeni veya üç deconstructed için.
Bir öğrenci üç değişkenlere atarsanız, tüm ad son adı ve GPA döndürdü. İki değişken için bir öğrenci atarsanız, yalnızca ilk adı ve Soyadı döndürülür.

[!code-csharp[Deconstruct extension method](../../samples/snippets/csharp/tuples/tuples/program.cs#13A_DeconstructExtension "Deconstruct a class type using an extension method")]

Birden fazla tanımlama dikkatli olmanız gerekir `Deconstruct` yöntemleri bir sınıf ya da bir sınıf hiyerarşisi. Birden çok `Deconstruct` aynı sayıda içeren yöntemlerin `out` parametreleri hızla belirsizliğe neden olabilir. Çağıranlar kolayca istenen arayabilmesi için olmayabilir `Deconstruct` yöntemi.

Bu örnekte var olduğundan belirsiz bir çağrı için en az bir fırsat `Deconstruct` yöntemi `Person` parametreleri, iki çıkışı vardır ve `Deconstruct` yöntemi `Student` üç.

Ayrıştırma deyiminin işleçleri eşitlik testinde katılamaz. Aşağıdaki örnek, derleyici hatası CS0019 oluşturur:

```csharp
Person p = new Person("Althea", "Goodwin");
if (("Althea", "Goodwin") == p)
    Console.WriteLine(p);
```

`Deconstruct` Yöntemi dönüştürme `Person` nesne `p` bir demet için iki dizeyi, ancak içeren eşitliği testleri bağlamında geçerli değil.

## <a name="conclusion"></a>Sonuç 

Adlandırılmış diziler yeni dil ve kitaplığa desteği sınıfları ve yapıları olduğu gibi birden çok öğe depolamak ancak davranışı tanımlamaz veri yapıları kullanan tasarımlar ile çalışmak çok daha kolay hale getirir. Bu, kolay ve Diziler bu türleri için kullanılacak kısa olur. Statik tür denetimi, türleri daha ayrıntılı kullanarak yazmak zorunda kalmadan tüm avantajlarını elde `class` veya `struct` söz dizimi. Bu halde bile, yardımcı program yöntemleri için en kullanışlı `private`, veya `internal`. Kullanıcı tanımlı türler, ya da oluşturma `class` veya `struct` genel yöntemlerinizi birden çok öğe içeren bir değer döndürmediğinde türleri.
