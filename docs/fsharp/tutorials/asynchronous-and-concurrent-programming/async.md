---
title: Zaman uyumsuz programlama
description: "F # ' ın, temel fonksiyonel programlama kavramlarından türetilmiş dil düzeyi bir programlama modeline bağlı olarak, zaman uyumsuzluğu için temizleme desteği sağladığını öğrenin."
ms.date: 08/15/2020
ms.openlocfilehash: 2e5d4fb744b4443eb9caf90cc1bf01473b809127
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811775"
---
# <a name="async-programming-in-f"></a>F 'de zaman uyumsuz programlama\#

Zaman uyumsuz programlama, farklı nedenlerle modern uygulamalar için gerekli olan bir mekanizmadır. Çoğu geliştiricinin karşılaştığı iki birincil kullanım durumu vardır:

- Çok sayıda eş zamanlı gelen isteğe hizmet veren bir sunucu işlemi sunma, ancak bu işleme ait sistemlerden veya hizmetlerden gelen bekleme girişlerini işlerken istek sırasında bulunan sistem kaynaklarını en aza indirme
- Eşzamanlı bir kullanıcı arabirimini veya ana iş parçacığını, arka planda çalışmaya devam ederken koruma

Arka plan çalışması genellikle birden çok iş parçacığının kullanımını içerse de, zaman uyumsuzluğu ve çoklu iş parçacığı kavramlarını ayrı ayrı ele almanız önemlidir. Aslında bunlar ayrı kaygılardır ve diğeri diğerini göstermez. Bu makalede, ayrı kavramlar daha ayrıntılı olarak açıklanmaktadır.

## <a name="asynchrony-defined"></a>Asynchrony tanımlı

Önceki nokta-eşzamanlı olarak birden çok iş parçacığının kullanımından bağımsız olduğu için, biraz daha ayrıntılı bir şekilde kullanılır. Bazen birbiriyle ilgili olan ancak birbirleriyle tamamen bağımsız olan üç kavram vardır:

- Zamanlı birden çok hesaplama, çakışan zaman dilimlerinde yürütülür.
- Paralellik birden çok hesaplama veya tek bir hesaplamanın çeşitli bölümleri tam olarak aynı anda çalıştığında.
- Zaman uyumsuzluğu bir veya daha fazla hesaplama ana program akışından ayrı ayrı Yürütülebilirler.

Üçü de birbirine diksiz kavramlardır, ancak özellikle birlikte kullanıldığında kolayca kolayca kanatılabilir. Örneğin, paralel olarak birden çok zaman uyumsuz hesaplama yürütmeniz gerekebilir. Bu ilişki, paralellik veya zaman uyumsuzluğu 'in bir diğeri olduğunu göstermez.

"Zaman uyumsuz" sözcüğünün ilgili listesini göz önünde bulundurmanız durumunda iki parça vardır:

- "a", anlamı "Not".
- "zaman uyumlu", anlamı "aynı anda".

Bu iki terimi birlikte yerleştirdiğinizde "zaman uyumsuz", "aynı anda değil" anlamına gelir. İşte bu kadar! Bu tanımda eşzamanlılık veya paralellik bir engel yoktur. Bu, pratikte de geçerlidir.

Pratik koşullarda, F # ' daki zaman uyumsuz hesaplamalar ana program akışından bağımsız olarak yürütülecek şekilde zamanlanır. Bu bağımsız yürütme eşzamanlılık veya paralellik anlamına gelmez veya bir hesaplamanın arka planda her zaman gerçekleştiğini göstermez. Aslında, hesaplamanın yapısına ve hesaplamanın yürütüldüğü ortama bağlı olarak zaman uyumsuz hesaplamalar bile zaman uyumlu bir şekilde çalıştırılabilir.

