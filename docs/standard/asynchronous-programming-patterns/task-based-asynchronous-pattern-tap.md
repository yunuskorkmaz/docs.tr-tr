---
title: "Görev Tabanlı Zaman Uyumsuz Desen (TAP)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 8cef1fcf-6f9f-417c-b21f-3fd8bac75007
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cb189dc35d3d4ae8744a408f458bc7dfad7cfa76
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="task-based-asynchronous-pattern-tap"></a>Görev Tabanlı Zaman Uyumsuz Desen (TAP)
Görev tabanlı zaman uyumsuz desen (TAP) dayanır <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> türlerini <xref:System.Threading.Tasks?displayProperty=nameWithType> rasgele zaman uyumsuz işlemleri temsil etmek için kullanılan ad. TAP yeni geliştirme için önerilen zaman uyumsuz tasarım desenidir.  
  
## <a name="naming-parameters-and-return-types"></a>Adlandırma, Parametreler ve Dönüş Türleri  
 TAP, bir zaman uyumsuz işlemin başlangıcını ve tamamlanmasını temsil etmek için tek bir yöntem kullanır. Zaman uyumsuz programlama modeli aksine budur (APM veya `IAsyncResult`) gerektiren düzeni `Begin` ve `End` yöntemleri ve buna karşılık olay tabanlı zaman uyumsuz desen (EAP), gerektiren içerenbiryöntem`Async`sonek ve ayrıca gerektiren bir veya daha fazla olaylar, olay işleyici temsilci türleri ve `EventArg`-türetilmiş tür. DOKUNUN zaman uyumsuz yöntemleri dahil `Async` soneki sonra işlem adı; Örneğin, `GetAsync` için bir `Get` işlemi. Bu yöntem adıyla zaten içeren bir sınıf için bir DOKUNUN yöntemi ekliyorsanız `Async` soneki, sonekini kullan `TaskAsync` yerine. Örneğin, sınıf zaten varsa, bir `GetAsync` yöntemi adı kullanmak `GetTaskAsync`.  
  
 DOKUNUN yöntemi döndürür bir <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> veya <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>bağlı karşılık gelen zaman uyumlu yöntemi geçersiz döner veya bir türü olarak `TResult`.  
  
 TAP yönteminin parametreleri onun zaman uyumlu karşılığı ile aynı olmalıdır, ve aynı sırada sağlanmalıdır.  Ancak, `out` ve `ref` parametreleri bu kuraldan muaf tutulan ve tamamen kaçınılmalıdır. Aracılığıyla Döndürülmüş herhangi bir veriyi bir `out` veya `ref` parametresi yerine döndürülüp döndürülmediğini parçası olarak `TResult` tarafından döndürülen <xref:System.Threading.Tasks.Task%601>ve bir tanımlama grubu ya da bir özel veri yapısı birden çok değer uyum sağlamak için kullanmalısınız. 
 
 Özel olarak oluşturma, düzenleme veya (yöntemi zaman uyumsuz amacı yöntem adı veya yöntemin ait olduğu tür adına açık olduğu) görevler birleşimi için ayrılan yöntemleri bu adlandırma deseni izlemeyecek; Bu tür yöntemleri olarak anılır *combinators*. Combinators örnekleri arasında <xref:System.Threading.Tasks.Task.WhenAll%2A> ve <xref:System.Threading.Tasks.Task.WhenAny%2A>ve ele alınmıştır [yerleşik görev tabanlı Combinators kullanarak](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md#combinators) makalenin bölümüne [görev tabanlı zaman uyumsuz desenkullanma](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).  
  
 Eski zaman uyumsuz programlama desenleri gibi zaman uyumsuz programlama modeli (APM) ve olay tabanlı zaman uyumsuz desen (EAP) kullanılan sözdizimi nasıl DOKUNUN sözdizimi farklıdır örnekler için bkz: [zaman uyumsuz programlama desenleri ](../../../docs/standard/asynchronous-programming-patterns/index.md).  
  
## <a name="initiating-an-asynchronous-operation"></a>Bir Zaman Uyumsuz İşlem Başlatma  
 TAP tabanlı bir zaman uyumsuz yöntem elde edilen görevi döndürmeden önce, az miktarda bir işi (bağımsız değişkenleri doğrulamak ya da zaman uyumsuz işlemi başlatmak gibi) zaman uyumlu olarak yapabilir. Zaman uyumsuz yöntemin çabuk dönmesini sağlamak için zaman uyumlu iş olabildiğince az tutulmalıdır. Hızlı dönüş nedenleri şunlardır:  
  
-   Zaman uyumsuz yöntemler kullanıcı arabirimi (UI) iş parçacıkları tarafında çağırılabilirler, ve herhangi bir uzun süre çalışan zaman uyumlu iş uygulamanın yanıt verme becerisine zarar verebilir.  
  
-   Birden çok zaman uyumsuz yöntem eşzamanlı başlatılabilir. Bu nedenle, bir zaman uyumsuz yöntemin herhangi bir uzun süren zaman uyumlu bölümü diğer zaman uyumsuz işlemlerin başlamasını geciktirerek eşzamanlılığın yararlarını azaltabilir.  
  
 Bazı durumlarda, işlemi tamamlamak için gereken iş, işlemi zaman uyumsuz olarak başlatmak için gereken işten daha azdır. Okuma işleminin bellekte zaten arabelleğe alınmış veri ile tamamlanabileceği bir akıştan okumak bu duruma bir örnektir. Bu gibi durumlarda, işlem zaman uyumlu olarak tamamlanabilir ve zaten tamamlanmış bir görevi döndürebilir.  
  
## <a name="exceptions"></a>Özel Durumlar  
 Bir zaman uyumsuz yöntem, zaman uyumsuz yöntem çağrısının dışına atılacak bir özel durumu sadece bir kullanım hatasına yanıt olarak harekete geçirmelidir. Kullanım hataları asla üretim kodunda gerçekleşmemelidir. Örneğin, bir null başvuru geçirilirse (`Nothing` Visual Basic'te) yöntemin bağımsız değişkenlerden biri bir hata durumuna neden olur (genellikle tarafından temsil edilen bir <xref:System.ArgumentNullException> özel durumu), bir null başvuru hiçbir zaman geçirilen emin olmak için arama kodu değiştirebilirsiniz. Diğer bütün hatalar için, görev döndürülene kadar zaman uyumsuz yöntem zaman uyumlu olarak tamamlansa bile, zaman uyumsuz yöntem yürütülüyorken oluşan özel durumlar döndürülen göreve atanmalıdır. Genel olarak, bir görev en fazla bir özel durum içerir. Ancak, görevi birden çok operations temsil ediyorsa (örneğin, <xref:System.Threading.Tasks.Task.WhenAll%2A>), birden çok özel durumları tek bir görev ile ilişkili olabilir.  
  
## <a name="target-environment"></a>Hedef Ortam  
 Bir TAP yöntemi oluştururken, zaman uyumsuz yürütülmenin nerede olacağını belirleyebilirsiniz. İş yükünü iş parçacığı havuzunda çalıştırmayı, zaman uyumsuz I/O kullanarak oluşturmayı (işlemin yürütülmesinin çoğunluğunda bir iş parçacığına bağlı kalmayarak), belirli bir iş parçacığında yürütmeyi (örneğin UI iş parçacığı), veya diğer olası bağlamları kullanmayı tercih edebilirsiniz. DOKUNUN yöntemi bile yürütmek için bir şey olabilir ve yalnızca döndürebilir bir <xref:System.Threading.Tasks.Task> temsil eden bir koşul örneğini başka bir yerde sisteminde (örneğin, bir Sıraya alınan veri yapısı ulaşan verilerin temsil eden bir görev).
 
 DOKUNUN yöntemini çağıran zaman uyumlu olarak elde edilen görevde bekleyerek tamamlamak DOKUNUN yöntemi bekleniyor engelleyebilir veya zaman uyumsuz işlemi tamamlandığında ek (devam) kod çalıştırabilir. Devam kodunun yaratıcısı kodun nerede çalışacağına dair denetime sahiptir. Devamlılık kodu ya da açıkça yöntemlerle üzerinde oluşturduğunuz <xref:System.Threading.Tasks.Task> sınıfı (örneğin, <xref:System.Threading.Tasks.Task.ContinueWith%2A>) veya üstünde devamlılıklar yerleşik dil desteği kullanılarak dolaylı olarak (örneğin, `await` C# ' ta, `Await` içinde İşlevlerin, `AwaitValue` F #).  
  
## <a name="task-status"></a>Görev Durumu  
 <xref:System.Threading.Tasks.Task> Sınıfı zaman uyumsuz işlemleri için bir yaşam döngüsü sağlar ve bu döngüsü tarafından temsil edilen <xref:System.Threading.Tasks.TaskStatus> numaralandırması. Öğesinden türetilen türler köşe örneklerini desteklemek için <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601>, planlama, oluşturma ayrılması desteklemek için ve <xref:System.Threading.Tasks.Task> sınıf çıkarır bir <xref:System.Threading.Tasks.Task.Start%2A> yöntemi. Ortak tarafından oluşturulan görevler <xref:System.Threading.Tasks.Task> oluşturucular denir *soğuk görevleri*, zamanlanmamış kendi yaşam döngüsü başlatmak için <xref:System.Threading.Tasks.TaskStatus.Created> durumu ve bu zamanlanmış yalnızca <xref:System.Threading.Tasks.Task.Start%2A> üzerinde çağrılır Bu örnekler. 
 
 Diğer tüm görevlerden yaşam döngüsünü temsil ettikleri zaman uyumsuz işlemleri zaten başlatılmış ve görev durumlarını devralınan numaralandırma değeri dışında olduğu anlamına gelir bir etkin durumda, başlamak <xref:System.Threading.Tasks.TaskStatus.Created?displayProperty=nameWithType>. TAP yöntemlerinden döndürülen tüm görevler etkinleştirilmelidir. **DOKUNUN yöntemi dahili bir görevin Oluşturucusu döndürülmesi için DOKUNUN yöntemi çağırmanız gerekir görev örneği oluşturmak için kullanıp kullanmadığını <xref:System.Threading.Tasks.Task.Start%2A> üzerinde <xref:System.Threading.Tasks.Task> onu dönmeden önce nesnesi.** DOKUNUN yöntemi tüketicileri güvenle varsayın döndürülen görev etkindir ve çağrılacak denemelisiniz değil <xref:System.Threading.Tasks.Task.Start%2A> herhangi <xref:System.Threading.Tasks.Task> DOKUNUN yönteminden döndürülen. Çağırma <xref:System.Threading.Tasks.Task.Start%2A> bir etkin görev sonuçlarını bir <xref:System.InvalidOperationException> özel durum.  
  
## <a name="cancellation-optional"></a>İptal (İsteğe Bağlı)  
 TAP kullanırken, iptal etmek hem zaman uyumsuz yöntem oluşturucuları hem de zaman uyumsuz yöntem tüketicileri için isteğe bağlıdır. Bir işlem iptal izin veriyorsa, bir aşırı yüklemesini kabul eden bir iptal belirteci zaman uyumsuz yöntem sunar (<xref:System.Threading.CancellationToken> örnek). Kurala göre parametresi adlı `cancellationToken`.  
  
 [!code-csharp[Conceptual.TAP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#1)]
 [!code-vb[Conceptual.TAP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#1)]  
  
 Zaman uyumsuz işlem iptal istekleri için bu belirteci izler. Eğer iptal isteği alırsa, bu isteği dikkate alarak işlemi iptal etmeyi seçebilir. İptal isteğini erken sona işlerinde sonuçlanırsa, DOKUNUN yöntemi ile biten bir görev döndürür <xref:System.Threading.Tasks.TaskStatus.Canceled> durum; kullanılabilen hiçbir sonuç yoktur ve hiçbir özel durum oluşur.  <xref:System.Threading.Tasks.TaskStatus.Canceled> Durumu ile birlikte bir görev için bir son (tamamlanmış) durumu olarak değerlendirilir <xref:System.Threading.Tasks.TaskStatus.Faulted> ve <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> durumları. Bu nedenle, bir görev ise <xref:System.Threading.Tasks.TaskStatus.Canceled> durumu, kendi <xref:System.Threading.Tasks.Task.IsCompleted%2A> özelliği döndürür `true`. Bir görev tamamlandığında <xref:System.Threading.Tasks.TaskStatus.Canceled> durumunda, kayıtlı olan görev devamlılıklar zamanlanmış veya yürütülen, bir devamlılık seçeneği sürece gibi <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled> dışında devamlılık kabul etmek için belirtildi. Dil özellikleri aracılığıyla iptal edilmiş bir görev çalışmaya devam eder için zaman uyumsuz olarak bekliyor, ancak aldığı herhangi bir kod bir <xref:System.OperationCanceledException> veya ondan türetilmiş bir özel durum. Zaman uyumlu olarak görevi gibi yöntemleri beklerken engellendi kod <xref:System.Threading.Tasks.Task.Wait%2A> ve <xref:System.Threading.Tasks.Task.WaitAll%2A> de bir özel durum ile çalışmaya devam eder.  
  
 Bir iptal belirteci iptal belirtecini çağrılır kabul DOKUNUN yöntemi önce varsa istedi, DOKUNUN yöntem döndürmelidir bir <xref:System.Threading.Tasks.TaskStatus.Canceled> görev.  Ancak, eğer zaman uyumsuz işlem yürütülüyorken bir iptal istenirse, zaman uyumsuz işlem iptal isteğini kabul etmek zorunda değildir.  Döndürülen görev sona erdirmelisiniz <xref:System.Threading.Tasks.TaskStatus.Canceled> yalnızca işlemi sonucunda iptal isteğini bitip bitmediğini belirtin. İptal istendi, ancak bir sonuç veya bir özel durum hala üretilen görev içinde bitmelidir <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> veya <xref:System.Threading.Tasks.TaskStatus.Faulted> durumu. 
 
 İlk iptal yeteneği kullanıma sunmak istediğiniz zaman uyumsuz yöntemleri için bir iptal belirteci kabul etmez bir aşırı sağlamak zorunda değilsiniz. İptal edilemeyen yöntemler için iptal belirteci kabul eden bir aşırı yükleme sağlamayın; bu çağırana hedef yöntemin iptal edilip edilemez olduğunu belirtmeye yardımcı olur.  İptal işlemleriniz değil tüketici kodu kabul eden bir yöntem çağrısı bir <xref:System.Threading.CancellationToken> ve sağlamak <xref:System.Threading.CancellationToken.None%2A> bağımsız değişken değeri olarak. <xref:System.Threading.CancellationToken.None%2A>Varsayılan işlevsel olarak eşdeğerdir <xref:System.Threading.CancellationToken>.  
  
## <a name="progress-reporting-optional"></a>İlerleme Raporlama (İsteğe Bağlı)  
 Bazı zaman uyumsuz işlemler ilerleme bildirimlerinden faydalanır; bunlar genel olarak kullanıcı arayüzünü zaman uyumsuz işlemin ilerlemesi ile ilgili bilgiyle güncelleştirmekte kullanılır. 
 
 DOKUNUN, ilerleme aracılığıyla işlenmesini bir <xref:System.IProgress%601> zaman uyumsuz yöntem genellikle adlı bir parametre olarak geçirilen arabirimi `progress`.  Zaman uyumsuz yöntem çağırıldığında ilerleme arabirimini sağlamak yanlış kullanım nedeniyle ortaya çıkan yarış durumlarını engellemeye yardımcı olur (yanlış kayıt olan olay işleyicilerinin işlem başladıktan sonra güncellemeleri kaçırabilmesi).  Daha da önemlisi, ilerleme arabirimi ilerlemenin tüketici kodunda belirlendiği üzere farklı uygulamalarını destekleyebilir.  Örneğin, tüketici kod yalnızca en son ilerleme güncellemesini isteyebilir, ya da tüm güncellemeleri arabelleğe koyabilir, ya da her güncelleme için bir eylem çağırabilir, ya da çağrının belirli bir iş parçacığına yönlendirilip yönlendirilmediğini denetlemek isteyebilir. Bütün bu seçenekler belirli tüketicinin ihtiyaçlarına göre arabirimin farklı uygulamalarını kullanarak elde edilebilir.  İptal etme ile DOKUNUN uygulamaları sağlamalıdır gibi bir <xref:System.IProgress%601> yalnızca API ilerleme bildirimleri destekliyorsa parametresi. 
 
 Örneğin, varsa `ReadAsync` bu makalenin önceki bölümlerinde açıklanan yöntemi ilerleme geri çağırma olabilir bayt sayısı biçiminde Ara ilerleme bugüne kadarki okuma bildirebiliyor bir <xref:System.IProgress%601> arabirimi:  
  
 [!code-csharp[Conceptual.TAP#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#2)]
 [!code-vb[Conceptual.TAP#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#2)]  
  
 Varsa bir `FindFilesAsync` yöntemi, belirli arama deseni karşılayan tüm dosyaların bir listesini döndürür, devam eden geri çağırma kısmi sonuçlar geçerli kümesini yanı sıra tamamlanan çalışma yüzdesi tahmini sağlayabilir.  Bunu ya bir kayıt düzeni ile yapabilir:  
  
 [!code-csharp[Conceptual.TAP#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#3)]
 [!code-vb[Conceptual.TAP#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#3)]  
  
 ya da API'ye özel bir veri türü ile yapabilir:  
  
 [!code-csharp[Conceptual.TAP#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#4)]
 [!code-vb[Conceptual.TAP#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#4)]  
  
 İkinci durumda, özel veri türü genellikle ile sonekine `ProgressInfo`.  
  
 DOKUNUN uygulamaları aşırı getirmediğini, kabul bir `progress` parametresi, bunlar izin vermelidir olmasını `null`, hiçbir ilerleme; bu durumda bildirilir. DOKUNUN uygulamaları için İlerleme raporu <xref:System.Progress%601> eşzamanlı olarak, ilerleme durumunu hızlı bir şekilde sağlamak zaman uyumsuz yöntem sağlayan nesne ve bilgiyi işlemek nasıl ve nerede en iyi şekilde belirlemek tüketici ilerleme izin. Örneğin, ilerleme örneği geri aramaları yönlendirmeyi ve yakalanan bir eşitleme bağlamında olay çağırmayı seçebilir.  
  
## <a name="iprogresst-implementations"></a>IProgress\<T > uygulamaları  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Tek bir sağlar <xref:System.IProgress%601> uygulama: <xref:System.Progress%601>. <xref:System.Progress%601> Sınıfı şu şekilde bildirilen:  
  
```csharp  
public class Progress<T> : IProgress<T>  
{  
    public Progress();  
    public Progress(Action<T> handler);  
    protected virtual void OnReport(T value);  
    public event EventHandler<T> ProgressChanged;  
}  
```  
  
```vb  
Public Class Progress(Of T) : Inherits IProgress(Of T)  
    Public Sub New()  
    Public Sub New(handler As Action(Of T))  
    Protected Overridable Sub OnReport(value As T)  
    Public Event ProgressChanged As EventHandler(Of T>  
End Class  
```  
  
 Örneği <xref:System.Progress%601> kullanıma sunan bir <xref:System.Progress%601.ProgressChanged> zaman uyumsuz işlemi ilerleme güncelleştirmesi raporlar her zaman oluşan olayı,. <xref:System.Progress%601.ProgressChanged> Olayı oluşturulur <xref:System.Threading.SynchronizationContext> olan nesne ne zaman yakalanan <xref:System.Progress%601> örneği örneği. Eğer hiçbir eşitleme bağlamı kullanılabilir değilse, iş parçacığı havuzunu hedefleyen bir varsayılan bağlam kullanılır. İşleyiciler bu olay ile kayıtlı olabilir. Tek bir işleyici için de sağlanabilir <xref:System.Progress%601> Oluşturucusu kolaylık sağlamak için ve bir olay işleyicisi gibi davranır <xref:System.Progress%601.ProgressChanged> olay. İlerleme güncelleştirmeleri zaman uyumsuz işlemi olay işleyicileri yürütülürken geciktirmemek için zaman uyumsuz olarak harekete geçirilir. Başka bir <xref:System.IProgress%601> uygulaması farklı semantiği uygulamak seçin.  
  
## <a name="choosing-the-overloads-to-provide"></a>Sağlanacak Aşırı Yüklemeleri Seçme  
 DOKUNUN uygulaması hem isteğe bağlı kullanıyorsa <xref:System.Threading.Tasks.TaskFactory.CancellationToken%2A> ve isteğe bağlı <xref:System.IProgress%601> parametreleri, en fazla dört aşırı büyük olasılıkla gerektiren:  
  
```csharp  
public Task MethodNameAsync(…);  
public Task MethodNameAsync(…, CancellationToken cancellationToken);  
public Task MethodNameAsync(…, IProgress<T> progress);   
public Task MethodNameAsync(…,   
    CancellationToken cancellationToken, IProgress<T> progress);  
```  
  
```vb  
Public MethodNameAsync(…) As Task  
Public MethodNameAsync(…, cancellationToken As CancellationToken cancellationToken) As Task  
Public MethodNameAsync(…, progress As IProgress(Of T)) As Task   
Public MethodNameAsync(…, cancellationToken As CancellationToken,   
                       progress As IProgress(Of T)) As Task  
```  
  
 Ancak, birçok TAP uygulaması ne iptal ne de ilerleme olanakları sağlar, bu nedenle tek bir yöntem gerektirirler:  
  
```csharp  
public Task MethodNameAsync(…);  
```  
  
```vb  
Public MethodNameAsync(…) As Task  
```  
  
 Eğer bir TAP uygulaması ya iptal ya da ilerleme destekliyorsa ama ikisini birden desteklemiyorsa, iki aşırı yükleme sağlayabilir:  
  
```csharp  
public Task MethodNameAsync(…);  
public Task MethodNameAsync(…, CancellationToken cancellationToken);  
  
// … or …  
  
public Task MethodNameAsync(…);  
public Task MethodNameAsync(…, IProgress<T> progress);  
```  
  
```vb  
Public MethodNameAsync(…) As Task  
Public MethodNameAsync(…, cancellationToken As CancellationToken) As Task  
  
' … or …  
  
Public MethodNameAsync(…) As Task  
Public MethodNameAsync(…, progress As IProgress(Of T)) As Task  
```  
  
 Eğer bir TAP uygulaması hem iptal hem de ilerleme destekliyorsa, tüm dört aşırı yüklemeyi ortaya çıkarabilir. Ancak, yalnızca aşağıdaki ikisini sağlayabilir:  
  
```csharp  
public Task MethodNameAsync(…);  
public Task MethodNameAsync(…,   
    CancellationToken cancellationToken, IProgress<T> progress);  
```  
  
```vb  
Public MethodNameAsync(…) As Task  
Public MethodNameAsync(…, cancellationToken As CancellationToken,   
                       progress As IProgress(Of T)) As Task  
```  
  
 Ara birleşimleri eksik iki için dengelemek için geliştiricilere iletebilir <xref:System.Threading.CancellationToken.None%2A> veya varsayılan bir <xref:System.Threading.CancellationToken> için `cancellationToken` parametre ve `null` için `progress` parametresi.  
  
 Eğer TAP yönteminin her kullanımının iptal veya ilerleme desteklemesini istiyorsanız, ilgili parametreyi kabul etmeyen aşırı yüklemeleri çıkarabilirsiniz.  
  
 İptal veya devam eden isteğe bağlı yapmak için birden çok aşırı kullanıma sunmak karar verirseniz, bunlar gibi aktarılırsa iptal ya da ilerleme desteklemeyen aşırı hareket etmesi gerektiğini <xref:System.Threading.CancellationToken.None%2A> iptalleri veya `null` aşırı yükleme için ilerleme durumu için Bunlar desteklemiyor.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Zaman uyumsuz programlama desenleri](../../../docs/standard/asynchronous-programming-patterns/index.md)|Zaman uyumsuz işlemler gerçekleştirmek için üç desen tanıtır: Görev-tabanlı Zaman Uyumsuz Desen (TAP), Zaman Uyumsuz Programlama Modeli (APM) ve Olay-tabanlı Uyumsuz Desen (EAP).|  
|[Görev tabanlı zaman uyumsuz deseni uygulama](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)|Görev-tabanlı Zaman Uyumsuz Desen (TAP) uygulamak için üç yol açıklar: Visual Studio içindeki C# ve Visual Basic derleyicilerini kullanarak, el yöntemi ile, veya derleyici ve el yönteminin bir kombinasyonu ile.|  
|[Görev tabanlı zaman uyumsuz desen kullanma](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)|Engellemeden beklemeyi görevler ve geri aramalar kullanarak nasıl kullanacağınızı açıklar.|  
|[Diğer zaman uyumsuz desen ve türlerle birlikte çalışma](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)|Zaman Uyumsuz Programlama Modeli (APM) ve Olay-tabanlı Zaman Uyumsuz Model (EAP) uygulamak için Görev-tabanlı Zaman Uyumsuz Model'in nasıl kullanılacağını açıklar.|
