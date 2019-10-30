---
title: Demet türleri- C# kılavuz
description: İçinde adlandırılmamış ve adlandırılmış demet türleri hakkında bilgi edininC#
ms.date: 05/15/2018
ms.technology: csharp-fundamentals
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
ms.openlocfilehash: f551a1df4a31c3311119a0327e02fbc6096ce0a0
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039719"
---
# <a name="c-tuple-types"></a>C#demet türleri

C#tanımlama grupları, hafif bir sözdizimi kullanarak tanımladığınız türlerdir. Daha basit bir sözdizimi, sayıya göre dönüştürme kuralları (kardinalite olarak adlandırılır) ve öğe türleri ve kopyalar, eşitlik testleri ve atamalar için tutarlı kurallar vardır. Zorunluluğunu getirir olarak, tanımlama grupları devralma ile ilişkili nesne odaklı bazı deyimleri desteklemez. 7,0 sürümündeki yenilikler makalesindeki tanımlama bilgileri bölümüne genel bakış alabilirsiniz. [ C# ](whats-new/csharp-7.md#tuples)

Bu makalede, C# 7,0 ve sonraki sürümlerde tanımlama gruplarını ve bunları kullanmanın farklı yollarını ve tanımlama grupları ile çalışmaya yönelik ilk Kılavuzu düzenleyen dil kurallarını öğreneceksiniz.