Sahip olmanız gereken ana zaman uyumsuz hesaplamaların ana program akışından bağımsız olması gerekir. Zaman uyumsuz hesaplamanın ne zaman ya da nasıl yürütüldüğü hakkında bazı garantiler olsa da, bunları düzenlemek ve zamanlamak için bazı yaklaşımlar vardır. Bu makalenin geri kalanında f # zaman uyumsuzluğu için temel kavramlar ve f # içinde oluşturulan türlerin, işlevlerin ve ifadelerin nasıl kullanılacağı ele alınarak anlatılmaktadır.

## <a name="core-concepts"></a>Temel kavramlar

F # içinde, zaman uyumsuz programlama üç temel kavram etrafında ortalandı:

- `Async<'T>`Birleştirilebilir bir zaman uyumsuz hesaplamayı temsil eden tür.
- `Async`Modül işlevleri, zaman uyumsuz iş zamanlamanıza, zaman uyumsuz hesaplamalar oluşturmanıza ve zaman uyumsuz sonuçları dönüştürmenizi sağlar.
- `async { }`Zaman uyumsuz hesaplamalar oluşturmak ve denetlemek için kullanışlı bir sözdizimi sağlayan [Hesaplama ifadesi](../../language-reference/computation-expressions.md).

Aşağıdaki örnekte bu üç kavramı görebilirsiniz:

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    printTotalFileBytes "path-to-file.txt"
    |> Async.RunSynchronously

    Console.Read() |> ignore
    0
```

Örnekte, `printTotalFileBytes` işlevi türündedir `string -> Async<unit>` . İşlevin çağrılması, zaman uyumsuz hesaplamayı gerçekten yürütmez. Bunun yerine, `Async<unit>` zaman uyumsuz olarak yürütülecek çalışmanın bir *belirtimi* görevi gören bir döndürür. Bu, `Async.AwaitTask` sonucunu, konumunu uygun bir türe dönüştüren gövdesinde çağırır <xref:System.IO.File.ReadAllBytesAsync%2A> .

Başka bir önemli satır, öğesine yapılan çağrıdır `Async.RunSynchronously` . Bu, gerçekten bir F # zaman uyumsuz hesaplamayı yürütmek istiyorsanız çağırmanız gereken bir zaman uyumsuz modül başlatma işlevleridir.

Bu, C#/Visual Basic 'in programlama stilinde temel bir farktır `async` . F # ' da, zaman uyumsuz hesaplamalar **soğuk görevler**olarak düşünülebilir. Gerçekten yürütmek için açıkça başlatılmış olmaları gerekir. Bu, zaman uyumsuz çalışmayı C# veya Visual Basic göre çok daha kolay bir şekilde birleştirip dizmenize olanak sağladığı için bazı avantajlar içerir.

## <a name="combine-asynchronous-computations"></a>Zaman uyumsuz hesaplamaları birleştirme

Hesaplamaları birleştirerek önceki bir örnek üzerinde derleme yapan bir örnek aşağıda verilmiştir:

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Parallel
    |> Async.Ignore
    |> Async.RunSynchronously

    0
```

Gördüğünüz gibi, `main` işlev çok daha fazla sayıda çağrı yaptı. Kavramsal olarak, şunları yapar:

1. Komut satırı bağımsız değişkenlerini `Async<unit>` ile hesaplamalar içine dönüştürün `Array.map` .
2. Çalışırken `Async<'T[]>` hesaplamaları zamanlayan ve çalıştıran bir oluştur `printTotalFileBytes` .
3. `Async<unit>`Paralel hesaplamayı çalıştıracak ve sonucunu yoksayacak bir oluştur.
4. Son hesaplamayı ile `Async.RunSynchronously` ve blok tamamlanana kadar açıkça çalıştırın.

Bu program çalıştığında, `printTotalFileBytes` her komut satırı bağımsız değişkeni için paralel olarak çalışır. Zaman uyumsuz hesaplamalar program akışından bağımsız olarak yürütüldüğünden, bilgilerini yazdırdıkları ve yürütmeyi tamamlayabileceği bir sıra yoktur. Hesaplamalar paralel olarak zamanlanır, ancak yürütme sırası garanti edilmez.

