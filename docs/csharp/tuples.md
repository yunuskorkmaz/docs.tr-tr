---
title: Tuple türleri - C# Kılavuzu
description: "C'de adsız ve adlandırılmış tuple türleri hakkında bilgi edinin #"
ms.date: 05/15/2018
ms.technology: csharp-fundamentals
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
ms.openlocfilehash: 9ce9e1d4395d1a75f36004384ec215c615cd9802
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156915"
---
# <a name="c-tuple-types"></a>C# tuple türleri

C# tuples hafif bir sözdizimi kullanarak tanımladığınız türleridir. Avantajları arasında daha basit bir sözdizimi, sayıya (kardinallik olarak anılacaktır) dayalı dönüşümkuralları ve öğe türleri ve kopyalar, eşitlik testleri ve atamalar için tutarlı kurallar yer almaktadır. Bir tradeoff olarak, tuples bazı nesne yönelimli deyimler devralma ile ilişkili desteklemez. [C# 7.0](whats-new/csharp-7.md#tuples) makalesinde yeni olan tuples bölümüne genel bir bakış alabilirsiniz.

Bu makalede, C# 7.0 ve sonraki sürümlerde tuples yöneten dil kuralları, bunları kullanmak için farklı yollar ve tuples ile çalışma ilk rehberlik öğreneceksiniz.

> [!NOTE]
> Yeni tuples özellikleri <xref:System.ValueTuple> türleri gerektirir.
> Türleri içermeyen platformlarda [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) kullanmak için NuGet paketini eklemeniz gerekir.
>
> Bu, çerçevede teslim edilen türlere dayanan diğer dil özelliklerine benzer. Örnekler `async` arasında `await` `INotifyCompletion` arayüze ve LINQ'a `IEnumerable<T>`güvenerek. Ancak,.NET daha platformbağımsız hale geldikçe teslimat mekanizması değişiyor. .NET Framework her zaman dil derleyicisi ile aynı cadence üzerinde gemi olmayabilir. Yeni dil özellikleri yeni türlere dayandığında, bu tür ler dil özellikleri geldiğinde NuGet paketleri olarak kullanılabilir. Bu yeni türler .NET Standart API'ye eklenip çerçevenin bir parçası olarak teslim edildikçe, NuGet paket gereksinimi kaldırılır.

Yeni tuple desteği ekleme nin nedenleri ile başlayalım. Yöntemler tek bir nesneyi döndürer. Tuples, o tek nesnedeki birden çok değeri daha kolay paketlemenizi sağlar.

.NET Framework zaten `Tuple` genel sınıflara sahiptir. Ancak bu sınıfların iki büyük sınırlaması vardı. İlk olarak, `Tuple` sınıflar kendi `Item1` `Item2`özellikleri , ve benzeri adlı. Bu isimler anlamsal bilgi taşımama. Bu `Tuple` türleri kullanmak, özelliklerin her birinin anlamını iletmesini sağlamaz. Yeni dil özellikleri, bir tuple'daki öğeler için anlamsal olarak anlamlı adlar beyan etmenizi ve kullanmanıza olanak tanır.

Sınıflar, `Tuple` başvuru türleri olduğundan daha fazla performans endişesine neden olur. `Tuple` Türlerden birini kullanmak, nesneleri ayırmaanlamına gelir. Sıcak yollarda, birçok küçük nesne ayırmak uygulamanızın performansı üzerinde ölçülebilir bir etki yapabilir. Bu nedenle, tuples için dil `ValueTuple` desteği yeni structs yararlanır.

Bu eksiklikleri önlemek için, birden `class` çok `struct` öğe taşımak için bir veya a oluşturabilirsiniz. Ne yazık ki, bu sizin için daha fazla iş, ve tasarım niyetini gizler. Hem `struct` veri `class` hem de davranış içeren bir tür tanımladığınızı veya bir tür tanımladığınızı ima etme. Çoğu zaman, yalnızca tek bir nesnede birden çok değer depolamak istiyorum.

