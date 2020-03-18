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
ms.openlocfilehash: f80e6ae520ab03c0f5f4edc30c0b7102193ee6c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139821"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a>Görev Tabanlı Zaman Uyumsuz Desen Kullanma

Asynchronous işlemleriyle çalışmak için Görev Tabanlı Eşenkron Desen'i (TAP) kullandığınızda, engellemeden beklemeyi başarmak için geri aramaları kullanabilirsiniz.  Görevler için bu, <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>. Dil tabanlı eşzamanlı destek, normal denetim akışı içinde asenkron işlemlerin beklenmesine izin vererek geri aramaları gizler ve derleyici tarafından oluşturulan kod aynı API düzeyinde destek sağlar.

## <a name="suspending-execution-with-await"></a>Bekleme ile Yürütmeyi Askıya Alma
 .NET Framework 4.5'ten başlayarak C#'daki [bekleme](../../csharp/language-reference/operators/await.md) anahtar sözcüklerini ve Visual Basic'teki <xref:System.Threading.Tasks.Task%601> Bekleme [Operatör'üni](../../visual-basic/language-reference/operators/await-operator.md) eşzamanlı olarak bekliyor <xref:System.Threading.Tasks.Task> ve nesneleri kullanabilirsiniz. Bir <xref:System.Threading.Tasks.Task>, `await` ifade yi beklerken. `void` Bir <xref:System.Threading.Tasks.Task%601>, `await` ifade yi beklerken. `TResult` Bir `await` ifade bir asynchronous yönteminin gövdesi içinde meydana gelmelidir. .NET Framework 4.5'te C# ve Visual Basic dil desteği hakkında daha fazla bilgi için C# ve Visual Basic dil belirtimleri'ne bakın.

 Kapakların altında, bekleme işlevi bir devamı kullanarak göreve bir geri arama yükler.  Bu geri arama süspansiyon noktasında asynchronous yöntemi devam eder. Eşkron yöntem sürdürüldüğünde, beklenen işlem başarıyla tamamlanıp , <xref:System.Threading.Tasks.Task%601>onun `TResult` döndürülür.  Beklenen <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> beklenen <xref:System.Threading.Tasks.TaskStatus.Canceled> durumda sona erdiyse, <xref:System.OperationCanceledException> bir özel durum atılır.  Beklenen <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> beklenen <xref:System.Threading.Tasks.TaskStatus.Faulted> durum sona erdiyse, hataya neden olan özel durum atılır. A, `Task` birden çok özel durum sonucunda hata yapabilir, ancak bu özel durumlardan yalnızca biri yayılır. Ancak, <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> özellik tüm <xref:System.AggregateException> hataları içeren bir özel durum döndürür.

 Bir eşitleme bağlamı<xref:System.Threading.SynchronizationContext> (nesnesi) askıya alma sırasında asenkron yöntemi ni gerçekleştiren iş parçacığıyla <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> ilişkilendirilirse (örneğin, özellik değilse), `null`eş zamanlı yöntem bağlamın <xref:System.Threading.SynchronizationContext.Post%2A> yöntemini kullanarak aynı eşitleme bağlamında devam eder. Aksi takdirde, askıya alma sırasında<xref:System.Threading.Tasks.TaskScheduler> geçerli olan görev zamanlayıcısına (nesne) dayanır. Genellikle, bu iş parçacığı havuzu<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>hedefleyen varsayılan görev zamanlayıcısı ( ), olduğunu. Bu görev zamanlayıcısı, beklenen eşsenkronize işlemin tamamlandığı yerde devam edip etmeyeceğini veya yeniden başlamanın zamanlanıp zamanlanmayacağını belirler. Varsayılan zamanlayıcı genellikle devamın beklenen işlemin tamamlandığı iş parçacığında çalışmasına izin verir.

 Bir eşzamanlı yöntem çağrıldığında, çağrının arayana döndüğü, henüz tamamlanmamış bir bekleyen örnekte ilk bekleyen ifadeye kadar işlevin gövdesini eşzamanlı olarak yürütür. Eşsenkron yöntem geri dönmezse, `void` <xref:System.Threading.Tasks.Task> devam <xref:System.Threading.Tasks.Task%601> eden hesaplamayı temsil etmek için bir veya nesne döndürülür. Geçersiz olmayan bir eşzamanlı yöntemde, bir iade deyimiyle karşılaşılırsa veya yöntem gövdesinin sonuna ulaşılırsa, <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> görev son durumda tamamlanır. Işlenmemiş bir özel durum denetimin eşzamanlı yöntemin gövdesinden ayrılmasına neden <xref:System.Threading.Tasks.TaskStatus.Faulted> olursa, görev durumla biter. Bu özel durum <xref:System.OperationCanceledException>bir ise, görev <xref:System.Threading.Tasks.TaskStatus.Canceled> yerine durumda sona erer. Bu şekilde, sonuç veya özel durum sonunda yayımlanır.

 Bu davranışın birkaç önemli varyasyonları vardır.  Performans nedenleriyle, görev beklenene kadar bir görev zaten tamamlanmışsa, denetim verim verilmeyecek ve işlev yürütmeye devam eder.  Ayrıca, özgün içeriğe dönmek her zaman istenen davranış değildir ve değiştirilebilir; bu sonraki bölümde daha ayrıntılı olarak açıklanmıştır.

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a>Verim ve Yapılandırma Ile Süspansiyon ve Devamı Yapılandırma
 Çeşitli yöntemler, bir eşzamanlı yöntemin yürütülmesi üzerinde daha fazla denetim sağlar. Örneğin, asynchronous <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> yöntemine bir verim noktası tanıtmak için yöntemi kullanabilirsiniz:

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 Bu, eşzamanlı olarak geçerli içeriğe yeniden deftere nakletmeye veya zamanlamaya eşdeğerdir.

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

 Ayrıca asynchronous yöntemi süspansiyon ve devamı üzerinde daha iyi kontrol için <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> yöntemi kullanabilirsiniz.  Daha önce de belirtildiği gibi, varsayılan olarak, geçerli bağlam bir eşzamanlı yöntem askıya alındı ve yakalanan bağlam devam ı üzerine asynchronous yöntemin devamını çağırmak için kullanılır yakalanır.  Çoğu durumda, bu tam olarak istediğiniz davranıştır.  Diğer durumlarda, devam bağlamını önemsemeyebilirsiniz ve bu tür gönderileri özgün içeriğe geri döndürerek daha iyi performans elde edebilirsiniz.  Bunu etkinleştirmek için, bekleme işlemini bağlamında yakalamamak ve devam ettirmek için değil, beklenen eşzamanlı işlemin tamamlandığı her yerde yürütmeye devam etmek için bu <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> yöntemi kullanın:

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a>Eşkron İşlemi İptal Etme
 .NET Framework 4'ten başlayarak, iptali destekleyen TAP yöntemleri, iptal jetonu<xref:System.Threading.CancellationToken> (nesne) kabul eden en az bir aşırı yükleme sağlar.

 İptal belirteci, iptal jetonu kaynağı<xref:System.Threading.CancellationTokenSource> (nesne) aracılığıyla oluşturulur.  Kaynağın <xref:System.Threading.CancellationTokenSource.Token%2A> özelliği, kaynağın <xref:System.Threading.CancellationTokenSource.Cancel%2A> yöntemi çağrıldığında işaretlenecek iptal belirteci döndürür.  Örneğin, tek bir web sayfası indirmek istiyorsanız ve işlemi iptal etmek istiyorsanız, <xref:System.Threading.CancellationTokenSource> bir nesne oluşturursunuz, belirteciTAP yöntemine geçer <xref:System.Threading.CancellationTokenSource.Cancel%2A> ve işlemi iptal etmeye hazır olduğunuzda kaynağın yöntemini ararsınız:

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 Birden çok eşzamanlı çağrıyı iptal etmek için, aynı belirteci tüm çağırmalara geçirebilirsiniz:

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 Veya, aynı belirteci seçici bir işlem alt kümesine geçirebilirsiniz:

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 İptal talepleri herhangi bir iş parçacığı başlatılabilir.

 <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> İptal talebinde bulunulamayacağını belirtmek için değeri iptal jetonu kabul eden herhangi bir yönteme geçirebilirsiniz.  Bu özelliğin <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> dönmesine `false`neden olur ve çağrılan yöntem buna göre en iyi duruma getirebilir.  Test amacıyla, belirteç zaten iptal edilmiş veya iptal edilemeyen bir durumda başlaması gerektiğini belirtmek için Boolean değerini kabul eden oluşturucuyu kullanarak anında iptal edilmiş bir iptal belirteci de geçebilirsiniz.

 İptal için bu yaklaşımın birkaç avantajı vardır:

