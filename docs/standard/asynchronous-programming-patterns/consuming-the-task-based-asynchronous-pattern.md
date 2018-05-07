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
ms.openlocfilehash: f7fd03a43d8722e32f64dd9cbe2936301d6bd2f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a>Görev Tabanlı Zaman Uyumsuz Desen Kullanma
Zaman uyumsuz işlemleri ile çalışmak için görev tabanlı zaman uyumsuz desen (TAP) kullandığınızda, bekleme engellenmeden elde etmek için geri aramalar kullanabilirsiniz.  Görevler için bu yöntemlerle gibi sağlanır <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>. Normal denetim akışı içinde beklemenin zaman uyumsuz işlemleri sağlayarak geri aramalar dil tabanlı zaman uyumsuz destek gizler ve derleyici tarafından üretilen kod aynı bu API düzeyinde destek sağlar.  
  
## <a name="suspending-execution-with-await"></a>Yürütme bekleme ile askıya alma  
 İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], kullanabileceğiniz [await](~/docs/csharp/language-reference/keywords/await.md) C# anahtar sözcüğü ve [Await işleci](~/docs/visual-basic/language-reference/operators/await-operator.md) zaman uyumsuz olarak beklemek için Visual Basic'te <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> nesneleri. Ne zaman bekleyen bir <xref:System.Threading.Tasks.Task>, `await` ifadesidir türü `void`. Ne zaman bekleyen bir <xref:System.Threading.Tasks.Task%601>, `await` ifadesidir türü `TResult`. Bir `await` ifade zaman uyumsuz bir yöntem gövdesi içinde gerçekleşmesi gerekir. C# ve Visual Basic dili hakkında daha fazla bilgi için destek [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# ve Visual Basic Dil belirtimleri bakın.  
  
 Perde arkasında bekleme işlevi bir geri çağırma görevde bir devamlılık kullanarak yükler.  Bu geri çağırma askıya noktasında zaman uyumsuz yöntem sürdürür. Zaman zaman uyumsuz yöntem sürdürüldü, awaited işlemi başarıyla tamamlandı ve başarısız olursa bir <xref:System.Threading.Tasks.Task%601>, kendi `TResult` döndürülür.  Varsa <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> , beklemenin içinde sona erdi <xref:System.Threading.Tasks.TaskStatus.Canceled> durumu, bir <xref:System.OperationCanceledException> özel durumu oluşur.  Varsa <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> , beklemenin içinde sona erdi <xref:System.Threading.Tasks.TaskStatus.Faulted> durumunda, hataya neden özel durum. A `Task` birden çok özel durumlar sonucunda hata edebilir, ancak bu özel durumlar yalnızca biri yayılır. Ancak, <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> özelliği döndürür bir <xref:System.AggregateException> tüm hataları içeren özel durum.  
  
 Eşitleme bağlamı varsa (<xref:System.Threading.SynchronizationContext> nesne) zaman uyumsuz yöntem askıya aynı anda yürütülmekte olan iş parçacığı ile ilişkili (örneğin, <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> özelliği değil `null`), o zaman uyumsuz yöntem sürdürür bağlamın kullanarak aynı eşitleme bağlamı <xref:System.Threading.SynchronizationContext.Post%2A> yöntemi. Aksi halde, Görev Zamanlayıcısı'kullanır (<xref:System.Threading.Tasks.TaskScheduler> nesnesi), askıya aynı anda geçerli. Genellikle, bu varsayılan Görev Zamanlayıcı'dır (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), iş parçacığı havuzu hedefler. Bu Görev Zamanlayıcısı'nı awaited zaman uyumsuz işlemi burada tamamlandı veya sürdürme olup zamanlanmalıdır devam belirler. Varsayılan Zamanlayıcı genellikle awaited işlemi tamamlandı iş parçacığı üzerinde çalıştırmak devamlılık sağlar.  
  
 Zaman uyumsuz bir yöntem çağrıldığında, bu noktada çağırma çağırana döndürür henüz tamamlanmadı bir bildirdiğimize örneğinde ifade ilk await kadar eşzamanlı olarak işlevinin gövdesini yürütür. Zaman uyumsuz yöntem oluşmazsa `void`, <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> devam eden hesaplama temsil etmek için Nesne döndürdü. Void olmayan zaman uyumsuz yöntem bir dönüş ifadesi karşılaştı veya yöntem gövdesi sonuna ulaşıldı, görev tamamlanır <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> son durum. Zaman uyumsuz yöntem gövdesi bırakmayı denetim işlenmeyen bir özel duruma neden olursa, görev ile biten <xref:System.Threading.Tasks.TaskStatus.Faulted> durumu. Bu özel durumu ise bir <xref:System.OperationCanceledException>, görevi yerine biten <xref:System.Threading.Tasks.TaskStatus.Canceled> durumu. Bu şekilde, sonuç veya özel durum sonunda yayımlanır.  
  
 Bu davranış birkaç önemli çeşidi vardır.  Performans nedeniyle, bir görev zaten zamana kadar tamamlanmış olan görev beklemenin, Denetim değil veriyor, ve işlevi yürütmek devam eder.  Ayrıca, özgün içerik döndüren her zaman istenen bir davranış değildir ve değiştirilebilir; Bu sonraki bölümünde daha ayrıntılı olarak açıklanmıştır.  
  
### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a>Askıya alma ve sürdürme verim ve ConfigureAwait ile yapılandırma  
 Çeşitli yöntemleri zaman uyumsuz bir yöntemin yürütme üzerinde daha fazla denetim sağlar. Örneğin, kullanabileceğiniz <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> yöntemi zaman uyumsuz yöntem verim noktası tanıtmak için:  
  
```csharp  
public class Task : …  
{  
    public static YieldAwaitable Yield();  
    …  
}  
```  
  
 Bu, zaman uyumsuz olarak gönderme veya geçerli bağlamın zamanlama eşdeğerdir.  
  
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
  
 Aynı zamanda <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> askıya alma ve sürdürme zaman uyumsuz bir yöntem de üzerinde daha iyi denetim için yöntem.  Daha önce belirtildiği gibi varsayılan olarak, geçerli bağlam zaman uyumsuz bir yöntem askıya aynı anda yakalanır ve yakalanan bu bağlam zaman uyumsuz yöntemin devamlılık sürdürme bağlı çağırmak için kullanılır.  Çoğu durumda, istediğiniz tam davranış budur.  Diğer durumlarda devamlılık bağlam hakkında önemli değil ve bu tür gönderimleri geri özgün içerik kaçınarak daha iyi performans elde edebilirsiniz.  Bu ayarı etkinleştirmek için kullanın <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> yakalamak ve bağlamda sürdürmek için ancak beklemenin zaman uyumsuz işlemi tamamlandı her yerde yürütme devam etmek için bekleme işlemi bildirmeniz yöntemi:  
  
```csharp  
await someTask.ConfigureAwait(continueOnCapturedContext:false);  
```  
  
## <a name="canceling-an-asynchronous-operation"></a>Zaman uyumsuz bir işlem iptal etme  
 İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], iptali desteklemek DOKUNUN yöntemleri bir iptal belirteci kabul eder en az bir aşırı yüklemesini sağlar (<xref:System.Threading.CancellationToken> nesnesi).  
  
 Bir iptal belirteci iptal belirteci kaynağı ile oluşturulur (<xref:System.Threading.CancellationTokenSource> nesnesi).  Kaynağın <xref:System.Threading.CancellationTokenSource.Token%2A> özelliği, işaret iptal belirteci döndürür, kaynağın <xref:System.Threading.CancellationTokenSource.Cancel%2A> yöntemi çağrılır.  Örneğin, tek bir Web sayfası indirmek istediğiniz ve işlemi iptal etmek istiyorsanız, oluşturduğunuz bir <xref:System.Threading.CancellationTokenSource> nesne, kendi belirteci DOKUNUN yönteme geçirin ve kaynağın çağrı <xref:System.Threading.CancellationTokenSource.Cancel%2A> işlemi iptal etmek hazır olduğunuzda yöntemi:  
  
