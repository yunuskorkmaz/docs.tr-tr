---
title: İçinde zaman uyumsuz programlamaF#
description: Temel fonksiyonel F# programlama kavramlarından türetilmiş bir dil düzeyi programlama modeline göre zaman uyumsuzluğu için nasıl temiz destek sağladığını öğrenin.
ms.date: 12/17/2018
ms.openlocfilehash: 1ede4a5c1e26df271ac94f9b2c216ac84fb38f59
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395786"
---
# <a name="async-programming-in-f"></a>F @ no__t-0 içinde zaman uyumsuz programlama

Zaman uyumsuz programlama, farklı nedenlerle modern uygulamalar için gerekli olan bir mekanizmadır. Çoğu geliştiricinin karşılaştığı iki birincil kullanım durumu vardır:

- Çok sayıda eş zamanlı gelen isteğe hizmet veren bir sunucu işlemi sunma, ancak bu işleme ait sistemlerden veya hizmetlerden gelen bekleme girişlerini işlerken istek sırasında bulunan sistem kaynaklarını en aza indirme
- Eşzamanlı bir kullanıcı arabirimini veya ana iş parçacığını, arka planda çalışmaya devam ederken koruma

Arka plan çalışması genellikle birden çok iş parçacığının kullanımını içerse de, zaman uyumsuzluğu ve çoklu iş parçacığı kavramlarını ayrı ayrı ele almanız önemlidir. Aslında bunlar ayrı kaygılardır ve diğeri diğerini göstermez. Bu makalede aşağıdaki özellikler daha ayrıntılı olarak açıklanır.

## <a name="asynchrony-defined"></a>Asynchrony tanımlı

Önceki nokta-eşzamanlı olarak birden çok iş parçacığının kullanımından bağımsız olduğu için, biraz daha ayrıntılı bir şekilde kullanılır. Bazen birbiriyle ilgili olan ancak birbirleriyle tamamen bağımsız olan üç kavram vardır:

- Zamanlı birden çok hesaplama, çakışan zaman dilimlerinde yürütülür.
- Paralellik birden çok hesaplama veya tek bir hesaplamanın çeşitli bölümleri tam olarak aynı anda çalıştığında.
- Zaman uyumsuzluğu bir veya daha fazla hesaplama ana program akışından ayrı ayrı Yürütülebilirler.

Üçü de birbirine diksiz kavramlardır, ancak özellikle birlikte kullanıldığında kolayca kolayca kanatılabilir. Örneğin, paralel olarak birden çok zaman uyumsuz hesaplama yürütmeniz gerekebilir. Bu, paralellik veya zaman uyumsuzluğu 'in bir diğerinin anlamı olduğunu göstermez.

"Zaman uyumsuz" sözcüğünün ilgili listesini göz önünde bulundurmanız durumunda iki parça vardır:

- "a", anlamı "Not".
- "zaman uyumlu", anlamı "aynı anda".

Bu iki terimi birlikte yerleştirdiğinizde "zaman uyumsuz", "aynı anda değil" anlamına gelir. İşte bu kadar! Bu tanımda eşzamanlılık veya paralellik bir engel yoktur. Bu, pratikte de geçerlidir.

Pratik koşullarda, içindeki F# zaman uyumsuz hesaplamalar ana program akışından bağımsız olarak yürütülecek şekilde zamanlanır. Bu, eşzamanlılık veya paralellik anlamına gelmez veya bir hesaplamanın arka planda her zaman gerçekleştiğini göstermez. Aslında, hesaplamanın yapısına ve hesaplamanın yürütüldüğü ortama bağlı olarak zaman uyumsuz hesaplamalar bile zaman uyumlu bir şekilde çalıştırılabilir.

Sahip olmanız gereken ana zaman uyumsuz hesaplamaların ana program akışından bağımsız olması gerekir. Zaman uyumsuz hesaplamanın ne zaman ya da nasıl yürütüldüğü hakkında bazı garantiler olsa da, bunları düzenlemek ve zamanlamak için bazı yaklaşımlar vardır. Bu makalenin geri kalanı, zaman uyumsuzluğu için F# temel kavramları ve içinde F#yerleşik olarak bulunan türleri, işlevleri ve ifadeleri nasıl kullanacağınızı anlatıyor.

## <a name="core-concepts"></a>Temel kavramlar

' F#De, zaman uyumsuz programlama üç temel kavram etrafında ortalandı:

- Birleştirilebilir zaman uyumsuz hesaplamayı temsil eden `Async<'T>` türü.
- Zaman uyumsuz iş zamanlamanıza, zaman uyumsuz hesaplamalar oluşturmanıza ve zaman uyumsuz sonuçları dönüştürmenizi sağlayan `Async` modül işlevleri.
- Zaman uyumsuz hesaplamalar oluşturmak ve denetlemek için kullanışlı bir sözdizimi sağlayan `async { }` [Hesaplama ifadesi](../../language-reference/computation-expressions.md).

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

Örnekte, `printTotalFileBytes` işlevi `string -> Async<unit>` türündedir. İşlevin çağrılması, zaman uyumsuz hesaplamayı gerçekten yürütmez. Bunun yerine, zaman uyumsuz olarak yürütülecek işin * belirtimi olarak davranan bir `Async<unit>` döndürür. Bu, gövdesinde `Async.AwaitTask` ' ı çağırır, bu da <xref:System.IO.File.WriteAllBytesAsync%2A> sonucunu çağrıldığında uygun bir türe dönüştürür.

Başka bir önemli satır `Async.RunSynchronously` ' a yapılan çağrıdır. Bu, gerçekten zaman uyumsuz bir F# hesaplamayı yürütmek istiyorsanız çağırmanız gereken bir zaman uyumsuz modül başlatma işlevleridir.

Bu, `async` programlamanın C#/vb stilinde temel bir farktır. ' F#De, zaman uyumsuz hesaplamalar **soğuk görevler**olarak düşünülebilir. Gerçekten yürütmek için açıkça başlatılmış olmaları gerekir. Bu, zaman uyumsuz çalışmayı C#/vbdan daha kolay bir şekilde birleştirip dizmenize olanak sağladığı için bazı avantajlar içerir.

## <a name="combining-asynchronous-computations"></a>Zaman uyumsuz hesaplamaları birleştirme

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

Gördüğünüz gibi `main` işlevi çok sayıda daha fazla çağrı yaptı. Kavramsal olarak, şunları yapar:

1. Komut satırı bağımsız değişkenlerini `Array.map` ile `Async<unit>` hesaplamalar olarak dönüştürün.
2. @No__t-1 hesaplamaları, çalıştırıldığında paralel olarak zamanlayan ve çalıştıran `Async<'T[]>` oluşturun.
3. Paralel hesaplamayı çalıştıracak ve sonucunu yoksaymayacak bir `Async<unit>` oluşturun.
4. Son hesaplamayı `Async.RunSynchronously` ile açık olarak çalıştırın ve tamamlanana kadar engelleyin.

Bu program çalıştığında, her komut satırı bağımsız değişkeni için `printTotalFileBytes` paralel olarak çalışır. Zaman uyumsuz hesaplamalar program akışından bağımsız olarak yürütüldüğünden, bilgilerini yazdırdıkları ve yürütmeyi tamamlayabileceği bir sıra yoktur. Hesaplamalar paralel olarak zamanlanır, ancak yürütme sırası garanti edilmez.

## <a name="sequencing-asynchronous-computations"></a>Zaman uyumsuz hesaplamaları sıralama

@No__t-0, zaten çalışan bir görev yerine bir iş belirtimi olduğundan, kolayca daha karmaşık dönüştürmeler gerçekleştirebilirsiniz. Bir dizi zaman uyumsuz hesaplamalar, bunlardan sonra çalıştırılacak bir örnek aşağıda verilmiştir.

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
    |> Async.RunSynchronously
    |> ignore