- Aynı iptal belirtecinizi herhangi bir sayıda ki eşzamanlı ve eşzamanlı işlemlere aktarabilirsiniz.

- Aynı iptal isteği herhangi bir sayıda dinleyiciye çoğaltılabilir.

- Eşzamanlı API'nin geliştiricisi, iptalin istenip istenmeyeceğini ve ne zaman yürürlüğe girebileceğini tam olarak kontrol eder.

- API'yi tüketen kod, iptal isteklerinin yayılacağı asynchronous davetlerini seçişle belirleyebilir.

## <a name="monitoring-progress"></a>İlerlemeyi İzleme
 Bazı eşzamanlı yöntemler, asynchronous yöntemine aktarılan ilerleme arabirimi aracılığıyla ilerlemeyi ortaya çıkarır.  Örneğin, eş senkronize bir metin dizesini karşıdan yükleyen ve yol boyunca şimdiye kadar tamamlanan karşıdan yükleme yüzdesini içeren ilerleme güncelleştirmelerini yükselten bir işlev düşünün.  Böyle bir yöntem bir Windows Presentation Foundation (WPF) uygulamasında aşağıdaki gibi tüketilebilir:

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
## <a name="using-the-built-in-task-based-combinators"></a>Yerleşik Görev Tabanlı Kombinatörleri Kullanma
 Ad <xref:System.Threading.Tasks> alanı, görevleri oluşturmak ve çalışmak için çeşitli yöntemler içerir.