```csharp  
var cts = new CancellationTokenSource();  
string result = await DownloadStringAsync(url, cts.Token);  
… // at some point later, potentially on another thread  
cts.Cancel();  
```  
  
 Birden çok zaman uyumsuz çağrıları iptal etmek için tüm çağrılarına aynı belirteci geçirebilirsiniz:  
  
```csharp  
var cts = new CancellationTokenSource();  
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));  
    // at some point later, potentially on another thread  
    …  
    cts.Cancel();  
```  
  
 Veya işlemlerinin seçmeli olarak alt kümesi için aynı belirteci geçirebilirsiniz:  
  
```csharp  
var cts = new CancellationTokenSource();  
    byte [] data = await DownloadDataAsync(url, cts.Token);  
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);  
    … // at some point later, potentially on another thread  
    cts.Cancel();  
```  
  
 İptal isteklerini herhangi bir iş parçacığından başlatılabilir.  
  
 Geçirebilirsiniz <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> iptal hiçbir zaman istenmesi belirtmek için bir iptal belirteci kabul eden herhangi bir yönteme değeri.  Bu neden <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> dönmek için özellik `false`, ve çağrılan yöntemin uygun şekilde en iyi duruma getirebilirsiniz.  Test amacıyla, ayrıca belirteci bir not iptal edilebilen veya zaten iptal durumda başlaması gerektiğini belirtmek için bir Boole değeri kabul Oluşturucusu kullanılarak örneği önceden iptal edilmiş iptal belirteci geçirebilirsiniz.  
  
 Bu yaklaşımın iptali çeşitli avantajları vardır:  
  
-   Zaman uyumsuz ve zaman uyumlu işlemler herhangi bir sayıda aynı iptal belirtecini geçirebilirsiniz.  
  
-   Aynı iptal isteğini dinleyicileri herhangi bir sayıda hızla.  
  
-   Zaman uyumsuz API Geliştirici tam iptal olup istenebilir ve ne zaman etkili denetimdir.  
  
-   API tüketir kod seçmeli olarak iptal isteklerini olarak yayıldığı zaman uyumsuz çağrıları belirleyebilir.  
  
## <a name="monitoring-progress"></a>İlerlemeyi İzleme  
 Bazı zaman uyumsuz yöntemleri zaman uyumsuz yönteme geçirilen bir ilerleme arabirimi ilerlemeyi kullanıma sunar.  Örneğin, zaman uyumsuz olarak bir dize metin ve yol indirmeleri bir işlevi bugüne kadarki tamamlandı indirme yüzdesini içeren ilerleme güncelleştirmeleri başlatır göz önünde bulundurun.  Bu tür bir yöntem aşağıdaki gibi bir Windows Presentation Foundation (WPF) uygulamasında tüketilen:  
  
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
## <a name="using-the-built-in-task-based-combinators"></a>Yerleşik görev tabanlı Combinators kullanma  
 <xref:System.Threading.Tasks> Ad alanı oluşturma ve görevleri ile çalışmak için birkaç yöntem içerir.  
  
### <a name="taskrun"></a>Task.Run  
 <xref:System.Threading.Tasks.Task> Sınıfı içeren birkaç <xref:System.Threading.Tasks.Task.Run%2A> kolayca olanak tanıyan yöntemler boşaltma olarak iş bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> iş parçacığı havuzuna, örneğin:  
  
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
  
 Bunlardan bazıları <xref:System.Threading.Tasks.Task.Run%2A> yöntemleri gibi <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> aşırı yükleme, için toplu olarak mevcut <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> yöntemi.  Gibi diğer overloads <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, etkinleştirme, kullanılacak bekleme Boşaltılan iş içinde örneğin:  
  
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
  
 Bu tür aşırı yüklemeleri kullanarak mantıksal olarak eşdeğerdir <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> yöntemi ile birlikte <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> görev paralel Kitaplığı'nda genişletme yöntemi.  
  