```

Bu işlem, `printTotalFileBytes` öğesini paralel olarak zamanlamak yerine `argv` öğelerinin sırasıyla yürütülecek şekilde zamanlıyor. Bir sonraki öğe, son hesaplamanın yürütülmesi bitinceye kadar zamanlanmayacak, bu hesaplamalar yürütmeyle ilgili bir çakışma olmaması gibi sıralanacaktır.

## <a name="important-async-module-functions"></a>Önemli zaman uyumsuz modül işlevleri

Zaman uyumsuz kod F# yazdığınızda, genellikle sizin için hesaplamaların zamanlamasını işleyen bir çerçeve ile etkileşime geçebilirsiniz. Ancak, bu her zaman durum değildir, bu nedenle zaman uyumsuz çalışmayı zamanlamak için çeşitli başlangıç işlevlerini öğrenmenizde yarar vardır.

Zaman F# uyumsuz hesaplamalar zaten yürütülmekte olan çalışmanın temsili yerine bir iş _belirtimi_ olduğundan, bu, bir başlangıç işleviyle açıkça başlatılmaları gerekir. Farklı bağlamlarda yararlı olan çok sayıda [zaman uyumsuz başlatma işlevi](https://msdn.microsoft.com/library/ee370232.aspx) vardır. Aşağıdaki bölümde daha yaygın başlangıç işlevlerinin bazıları açıklanmaktadır.

### <a name="asyncstartchild"></a>Async. StartChild

Bir zaman uyumsuz hesaplama içinde bir alt hesaplama başlatır. Bu, birden çok zaman uyumsuz hesaplamaların eşzamanlı olarak yürütülmesini sağlar. Alt hesaplama, bir iptal belirtecini üst hesaplama ile paylaşır. Üst hesaplama iptal edilirse, alt hesaplama da iptal edilir.

İmza

```fsharp
computation: Async<'T> - timeout: ?int -> Async<Async<'T>>
```

Ne zaman kullanılır:

- Aynı anda birden çok zaman uyumsuz hesaplamalar çalıştırmak istediğinizde, ancak paralel olarak zamanlanamaz.
- Bir alt hesaplamanın ömrünü bir üst hesaplamadan bağlamak istediğinizde.

İçin izlenecek:

- @No__t-0 ile birden çok hesaplama başlatmak, bunları paralel olarak zamanlamaya göre aynı değildir. Hesaplamaları paralel olarak zamanlamak istiyorsanız, `Async.Parallel` ' ı kullanın.
- Bir üst hesaplamayı iptal etmek, başlattığı tüm alt hesaplamaların iptalini tetikler.

### <a name="asyncstartimmediate"></a>Async. StartImmediate

Geçerli işletim sistemi iş parçacığında hemen başlayarak bir zaman uyumsuz hesaplama çalıştırır. Bu, hesaplama sırasında çağıran iş parçacığında bir şeyi güncelleştirmeniz gerekiyorsa yararlıdır. Örneğin, bir zaman uyumsuz hesaplamanın bir kullanıcı arabirimini güncelleştirmesi gerekiyorsa (bir ilerleme çubuğunu güncelleştirme gibi), `Async.StartImmediate` kullanılmalıdır.

İmza

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

Ne zaman kullanılır:

- Bir zaman uyumsuz hesaplamanın ortasında çağıran iş parçacığında bir şeyi güncelleştirmeniz gerektiğinde.

İçin izlenecek:

- Zaman uyumsuz hesaplama içindeki kod, üzerinde zamanlanabilecek her iş parçacığında çalışır. Bu iş parçacığı, bir kullanıcı arabirimi iş parçacığı gibi bir şekilde hassas olduğunda sorunlu olabilir. Bu gibi durumlarda, `Async.StartImmediate` büyük olasılıkla kullanım için uygun değildir.

### <a name="asyncstartastask"></a>Async. StartAsTask

İş parçacığı havuzunda bir hesaplama yürütür. Hesaplama sonlandırıldığında (sonucu üretir, özel durum oluşturur veya iptal edildiğinde) karşılık gelen durumda tamamlanacak olan <xref:System.Threading.Tasks.Task%601> döndürür. İptal belirteci sağlanmazsa, varsayılan iptal belirteci kullanılır.

İmza

```fsharp
computation: Async<'T> - taskCreationOptions: ?TaskCreationOptions - cancellationToken: ?CancellationToken -> Task<'T>
```

Ne zaman kullanılır:

- Bir @no__t bekleyen bir .NET API 'sine çağrı yapmanız gerektiğinde, zaman uyumsuz hesaplamanın sonucunu göstermek için 0.

İçin izlenecek:

- Bu çağrı, sık kullanılan ek yükü artırabilen ek bir `Task` nesnesi ayırır.

### <a name="asyncparallel"></a>Async. Parallel

Paralel olarak yürütülecek zaman uyumsuz hesaplamalar dizisini zamanlar. Paralellik derecesi, `maxDegreesOfParallelism` parametresi belirtilerek isteğe bağlı olarak ayarlanabilir/kısıtlanabilir.

İmza

```fsharp
computations: seq<Async<'T>> - ?maxDegreesOfParallelism: int -> Async<'T[]>
```

Ne zaman kullanılır:

- Aynı anda bir hesaplamalar kümesi çalıştırmanız gerekiyorsa ve bunların yürütme sırasına göre hiçbir rahatlık olmaz.
- Tüm tamamlanana kadar paralel olarak zamanlanan hesaplamaların sonuçlarına gerek yoksa.

İçin izlenecek:

- Yalnızca tüm hesaplamalar bittikten sonra elde edilen değer dizisine erişebilirsiniz.
- Hesaplamalar çalıştırılacak, ancak zamanlanan işleri çalıştırırlar. Bu, yürütmesinin sırasıyla güvenemeyeceğiniz anlamına gelir.

### <a name="asyncsequential"></a>Async. Sequential

Bir dizi zaman uyumsuz hesaplamaların, geçirildikleri sırada yürütülecek şekilde zamanlamasını zamanlar. İlk hesaplama yürütülür, sonra bir sonraki ve bu şekilde devam eder. Paralel olarak hiçbir hesaplama yürütülmeyecektir.

İmza

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

Ne zaman kullanılır:

- Sırayla birden çok hesaplama yürütmeniz gerekiyorsa.

İçin izlenecek:

- Yalnızca tüm hesaplamalar bittikten sonra elde edilen değer dizisine erişebilirsiniz.
- Hesaplamalar, bu işleve geçirildikleri sırada çalıştırılır, bu da sonuçlar döndürülmeden önce geçecek daha fazla zaman geçilecektir.

### <a name="asyncawaittask"></a>Async. AwaitTask

Verilen <xref:System.Threading.Tasks.Task%601> ' ın tamamlanmasını bekleyen bir zaman uyumsuz hesaplama döndürür ve bunun sonucunu `Async<'T>` olarak döndürür