Dil özellikleri ve `ValueTuple` genel yapı, bu tuple türlerine herhangi bir davranış (yöntem) ekleyemeyeceğiniz kuralını uygular.
Tüm `ValueTuple` türleri *mutable structs*vardır. Her üye alanı ortak bir alandır. Bu onları çok hafif yapar. Ancak, bu, değişmezliğin önemli olduğu yerlerde tuples kullanılmamalıdır anlamına gelir.

Tuples hem basit ve daha esnek `class` `struct` veri kapsayıcıları ve türleri vardır. Bu farklılıkları inceleyelim.

## <a name="named-and-unnamed-tuples"></a>Adlandırılmış ve adsız tuples

`ValueTuple` Yapı, varolan `Item1` `Item2` `Item3` `Tuple` türlerde tanımlanan özelliklere benzer şekilde , , , vb. adlı alanlara sahiptir.
Bu *adlar, adsız tuples*için kullanabileceğiniz tek adlardır. Bir tuple'a alternatif alan adları sağlamadığınızda, adsız bir tuple oluşturdunuz:

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/program.cs#01_UnNamedTuple "Unnamed tuple")]

Önceki örnekte tuple literal sabitler kullanılarak başharfe getirilmiştir ve C# 7.1'de *tuple alan adı projeksiyonları* kullanılarak oluşturulan öğe adları yoktur.

Ancak, bir tuple'ı başharfe aldığınızda, her alana daha iyi adlar veren yeni dil özelliklerini kullanabilirsiniz. Bunu yapmak adlandırılmış bir *tuple*oluşturur.
Adlandırılmış tuples hala `Item1` `Item2`adlı `Item3` öğeleri var , , ve benzeri.
Ama aynı zamanda sizin adlandırdığınız bu öğelerin herhangi biri için eşanlamlı var.
Her öğeiçin adları belirterek adlandırılmış bir tuple oluşturursunuz. Bir yolu tuple başlatma nın bir parçası olarak adları belirtmektir:

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/program.cs#02_NamedTuple "Named tuple")]

Bu eşanlamlılar derleyici ve dil tarafından işlenir, böylece adlandırılmış tuples'ı etkili bir şekilde kullanabilirsiniz. IID'ler ve editörler bu anlamsal adları Roslyn API'lerini kullanarak okuyabilirler. Adlandırılmış bir tuple'ın öğelerini, aynı derlemenin herhangi bir yerinde ki anlamsal adlarla başvurulayabilirsiniz. Derleyici, derlenmiş çıktıyı oluştururken `Item*` tanımladığınız adları eşdeğerleriyle değiştirir. Derlenmiş Microsoft Intermediate Language (MSIL), bu öğeleri vermiş olduğunuz adları içermez.

C# 7.1 ile başlayarak, bir tuple için alan adları tuple başlatılması için kullanılan değişkenlerden sağlanabilir. Bu **[tuple projeksiyon başharfleri](#tuple-projection-initializers)** olarak adlandırılır. Aşağıdaki kod, öğeler `accumulation` `count` (bir tamsayı) ve `sum` (çift) ile birlikte bir tuple oluşturur.