### <a name="taskfromresult"></a>Task.FromResult  
 Kullanım <xref:System.Threading.Tasks.Task.FromResult%2A> içine kaldırılmış görev döndürme yönteminden döndürülen gerekiyor yöntemi burada veri zaten olabilir kullanılabilir ve yalnızca senaryolarda bir <xref:System.Threading.Tasks.Task%601>:  
  
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
 Kullanım <xref:System.Threading.Tasks.Task.WhenAll%2A> yöntemi zaman uyumsuz olarak görevleri olarak temsil edilir birden çok zaman uyumsuz işlemleri üzerinde bekleyin.  Genel olmayan görevleri bir dizi veya genel görevler Tekdüzen olmayan kümesini destekleyen birden çok aşırı has yöntemi (örneğin, zaman uyumsuz olarak birden çok geçersiz kılma döndürme işlemleri bekleme veya zaman uyumsuz olarak birden fazla değer döndüren yöntemler için bekleyen nerede Her değer farklı bir türe sahip) ve genel görevleri Tekdüzen kümesini destekleyecek şekilde (birden çok zaman uyumsuz olarak bekleyen gibi `TResult`-yöntemleri döndüren).  
  
 Birkaç müşterilere e-posta iletileri göndermek istediğiniz varsayalım. Sonraki göndermeden önce tamamlamak bir ileti için bekleme olmayan şekilde iletileri gönderme binebilir. Ayrıca, gönderme işlemleri tamamladığınızda ve hata oluşup oluşmadığını çıkış bulabilirsiniz:  
  
```csharp  
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);  
await Task.WhenAll(asyncOps);  
```  
  
 Bu kod açıkça özel durumlar oluşabilir, ancak özel durumlar dışında yayılmasına olanak tanır işlemiyor `await` elde edilen görevden üzerinde <xref:System.Threading.Tasks.Task.WhenAll%2A>.  Özel durumları işlemek için aşağıdaki gibi kodu kullanabilirsiniz:  
  
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
  
 Herhangi bir zaman uyumsuz işlem başarısız olursa, bu durumda, tüm özel durumları olarak birleştirilecektir bir <xref:System.AggregateException> depolanan özel durum <xref:System.Threading.Tasks.Task> sağlayıcıdan döndürülen <xref:System.Threading.Tasks.Task.WhenAll%2A> yöntemi.  Ancak, bu özel durumlar yalnızca biri tarafından yayılır `await` anahtar sözcüğü.  Tüm özel durumları incelemek isterseniz, önceki kod şu şekilde yazabilirsiniz:  
  
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
  
 Şimdi, birden çok dosya zaman uyumsuz olarak Web'den örneği göz önünde bulundurun.  Bu durumda, tüm zaman uyumsuz işlemleri homojen sonuç türlerine sahip ve sonuçları erişmek kolaydır:  
  
```csharp  
string [] pages = await Task.WhenAll(  
    from url in urls select DownloadStringAsync(url));  
```  
  
 Biz önceki void döndürme senaryoda açıklanan aynı özel durum işleme teknikleri kullanabilirsiniz:  
  
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
 Kullanabileceğiniz <xref:System.Threading.Tasks.Task.WhenAny%2A> zaman uyumsuz olarak birden çok zaman uyumsuz işlemleri yalnızca biri için beklenecek yöntemi temsil edilen görevleri tamamlamak için.  Bu yöntem, dört birincil kullanım örnekleri hizmet eder:  
  
-   Artıklık: birden çok kez bir işlemi gerçekleştirilirken ve ilk (örneğin, tek bir sonuç oluşturur birden çok hisse senedi web Hizmetleri iletişim kurmasını ve hızlı tamamlanır seçmenizi) tamamlandıktan birini seçerek.  
  
-   Interleaving: birden çok işlem başlatma ve tüm bunların tamamlanması bekleniyor, ancak tamamlandıkça işlemeden.  
  
-   Azaltma: başkalarının tamamlandı olarak başlamak ek işlem yapılmasına olanak sağlar.  Bu bir araya senaryo uzantısıdır.  
  
