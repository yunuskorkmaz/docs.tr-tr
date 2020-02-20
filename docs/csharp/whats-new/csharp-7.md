---
title: C# 7,0 C# kılavuzundaki yenilikler
description: C# Dilin sürüm 7,0 ' deki yeni özelliklere genel bakış alın.
ms.date: 02/20/2019
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: a6ac5c00ceb2ce8e5e56e2a86a8cde937d5108e2
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448640"
---
# <a name="whats-new-in-c-70"></a>C# 7,0 sürümündeki yenilikler

C#7,0, C# dile bir dizi yeni özellik ekler:

- [`out` değişkenleri](#out-variables)
  - `out` değerlerini, kullanıldıkları yöntemin bağımsız değişkeni olarak satır içi olarak bildirebilirsiniz.
- [Demetler](#tuples)
  - Birden çok ortak alan içeren hafif, adlandırılmamış türler oluşturabilirsiniz. Derleyiciler ve IDE araçları bu türlerin semantiğini anlayın.
- [Atılanlar](#discards)
  - Atama, atanan değer hakkında endişelenmezseniz atamalar içinde kullanılan geçici, salt yazılır değişkenlerdir. Bunlar, tanımlama grupları ve Kullanıcı tanımlı türler oluştururken ve `out` parametreleriyle Yöntemler çağrılırken faydalıdır.
- [Desen Eşleştirme](#pattern-matching)
  - Bu türlerin üyelerinin rastgele türlerini ve değerlerini temel alarak dallanma mantığı oluşturabilirsiniz.
- [Yereller ve döndürü `ref`](#ref-locals-and-returns)
  - Yöntem yerel değişkenleri ve dönüş değerleri diğer depolamaya başvuru olabilir.
- [Yerel Işlevler](#local-functions)
  - Kendi kapsamını ve görünürlüğünü sınırlamak için işlevleri diğer işlevlerde iç içe geçirebilirsiniz.
- [Daha fazla ifade-Bodied Üyeler](#more-expression-bodied-members)
  - İfadeler kullanılarak yazılabilir üyelerin listesi artmıştır.
- [`throw` Ifadeleri](#throw-expressions)
  - `throw` bir deyimiydi, daha önce izin verilmeyen kod yapılarında özel durumlar oluşturabilirsiniz.
- [Genelleştirilmiş zaman uyumsuz dönüş türleri](#generalized-async-return-types)
  - `async` değiştiricisi ile belirtilen Yöntemler `Task` ve `Task<T>`ek olarak diğer türleri döndürebilir.
- [Sayısal sabit değer sözdizimi geliştirmeleri](#numeric-literal-syntax-improvements)
  - Yeni belirteçler Sayısal sabitler için okunabilirliği geliştirir.

Bu makalenin geri kalanında her özelliğe bir genel bakış sunulmaktadır. Her bir özellik için, arkasında yatan bir düşünme olduğunu öğrenirsiniz. Söz dizimini öğrenirsiniz. Ortamınızdaki bu özellikleri, `dotnet try` genel aracını kullanarak inceleyebilirsiniz:

1. [DotNet-TRY](https://github.com/dotnet/try/blob/master/README.md#setup) küresel aracını yükler.
1. [DotNet/TRY-Samples](https://github.com/dotnet/try-samples) deposunu kopyalayın.
1. *TRY-Samples* deposu için geçerli dizini *csharp7* alt dizinine ayarlayın.
1. `dotnet try` öğesini çalıştırın.

## <a name="out-variables"></a>`out` değişkenleri

`out` parametrelerini destekleyen mevcut sözdizimi bu sürümde geliştirildi. Artık, ayrı bir bildirim bildirimi yazmak yerine bir yöntem çağrısının bağımsız değişken listesinde `out` değişkenlerini bildirebilirsiniz:

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

Yukarıda gösterildiği gibi, açıklık için `out` değişkeninin türünü belirtmek isteyebilirsiniz. Ancak, dil örtük olarak yazılmış bir yerel değişken kullanmayı destekler:

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

- Kodu daha kolay okunabilir.
  - Yukarıdaki diğer bir satırda değil, kullandığınız yerde çıkış değişkenini bildirirsiniz.
- İlk değer atamaya gerek yoktur.
  - Bir yöntem çağrısında kullanıldığı `out` değişkenini bildirerek, atanmadan önce onu kullanamazsınız.

## <a name="tuples"></a>Demetler

C#, tasarım amacını açıklamak için kullanılan sınıflar ve yapılar için zengin bir sözdizimi sağlar. Ancak bazen zengin söz dizimi çok az avantajlı ek iş gerektirir. Genellikle birden fazla veri öğesi içeren basit bir yapıya ihtiyacı olan Yöntemler yazabilirsiniz. Bu *senaryoları desteklemek* için, ' ye C#eklenmiştir. Tanımlama grupları, veri üyelerini temsil etmek için birden çok alan içeren hafif veri yapılarıdır.
Alanlar doğrulanmaz ve kendi yöntemlerinizi tanımlayamazsınız

> [!NOTE]
> Tanımlama grupları 7,0 'den C# önce kullanılabilir, ancak verimsiz ve dil desteği yoktu.
> Bu, demet öğelerine yalnızca `Item1`, `Item2` vb. olarak başvurulabilen anlamına gelir. C#7,0, tanımlama grupları için dil desteğini tanıtır ve bu, yeni, daha verimli demet türleri kullanarak bir kayıt düzeni alanları için anlamsal adlar sağlar.

Her üyeye bir değer atayarak ve isteğe bağlı olarak tanımlama grubu üyelerinin her birine anlamsal adlar sağlayarak bir tanımlama grubu oluşturabilirsiniz:

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

`namedLetters` kayıt düzeni `Alpha` ve `Beta`olarak adlandırılan alanları içerir. Bu adlar yalnızca derleme sırasında bulunur ve korunmaz, örneğin, çalışma zamanında yansıma kullanarak tanımlama grubu incelenirken.

Tanımlama grubu atamasında, atamanın sağ tarafındaki alanların adlarını da belirtebilirsiniz:

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

Bir yöntemden döndürülen bir tanımlama grubunun üyelerinin paketini kaldırmak istediğiniz zamanlar olabilir.  Bu, kayıt grubundaki her bir değer için ayrı değişkenler bildirerek yapabilirsiniz. Bu paketten *çıkarılması* , kayıt düzeninin kaldırılması olarak adlandırılır:

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

Ayrıca, .NET 'teki herhangi bir tür için benzer bir deme sağlayabilirsiniz. Sınıfının bir üyesi olarak bir `Deconstruct` yöntemi yazarsınız. Bu `Deconstruct` yöntemi, ayıklamak istediğiniz her bir özellik için bir dizi `out` bağımsız değişken sağlar. `X` ve `Y` koordinatlarını çıkaran bir Deconstructor yöntemi sağlayan bu `Point` sınıfını göz önünde bulundurun:

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

Bir tanımlama grubu `Point` atayarak tek tek alanları ayıklayabilirsiniz:

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

Tanımlama grupları [makalesindeki](../tuples.md)tanımlama grupları hakkında ayrıntılı bilgi edinebilirsiniz.

## <a name="discards"></a>Atılanlar

Genellikle, bir tanımlama grubu oluştururken veya `out` parametrelerle bir yöntemi çağırırken, değeri ilgilenmediğiniz ve kullanmayı düşünmediğiniz bir değişken tanımlamaya zorlanır. C#Bu senaryoyu işlemek için *atma* desteği ekler. Bir atma, adı `_` (alt çizgi karakteri) olan salt yazılır bir değişkendir; atmayı planladığınız tüm değerleri tek bir değişkene atayabilirsiniz. Bir atma atanmamış değişken gibidir; atama ifadesinden ayrı olarak, atma kodda kullanılamaz.

Atma, aşağıdaki senaryolarda desteklenir:

- Tanımlama grupları veya Kullanıcı tanımlı türler kaldırılıyor.
- [Out](../language-reference/keywords/out-parameter-modifier.md) parametreleri ile Yöntemler çağrılırken.
- WITH ve [Switch](../language-reference/keywords/switch.md) deyimleriyle bir kalıp [](../language-reference/keywords/is.md) eşleştirme işleminde.
- Bir atamanın değerini bir atma olarak açıkça tanımlamak istediğinizde tek başına tanımlayıcı olarak.

Aşağıdaki örnek, iki farklı yıl için bir şehir için veri içeren 6 demet döndüren bir `QueryCityDataForYears` yöntemi tanımlar. Örnekteki yöntem çağrısı yalnızca yöntemi tarafından döndürülen iki popülasyon değeriyle ilgilidir ve bu nedenle, kayıt düzeni oluşturulduğunda, kayıt düzeninde kalan değerleri atma olarak değerlendirir.

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Daha fazla bilgi için bkz. [atma](../discards.md).

## <a name="pattern-matching"></a>Desen eşleştirme

*Model eşleştirme* , nesne türünden farklı özelliklerde Yöntem gönderimi uygulamanıza olanak sağlayan bir özelliktir. Büyük olasılıkla nesne türüne göre Yöntem gönderimi hakkında zaten bilgi sahibisiniz. Nesne odaklı programlamada, sanal ve geçersiz kılma yöntemleri, nesne türünü temel alarak yöntem gönderme uygulamak için dil sözdizimi sağlar. Temel ve türetilmiş sınıflar farklı uygulamalar sağlar.
Desen eşleştirme ifadeleri, devralma hiyerarşisi aracılığıyla ilgili olmayan türler ve veri öğeleri için benzer dağıtım düzenlerini kolayca uygulayabileceğiniz şekilde bu kavramı genişletir.

Model eşleştirme `is` ifadeleri ve `switch` ifadelerini destekler. Her biri, nesnenin aranan düzene karşılayıp karşılamadığını tespit etmek için bir nesne ve özelliklerini inceleyerek sağlar. Modele ek kurallar belirtmek için `when` anahtar sözcüğünü kullanırsınız.

`is` deseninin ifadesi, bir nesneyi türü hakkında sorgulamak ve sonucu bir yönergede atamak için tanıdık [`is` işlecini](../language-reference/keywords/is.md#pattern-matching-with-is) genişletir. Aşağıdaki kod, bir değişkenin `int`olup olmadığını denetler ve varsa geçerli Sum 'a ekler:

```csharp
if (input is int count)
    sum += count;
```

Önceki küçük örnek `is` ifadeye yönelik geliştirmeleri gösterir. Aynı zamanda değer türlerine ve başvuru türlerine karşı test edebilirsiniz ve başarılı sonucu doğru türdeki yeni bir değişkene atayabilirsiniz.

Anahtar eşleştirme ifadesinde, zaten C# dilin bir parçası olan `switch` deyimine göre tanıdık bir sözdizimi vardır. Güncelleştirilmiş switch ifadesinin çeşitli yeni yapıları vardır:

- `switch` ifadesinin yöneten türü artık, bu türlerden birine karşılık gelen tamsayı türleri, `Enum` türleri, `string`veya null olabilen bir türle sınırlı değildir. Herhangi bir tür kullanılabilir.
- Her `case` etiketinde `switch` ifadesinin türünü test edebilirsiniz. `is` ifadesinde olduğu gibi, bu türe yeni bir değişken atayabilirsiniz.
- Bu değişkende daha fazla test koşullarına `when` yan tümce ekleyebilirsiniz.
- `case` etiketlerinin sırası artık önemlidir. Eşleştirilecek ilk dal yürütülür; diğerleri atlanır.

Aşağıdaki kod bu yeni özellikleri göstermektedir:

```csharp
public static int SumPositiveNumbers(IEnumerable<object> sequence)
{
    int sum = 0;
    foreach (var i in sequence)
    {
        switch (i)
        {
            case 0:
                break;
            case IEnumerable<int> childSequence:
            {
                foreach(var item in childSequence)
                    sum += (item > 0) ? item : 0;
                break;
            }
            case int n when n > 0:
                sum += n;
                break;
            case null:
                throw new NullReferenceException("Null found in sequence");
            default:
                throw new InvalidOperationException("Unrecognized type");
        }
    }
    return sum;
}
```

- `case 0:` tanıdık sabit bir modeldir.
- `case IEnumerable<int> childSequence:` bir tür deseninin.
- `case int n when n > 0:`, ek `when` koşulunun bulunduğu bir tür modelidir.
- `case null:` null bir modeldir.
- `default:`, bilinen varsayılan durumdur.

[' De C#örüntüme ](../pattern-matching.md)göre desenler eşleştirmesi hakkında daha fazla bilgi edinebilirsiniz.

## <a name="ref-locals-and-returns"></a>Ref Yereller ve geri dönüşler

Bu özellik, tarafından kullanılan ve başka bir yerde tanımlanan değişkenlere başvuru döndüren algoritmaların yapılmasını sağlar. Bir örnek büyük matrislerle çalışıyor ve belirli özelliklere sahip tek bir konum buluyor. Aşağıdaki yöntem, matriste bu depolama için bir **başvuru** döndürür:

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

Aşağıdaki kodda gösterildiği gibi, dönüş değerini bir `ref` olarak bildirebilir ve matriste bu değeri değiştirebilirsiniz:

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/Program.cs#AssignRefReturn "Assign ref return")]

C# Dil, `ref` yerelleri yanlış kullanmanızı ve şunu döndürdüğünü koruyan çeşitli kurallara sahiptir:

- Yöntem imzasına ve bir yöntemindeki tüm `return` deyimlerine `ref` anahtar sözcüğünü eklemeniz gerekir.
  - Bu, yöntem boyunca başvuruya göre döndürülen yöntemi temizler.
- Bir `ref return` bir değer değişkenine veya bir `ref` değişkenine atanabilir.
  - Çağıran, dönüş değerinin kopyalanıp kopyalanmadığını denetler. Dönüş değerini atarken `ref` değiştiricinin atlanması, çağıranın depolama için bir başvuru değil, değer kopyasının istediğini gösterir.
- Bir `ref` yerel değişkenine standart bir yöntem dönüş değeri atayamazsınız.
  - Bu, `ref int i = sequence.Count();` gibi deyimlere izin vermez
- Ömrü yöntemi yürütme ötesinde genişlemeyen bir değişkene `ref` döndüremez.
  - Bu, yerel bir değişkene veya benzer kapsama sahip bir değişkene bir başvuru döndüremeyeceğiniz anlamına gelir.
- `ref` Yereller ve geri dönüş, zaman uyumsuz yöntemlerle kullanılamaz.
  - Zaman uyumsuz yöntem döndürüldüğünde, derleyici başvurulan değişkenin son değerine ayarlandığını bilemez.

Ref Yereller ve ref işlevinin eklenmesi, değerleri kopyalamayı önleyerek veya birden çok kez başvuru işlemleri gerçekleştirerek daha etkili olan algoritmaların kullanılmasına izin verir.

Dönüş değerine `ref` eklemek, [kaynak ile uyumlu bir değişikdir](version-update-considerations.md#source-compatible-changes). Varolan kod derlenir, ancak ref dönüş değeri atandığında kopyalanır. Çağıranlar, döndürmeyi bir başvuru olarak depolamak için dönüş değeri için depolamayı `ref` yerel bir değişkene güncelleştirmelidir.

Daha fazla bilgi için bkz. [ref anahtar sözcüğü](../language-reference/keywords/ref.md) makalesi.

## <a name="local-functions"></a>Yerel işlevler

Sınıfların pek çok tasarımı yalnızca bir konumdan çağrılan yöntemleri içerir. Bu ek özel yöntemler her bir yöntemi küçük ve odaklanmış olarak tutar. *Yerel işlevler* , yöntemleri başka bir yöntem bağlamı içinde bildirmenize olanak tanır. Yerel işlevler, sınıfının okuyucularının, yerel yöntemin yalnızca bildirildiği bağlamdan çağrıldığını görmesini kolaylaştırır.

Yerel işlevler için iki yaygın kullanım durumu vardır: genel Yineleyici yöntemleri ve genel zaman uyumsuz yöntemler. Her iki yöntem türü, programcılar tarafından daha sonra oluşabilecek hataları raporlayan kodu oluşturur. Yineleyici metotlarda, tüm özel durumlar yalnızca döndürülen sırayı belirten kod çağrılırken izlenir. Zaman uyumsuz metotlarda, tüm özel durumlar yalnızca döndürülen `Task` beklediğinde gözlemlenir. Aşağıdaki örnek, yerel bir işlev kullanarak Yineleyici uygulamasından parametre doğrulamayı ayırmayı gösterir:

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

Bağımsız değişken doğrulamasından doğan özel durumların, zaman uyumsuz iş başlamadan önce oluşturulması için `async` yöntemlerle aynı teknik çalıştırılabilir:

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

> [!NOTE]
> Yerel işlevler tarafından desteklenen tasarımlardan bazıları *lambda ifadeleri*kullanılarak da gerçekleştirilebilir. Daha fazla bilgi için bkz [. yerel işlevler ve lambda ifadeleri](../local-functions-vs-lambdas.md).

## <a name="more-expression-bodied-members"></a>Daha fazla ifade-Bodied Üyeler

C#6 eklenen [ifade-üye işlevleri için Bodied Üyeler](csharp-6.md#expression-bodied-function-members) ve salt okunurdur özellikleri. C#7,0, ifade olarak uygulanabilecek izin verilen üyeleri genişletir. 7,0 C# ' de, *Özellikler* ve *Dizin oluşturucular*üzerinde *oluşturucular*, *sonlandırıcılar*ve `get` ve `set` erişimcileri uygulayabilirsiniz. Aşağıdaki kod, her birinin örneklerini gösterir:

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> Bu örnekte sonlandırıcısı gerekmez, ancak söz dizimini göstermek için gösterilir. Yönetilmeyen kaynakları serbest bırakmak gerekmedikçe, sınıfınıza sonlandırıcıyı uygulamamalısınız. Ayrıca, yönetilmeyen kaynakları doğrudan yönetmek yerine <xref:System.Runtime.InteropServices.SafeHandle> sınıfını kullanmayı göz önünde bulundurmanız gerekir.

İfade ile ilgili bu yeni konumlar C# dilin önemli bir kilometre taşını temsil eder: Bu özellikler, açık kaynaklı [Roslyn](https://github.com/dotnet/Roslyn) projesinde çalışan topluluk üyeleri tarafından uygulanmıştır.

Bir yöntemi bir ifade ile değiştirmek, [ikili uyumlu bir değişiklik](version-update-considerations.md#binary-compatible-changes)olur.

## <a name="throw-expressions"></a>Throw ifadeleri

' C#De, `throw` her zaman bir ifade olmuştur. `throw` ifade değil, bir deyim olduğundan, bunu kullanamadığı C# yapılar vardı. Bu dahil edilen Koşullu ifadeler, null birleştirme ifadeleri ve bazı lambda ifadeleri. İfade bululmuş üyelerin eklenmesi `throw` ifadelerin yararlı olacağı daha fazla konum ekler. Bu yapıtın herhangi birini yazmak için 7,0, C# [*throw ifadelerini*](../language-reference/keywords/throw.md#the-throw-expression)tanıtır.

Bu ek, daha fazla ifade tabanlı kod yazmayı kolaylaştırır. Hata denetimi için ek deyimlere ihtiyacınız yoktur.

## <a name="generalized-async-return-types"></a>Genelleştirilmiş zaman uyumsuz dönüş türleri

Zaman uyumsuz metotlardan `Task` bir nesne döndürmek, belirli yollarda performans sorunlarını ortaya çıkarabilir. `Task` bir başvuru türüdür, bu nedenle kullanmak bir nesne ayırmayı gösterir. `async` değiştiricisi ile belirtilen bir yöntemin önbelleğe alınmış bir sonuç döndürdüğü veya zaman uyumlu olarak tamamladığı durumlarda, ek ayırmalar kodun performans açısından kritik bölümlerinde önemli bir zaman maliyeti olabilir. Bu ayırmalar sıkı Döngülerde gerçekleşirse maliyetli hale gelebilir.

Yeni dil özelliği, zaman uyumsuz yöntem dönüş türlerinin `Task`, `Task<T>`ve `void`sınırlı olmadığı anlamına gelir. Döndürülen tür zaman uyumsuz düzene uymalıdır, yani bir `GetAwaiter` yöntemi erişilebilir olmalıdır. Tek bir somut örnek olarak, bu yeni dil özelliğinin kullanılması için `ValueTask` türü .NET 'e eklenmiştir:

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> <xref:System.Threading.Tasks.ValueTask%601> türünü kullanmak için NuGet paketini [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) eklemeniz gerekir.

Bu geliştirme, performans açısından kritik kodda `Task` ayırmayı önlemek için kitaplık yazarları için en yararlı seçenektir.

## <a name="numeric-literal-syntax-improvements"></a>Sayısal sabit değer sözdizimi geliştirmeleri

Hatalı okuma sayısal sabitleri, ilk kez okurken kodu daha zor hale getirir. Bit maskeleri veya diğer sembolik değerler yanlış anlama eğilimindedir. C#7,0, tasarlanan kullanım için en okunabilir biçimde sayı yazmak için iki yeni özellik içerir: *ikili sabit değerler*ve *basamak ayırıcıları*.

Bit maskeleri oluştururken veya bir sayının ikili gösteriminin en çok okunabilen kodu yaptığı durumlarda bu süreler için bu sayıyı binary olarak yazın:

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

Sabitin başındaki `0b`, sayının bir ikili sayı olarak yazıldığını gösterir. İkili sayılar uzun sürebilir, bu nedenle, ikili Sabitte yukarıda gösterildiği gibi, `_` rakam ayırıcısı olarak girerek bit desenlerini görmek daha kolaydır. Sayı ayırıcısı, sabit içinde herhangi bir yerde görünebilir. 10 tabanında numara için bu, binlerce ayırıcı olarak kullanılması yaygındır:

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

Rakam ayırıcısı `decimal`, `float`ve `double` türleriyle birlikte kullanılabilir:

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

Birlikte çalışarak, sayısal sabitleri çok daha okunaklı bir şekilde bildirebilirsiniz.