### <a name="taskrun"></a>Görev.Çalıştır
 Sınıf, <xref:System.Threading.Tasks.Task> örneğin <xref:System.Threading.Tasks.Task.Run%2A> iş parçacığı havuzunda <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> çalışmayı kolayca boşaltmanızı sağlayan çeşitli yöntemler içerir:

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

 Aşırı yükleme <xref:System.Threading.Tasks.Task.Run%2A> gibi bu yöntemlerden <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> bazıları yöntem için kısaltma olarak bulunur. <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>  Diğer aşırı yüklemeler, <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>örneğin, boşaltılmış iş içinde beklemeyi kullanmanıza olanak sağlar:

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

 Bu tür aşırı yüklemeler, <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> Görev Paralel Kitaplığı'ndaki <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> uzantı yöntemiyle birlikte yöntemi kullanmaya mantıksal olarak eşdeğerdir.

### <a name="taskfromresult"></a>Görev.Kaynak
 Verilerin <xref:System.Threading.Tasks.Task.FromResult%2A> zaten mevcut olabileceği ve görev döndürme yönteminden döndürülmesi gereken senaryolarda yöntemi <xref:System.Threading.Tasks.Task%601>kullanın:

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
 Görev <xref:System.Threading.Tasks.Task.WhenAll%2A> olarak temsil edilen birden çok eşzamanlı işlemi eş senkronize olarak beklemek için yöntemi kullanın.  Yöntem, genel olmayan bir görev kümesini veya tek düze olmayan genel görevleri (örneğin, birden çok geçersiz döndüren işlemi bekleyen veya her değerin farklı bir türü olabileceği birden çok değer döndüren yöntemi bekleyen) ve tek tip genel `TResult`görevleri (eşzamanlı olarak birden çok dönen yöntemleri beklemek gibi) destekleyen birden çok fazla yüklemeye sahiptir.

 Birkaç müşteriye e-posta iletisi göndermek istediğinizi varsayalım. İletileri göndermenin çakışmasını sağlayabilirsiniz, böylece bir sonraki iletiyi göndermeden önce bir iletinin tamamlanmasını beklemezsiniz. Ayrıca, gönderme işlemlerinin ne zaman tamamlandığını ve herhangi bir hata nın oluşup oluşmadığını da öğrenebilirsiniz:

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 Bu kod, oluşabilecek özel durumları açıkça işlemez, ancak özel durumlar `await` <xref:System.Threading.Tasks.Task.WhenAll%2A>' dan gelen 'den kaynaklanan görevin dışına yayılmasına izin verir.  Özel durumları işlemek için aşağıdaki gibi kod kullanabilirsiniz:

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

 Bu durumda, herhangi bir eşyokolün işlemi başarısız olursa, tüm <xref:System.AggregateException> özel durumlar <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task.WhenAll%2A> yöntemden döndürülen depolanan bir özel durum olarak birleştirilir.  Ancak, bu özel durumlardan yalnızca biri `await` anahtar kelime tarafından yayılır.  Tüm özel durumları incelemek istiyorsanız, önceki kodu aşağıdaki gibi yeniden yazabilirsiniz:

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

 Web'den eşzamanlı olarak birden fazla dosya indirme örneğini ele alalım.  Bu durumda, tüm eşzamanlı işlemlerhomojen sonuç türlerine sahiptir ve sonuçlara erişmek kolaydır:

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 Önceki geçersiz döndürme senaryosunda tartıştığımız aynı özel durum işleme tekniklerini kullanabilirsiniz:

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
 <xref:System.Threading.Tasks.Task.WhenAny%2A> Tamamlanmagörevi olarak temsil edilen birden çok eşzamanlı işlemden yalnızca birini beklemek için yöntemi kullanabilirsiniz.  Bu yöntem dört birincil kullanım örnekleri ne hizmet vermektedir:

- Artıklık: Bir işlemi birden çok kez gerçekleştirmek ve ilk tamamlananı seçmek (örneğin, tek bir sonuç üretecek birden çok hisse senedi teklifi web hizmetleriyle iletişim kurmak ve en hızlı tamamlananı seçmek).

- Ayrılma: Birden çok işlemi başlatmak ve hepsinin tamamlanmasını beklemek, ancak tamamlandıkça işleme.

- Azaltma: Diğerleri tamamlandıkça ek işlemlerin başlamasına izin verme.  Bu, ayrılma senaryosunun bir uzantısıdır.

- Erken kurtarma: Örneğin, görev t1 tarafından temsil edilen bir <xref:System.Threading.Tasks.Task.WhenAny%2A> işlem başka bir görev t2 ile <xref:System.Threading.Tasks.Task.WhenAny%2A> bir görev gruplandırılabilir ve görev üzerinde bekleyebilirsiniz. Görev t2 bir zaman-out veya iptal veya t1 <xref:System.Threading.Tasks.Task.WhenAny%2A> tamamlanmadan önce görev tamamlanmasına neden başka bir sinyal temsil edebilir.

#### <a name="redundancy"></a>Yedeklilik
 Hisse senedi alıp almayacağınız konusunda karar vermek istediğiniz bir durumu düşünün.  Güvendiğiniz birkaç hisse senedi tavsiyesi web hizmetleri vardır, ancak günlük yüke bağlı olarak, her hizmet farklı zamanlarda yavaş sona erebilir.  Herhangi bir <xref:System.Threading.Tasks.Task.WhenAny%2A> işlem tamamlandığında bildirim almak için yöntemi kullanabilirsiniz:

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

 Başarıyla tamamlanan tüm görevlerin paketlenmemiş sonuçlarını <xref:System.Threading.Tasks.Task.WhenAll%2A>döndüren, tamamlanan görevi <xref:System.Threading.Tasks.Task.WhenAny%2A> döndürür. Bir görev başarısız olursa, başarısız olduğunu bilmek önemlidir ve bir görev başarılı olursa, iade değerinin hangi görevle ilişkili olduğunu bilmek önemlidir.  Bu nedenle, döndürülen görevin sonucuna erişmeniz veya bu örneğin gösterdiği gibi daha fazla beklemeniz gerekir.

 Olduğu <xref:System.Threading.Tasks.Task.WhenAll%2A>gibi, özel durumlara uyum sağlamak gerekir.  Tamamlanan görevi geri aldığınızdan, döndürülen görevi hataların yayılmasını ve `try/catch` uygun şekilde yayılmasını bekleyebilirsiniz; örneğin:

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

 Ayrıca, ilk görev başarıyla tamamlaşsa bile, sonraki görevler başarısız olabilir.  Bu noktada, özel durumlarla başa çıkmak için çeşitli seçenekleriniz vardır: Başlatılan tüm görevler tamamlanana <xref:System.Threading.Tasks.Task.WhenAll%2A> kadar bekleyebilir, bu durumda yöntemi kullanabilirsiniz veya tüm özel durumların önemli olduğuna ve günlüğe kaydedilmesi gerektiğine karar verebilirsiniz.  Bunun için, görevler eşeşitle tamamlandığında bildirim almak için devamları kullanabilirsiniz:

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

