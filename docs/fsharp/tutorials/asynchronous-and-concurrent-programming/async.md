---
title: Async Programlama
description: F#'nın temel işlevsel programlama kavramlarından türetilen dil düzeyindebir programlama modeline dayalı olarak eş zamanlılık için nasıl temiz destek sağladığını öğrenin.
ms.date: 12/17/2018
ms.openlocfilehash: 9b2e3057c126d84474c21fde653da5bbee32938a
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608042"
---
# <a name="async-programming-in-f"></a>F'de Async programlama\#

Asynchronous programlama çeşitli nedenlerle modern uygulamalar için gerekli olan bir mekanizmadır. Çoğu geliştiricinin karşılaşacağı iki birincil kullanım örnekleri vardır:

- İstek işleme işlemi, bu işlemin dışındaki sistemlerden veya hizmetlerden gelen girişleri beklerken, meşgul olan sistem kaynaklarını en aza indirirken, önemli sayıda eşzamanlı gelen isteke hizmet verebilen bir sunucu işlemi sunmak
- Arka plan çalışmasını aynı anda ilerletirken yanıt veren bir ui veya ana iş parçacığı koruma

Arka plan çalışmaları genellikle birden çok iş parçacığı kullanımını içerse de, eş zamanlı ve çoklu iş parçacığı kavramlarını ayrı ayrı dikkate almak önemlidir. Aslında, onlar ayrı endişeler, ve biri diğer anlamına gelmez. Bu makalede aşağıdaki ler bunu daha ayrıntılı olarak açıklar.

## <a name="asynchrony-defined"></a>Asynchrony tanımlı

Önceki nokta - bu eşzamanlılık birden fazla iş parçacığı kullanımı bağımsızdır - biraz daha fazla açıklamaya değer. Bazen ilişkili olan, ancak birbirinden tamamen bağımsız olan üç kavram vardır:

- Eşzamanlılık; çakışan dönemlerde birden çok hesaplama yürütüldüğünde.
- Paralellik; birden çok hesaplama veya tek bir hesaplamanın birkaç bölümü tam olarak aynı anda çalıştırıldığında.
- Asynchrony; bir veya daha fazla hesaplama ana program akışından ayrı olarak yürütebilir.

Her üç ortogonal kavramlar, ama kolayca conflated olabilir, özellikle birlikte kullanılır. Örneğin, birden çok eşzamanlı hesaplamayı paralel olarak yürütmeniz gerekebilir. Bu paralellik veya eşzamanlılık birbirini ima anlamına gelmez.

"Asynchronous" kelimesinin etimolojisini göz önünde bulundurursanız, iki parça vardır:

- "a", "değil" anlamına gelir.
- "senkron", "aynı anda" anlamına gelir.

Bu iki terimi bir araya getirdiğinizde, "eşzamanlı"nın "aynı anda değil" anlamına geldiğini görürsünüz. İşte bu kadar! Bu tanımda eşzamanlılık veya paralellik iması yoktur. Bu uygulamada da geçerlidir.

Pratik açıdan, F# daki eşzamanlı hesaplamalar ana program akışından bağımsız olarak yürütülecek şekilde zamanlanır. Bu eşzamanlılık veya paralellik anlamına gelmez, ne de bir hesaplama her zaman arka planda olur anlamına gelmez. Aslında, eşzamanlı hesaplamalar, hesaplamanın doğasına ve hesaplamanın yürütüldettiği ortama bağlı olarak eşzamanlı olarak bile yürütülebilir.

Sahip olması gereken ana paket, asynchronöz hesaplamaların ana program akışından bağımsız olmasıdır. Eşzamanlı hesaplamanın ne zaman veya nasıl yürütüldüğü konusunda az garanti olmasına rağen, bunları planlamak ve planlamak için bazı yaklaşımlar vardır. Bu makalenin geri kalanında, F# eşzamanlılığı ve F# içine yerleşik tür, işlev ve ifadelerin nasıl kullanılacağı ile ilgili temel kavramlar incelenir.

## <a name="core-concepts"></a>Temel kavramlar

F#'da, asynchronous programlama üç temel kavram etrafında ortalanır:

- Tek `Async<'T>` bir eşzamanlı hesaplamayı temsil eden tür.
- Asynchronous `Async` çalışmasını zamanlamanızı, asynchronous hesaplamaları oluşturmanızı ve eşzamanlı sonuçları dönüştürmenizi sağlayan modül işlevleri.
- Asynchronöz `async { }` hesaplamaları oluşturmak ve denetlemek için uygun bir sözdizimi sağlayan [hesaplama ifadesi.](../../language-reference/computation-expressions.md)

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

