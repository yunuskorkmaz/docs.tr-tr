---
title: Görev Tabanlı Zaman Uyumsuz Desen Kullanma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9cad5b24af86afdb1f3894dc124362fed732e93
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64628895"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a>Görev Tabanlı Zaman Uyumsuz Desen Kullanma

Zaman uyumsuz işlemler ile çalışmak için görev tabanlı zaman uyumsuz desen (TAP) kullandığınızda, geri çağırmaları engellemeden beklemeyi için kullanabilirsiniz.  Görevler için bu yöntemleri gibi gerçekleştirilir <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>. İçinde normal denetim akışını beklenmesini zaman uyumsuz işlemleri sağlayarak geri çağırmaları dil tabanlı zaman uyumsuz destek gizler ve derleyicinin ürettiği kodun bu aynı API düzeyinde destek sağlar.

## <a name="suspending-execution-with-await"></a>Await ile yürütmeyi askıya alma
 İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], kullanabileceğiniz [await](~/docs/csharp/language-reference/keywords/await.md) C# anahtar sözcüğü ve [Await işleci](~/docs/visual-basic/language-reference/operators/await-operator.md) zaman uyumsuz olarak beklemek için Visual Basic'te <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> nesneleri. Ne zaman bekleyen bir <xref:System.Threading.Tasks.Task>, `await` ifadesidir türünü `void`. Ne zaman bekleyen bir <xref:System.Threading.Tasks.Task%601>, `await` ifadesidir türünü `TResult`. Bir `await` ifadesi, zaman uyumsuz bir yöntem gövdesi içinde gerçekleşmelidir. C# ve Visual Basic dili hakkında daha fazla bilgi için destek [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# ve Visual Basic dil özellikleri bakın.

 Perde await işlevi bir geri çağırma göreve bir devamlılık kullanarak yükler.  Bu geri çağırma zaman uyumsuz yöntem askıya alma noktasında sürdürür. Zaman uyumsuz yöntemin sürdürüldü, beklenen işlemi başarıyla tamamlandı ve bir <xref:System.Threading.Tasks.Task%601>, kendi `TResult` döndürülür.  Varsa <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> , bekleniyor, sona erdi <xref:System.Threading.Tasks.TaskStatus.Canceled> durumu, bir <xref:System.OperationCanceledException> özel durumu oluşturulur.  Varsa <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> , bekleniyor, sona erdi <xref:System.Threading.Tasks.TaskStatus.Faulted> durumunda hataya neden olan özel durum harekete geçirilir. A `Task` birden çok özel durum sonucu olarak hata olabilir, ancak bu özel durumların yalnızca biri yayılır. Ancak, <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> özelliği döndürür bir <xref:System.AggregateException> içeren tüm hataları özel durum.

 Bir eşitleme bağlamı ise (<xref:System.Threading.SynchronizationContext> nesne) zaman uyumsuz yöntem askıya alma bir anda yürütülmekte olan iş parçacığı ile ilişkili (örneğin, <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> özelliği değil `null`), zaman uyumsuz yöntemin oturum sürdürür bağlamın kullanarak aynı eşitleme bağlamı <xref:System.Threading.SynchronizationContext.Post%2A> yöntemi. Aksi takdirde, Görev Zamanlayıcı üzerinde kullanır (<xref:System.Threading.Tasks.TaskScheduler> nesne), askıya alma zamanında geçerli. Genellikle, bu varsayılan Görev Zamanlayıcısı'nı, (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), iş parçacığı havuzu hedefler. Bu Görev Zamanlayıcı'yı beklenen zaman uyumsuz işlemi burada tamamlandı veya sürdürme olup zamanlanması gerektiğini sürdürme belirler. Varsayılan Zamanlayıcı genellikle beklenen işlem tamamlanmış iş parçacığı üzerinde çalıştırılacak süreklilik sağlar.

 Zaman uyumsuz bir yöntem çağrıldığında, ilk await ifadesi bu noktada çağırma çağırana döner. henüz tamamlanmamış bir beklenebilir örneğinde kadar eş zamanlı olarak işlev gövdesini yürütür. Zaman uyumsuz yöntemin oluşmazsa `void`, <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> sürekli hesaplama temsil etmek için nesne döndürülür. Void olmayan zaman uyumsuz yönteminde return deyimi karşılaşılanaa ya da yöntem gövdesinin sonuna ulaşıldığında, görev tamamlanır <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> son durumu. Zaman uyumsuz Yöntemin gövdesi bırakmak denetim işlenmeyen bir özel durum neden olursa, görev biten <xref:System.Threading.Tasks.TaskStatus.Faulted> durumu. O özel durumu ise bir <xref:System.OperationCanceledException>, görevi yerine biten <xref:System.Threading.Tasks.TaskStatus.Canceled> durumu. Bu şekilde, sonuç ya da özel durum sonunda yayımlanır.

 Bu davranış birkaç önemli farklılıklar vardır.  Performans nedenleriyle zaman bir görev zaten tamamlandıysa görev beklenir, Denetim değil oluşturulur ve işlev yürütmeye devam eder.  Buna ek olarak, özgün bağlamına döndürerek her zaman istenen davranış değildir ve değiştirilebilir; Bu, sonraki bölümde daha ayrıntılı açıklanmıştır.

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a>Askıya alma ve sürdürme ConfigureAwait Yield ile yapılandırma
 Çeşitli yöntemler, zaman uyumsuz bir yöntemin yürütme üzerinde daha fazla denetim sağlar. Örneğin, kullanabileceğiniz <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> yöntemi zaman uyumsuz yönteme bir bekletme noktası tanıtmak için:

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 Bu, zaman uyumsuz olarak yayınlayarak veya geçerli bağlama zamanlama eşdeğerdir.