#### <a name="interleaving"></a>Aralaması
 Web'den resim indirdiğiniz ve her görüntüyü işlediğiniz (örneğin, görüntüyü ui denetimine ekleme) bir durum düşünün.  İşlemi UI iş parçacığıüzerinde sırayla yapmanız gerekir, ancak görüntüleri mümkün olduğunca aynı anda indirmek istersiniz. Ayrıca, görüntüleri indirilene kadar UI'ye eklemeyi ertelemek istemezsiniz— tamamlanırken eklemek istiyorsunuz:

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

 İndirilen görüntülerin üzerinde <xref:System.Threading.ThreadPool> hesaplama açısından yoğun işlem içeren bir senaryoya ara ayrılma da uygulayabilirsiniz; örneğin:

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

#### <a name="throttling"></a>Azaltma
 Kullanıcının o kadar çok resim indiriyor olması ve indirmelerin azaltılması gerektiği dışında, ara ayrılma örneğini göz önünde bulundurun; örneğin, yalnızca belirli sayıda indirmenin aynı anda gerçekleşmesini istiyorsunuz. Bunu başarmak için, eşzamanlı işlemlerin bir alt kümesini başlatabilirsiniz.  İşlemler tamamlandıkça, onların yerini almak için ek işlemler başlatabilirsiniz:

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

#### <a name="early-bailout"></a>Erken Kurtarma
 Bir kullanıcının iptal isteğine aynı anda yanıt verirken bir işlemin tamamlanmasını eş zamanlı olarak beklediğiniz göz önünde bulundurun (örneğin, kullanıcı bir iptal düğmesini tıklattı). Aşağıdaki kod bu senaryoyu göstermektedir:

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

 Bu uygulama, siz ödemeye karar verir vermez kullanıcı arabirimini yeniden etkinleştirir, ancak temel asenkron işlemleri iptal etmez.  Başka bir alternatif, kurtarma kararı aldığınızda bekleyen işlemleri iptal etmek, ancak iptal isteği nedeniyle erken sona ermesi nedeniyle işlemler gerçekten tamamlanana kadar kullanıcı arabirimini yeniden kurmamak olacaktır:

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

 Erken kurtarma başka bir <xref:System.Threading.Tasks.Task.WhenAny%2A> örnek, bir <xref:System.Threading.Tasks.Task.Delay%2A> sonraki bölümde ele alındığı gibi, yöntem ile birlikte yöntemi kullanarak içerir.

### <a name="taskdelay"></a>Task.Delay
 Asynchronous <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> yöntemyürütme içine duraklatma tanıtmak için yöntemi kullanabilirsiniz.  Bu, yoklama döngüleri oluşturma ve kullanıcı girişinin işlenmesini önceden belirlenmiş bir süre için geciktirme de dahil olmak üzere birçok işlevsellik türü için yararlıdır.  Yöntem, <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> bekleme lerde zaman <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> çıkışları uygulamak için birlikte de yararlı olabilir.

 Daha büyük bir eşzamanlı işlemin parçası olan bir görevin (örneğin, ASP.NET bir web hizmetinin) tamamlanması çok uzun sürerse, genel işlem özellikle tamamlanmamışsa zarar görebilir.  Bu nedenle, bir eşzamanlı işlemi beklerken zaman dışarı edebilmek önemlidir.  Senkron <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>ve <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> yöntemler zaman dışarı değerleri kabul, <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> ancak karşılık gelen <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> ve daha önce belirtilen yöntemler yok.  Bunun yerine, <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> bir <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> zaman-out uygulamak için kullanabilirsiniz ve birlikte.

 Örneğin, Kullanıcı Arabirimi uygulamanızda, bir resim indirmek ve görüntü indirirken Kullanıcı Arabirimi'ni devre dışı bırakmak istediğinizi varsayalım. Ancak, indirme çok uzun sürerse, UI'yi yeniden etkinleştirmek ve karşıdan yüklemeyi atmak istiyorsunuz:

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

 Aynı durum birden çok indirme <xref:System.Threading.Tasks.Task.WhenAll%2A> için de geçerlidir, çünkü bir görevi döndürür:

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

