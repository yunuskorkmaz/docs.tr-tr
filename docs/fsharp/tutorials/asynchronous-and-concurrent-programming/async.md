---
title: 'F # zaman uyumsuz programlama'
description: 'F # zaman uyumsuz programlama kullanımı kolay ve doğal dil için bir dil düzeyi programlama modeli aracılığıyla nasıl yapıldığını öğrenin.'
ms.date: 06/20/2016
ms.openlocfilehash: 93ecd05efc493489435214dcd7ae78fffcccec1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="async-programming-in-f"></a>F # zaman uyumsuz programlama #

> [!NOTE]
> Bu makaledeki bazı yanlışlıklar bulundu.  Bunu yeniden yazılıyor.  Bkz: [sorunu #666](https://github.com/dotnet/docs/issues/666) değişiklikler hakkında bilgi edinmek için.

Zaman uyumsuz programlama F #'de, kullanımı kolay ve doğal dil için olmak üzere tasarlanmış bir dil düzeyi programlama modeli aracılığıyla gerçekleştirilebilir.

F # zaman uyumsuz programlama çekirdeği `Async<'T>`, arka planda çalışmaya tetiklenen iş gösterimini nerede `'T` türlerinden özel döndürülen `return` anahtar sözcüğü veya `unit` zaman uyumsuz iş akışı no varsa döndürülecek sonuç.

Bir zaman uyumsuz deyim türü olduğunu anlamak için anahtar kavram olan `Async<'T>`, olan yalnızca bir _belirtimi_ zaman uyumsuz bir bağlamda yapılması çalışma. Açıkça başlangıç işlevleri biriyle başlatmanız kadar yürütülür değil (gibi `Async.RunSynchronously`). Bu iş yapma hakkında düşünmeye farklı bir şekilde olsa da, uygulamada oldukça basit olan sona erer.

Örneğin, ana iş parçacığı engellenmeden HTML dotnetfoundation.org karşıdan yüklemek istediğinizi varsayalım. Bunu şu şekilde gerçekleştirebilirsiniz:

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

Ve bu kadar! Kullanımını yanı sıra `async`, `let!`, ve `return`, yalnızca normal F # kodu budur.

Belirtmeye değer olan birkaç söz dizimi yapıları vardır:

*   `let!` (başka bir bağlamda çalışır) bir zaman uyumsuz ifadesi sonucu bağlar.
*   `use!` Works olduğu gibi `let!`, ancak kapsam dışına çıktığında, ilişkili kaynakları siler.
*   `do!` herhangi bir şey döndürmez bir zaman uyumsuz iş akışı await.
*   `return` yalnızca zaman uyumsuz ifadeden bir sonuç döndürür.
*   `return!` başka bir zaman uyumsuz iş akışı çalıştırır ve sonuç olarak kendi dönüş değerini döndürür.

Ayrıca, normal `let`, `use`, ve `do` anahtar sözcükleri normal bir işlevde gibi zaman uyumsuz sürümlerini kullanılabilir.

## <a name="how-to-start-async-code-in-f"></a>Zaman uyumsuz kod F #'ta başlatma #

Daha önce belirtildiği gibi zaman uyumsuz açıkça başlatılması gereken başka bir bağlamda yapılacak işleri belirtimini kodudur. Bunu yapmanın iki birincil yollar şunlardır:

1.  `Async.RunSynchronously` işlem başka bir iş parçacığında bir zaman uyumsuz iş akışını başlatmak ve sonucunu bekler.

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

2.  `Async.Start` başka bir iş parçacığında bir zaman uyumsuz iş akışını başlatmak ve olacak **değil** sonucunu bekler.

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

Bir zaman uyumsuz iş akışı daha belirli senaryolar için kullanılabilir başlatmak için diğer yolları vardır. Ayrıntılı olmayan [zaman uyumsuz başvurusu](https://msdn.microsoft.com/library/ee370232.aspx).

### <a name="a-note-on-threads"></a>İş parçacığı üzerinde Not

"Üzerinde başka bir iş parçacığı" tümceciği yukarıda belirtilen ancak bilmek önemlidir **bu zaman uyumsuz iş akışları için cephesi olduğunu gelmez çoklu iş parçacığı kullanımı**. İş akışı gerçekte "bir küçük süreyi yararlı çalışmanız için ödünç iş parçacıkları arasında atlar". Zaman uyumsuz iş akışı etkili bir şekilde "(örneğin, bir şey döndürmek ağ arama için bekleniyor) beklediği sırada" zaman ödünç herhangi bir iş parçacığı gidin yararlı çalışmaları başka bir şey kadar serbest bırakılır. Bu çalıştıkları olabildiğince etkili bir şekilde sistemini kullanmak için zaman uyumsuz iş akışları sağlar ve yüksek hacimli g/ç senaryoları için özellikle güçlü hale getirir.

## <a name="how-to-add-parallelism-to-async-code"></a>Zaman uyumsuz kodu paralellik ekleme

Bazen, paralel olarak birden çok zaman uyumsuz işlerini gerçekleştirmek için kendi sonuçlarını toplamak ve bazı şekilde yorumlamaya. `Async.Parallel` Görev paralel coerce gerek içerir kitaplığı, kullanmaya gerek kalmadan bunu sayesinde `Task<'T>` ve `Async<'T>` türleri.

Aşağıdaki örnek kullanacağı `Async.Parallel` paralel dört popüler sitelerinden HTML indirmek için bu görevin tamamlanmasını bekleyin ve sonra indirilen HTML yazdırın.

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

*   "Zaman uyumsuz" tüketen işlevleri sonuna

 Bu yalnızca bir adlandırma kuralı olsa da, API bulunabilirliği gibi şeyleri kolaylaştırır. Özellikle varsa aynı yordamını zaman uyumlu ve zaman uyumsuz sürümlerini açıkça ad yoluyla zaman uyumsuz olduğu durum için iyi bir fikirdir.

*   Derleyiciye dinleme!

 F #'ın derleyici çok sıkı, bir şeyler neredeyse olanaksız hale gibi troubling "zaman uyumsuz" kod eşzamanlı olarak çalıştır. Bir uyarı üzerinden geliyorsa, kodu nasıl içinde düşündüğünüz yürütme olmaz oturum olmasıdır. Derleyici mutluluk yapabiliyorsanız kodunuzu beklendiği gibi büyük olasılıkla yürütülür.

## <a name="for-the-cvb-programmer-looking-into-f"></a>F # diline arayan C# /VB programcı için #

Bu bölümde, C# zaman uyumsuz modeli alışık olduğunuz varsayılır / vb Siz değilseniz, [zaman uyumsuz programlama C#](../../../csharp/async.md) bir başlangıç noktasıdır.

C# /VB zaman uyumsuz modeli ve F # zaman uyumsuz modeli arasındaki temel fark yoktur.

Döndüren bir işlev çağırdığınızda bir `Task` veya `Task<'T>`, bu iş zaten yürütme başladı. Döndürülen tanıtıcı zaten çalışan zaman uyumsuz işlemi temsil eder. Buna karşılık, çağırdığınızda async işlevi F #'ta `Async<'a>` döndürülen olacağı bir işi temsil eden **oluşturulan** belirli bir noktada. Bu model anlamak, güçlü, birbirine zincirlenmesi için zaman uyumsuz işler F # için izin verdiğinden daha kolay koşullu gerçekleştirilen ve daha hassas bir denetim çizgisi ile başlatıldı.

Diğer birkaç benzerlikler ve eşitlenmeyeceği farklar vardır.

### <a name="similarities"></a>Benzerlikler

*   `let!`, `use!`, ve `do!` için benzer `await` bir zaman uyumsuz iş içinden çağrılırken bir `async{ }` bloğu.

 Üç anahtar sözcükler yalnızca içinde kullanılabilir bir `async { }` bloğu, nasıl benzer `await` içinde yalnızca çağrılabilir bir `async` yöntemi. Kısacası, `let!` yakalamak ve bir sonucu kullanmak istediğinizde içindir `use!` aynı ancak için kaynakları temizlendi kullanıldığı sonra şeydir ve `do!` tamamlamak için hiçbir değer döndürmeyen bir zaman uyumsuz iş akışı için beklenecek istediğinizde içindir devam etmeden önce.

*   F # veri paralelliği benzer şekilde destekler.

 Çok farklı şekilde çalışır ancak `Async.Parallel` karşılık gelen `Task.WhenAll` tümü tamamlandığında sonuçları zaman uyumsuz işler kümesinin isteyen senaryoyu için.

### <a name="differences"></a>Farkları

*   İç içe geçmiş `let!` değil izin, farklı olarak iç içe geçmiş `await`

 Farklı `await`, hangi iç içe geçirilemez süresiz olarak, `let!` olamaz ve içinde başka bir kullanmadan önce bağlı sonucu olmalıdır `let!`, `do!`, veya `use!`.

*   F # C# iptal destek basittir / vb

 C# /VB görev yarıda yürütülmesinin aracılığıyla iptaline destek gerekir denetimi `IsCancellationRequested` özelliği veya arama `ThrowIfCancellationRequested()` üzerinde bir `CancellationToken` zaman uyumsuz yönteme geçirilen nesne.

Buna karşılık, F # zaman uyumsuz iş akışları daha doğal olarak işlem iptal edilemez. İptal basit bir üç adımlık işlemdir.

1.  Yeni bir `CancellationTokenSource`.
2.  Başlangıç bir işlevdeki geçirin.
3.  Çağrı `Cancel` belirtecine.

Örnek:

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

let token = new CancellationTokenSource()
Async.Start (workflow, token)

// Immediately cancel uploadDataAsync after it's been started.
token.Cancel()
```

Ve bu kadar!

## <a name="further-resources"></a>Ek kaynaklar:

*   [MSDN'de zaman uyumsuz iş akışları](https://msdn.microsoft.com/library/dd233250.aspx)
*   [F # için zaman uyumsuz sıraları](https://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [F # veri HTTP yardımcı programları](https://fsharp.github.io/FSharp.Data/library/Http.html)