```csharp
Task.Run(async delegate
{
    for(int i=0; i<1000000; i++)
    {
        await Task.Yield(); // fork the continuation into a separate work item
        ...
    }
});
```

 Ayrıca <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> askıya alma ve sürdürme zaman uyumsuz bir yöntemde üzerinde daha iyi denetim için yöntemi.  Daha önce belirtildiği gibi varsayılan olarak, zaman uyumsuz bir yöntem askıya zaman geçerli bağlam yakalanır ve yakalanan bu bağlamı zaman uyumsuz yöntemin devamı sürdürme üzerinde çağırmak için kullanılır.  Çoğu durumda, istediğiniz tam davranış budur.  Diğer durumlarda, devamlılık bağlamı hakkında önemsemez ve bu tür postaları orijinal bağlamdaki dön önleyerek daha iyi performans elde edebilirsiniz.  Bunu etkinleştirmek için <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> yakalamak ve bağlamda sürdürmek için ancak erdirdi beklemenin zaman uyumsuz işlem tamamlanmış her yerde yürütme devam etmek için bekleme işlemi bildirmek için yöntemi:

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a>Zaman uyumsuz bir işlem iptal ediliyor
 İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], iptal desteği DOKUNUN yöntemler sağlar bir iptal belirteci kabul eden en az bir aşırı yükleme (<xref:System.Threading.CancellationToken> nesne).

 Bir iptal belirteci iptal belirteci kaynağı oluşturulur (<xref:System.Threading.CancellationTokenSource> nesne).  Kaynağın <xref:System.Threading.CancellationTokenSource.Token%2A> özelliği işareti iptal belirtecini döndürür, kaynağın <xref:System.Threading.CancellationTokenSource.Cancel%2A> yöntemi çağrılır.  Örneğin, tek bir Web sayfasından indirin ve işlemi iptal edemezsiniz eklemek istiyorsanız, oluşturduğunuz bir <xref:System.Threading.CancellationTokenSource> nesne, TAP yöntemi, belirtecin geçip ve ardından kaynağın çağrısı <xref:System.Threading.CancellationTokenSource.Cancel%2A> işlemi iptal etmek hazır olduğunuzda yöntemi:

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 Birden çok zaman uyumsuz çağrılar iptal etmek için aynı belirteci için tüm etkinleştirmeleri geçirebilirsiniz:

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 Ya da aynı belirteci için seçmeli alt işlemlerin geçirebilirsiniz:

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 Herhangi bir iş parçacığından iptal isteklerini başlatılabilir.

 Geçirebilirsiniz <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> iptal hiçbir zaman istenmesi belirtmek için bir iptal belirteci kabul eden herhangi bir yöntemi için değer.  Bu neden <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> dönmesini `false`, ve çağrılan yöntemin uygun şekilde en iyi duruma getirebilirsiniz.  Test amacıyla de belirteç zaten iptal edildi veya iptal edilebilir olmayan bir durumda başlaması göstermek için bir Boole değeri kabul eden Oluşturucusu kullanarak örneği oluşturulan bir önceden iptal edilmiş bir iptal belirteci geçirebilirsiniz.

 Bu yaklaşım iptali çeşitli avantajları vardır:

- Zaman uyumsuz ve zaman uyumlu işlemler herhangi bir sayıda, aynı iptal belirtecini geçirebilirsiniz.

- Aynı iptal isteği herhangi bir sayıda dinleyicileri hızla.

- Zaman uyumsuz API geliştiricidir tam denetimi iptal isteğinde ve ne zaman etkili olması.

- API kullanan kod için iptal isteklerini aktarılacaktır zaman uyumsuz çağrılar seçmeli olarak belirleyebilirsiniz.