## <a name="building-task-based-combinators"></a>Görev Tabanlı Kombinatörler Oluşturma
 Bir görev tamamen bir eşzamanlı işlemi temsil edebilir ve operasyona katılmak, sonuçlarını almak ve benzeri için senkron ve eşzamanlı yetenekler sağlayabildiği için, görevleri oluşturan kombinatörlerin yararlı kitaplıklarını oluşturabilirsiniz daha büyük desenler oluşturun.  Önceki bölümde ele alındığı gibi, .NET Framework birkaç yerleşik kombinör içerir, ancak kendi de oluşturabilirsiniz. Aşağıdaki bölümlerde potansiyel kombinatör yöntemleri ve türleri birkaç örnek sağlar.

### <a name="retryonfault"></a>RetryOnFault
 Birçok durumda, önceki bir deneme başarısız olursa bir işlemi yeniden denemek isteyebilirsiniz.  Senkron kod için, bunu gerçekleştirmek için aşağıdaki `RetryOnFault` örnekte olduğu gibi bir yardımcı yöntemi oluşturabilirsiniz:

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

 TAP ile uygulanan eşzamanlı işlemler için hemen hemen aynı yardımcı yöntemi oluşturabilir ve böylece görevleri döndürebilirsiniz:

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

 Daha sonra bu kombinatörün uygulamanın mantığına yeniden denemeleri kodlamak için kullanabilirsiniz; örneğin:

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 İşlevi daha `RetryOnFault` da genişletebilirsiniz. Örneğin, işlev, işlemi `Func<Task>` yeniden ne zaman deneyeceğini belirlemek için yeniden denemeler arasında çağrılacak başka bir işlevi kabul edebilir; örneğin:

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

 Daha sonra işlemi yeniden denemeden önce bir saniye beklemek için aşağıdaki işlevi kullanabilirsiniz:

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a>NeedOnlyOne
 Bazen, bir işlemin gecikmesini ve başarı şansını artırmak için artıklılılılılılılılığınızdan yararlanabilirsiniz.  Hisse senedi fiyatları sağlayan birden çok web hizmetini düşünün, ancak günün çeşitli saatlerinde, her hizmet farklı kalite ve yanıt süreleri sağlayabilir.  Bu dalgalanmalarla başa çıkmak için tüm web hizmetlerine istekler verebilir ve birinden yanıt alır almaz kalan istekleri iptal edebilirsiniz.  Birden çok işlem başlatma, herhangi bir bekleyen ve daha sonra geri kalanını iptal bu ortak desen uygulamak için daha kolay hale getirmek için bir yardımcı işlevi uygulayabilirsiniz. Aşağıdaki `NeedOnlyOne` örnekteki işlev bu senaryoyu göstermektedir:

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

 Daha sonra aşağıdaki gibi bu işlevi kullanabilirsiniz:

```csharp
double currentPrice = await NeedOnlyOne(
    ct => GetCurrentPriceFromServer1Async("msft", ct),
    ct => GetCurrentPriceFromServer2Async("msft", ct),
    ct => GetCurrentPriceFromServer3Async("msft", ct));
```

### <a name="interleaved-operations"></a>Ara İşlemler
 Çok büyük görev kümeleriyle <xref:System.Threading.Tasks.Task.WhenAny%2A> çalışırken, ayrılmalar arası senaryoyu desteklemek için yöntemi kullanmada olası bir performans sorunu vardır. Her arama, her göreve kaydolarak devam edilmesiyle <xref:System.Threading.Tasks.Task.WhenAny%2A> sonuçlanır. N görev sayısı için bu, ayrılma işleminin ömrü boyunca oluşturulan O(N<sup>2)</sup>devamlarına neden olur. Büyük bir görev kümesiyle çalışıyorsanız, performans sorununu gidermek için`Interleaved` bir kombinatör (aşağıdaki örnekte) kullanabilirsiniz:

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

 Daha sonra, görevlerin sonuçlarını tamamlanırken işlemek için kombinatörü kullanabilirsiniz; örneğin:

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a>WhenallOrFirstException
 Belirli dağılım/toplama senaryolarında, bu hatalardan biri hatalar olmadığı sürece, bir kümedeki tüm görevleri beklemek isteyebilirsiniz ve bu durumda özel durum oluşur oluşmaz beklemeyi durdurmak isteyebilirsiniz.  Bunu aşağıdaki örnekte olduğu gibi `WhenAllOrFirstException` bir kombinatör yöntemiyle gerçekleştirebilirsiniz:

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