## <a name="sequence-asynchronous-computations"></a>Sıra zaman uyumsuz hesaplamalar

`Async<'T>`, Zaten çalışan bir görev yerine bir iş belirtimi olduğundan, kolayca daha karmaşık dönüştürmeler gerçekleştirebilirsiniz. Bir dizi zaman uyumsuz hesaplamalar, bunlardan sonra çalıştırılacak bir örnek aşağıda verilmiştir.

```fsharp
let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Sequential
    |> Async.Ignore
    |> Async.RunSynchronously
    |> ignore
```

Bu işlem, `printTotalFileBytes` öğeleri `argv` paralel olarak zamanlamak yerine öğesinin sırasıyla yürütmeye zamanlanır. Bir sonraki öğe, son hesaplamanın yürütülmesi bitinceye kadar zamanlanmayacak, bu hesaplamalar yürütmeyle ilgili bir çakışma olmaması gibi sıralanacaktır.

## <a name="important-async-module-functions"></a>Önemli zaman uyumsuz modül işlevleri

F # ' da zaman uyumsuz kod yazdığınızda, genellikle sizin için hesaplamaların zamanlamasını işleyen bir çerçeve ile etkileşime geçebilirsiniz. Ancak, bu her zaman durum değildir, bu nedenle zaman uyumsuz çalışmayı zamanlamak için çeşitli başlangıç işlevlerini öğrenmenizde yarar vardır.

F # zaman uyumsuz hesaplamalar, zaten yürütülmekte olan çalışmanın temsili yerine bir iş _belirtimi_ olduğundan, bir başlangıç işleviyle açıkça başlatılmaları gerekir. Farklı bağlamlarda yararlı olan çok sayıda [zaman uyumsuz başlangıç yöntemi](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#section0) vardır. Aşağıdaki bölümde daha yaygın başlangıç işlevlerinin bazıları açıklanmaktadır.

### <a name="asyncstartchild"></a>Async. StartChild

Bir zaman uyumsuz hesaplama içinde bir alt hesaplama başlatır. Bu, birden çok zaman uyumsuz hesaplamaların eşzamanlı olarak yürütülmesini sağlar. Alt hesaplama, bir iptal belirtecini üst hesaplama ile paylaşır. Üst hesaplama iptal edilirse, alt hesaplama da iptal edilir.

İmza:

```fsharp
computation: Async<'T> * timeout: ?int -> Async<Async<'T>>
```

Ne zaman kullanılır:

- Aynı anda birden çok zaman uyumsuz hesaplamalar çalıştırmak istediğinizde, ancak paralel olarak zamanlanamaz.
- Bir alt hesaplamanın ömrünü bir üst hesaplamadan bağlamak istediğinizde.

İçin izlenecek:

- Birden çok hesaplama başlatma `Async.StartChild` , bunları paralel olarak zamanlamaya yönelik değildir. Hesaplamaları paralel olarak zamanlamak istiyorsanız kullanın `Async.Parallel` .
- Bir üst hesaplamayı iptal etmek, başlattığı tüm alt hesaplamaların iptalini tetikler.

### <a name="asyncstartimmediate"></a>Async. StartImmediate

Geçerli işletim sistemi iş parçacığında hemen başlayarak bir zaman uyumsuz hesaplama çalıştırır. Bu, hesaplama sırasında çağıran iş parçacığında bir şeyi güncelleştirmeniz gerekiyorsa yararlıdır. Örneğin, bir zaman uyumsuz hesaplamanın bir kullanıcı arabirimini Güncelleştirmesi (bir ilerleme çubuğunu güncelleştirme gibi) gerekiyorsa, `Async.StartImmediate` kullanılması gerekir.

İmza:

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

Ne zaman kullanılır:

- Bir zaman uyumsuz hesaplamanın ortasında çağıran iş parçacığında bir şeyi güncelleştirmeniz gerektiğinde.