## <a name="monitoring-progress"></a>İlerlemeyi İzleme
 Bazı zaman uyumsuz yöntemler, ilerleme zaman uyumsuz yönteme geçirilen bir ilerleme arabirimi aracılığıyla kullanıma sunar.  Örneğin, metin ve yol boyunca bir dize zaman uyumsuz olarak indiren bir işlev, şimdiye kadarki tamamlanan indirme yüzdesini içeren devam eden güncelleştirmelerin başlatır göz önünde bulundurun.  Böyle bir yöntemi gibi bir Windows Presentation Foundation (WPF) uygulamasında tüketilebilecek:

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtResult.Text = await DownloadStringAsync(txtUrl.Text,
            new Progress<int>(p => pbDownloadProgress.Value = p));
    }
    finally { btnDownload.IsEnabled = true; }
}
```

<a name="combinators"></a>
## <a name="using-the-built-in-task-based-combinators"></a>Yerleşik görev tabanlı Kombinatör kullanımı
 <xref:System.Threading.Tasks> Ad alanı oluşturma ve görevler ile çalışmak için birkaç yöntem içerir.

### <a name="taskrun"></a>Gt;Task.Run
 <xref:System.Threading.Tasks.Task> Sınıfı içeren birkaç <xref:System.Threading.Tasks.Task.Run%2A> kolayca olanak tanıyan yöntemler yük boşaltma iş olarak bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> iş parçacığı havuzuna, örneğin:

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    textBox1.Text = await Task.Run(() =>
    {
        // … do compute-bound work here
        return answer;
    });
}
```

 Bunlardan bazıları <xref:System.Threading.Tasks.Task.Run%2A> yöntemleri gibi <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> aşırı yükleme, için kısayol olarak mevcut <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> yöntemi.  Gibi diğer aşırı <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, kullanmanızı await Boşaltılan işe, örneğin etkinleştir:

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    pictureBox1.Image = await Task.Run(async() =>
    {
        using(Bitmap bmp1 = await DownloadFirstImageAsync())
        using(Bitmap bmp2 = await DownloadSecondImageAsync())
        return Mashup(bmp1, bmp2);
    });
}
```

 Stl'yi Bu aşırı kullanarak mantıksal eşdeğer <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> yöntemi ile birlikte <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> görev paralel Kitaplığı'nda genişletme yöntemi.

### <a name="taskfromresult"></a>Task.FromResult
 Kullanım <xref:System.Threading.Tasks.Task.FromResult%2A> yöntemi burada verileri zaten olabilir kullanılabilir ve yalnızca senaryolarda gereken içine yükseltilmiş görev döndüren bir yöntem döndürülecek bir <xref:System.Threading.Tasks.Task%601>:

```csharp
public Task<int> GetValueAsync(string key)
{
    int cachedValue;
    return TryGetCachedValue(out cachedValue) ?
        Task.FromResult(cachedValue) :
        GetValueAsyncInternal();
}

private async Task<int> GetValueAsyncInternal(string key)
{
    …
}
```

### <a name="taskwhenall"></a>Task.WhenAll
 Kullanım <xref:System.Threading.Tasks.Task.WhenAll%2A> yöntemini zaman uyumsuz olarak görevleri olarak temsil edilen birden çok zaman uyumsuz işlemler üzerinde bekleyin.  Genel olmayan görevler kümesini veya bir genel görevler Tekdüzen olmayan kümesini destekleyen birden çok aşırı yükleme yöntemi vardır (örneğin, zaman uyumsuz olarak birden çok void döndüren işlemleri bekleme veya zaman uyumsuz olarak birden çok değer döndüren yöntem için bekleyen burada Her bir değeri, farklı bir türe sahip olabilir) ve genel görevler Tekdüzen bir dizi desteklemek için (birden çok zaman uyumsuz olarak bekleyen gibi `TResult`-döndürme yöntemlerini).

 Birçok müşteri için e-posta iletilerini göndermek istediğiniz varsayalım. Sonraki göndermeden önce tamamlamak bir ileti için bekliyorsunuz değil için gönderme binebilir. Ayrıca, hata oluşup oluşmadığını ve gönderme işlemleri tamamlandığında çıkış bulabilirsiniz:

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 Bu kod, açıkça özel durumlar oluşabilir, ancak özel durumlar / yayılmasına olanak tanır işlemiyor `await` elde edilen görev üzerinde <xref:System.Threading.Tasks.Task.WhenAll%2A>.  Özel durumları işlemek için kod aşağıdaki gibi kullanabilirsiniz:

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    ...
}
```

 Herhangi bir zaman uyumsuz işlem başarısız olursa, bu durumda, tüm özel durumları olarak birleştirilecektir bir <xref:System.AggregateException> depolanan özel durum <xref:System.Threading.Tasks.Task> sağlayıcıdan döndürülen <xref:System.Threading.Tasks.Task.WhenAll%2A> yöntemi.  Ancak, bu özel durumların yalnızca biri tarafından yayılır `await` anahtar sözcüğü.  Tüm özel durumları incelemek isterseniz, önceki kod şu şekilde yeniden yazabilirsiniz:

```csharp
Task [] asyncOps = (from addr in addrs select SendMailAsync(addr)).ToArray();
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    foreach(Task faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

 Birden çok dosyayı Web'den zaman uyumsuz olarak yükleme, bir örnek düşünelim.  Bu durumda, tüm zaman uyumsuz işlemlerin homojen sonuç türleri olan ve sonuçları erişmek kolaydır:

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 Önceki void döndüren senaryoda ele aldığımız aynı özel durum işleme teknikleri kullanabilirsiniz:

```csharp
Task [] asyncOps =
    (from url in urls select DownloadStringAsync(url)).ToArray();