-   Erken BailOut komutunu: Örneğin, görev t1 tarafından temsil edilen bir işlem içinde gruplandırılabilir bir <xref:System.Threading.Tasks.Task.WhenAny%2A> başka bir görev t2 ve görevle bekleyin <xref:System.Threading.Tasks.Task.WhenAny%2A> görev. Görev t2'ın temsil eden bir zaman aşımı veya iptal ya da neden olan bazı bir sinyal <xref:System.Threading.Tasks.Task.WhenAny%2A> t1 tamamlanmadan önce görev.  
  
#### <a name="redundancy"></a>Artıklık  
 Hisse satın konusunda karar istediğiniz bir durum düşünün.  Güvendiğiniz birkaç stok öneri web hizmetleri vardır, ancak günlük yüke bağlı olarak, her bir hizmet farklı zamanlarda yavaş olduğundan yukarı sona erdirebilirsiniz.  Kullanabileceğiniz <xref:System.Threading.Tasks.Task.WhenAny%2A> yöntemi herhangi bir işlem tamamlandığında bildirim almak için:  
  
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
  
 Farklı <xref:System.Threading.Tasks.Task.WhenAll%2A>, işleminin başarıyla tamamlandığını tüm görevlerin sarmalanmamış sonuçları döndüren <xref:System.Threading.Tasks.Task.WhenAny%2A> tamamlanan görev döndürür. Bir görev başarısız olursa, başarısız ve bir görev başarılı olursa, hangi görev dönüş değeri ile ilişkili olduğunu bilmeniz önemli olduğunu bilmek önemlidir.  Bu nedenle, bu örnekte gösterildiği gibi döndürülen görev sonucu erişim ya da daha fazla, beklemek gerekir.  
  
 İle <xref:System.Threading.Tasks.Task.WhenAll%2A>, istisnalara uyum sağlamaya mümkün olması gerekir.  Tamamlanan görevin geri aldıklarından yayılan, hatalarının bildirilmesini döndürülen görev await ve `try/catch` bunları uygun şekilde; örneğin:  
  
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
  
 Ayrıca, ilk görevi başarıyla tamamlandıktan olsa bile, sonraki görevleri başarısız olabilir.  Bu noktada, özel durumlar ilgilenmek için birkaç seçeneğiniz vardır:; Bu durumda kullanabileceğiniz tüm başlatılan görevlerini tamamlayıncaya kadar bekleyebilirsiniz <xref:System.Threading.Tasks.Task.WhenAll%2A> yöntemi ya da siz karar tüm özel durumları önemlidir ve oturum açmış olmanız gerekir.  Bunun için zaman uyumsuz olarak görevleri tamamladıktan sonra bir bildirim almak için devamlılıklar kullanabilirsiniz:  
  
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
  
 ya da hatta:  
  