İçin izlenecek:

- Zaman uyumsuz hesaplama içindeki kod, üzerinde zamanlanabilecek her iş parçacığında çalışır. Bu iş parçacığı, bir kullanıcı arabirimi iş parçacığı gibi bir şekilde hassas olduğunda sorunlu olabilir. Bu gibi durumlarda, `Async.StartImmediate` kullanımı uygunsuz olabilir.

### <a name="asyncstartastask"></a>Async. StartAsTask

İş parçacığı havuzunda bir hesaplama yürütür. <xref:System.Threading.Tasks.Task%601>Hesaplama sonlandırıldığında (sonucu üretir, özel durum oluşturur veya iptal edildiğinde) karşılık gelen durumda tamamlanacak bir döndürür. İptal belirteci sağlanmazsa, varsayılan iptal belirteci kullanılır.

İmza:

```fsharp
computation: Async<'T> * taskCreationOptions: ?TaskCreationOptions * cancellationToken: ?CancellationToken -> Task<'T>
```

Ne zaman kullanılır:

- Bir <xref:System.Threading.Tasks.Task%601> zaman uyumsuz hesaplamanın sonucunu temsil eden bir .NET API 'sine çağrı yapmanız gerektiğinde.

İçin izlenecek:

- Bu çağrı ek bir nesne ayırır `Task` ve bu, sıklıkla kullanılıyorsa yükü artırabilir.

### <a name="asyncparallel"></a>Async. Parallel

Paralel olarak yürütülecek zaman uyumsuz hesaplamalar dizisini zamanlar. Paralellik derecesi, parametre belirtilerek isteğe bağlı olarak ayarlanabilir/kısıtlanabilir `maxDegreesOfParallelism` .

İmza:

```fsharp
computations: seq<Async<'T>> * ?maxDegreesOfParallelism: int -> Async<'T[]>
```

Ne zaman kullanılır:

- Aynı anda bir hesaplamalar kümesi çalıştırmanız gerekiyorsa ve bunların yürütme sırasına göre hiçbir rahatlık olmaz.
- Tüm tamamlanana kadar paralel olarak zamanlanan hesaplamaların sonuçlarına gerek yoksa.

İçin izlenecek:

- Yalnızca tüm hesaplamalar bittikten sonra elde edilen değer dizisine erişebilirsiniz.
- Hesaplamalar, her zaman zamanlandığı her seferinde çalıştırılır. Bu davranış, yürütmesinin sırasıyla güvenemeyeceğiniz anlamına gelir.

### <a name="asyncsequential"></a>Async. Sequential

Bir dizi zaman uyumsuz hesaplamaların, geçirildikleri sırada yürütülecek şekilde zamanlamasını zamanlar. İlk hesaplama yürütülür, sonra bir sonraki ve bu şekilde devam eder. Paralel olarak hiçbir hesaplama yürütülmeyecektir.

İmza:

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

Ne zaman kullanılır:

- Sırayla birden çok hesaplama yürütmeniz gerekiyorsa.

İçin izlenecek:

- Yalnızca tüm hesaplamalar bittikten sonra elde edilen değer dizisine erişebilirsiniz.
- Hesaplamalar, bu işleve geçirildikleri sırada çalıştırılır, bu da sonuçlar döndürülmeden önce geçecek daha fazla zaman geçilecektir.

### <a name="asyncawaittask"></a>Async. AwaitTask

Verilen öğenin tamamlanmasını bekleyen bir zaman uyumsuz hesaplama döndürür <xref:System.Threading.Tasks.Task%601> ve bunun sonucunu bir olarak döndürür `Async<'T>`

İmza:

```fsharp
task: Task<'T> -> Async<'T>
```

Ne zaman kullanılır:

- Bir <xref:System.Threading.Tasks.Task%601> F # zaman uyumsuz hesaplama içinde bir .NET API 'si kullandığınızda.

