---
title: Zaman uyumsuz programlama
description: Bilgi nasıl F# zaman uyumsuz programlama, kullanımı kolay ve doğal dil için dil düzeyinde bir programlama modeli aracılığıyla gerçekleştirilir.
ms.date: 06/20/2016
ms.openlocfilehash: 8cd7d7bcecabe8ea2c33a4787fe9ebbadd67fe67
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753599"
---
# <a name="async-programming-in-f"></a>Zaman uyumsuz programlamada, F\#

> [!NOTE]
> Bu makaledeki bazı hatalar bulundu.  Bunu yeniden yazılıyor.  Bkz: [sorun #666](https://github.com/dotnet/docs/issues/666) değişiklikler hakkında bilgi edinmek için.

Zaman uyumsuz programlama F# kullanımı kolay ve doğal dil için tasarlanmış bir dil düzeyi programlama modeli aracılığıyla gerçekleştirilebilir.

Zaman uyumsuz programlama setinin F# olduğu `Async<'T>`, arka planda çalışmaya devam tetiklenen iş gösterimini burada `'T` ya da türü özel döndürülür `return` anahtar sözcüğü veya `unit` , zaman uyumsuz iş akışı döndürülecek sonuç var.

Bir zaman uyumsuz ifadesinin türü olduğunu anlamak için en önemli kavram olan `Async<'T>`, olan yalnızca bir _belirtimi_ zaman uyumsuz bir bağlamda yapılacak iş. Açıkça başlangıç işlevlerden biri ile başlattığınızda kadar yürütülmez (gibi `Async.RunSynchronously`). Bu iş yapma hakkında düşünmek için farklı bir şekilde olsa da, uygulamada oldukça basit olan sona erer.

Örneğin, ana iş parçacığını engellemeden dotnetfoundation.org HTML indirmek istediğinizi düşünelim. Bunu şu şekilde gerçekleştirebilirsiniz:

```fsharp
open System
open System.Net

let fetchHtmlAsync url =
    async {
        let uri = Uri(url)
        use webClient = new WebClient()

        // Execution of fetchHtmlAsync won't continue until the result
        // of AsyncDownloadString is bound.
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously
printfn "%s" html
```

Ve İşte bu kadar! Kullanımı dışında `async`, `let!`, ve `return`, bu yalnızca normal F# kod.

Dikkate almaya değer birkaç söz dizimi yapıları vardır:

* `let!` (Bu, başka bir bağlamda çalışır) zaman uyumsuz ifadenin sonucu bağlar.
* `use!` yalnızca gibi çalışır `let!`, ancak kapsam dışına çıktığında bağımlı kaynaklarını siler.
* `do!` hiçbir şey döndürmeyen bir zaman uyumsuz iş akışı await.
* `return` yalnızca bir async ifadesinden bir sonuç döndürür.
* `return!` başka bir zaman uyumsuz iş akışı çalıştırır ve sonuç olarak, dönüş değeri döndürür.

Ayrıca, normal `let`, `use`, ve `do` anahtar sözcükleri normal işlevinde olduğu gibi zaman uyumsuz sürümleri ile birlikte kullanılabilir.

## <a name="how-to-start-async-code-in-f"></a>Zaman uyumsuz kod içinde F başlatma\#

Daha önce bahsedildiği gibi zaman uyumsuz kodu açıkça başlatılması gereken başka bir bağlamda yapılacak iş belirtimidir. Bunu yapmanın birincil iki yolu vardır:

1. `Async.RunSynchronously` başka bir iş parçacığında bir zaman uyumsuz iş akışı başlatılacağından ve sonucunu bekler.

    ```fsharp
    open System
    open System.Net

    let fetchHtmlAsync url =
        async {
            let uri = Uri(url)
            use webClient = new WebClient()
            let! html = webClient.AsyncDownloadString(uri)
            return html
        }

    // Execution will pause until fetchHtmlAsync finishes
    let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously

    // you actually have the result from fetchHtmlAsync now!
    printfn "%s" html
    ```

2. `Async.Start` başka bir iş parçacığında zaman uyumsuz bir iş akışını başlatmak ve olacak **değil** sonucunu bekler.

    ```fsharp
    open System
    open System.Net

    let uploadDataAsync url data =
        async {
            let uri = Uri(url)
            use webClient = new WebClient()
            webClient.UploadStringAsync(uri, data)
        }

    let workflow = uploadDataAsync "https://url-to-upload-to.com" "hello, world!"

    // Execution will continue after calling this!
    Async.Start(workflow)

    printfn "%s" "uploadDataAsync is running in the background..."
    ```

Bir zaman uyumsuz iş akışı daha özel senaryoları için kullanılabilir başlatmak için farklı yöntemleri vardır. Ayrıntılı olan [zaman uyumsuz başvurusu](https://msdn.microsoft.com/library/ee370232.aspx).

### <a name="a-note-on-threads"></a>İş parçacığı üzerinde Not

Deyimini "başka bir iş parçacığı" yukarıda belirtilen ancak bilmek önemlidir **bu zaman uyumsuz iş akışları için bir cephe olduğunu gelmez çoklu iş parçacığı kullanımı**. İş akışı gerçekten "iş parçacıkları, bunları küçük bir kullanışlı kitaplıklarımızı zaman miktarı için ödünç arasında atlar". Bir zaman uyumsuz iş akışı etkili bir şekilde "(örneğin, bir şey döndürülecek ağ arama için bekleniyor) beklediği sırada" zaman ödünç herhangi bir iş parçacığı, go yapmak yararlı iş başka bir şey kadar serbest bırakılır. Bu zaman uyumsuz iş akışları, sistem çalıştıkları mümkün olduğunca etkili bir şekilde kullanmasına izin verir ve yüksek hacimli g/ç senaryoları için özellikle güçlü hale getirir.

## <a name="how-to-add-parallelism-to-async-code"></a>Zaman uyumsuz kod için paralellik ekleme

Bazen, paralel olarak birden çok zaman uyumsuz işler gerçekleştirmek için sonuçlarını toplamak ve bunları başka bir yolla yorumlar. `Async.Parallel` Bu görev paralel coerce gerek kalmadan kapsayacaktır kitaplığı kullanmak zorunda kalmadan gerçekleştirmenize izin verir `Task<'T>` ve `Async<'T>` türleri.

Aşağıdaki örnekte `Async.Parallel` paralel dört popüler sitelerden HTML indirmek için bu görevleri tamamlamak bekleyin ve sonra indirilen HTML yazdırın.

```fsharp
open System
open System.Net

let urlList =
    [ "https://www.microsoft.com"
      "https://www.google.com"
      "https://www.amazon.com"
      "https://www.facebook.com" ]

let fetchHtmlAsync url =
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let getHtmlList urls =
    urls
    |> Seq.map fetchHtmlAsync   // Build an Async<'T> for each site
    |> Async.Parallel           // Returns an Async<'T []>
    |> Async.RunSynchronously   // Wait for the result of the parallel work

let htmlList = getHtmlList urlList

// We now have the downloaded HTML for each site!
for html in htmlList do
    printfn "%s" html
```

## <a name="important-info-and-advice"></a>Önemli bilgiler ve öneriler

* "Async" tükettiğiniz tüm işlevleri sonuna

 Bu yalnızca bir adlandırma kuralı olsa da, API keşfedilebilirliğini gibi şeyleri kolaylaştırır. Özellikle varsa aynı yordamı zaman uyumlu ve zaman uyumsuz sürümlerini açıkça adı zaman uyumsuz olduğu durum için iyi bir fikirdir.

* Derleyiciye dinleyin!

F#ın derleyici çok katı, neredeyse imkansız vericidir gibi bir şey yapmadan "async" kod eşzamanlı olarak çalıştır. Bir uyarı arasında geliyorsa, kod nasıl çalışır düşündüğünüz yürütme olmaz işareti olmasıdır. Derleyici mutlu yapabilirsiniz, kodunuzu büyük olasılıkla beklenen şekilde çalıştırır.

## <a name="for-the-cvb-programmer-looking-into-f"></a>İçin C#/VB Programcı F aranıyor\#

Bu bölümde zaman uyumsuz model hakkında bilgi sahibi olduğunuz varsayılır C#/VB. Kullanmıyorsanız, [zaman uyumsuz programlamada C# ](../../../csharp/async.md) bir başlangıç noktasıdır.

Bir temel fark arasında C#/VB zaman uyumsuz model ve F# zaman uyumsuz model.

Döndüren bir işlev çağırdığınızda bir `Task` veya `Task<'T>`, o işin yürütme zaten başladı. Döndürülen tanıtıcı zaten çalışan bir zaman uyumsuz işi temsil eder. Buna karşılık, çağırdığınızda bir zaman uyumsuz işlev F#, `Async<'a>` döndürülen olacağı işi temsil **oluşturulan** belirli bir noktada. Bu model anlamak, güçlü, zaman uyumsuz işler için izin verdiğinden F# birbirine zincirlenmiş için daha kolay koşullu olarak gerçekleştirilen ve Denetim ile daha hassas bir çizgisi başlatılması.

Diğer bazı benzerlikler ve önemli farklar vardır.

### <a name="similarities"></a>Benzerlikler

* `let!`, `use!`, ve `do!` için benzer `await` bir zaman uyumsuz iş içinden çağrılırken bir `async{ }` blok.

  Üç anahtar sözcükler yalnızca içinde kullanılabilir bir `async { }` bloğu nasıl benzer `await` içinde yalnızca çağrılabilen bir `async` yöntemi. Kısacası, `let!` yakalamak ve bir sonucu kullanmak istediğinizde içindir `use!` aynı ancak için kaynaklarını temizlendi kullanıldığı sonra bir şeydir ve `do!` tamamlamak için hiçbir değer döndürmeyen bir zaman uyumsuz iş akışı beklemek istediğinizde içindir devam etmeden önce.

* F#Veri paralelliği benzer şekilde destekler.

  Çok farklı bir şekilde çalışır ancak `Async.Parallel` karşılık gelen `Task.WhenAll` tümü tamamlandığında, birtakım zaman uyumsuz işler sonuçları isteyen senaryosu için.

### <a name="differences"></a>Farkları

* İç içe geçmiş `let!` değil izin, farklı olarak iç içe geçmiş `await`

  Farklı `await`, iç içe geçirilemez, `let!` olamaz ve başka içinde kullanmadan önce ilişkili sonucu olmalıdır `let!`, `do!`, veya `use!`.

* İptal desteği basittir F# kıyasla C#/VB.

  Bir görev sürecin yarısında, yürütme iptalini destekleyen C#/VB gerektirir denetimi `IsCancellationRequested` özelliği veya arama `ThrowIfCancellationRequested()` üzerinde bir `CancellationToken` zaman uyumsuz yönteme geçirilen nesne.

Buna karşılık, F# doğal olarak edilebilen zaman uyumsuz iş akışları. İptal basit bir üç adımlık işlemdir.

1. Yeni bir `CancellationTokenSource`.
2. Bir başlangıç işlevine geçirin.
3. Çağrı `Cancel` belirtecine.

Örnek:

```fsharp
open System.Threading

// Create a workflow which will loop forever.
let workflow =
    async {
        while true do
            printfn "Working..."
            do! Async.Sleep 1000
    }

let tokenSource = new CancellationTokenSource()

// Start the workflow in the background
Async.Start (workflow, tokenSource.Token)

// Executing the next line will stop the workflow
tokenSource.Cancel()
```

Ve İşte bu kadar!

## <a name="further-resources"></a>Ek kaynaklar:

* [MSDN üzerinde zaman uyumsuz iş akışları](https://msdn.microsoft.com/library/dd233250.aspx)
* [Zaman uyumsuz sıraları içinF#](https://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
* [F#Veri HTTP yardımcı programları](https://fsharp.github.io/FSharp.Data/library/Http.html)
