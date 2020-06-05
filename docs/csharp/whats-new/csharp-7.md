---
title: C# 7,0 ' deki yenilikler-C# Kılavuzu
description: C# dilinin sürüm 7,0 ' deki yeni özelliklere genel bakış alın.
ms.date: 02/20/2019
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: e78d680e19709bf3dd854531d5d9f6b7d6464f49
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392255"
---
# <a name="whats-new-in-c-70"></a>C# 7.0 Yenilikleri

C# 7,0, C# diline bir dizi yeni özellik ekler:

- [`out`değişkenlerinin](#out-variables)
  - `out`Değerleri, kullanıldığı yönteme bağımsız değişken olarak satır içi olarak bildirebilirsiniz.
- [Demetler](#tuples)
  - Birden çok ortak alan içeren hafif, adlandırılmamış türler oluşturabilirsiniz. Derleyiciler ve IDE araçları bu türlerin semantiğini anlayın.
- [Atılanlar](#discards)
  - Atama, atanan değer hakkında endişelenmezseniz atamalar içinde kullanılan geçici, salt yazılır değişkenlerdir. Bunlar, tanımlama grupları ve Kullanıcı tanımlı türler oluştururken ve parametreleri ile Yöntemler çağrılırken faydalıdır `out` .
- [Desen Eşleştirme](#pattern-matching)
  - Bu türlerin üyelerinin rastgele türlerini ve değerlerini temel alarak dallanma mantığı oluşturabilirsiniz.
- [`ref`Yereller ve döndürür](#ref-locals-and-returns)
  - Yöntem yerel değişkenleri ve dönüş değerleri diğer depolamaya başvuru olabilir.
- [Yerel Işlevler](#local-functions)
  - Kendi kapsamını ve görünürlüğünü sınırlamak için işlevleri diğer işlevlerde iç içe geçirebilirsiniz.
- [Daha fazla ifade-Bodied Üyeler](#more-expression-bodied-members)
  - İfadeler kullanılarak yazılabilir üyelerin listesi artmıştır.
- [`throw`İfadelerde](#throw-expressions)
  - Daha önce izin verilmeyen kod yapılarında özel durumlar oluşturabilir, çünkü `throw` bir deyimidir.
- [Genelleştirilmiş zaman uyumsuz dönüş türleri](#generalized-async-return-types)
  - Değiştiriciyle belirtilen Yöntemler, `async` ve ' a ek olarak başka türler `Task` döndürebilir `Task<T>` .
- [Sayısal sabit değer sözdizimi geliştirmeleri](#numeric-literal-syntax-improvements)
  - Yeni belirteçler Sayısal sabitler için okunabilirliği geliştirir.

Bu makalenin geri kalanında her özelliğe bir genel bakış sunulmaktadır. Her bir özellik için, arkasında yatan bir düşünme olduğunu öğrenirsiniz. Söz dizimini öğrenirsiniz. Genel aracı kullanarak ortamınızdaki bu özellikleri keşfedebilirsiniz `dotnet try` :

1. [DotNet-TRY](https://github.com/dotnet/try/blob/master/README.md#setup) küresel aracını yükler.
1. [DotNet/TRY-Samples](https://github.com/dotnet/try-samples) deposunu kopyalayın.
1. *TRY-Samples* deposu için geçerli dizini *csharp7* alt dizinine ayarlayın.
1. `dotnet try` öğesini çalıştırın.

## <a name="out-variables"></a>`out`değişkenlerinin

`out`Bu sürümde, parametreleri destekleyen mevcut sözdizimi geliştirilmiştir. Artık `out` değişkenleri, ayrı bir bildirim bildirimi yazmak yerine bir yöntem çağrısının bağımsız değişken listesinde bildirebilirsiniz:

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

`out`Yukarıda gösterildiği gibi, açıklık için değişkenin türünü belirtmek isteyebilirsiniz. Ancak, dil örtük olarak yazılmış bir yerel değişken kullanmayı destekler:

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

- Kodu daha kolay okunabilir.
  - Yukarıdaki diğer bir satırda değil, kullandığınız yerde çıkış değişkenini bildirirsiniz.
- İlk değer atamaya gerek yoktur.
  - `out`Yöntemi bir yöntem çağrısında kullanıldığı yerde bildirerek, yanlışlıkla onu atanmadan kullanamazsınız.

## <a name="tuples"></a>Demetler

C#, tasarım amacını açıklamak için kullanılan sınıflar ve yapılar için zengin bir sözdizimi sağlar. Ancak bazen zengin söz dizimi çok az avantajlı ek iş gerektirir. Genellikle birden fazla veri öğesi içeren basit bir yapıya ihtiyacı olan Yöntemler yazabilirsiniz. Bu *senaryoları desteklemek* için C# ' ye eklenmiştir. Tanımlama grupları, veri üyelerini temsil etmek için birden çok alan içeren hafif veri yapılarıdır.
Alanlar doğrulanmaz ve kendi yöntemlerinizi tanımlayamazsınız

> [!NOTE]
> Tanımlama grupları C# 7,0 ' den önce kullanılabilir, ancak verimsiz ve dil desteği yoktu.
> Bu, demet öğelerine yalnızca olarak başvurulabilir `Item1` , `Item2` vb. anlamına gelir. C# 7,0, tanımlama grupları için dil desteğini tanıtır ve bu, yeni, daha verimli demet türleri kullanarak bir kayıt düzeni alanları için anlamsal adlar sağlar.

Her üyeye bir değer atayarak ve isteğe bağlı olarak tanımlama grubu üyelerinin her birine anlamsal adlar sağlayarak bir tanımlama grubu oluşturabilirsiniz:

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

`namedLetters`Kayıt düzeni ve olarak adlandırılan alanları içerir `Alpha` `Beta` . Bu adlar yalnızca derleme sırasında bulunur ve korunmaz, örneğin, çalışma zamanında yansıma kullanarak tanımlama grubu incelenirken.

Tanımlama grubu atamasında, atamanın sağ tarafındaki alanların adlarını da belirtebilirsiniz:

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

Bir yöntemden döndürülen bir tanımlama grubunun üyelerinin paketini kaldırmak istediğiniz zamanlar olabilir.  Bu, kayıt grubundaki her bir değer için ayrı değişkenler bildirerek yapabilirsiniz. Bu paketten *çıkarılması* , kayıt düzeninin kaldırılması olarak adlandırılır:

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

Ayrıca, .NET 'teki herhangi bir tür için benzer bir deme sağlayabilirsiniz. Bir `Deconstruct` yöntemi sınıfının bir üyesi olarak yazarsınız. Bu `Deconstruct` Yöntem `out` , ayıklamak istediğiniz her bir özellik için bir dizi bağımsız değişken sağlar. `Point`Ve koordinatlarını çıkaran bir Deconstructor yöntemi sağlayan bu sınıfı göz önünde `X` bulundurun `Y` :

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

Bir tanımlama grubu 'na atayarak tek tek alanları ayıklayabilirsiniz `Point` :

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

Tanımlama grupları [makalesindeki](../tuples.md)tanımlama grupları hakkında ayrıntılı bilgi edinebilirsiniz.

## <a name="discards"></a>Atılanlar

Genellikle, bir tanımlama grubu oluştururken veya parametreler ile bir yöntemi çağırırken `out` , değeri ilgilenmediğiniz ve kullanmayı planlamadığınız bir değişken tanımlamaya zorlanır. C#, bu senaryoyu işlemek için *atma* desteği ekler. Bir atma, adı `_` (alt çizgi karakteri) olan salt yazılır bir değişkendir; atmayı planladığınız tüm değerleri tek bir değişkene atayabilirsiniz. Bir atma atanmamış değişken gibidir; atama ifadesinden ayrı olarak, atma kodda kullanılamaz.

Atma, aşağıdaki senaryolarda desteklenir:

- Tanımlama grupları veya Kullanıcı tanımlı türler kaldırılıyor.
- [Out](../language-reference/keywords/out-parameter-modifier.md) parametreleri ile Yöntemler çağrılırken.
- WITH ve [Switch](../language-reference/keywords/switch.md) deyimleriyle bir kalıp [is](../language-reference/keywords/is.md) eşleştirme işleminde.
- Bir atamanın değerini bir atma olarak açıkça tanımlamak istediğinizde tek başına tanımlayıcı olarak.

Aşağıdaki örnek, `QueryCityDataForYears` iki farklı yıl için şehir için veri içeren 6 demet döndüren bir yöntemi tanımlar. Örnekteki yöntem çağrısı yalnızca yöntemi tarafından döndürülen iki popülasyon değeriyle ilgilidir ve bu nedenle, kayıt düzeni oluşturulduğunda, kayıt düzeninde kalan değerleri atma olarak değerlendirir.

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Daha fazla bilgi için bkz. [atma](../discards.md).

## <a name="pattern-matching"></a>Desen eşleştirme

*Model eşleştirme* , nesne türünden farklı özelliklerde Yöntem gönderimi uygulamanıza olanak sağlayan bir özelliktir. Büyük olasılıkla nesne türüne göre Yöntem gönderimi hakkında zaten bilgi sahibisiniz. Nesne odaklı programlamada, sanal ve geçersiz kılma yöntemleri, nesne türünü temel alarak yöntem gönderme uygulamak için dil sözdizimi sağlar. Temel ve türetilmiş sınıflar farklı uygulamalar sağlar.
Desen eşleştirme ifadeleri, devralma hiyerarşisi aracılığıyla ilgili olmayan türler ve veri öğeleri için benzer dağıtım düzenlerini kolayca uygulayabileceğiniz şekilde bu kavramı genişletir.

Model eşleştirme `is` , ifadeleri ve `switch` ifadeleri destekler. Her biri, nesnenin aranan düzene karşılayıp karşılamadığını tespit etmek için bir nesne ve özelliklerini inceleyerek sağlar. `when`Modele ek kurallar belirtmek için anahtar sözcüğünü kullanırsınız.

`is`Model ifadesi, bir nesneyi türü hakkında sorgulamak ve sonucu bir yönergede atamak için tanıdık [ `is` işleci](../language-reference/keywords/is.md#pattern-matching-with-is) genişletir. Aşağıdaki kod, bir değişkenin bir olduğunu denetler `int` ve varsa, geçerli Sum 'a ekler:

```csharp
if (input is int count)
    sum += count;
```

Önceki küçük örnek, ifadeye yönelik geliştirmeleri gösterir `is` . Aynı zamanda değer türlerine ve başvuru türlerine karşı test edebilirsiniz ve başarılı sonucu doğru türdeki yeni bir değişkene atayabilirsiniz.

Anahtar eşleşme ifadesi, `switch` C# dilinin zaten bir parçası olan bildirime göre tanıdık bir sözdizimine sahiptir. Güncelleştirilmiş switch ifadesinin çeşitli yeni yapıları vardır:

- Bir ifadenin yöneten türü `switch` artık, `Enum` `string` Bu türlerden birine karşılık gelen tamsayı türleri, türleri veya null olabilen bir türle sınırlı değildir. Herhangi bir tür kullanılabilir.
- `switch`Her etikette ifadenin türünü test edebilirsiniz `case` . İfadesinde olduğu gibi `is` , bu türe yeni bir değişken atayabilirsiniz.
- `when`O değişkende daha fazla test koşullarına bir yan tümce ekleyebilirsiniz.
- `case`Etiketlerin sırası artık önemlidir. Eşleştirilecek ilk dal yürütülür; diğerleri atlanır.

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

- `case 0:`tanıdık sabit bir örüntü.
- `case IEnumerable<int> childSequence:`bir tür deseninin.
- `case int n when n > 0:`, ek bir koşula sahip bir tür düzendir `when` .
- `case null:`null desenli bir değer.
- `default:`tanıdık varsayılan durumdur.

[C# ' de model eşleştirme](../pattern-matching.md)ile model eşleştirme hakkında daha fazla bilgi edinebilirsiniz.

## <a name="ref-locals-and-returns"></a>Ref Yereller ve geri dönüşler

Bu özellik, tarafından kullanılan ve başka bir yerde tanımlanan değişkenlere başvuru döndüren algoritmaların yapılmasını sağlar. Bir örnek büyük matrislerle çalışıyor ve belirli özelliklere sahip tek bir konum buluyor. Aşağıdaki yöntem, matriste bu depolama için bir **başvuru** döndürür:

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

`ref`Aşağıdaki kodda gösterildiği gibi, dönüş değerini bir olarak bildirebilir ve matriste bu değeri değiştirebilirsiniz:

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/Program.cs#AssignRefReturn "Assign ref return")]

C# dili, yerelleri yanlış kullanmanızı ve şunu döndürdüğünü koruyan çeşitli kurallara sahiptir `ref` :

- `ref`Anahtar sözcüğünü Yöntem imzasına ve `return` bir yöntemindeki tüm deyimlere eklemeniz gerekir.
  - Bu, yöntem boyunca başvuruya göre döndürülen yöntemi temizler.
- Bir `ref return` değer değişkenine veya bir `ref` değişkene atanabilir.
  - Çağıran, dönüş değerinin kopyalanıp kopyalanmadığını denetler. `ref`Dönüş değerini atarken değiştiricinin atlanması, çağıranın depolama için bir başvuru değil, değer kopyasının istediğini gösterir.
- Bir yerel değişkene standart bir yöntem dönüş değeri atayamazsınız `ref` .
  - Şunun gibi deyimler izin vermez`ref int i = sequence.Count();`
- `ref`Ömrü, yönteminin yürütülmesinden daha fazla genişlemeyen bir değişkene geri dönemez.
  - Bu, yerel bir değişkene veya benzer kapsama sahip bir değişkene bir başvuru döndüremeyeceğiniz anlamına gelir.
- `ref`Yereller ve geri dönüş, zaman uyumsuz yöntemlerle kullanılamaz.
  - Zaman uyumsuz yöntem döndürüldüğünde, derleyici başvurulan değişkenin son değerine ayarlandığını bilemez.

Ref Yereller ve ref işlevinin eklenmesi, değerleri kopyalamayı önleyerek veya birden çok kez başvuru işlemleri gerçekleştirerek daha etkili olan algoritmaların kullanılmasına izin verir.

`ref`Dönüş değerine ekleme, [kaynak ile uyumlu bir değişikdir](version-update-considerations.md#source-compatible-changes). Varolan kod derlenir, ancak ref dönüş değeri atandığında kopyalanır. Çağıranlar, döndürmeyi `ref` bir başvuru olarak depolamak için dönüş değeri için depolamayı yerel bir değişkene güncelleştirmelidir.

Daha fazla bilgi için bkz. [ref anahtar sözcüğü](../language-reference/keywords/ref.md) makalesi.

## <a name="local-functions"></a>Yerel işlevler

Sınıfların pek çok tasarımı yalnızca bir konumdan çağrılan yöntemleri içerir. Bu ek özel yöntemler her bir yöntemi küçük ve odaklanmış olarak tutar. *Yerel işlevler* , yöntemleri başka bir yöntem bağlamı içinde bildirmenize olanak tanır. Yerel işlevler, sınıfının okuyucularının, yerel yöntemin yalnızca bildirildiği bağlamdan çağrıldığını görmesini kolaylaştırır.

Yerel işlevler için iki yaygın kullanım durumu vardır: genel Yineleyici yöntemleri ve genel zaman uyumsuz yöntemler. Her iki yöntem türü, programcılar tarafından daha sonra oluşabilecek hataları raporlayan kodu oluşturur. Yineleyici metotlarda, tüm özel durumlar yalnızca döndürülen sırayı belirten kod çağrılırken izlenir. Zaman uyumsuz metotlarda, tüm özel durumlar yalnızca döndürülen geri beklendiğinde gözlemlenir `Task` . Aşağıdaki örnek, yerel bir işlev kullanarak Yineleyici uygulamasından parametre doğrulamayı ayırmayı gösterir:

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

`async`Bağımsız değişken doğrulamasından doğan özel durumların, zaman uyumsuz iş başlamadan önce oluşturulması için yöntemler ile aynı yöntem kullanılabilir:

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

> [!NOTE]
> Yerel işlevler tarafından desteklenen tasarımlardan bazıları *lambda ifadeleri*kullanılarak da gerçekleştirilebilir. Daha fazla bilgi için bkz [. yerel işlevler ve lambda ifadeleri](../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions).

## <a name="more-expression-bodied-members"></a>Daha fazla ifade-Bodied Üyeler

C# 6 ifadesi-üye işlevleri için [Bodied Üyeler](csharp-6.md#expression-bodied-function-members) ve salt okunurdur özellikleri eklendi. C# 7,0, ifade olarak uygulanabilecek izin verilen üyeleri genişletir. C# 7,0 ' de, *constructors* *finalizers* `get` `set` *Özellikler* ve *Dizin oluşturucular*üzerinde oluşturucular, sonlandırıcılar ve erişimciler uygulayabilirsiniz. Aşağıdaki kod, her birinin örneklerini gösterir:

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> Bu örnekte sonlandırıcısı gerekmez, ancak söz dizimini göstermek için gösterilir. Yönetilmeyen kaynakları serbest bırakmak gerekmedikçe, sınıfınıza sonlandırıcıyı uygulamamalısınız. Ayrıca, <xref:System.Runtime.InteropServices.SafeHandle> yönetilmeyen kaynakları doğrudan yönetmek yerine sınıfını kullanmayı göz önünde bulundurmanız gerekir.

İfade için bu yeni konumlar C# dili için önemli bir kilometre taşını temsil eder: Bu özellikler, açık kaynaklı [Roslyn](https://github.com/dotnet/Roslyn) projesinde çalışan topluluk üyeleri tarafından uygulanmıştır.

Bir yöntemi bir ifade ile değiştirmek, [ikili uyumlu bir değişiklik](version-update-considerations.md#binary-compatible-changes)olur.

## <a name="throw-expressions"></a>Throw ifadeleri

C# ' de `throw` her zaman bir ifade olmuştur. Bir `throw` ifade değil, bir deyim olduğundan, bunu kullanamadığı Için C# yapıları vardı. Bu dahil edilen Koşullu ifadeler, null birleştirme ifadeleri ve bazı lambda ifadeleri. İfade bululmuş üyelerin eklenmesi, ifadelerin yararlı olacağı daha fazla konum ekler `throw` . Bu yapıların herhangi birini yazmak için C# 7,0, [*throw ifadelerini*](../language-reference/keywords/throw.md#the-throw-expression)tanıtır.

Bu ek, daha fazla ifade tabanlı kod yazmayı kolaylaştırır. Hata denetimi için ek deyimlere ihtiyacınız yoktur.

## <a name="generalized-async-return-types"></a>Genelleştirilmiş zaman uyumsuz dönüş türleri

`Task`Zaman uyumsuz metotlardan bir nesne döndürmek, belirli yollarda performans sorunlarını ortaya çıkarabilir. `Task`bir başvuru türüdür, bu nedenle bu bir nesne ayırma anlamına gelir. Değiştirici ile belirtilen bir yöntemin `async` önbelleğe alınmış bir sonuç döndürdüğü veya zaman uyumlu olarak tamamladığı durumlarda, ek ayırmalar kodun performans açısından kritik bölümlerinde önemli bir zaman maliyeti olabilir. Bu ayırmalar sıkı Döngülerde gerçekleşirse maliyetli hale gelebilir.

Yeni dil özelliği, zaman uyumsuz yöntem dönüş türlerinin `Task` , ve ile sınırlı olmadığı anlamına gelir `Task<T>` `void` . Döndürülen türün zaman uyumsuz düzene uygun olması gerekir, yani bir `GetAwaiter` yönteme erişilebilir olması gerekir. Tek bir somut örnek olarak, `ValueTask` Bu yeni dil özelliğinin kullanılması için tür .net 'e eklenmiştir:

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> Türü kullanabilmek için NuGet paketini eklemeniz gerekir [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) <xref:System.Threading.Tasks.ValueTask%601> .

Bu geliştirme, en çok bir performans kritik kodunda ayırmayı önlemek için kitaplık yazarları için yararlıdır `Task` .

## <a name="numeric-literal-syntax-improvements"></a>Sayısal sabit değer sözdizimi geliştirmeleri

Hatalı okuma sayısal sabitleri, ilk kez okurken kodu daha zor hale getirir. Bit maskeleri veya diğer sembolik değerler yanlış anlama eğilimindedir. C# 7,0, tasarlanan kullanım için en okunabilir şekilde sayı yazmak üzere iki yeni özellik içerir: *ikili sabit değerler*ve *basamak ayırıcıları*.

Bit maskeleri oluştururken veya bir sayının ikili gösteriminin en çok okunabilen kodu yaptığı durumlarda bu süreler için bu sayıyı binary olarak yazın:

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

`0b`Sabitin başlangıcında, sayının bir ikili sayı olarak yazıldığını gösterir. İkili sayılar uzun sürebilir, bu nedenle, `_` ikili Sabitte yukarıda gösterildiği gibi, bir rakam ayırıcısı olarak girerek bit düzenlerini görmeyi daha kolay hale getirirsiniz. Sayı ayırıcısı, sabit içinde herhangi bir yerde görünebilir. 10 tabanında numara için bu, binlerce ayırıcı olarak kullanılması yaygındır:

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

Rakam ayırıcısı,, ve türleri ile birlikte kullanılabilir `decimal` `float` `double` :

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

Birlikte çalışarak, sayısal sabitleri çok daha okunaklı bir şekilde bildirebilirsiniz.