İçin izlenecek:

- Özel durumlar, <xref:System.AggregateException> görev paralel kitaplığı kuralına göre sarmalanır ve bu davranış, F # zaman uyumsuz genellikle özel durumların dışında farklılık gösterir.

### <a name="asynccatch"></a>Async. catch

Verilen ve döndüren zaman uyumsuz bir hesaplama oluşturur `Async<'T>` `Async<Choice<'T, exn>>` . Verilen `Async<'T>` başarıyla tamamlanırsa, `Choice1Of2` sonuç değeri ile bir döndürülür. İşlem tamamlanmadan önce bir özel durum oluşturulursa, bir özel durum `Choice2of2` ortaya çıkan özel durumla döndürülür. Bu, birçok hesaplamayı oluşturan zaman uyumsuz bir hesaplamada kullanılırsa ve bu hesaplamaların biri bir özel durum oluşturursa, dahil edilen hesaplama tamamen durdurulur.

İmza:

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

Ne zaman kullanılır:

- Bir özel durumla başarısız olabilecek ve çağıranın bu özel durumu işlemek istediğiniz zaman uyumsuz iş yaparken.

İçin izlenecek:

- Birleşik veya sıralı zaman uyumsuz hesaplamalar kullanılırken, "iç" hesaplamalarından biri bir özel durum oluşturursa, birlikte bulunan hesaplama tam olarak durdurulur.

### <a name="asyncignore"></a>Async. Ignore

Verilen hesaplamayı çalıştıran ve sonucunu yoksayan zaman uyumsuz bir hesaplama oluşturur.

İmza:

```fsharp
computation: Async<'T> -> Async<unit>
```

Ne zaman kullanılır:

- Zaman uyumsuz bir hesaplamanız olduğunda, sonucu gerekli değildir. Bu, `ignore` zaman uyumsuz kod için koda benzerdir.

İçin izlenecek:

- `Async.Ignore`Kullanmak istediğiniz `Async.Start` veya gerektiren başka bir işlev için kullanmanız gerekiyorsa, sonucun atılıp `Async<unit>` atılmadığı konusunda düşünün. Sonuçları bir tür imzasına uyacak şekilde yok saymaktan kaçının.

### <a name="asyncrunsynchronously"></a>Async. RunSynchronously

Zaman uyumsuz bir hesaplama çalıştırır ve bunun sonucunu çağıran iş parçacığında bekler. Bu çağrı engelleniyor.

İmza:

```fsharp
computation: Async<'T> * timeout: ?int * cancellationToken: ?CancellationToken -> 'T
```

Ne zaman kullanılır:

- İhtiyacınız varsa, çalıştırılabilir dosyanın giriş noktasında uygulamayı yalnızca bir kez kullanın.
- Performansla ilgilenmezseniz ve aynı anda başka bir zaman uyumsuz işlem kümesi yürütmek istiyorsanız.

İçin izlenecek:

- Çağırma `Async.RunSynchronously` , yürütme tamamlanana kadar çağıran iş parçacığını engeller.

### <a name="asyncstart"></a>Async. Start

Öğesini döndüren iş parçacığı havuzunda zaman uyumsuz bir hesaplama başlatır `unit` . Sonucunu beklemez. İle başlatılan iç içe hesaplamalar `Async.Start` , onları çağıran üst hesaplamadan bağımsız olarak başlatılır. Yaşam süresi herhangi bir üst hesaplamasına bağlı değildir. Üst hesaplama iptal edilirse, hiçbir alt hesaplama iptal edilemez.

İmza:

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

Yalnızca şu durumlarda kullanın:

- Bir sonuç elde etmez ve/veya işlemesini gerektirmeyen zaman uyumsuz bir hesaplasahipsiniz.
- Zaman uyumsuz bir hesaplamanın tamamlanışında, bilmeniz gerekmez.
- Zaman uyumsuz bir hesaplamanın çalışacağı iş parçacığını ilgilenmezsiniz.
- Görevden kaynaklanan özel durumları bilmeniz veya bunları raporlamak zorunda kalmazsınız.