Örnekte, `printTotalFileBytes` işlev türü. `string -> Async<unit>` İşlev çağırma aslında asynchronous hesaplama yürütmez. Bunun yerine, `Async<unit>` eşzamanlı olarak yürütmek için işin bir *belirtimi* olarak hareket eden bir döndürür. Bu `Async.AwaitTask` uygun bir tür sonucu <xref:System.IO.File.ReadAllBytesAsync%2A> dönüştürür kendi vücudunda çağırır.

Bir diğer önemli satır `Async.RunSynchronously`da. Bu, f# asynchronous hesaplamasını gerçekten yürütmek istiyorsanız aramanız gereken Async modülü başlangıç işlevlerinden biridir.

Bu `async` programlama C # / Visual Basic tarzı ile temel bir farktır. F#'da, asenkron hesaplamalar **Soğuk görevler**olarak düşünülebilir. Bunlar açıkça gerçekten yürütmek için başlatılmalıdır. Bu, c# veya Visual Basic'tekinden çok daha kolay bir şekilde asynchronous çalışmasını birleştirmenize ve dizilemenize olanak sağladığından bazı avantajları vardır.

## <a name="combine-asynchronous-computations"></a>Eşzamanlı hesaplamaları birleştirme

Aşağıda, hesaplamaları birleştirerek bir öncekinin üzerine inşa edilen bir örnek verilmiştir:

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

Gördüğünüz gibi, `main` işlev yapılan oldukça birkaç arama vardır. Kavramsal olarak, aşağıdakileri yapar:

1. Komut satırı bağımsız değişkenlerini ' `Async<unit>` `Array.map`ile hesaplamalara dönüştürün
2. `printTotalFileBytes` Bir zamanlama `Async<'T[]>` ve çalışırken paralel olarak hesaplamaları çalıştırAn oluşturun.
3. Paralel `Async<unit>` hesaplamayı çalıştıracak ve sonucunu yoksayacak bir oluştur.
4. Son hesaplamayı açıkça çalıştırın `Async.RunSynchronously` ve tamamlanana kadar engelleyin.

Bu program çalıştığında, `printTotalFileBytes` her komut satırı bağımsız değişkeni için paralel olarak çalışır. Eşzamanlı hesaplamalar program akışından bağımsız olarak yürütüldeğinden, bilgilerini yazdırDıkları ve yürütmeyi bitirdikleri bir sıra yoktur. Hesaplamalar paralel olarak zamanlanır, ancak bunların yürütme sırası garanti edilmez.

## <a name="sequence-asynchronous-computations"></a>Sıralı asenkron hesaplamalar

Zaten `Async<'T>` çalışan bir görev yerine çalışmanın bir belirtimi olduğundan, daha karmaşık dönüşümleri kolayca gerçekleştirebilirsiniz. Aşağıda, bir dizi Async hesaplamasını sıralayan bir örnek ve böylece birbiri ardına çalıştırışlar.

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

Bu, `printTotalFileBytes` bunları paralel olarak planlamak `argv` yerine öğelerin sırasına göre yürütülmesi için zamanlayacaktır. Sonraki öğe son hesaplama yürütme tamamlanana kadar zamanlanmadığından, hesaplamalar yürütmede çakışmayacak şekilde sıralanır.

## <a name="important-async-module-functions"></a>Önemli Async modülü fonksiyonları

F# kodu yazdığınızda genellikle sizin için hesaplamaların zamanlamasını işleyen bir çerçeveyle etkileşime girebilirsiniz. Ancak, bu her zaman böyle değildir, bu nedenle asynchronous çalışma zamanlamak için çeşitli başlangıç işlevleri öğrenmek iyidir.

F# asynchronous hesaplamaları, zaten yürütülmakta olan çalışmanın bir gösterimi yerine çalışmanın bir _belirtimi_ olduğundan, açıkça bir başlangıç işlevi ile başlatılmalıdır. Farklı bağlamlarda yararlı olan birçok [Async başlangıç işlevi](https://msdn.microsoft.com/library/ee370232.aspx) vardır. Aşağıdaki bölümde daha yaygın başlangıç işlevlerinden bazıları açıklanmaktadır.

### <a name="asyncstartchild"></a>Async.StartChild

