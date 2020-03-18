---
title: C# 7.0'da Yenilikler - C# Rehberi
description: C# dilinin 7.0 sürümündeki yeni özellikler hakkında genel bir bakış alın.
ms.date: 02/20/2019
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: a6ac5c00ceb2ce8e5e56e2a86a8cde937d5108e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399695"
---
# <a name="whats-new-in-c-70"></a>C# 7.0 Yenilikleri

C# 7.0, C# diline bir dizi yeni özellik ekler:

- [`out`Değişken](#out-variables)
  - Değerleri, `out` kullanıldıkları yönteme bağımsız değişken olarak sıralı olarak bildirebilirsiniz.
- [Dizilerini](#tuples)
  - Birden çok ortak alan içeren hafif, adsız türler oluşturabilirsiniz. Derleyiciler ve IDE araçları bu tür anlambilimini anlar.
- [Atılanlar](#discards)
  - Atanan değer le ilgilenmediğiniz durumlarda atamalarda kullanılan geçici, yalnızca yazma değişkenleridir. Tuples ve kullanıcı tanımlı türleri deconstructing yanı sıra parametreleri ile `out` yöntemleri arama yaparken en yararlıdır.
- [Desen Eşleştirme](#pattern-matching)
  - Bu tür üyelerin rasgele türleri ve değerlerini temel alan dallanma mantığı oluşturabilirsiniz.
- [`ref`yerliler ve iadeler](#ref-locals-and-returns)
  - Yöntem yerel değişkenler ve iade değerleri diğer depolama referansları olabilir.
- [Yerel Fonksiyonlar](#local-functions)
  - Kapsamlarını ve görünürlüklerini sınırlamak için işlevleri diğer işlevlerin içine sokabilirsiniz.
- [Daha fazla ifade gövdeli üye](#more-expression-bodied-members)
  - İfadeler kullanılarak yazılabilir üye listesi büyüdü.
- [`throw`Ifa -de](#throw-expressions)
  - Bir deyim `throw` olduğu için daha önce izin verilmeyen kod yapılarında özel durumlar atabilirsiniz.
- [Genelleştirilmiş async dönüş türleri](#generalized-async-return-types)
  - Değiştirici ile bildirilen yöntemler ek olarak diğer `Task` `Task<T>`türleri döndürebilir ve . `async`
- [Sayısal gerçek sözdizimi geliştirmeleri](#numeric-literal-syntax-improvements)
  - Yeni belirteçler sayısal sabitler için okunabilirliği artırır.

Bu makalenin geri kalanı her özelliğin genel bir özetini sağlar. Her özellik için, bunun arkasındaki mantığı öğreneceksiniz. Sözdizimini öğreneceksin. `dotnet try` Bu özellikleri ortamınızda genel aracı kullanarak keşfedebilirsiniz:

1. [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global aracını yükleyin.
1. [Dotnet/try-samples](https://github.com/dotnet/try-samples) deposunu klonla.
1. *Deneme örnekleri* deposu için geçerli dizini *csharp7* alt dizinine ayarlayın.
1. `dotnet try` öğesini çalıştırın.

## <a name="out-variables"></a>`out`Değişken

Parametreleri destekleyen `out` varolan sözdizimi bu sürümde geliştirilmiştir. Artık ayrı `out` bir bildirim bildirimi yazmak yerine bir yöntem çağrısının bağımsız değişken listesinde değişkenleri bildirebilirsiniz:

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

Yukarıda gösterildiği gibi, netlik `out` için değişkenin türünü belirtmek isteyebilirsiniz. Ancak, dil örtülü olarak yazılan yerel değişkeni destekler:

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

- Kodu okumak daha kolaydır.
  - Dış değişkeni kullandığınız yerde bildirirsiniz, yukarıdaki başka bir satırda değil.
- Başlangıç değeri atamaya gerek yok.
  - Değişkeni `out` bir yöntem çağrısında kullanıldığı yeri beyan ederek, atanmadan önce yanlışlıkla kullanamazsınız.

## <a name="tuples"></a>Demetler

C#, tasarım amacınızı açıklamak için kullanılan sınıflar ve strüktler için zengin bir sözdizimi sağlar. Ama bazen bu zengin sözdizimi en az yararı ile ekstra çalışma gerektirir. Genellikle birden fazla veri öğesi içeren basit bir yapı gerektiren yöntemler yazabilirsiniz. Bu senaryoları desteklemek için *Tuples* C#'a eklendi. Tuples, veri üyelerini temsil edecek birden çok alan içeren hafif veri yapılarıdır.
Alanlar doğrulanmadı ve kendi yöntemlerinizi tanımlayamadığınız

> [!NOTE]
> Tuples C # 7.0 önce mevcut, ama verimsiz ve hiçbir dil desteği vardı.
> Bu, tuple öğelerinin yalnızca `Item1`"ve `Item2` benzeri" olarak başvurulabileceği anlamına geliyordu. C# 7.0, yeni, daha verimli tuple türleri kullanarak bir tuple alanları için anlamsal adlar sağlayan tuples için dil desteği sunar.

Her üyeye bir değer atayarak ve isteğe bağlı olarak tuple üyelerinin her birine anlamsal adlar sağlayarak bir tuple oluşturabilirsiniz:

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

Tuple `namedLetters` olarak `Alpha` adlandırılan alanları `Beta`içerir ve. Bu adlar yalnızca derleme zamanında bulunur ve örneğin çalışma zamanında yansımayı kullanarak tuple'ı incelerken korunmaz.

Bir tuple atamasında, atamanın sağ tarafındaki alanların adlarını da belirtebilirsiniz:

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

Bir yöntemden döndürülen bir tuple'ın üyelerini paketini açmak istediğiniz zamanlar olabilir.  Bunu, tuple'daki değerlerin her biri için ayrı değişkenler beyan ederek yapabilirsiniz. Bu unpackaging tuple *deconstructing* denir:

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

Ayrıca,.NET'teki herhangi bir tür için benzer bir yapısızlaştırma sağlayabilirsiniz. Sınıfın bir `Deconstruct` üyesi olarak bir yöntem yazarsınız. Bu `Deconstruct` yöntem, ayıklamak istediğiniz özelliklerin her biri için bir `out` bağımsız değişken kümesi sağlar. Bunları `Point` `X` ve `Y` koordinatları ayıklayan bir dekonstrüktör yöntemi sağlayan bu sınıfı düşünün:

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

Bir tuple'a bir `Point` a atayarak tek tek alanları ayıklayabilirsiniz:

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

[Tuples makalede tuples](../tuples.md)hakkında derinlemesine daha fazla bilgi edinebilirsiniz.

## <a name="discards"></a>Atılanlar

Genellikle bir tuple'ı dekonstrükte ederken veya parametreleri olan `out` bir yöntemi ararken, değerini önemsemeyen ve kullanmak istemediğiniz bir değişkeni tanımlamak zorunda kalırsınız. C# bu senaryoyu işlemek için *atılanlar* için destek ekler. Bir atma, yalnızca yazma yla `_` ilgili bir değişkendir ve adı (alt karakter) dir; tek bir değişkene atmayı istediğiniz tüm değerleri atayabilirsiniz. Bir atma atanmamış bir değişken gibidir; atama deyimi dışında, atama kodunda kullanılamaz.

Atılanlar aşağıdaki senaryolarda desteklenir:

- Tuples veya kullanıcı tanımlı türleri deconstructing zaman.
- Parametreleri [ile](../language-reference/keywords/out-parameter-modifier.md) yöntemleri ararken.
- Is [ve](../language-reference/keywords/is.md) [switch](../language-reference/keywords/switch.md) deyimleri ile eşleşen bir desen deseni.
- Bir atamanın değerini bir atama olarak açıkça tanımlamak istediğinizde bağımsız bir tanımlayıcı olarak.

Aşağıdaki örnek, iki `QueryCityDataForYears` farklı yıl için bir şehir için veri içeren bir 6-tuple döndüren bir yöntem tanımlar. Örnekteki yöntem çağrısı yalnızca yöntem tarafından döndürülen iki popülasyon değeriyle ilgilidir ve bu nedenle tuple'da kalan değerleri, tuple'ı yapısızleştirdiği zaman atar gibi davranır.

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Daha fazla bilgi için [bkz.](../discards.md)

## <a name="pattern-matching"></a>Desen eşleştirme

*Desen eşleştirme,* bir nesnenin türü dışındaki özellikler üzerinde yöntem gönderme uygulamanızı sağlayan bir özelliktir. Büyük olasılıkla bir nesnenin türüne göre yöntem gönderimi hakkında zaten aşinasınızdır. Nesne yönelimli programlamada, sanal ve geçersiz kılma yöntemleri, nesnenin türüne göre yöntem gönderme yöntemini uygulamak için dil sözdizimini sağlar. Taban ve Türetilmiş sınıflar farklı uygulamalar sağlar.
Desen eşleştirme ifadeleri, devralma hiyerarşisi aracılığıyla ilişkili olmayan türler ve veri öğeleri için benzer gönderme desenleri kolayca uygulayabilmeniz için bu kavramı genişletir.

Desen eşleştirme `is` ifadeleri `switch` ve ifadeleri destekler. Her nesne nin aranan deseni karşılayıp karşıladığını belirlemek için bir nesnenin ve özelliklerinin incelenmesini sağlar. Desene `when` ek kurallar belirtmek için anahtar sözcüğü kullanırsınız.

`is` Desen ifadesi, tanıdık [ `is` işleci,](../language-reference/keywords/is.md#pattern-matching-with-is) bir nesneyi türü hakkında sorgulamak ve sonucu tek bir yönergeyle atamak için genişletir. Aşağıdaki kod, bir değişkenin `int`,, eğer öyleyse, geçerli toplama ekleyip ekleninbileni denetler:

```csharp
if (input is int count)
    sum += count;
```

Önceki küçük `is` örnek, ifadedeki geliştirmeleri gösterir. Değer türlerinin yanı sıra başvuru türlerine karşı sınayabilir ve başarılı sonucu doğru türden yeni bir değişkene atayabilirsiniz.

Anahtar eşleşmesi ifadesi, C# dilinin `switch` zaten bir parçası olan deyimi temel alan tanıdık bir sözdizimine sahiptir. Güncelleştirilmiş anahtar deyimibirkaç yeni yapıya sahiptir:

- Bir `switch` ifadenin yönetim türü artık integral türleri, `Enum` türleri `string`veya bu türlerden birine karşılık gelen nullable türüyle sınırlı değildir. Herhangi bir tür kullanılabilir.
- Her `switch` `case` etiketteki ifade türünü sınayabilirsiniz. İfadede `is` olduğu gibi, bu türe yeni bir değişken atayabilirsiniz.
- Bu değişkendeki `when` diğer test koşullarına bir yan tümce ekleyebilirsiniz.
- Etiketlerin `case` sırası artık önemlidir. Eşleşen ilk dal yürütülür; diğerleri atlanır.

Aşağıdaki kod bu yeni özellikleri gösterir:

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

- `case 0:`tanıdık sabit desendir.
- `case IEnumerable<int> childSequence:`bir tür desenidir.
- `case int n when n > 0:`ek `when` bir koşul ile bir tür desendir.
- `case null:`null desendir.
- `default:`tanıdık varsayılan durumdur.

[C#'da Desen Eşleştirme'de](../pattern-matching.md)desen eşleştirme hakkında daha fazla bilgi edinebilirsiniz.

## <a name="ref-locals-and-returns"></a>Ref yerlileri ve döner

Bu özellik, başka bir yerde tanımlanan değişkenlere başvuru kullanan ve döndüren algoritmalar sağlar. Bir örnek, büyük matrisler ile çalışıyor ve belirli özelliklere sahip tek bir konum bulmaktır. Aşağıdaki yöntem matristeki depolama alanına bir **başvuru** döndürür:

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

İade değerini a `ref` olarak bildirebilir ve aşağıdaki kodda gösterildiği gibi matristeki bu değeri değiştirebilirsiniz:

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/Program.cs#AssignRefReturn "Assign ref return")]

C# dili, `ref` yerel halkı kötüye kullanmaktan koruyan çeşitli kurallara sahiptir ve geri döner:

- Yöntem imzasına `ref` ve yöntemdeki tüm `return` ifadelere anahtar kelime eklemeniz gerekir.
  - Bu yöntem, yöntem boyunca referans yoluyla döner açıkça yapar.
- A `ref return` bir değer değişkenine veya `ref` bir değişkene atanabilir.
  - Arayan, iade değerinin kopyalanıp kopyalanmadığını denetler. İade değerini `ref` atarken değiştiriciyi atamak, arayanın depolamaya bir başvuru değil, değerin bir kopyasını istediğini gösterir.
- `ref` Yerel bir değişkene standart yöntem iade değeri atayamazsınız.
  - Bu gibi ifadeler indasvesi`ref int i = sequence.Count();`
- Ömrü metodun yürütülmesinden öteye uzanamayan bir değişkene bir değişkeni `ref` döndüremezsiniz.
  - Bu, yerel bir değişkene veya benzer kapsama sahip bir değişkene başvuru veremezsiniz anlamına gelir.
- `ref`yerel ve döner async yöntemleri ile kullanılamaz.
  - Derleyici, async yöntemi döndüğünde başvurulan değişkenin son değerine ayarlandığını bilemiyor.

Ref locals ve ref returns eklenmesi, değerleri kopyalamaktan kaçınarak veya birden çok kez dereferencing işlemleri gerçekleştirerek daha verimli algoritmalar sağlar.

İade `ref` değerine [ekleme, kaynak uyumlu](version-update-considerations.md#source-compatible-changes)bir değişikliktir. Varolan kod derlenir, ancak atandığında ref iade değeri kopyalanır. Arayanların, iadeyi referans olarak depolamak için iade değeri depolama alanını yerel bir `ref` değişkene güncelleştirmeleri gerekir.

Daha fazla bilgi için [ref anahtar kelime](../language-reference/keywords/ref.md) makalesine bakın.

## <a name="local-functions"></a>Yerel işlevler

Sınıflar için birçok tasarım, yalnızca bir konumdan çağrılan yöntemleri içerir. Bu ek özel yöntemler her yöntemi küçük ve odaklanmış tutar. *Yerel işlevler,* yöntemleri başka bir yöntemin bağlamında bildirmenizi sağlar. Yerel işlevler, sınıf okuyucularının yerel yöntemin yalnızca beyan edildiği bağlamdan çağrıldığını görmesini kolaylaştırır.

Yerel işlevler için iki yaygın kullanım nedeni vardır: genel yineleyici yöntemleri ve genel async yöntemleri. Her iki yöntem türü de, programcıların beklediğinden daha geç hata bildiren kod oluşturur. Yineleme yöntemlerinde, yalnızca döndürülen sırayı sıralayan kodu ararken herhangi bir özel durum gözlenir. Async yöntemleri, herhangi bir özel durum `Task` yalnızca döndürülen bekleniyor gözlenir. Aşağıdaki örnek, parametre doğrulaması nın yerel bir işlev kullanılarak yineleyici uygulamasından ayırılmasını gösterir:

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

Aynı teknik, bağımsız `async` değişken doğrulamasından kaynaklanan özel durumların asenkron çalışma başlamadan önce atılmasını sağlamak için yöntemlerle kullanılabilir:

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

> [!NOTE]
> Yerel fonksiyonlar tarafından desteklenen bazı tasarımlar da *lambda ifadeleri*kullanılarak gerçekleştirilebilir. Daha fazla bilgi için, [yerel işlevler vs lambda ifadeler](../local-functions-vs-lambdas.md)bakın.

## <a name="more-expression-bodied-members"></a>Daha fazla ifade gövdeli üye

C# 6, üye işlevler ve salt okunur özellikler için [ifade gövdeli üyeleri](csharp-6.md#expression-bodied-function-members) tanıttı. C# 7.0, ifade olarak uygulanabilen izin verilen üyeleri genişletir. C# 7.0'da, *özellikler* ve *dizin*oluşturucular, *sonlandırıcılar*ve `get` `set` erişimciler uygulayabilirsiniz. *constructors* Aşağıdaki kod her birinin örneklerini gösterir:

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> Bu örnek bir sonlandırıcı gerekmez, ancak sözdizimini göstermek için gösterilir. Yönetilmeyen kaynakları serbest bırakmak gerekli olmadıkça sınıfınızda bir sonlandırıcı uygulamamalısınız. Ayrıca, yönetilmeyen <xref:System.Runtime.InteropServices.SafeHandle> kaynakları doğrudan yönetmek yerine sınıfı kullanmayı da düşünmelisiniz.

İfade gövdeli üyeler için bu yeni konumlar C# dili için önemli bir kilometre taşını temsil ediyor: Bu özellikler açık kaynak [roslyn](https://github.com/dotnet/Roslyn) projesi üzerinde çalışan topluluk üyeleri tarafından uygulanmıştır.

Bir metodu ifade gövdeli üyeye değiştirmek ikili uyumlu bir [değişikliktir.](version-update-considerations.md#binary-compatible-changes)

## <a name="throw-expressions"></a>Throw ifadeleri

C#'da `throw` her zaman bir ifade olmuştur. Çünkü `throw` bir ifade değil, bir ifadedir, kullanamadığınız C# yapıları vardı. Bunlar koşullu ifadeler, null coalescing ifadeler ve bazı lambda ifadeler dahil. İfade gövdeli üyelerin eklenmesi, `throw` ifadelerin yararlı olacağı daha fazla konum ekler. Böylece bu yapılardan herhangi birini yazabilirsiniz, C# 7.0 [*ifadeleri atmak*](../language-reference/keywords/throw.md#the-throw-expression)tanıttı.

Bu ek, daha fazla ifade tabanlı kod yazmayı kolaylaştırır. Hata denetimi için ek ifadelergerekmez.

## <a name="generalized-async-return-types"></a>Genelleştirilmiş async dönüş türleri

Nesneyi `Task` async yöntemlerinden döndürmek, belirli yollarda performans darboğazlarına neden olabilir. `Task`bir başvuru türüdür, bu nedenle kullanmak bir nesneyi ayırmak anlamına gelir. Değiştirici ile bildirilen bir `async` yöntemin önbelleğe alınmış bir sonucu döndürdüğü veya eşzamanlı olarak tamamlandığı durumlarda, ek ayırmalar kodun performans açısından kritik bölümlerinde önemli bir zaman maliyeti ne olabilir. Bu ayırmalar sıkı döngüler halinde gerçekleşirse pahalıya mal olabilir.

Yeni dil özelliği, async yöntemi dönüş türlerinin `Task` `Task<T>`, `void`ve . Döndürülen tür yine de async deseni karşılamalıdır, yani bir `GetAwaiter` yöntem erişilebilir olmalıdır. Somut bir örnek `ValueTask` olarak, bu yeni dil özelliğinden yararlanmak için .NET türü eklendi:

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> Türü kullanmak için NuGet [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) paketini <xref:System.Threading.Tasks.ValueTask%601> eklemeniz gerekir.

Bu geliştirme, performans açısından kritik kod `Task` ayırmayı önlemek için kitaplık yazarları için en yararlıdır.

## <a name="numeric-literal-syntax-improvements"></a>Sayısal gerçek sözdizimi geliştirmeleri

Sayısal sabitleri yanlış okumak, kodu ilk kez okurken kodu anlamayı zorlaştırabilir. Bit maskeleri veya diğer sembolik değerler yanlış anlama yatkındır. C# 7.0 amaçlanan kullanım için en okunabilir şekilde sayılar yazmak için iki yeni özellik içerir: *ikili literals*, ve *basamak ayırıcılar*.

Bit maskeleri oluşturduğunuz veya bir sayının ikili gösteriminin en çok okunabilir kodu oluşturduğu zamanlar için, bu sayıyı ikili olarak yazın:

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

Sabitin `0b` başında, sayının ikili sayı olarak yazıldığı belirtilir. İkili sayılar uzun olabilir, bu nedenle yukarıda ikili sabitte gösterildiği `_` gibi, bir basamak ayırıcısı olarak tanıtarak bit desenlerini görmek genellikle daha kolaydır. Basamak ayırıcısı sabitin herhangi bir yerinde görünebilir. Temel 10 sayı için, onu binlerce ayırıcı olarak kullanmak yaygındır:

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

Basamak ayırıcısı , `decimal`, `float`ve `double` türleri ile de kullanılabilir:

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

Birlikte ele alındığında, çok daha okunabilirlik ile sayısal sabitleri bildirebilirsiniz.