[!code-csharp[ProjectedTuple](../../samples/snippets/csharp/tuples/program.cs#ProjectedTupleNames "Named tuple")]

Derleyici, ortak yöntemlerden veya özelliklerden döndürülen tuples için oluşturduğunuz adları iletmelidir. Bu gibi durumlarda, derleyici <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> yönteme bir öznitelik ekler. Bu öznitelik, <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> tuple'daki öğelerin her birine verilen adları içeren bir liste özelliği içerir.

> [!NOTE]
> Visual Studio gibi Geliştirme Araçları da bu meta verileri okur ve meta veri alan adlarını kullanarak IntelliSense ve diğer özellikleri sağlar.

Yeni tuples bu temelleri ve `ValueTuple` birbirlerine adlandırılmış tuples atama kurallarını anlamak için türü anlamak önemlidir.

## <a name="tuple-projection-initializers"></a>Tuple projeksiyon başfçıları

Genel olarak, tuple projeksiyon başfasyonları, bir tuple başlatma deyiminin sağ tarafındaki değişken veya alan adlarını kullanarak çalışır.
Açık bir ad verilirse, bu, yansıtılan herhangi bir ada göre önceliklidir. Örneğin, aşağıdaki baş harfe yönelik olarak, `explicitFieldTwo`öğeler `localVariableOne` `localVariableTwo` `explicitFieldOne` ve , değil ve:

[!code-csharp[ExplicitNamedTuple](../../samples/snippets/csharp/tuples/program.cs#ProjectionExample_Explicit "Explicitly named tuple")]

Açık bir ad verilen herhangi bir alan için, geçerli bir örtülü ad yansıtılır. Anlamsal adlar sağlamak için herhangi bir gereklilik yoktur, ya açık veya örtülü. Aşağıdaki baş harf, değeri `Item1` `42` `stringContent`"Her şeyin cevabı" olan alan adları vardır:

[!code-csharp[MixedTuple](../../samples/snippets/csharp/tuples/program.cs#MixedTuple "mixed tuple")]

Aday alan adlarının tuple alanına yansıtılan olmayan iki koşulu vardır:

1. Aday adı ayrılmış bir tuple adı olduğunda. Örnekler `Item3`arasında `ToString`, `Rest`, veya .
1. Aday adı açık veya örtülü başka bir tuple alan adının bir kopyası olduğunda.

Bu koşullar belirsizliği önler. Bu adlar, bir tuple'daki bir alanın alan adları olarak kullanılırsa belirsizliğe neden olur. Bu koşulların hiçbiri derleme zamanı hatalarına neden değildir. Bunun yerine, yansıtılan adları olmayan öğeler için yansıtılan anlamsal adlar yoktur.  Aşağıdaki örnekler bu koşulları göstermektedir:

[!code-csharp-interactive[Ambiguity](../../samples/snippets/csharp/tuples/program.cs#ProjectionAmbiguities "tuples where projections are not performed")]

Bu durumlar derleyici hatalarına neden olmaz, çünkü bu, tuple alan adı projeksiyonları olmadığında C# 7.0 ile yazılmış kod için bir bozma değişikliği olacaktır.

## <a name="equality-and-tuples"></a>Eşitlik ve tuples

C# 7.3 ile başlayarak, tuple türleri `==` ve `!=` işleçleri destekler. Bu işleçler, sol bağımsız değişkenin her üyesini sırayla sağ bağımsız değişkenin her üyesiyle karşılaştırarak çalışır. Bu karşılaştırmalar kısa devre. Bir çift eşit olmadığı anda üyeleri değerlendirmeyi bırakırlar. Aşağıdaki kod örnekleri `==`kullanır, ancak karşılaştırma `!=`kurallarının tümü . Aşağıdaki kod örneği, iki çift bir sonda için eşitlik karşılaştırması gösterir:

[!code-csharp-interactive[TupleEquality](../../samples/snippets/csharp/tuples/program.cs#Equality "Testing tuples for equality")]

Tuple eşitlik testlerini daha kullanışlı hale getiren birkaç kural vardır. Tuple eşitliği, aşağıdaki kodda gösterildiği gibi, tuples biri nullable tuple ise [kaldırılmış dönüşümler](~/_csharplang/spec/conversions.md#lifted-conversion-operators) gerçekleştirir:

[!code-csharp-interactive[NullableTupleEquality](../../samples/snippets/csharp/tuples/program.cs#NullableEquality "Comparing Tuples and nullable tuples")]

Tuple eşitliği aynı zamanda her iki tuples her üyesi üzerinde örtülü dönüşümler gerçekleştirir. Bunlar arasında kaldırılmış dönüşümler, genişletme dönüşümleri veya diğer örtülü dönüşümler yer almaktadır. Aşağıdaki örnekler, tamsayıdan uzuna örtülü dönüşüm nedeniyle bir tamsayı 2-tuple ile karşılaştırılabilen bir tamsayı 2-tuple'ı göstermektedir:

[!code-csharp-interactive[SnippetMemberConversions](../../samples/snippets/csharp/tuples/program.cs#SnippetMemberConversions "converting tuples for equality tests")]

Tuple üyelerinin adları eşitlik testlerine katılmaz. Ancak, operands biri açık adlarla bir tuple literal ise, derleyici bu adlar diğer operand adlarını eşleşmiyorsa CS8383 uyarı oluşturur.
Her iki operands tuple literals olduğu durumlarda, uyarı sağ operand aşağıdaki örnekte gösterildiği gibi:

[!code-csharp-interactive[MemberNames](../../samples/snippets/csharp/tuples/program.cs#SnippetMemberNames "Tuple member names do not participate in equality tests")]

Son olarak, tuples iç içe tuples içerebilir. Tuple eşitliği aşağıdaki örnekte gösterildiği gibi iç içe geçen tupüller aracılığıyla her operand "şekli" karşılaştırır:

[!code-csharp-interactive[NestedTuples](../../samples/snippets/csharp/tuples/program.cs#SnippetNestedTuples "Tuples may contain nested tuples that participate in tuple equality.")]

Farklı şekillere sahip olduklarında eşitlik (veya eşitsizlik) için iki tuple'ı karşılaştırmak için bir derleme zaman hatasıdır. Derleyici, iç içe geçmiş tupülleri karşılaştırmak için herhangi bir yapısızlaştırma girişiminde bulunmaz.

## <a name="assignment-and-tuples"></a>Atama ve tuples

Dil, her sağ yan öğenin örtülü olarak karşılık gelen sol yan öğesine dönüştürülebileceği aynı sayıda öğeye sahip tuple türleri arasındaki atamayı destekler. Diğer dönüşümler atamalar için dikkate alınmaz. Farklı şekiller olduğunda bir tuple'ı diğerine atamak için bir derleme zaman hatasıdır. Derleyici, iç içe geçmiş tupülleri atamak için herhangi bir yapısızlaştırma girişiminde bulunmaz.
Tuple türleri arasında izin verilen atama türlerine bakalım.

Aşağıdaki örneklerde kullanılan bu değişkenleri göz önünde bulundurun:

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/program.cs#03_VariableCreation "Variable creation")]

İlk iki değişken `unnamed` ve `anonymous` öğeler için sağlanan anlamsal adları yok. Alan adları `Item1` ve. `Item2`
Son iki değişken `named` ve `differentName` öğeler için verilen anlamsal adlara sahiptir. Bu iki tuples öğeleri için farklı adlar vardır.

Bu tuples dört öğeleri aynı sayıda ('kardinallik' olarak anılacaktır) ve bu öğelerin türleri aynıdır. Bu nedenle, tüm bu atamalar çalışır:

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/program.cs#04_VariableAssignment "Variable assignment")]

Tuples adlarının atanmamış olduğuna dikkat edin. Öğelerin değerleri, tuple'daki öğelerin sırasına göre atanır.

Farklı türde veya sayıda öğenin tuples atanamaz:

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a>Yöntem döndürme değerleri olarak tuples

Tuples için en yaygın kullanımlarından biri bir yöntem dönüş değeri olarak. Bir örnek üzerinden bakalım. Bir sayı dizisi için standart sapmayı hesaplayan bu yöntemi göz önünde bulundurun:

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/statistics.cs#05_StandardDeviation "Compute Standard Deviation")]

> [!NOTE]
> Bu örnekler düzeltilmemiş örnek standart sapması hesaplamak.
> Düzeltilmiş örnek standart sapma formülü, `Average` uzantı yönteminin yaptığı gibi, kareli farklılıkların toplamını N yerine (N-1) ortalamasından böler. Standart sapma için bu formüller arasındaki farklar hakkında daha fazla bilgi için bir istatistik metnine başvurun.

Önceki kod standart sapma için ders kitabı formülü izler. Doğru cevabı üretiyor, ama verimsiz bir uygulama. Bu yöntem sırayı iki kez sıralar: Bir kez ortalamaüretmek için, ve bir kez ortalama farkı nın kare ortalamasını üretmek için.
(LINQ sorgularının tembelce değerlendirildiğini unutmayın, bu nedenle bu farkların ortalaması ve ortalaması arasındaki farkların hesaplanması yalnızca bir numaralandırma yapar.)

Sıranın yalnızca bir numaralandırmasını kullanarak standart sapmayı hesaplayan alternatif bir formül vardır.  Bu hesaplama, sırayı sıralarken iki değer üretir: dizideki tüm öğelerin toplamı ve karedeki her değerin toplamı:

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/statistics.cs#06_SumOfSquaresFormula "Compute Standard Deviation using the sum of squares")]

Bu sürüm, diziyi tam olarak bir kez sıralar. Ama bu yeniden kullanılabilir bir kod değil. Çalışmaya devam ettikçe, birçok farklı istatistiksel hesaplamanın dizideki öğe sayısını, sıranın toplamını ve sıranın karelerinin toplamını kullandığını göreceksiniz. Bu yöntemi yeniden düzenlemeyi ve bu değerlerin üçünü de üreten bir yardımcı program yöntemi yazalım. Her üç değer bir tuple olarak döndürülebilir.

Numaralandırma sırasında hesaplanan üç değer bir tuple'da depolansın diye bu yöntemi güncelleştirelim. Bu sürüm oluşturur:

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/statistics.cs#07_TupleVersion "Refactor to use tuples")]

Visual Studio'nun Refactoring desteği, çekirdek istatistiklerinin işlevselliğini özel bir yönteme dönüştürmeyi kolaylaştırır. Bu size `private static` `Sum`üç değer , , `SumOfSquares`ve `Count`: tuple türü döndüren bir yöntem verir

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/statistics.cs#08_TupleMethodVersion "After extracting utility method")]

Dil, elle birkaç hızlı düzenleme yapmak istiyorsanız, kullanabileceğiniz birkaç seçenek daha sağlar. İlk olarak, `var` `ComputeSumAndSumOfSquares` yöntem çağrısından tuple sonucunu açmak için bildirimi kullanabilirsiniz. Ayrıca `ComputeSumAndSumOfSquares` yöntem içinde üç ayrı değişken oluşturabilirsiniz. Son sürüm aşağıdaki kodda gösterilir:

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/statistics.cs#09_CleanedTupleVersion "After final cleanup")]

Bu son sürüm, bu üç değere veya bunların herhangi bir alt kümesine ihtiyaç duyan herhangi bir yöntem için kullanılabilir.

Dil, bu tuple returning yöntemleriöğelerinin adlarını yönetmede diğer seçenekleri destekler.

Alan adlarını iade değer bildiriminden kaldırabilir ve adsız bir tuple döndürebilirsiniz:

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

Bu tuple alanları , `Item1` `Item2`, `Item3`ve .
Yöntemlerden döndürülen tuples öğelerine anlamsal adlar sağlamanız önerilir.

Tuples yararlı olabilir başka bir deyim linq sorguları yazarken. Son öngörülen sonuç genellikle seçili nesnelerin özelliklerinin bazılarını içerir, ancak tümü içermez.

Sorgunun sonuçlarını geleneksel olarak anonim bir tür olan nesneler dizisine yansıtın. Bu, öncelikle anonim türleri uygun bir yöntem için dönüş türünde adlandırılamaz çünkü birçok sınırlamalar sundu. Alternatifler `object` kullanarak `dynamic` veya sonuç türü olarak önemli performans maliyetleri ile geldi.

Bir tuple türünden bir sırayı döndürmek kolaydır ve öğelerin adları ve türleri derleme zamanında ve IDE araçları aracılığıyla kullanılabilir.
Örneğin, bir ToDo uygulamasını düşünün. Yapılacaklar listesinde tek bir girişi temsil etmek için aşağıdakilere benzer bir sınıf tanımlayabilirsiniz:

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/projectionsample.cs#14_ToDoItem "To Do Item")]

Mobil uygulamalarınız, yalnızca başlığı görüntüleyen geçerli ToDo öğelerinin kompakt bir biçimini destekleyebilir. Bu LINQ sorgusu yalnızca kimlik ve başlık içeren bir projeksiyon yapacak. Tuples bir dizi döndüren bir yöntem iyi tasarım ifade eder:

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/projectionsample.cs#15_QueryReturningTuple "Query returning a tuple")]

> [!NOTE]
> C# 7.1'de, tuple projeksiyonları, adlandırılmış tuples'ı anonim türlerdeki özellik adlandırmasına benzer bir şekilde öğeleri kullanarak oluşturmanıza olanak tanır. Yukarıdaki kodda, `select` sorgu projeksiyonundaki deyim, öğeleri `ID` olan bir `Title`tuple oluşturur ve .

Adlandırılmış tuple imzanın bir parçası olabilir. Derleyici ve IDE araçlarının sonucu doğru kullandığınızı statik olarak denetlemesini sağlar. Adlandırılmış tuple da sonuçları ile çalışmak için yansıma veya dinamik bağlama gibi pahalı çalışma süresi özellikleri kullanmaya gerek yoktur, böylece statik türü bilgileri taşır.

## <a name="deconstruction"></a>Yapısızlaştırma

Bir yöntemle döndürülen tuple'ı *dekonstrükte ederek* bir tuple'daki tüm öğeleri kaldırabilirsiniz. Tuples deconstructing için üç farklı yaklaşım vardır.  İlk olarak, tuple'daki öğelerin her biri için ayrı değişkenler oluşturmak için parantez içindeki her alanın türünü açıkça bildirebilirsiniz:

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/statistics.cs#10_Deconstruct "Deconstruct")]

Ayrıca, parantez dışındaki `var` anahtar sözcüğü kullanarak bir tuple'daki her alan için örtülü olarak yazılan değişkenleri de bildirebilirsiniz:

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/statistics.cs#11_DeconstructToVar "Deconstruct to Var")]

Anahtar kelimeyi `var` parantez içindeki değişken bildirimlerin herhangi biriyle veya tümüyle kullanmak da yasaldır.

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```

Tuple'daki her alan aynı türe sahip olsa bile, parantez dışında belirli bir tür kullanamazsınız.

Varolan bildirimlerle tuples'ı da çözebilirsiniz:

```csharp
public class Point
{
    public int X { get; set; }
    public int Y { get; set; }

    public Point(int x, int y) => (X, Y) = (x, y);
}
```

> [!WARNING]
> Varolan bildirimleri parantez içindeki bildirimlerle karıştıramazsınız. Örneğin, aşağıdakiizin verilmez: `(var x, y) = MyMethod();`. Bu hata CS8184 üretir, çünkü *x* parantez içinde bildirilir ve *y* daha önce başka bir yerde bildirilir.

### <a name="deconstructing-user-defined-types"></a>Kullanıcı tanımlı türleri deconstructing

Herhangi bir tuple türü yukarıda gösterildiği gibi dekonstrüktülüolabilir. Ayrıca, kullanıcı tarafından tanımlanan herhangi bir türde (sınıflar, yapılar ve hatta arabirimler) yapısızlaştırmayı etkinleştirmek de kolaydır.

Tür yazarı, türü oluşturan `Deconstruct` veri öğelerini temsil eden `out` herhangi bir sayıda değişkene değer atayabilen bir veya daha fazla yöntem tanımlayabilir. Örneğin, aşağıdaki `Person` tür, bir `Deconstruct` kişi nesnesini ilk adı ve soyadını temsil eden öğelere dönüştüren bir yöntem tanımlar:

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/person.cs#12_TypeWithDeconstructMethod "Type with a deconstruct method")]

Deconstruct yöntemi, atamayı `Person` bir den iki dizeye kadar, aşağıdakileri `FirstName` ve `LastName` özellikleri temsil eden şekilde sağlar:

[!code-csharp[Deconstruct Type](../../samples/snippets/csharp/tuples/program.cs#12A_DeconstructType "Deconstruct a class type")]

Yazmadığınız türler için bile yapısızlaştırmayı etkinleştirebilirsiniz.
Yöntem, `Deconstruct` bir nesnenin erişilebilir veri üyelerini paketleyen bir uzantı yöntemi olabilir. Aşağıdaki örnekte, `Student` `Person` türden türetilen bir tür ve `Student` bir üç değişkene ayıran bir `FirstName`uzantı yöntemi gösterilmektedir, ", `LastName`" ve : `GPA`

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/person.cs#13_ExtensionDeconstructMethod "Type with a deconstruct extension method")]

Bir `Student` nesnenin artık `Deconstruct` iki erişilebilir yöntemi `Student` vardır: türler için `Person` bildirilen uzantı yöntemi ve türün üyesi. Her ikisi de kapsamdadır ve `Student` bu, a'nın iki değişken veya üç değişkene dönüştürülmesini sağlar.
Bir öğrenciyi üç değişkene atarsanız, ad, soyad ve genel not ortalaması döndürülür. Bir öğrenciyi iki değişkene atarsanız, yalnızca ad ve soyadı döndürülür.

[!code-csharp[Deconstruct extension method](../../samples/snippets/csharp/tuples/program.cs#13A_DeconstructExtension "Deconstruct a class type using an extension method")]

Bir sınıf veya sınıf `Deconstruct` hiyerarşisinde birden çok yöntemi tanımlarken dikkatli olmalısınız. Aynı `Deconstruct` sayıda `out` parametreye sahip birden çok yöntem hızla belirsizliklere neden olabilir. Arayanlar istenilen `Deconstruct` yöntemi kolayca arayamayabilir.

Bu örnekte, belirsiz bir arama için `Deconstruct` en `Person` az şans vardır, `Deconstruct` çünkü `Student` yöntem iki çıkış parametreye sahiptir ve yöntem üçtür.

Dekonstrüksiyon operatörleri eşitliği test etmeye katılmaz. Aşağıdaki örnek derleyici hatası CS0019 oluşturur:

```csharp
Person p = new Person("Althea", "Goodwin");
if (("Althea", "Goodwin") == p)
    Console.WriteLine(p);
```

Yöntem `Deconstruct` nesneyi `Person` `p` iki dize içeren bir tuple dönüştürebilir, ancak eşitlik testleri bağlamında geçerli değildir.

## <a name="tuples-as-out-parameters"></a>Çıkış parametreleri olarak Tuples

Tuples dışarı parametreleri *kendileri*olarak kullanılabilir. [Yapısızlaştırma](#deconstruction) bölümünde daha önce bahsedilen herhangi bir belirsizlik ile karıştırılmamalıdır. Yöntem çağrısında yalnızca tuple'ın şeklini açıklamanız gerekir:

[!code-csharp[TuplesAsOutParameters](~/samples/snippets/csharp/tuples/program.cs#01_TupleAsOutVariable "Tuples as out parameters")]

Alternatif olarak, [_adsız_](#named-and-unnamed-tuples) bir tuple kullanabilirsiniz `Item1` ve `Item2`alanları bakın ve:

```csharp
dict.TryGetValue(2, out (int, string) pair);
// ...
Console.WriteLine($"{pair.Item1}: {pair.Item2}");
```

## <a name="conclusion"></a>Sonuç

Adlandırılmış tuples için yeni dil ve kitaplık desteği, birden çok öğe depolayan ancak davranışları tanımlamayan, sınıflar ve yapılar gibi veri yapıları kullanan tasarımlarla çalışmayı çok daha kolay hale getirir. Bu tür için tuples kullanmak kolay ve özlü. Daha ayrıntılı `class` veya `struct` sözdizimi kullanarak yazar türlerine gerek kalmadan statik tür denetiminin tüm avantajlarından yararlanırsınız. Buna rağmen, onlar en yararlı olan `private`yardımcı `internal`yöntemleri için yararlıdır , ya da . Ortak yöntemleriniz birden `class` çok `struct` öğeiçeren bir değer döndürdüğünde kullanıcı tanımlı türler oluşturun veya türleri oluşturun.