Bir eşyoknom hesaplaması içinde bir alt hesaplama başlatır. Bu, birden çok eşzamanlı hesaplamanın aynı anda yürütülmesini sağlar. Alt hesaplama, üst hesaplamaile bir iptal belirteci paylaşır. Üst hesaplama iptal edilirse, alt hesaplama da iptal edilir.

İmza:

```fsharp
computation: Async<'T> * timeout: ?int -> Async<Async<'T>>
```

Ne zaman kullanılır:

- Birden çok eşzamanlı hesaplamayı aynı anda değil, aynı anda yürütmek istediğinizde, ancak bunları paralel olarak zamanlatmayın.
- Bir çocuğun hesaplamasının ömrünü bir ebeveyn hesaplamasına bağlamak istediğinizde.

Dikkat et:

- Birden çok hesaplamayla `Async.StartChild` başlatıcı, bunları paralel olarak zamanlamayla aynı şey değildir. Hesaplamaları paralel olarak zamanlamak istiyorsanız, `Async.Parallel`'yi kullanın.
- Bir üst hesaplamanın iptaledilmesi, başlattığı tüm alt hesaplamaların iptalini tetikler.

### <a name="asyncstartimmediate"></a>Async.StartHemen

Geçerli işletim sistemi iş parçacığıüzerinde hemen başlayarak, bir eşzamanlı hesaplama çalıştırın. Hesaplama sırasında arama iş parçacığı üzerinde bir şey güncelleştirmeniz gerekiyorsa bu yararlıdır. Örneğin, bir eşzamanlı hesaplama nın bir Kullanıcı Arabirimi güncelleştirmesi gerekiyorsa (ilerleme `Async.StartImmediate` çubuğunun güncelleştirilmesi gibi), daha sonra kullanılmalıdır.

İmza:

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

Ne zaman kullanılır:

- Bir eşzamanlı hesaplamanın ortasındaki arama iş parçacığında bir şeyi güncelleştirmeniz gerektiğinde.

Dikkat et:

- Asynchronous hesaplamasındaki kod, zamanlanan iş parçacığı üzerinde çalışacaktır. Bu iş parçacığı bir şekilde bir ui iş parçacığı gibi hassas ise bu sorunlu olabilir. Bu gibi `Async.StartImmediate` durumlarda, kullanmak için büyük olasılıkla uygun değildir.

### <a name="asyncstartastask"></a>Async.StartAsTask

İş parçacığı havuzunda bir hesaplama yürütür. Hesaplama <xref:System.Threading.Tasks.Task%601> sona erdiğinde (sonucu üreten, özel durum ortaya koyan veya iptal edilen) ilgili durumda tamamlanacak bir belge döndürür. İptal belirteci sağlanmazsa, varsayılan iptal belirteci kullanılır.

İmza:

```fsharp
computation: Async<'T> - taskCreationOptions: ?TaskCreationOptions - cancellationToken: ?CancellationToken -> Task<'T>
```

Ne zaman kullanılır:

- A'nın <xref:System.Threading.Tasks.Task%601> eşzamanlı bir hesaplamanın sonucunu temsil etmesini bekleyen bir .NET API'sini aramanız gerektiğinde.

Dikkat et:

- Bu çağrı, sık `Task` sık kullanılırsa ek yükü artırabilir ek bir nesne tahsis edecektir.

### <a name="asyncparallel"></a>Async.Parallel

Paralel olarak yürütülecek bir eşzamanlı hesaplama dizisi zamanlar. Paralellik `maxDegreesOfParallelism` derecesi, parametre belirtilmek suretiyle isteğe bağlı olarak ayarlanabilir/daraltılabilir.

İmza:

```fsharp
computations: seq<Async<'T>> - ?maxDegreesOfParallelism: int -> Async<'T[]>
```

Ne zaman kullanılır:

- Aynı anda bir dizi hesaplama çalıştırmanız gerekiyorsa ve bunların yürütme sırasına güvenmeniz gerekmez.
- Hepsi tamamlanana kadar paralel olarak zamanlanan hesaplamalardan sonuç gerektirmezseniz.

Dikkat et:

- Tüm hesaplamalar tamamlandıktan sonra yalnızca ortaya çıkan değerler dizisine erişebilirsiniz.
- Hesaplamalar ancak zamanlanan alma sonunda çalıştırılacaktır. Bu, onların idam sıralarına güvenemeyeceğiniz anlamına gelir.