İçin izlenecek:

- İle başlatılan hesaplamalar tarafından oluşturulan özel durumlar `Async.Start` çağırana yayılmaz. Çağrı yığını tamamen kalıcı olmayacak.
- İle başlatılan herhangi bir iş (örneğin `printfn` , çağırma) `Async.Start` , bir programın yürütmenin ana iş parçacığında meydana gelmesine neden olmaz.

## <a name="interoperate-with-net"></a>.NET ile birlikte çalışma

[Zaman uyumsuz/await](../../../standard/async.md)stili zaman uyumsuz programlama kullanan bir .NET kitaplığı veya C# kod temeli ile çalışıyor olabilirsiniz. C# ve .NET kitaplıklarının çoğunluğu <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> bunun yerine temel soyutlamaları olarak ' i kullandığından, `Async<'T>` Bu iki yaklaşım arasında bir sınır arasında geçiş yapmanız gerekir.

### <a name="how-to-work-with-net-async-and-taskt"></a>.NET Async ve ile çalışma `Task<T>`

.NET Async kitaplıkları ve kod tabanları ile çalışma (yani <xref:System.Threading.Tasks.Task%601> , dönüş değeri olan zaman uyumsuz hesaplamalar) basittir ve F # ile yerleşik destek vardır.

`Async.AwaitTask`.NET zaman uyumsuz hesaplamayı beklemek için işlevini kullanabilirsiniz:

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

`Async.StartAsTask`Bir .net çağıranına zaman uyumsuz bir hesaplama geçirmek için işlevini kullanabilirsiniz:

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a>.NET Async ve ile çalışma `Task`

Kullanan API 'lerle çalışmak için <xref:System.Threading.Tasks.Task> (yani, bir değer döndürmeyen .NET zaman uyumsuz hesaplamalar), öğesini öğesine dönüştürecek ek bir işlev eklemeniz gerekebilir `Async<'T>` <xref:System.Threading.Tasks.Task> :

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

`Async.AwaitTask`Bir as girişi kabul eden bir zaten var <xref:System.Threading.Tasks.Task> . Bu ve daha önce tanımlanmış olan `startTaskFromAsyncUnit` işlevle, <xref:System.Threading.Tasks.Task> bir F # Async hesaplamadan türleri başlatabilir ve beklede olursunuz.

## <a name="relationship-to-multi-threading"></a>Çoklu iş parçacıklı ilişki

Bu makale boyunca iş parçacığına bahsedilse de, dikkat etmeniz gereken iki önemli nokta vardır:

1. Geçerli iş parçacığında açıkça başlamadıkça, zaman uyumsuz bir hesaplama ve bir iş parçacığı arasında benzeşim yoktur.
1. F # içinde zaman uyumsuz programlama, çoklu iş parçacığı oluşturma için bir soyutlama değildir.

Örneğin, bir hesaplama, işin doğasına bağlı olarak, çağıranın iş parçacığı üzerinde çalışır. Bir hesaplama Ayrıca, iş parçacıkları arasında "bekleyen" (bir ağ çağrısının aktarım aşamasında olduğu gibi) kullanım süreleri arasında yararlı bir süre için ödünç alınan "atlayabilir".

F #, geçerli iş parçacığında (veya açık olarak geçerli iş parçacığında değil) zaman uyumsuz bir hesaplama başlatmak için bazı yetenekler sağlasa da, zaman uyumsuzluğu genellikle belirli bir iş parçacığı stratejisiyle ilişkili değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [F # zaman uyumsuz programlama modeli](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [Jet. com ' un F # Async Kılavuzu](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [Eğlence ve karın zaman uyumsuz programlama kılavuzu için F #](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [C# ve F # dilinde Async: C 'de zaman uyumsuz tuzakları #](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