İmza

```fsharp
task: Task<'T>  -> Async<'T>
```

Ne zaman kullanılır:

- F# Zaman uyumsuz bir hesaplama içinde <xref:System.Threading.Tasks.Task%601> döndüren BIR .NET API kullandığınızda.

İçin izlenecek:

- Özel durumlar, görev paralel kitaplığı kuralına göre <xref:System.AggregateException> ' a sarmalanır ve bu, F# zaman uyumsuz olarak genellikle özel durumların yüzeylerinden farklıdır.

### <a name="asynccatch"></a>Async. catch

Verilen bir @no__t (0) yürüten zaman uyumsuz bir hesaplama oluşturur ve `Async<Choice<'T, exn>>` döndürür. Verilen `Async<'T>` başarıyla tamamlanırsa, sonuç değeri ile bir `Choice1Of2` döndürülür. İşlem tamamlanmadan önce bir özel durum oluşturulursa, oluşturulan özel durumla bir `Choice2of2` döndürülür. Bu, birçok hesaplamayı oluşturan zaman uyumsuz bir hesaplamada kullanılırsa ve bu hesaplamaların biri bir özel durum oluşturursa, dahil edilen hesaplama tamamen durdurulur.

İmza

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

Ne zaman kullanılır:

- Bir özel durumla başarısız olabilecek ve çağıranın bu özel durumu işlemek istediğiniz zaman uyumsuz iş yaparken.

İçin izlenecek:

- Birleşik veya sıralı zaman uyumsuz hesaplamalar kullanılırken, "iç" hesaplamalarından biri bir özel durum oluşturursa, birlikte bulunan hesaplama tam olarak durdurulur.

### <a name="asyncignore"></a>Async. Ignore

Verilen hesaplamayı çalıştıran ve sonucunu yoksayan zaman uyumsuz bir hesaplama oluşturur.

İmza

```fsharp
computation: Async<'T> -> Async<unit>
```

Ne zaman kullanılır:

- Zaman uyumsuz bir hesaplamanız olduğunda, sonucu gerekli değildir. Bu, zaman uyumsuz kod için `ignore` koduna benzerdir.

İçin izlenecek:

- @No__t-0 veya `Async<unit>` gerektiren başka bir işlev kullanmak istiyorsanız bunu kullanmanız gerekiyorsa, sonucun atılıp atılıp yapılmayacağınızı düşünün. Yalnızca tür imzasını sığdırmak için sonuçların atılması genellikle yapılmamalıdır.

### <a name="asyncrunsynchronously"></a>Async. RunSynchronously

Zaman uyumsuz bir hesaplama çalıştırır ve bunun sonucunu çağıran iş parçacığında bekler. Bu çağrı engelleniyor.

İmza

```fsharp
computation: Async<'T> - timeout: ?int - cancellationToken: ?CancellationToken -> 'T
```

Ne zaman kullanılır:

- İhtiyacınız varsa, çalıştırılabilir dosyanın giriş noktasında uygulamayı yalnızca bir kez kullanın.
- Performansla ilgilenmezseniz ve aynı anda başka bir zaman uyumsuz işlem kümesi yürütmek istiyorsanız.

İçin izlenecek:

- @No__t çağrılması-0, yürütme tamamlanana kadar çağıran iş parçacığını engeller.

### <a name="asyncstart"></a>Async. Start