### <a name="asyncsequential"></a>Async.Sequential

Geçirilme sırasına göre yürütülecek bir eşzamanlı hesaplama dizisi zamanlar. İlk hesaplama yürütülür, sonra sonraki, ve benzeri. Hiçbir hesaplama paralel olarak yürütülmez.

İmza:

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

Ne zaman kullanılır:

- Sırayla birden çok hesaplama yürütmeniz gerekiyorsa.

Dikkat et:

- Tüm hesaplamalar tamamlandıktan sonra yalnızca ortaya çıkan değerler dizisine erişebilirsiniz.
- Hesaplamalar, bu işleve geçirilme sırasına göre çalıştırılır, bu da sonuçlar döndürülmeden önce daha fazla zamanın geçeceği anlamına gelebilir.

### <a name="asyncawaittask"></a>Async.AwaitTask

Verilenin <xref:System.Threading.Tasks.Task%601> tamamlanmasını bekleyen bir eşzamanlı hesaplama verir ve sonucunu`Async<'T>`

İmza:

```fsharp
task: Task<'T>  -> Async<'T>
```

Ne zaman kullanılır:

- Bir F# asynchronous hesaplama içinde <xref:System.Threading.Tasks.Task%601> bir .NET API tüketirken.

Dikkat et:

- Özel durumlar Görev <xref:System.AggregateException> Paralel Kitaplığı kuralını izleyerek sarılır ve bu, F# async'in genellikle özel durumları nasıl yüzeye çıkardığını gösterir.

### <a name="asynccatch"></a>Async.Catch

Belirli `Async<'T>`bir , döndüren bir `Async<Choice<'T, exn>>`' yi yürüten bir eşzamanlı hesaplama oluşturur. Verilen `Async<'T>` başarıyla tamamlanırsa, a `Choice1Of2` elde edilen değerle döndürülür. Bir özel durum tamamlanmadan önce atılırsa, a `Choice2of2` yükseltilen özel durum la döndürülür. Kendisi birçok hesaplamadan oluşan bir eşzamanlı hesaplamada kullanılırsa ve bu hesaplamalardan biri özel bir durum oluşturursa, kapsayan hesaplama tamamen durdurulur.

İmza:

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

Ne zaman kullanılır:

- Bir özel durumla başarısız olabilecek eşzamanlı çalışma gerçekleştirirken ve bu özel durumu arayanda işlemek istediğinizde.

Dikkat et:

- Birleştirilmiş veya sıralanmış asynchronöz hesaplamalar kullanılırken, "dahili" hesaplamalarından biri özel durum oluşturursa, kapsamlı hesaplama tamamen durdurulacaktır.

### <a name="asyncignore"></a>Async.Ignore

Verilen hesaplamayı çalıştıran ve sonucunu yok sayan bir eşzamanlı hesaplama oluşturur.

İmza:

```fsharp
computation: Async<'T> -> Async<unit>
```

Ne zaman kullanılır:

- Sonucu gerekli olmayan bir eşzamanlı hesaplamanız olduğunda. Bu, eşzamanlı olmayan `ignore` kod koduna benzer.

Dikkat et:

- Kullanmak `Async.Start` istediğiniz için bunu kullanmanız gerekiyorsa veya gerektiren `Async<unit>`başka bir işlev varsa, sonucu atmanın tamam olup olmadığını göz önünde bulundurun. Bir tür imzasını sığdırmak için sonuçları atmak genellikle yapılmamalıdır.

### <a name="asyncrunsynchronously"></a>Async.RunSynchronously

Asynchronous hesaplaması çalıştırıyor ve arama iş parçacığında sonucunu bekliyor. Bu arama engelliyor.

İmza:

```fsharp
computation: Async<'T> - timeout: ?int - cancellationToken: ?CancellationToken -> 'T
```

Ne zaman kullanılır:

- İhtiyacınız varsa, yürütülebilir bir giriş noktasında bir uygulamada yalnızca bir kez kullanın.
- Performansı önemsemiyorsanız ve aynı anda bir dizi diğer eşzamanlı işlemi yürütmek istediğinizde.

Dikkat et:

- Yürütme `Async.RunSynchronously` tamamlanana kadar arama iş parçacığı engeller.

### <a name="asyncstart"></a>Async.Start

İş parçacığı havuzunda dönen bir eşzamanlı hesaplama `unit`başlatır. Sonucunu beklemez. İç içe başlayan `Async.Start` hesaplamalar, onları çağıran ana hesaplamadan tamamen bağımsız olarak başlatılır. Onların ömrü herhangi bir üst hesaplama bağlı değildir. Üst hesaplama iptal edilirse, alt hesaplamalar iptal edilir.

İmza:

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

Yalnızca:

- Sonuç vermeyen ve/veya bir sonuç alınmasını gerektiren bir eşzamanlı hesaplamanız var.
- Eşzamanlı hesaplamanın ne zaman tamamlaşacağını bilmeniz gerekmez.
- Asynchronous hesaplamanın hangi iş parçacığı üzerinde çalıştığı umurunda değil.
- Görevden kaynaklanan özel durumları bilmeniz veya bildirmeniz gerekmez.

Dikkat et:

- Başlatılan hesaplamalar tarafından `Async.Start` yükseltilen özel durumlar arayana yayılmaz. Arama yığını tamamen çözülecektir.
- Herhangi bir etkili çalışma `printfn`(arama `Async.Start` gibi) bir programın yürütülmesi nin ana iş parçacığı üzerinde gerçekleşmesine neden olmaz ile başladı.

## <a name="interoperate-with-net"></a>.NET ile birlikte çalışma

[Async/await](../../../standard/async.md)-style asynchronous programlama kullanan bir .NET kitaplığı veya C# kod tabanıyla çalışıyor olabilirsiniz. C# ve .NET kitaplıklarının <xref:System.Threading.Tasks.Task%601> çoğunluğu <xref:System.Threading.Tasks.Task> çekirdek soyutlamaları yerine `Async<'T>`çekirdek soyutlamaları olarak kullandığından, bu iki eşsenkronizasyon yaklaşımı arasında bir sınırı geçmeniz gerekir.