```  
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
  
#### <a name="interleaving"></a>Araya ekleme  
 Burada görüntüleri Web'den ve (örneğin, bir kullanıcı Arabirimi denetim için görüntü ekleme) her görüntü işleme bir durum düşünün.  Sıralı olarak kullanıcı Arabirimi iş parçacığı üzerinde işlem yapmanız gereken, ancak görüntüleri olarak aynı anda indirmek istediğiniz. Ayrıca, tüm karşıdan kadar görüntüler için kullanıcı Arabirimi ekleme tutacak istemediğiniz — tamamlandıkça bunları eklemek istediğiniz:  
  
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
  
 Üzerinde pkı'ya yoğun işleme içeren bir senaryo için Interleaving uygulayabilirsiniz <xref:System.Threading.ThreadPool> indirilen görüntülerinin; örneğin:  
  
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
 Kullanıcı yüklemeleri kısıtlanan gerektiğini çok fazla sayıda resimler karşıdan dışında araya örneği göz önünde bulundurun; Örneğin, belirli sayıda eşzamanlı olarak gerçekleşecek şekilde yüklemeleri istiyorsunuz. Bunu başarmak için bir alt kümesini zaman uyumsuz işlemleri başlatabilirsiniz.  İşlem tamamlanmış olarak kendi gerçekleşmesi için ek işlemler başlatabilirsiniz:  
  
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
 Zaman uyumsuz bir işlemin aynı anda bir kullanıcının iptal isteğini yanıtlarken tamamlanmasını bekleme olduğunu göz önünde bulundurun (örneğin, kullanıcının iptal düğmesine tıklanana). Aşağıdaki kod bu senaryo gösterilmektedir:  
  
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
  
 Bail karar, ancak temel alınan zaman uyumsuz işlemleri iptal değil hemen sonra bu uygulama kullanıcı arabirimi yeniden etkinleştirir.  Başka bir alternatif bail, ancak kullanıcı arabirimi tamamladığınız, büyük olasılıkla nedeniyle iptal isteği nedeniyle erken bitiş işlemleri kadar oluşturmayacak karar verirken bekleyen işlemler iptal etmek için olacaktır:  
  
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
  
 Erken BailOut komutunu başka bir örneği kullanılmasına <xref:System.Threading.Tasks.Task.WhenAny%2A> yöntemi ile birlikte <xref:System.Threading.Tasks.Task.Delay%2A> sonraki bölümde açıklandığı gibi yöntemi.  
  
### <a name="taskdelay"></a>Task.Delay  
 Kullanabileceğiniz <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> tanıtmak için yöntemi zaman uyumsuz bir yöntemin yürütme duraklatır.  Bu işlevsellik, yoklama döngüsü oluşturma ve kullanıcı girişini işleme önceden belirlenmiş bir süre için geciktirme dahil olmak üzere çok çeşitli için kullanışlıdır.  <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> Yöntemi de birlikte yararlı olabilir <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> üzerinde zaman aşımlarını uygulayarak bekler için.  
  
 Daha büyük bir zaman uyumsuz işlemi (örneğin, bir ASP.NET web hizmeti) bir parçası olan bir görev tamamlanması çok uzun sürerse, genel işlem yaşar, özellikle için herhangi bir zamanda başarısız olursa tamamlayın.  Bu nedenle, zaman uyumsuz bir işlem üzerinde beklenirken zaman aşımına olması önemlidir.  Zaman uyumlu <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, ve <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> yöntemleri karşılık gelen ancak zaman aşımı değerlerini kabul <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> ve yukarıda açıklanan <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>yöntemleri desteklemez.  Bunun yerine, kullanabileceğiniz <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> birlikte bir zaman aşımı uygulamak için.  
  
 Örneğin, kullanıcı Arabirimi uygulamanızda bir görüntüsünü karşıdan yüklemek ve görüntünün indirirken kullanıcı arabirimini devre dışı bırakmak istediğinizi varsayalım. Ancak, indirme çok uzun sürerse, kullanıcı arabirimini yeniden etkinleştirin ve indirme atmak istiyor:  
  
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
  
 Aynı olduğundan birden çok yüklemeler için geçerlidir <xref:System.Threading.Tasks.Task.WhenAll%2A> bir görev döndürür:  
  
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
  
## <a name="building-task-based-combinators"></a>Görev tabanlı Combinators oluşturma  
 Bir görev tamamen zaman uyumsuz işlemi temsil eden ve işlemiyle katılmak için zaman uyumlu ve zaman uyumsuz yetenekleri sağlamak mümkün olduğundan, kendi sonuçları ve benzeri, alma, görevler oluşturma combinators yararlı kitaplıklarının oluşturabilirsiniz daha büyük desenleri oluşturun.  Önceki bölümde açıklandığı gibi .NET Framework birkaç yerleşik combinators içerir, ancak Ayrıca kendi oluşturabilirsiniz. Aşağıdaki bölümlerde olası birleştiriciden yöntemleri ve türleri bazı örnekleri verilmiştir.  
  
### <a name="retryonfault"></a>RetryOnFault  
 Çoğu durumda, önceki girişim başarısız olursa bir işlemi yeniden denemek isteyebilirsiniz.  Zaman uyumlu bir kod için bir yardımcı yöntemi gibi oluşturabilir `RetryOnFault` Bunu başarmak için aşağıdaki örnekte:  
  
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
  
 Neredeyse aynı yardımcı yöntem DOKUNMAYLA uygulanır ve bu nedenle görevleri zaman uyumsuz işlemleri için oluşturabilirsiniz:  
  
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
  
 Daha sonra yeniden deneme uygulamanın mantığı kodlamak için bu birleştiriciden kullanabilirsiniz; Örneğin:  
  
```csharp  
// Download the URL, trying up to three times in case of failure  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3);  
```  
  
 Genişletme `RetryOnFault` daha fazla işlev. İşlevin başka bir örneğin kabul edebilecek `Func<Task>` , çağrılabilir yeniden denemeler arasında yeniden; örneğin işlemi denemek ne zaman belirlemek için:  
  
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
  
 Daha sonra işlevi aşağıdaki gibi işlemi yeniden denemeden önce ikinci bir beklemek için kullanabilirsiniz:  
  
```csharp  
// Download the URL, trying up to three times in case of failure,  
// and delaying for a second between retries  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));  
```  
  
### <a name="needonlyone"></a>NeedOnlyOne  
 Bazı durumlarda, bir işlemin gecikme süresi ve başarı olasılığını artırmak için artıklık yararlanabilir.  Borsa bilgileri sağlayan birden çok web hizmetleri düşünün, ancak çeşitli zamanlarda günün, her hizmetin kalitesi ve yanıt sürelerini farklı düzeylerde sağlayabilir.  Bu dalgalanmaları ile mücadele etmek için tüm web hizmetlerine isteklerini yürütmek ve birinden, bir yanıt elde hemen sonra kalan istekleri iptal.  Birden çok işlem başlatma, için bekleyen ve rest iptal etme ortak bu deseni uygulayan kolaylaştırmak için yardımcı bir işlev uygulayabilirsiniz. `NeedOnlyOne` İşlevi aşağıdaki örnekte, bu senaryo gösterilmektedir:  
  
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
  
 Ardından, bu işlevi aşağıdaki gibi kullanabilirsiniz:  
  
```csharp  
double currentPrice = await NeedOnlyOne(  
    ct => GetCurrentPriceFromServer1Async("msft", ct),  
    ct => GetCurrentPriceFromServer2Async("msft", ct),  
    ct => GetCurrentPriceFromServer3Async("msft", ct));  