@No__t-0 döndüren iş parçacığı havuzunda zaman uyumsuz bir hesaplama başlatır. Sonucunu beklemez. @No__t-0 ile başlatılan iç içe hesaplamalar, onları çağıran üst hesaplamadan tamamen bağımsız olarak başlatılır. Yaşam süresi herhangi bir üst hesaplamasına bağlı değildir. Üst hesaplama iptal edilirse, hiçbir alt hesaplama iptal edilemez.

İmza

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

Yalnızca şu durumlarda kullanın:

- Bir sonuç elde etmez ve/veya işlemesini gerektirmeyen zaman uyumsuz bir hesaplasahipsiniz.
- Zaman uyumsuz bir hesaplamanın tamamlanışında, bilmeniz gerekmez.
- Zaman uyumsuz bir hesaplamanın çalışacağı iş parçacığını ilgilenmezsiniz.
- Görevden kaynaklanan özel durumları bilmeniz veya bunları raporlamak zorunda kalmazsınız.

İçin izlenecek:

- @No__t-0 ile başlatılan hesaplamalar tarafından oluşturulan özel durumlar, çağırana yayılmaz. Çağrı yığını tamamen kalıcı olmayacak.
- @No__t-1 ile başlatılan tüm etkizli işler (`printfn` çağırma gibi), bir program yürütmenin ana iş parçacığında etkisinin oluşmasına neden olmaz.

## <a name="interoperating-with-net"></a>.NET ile çalışma

Zaman uyumsuz [/await](../../../standard/async.md)stili zaman uyumsuz programlama kullanan C# bir .NET kitaplığı veya kod temeli ile çalışıyor olabilirsiniz. C# .Net kitaplıklarının çoğunluğu, <xref:System.Threading.Tasks.Task%601> ve <xref:System.Threading.Tasks.Task> türlerini `Async<'T>` yerine temel soyutlamalar olarak kullandığından, bu iki yaklaşım arasında zaman uyumlu olarak bir sınır olmalıdır.

### <a name="how-to-work-with-net-async-and-taskt"></a>.NET Async ve @no__t ile çalışma-0

@No__t-0 (yani, dönüş değeri olan zaman uyumsuz hesaplamalar) kullanan .NET Async kitaplıkları ve codetabanlarıyla çalışma, basittir ve ile F#yerleşik desteğe sahiptir.

Bir .NET zaman uyumsuz hesaplamayı beklemek için `Async.AwaitTask` işlevini kullanabilirsiniz:

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

Bir .NET çağıranına zaman uyumsuz bir hesaplama geçirmek için `Async.StartAsTask` işlevini kullanabilirsiniz:

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a>.NET Async ve @no__t ile çalışma-0

@No__t-0 kullanan API 'lerle çalışmak için (yani, bir değer döndürmeyen .NET zaman uyumsuz hesaplamalar), `Async<'T>` ' i <xref:System.Threading.Tasks.Task> ' ye dönüştürecek ek bir işlev eklemeniz gerekebilir:

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

Girdi olarak bir <xref:System.Threading.Tasks.Task> kabul eden `Async.AwaitTask` zaten var. Bu ve daha önce tanımlanmış `startTaskFromAsyncUnit` işleviyle, zaman uyumsuz bir F# hesaplamadan <xref:System.Threading.Tasks.Task> türlerini başlatabilir ve bekleolursunuz.

## <a name="relationship-to-multithreading"></a>Çoklu iş parçacıklı ilişki

Bu makale boyunca iş parçacığına bahsedilse de, dikkat etmeniz gereken iki önemli nokta vardır:

1. Geçerli iş parçacığında açıkça başlamadıkça, zaman uyumsuz bir hesaplama ve bir iş parçacığı arasında benzeşim yoktur.
1. İçinde F# zaman uyumsuz programlama, çoklu iş parçacığı oluşturma için bir soyutlama değildir.

Örneğin, bir hesaplama, işin doğasına bağlı olarak, çağıranın iş parçacığı üzerinde çalışır. Bir hesaplama Ayrıca, iş parçacıkları arasında "bekleyen" (bir ağ çağrısının aktarım aşamasında olduğu gibi) kullanım süreleri arasında yararlı bir süre için ödünç alınan "atlayabilir".

, F# Geçerli iş parçacığında (veya açık olarak geçerli iş parçacığında değil) zaman uyumsuz bir hesaplama başlatmak için bazı yetenekler sağlar, ancak zaman uyumsuzluğu genellikle belirli bir iş parçacığı stratejisiyle ilişkili değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Zaman uyumsuz programlama modeli](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [Jet. com F# zaman uyumsuz Kılavuzu](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [F#eğlenceli ve karın zaman uyumsuz programlama kılavuzu](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [Ve F#içinde C# zaman uyumsuz: içinde zaman uyumsuz tuzaklarıC#](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
