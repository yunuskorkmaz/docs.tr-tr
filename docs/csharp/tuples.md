---
title: "Diziler - C# Kılavuzu"
description: "C# adsız ve adlandırılmış tanımlama grubu türleri hakkında bilgi edinin"
keywords: .NET, .NET core, C#
author: BillWagner
ms-author: wiwagn
ms.date: 11/23/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
ms.openlocfilehash: 58f76332a8f3717fe10788382552598d6693e7e3
ms.sourcegitcommit: 882e02b086d7cb9c75f748494cf7a8d3377c5874
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2017
---
# <a name="c-tuple-types"></a>C# tanımlama grubu türleri #

C# diziler basit bir söz dizimi kullanılarak tanımlayan türleridir. Avantajlar kuralları (kardinalite adlandırılır) sayısı ve türleri öğeleri ve kopyalar ve atamaları için tutarlı kurallarını temel dönüştürmeleri için daha basit bir sözdizimi vardır. Bir kolaylığını diziler devralma ile ilişkili nesne yönelimli deyimleri bazıları desteklemez. Bir genel bakış bölümünde alma [C# 7'de yenilikler içindeki diziler](whats-new/csharp-7.md#tuples) konu.

Bu konuda, C# 7, tanımlama grupları ile çalışma hakkında onları ve Başlangıç Kılavuzu kullanmak için farklı yollar diziler yöneten dil kurallarına öğreneceksiniz.