```  
  
### <a name="interleaved-operations"></a>Araya eklemeli işlemleri  
 Kullanarak olası performans sorunu <xref:System.Threading.Tasks.Task.WhenAny%2A> görevleri çok büyük kümeleriyle çalışırken bir araya senaryoyu desteklemek için yöntem.  Her çağrı için <xref:System.Threading.Tasks.Task.WhenAny%2A> her görevle Kaydedilmekte devamlılık sonuçlanıyor. N sayıda görev için bu araya işlemi ömrü boyunca oluşturulan O(N2) devamlılıklar sonuçlanır.  Çok sayıda görev ile çalışıyorsanız, birleştiriciden kullanabilirsiniz (`Interleaved` aşağıdaki örnekte) performans sorunu gidermek için:  
  
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
  
 Ardından, görevlerin sonuçları tamamlandıkça için birleştiriciden kullanabilirsiniz; Örneğin:  
  
```csharp  
IEnumerable<Task<int>> tasks = ...;  
foreach(var task in Interleaved(tasks))  
{  
    int result = await task;  
    …  
}  
```  
  
### <a name="whenallorfirstexception"></a>WhenAllOrFirstException  
 Bunlardan biri, özel durum oluştu hemen beklemeyin istediğiniz; bu durumda hataları sürece belirli dağıtma/toplama senaryolarda kümesinde, tüm görevler için bekleyin isteyebilirsiniz.  Bir birleştiriciden yöntemiyle gibi gerçekleştirebilirsiniz `WhenAllOrFirstException` aşağıdaki örnekte:  
  
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
  
## <a name="building-task-based-data-structures"></a>Yapı görev tabanlı veri yapıları  
 Özel görev tabanlı combinators oluşturmak için ek olarak, bir veri yapısı yaramasını <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> hem sonuçlarını zaman uyumsuz işlemi temsil eden ve onunla katılmak için gerekli eşitleme çok güçlü yapar zaman uyumsuz senaryolarında kullanılacak özel veri yapılarını oluşturulacağı yazın.  
  
### <a name="asynccache"></a>AsyncCache  
 Önemli bir görev yönüdür bunu kime tümünün await, kayıt devamlılıklar, ile birden çok tüketiciye karmalayan olduğunu edinebileceğinizi sonuç veya özel durumları (durumunda <xref:System.Threading.Tasks.Task%601>) ve benzeri.  Böylece <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> mükemmel uygun bir zaman uyumsuz önbelleğe alma altyapısı kullanılacak.  Küçük bir örneği burada verilmiştir ancak güçlü zaman uyumsuz önbellek yerleşik üstünde <xref:System.Threading.Tasks.Task%601>:  
  
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
  
 [AsyncCache\<TKey, TValue >](https://blogs.msdn.microsoft.com/pfxteam/2010/04/23/parallelextensionsextras-tour-12-asynccache/) sınıfı kabul kendi oluşturucusunu temsilci olarak isteyen bir işlevi bir `TKey` ve döndüren bir <xref:System.Threading.Tasks.Task%601>.  Daha önce erişilen tüm değerler önbellekten iç sözlükte depolanır ve `AsyncCache` önbellek eşzamanlı olarak erişilen bile, yalnızca görev anahtar oluşturulan sağlar.  
  
 Örneğin, indirilen web sayfaları için bir önbellek oluşturabilirsiniz:  
  
```csharp  
private AsyncCache<string,string> m_webPages =   
    new AsyncCache<string,string>(DownloadStringAsync);  