> [!NOTE]
> Yeni tanımlama grubu özellikleri <xref:System.ValueTuple> türleri gerektirir.
> Türü içermeyen platformlarda kullanabilmek için, NuGet paketini [`System.ValueTuple` ' i](https://www.nuget.org/packages/System.ValueTuple/) eklemeniz gerekir.
>
> Bu, çerçeveye teslim edilen türleri kullanan diğer dil özelliklerine benzerdir. Örnek olarak, `INotifyCompletion` arabirimine bağlı `async` ve `await` ve `IEnumerable<T>` ' e bağlı LINQ verilebilir. Bununla birlikte, .NET daha fazla platforma bağımlı olduğu için teslim mekanizması değişiyor. .NET Framework, dil derleyicisi ile aynı temposunda her zaman yollanmayabilir. Yeni dil özellikleri yeni türlere dayandığınızda, bu türler dil Özellikleri sevk edildiğinde NuGet paketleri olarak kullanılabilir olacaktır. Bu yeni türler .NET Standard API 'sine eklendikçe ve Framework 'ün bir parçası olarak teslim edildiğinde, NuGet paket gereksinimi kaldırılır.

Yeni demet desteği ekleme nedenlerinden başlayalım. Yöntemler tek bir nesne döndürür. Tanımlama grupları bu tek nesnede birden çok değeri daha kolay paketlemenize olanak tanır.

.NET Framework zaten genel `Tuple` sınıfları var. Ancak, bu sınıfların iki önemli sınırlaması vardı. Biri için, `Tuple` sınıfları özellikleri `Item1`, `Item2` vb. olarak adlandırılır. Bu adlar hiçbir anlam bilgisi içermez. Bu `Tuple` türlerinin kullanılması, özelliklerin her birinin anlamını karşılayarak iletişim kurmasına imkan vermez. Yeni dil özellikleri, bir tanımlama grubu içindeki öğeler için anlamsal anlamlı adlar bildirme ve kullanma imkanı sağlar.

`Tuple` sınıfları, başvuru türleri olduklarından daha fazla performans sorunlarına neden olur. `Tuple` türlerinden birini kullanmak nesneleri ayırmayı gösterir. Etkin yollarda birçok küçük nesne ayırmak uygulamanızın performansı üzerinde ölçülebilir bir etkiye sahip olabilir. Bu nedenle, tanımlama birimleri için dil desteği yeni `ValueTuple` yapılarını kullanır.

Bu eksiklikleri önlemek için, birden çok öğeyi yürütmek üzere `class` veya `struct` oluşturabilirsiniz. Ne yazık ki, sizin için daha fazla çalışma ve tasarım amacınızı gizler. `struct` veya `class` yapmak, hem veri hem de davranışla bir tür tanımlamanız gerektiğini gösterir. Birçok kez yalnızca birden çok değeri tek bir nesnede depolamak istiyorsunuz.

Dil özellikleri ve `ValueTuple` genel yapıları, bu demet türlerine herhangi bir davranış (Yöntem) ekleyemeyeceği kuralını zorlar.
Tüm `ValueTuple` türleri *değişebilir yapılar*. Her üye alanı bir ortak alandır. Böylece çok hafif hale gelir. Bununla birlikte, bu, her ne kadar önemli olduğu durumlarda başlıkların kullanılması gerektiği anlamına gelir.

Tanımlama grupları, `class` ve `struct` türlerinden daha basit ve daha esnek veri kapsayıcılarıdır. Bu farklılıkları keşfedelim.

## <a name="named-and-unnamed-tuples"></a>Adlandırılmış ve adlandırılmamış diziler

`ValueTuple` yapısı, var olan `Tuple` türlerinde tanımlanan özelliklere benzer şekilde `Item1`, `Item2`, `Item3`, vb. adlı alanlara sahiptir.
Bu adlar, *adlandırılmamış tanımlama grupları*için kullanabileceğiniz tek adlardır. Bir tanımlama grubu için alternatif alan adı sağlamadığınızda, adlandırılmamış bir tanımlama grubu oluşturdunuz:

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/program.cs#01_UnNamedTuple "Unnamed tuple")]

Önceki örnekteki tanımlama grubu, değişmez sabitler kullanılarak başlatılmış ve 7,1 içinde C# *demet alan adı tahminleri* kullanılarak oluşturulan öğe adlarına sahip olmayacaktır.

Ancak, bir tanımlama grubu başlattığınızda, her bir alana daha iyi adlar veren yeni dil özellikleri kullanabilirsiniz. Bunun yapılması adlandırılmış bir *tanımlama grubu*oluşturur.
Adlandırılmış tanımlama gruplarının hala `Item1`, `Item2`, `Item3` vb. adlı öğeleri vardır.
Ancak, adlandırmış olduğunuz öğelerin herhangi biri için eş anlamlıları da vardır.
Her öğe için ad belirterek adlandırılmış bir tanımlama grubu oluşturursunuz. Bir yol, kayıt kümesi başlatmasının parçası olarak adları belirtmektir:

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/program.cs#02_NamedTuple "Named tuple")]

Adlandırılmış tanımlama gruplarını etkin bir şekilde kullanabilmeniz için bu eş anlamlılar derleyici ve dil tarafından işlenir. Ides ve düzenleyiciler, Roslyn API 'Lerini kullanarak bu anlam adlarını okuyabilir. Adlandırılmış bir tanımlama grubunun öğelerine aynı derlemenin herhangi bir yerindeki anlam adlarıyla başvurabilirsiniz. Derleyici, derlenmiş çıktıyı oluştururken `Item*` eşdeğerleriyle tanımladığınız adların yerini alır. Derlenen Microsoft ara dili (MSIL), bu öğeleri verdiğiniz adları içermez.

7,1 ' C# den başlayarak, kayıt düzeni için alan adları, kayıt düzeni başlatmak için kullanılan değişkenlerden bulunabilir. Bu, **[demet yansıtma başlatıcıları](#tuple-projection-initializers)** olarak adlandırılır. Aşağıdaki kod, `accumulation` adlı `count` (bir tamsayı) ve `sum` (çift) içeren bir tanımlama grubu oluşturur.

[!code-csharp[ProjectedTuple](../../samples/snippets/csharp/tuples/program.cs#ProjectedTupleNames "Named tuple")]

Derleyici, ortak Yöntemler veya özelliklerden döndürülen tanımlama grupları için oluşturduğunuz adları iletmelidir. Bu durumlarda, derleyici yöntemine bir <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> özniteliği ekler. Bu öznitelik, kayıt grubundaki her öğeye verilen adları içeren <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> liste özelliği içerir.

> [!NOTE]
> Visual Studio gibi geliştirme araçları da bu meta verileri okur ve meta veri alanı adlarını kullanarak IntelliSense ve diğer özellikleri sağlar.

Adlandırılmış tanımlama gruplarını birbirlerine atamaya yönelik kuralları anlamak için yeni tanımlama bilgileri ve `ValueTuple` türü temel temellerini anlamak önemlidir.

## <a name="tuple-projection-initializers"></a>Demet projeksiyon başlatıcıları

Genel olarak, demet yansıtma başlatıcıları, bir demet başlatma bildiriminin sağ tarafındaki değişken veya alan adlarını kullanarak çalışır.
Açık bir ad verilirse, bu, yansıtılan herhangi bir adın önüne geçer. Örneğin, aşağıdaki başlatıcıda öğeler `explicitFieldOne` ve `explicitFieldTwo` ' dir `localVariableOne` ve `localVariableTwo`:

[!code-csharp[ExplicitNamedTuple](../../samples/snippets/csharp/tuples/program.cs#ProjectionExample_Explicit "Explicitly named tuple")]

Açık bir adın sağlanmadığı herhangi bir alan için, geçerli bir örtük ad yansıtıldır. Açıkça veya örtük olarak anlamsal adlar sağlama gereksinimi yoktur. Aşağıdaki başlatıcıda, değeri "her şeye yanıt" olan, değeri `42` ve `stringContent` olan `Item1` alan adlarına sahiptir:

[!code-csharp[MixedTuple](../../samples/snippets/csharp/tuples/program.cs#MixedTuple "mixed tuple")]

Aday alan adlarının demet alanı üzerinde yansıtılmamaları gereken iki koşul vardır:

1. Aday adı, ayrılmış bir tanımlama grubu adı olduğunda. Örnekler arasında `Item3`, `ToString` veya `Rest` sayılabilir.
1. Aday adı, başka bir demet alan adının bir yinelemesi olduğunda açık veya kapalı olur.

Bu koşullar belirsizlik kullanmaktan kaçının. Bu adlar, bir tanımlama grubu içindeki bir alanın alan adları olarak kullanıldıklarında belirsizliğe neden olur. Bu koşullardan hiçbiri derleme zamanı hatalarına neden olur. Bunun yerine, yansıtılan adlara sahip öğeler kendileri için öngörülen semantik adlara sahip değildir.  Aşağıdaki örneklerde bu koşullar gösterilmektedir:

[!code-csharp-interactive[Ambiguity](../../samples/snippets/csharp/tuples/program.cs#ProjectionAmbiguities "tuples where projections are not performed")]

Bu durumlar derleyici hatalarına neden olmaz çünkü demet alan adı projeksiyonu kullanılabilir olmadığında, 7,0 ile C# yazılan koda yönelik bir değişiklik olacaktır.

## <a name="equality-and-tuples"></a>Eşitlik ve tanımlama grupları

7,3 ile C# başlayarak, demet türleri `==` ve `!=` işleçlerini destekler. Bu işleçler, sol bağımsız değişkenin her bir üyesini sırasıyla doğru bağımsız değişkenin her bir üyesiyle karşılaştırarak çalışır. Bu karşılaştırmalar kısa devre. Bir çift eşit olmadığı anda üyelerin değerlendirilmesi durdurulur. Aşağıdaki kod örnekleri `==` kullanır, ancak karşılaştırma kuralları hepsi `!=` ' e uygulanır. Aşağıdaki kod örneği iki tamsayı çifti için bir eşitlik karşılaştırması gösterir:

[!code-csharp-interactive[TupleEquality](../../samples/snippets/csharp/tuples/program.cs#Equality "Testing tuples for equality")]

Demet eşitlik testlerini daha uygun hale getirmek için çeşitli kurallar vardır. Tanımlama grubu eşitliği, aşağıdaki kodda gösterildiği gibi, tanımlama gruplarının biri null yapılabilir bir tanımlama grubu ise [yükseltilmemiş dönüştürmeleri](~/_csharplang/spec/conversions.md#lifted-conversion-operators) gerçekleştirir:

[!code-csharp-interactive[NullableTupleEquality](../../samples/snippets/csharp/tuples/program.cs#NullableEquality "Comparing Tuples and nullable tuples")]

Tanımlama grubu eşitliği, her iki başlığın de her bir üyesinde örtük dönüştürmeler de gerçekleştirir. Bunlar, yükseltilmemiş dönüştürmeleri, genişleyen dönüşümler veya diğer örtük dönüştürmeler içerir. Aşağıdaki örneklerde, tamsayı 2 kayıt düzeninin, tamsayıdan Long 'a örtük dönüştürme nedeniyle uzun 2 tanımlama grubu ile karşılaştırılabilmesinin gösterilmektedir:

[!code-csharp-interactive[SnippetMemberConversions](../../samples/snippets/csharp/tuples/program.cs#SnippetMemberConversions "converting tuples for equality tests")]

Demet üyelerinin adları, eşitlik için testlere katılmaz. Ancak, işlenenden biri açık adlara sahip bir demet sabit değeri ise, bu adlar diğer işlenenin adlarıyla eşleşmezse, derleyici uyarı CS8383 oluşturur.
Her iki işlenenin de demet sabit değerleri olduğu durumlarda, aşağıdaki örnekte gösterildiği gibi uyarı sağ işlenende olur:

[!code-csharp-interactive[MemberNames](../../samples/snippets/csharp/tuples/program.cs#SnippetMemberNames "Tuple member names do not participate in equality tests")]

Son olarak, tanımlama grupları iç içe diziler içerebilir. Tanımlama grubu eşitliği, aşağıdaki örnekte gösterildiği gibi, iç içe geçmiş diziler aracılığıyla her bir işlenenin "şeklini" karşılaştırır:

[!code-csharp-interactive[NestedTuples](../../samples/snippets/csharp/tuples/program.cs#SnippetNestedTuples "Tuples may contain nested tuples that participate in tuple equality.")]

Farklı şekilleri olduğunda, eşitlik (veya eşitsizlik) için iki tanımlama grubunu karşılaştırmak üzere bir derleme zamanı hatası. Derleyici, iç içe geçmiş tanımlama gruplarının kendisini karşılaştırmak için denenmez.

## <a name="assignment-and-tuples"></a>Atama ve tanımlama grupları

Dil, her bir sağ taraftaki öğenin örtük olarak karşılık gelen sol taraftaki öğesine dönüştürülebileceği, aynı sayıda öğeye sahip demet türleri arasında atamayı destekler. Diğer dönüşümler atamalar için kabul edilmez. Farklı şekillerde bir tanımlama grubu atamak için bir derleme zamanı hatası vardır. Derleyici, iç içe geçmiş tanımlama gruplarının atamasını atamak için denenmez.
Demet türleri arasında izin verilen atama türlerine bakalım.

Aşağıdaki örneklerde kullanılan değişkenleri göz önünde bulundurun:

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/program.cs#03_VariableCreation "Variable creation")]

İlk iki değişken, `unnamed` ve `anonymous` öğeler için belirtilen semantik adlara sahip değildir. Alan adları `Item1` ve `Item2` ' dir.
Son iki değişken, `named` ve `differentName` öğeler için verilen semantik adlara sahiptir. Bu iki başlık, öğeler için farklı adlara sahiptir.

Bu başlıkların dördü, aynı sayıda öğeye sahiptir (' kardinalite ' olarak adlandırılır) ve bu öğelerin türleri aynıdır. Bu nedenle, bu atamaların hepsi çalışır:

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/program.cs#04_VariableAssignment "Variable assignment")]

Başlıkların adlarının atanmadığından emin olun. Öğelerin değerleri, kayıt düzeni içindeki öğelerin sırasını izleyerek atanır.

Farklı türlerin veya öğe sayılarının başlıkları atanamaz:

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a>Yöntem dönüş değerleri olarak tanımlama grubu

Tanımlama grupları için en yaygın kullanımdan biri yöntem dönüş değeri olarak belirlenir. Bir örnek adım adım inceleyelim. Bir dizi sayı için standart sapmayı hesaplayan bu yöntemi göz önünde bulundurun:

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/statistics.cs#05_StandardDeviation "Compute Standard Deviation")]

> [!NOTE]
> Bu örnekler düzeltilmeyen örnek standart sapmayı hesaplar.
> Düzeltilen örnek standart sapma formülü, `Average` genişletme yöntemi olduğundan, kare farklarının toplamını N yerine (N-1) değerine böler. Standart sapma için bu formüller arasındaki farklılıklar hakkında daha fazla ayrıntı için bir istatistik metnine danışın.

Yukarıdaki kod, standart sapma için textbook formülünü izler. Doğru yanıtı üretir ancak bu, verimsiz bir uygulama. Bu yöntem, diziyi iki kez numaralandırır: ortalamayı üretmek için bir kez ve ortalamanın farkının ortalamasının ortalamasını üretmek için bir kez.
(LINQ sorgularının geç değerlendirildiğini unutmayın. bu nedenle, ortalama farklar ve bu farkların ortalaması yalnızca bir numaralandırma yapar.)

Dizinin yalnızca bir listesini kullanarak standart sapmayı hesaplayan alternatif bir formül vardır.  Bu hesaplama, diziyi numaralandırdığından iki değer üretir: dizideki tüm öğelerin toplamı ve her bir değerin kare toplamı:

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/statistics.cs#06_SumOfSquaresFormula "Compute Standard Deviation using the sum of squares")]

Bu sürüm, diziyi tam olarak bir kez numaralandırır. Ancak yeniden kullanılabilir kod değildir. Çalışmaya devam ederseniz, birçok farklı istatistiksel hesaplamaların dizideki öğelerin sayısını, sıranın toplamını ve dizi karelerinin toplamını kullanmasını göreceksiniz. Bu yöntemi yeniden düzenleme ve bu değerlerin üçünü de üreten bir yardımcı program yöntemi yazma. Üç değer de bir tanımlama grubu olarak döndürülebilir.

Bu yöntemi, numaralandırma sırasında hesaplanan üç değerin bir kayıt düzeninde depolanması için güncelleştirelim. Bu sürümü oluşturur:

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/statistics.cs#07_TupleVersion "Refactor to use tuples")]

Visual Studio 'nun yeniden düzenleme desteği, çekirdek istatistik işlevlerinin özel bir yönteme ayıklanabilmesini kolaylaştırır. Bu, `Sum`, `SumOfSquares` ve `Count` ' ün üç değeri ile demet türünü döndüren `private static` yöntemi sağlar:

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/statistics.cs#08_TupleMethodVersion "After extracting utility method")]
 
Dil, el ile birkaç hızlı düzenleme yapmak istiyorsanız kullanabileceğiniz birkaç seçenek sağlar. İlk olarak, `var` bildirimini kullanarak `ComputeSumAndSumOfSquares` yöntem çağrısından kayıt düzeni sonucunu başlatabilirsiniz. `ComputeSumAndSumOfSquares` yöntemi içinde üç ayrı değişken de oluşturabilirsiniz. Son sürüm aşağıdaki kodda gösterilmiştir:

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/statistics.cs#09_CleanedTupleVersion "After final cleanup")]

Bu son sürüm, bu üç değere veya bunların herhangi bir alt kümesine ihtiyacı olan herhangi bir yöntem için kullanılabilir.

Dil, bu demet döndürme yöntemlerinde öğelerin adlarını yönetmenin diğer seçeneklerini destekler.

Dönüş değeri bildiriminden alan adlarını kaldırabilir ve adlandırılmamış bir tanımlama grubu döndürebilirsiniz:

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

Bu kayıt düzeninin alanları `Item1`, `Item2` ve `Item3` olarak adlandırılır.
Metotlardan döndürülen başlıkların öğelerine anlam isimleri sağlamanız önerilir.

LINQ sorguları yazarken, tanımlama gruplarının yararlı olabilecek başka bir IOM. Son öngörülen sonuç, seçilen nesnelerin özelliklerinin tümünü değil, genellikle bazılarını içerir.

Genellikle sorgunun sonuçlarını anonim bir tür bir nesne dizisine proje olarak projecekti. Bu çok sayıda kısıtlama sunuyordu, öncelikle anonim türler bir yöntem için dönüş türünde kolaylıkla adlandırılamadığından. Sonuç türü olarak `object` veya `dynamic` kullanmanın alternatifleri, önemli performans maliyetleriyle birlikte geldi.

Bir demet türü dizisinin döndürülmesi kolaydır ve öğelerin adları ve türleri derleme zamanında ve IDE araçları aracılığıyla kullanılabilir.
Örneğin, bir ToDo uygulaması düşünün. Yapılacaklar listesindeki tek bir girişi göstermek için aşağıdakine benzer bir sınıf tanımlayabilirsiniz:

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/projectionsample.cs#14_ToDoItem "To Do Item")]

Mobil uygulamalarınız, yalnızca başlığı görüntüleyen geçerli ToDo öğelerinin Compact formunu destekleyebilir. Bu LINQ sorgusu, yalnızca KIMLIĞI ve başlığı içeren bir projeksiyon oluşturacak. Bir tanımlama grubu sırası döndüren bir yöntem tasarımın iyi olduğunu ifade eder:

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/projectionsample.cs#15_QueryReturningTuple "Query returning a tuple")]

> [!NOTE]
> 7,1 C# ' de demet projeksiyonları, anonim türlerde özellik adlandırmasına benzer şekilde, öğeleri kullanarak, adlandırılmış tanımlama grupları oluşturmanıza imkan tanır. Yukarıdaki kodda, sorgu projeksiyonundaki `select` deyimleri, `ID` ve `Title` öğelerine sahip bir tanımlama grubu oluşturur.

Adlandırılmış tanımlama grubu, imzanın bir parçası olabilir. Derleyicinin ve IDE araçlarının, sonucu doğru şekilde kullandığınızı, statik denetim sağlamasına imkan tanır. Adlandırılmış tanımlama grubu statik tür bilgilerini de taşır, bu nedenle, sonuçlarla çalışmak için yansıma veya dinamik bağlama gibi pahalı çalışma süresi özelliklerinin kullanılmasına gerek yoktur.

## <a name="deconstruction"></a>Ayrıştırma

Bir yöntem tarafından döndürülen kayıt *grubunu kaldırarak bir* kayıt grubundaki tüm öğelerin paketini kaldırabilirsiniz. Başlıkların çıkarılması için üç farklı yaklaşım vardır.  İlk olarak, her bir alanın türünü parantez içindeki her bir öğe için ayrı değişkenler oluşturmak üzere açıkça bildirebilirsiniz:

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/statistics.cs#10_Deconstruct "Deconstruct")]

Ayrıca, parantez dışında `var` anahtar sözcüğünü kullanarak bir kayıt grubundaki her bir alan için örtük olarak yazılan değişkenler de bildirebilirsiniz:

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/statistics.cs#11_DeconstructToVar "Deconstruct to Var")]

Ayrıca, parantez içindeki tüm değişken bildirimleri veya `var` anahtar sözcüğünü kullanmak da geçerlidir. 

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```

Kayıt grubundaki her alan aynı türde olsa bile, parantez dışında belirli bir tür kullanamazsınız.

Mevcut bildirimlerle de tanımlama gruplarını kaldırabilirsiniz:

```csharp
public class Point
{
    public int X { get; set; }
    public int Y { get; set; }

    public Point(int x, int y) => (X, Y) = (x, y);
}
```

> [!WARNING]
> Parantez içindeki bildirimlerle mevcut bildirimleri karıştıramazsınız. Örneğin, aşağıdakilere izin verilmez: `(var x, y) = MyMethod();`. *X* , parantez içinde bildirildiği ve *y* daha önce başka bir yerde BILDIRILDIĞI için bu hata CS8184 oluşturur.

### <a name="deconstructing-user-defined-types"></a>Kullanıcı tanımlı türleri kaldırma

Herhangi bir demet türü, yukarıda gösterilen şekilde kaldırılabilir. Kullanıcı tanımlı herhangi bir tür (sınıflar, yapılar veya hatta arabirimler) üzerinde oluşturmayı etkinleştirmek de kolaydır.

Tür yazarı, türü oluşturan veri öğelerini temsil eden herhangi bir sayıda `out` değişkenine değer atayan bir veya daha fazla `Deconstruct` yöntemi tanımlayabilir. Örneğin, aşağıdaki `Person` türü, bir kişi nesnesini ilk adı ve soyadı temsil eden öğelere oluşturan bir `Deconstruct` yöntemi tanımlar:

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/person.cs#12_TypeWithDeconstructMethod "Type with a deconstruct method")]

Deyapý yöntemi, `FirstName` ve `LastName` özelliklerini temsil eden `Person` ' dan iki dizeye atamayı sağlar:

[!code-csharp[Deconstruct Type](../../samples/snippets/csharp/tuples/program.cs#12A_DeconstructType "Deconstruct a class type")]

Yazmayan türler için bile, oluşturmayı etkinleştirebilirsiniz.
`Deconstruct` yöntemi, bir nesnenin erişilebilir veri üyelerini paketten uygulayan bir genişletme yöntemi olabilir. Aşağıdaki örnekte, `Person` türünden türetilmiş bir `Student` türü ve `FirstName`, `LastName` ve `GPA` temsil eden üç değişkene `Student` oluşturan bir genişletme yöntemi gösterilmektedir:

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/person.cs#13_ExtensionDeconstructMethod "Type with a deconstruct extension method")]

`Student` nesnesi artık iki adet erişilebilir `Deconstruct` yöntemine sahiptir: `Student` türleri için belirtilen genişletme yöntemi ve `Person` türü üyesi. Her ikisi de kapsamdadır ve bir `Student` ' ı iki değişkene veya üçüne ayırmayı sağlar.
Üç değişkene bir öğrenci atarsanız, ilk ad, soyadı ve GPA döndürülür. İki değişkene bir öğrenci atarsanız, yalnızca ad ve soyadı döndürülür.

[!code-csharp[Deconstruct extension method](../../samples/snippets/csharp/tuples/program.cs#13A_DeconstructExtension "Deconstruct a class type using an extension method")]

Bir sınıfta veya sınıf hiyerarşisinde birden çok `Deconstruct` yöntemi tanımlamayı dikkatli olmanız gerekir. Aynı sayıda `out` parametresi olan birden çok `Deconstruct` yöntemi hızla belirsizlikleri neden olabilir. Çağıranlar istenen `Deconstruct` yöntemini kolayca çağıramayabilir.

Bu örnekte, belirsiz bir çağrı için en az şans vardır çünkü `Person` için `Deconstruct` yöntemi iki çıkış parametresine sahip ve `Student` için `Deconstruct` yönteminin üç tane vardır.

Yinelenenleri kaldırma işleçleri, test eşitliğine katılmaz. Aşağıdaki örnek, CS0019 derleyici hatası oluşturur:

```csharp
Person p = new Person("Althea", "Goodwin");
if (("Althea", "Goodwin") == p)
    Console.WriteLine(p);
```

`Deconstruct` yöntemi, `Person` nesne `p` iki dize içeren bir kayıt türüne dönüştürebilir, ancak eşitlik testleri bağlamında geçerli değildir.

## <a name="tuples-as-out-parameters"></a>Out parametreleri olarak tanımlama grubu

Tanımlama grupları, *out parametreleri olarak*kullanılabilir. Daha önce [ayrıştırma](#deconstruction) bölümünde bahsedilen belirsizlik ile karıştırılmamalıdır. Bir yöntem çağrısında, yalnızca demet 'in şeklini açıklamanız gerekir:

[!code-csharp[TuplesAsOutParameters](~/samples/snippets/csharp/tuples/program.cs#01_TupleAsOutVariable "Tuples as out parameters")]

Alternatif olarak, [_adlandırılmamış_](#named-and-unnamed-tuples) bir tanımlama grubu kullanabilir ve alanlarına `Item1` ve `Item2` olarak başvurabilirsiniz:

```csharp
dict.TryGetValue(2, out (int, string) pair);
// ...
Console.WriteLine($"{pair.Item1}: {pair.Item2}");
```

## <a name="conclusion"></a>Sonuç 

Adlandırılmış tanımlama grupları için yeni dil ve kitaplık desteği, birden çok öğeyi depolayan ancak sınıflar ve yapılar için davranış tanımlamadığınız veri yapılarını kullanan tasarımlarla çalışmayı çok daha kolay hale getirir. Bu türler için tanımlama gruplarını kullanmak kolaydır. Daha ayrıntılı `class` veya `struct` sözdizimini kullanarak tür yazmak zorunda kalmadan statik tür denetimi avantajlarından yararlanın. Bu sayede bile, `private` veya `internal` olan yardımcı program yöntemleri için en iyi seçenektir. Ortak yöntemleriniz birden çok öğeye sahip bir değer döndürzaman `class` veya `struct` tür Kullanıcı tanımlı türler oluşturun.