> [!NOTE]
> Yeni diziler işlevleri <xref:System.ValueTuple> türleri.
> NuGet paketini eklemeniz gerekir [ `System.ValueTuple` ](https://www.nuget.org/packages/System.ValueTuple/) türleri dahil etmeyin platformlarda kullanmak için.
>
> Bu framework teslim türlerine dayanan diğer dil özellikleri benzer. Örnekler `async` ve `await` güvenmek `INotifyCompletion` arabirimi ve güvenmek LINQ `IEnumerable<T>`. Ancak, daha fazla platform bağımsız .NET olma gibi teslim mekanizması değiştiriyor. .NET Framework her zaman aynı tempoyla dil derleyici olarak yükleyeceğiniz değil. Yeni dil özellikleri yeni türlerinde kullanır, dil özellikleri sevk ettiğinizde bu türlerde NuGet paketleri olarak kullanılabilir. Bu yeni tür .NET standart API'sine eklenir ve framework'ün bir parçası olarak teslim olarak NuGet paketi gereksinimi kaldırılacak.

Yeni tanımlama grubu desteği ekleme nedenleri ile başlayalım tıklatın. Yöntemleri tek bir nesne döndürür. Diziler, söz konusu tek nesne birden fazla değer daha kolay paketini olanak tanır.

.NET Framework genel zaten `Tuple` sınıfları. Bu sınıfların ancak, iki önemli kısıtlama vardı. Birisi, `Tuple` sınıfları, özellikleri adlı `Item1`, `Item2`ve benzeri. Bu adları yok anlamsal bilgilerin taşır. Bunlar kullanarak `Tuple` türleri özelliklerin her biri anlamını iletişim sağlamaz. Yeni dil özellikleri bildirme ve bir dizi öğelerin anlamsal olarak anlamlı adlarını kullanma olanak sağlar.

Başka bir önemli olan `Tuple` sınıfları başvuru türleridir. Aşağıdakilerden birini kullanarak `Tuple` türleri nesneleri ayırma anlamına gelir. Sık kullanılan yollarına göre bu, uygulamanızın performans üzerinde ölçülebilir bir etkisi olabilir. Bu nedenle, tanımlama grupları için dil desteği yeni yararlanır `ValueTuple` yapılar.

Bu eksiklikler önlemek için oluşturabilirsiniz bir `class` veya `struct` birden çok öğe taşımak için. Ne yazık ki, sizin için daha fazla iş ve tasarım hedefi gizler. Yaparak bir `struct` veya `class` hem veri hem de davranış türüyle tanımlama anlamına gelir. Çoğu zaman, yalnızca birden çok değeri tek bir nesnede depolamak istediğiniz.

Dil özellikleri ve `ValueTuple` genel yapılar bu kayıt türlerinin herhangi davranışları (yöntemleri) ekleyemezsiniz kural zorla.
Tüm `ValueTuple` türleri *değişebilir yapılar*. Her üye alan genel bir alandır. Bunları çok basit hale getirir. Ancak, bu girişi önemli olduğu diziler kullanılmamalıdır anlamına gelir.

Diziler olan hem de daha basit ve daha esnek veri kapsayıcıları daha `class` ve `struct` türleri. Bu farklılıklar inceleyelim.

## <a name="named-and-unnamed-tuples"></a>Adlandırılmış ve adlandırılmamış diziler

`ValueTuple` Yapısı sahip adlı alanları `Item1`, `Item2`, `Item3` ve vb., varolan tanımlanan özellikleri benzer `Tuple` türleri.
Bu adları, için kullanabileceğiniz yalnızca adlarıdır *diziler adlandırılmamış*. Herhangi bir tanımlama grubu alternatif alan adlarını sağlamaz, adsız bir tanımlama grubu oluşturduğunuzu düşünün:

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#01_UnNamedTuple "Unnamed tuple")]

Önceki örnekte yer alan tanımlama grubu değişmez değer sabitleri kullanarak başlatıldı ve öğe adları kullanarak oluşturduğunuz olmaz *tanımlama grubu alan adı tahminleri* C# 7.1 içinde.

Ancak, bir tanımlama grubu başlattığınızda, her bir alan için daha iyi adlar verin yeni dil özellikleri kullanabilirsiniz. Bunun yapılması oluşturur bir *tanımlama grubu adlı*.
Adlandırılmış diziler adlı öğe çözümlenmedi `Item1`, `Item2`, `Item3` ve benzeri.
Ancak aynı zamanda herhangi bu öğelerin adlı için eş anlamlı sözcükleri sahiptirler.
Her öğe için adları belirterek adlandırılmış bir tanımlama grubu oluşturun. Tuple başlatma bir parçası olarak adlarını belirtmek için bir yolu şöyledir:

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#02_NamedTuple "Named tuple")]

Bu eş anlamlıları derleyici tarafından işlenir ve dil etkili bir şekilde adlandırılmış'u diziler böylece kullanabilirsiniz. IDE ve düzenleyiciler Roslyn API'leri kullanılarak bu anlam adları okuyabilir. Bu adlandırılmış bir tanımlama grubu öğelerini bu anlam adlarıyla aynı bütünleştirilmiş kodda başka bir yerindeki başvuru sağlar. Derleyici ile tanımlanan adlar değiştirir `Item*` derlenmiş çıkış oluştururken eşdeğerleri. Derlenmiş Microsoft Ara dili (MSIL) bu öğelerin verdiniz adları içermez.

C# 7.1 ile başlayarak, bir tanımlama grubu için alan adlarını alan tanımlama grubu başlatmak için kullanılan değişkenler arasından sağlanabilir. Bu olarak adlandırılır  **[tanımlama grubu projeksiyon başlatıcıları](#tuple-projection-initializers)**. Aşağıdaki kod adlı bir tanımlama grubu oluşturur `accumulation` öğelerle `count` (tamsayı) ve `sum` (bir double).

[!code-csharp[ProjectedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectedTupleNames "Named tuple")]

Derleyici ortak yöntemleri ya da özellikleri döndürülen diziler için oluşturulan bu adlar iletişim kurması gerekir. Bu gibi durumlarda derleyici ekler bir <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> yöntemi özniteliği. Bu öznitelik içeren bir <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> tanımlama grubundaki öğelerin her biri için verilen adlarını içeren özellik listesi.

> [!NOTE]
> Visual Studio gibi geliştirme araçları Ayrıca bu meta verilerini okuma ve IntelliSense meta verileri alan adları kullanarak ve diğer özellikleri sağlar.

Bu yeni başlıklar temelleri temel anlamak önemlidir ve `ValueTuple` atamak için kurallar anlamak için türünün adlı birbirlerine diziler.

## <a name="tuple-projection-initializers"></a>Tuple projeksiyon başlatıcıları

Genel olarak, bir tanımlama grubu başlatma ifadesinin sağ taraftaki değişken veya alan adları kullanarak tanımlama grubu projeksiyon başlatıcıları çalışır.
Açık bir ad belirtilmezse, tüm tahmini adın üzerine önceliklidir. Örneğin, aşağıdaki Başlatıcı öğeleridir `explicitFieldOne` ve `explicitFieldTwo`değil `localVariableOne` ve `localVariableTwo`:

[!code-csharp[ExplicitNamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectionExample_Explicit "Explicitly named tuple")]

Burada açık bir ad sağlanmayan herhangi bir alan için geçerli bir örtük adı yansıtılacak. Anlam adları, açıkça veya örtük sağlamak için gereksinim olduğuna dikkat edin. Aşağıdaki Başlatıcı alan adları olacaktır `Item1`, değeri olan `42` ve `StringContent`, "Her şeyi yanıt" değeri olan:

[!code-csharp[MixedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#MixedTuple "mixed tuple")]

Burada adayı alan adları tanımlama grubu alanın öngörülen olmayan iki koşul vardır:

1. Aday adı ayrılmış bir tanımlama grubu adı olduğunda. Örnekler `Item3`, `ToString` veya `Rest`.
1. Aday adı başka bir tanımlama grubu alan adı, açık veya örtülü tekrarı olduğunda.

Bu koşullar belirsizlik kaçının. Bir tanımlama grubu alanında alan adları olarak kullanıldıysa, bu adları bir belirsizlik neden olur. Bu koşullar neden derleme zamanı hataları hiçbiri. Bunun yerine, tahmini adları olmadan öğeleri kendileri için öngörülen anlamsal adları yok.  Aşağıdaki örnekler, bu koşullar göstermektedir:

[!code-csharp[Ambiguity](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectionAmbiguities "tuples where projections are not performed")]

Bu durumlarda, tanımlama grubu alan adı tahminleri kullanılamıyordu, C# 7.0 ile yazılan kod için önemli bir değişiklik olacağından derleyici hataları neden olmaz.

## <a name="assignment-and-tuples"></a>Atama ve diziler

Dil aynı sayıda öğe olan tanımlama grubu türlerini örtük dönüşümler arasındaki atama türleri için her bu öğeler için destekler. Diğer dönüştürme atamaları dikkate alınmaz. Dizi türleri arasında izin atamalarını türlerini bakalım.

Aşağıdaki örneklerde kullanılan bu değişkenleri göz önünde bulundurun:

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/tuples/program.cs#03_VariableCreation "Variable creation")]

İlk iki değişkenleri `unnamed` ve `anonymous` sahip değil öğeleri için sağlanan anlamsal adları. Alan adları `Item1` ve `Item2`.
Son iki değişken `named` ve `differentName` öğeleri için verilen anlamsal adlara sahip olması. Bu iki başlığın öğeleri için farklı adlar gerektiğini unutmayın.

Bu başlık dört aynı sayıda öğe ('kardinalite' adlandırılır) varsa ve bu öğeleri türlerini aynıdır. Bu nedenle, tüm bu atamaları çalışır:

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/tuples/program.cs#04_VariableAssignment "Variable assignment")]

Diziler adları atanmamıştır dikkat edin. Tanımlama grubundaki öğelerin sırasını aşağıdaki öğelerin değerleri atanır.

Diziler farklı türlerin veya öğeleri sayıda atanabilir değil:

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a>Diziler yöntemi olarak dönüş değerleri

Diziler için en yaygın kullanımları yönteminin dönüş değeri olarak biridir. Şimdi bir örnek yol. Sayılardan oluşan bir dizi standart sapmayı hesaplar bu yöntem göz önünde bulundurun:

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/tuples/statistics.cs#05_StandardDeviation "Compute Standard Deviation")]

> [!NOTE]
> Bu örnekler düzeltilemeyen örnek standart sapma işlem.
> Düzeltilmiş örnek standart sapma formülü (N-1) tarafından N yerine ortalaması arasındaki karesi alınmış farklar toplamı olarak bölmek `Average` genişletme yöntemi yapar. Standart sapma için bu formüller arasındaki farklar hakkında daha fazla ayrıntı için istatistikleri metin başvurun.

Standart sapma Ders Kitabı formülü izler. Doğru yanıt oluşturur, ancak çok verimli bir uygulamasıdır. Bu yöntem dizisi iki kez numaralandırır: ortalama üretmek için bir kez ve ortalama farkı kare ortalaması üretmek için bir kez.
(Yalnızca bir numaralandırma ortalaması arasındaki farklar hesaplama ve bu farklılıkları ortalaması yapar şekilde LINQ sorgularını gevşek, değerlendirildiğini unutmayın.)

Yalnızca bir numaralandırma dizisi kullanarak alarak standart sapmayı hesaplar alternatif bir formül yoktur.  Dizisini numaralandıran gibi iki değerleri bu hesaplama üreten: dizisindeki tüm öğelerin toplamı ve her bir değerin toplamını kare:

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/tuples/statistics.cs#06_SumOfSquaresFormula "Compute Standard Deviation using the sum of squares")]

Bu sürüm dizisi tam olarak bir kez numaralandırır. Ancak, çok yeniden kullanılabilir kodu değil. Çalışmaya devam gibi birçok farklı istatistiksel hesaplamalar sırası, sıra toplamı ve dizisi kareler toplamı öğelerin sayısı kullandığınız bulabilirsiniz. Şimdi bu yöntem yeniden düzenlemeniz ve bu değerlerin üçünü üreten bir yardımcı program yöntemi yazın.

Diziler çok kullanışlı yeri budur. 

Hesaplanan numaralandırma sırasında üç değerden bir tanımlama grubu içinde depolanan şimdi bu yöntem güncelleştirin. Bu sürüm oluşturur:

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#07_TupleVersion "Refactor to use tuples")]

Visual Studio'nun Refactoring destek işlevsellik çekirdek istatistikler için özel bir yöntem ayıklamak kolaylaşır. Gösteren bir `private static` üç değerlerini dizi türüyle döndürür yöntemi `Sum`, `SumOfSquares`, ve `Count`:

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#08_TupleMethodVersion "After extracting utility method")]
 
El ile birkaç Hızlı düzenlemeleri yapmak istiyorsanız dil kullanabilirsiniz, birkaç diğer seçenekler sağlar. İlk olarak, kullanabileceğiniz `var` tanımlama grubu sonucundan başlatmak için bildirimi `ComputeSumAndSumOfSquares` yöntem çağrısı. İçinde üç ayrık değişkenleri oluşturabilirsiniz `ComputeSumAndSumOfSquares` yöntemi. Son sürümü aşağıdadır:

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#09_CleanedTupleVersion "After final cleanup")]

Bu son sürümü bu üç değerleri veya herhangi bir kısmını gereken herhangi bir yöntemi için kullanılabilir.

Dili, bu tanımlama grubu döndüren yöntemler öğeleri adları yönetilmesindeki diğer seçenekleri destekler.

Dönüş değeri bildiriminden alan adlarını kaldırmak ve adsız bir tanımlama grubu döndürür:

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

Bu tanımlama grubu alanlarının adres `Item1`, `Item2`, ve `Item3`.
Yöntemleri iade diziler öğelerine anlamsal adları sağladığınız önerilir.

Başka bir deyim burada diziler çok kullanışlı olabilir, nihai sonucu bazı içeren bir yansıtma olduğu LINQ sorgularını yazarken, ancak seçilmesini nesneleri özelliklerinin tümünü değil ' dir.

Geleneksel olarak anonim bir tür olan nesneler dizisi sorgu sonuçlarını proje. Öncelikle anonim türler rahat dönüş türü için bir yöntem adlandırılabilir değil çünkü, çok sayıda sınırlamaya sunulmuştur. Kullanarak alternatifleri `object` veya `dynamic` sonuç türü ile önemli performans maliyetleri gelen gibi.

Bir tanımlama grubu bir dizi döndürme türü kolaydır ve adlarını ve öğeleri türlerini derleme zamanında ve IDE araçları aracılığıyla kullanılabilir.
Örneğin, bir Yapılacaklar uygulamasının göz önünde bulundurun. Yapılacaklar listesindeki tek bir giriş temsil etmek için aşağıdakine benzer bir sınıf tanımlama:

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#14_ToDoItem "To Do Item")]

Mobil uygulamalarınız başlık yalnızca görüntüleyen bir compact biçiminde geçerli Yapılacaklar öğelerini desteklemiyor olabilir. LINQ Sorgu projeksiyon, yapacağınız, yalnızca kimliği ve başlık içerir. Diziler dizisi döndüren bir yöntem bu tasarımı çok iyi ifade eder:

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#15_QueryReturningTuple "Query returning a tuple")]

> [!NOTE]
> C# içinde 7.1, tanımlama grubu tahminleri özelliği adlandırma anonim türlerinde benzer bir şekilde kullanan öğeler, adlandırılmış diziler oluşturmanızı sağlar. Yukarıdaki kod `select` sorgu projeksiyon deyiminde öğesi içeren bir tanımlama grubu oluşturur `ID` ve `Title`.

Adlandırılmış tanımlama grubu imza parçası olabilir. Derleyici sağlar ve IDE araçları statik sonucu doğru kullanıyorsanız denetimi sağlar. Bu yüzden sonuçlarıyla çalışmaya yansıma ya da dinamik bağlama gibi pahalı çalışma zamanı özellikleri kullanmak için gerekli adlandırılmış tanımlama grubu statik türü bilgileri de taşır.

## <a name="deconstruction"></a>Deconstruction

Bir tanımlama grubu tarafından tüm öğelerde gitmeniz *deconstructing* yöntemi tarafından döndürülen tanımlama grubu. Diziler deconstructing için üç farklı yaklaşım vardır.  İlk olarak, her tanımlama grubu öğeleri ayrık değişkenleri oluşturmak üzere parantez içindeki her bir alan türü açıkça bildirebilirsiniz:

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/tuples/statistics.cs#10_Deconstruct "Deconstruct")]

Kullanarak bir tanımlama grubu içindeki her alan için örtük olarak yazılan değişkenler de bildirebilirsiniz `var` anahtar sözcüğü parantez dışında:

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/tuples/statistics.cs#11_DeconstructToVar "Deconstruct to Var")]

Kullanmak için uygundur `var` , bir bölümünü veya tamamını parantez içinde değişken bildirimleri olan anahtar sözcük. 

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```

Dizideki her alan aynı türde olsa bile belirli bir tür parantez dışında kullanamayacağınızı unutmayın.

Varolan bildirimleri de içeren başlık deconstruct:

```csharp
public class Point
{
    public int X { get; set; }
    public int Y { get; set; }

    public Point(int x, int y) => (X, Y) = (x, y);
}
```

> [!WARNING]
>  Bildirimleri parantez içinde varolan bildirimlerle karıştıramazsınız. Örneğin, aşağıdaki verilmez: `(var x, y) = MyMethod();`. Bu hata CS8184 çünkü oluşturur *x* parantez içinde bildirilen ve *y* daha önce başka bir yerde bildirilir.

### <a name="deconstructing-user-defined-types"></a>Deconstructing kullanıcı tanımlı türler

Herhangi bir tanımlama grubu türü yukarıda gösterildiği gibi deconstructed. Kullanıcı tanımlı türler (sınıflar, yapılar veya hatta arabirimleri) üzerinde deconstruction etkinleştirmek kolaydır.

Bir veya daha fazla türü yazarı tanımlayabilirsiniz `Deconstruct` herhangi bir sayıda için değerler atayın yöntemleri `out` türü olun veri öğelerini temsil eden değişkenleri. Örneğin, aşağıdaki `Person` türünü tanımlayan bir `Deconstruct` bir kişi nesnesi ilk ad ve soyadı temsil eden elemanlara deconstructs yöntemi:

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#12_TypeWithDeconstructMethod "Type with a deconstruct method")]

Bir atama deconstruct yöntemi etkinleştirir bir `Person` temsil eden iki dizelere `FirstName` ve `LastName` özellikleri:

[!code-csharp[Deconstruct Type](../../samples/snippets/csharp/tuples/tuples/program.cs#12A_DeconstructType "Deconstruct a class type")]

Deconstruction bile değil Yazar türleri için etkinleştirebilirsiniz.
`Deconstruct` Yöntemi, bir nesnenin erişilebilir veri üyelerine tutucusu paketten çıkarır bir genişletme yöntemi olabilir. Gösterir aşağıdaki örnekte bir `Student` öğesinden türetilen tür `Person` türü ve deconstructs bir genişletme yöntemi bir `Student` temsil eden üç değişkenleri içine `FirstName`, `LastName` ve `GPA`:

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#13_ExtensionDeconstructMethod "Type with a deconstruct extension method")]

A `Student` nesne artık sahiptir erişilebilir iki `Deconstruct` yöntemleri: uzantı yöntemi için bildirilen `Student` türleri ve üyesi `Person` türü. Her ikisi de kapsamındaki ve sağlayan bir `Student` iki değişkeni veya üç deconstructed için.
Üç değişkenlere öğrencinin atarsanız, tüm ad, son adı ve GPA döndürdü. İki değişken öğrencinin atarsanız, yalnızca ilk ad ve Soyadı döndürülür.

[!code-csharp[Deconstruct extension method](../../samples/snippets/csharp/tuples/tuples/program.cs#13A_DeconstructExtension "Deconstruct a class type using an extension method")]

Birden çok tanımlama çok dikkatli olmalıdır `Deconstruct` yöntemleri bir sınıf ya da bir sınıf hiyerarşisi. Birden çok `Deconstruct` aynı sayıda yöntemleri `out` parametreleri hızla belirsizliğe neden olabilir. Arayanlar kolayca istenen arayabilmesi için olmayabilir `Deconstruct` yöntemi.

Bu örnekte, yoktur belirsiz bir çağrı için en az fırsat olmadığından `Deconstruct` yöntemi `Person` iki parametreleri çıktısı ve `Deconstruct` yöntemi `Student` üç sahiptir.

## <a name="conclusion"></a>Sonuç 

Adlandırılmış diziler yeni dil ve kitaplık desteği sınıfları ve yapıları yaptığınız gibi birden çok öğe depolamak ancak davranışı tanımlamayın veri yapılarını kullanan tasarımlar ile çalışmak çok daha kolay hale getirir. Kolay ve Diziler bu türleri için kullanılacak kısa. Daha ayrıntılı kullanarak türleri yazmak zorunda kalmadan statik tür denetlemesi tüm avantajlarını elde `class` veya `struct` sözdizimi. Buna rağmen yardımcı program yöntemleri için en kullanışlı `private`, veya `internal`. Kullanıcı tanımlı türler ya da oluşturma `class` veya `struct` ortak yöntemlerinizi birden çok öğeye sahip bir değer döndüğünüzde türleri.