## <a name="building-task-based-data-structures"></a>Görev Tabanlı Veri Yapıları Oluşturma
 Özel görev tabanlı kombinleyiciler oluşturma yeteneğine ek olarak, <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> içinde bir veri yapısına sahip ve bu da hem bir eşzamanlı işlemin sonuçlarını hem de onunla birleştirilmesi için gerekli eşitlemeyi temsil eder, bu da onu eşzamanlı senaryolarda kullanılacak özel veri yapıları oluşturmak için çok güçlü bir tür yapar.

### <a name="asynccache"></a>AsyncÖnbellek
 Bir görevin önemli bir yönü birden fazla tüketiciye dağıtılabilir, hepsi de onu bekleyebilir, onunla devam ları kaydedebilir, <xref:System.Threading.Tasks.Task%601>sonucunu veya özel durumlarını (durumunda) alabilir.  Bu <xref:System.Threading.Tasks.Task> yapar <xref:System.Threading.Tasks.Task%601> ve mükemmel bir asynchronöz önbelleğe alma altyapısında kullanılmak üzere uygundur.  Burada küçük ama güçlü bir asynchronous önbellek üstüne <xref:System.Threading.Tasks.Task%601>inşa bir örnek:

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

 [AsyncCache\<TKey,TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) sınıfı, bir alır `TKey` ve bir <xref:System.Threading.Tasks.Task%601>döndürür bir işlevi oluşturucu bir temsilci olarak kabul eder.  Önbellekten daha önce erişilen değerler iç sözlükte depolanır ve önbelleğe aynı anda erişilmiş olsa bile anahtar başına yalnızca bir görevin oluşturulmasını `AsyncCache` sağlar.

 Örneğin, indirilen web sayfaları için bir önbellek oluşturabilirsiniz:

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 Daha sonra, bir web sayfasının içeriğine ihtiyaç duyduğunuzda bu önbelleği eşzamanlı yöntemlerle kullanabilirsiniz. Sınıf, `AsyncCache` mümkün olduğunca az sayfa indirmenizi sağlar ve sonuçları önbelleğe almaz.

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
 Eşzamanlı etkinlikleri koordine etmek için veri yapıları oluşturmak için görevleri de kullanabilirsiniz.  Klasik paralel tasarım desenlerinden birini düşünün: üretici/tüketici.  Bu modelde, üreticiler tüketiciler tarafından tüketilen verileri üretirler ve üreticiler ve tüketiciler paralel olarak çalışabilirler. Örneğin, tüketici, daha önce madde 2'yi üreten bir üretici tarafından oluşturulan madde 1'i işler.  Üretici/tüketici modeli için, tüketicilerin yeni verilerden haberdar edilebilmeleri ve mevcut olduğunda bulabilmeleri için üreticiler tarafından oluşturulan çalışmayı depolamak için her zaman bazı veri yapısına ihtiyacınız vardır.

 Asynchronous yöntemlerinin üretici ve tüketici olarak kullanılmasını sağlayan görevlerin üzerine inşa edilmiş basit bir veri yapısı aşağıda verilmiştir:

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

 Bu veri yapısı yerinde olduğundan, aşağıdaki gibi kod yazabilirsiniz:

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

Ad <xref:System.Threading.Tasks.Dataflow> alanı, <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> benzer bir şekilde kullanabileceğiniz, ancak özel bir koleksiyon türü oluşturmak zorunda kalmadan türünü içerir:

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
> İsim <xref:System.Threading.Tasks.Dataflow> alanı **NuGet**üzerinden .NET Framework 4.5'te mevcuttur. Ad alanını içeren derlemeyi <xref:System.Threading.Tasks.Dataflow> yüklemek için Visual Studio'da projenizi açın, Proje menüsünden **NuGet Paketlerini Yönet'i** seçin ve Microsoft.Tpl.Dataflow paketini çevrimiçi olarak arayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Görev Tabanlı Zaman Uyumsuz Deseni Uygulama](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