### <a name="how-to-work-with-net-async-and-taskt"></a>.NET async ve`Task<T>`

.NET async kitaplıkları ve kullanan <xref:System.Threading.Tasks.Task%601> kod tabanları (yani, iade değerlerine sahip async hesaplamaları) ile çalışmak basittir ve F# ile yerleşik desteği vardır.

İşlevi `Async.AwaitTask` .NET asynchronous hesaplamasını beklemek için kullanabilirsiniz:

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

İşlev, `Async.StartAsTask` bir .NET arayana eşzamanlı bir hesaplama geçirmek için kullanabilirsiniz:

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a>.NET async ve`Task`

Kullanan <xref:System.Threading.Tasks.Task> API'lerle çalışmak için (yani bir değer döndürmeyen .NET async hesaplamaları), bir değeri `Async<'T>` dönüştürecek ek <xref:System.Threading.Tasks.Task>bir işlev eklemeniz gerekebilir:

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

Zaten `Async.AwaitTask` bir girdi olarak <xref:System.Threading.Tasks.Task> kabul eden bir. Bu ve daha önce `startTaskFromAsyncUnit` tanımlanmış işlevle, <xref:System.Threading.Tasks.Task> F# async hesaplamasından türleri başlatabilir ve bekleyebilirsiniz.

## <a name="relationship-to-multi-threading"></a>Çoklu iş parçacığı ile ilişki

Bu makale boyunca iş parçacığı belirtilmiş olsa da, hatırlanması gereken iki önemli şey vardır:

1. Geçerli iş parçacığı üzerinde açıkça başlıkça, bir eşzamanlı hesaplama ile iş parçacığı arasında bir benzerlik yoktur.
1. F# asynchronous programlama çoklu iş parçacığı için bir soyutlama değildir.

Örneğin, bir hesaplama aslında işin doğasına bağlı olarak, arayan kişinin iş parçacığı üzerinde çalışabilir. Bir hesaplama da iş parçacıkları arasında "atlama" olabilir, "bekleme" dönemleri arasında yararlı işler yapmak için zaman küçük bir miktar için ödünç (örneğin bir ağ araması transit olduğunda gibi).

F# geçerli iş parçacığı (veya açıkça geçerli iş parçacığı üzerinde değil) bir eşzamanlı hesaplama başlatmak için bazı yetenekler sağlar, asynchrony genellikle belirli bir iş parçacığı stratejisi ile ilişkili değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Asynchronous Programlama Modeli](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [Jet.com'un F# Async Rehberi](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [Eğlence ve kar için F# Asynchronous Programlama kılavuzu](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [C# ve F#'da Async: C'de asynchronous gotchas #](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