```  
  
 Bir web sayfasının içeriği gerektiğinde daha sonra bu önbellek zaman uyumsuz yöntemler kullanabilirsiniz. `AsyncCache` Sınıfı sağlar, olabildiğince az sayfaları olası ve önbellekleri sonuçları karşıdan yükleme olduğunu.  
  
```csharp  
private async void btnDownload_Click(object sender, RoutedEventArgs e)   
{  
    btnDownload.IsEnabled = false;  
    try  
    {  
        txtContents.Text = await m_webPages["http://www.microsoft.com"];  
    }  
    finally { btnDownload.IsEnabled = true; }  
}  
```  
  
### <a name="asyncproducerconsumercollection"></a>AsyncProducerConsumerCollection  
 Görevler, zaman uyumsuz etkinlikleri Eşgüdümleme için veri yapılarını oluşturmak için de kullanabilirsiniz.  Klasik paralel tasarım desenleri birini göz önünde bulundurun: üretici/tüketici.  Bu desen tüketiciler tarafından tüketilen veri üreticileri oluşturmak ve üreticileri ve tüketicileri paralel olarak çalışabilir. Örneğin, tüketici 2 öğesi artık üreten bir üretici tarafından önceden oluşturulan 1, öğeyi işler.  Üretici/tüketici düzeni için neredeyse şaşmaz biçimde tüketiciler yeni verileri bildirilebilir ve kullanılabilir olduğunda bulmak için üreticileri tarafından oluşturulan iş depolamak için bazı veri yapısı gerekir.  
  
 Üreticileri ve tüketicileri kullanılacak zaman uyumsuz yöntemleri sağlayan basit veri yapısı üstünde görevler yerleşik şöyledir:  
  
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
  
 Yerinde veri yapıyı ile aşağıdaki gibi kod yazabilirsiniz:  
  
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
  
 <xref:System.Threading.Tasks.Dataflow> Ad alanı içeren <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> , benzer şekilde kullanabilirsiniz, ancak özel koleksiyon türü oluşturmak zorunda kalmadan türü:  
  
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
>  <xref:System.Threading.Tasks.Dataflow> Ad alanı bulunan [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] aracılığıyla **NuGet**. İçeren derlemenin yüklemek için <xref:System.Threading.Tasks.Dataflow> ad alanı, projenizi açın [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], seçin **NuGet paketlerini Yönet** proje menüsünden ve çevrimiçi Microsoft.Tpl.Dataflow paketi için arama.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 [Görev Tabanlı Zaman Uyumsuz Deseni Uygulama](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
 [Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