try
{
    string [] pages = await Task.WhenAll(asyncOps);
    ...
}
catch(Exception exc)
{
    foreach(Task<string> faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

### <a name="taskwhenany"></a>Task.WhenAny
 Kullanabileceğiniz <xref:System.Threading.Tasks.Task.WhenAny%2A> zaman uyumsuz olarak birden çok zaman uyumsuz işlemler yalnızca biri için beklemeniz yöntemi temsil görevleri tamamlamak için.  Bu yöntem, dört birincil kullanım örnekleri sunar:

- Artıklık:  Birden çok kez bir işlemi gerçekleştirilirken ve ilk (örneğin, tek bir sonuç oluşturan birden çok hisse senedi web Hizmetleri ile irtibat ve hızlı tamamlayan bir seçme) tamamlayan bir seçme.

- Gerekecektir:  Birden çok işlem başlatma ve tüm bunları tamamlanması için bekleniyor, ancak tamamlandıkça işlemeden.

- Azaltma:  Başkalarının tamamlanmış olarak başlamak ek işlem yapılmasına olanak sağlar.  Bu bir araya senaryo uzantısıdır.

- Erken BailOut komutunu:  Örneğin, görev t1 tarafından temsil edilen bir işlem içinde gruplandırılabilir bir <xref:System.Threading.Tasks.Task.WhenAny%2A> başka bir görev t2 ve görevle bekleyebilir <xref:System.Threading.Tasks.Task.WhenAny%2A> görev. Görev t2'ın temsil eden bir zaman aşımı veya iptal ya da neden olan bazı bir sinyal <xref:System.Threading.Tasks.Task.WhenAny%2A> t1 tamamlanmadan önce tamamlanması gereken görev.

#### <a name="redundancy"></a>Yedeklilik
 Bir hisse senedi satın alma konusunda karar istediğiniz bir durum düşünün.  Güvendiğiniz birkaç stok öneri web hizmetleri vardır, ancak günlük yüke bağlı olarak, her hizmet farklı zamanlarda yavaş olduğundan yukarı sonlandırabilirsiniz.  Kullanabileceğiniz <xref:System.Threading.Tasks.Task.WhenAny%2A> yöntemi herhangi bir işlem tamamlandığında bir bildirim almak için:

```csharp
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol),
    GetBuyRecommendation2Async(symbol),
    GetBuyRecommendation3Async(symbol)
};
Task<bool> recommendation = await Task.WhenAny(recommendations);
if (await recommendation) BuyStock(symbol);
```

 Farklı <xref:System.Threading.Tasks.Task.WhenAll%2A>, başarıyla tamamlanan tüm görevleri sarmalanmış halden sonuçları döndüren <xref:System.Threading.Tasks.Task.WhenAny%2A> tamamlanan bir görev döndürür. Bir görev başarısız olursa, başarısız ve bir görev başarılı olursa, dönüş değeri hangi görev ile ilişkili bilmek önemlidir bilmeniz önemlidir.  Bu nedenle, bu örnekte gösterildiği gibi döndürülen görevin sonucunu erişmek veya daha fazla, await gerekir.

 Olduğu gibi <xref:System.Threading.Tasks.Task.WhenAll%2A>, istisnalara uyum sağlamaya yönelik yapabilmesi gerekir.  Tamamlanan görevin geri alması için döndürülen görevin hataları yayılır, await ve `try/catch` bunları uygun şekilde; örneğin:

```csharp
Task<bool> [] recommendations = …;
while(recommendations.Count > 0)
{
    Task<bool> recommendation = await Task.WhenAny(recommendations);
    try
    {
        if (await recommendation) BuyStock(symbol);
        break;
    }
    catch(WebException exc)
    {
        recommendations.Remove(recommendation);
    }
}
```

 Ayrıca, ilk görevi başarıyla tamamlandıktan olsa bile, sonraki görevleri başarısız olabilir.  Bu noktada, özel durumlar başa çıkmak için birkaç seçeneğiniz vardır:  Bu durumda kullanabileceğiniz başlatılan tüm görev tamamlanana kadar bekleyebilirsiniz <xref:System.Threading.Tasks.Task.WhenAll%2A> yöntemi veya karar verebilir tüm özel durumları önemli olduğunu ve oturum açmış olmanız gerekir.  Görevler zaman uyumsuz olarak tamamlandığında bir bildirim almak için bu devamlılıklar kullanabilirsiniz:

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => { if (t.IsFaulted) Log(t.Exception); });
}
```

 veya:

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);
}
```

 hatta:

```csharp
private static async void LogCompletionIfFailed(IEnumerable<Task> tasks)
{
    foreach(var task in tasks)
    {
        try { await task; }
        catch(Exception exc) { Log(exc); }
    }
}
…
LogCompletionIfFailed(recommendations);
```

 Son olarak, kalan tüm işlemleri iptal etmek isteyebilirsiniz:

```csharp
var cts = new CancellationTokenSource();
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol, cts.Token),
    GetBuyRecommendation2Async(symbol, cts.Token),
    GetBuyRecommendation3Async(symbol, cts.Token)
};

Task<bool> recommendation = await Task.WhenAny(recommendations);
cts.Cancel();
if (await recommendation) BuyStock(symbol);
```

#### <a name="interleaving"></a>Aralama
 Burada, Web'den görüntüleri ve (örneğin, bir UI denetimine görüntü ekleme) her bir görüntü işleme bir durum düşünün.  İşlem UI iş parçacığı üzerinde sıralı olarak yapmanız gereken, ancak görüntüleri olarak eşzamanlı olarak karşıdan yüklemek istediğiniz. Ayrıca, tüm indirdikten kadar görüntüleri için kullanıcı Arabirimi ekleme tutmak istemediğiniz — tamamlandıkça bunları eklemek istediğiniz:

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

 Üzerinde işlem bakımından yoğun işleme içeren bir senaryo için Aralama uygulayabilirsiniz <xref:System.Threading.ThreadPool> indirilen görüntüleri; örneğin:

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)
         .ContinueWith(t => ConvertImage(t.Result)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

#### <a name="throttling"></a>Sınırlama
 Kullanıcı çok sayıda görüntü indirmeleri kısıtlanabilir olduğunu yüklüyor dışında araya örneği göz önünde bulundurun; Örneğin, yalnızca belirli sayıda indirmeleri aynı anda gerçekleşecek istersiniz. Bunu başarmak için zaman uyumsuz işlemler kümesini başlayabilirsiniz.  İşlem tamamlandı olarak bunların gerçekleşmesi için ek işlemler başlayabilirsiniz:

```csharp
const int CONCURRENCY_LEVEL = 15;
Uri [] urls = …;
int nextIndex = 0;
var imageTasks = new List<Task<Bitmap>>();
while(nextIndex < CONCURRENCY_LEVEL && nextIndex < urls.Length)
{
    imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
    nextIndex++;
}

while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch(Exception exc) { Log(exc); }

    if (nextIndex < urls.Length)
    {
        imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
        nextIndex++;
    }
}
```

#### <a name="early-bailout"></a>Erken BailOut komutunu
 Zaman uyumsuz bir işlemin aynı anda bir kullanıcının iptal isteğine yanıt çalışırken tamamlanması bekliyorsunuz olduğunu göz önünde bulundurun (örneğin, kullanıcının iptal düğmesine tıklandığında). Aşağıdaki kod, bu senaryo gösterilmektedir:

```csharp
private CancellationTokenSource m_cts;

public void btnCancel_Click(object sender, EventArgs e)
{
    if (m_cts != null) m_cts.Cancel();
}

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();
    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        if (imageDownload.IsCompleted)
        {
            Bitmap image = await imageDownload;
            panel.AddImage(image);
        }
        else imageDownload.ContinueWith(t => Log(t));
    }
    finally { btnRun.Enabled = true; }
}

private static async Task UntilCompletionOrCancellation(
    Task asyncOp, CancellationToken ct)
{
    var tcs = new TaskCompletionSource<bool>();
    using(ct.Register(() => tcs.TrySetResult(true)))
        await Task.WhenAny(asyncOp, tcs.Task);
    return asyncOp;
}
```

 Bail karar, ancak temel alınan zaman uyumsuz işlemlerin iptal edilmiyor hemen sonra bu uygulama kullanıcı arabirimi yeniden etkinleştirir.  Bail, ancak kullanıcı arabirimi olasılığı nedeniyle iptal isteği nedeniyle erken bitiş gerçekten tam işlemleri kadar oluşturmayacak karar bekleyen işlemler iptal etmek için başka bir seçenek olacaktır:

```csharp
private CancellationTokenSource m_cts;

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();

    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text, m_cts.Token);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        Bitmap image = await imageDownload;
        panel.AddImage(image);
    }
    catch(OperationCanceledException) {}
    finally { btnRun.Enabled = true; }
}
```

 Başka bir örneği erken BailOut komutunu kullanılmasına <xref:System.Threading.Tasks.Task.WhenAny%2A> yöntemi ile birlikte <xref:System.Threading.Tasks.Task.Delay%2A> yöntemi, sonraki bölümde açıklandığı gibi.

### <a name="taskdelay"></a>Task.Delay
 Kullanabileceğiniz <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> tanıtmak için yöntemi içinde zaman uyumsuz bir yöntemin yürütülmesine duraklatır.  Bu işlevsellik, yoklama döngüler oluşturmak ve kullanıcı girişini işleme önceden belirlenmiş bir süre için erteleme dahil olmak üzere birçok türdeki için kullanışlıdır.  <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> Yöntemi de birlikte yararlı olabilir <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> için zaman aşımları, üzerinde uygulama bekler.

 Daha büyük bir zaman uyumsuz işlemi (örneğin, bir ASP.NET web hizmeti) parçası olan bir görevin tamamlanması çok uzun sürerse, genel işlem etkilese, özellikle için hiç başarısız olursa tamamlayın.  Bu nedenle, zaman uyumsuz bir işlemi beklenirken zaman aşımına görebilmek önemlidir.  Zaman uyumlu <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, ve <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> yöntemleri zaman aşımı değerlerini, ancak karşılık gelen, kabul <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> ve daha önce bahsedilen <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>yöntemleri yapın.  Bunun yerine kullanabileceğiniz <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> birlikte bir zaman aşımı uygulamak için.

 Örneğin, kullanıcı Arabirimi uygulamanızda bir resim indirmek ve görüntü yüklenirken kullanıcı arabirimini devre dışı bırakmak istediğinizi varsayalım. Ancak, yükleme çok uzun sürerse, kullanıcı arabirimini yeniden etkinleştirme ve indirme atmak istiyor:

```csharp
public async void btnDownload_Click(object sender, EventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap> download = GetBitmapAsync(url);
        if (download == await Task.WhenAny(download, Task.Delay(3000)))
        {
            Bitmap bmp = await download;
            pictureBox.Image = bmp;
            status.Text = "Downloaded";
        }
        else
        {
            pictureBox.Image = null;
            status.Text = "Timed out";
            var ignored = download.ContinueWith(
                t => Trace("Task finally completed"));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

 Aynı çünkü birden çok indirmeler için geçerlidir <xref:System.Threading.Tasks.Task.WhenAll%2A> bir görev döndürür:

```csharp
public async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap[]> downloads =
            Task.WhenAll(from url in urls select GetBitmapAsync(url));
        if (downloads == await Task.WhenAny(downloads, Task.Delay(3000)))
        {
            foreach(var bmp in downloads) panel.AddImage(bmp);
            status.Text = "Downloaded";
        }
        else
        {
            status.Text = "Timed out";
            downloads.ContinueWith(t => Log(t));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

## <a name="building-task-based-combinators"></a>Görev tabanlı Kombinatör oluşturma
 Tamamen zaman uyumsuz işlemi temsil eden ve birleştirme işlemi için zaman uyumlu ve zaman uyumsuz özellikler sağlamak için bir görev olduğundan, kendi sonuçları ve benzeri, görevler oluşturan kombinatörlere yararlı kitaplıkları oluşturabilirsiniz daha büyük düzenleri oluşturun.  Önceki bölümde açıklandığı gibi .NET Framework birkaç yerleşik kombinatör içerir, ancak Ayrıca kendi oluşturabilirsiniz. Aşağıdaki bölümler, olası combinator tarafından kurulan yöntemleri ve türleri çeşitli örneklerini sağlar.

### <a name="retryonfault"></a>RetryOnFault
 Çoğu durumda, bir önceki girişim başarısız olursa bir işlemi yeniden deneyin. isteyebilirsiniz.  Zaman uyumlu bir kod için bir yardımcı yöntem gibi derleme `RetryOnFault` bunu gerçekleştirmek için aşağıdaki örnekte:

```csharp
public static T RetryOnFault<T>(
    Func<T> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return function(); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 Bir neredeyse aynı yardımcı yöntem DOKUNARAK uygulanır ve bu nedenle görevleri döndürür zaman uyumsuz işlemlerin oluşturabilirsiniz:

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 Ardından, yeniden denemeleri uygulama mantığı eklemenize kodlamak için bu combinator tarafından kurulan kullanabilirsiniz; Örneğin:

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 Genişletilebiliyordu `RetryOnFault` daha fazla işlev. İşlev başka bir örneğin kabul edebilecek `Func<Task>` yeniden denemeler arasında yeniden; örneğin işlemi denemek ne zaman belirlemek için çağrılacak:

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries, Func<Task> retryWhen)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
        await retryWhen().ConfigureAwait(false);
    }
    return default(T);
}
```

 Ardından işlev gibi ikinci bir işlemi yeniden denemeden önce beklenecek kullanabilirsiniz:

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a>NeedOnlyOne
 Bazı durumlarda, bir işlemin gecikme süresi ve başarı olasılığını artırmak için yedeklilik yararlanabilir.  Hisse senedi fiyatlarını sağlayan birden çok web hizmetlerinden göz önünde bulundurun, ancak günü çeşitli zamanlarda her hizmet kalitesi ve yanıt sürelerini farklı düzeylerde sağlayabilir.  Bu dalgalanmaları ile dağıtılacak verme isteği göndermek için tüm web hizmetleri ve birinden, yanıt alın hemen sonra kalan istekleri iptal.  Birden çok işlemi başlatılıyor, için bekleyen ve ardından kalan iptal ortak Bu tasarımın daha kolay hale getirmek için bir yardımcı işlevinizi uygulayabilirsiniz. `NeedOnlyOne` İşlevi aşağıdaki örnekte, bu senaryo gösterilmektedir:

```csharp
public static async Task<T> NeedOnlyOne(
    params Func<CancellationToken,Task<T>> [] functions)
{
    var cts = new CancellationTokenSource();
    var tasks = (from function in functions
                 select function(cts.Token)).ToArray();
    var completed = await Task.WhenAny(tasks).ConfigureAwait(false);
    cts.Cancel();
    foreach(var task in tasks)
    {
        var ignored = task.ContinueWith(
            t => Log(t), TaskContinuationOptions.OnlyOnFaulted);
    }
    return completed;
}
```

 Ardından, bu işlev şu şekilde kullanabilirsiniz:

```csharp
double currentPrice = await NeedOnlyOne(
    ct => GetCurrentPriceFromServer1Async("msft", ct),
    ct => GetCurrentPriceFromServer2Async("msft", ct),
    ct => GetCurrentPriceFromServer3Async("msft", ct));
```

### <a name="interleaved-operations"></a>Dönüşümlü işlemler
 Kullanırken olası performans sorunu var. <xref:System.Threading.Tasks.Task.WhenAny%2A> görevleri çok büyük kümeleriyle çalışırken bir araya senaryoyu desteklemek için yöntemi.  Yapılan her çağrı <xref:System.Threading.Tasks.Task.WhenAny%2A> her görevle Kaydedilmekte devamlılık sonuçlanıyor. N pek çok görev için araya işlem yaşam süresi boyunca oluşturulan O(N2) devamlılıklar sonuçlanır.  Çok sayıda görev ile çalışıyorsanız, bir combinator tarafından kurulan kullanabilirsiniz (`Interleaved` aşağıdaki örnekte) performans sorunu çözmek için:

```csharp
static IEnumerable<Task<T>> Interleaved<T>(IEnumerable<Task<T>> tasks)
{
    var inputTasks = tasks.ToList();
    var sources = (from _ in Enumerable.Range(0, inputTasks.Count)
                   select new TaskCompletionSource<T>()).ToList();
    int nextTaskIndex = -1;
    foreach (var inputTask in inputTasks)
    {
        inputTask.ContinueWith(completed =>
        {
            var source = sources[Interlocked.Increment(ref nextTaskIndex)];
            if (completed.IsFaulted)
                source.TrySetException(completed.Exception.InnerExceptions);
            else if (completed.IsCanceled)
                source.TrySetCanceled();
            else
                source.TrySetResult(completed.Result);
        }, CancellationToken.None,
           TaskContinuationOptions.ExecuteSynchronously,
           TaskScheduler.Default);
    }
    return from source in sources
           select source.Task;
}
```

 Ardından, combinator tarafından kurulan sonuçlarını görevleri tamamlandıkça işleme için de kullanabilirsiniz; Örneğin:

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a>WhenAllOrFirstException
 Bunlardan biri, bu durumda, özel durum oluşur oluşmaz beklemeyi durdurmak istediğiniz hataları sürece belirli dağıtma/toplama senaryolarda, bir kümedeki tüm görevler için beklenecek isteyebilirsiniz.  Bir combinator tarafından kurulan yöntemiyle gibi gerçekleştirebilirsiniz `WhenAllOrFirstException` aşağıdaki örnekte:

```csharp
public static Task<T[]> WhenAllOrFirstException<T>(IEnumerable<Task<T>> tasks)
{
    var inputs = tasks.ToList();
    var ce = new CountdownEvent(inputs.Count);
    var tcs = new TaskCompletionSource<T[]>();

    Action<Task> onCompleted = (Task completed) =>
    {
        if (completed.IsFaulted)
            tcs.TrySetException(completed.Exception.InnerExceptions);
        if (ce.Signal() && !tcs.Task.IsCompleted)
            tcs.TrySetResult(inputs.Select(t => t.Result).ToArray());
    };

    foreach (var t in inputs) t.ContinueWith(onCompleted);
    return tcs.Task;
}
```

## <a name="building-task-based-data-structures"></a>Yapı görev-tabanlı veri yapıları
 Özel görev tabanlı kombinatör derleme özelliğine ek olarak, bir veri yapısına sahip olmanın <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> sonuçlarını zaman uyumsuz bir işlemin temsil eden ve çok güçlü getirir ile katılmak için gerekli eşitleme zaman uyumsuz senaryolarında kullanılmak üzere özel veri yapılarını oluşturmak için yazın.

### <a name="asynccache"></a>AsyncCache
 Biri önemli bir yönüdür bir görevin, hepsi await Bu, kayıt devamlılıklarla birden çok tüketiciye. Bu sayede, alın, sonuç ya da özel durumlar (durumunda <xref:System.Threading.Tasks.Task%601>) ve benzeri.  Böylece <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> mükemmel uygun zaman uyumsuz bir önbelleğe alma altyapısı kullanılacak.  Küçük bir örnek aşağıda verilmiştir ancak güçlü zaman uyumsuz önbelleği kurulmuştur üst kısmındaki <xref:System.Threading.Tasks.Task%601>:

```csharp
public class AsyncCache<TKey, TValue>
{
    private readonly Func<TKey, Task<TValue>> _valueFactory;
    private readonly ConcurrentDictionary<TKey, Lazy<Task<TValue>>> _map;

    public AsyncCache(Func<TKey, Task<TValue>> valueFactory)
    {
        if (valueFactory == null) throw new ArgumentNullException("loader");
        _valueFactory = valueFactory;
        _map = new ConcurrentDictionary<TKey, Lazy<Task<TValue>>>();
    }

    public Task<TValue> this[TKey key]
    {
        get
        {
            if (key == null) throw new ArgumentNullException("key");
            return _map.GetOrAdd(key, toAdd =>
                new Lazy<Task<TValue>>(() => _valueFactory(toAdd))).Value;
        }
    }
}
```

 [AsyncCache\<TKey, TValue >](https://blogs.msdn.microsoft.com/pfxteam/2010/04/23/parallelextensionsextras-tour-12-asynccache/) sınıf kabul oluşturucusuna bir temsilci olarak alan bir işlev bir `TKey` ve döndüren bir <xref:System.Threading.Tasks.Task%601>.  Daha önce erişilen tüm değerleri önbellekten iç sözlükte depolanır ve `AsyncCache` anahtar başına, yalnızca bir görev oluşturulur, aynı anda bir önbelleğe eriştikten bile sağlar.

 Örneğin, karşıdan yüklenen web sayfaları için bir önbelleği oluşturabilirsiniz:

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 Bir web sayfasının içeriğini ihtiyaç duyduğunuzda, bu zaman uyumsuz yöntemler önbellekte kullanabilirsiniz. `AsyncCache` Sınıfı, olabildiğince az sayfaları mümkün ve önbellekler sonuçları karşıdan yükleme olduğunu sağlar.

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtContents.Text = await m_webPages["https://www.microsoft.com"];
    }
    finally { btnDownload.IsEnabled = true; }
}
```

### <a name="asyncproducerconsumercollection"></a>AsyncProducerConsumerCollection
 Görevler de zaman uyumsuz etkinlikler koordine için veri yapıları oluşturmak için de kullanabilirsiniz.  Klasik paralel tasarım desenleri birini göz önünde bulundurun: üretici/tüketici.  Bu düzen tüketiciler tarafından tüketilen veri Üreticiler oluşturmak ve üreticilerin ve tüketicilerin paralel olarak çalışabilir. Örneğin, tüketici artık 2 öğesini oluşturan bir üretici tarafından daha önce oluşturulan 1 ' öğesi işler.  Üretici/tüketici düzeni için neredeyse şaşmaz biçimde tüketicileri yeni veri bildirilebilir ve kullanılabilir olduğunda bulmak için üreticileri tarafından oluşturulan iş depolamak için bazı veri yapısı gerekir.

 Üreticilerin ve tüketicilerin kullanılmak üzere zaman uyumsuz yöntemler sağlayan görevleri üzerinde oluşturulmuş bir basit veri yapısı şu şekildedir:

```csharp
public class AsyncProducerConsumerCollection<T>
{
    private readonly Queue<T> m_collection = new Queue<T>();
    private readonly Queue<TaskCompletionSource<T>> m_waiting =
        new Queue<TaskCompletionSource<T>>();

    public void Add(T item)
    {
        TaskCompletionSource<T> tcs = null;
        lock (m_collection)
        {
            if (m_waiting.Count > 0) tcs = m_waiting.Dequeue();
            else m_collection.Enqueue(item);
        }
        if (tcs != null) tcs.TrySetResult(item);
    }

    public Task<T> Take()
    {
        lock (m_collection)
        {
            if (m_collection.Count > 0)
            {
                return Task.FromResult(m_collection.Dequeue());
            }
            else
            {
                var tcs = new TaskCompletionSource<T>();
                m_waiting.Enqueue(tcs);
                return tcs.Task;
            }
        }
    }
}
```

 Bu yerinde veri yapısı ile aşağıdaki gibi bir kod yazabilirsiniz:

```csharp
private static AsyncProducerConsumerCollection<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.Take();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Add(data);
}
```

<xref:System.Threading.Tasks.Dataflow> Ad alanı içerir <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> benzer şekilde, ancak bir özel koleksiyon türü oluşturmak zorunda kalmadan kullanabileceğiniz türü:

```csharp
private static BufferBlock<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.ReceiveAsync();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Post(data);
}
```

> [!NOTE]
> <xref:System.Threading.Tasks.Dataflow> Ad alanı kullanılabilir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] aracılığıyla **NuGet**. İçeren derlemeyi yüklemek için <xref:System.Threading.Tasks.Dataflow> ad alanı, projenizi Visual Studio'da açın, **NuGet paketlerini Yönet** proje menüsünden ve çevrimiçi Microsoft.Tpl.Dataflow paketini arayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Görev Tabanlı Zaman Uyumsuz Deseni Uygulama](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
