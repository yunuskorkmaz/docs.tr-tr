---
title: Görev Tabanlı Zaman Uyumsuz Desen (TAP)
ms.date: 02/26/2019
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96499d2a3d74deb7208fa49f9fc0927109d93a69
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623802"
---
# <a name="task-based-asynchronous-pattern-tap"></a>Görev tabanlı zaman uyumsuz desen (TAP)
Görev tabanlı zaman uyumsuz desen (TAP) dayanır <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> türlerini <xref:System.Threading.Tasks?displayProperty=nameWithType> zaman uyumsuz işlemleri temsil etmekte kullanılan ad alanı. TAP yeni geliştirme için önerilen zaman uyumsuz tasarım desenidir.  
  
## <a name="naming-parameters-and-return-types"></a>Adlandırma, parametreler ve dönüş türleri

TAP, bir zaman uyumsuz işlemin başlangıcını ve tamamlanmasını temsil etmek için tek bir yöntem kullanır. Bu hem zaman uyumsuz programlama modeli ile karşılaştırır (APM ya da `IAsyncResult`) deseni ve olay-tabanlı zaman uyumsuz desen (EAP). APM gerektirir `Begin` ve `End` yöntemleri. EAP içeren bir yöntem gerektirir `Async` sonek ve ayrıca bir veya daha fazla olay, olay işleyicisi temsilci türleri, gerektirir ve `EventArg`-türetilmiş türler. TAP içindeki zaman uyumsuz yöntemler `Async` beklenebilir döndüren yöntemler için işlem adı türleri, aşağıdaki gibi sonra soneki <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask>, ve <xref:System.Threading.Tasks.ValueTask%601>. Örneğin, bir zaman uyumsuz `Get` döndüren işlemi bir `Task<String>` adlandırılabilir `GetAsync`. Bir EAP yöntemi adı zaten var. bir sınıfa bir TAP yöntemi ekliyorsanız `Async` soneki,'ın soneki kullanıp `TaskAsync` yerine. Örneğin, sınıf zaten varsa, bir `GetAsync` yöntemi adı `GetTaskAsync`. Bir yöntem, zaman uyumsuz bir işlem başlatır ancak bir beklenebilir türü döndürmüyor adı ile başlamanız gerekir `Begin`, `Start`, ya da bu yöntemi yok döndürmesine veya bir işlemin sonucunu, önermek için diğer bazı fiil.  
  
 Bir TAP yöntemi döndürür bir <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> veya <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>karşılık gelen zaman uyumlu yöntemin void döndüren veya tür göre `TResult`.  
  
 Bir TAP yönteminin parametreleri onun zaman uyumlu karşılığı parametreleri eşleşmelidir ve aynı sırada sağlanmalıdır.  Ancak, `out` ve `ref` parametreleri bu kurala ve tamamen kaçınılmalıdırlar. Üzerinden döndürülen veriler bir `out` veya `ref` parametre yerine döndürülecek bir parçası olarak `TResult` tarafından döndürülen <xref:System.Threading.Tasks.Task%601>ve birden çok değere uyum sağlayacak bir kayıt düzeni veya özel veri yapısı kullanmanız gerekir. Eklemeyi düşünmelidir bir <xref:System.Threading.CancellationToken> bile, TAP yöntemi zaman uyumlu karşılığı sunmaz bir parametre.
 
 Oluşturma, düzenleme veya görevleri (yöntemin zaman uyumsuz amacı yöntem adında veya yöntemin ait olduğu tür adında açık olduğu) birleşimi için özel olarak ayrılmış yöntemler şu adlandırma desenini izler değil; Bu tür yöntemler olarak anılır *kombinatör*. Kombinatörlere <xref:System.Threading.Tasks.Task.WhenAll%2A> ve <xref:System.Threading.Tasks.Task.WhenAny%2A>ve [görev tabanlı Kombinatör kullanımı](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md#combinators) makalenin bölümü [görev tabanlı zaman uyumsuz desenkullanma](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).  
  
 TAP sözdiziminin eski zaman uyumsuz programlama desenleri gibi zaman uyumsuz programlama modeli (APM) ve olay-tabanlı zaman uyumsuz desen (EAP) kullanılan söz farkı örnekler için bkz [zaman uyumsuz programlama desenleri ](../../../docs/standard/asynchronous-programming-patterns/index.md).  
  
## <a name="initiating-an-asynchronous-operation"></a>Zaman uyumsuz bir işlem başlatma  
 TAP tabanlı bir zaman uyumsuz yöntem elde edilen görevi döndürmeden önce, az miktarda bir işi (bağımsız değişkenleri doğrulamak ya da zaman uyumsuz işlemi başlatmak gibi) zaman uyumlu olarak yapabilir. Zaman uyumsuz yöntemin çabuk dönmesini sağlamak için zaman uyumlu iş olabildiğince az tutulmalıdır. Hızlı dönüş nedenleri şunlardır:  
  
- Zaman uyumsuz yöntemler kullanıcı arabirimi (UI) iş parçacıkları tarafında çağırılabilirler, ve herhangi bir uzun süre çalışan zaman uyumlu iş uygulamanın yanıt verme becerisine zarar verebilir.  
  
- Birden çok zaman uyumsuz yöntem eşzamanlı başlatılabilir. Bu nedenle, bir zaman uyumsuz yöntemin herhangi bir uzun süren zaman uyumlu bölümü diğer zaman uyumsuz işlemlerin başlamasını geciktirerek eşzamanlılığın yararlarını azaltabilir.  
  
 Bazı durumlarda, işlemi tamamlamak için gereken iş, işlemi zaman uyumsuz olarak başlatmak için gereken işten daha azdır. Okuma işleminin bellekte zaten arabelleğe alınmış veri ile tamamlanabileceği bir akıştan okumak bu duruma bir örnektir. Bu gibi durumlarda, işlem zaman uyumlu olarak tamamlanabilir ve zaten tamamlanmış bir görevi döndürebilir.  
  
## <a name="exceptions"></a>Özel Durumlar  
 Bir zaman uyumsuz yöntem, zaman uyumsuz yöntem çağrısının dışına atılacak bir özel durumu sadece bir kullanım hatasına yanıt olarak harekete geçirmelidir. Kullanım hataları asla üretim kodunda gerçekleşmemelidir. Örneğin, bir null başvurusu (`Nothing` Visual Basic'te) bir hata durumu yöntemin bağımsız değişkenlerden biri neden olur (genellikle tarafından temsil edilen bir <xref:System.ArgumentNullException> özel durumu), bir null başvuru hiçbir zaman geçtiğinden emin olmak için çağıran kodu değiştirebilirsiniz. Diğer bütün hatalar için, görev döndürülene kadar zaman uyumsuz yöntem zaman uyumlu olarak tamamlansa bile, zaman uyumsuz yöntem yürütülüyorken oluşan özel durumlar döndürülen göreve atanmalıdır. Genel olarak, bir görev en fazla bir özel durum içerir. Ancak, görevin birden çok işlemi temsil ediyorsa (örneğin, <xref:System.Threading.Tasks.Task.WhenAll%2A>), birden çok özel durum tek bir görevle ilişkilendirilebilir.  
  
## <a name="target-environment"></a>Hedef ortam  
 Bir TAP yöntemi oluştururken, zaman uyumsuz yürütülmenin nerede olacağını belirleyebilirsiniz. İş yükünü iş parçacığı havuzunda çalıştırmayı, zaman uyumsuz I/O kullanarak oluşturmayı (işlemin yürütülmesinin çoğunluğunda bir iş parçacığına bağlı kalmayarak), belirli bir iş parçacığında yürütmeyi (örneğin UI iş parçacığı), veya diğer olası bağlamları kullanmayı tercih edebilirsiniz. Bir TAP yöntemi yürütmek için bir şey bile olabilir ve yalnızca döndürebilir bir <xref:System.Threading.Tasks.Task> temsil eden bir koşul oluşumunu başka bir yerde sisteminde (örneğin, bir kuyruğa alınan verilerin yapısı gelen verileri temsil eden bir görev).
 
 TAP yöntemi çağıran kişi, TAP yöntemi, sonuçta elde edilen görevi zaman uyumlu olarak bekleyerek tamamlanması beklenirken engelleyebilir veya zaman uyumsuz işlem tamamlandığında ek (devam) kodu çalıştırabilir. Devam kodunun yaratıcısı kodun nerede çalışacağına dair denetime sahiptir. Devamlılık kod ya da açıkça yöntemleri ile oluşturduğunuz <xref:System.Threading.Tasks.Task> sınıfı (örneğin, <xref:System.Threading.Tasks.Task.ContinueWith%2A>) veya devamlılıklar üzerine kurulu bir dil desteği kullanılarak örtük olarak (örneğin, `await` içinde C#, `Await` Visual Basic'te `AwaitValue` içinde F#).  
  
## <a name="task-status"></a>Görev durumu  
 <xref:System.Threading.Tasks.Task> Sınıfı zaman uyumsuz işlemler için bir yaşam döngüsü sağlar ve bu döngüyü tarafından temsil edilen <xref:System.Threading.Tasks.TaskStatus> sabit listesi. Öğesinden türetilen türlerin köşe durumlarını desteklemek üzere <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601>, planlama, oluşturma ayrılmasını destekliyor ve <xref:System.Threading.Tasks.Task> sınıfı kullanıma sunan bir <xref:System.Threading.Tasks.Task.Start%2A> yöntemi. Genel tarafından oluşturulan görevler <xref:System.Threading.Tasks.Task> oluşturucular denir *soğuk görevler*, çünkü onlar yaşam döngülerine zamanlanmamış çalışmaya <xref:System.Threading.Tasks.TaskStatus.Created> ve bu durum yalnızca zamanlanmış <xref:System.Threading.Tasks.Task.Start%2A> üzerinde çağrılır Bu örnekler. 
 
 Tüm diğer görevler yaşam döngüsü temsil ettikleri zaman uyumsuz işlemler zaten başlatıldığını ve görev durumlarının dışında bir numaralandırma değeri olduğu anlamına gelir bir sıcak durumunda başlarlar, <xref:System.Threading.Tasks.TaskStatus.Created?displayProperty=nameWithType>. TAP yöntemlerinden döndürülen tüm görevler etkinleştirilmelidir. **Bir TAP yöntemi dahili olarak görevin Oluşturucusu döndürülmesi için TAP yönteminin çağırmalıdır örneklerse, <xref:System.Threading.Tasks.Task.Start%2A> üzerinde <xref:System.Threading.Tasks.Task> nesnesini döndürmeden önce.** TAP yönteminin tüketicileri güvenli bir şekilde varsayar döndürülen görevin etkindir ve çağırmak denememelisiniz <xref:System.Threading.Tasks.Task.Start%2A> herhangi <xref:System.Threading.Tasks.Task> bir TAP yönteminden döndürülen. Çağırma <xref:System.Threading.Tasks.Task.Start%2A> bir etkin görev sonuçları üzerinde bir <xref:System.InvalidOperationException> özel durum.  
  
## <a name="cancellation-optional"></a>İptal (isteğe bağlı)  
 TAP kullanırken, iptal etmek hem zaman uyumsuz yöntem oluşturucuları hem de zaman uyumsuz yöntem tüketicileri için isteğe bağlıdır. Bir işlem iptale izin veriyorsa, zaman uyumsuz yöntemin bir iptal belirteci kabul eden bir aşırı kullanıma sunduğu (<xref:System.Threading.CancellationToken> örnek). Kural gereği, parametre olarak adlandırılır `cancellationToken`.  
  
 [!code-csharp[Conceptual.TAP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#1)]
 [!code-vb[Conceptual.TAP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#1)]  
  
 Zaman uyumsuz işlem iptal istekleri için bu belirteci izler. Eğer iptal isteği alırsa, bu isteği dikkate alarak işlemi iptal etmeyi seçebilir. İptal isteği işin tamamlanmadan önce olursa, TAP yöntemi ile biten bir görev döndürür. <xref:System.Threading.Tasks.TaskStatus.Canceled> durum; kullanılabilir sonuç yoktur ve hiçbir özel durum.  <xref:System.Threading.Tasks.TaskStatus.Canceled> Durumu ile birlikte bir görev için son (tamamlanmış) bir durumu olarak kabul edilir <xref:System.Threading.Tasks.TaskStatus.Faulted> ve <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> durumları. Bu nedenle, bir görev ise <xref:System.Threading.Tasks.TaskStatus.Canceled> durumu, kendi <xref:System.Threading.Tasks.Task.IsCompleted%2A> özelliği döndürür `true`. Bir görev tamamlandığında <xref:System.Threading.Tasks.TaskStatus.Canceled> durumunda göreve kaydedilmiş tüm devamlar zamanlanır ya da yürütülür, bir devam seçeneği sürece gibi <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled> devamdan belirtildi. Dil özellikleri iptal edilmiş bir görev çalışmaya devam eden zaman uyumsuz olarak bekliyor, ancak alan herhangi bir kod bir <xref:System.OperationCanceledException> veya ondan türetilmiş bir özel durum. Zaman uyumlu olarak görev üzerinde yöntemleri gibi bekleyerek engellenen kod <xref:System.Threading.Tasks.Task.Wait%2A> ve <xref:System.Threading.Tasks.Task.WaitAll%2A> Ayrıca, bir özel durum ile çalışmaya devam eder.  
  
 Bir iptal belirteci iptal belirtecini kabul TAP yönteminin önce varsa istedi, TAP yöntemi döndürmelidir bir <xref:System.Threading.Tasks.TaskStatus.Canceled> görev.  Ancak, eğer zaman uyumsuz işlem yürütülüyorken bir iptal istenirse, zaman uyumsuz işlem iptal isteğini kabul etmek zorunda değildir.  Döndürülen görevin bitmelidir <xref:System.Threading.Tasks.TaskStatus.Canceled> yalnızca işlem iptal isteği nedeniyle bitip bitmediğini belirtin. Eğer iptal istendiyse, ancak yine de bir sonuç ya da bir özel durum üretilir, görev bitmelidir <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> veya <xref:System.Threading.Tasks.TaskStatus.Faulted> durumu. 
 
 Özellikle iptal özelliğini kullanıma sunmak istiyorsanız zaman uyumsuz yöntemler için iptal belirteci kabul etmeyen bir aşırı yükleme sağlamanıza gerek yoktur. İptal edilemeyen yöntemler için iptal belirteci kabul eden bir aşırı yükleme sağlamayın; bu çağırana hedef yöntemin iptal edilip edilemez olduğunu belirtmeye yardımcı olur.  İptal bağlamasına değil tüketici kodu kabul eden bir yöntemi çağırıp bir <xref:System.Threading.CancellationToken> ve <xref:System.Threading.CancellationToken.None%2A> bağımsız değişken değeri olarak. <xref:System.Threading.CancellationToken.None%2A> Varsayılan işlevsel olarak eşdeğerdir <xref:System.Threading.CancellationToken>.  
  
## <a name="progress-reporting-optional"></a>İlerleme raporlama (isteğe bağlı)  
 Bazı zaman uyumsuz işlemler ilerleme bildirimlerinden faydalanır; bunlar genel olarak kullanıcı arayüzünü zaman uyumsuz işlemin ilerlemesi ile ilgili bilgiyle güncelleştirmekte kullanılır. 
 
 TAP, ilerleme durumu ile işlenir bir <xref:System.IProgress%601> zaman uyumsuz yönteme genelde adlı bir parametre olarak geçirilen arabirimi `progress`.  Zaman uyumsuz yöntem çağırıldığında ilerleme arabirimini sağlamak yanlış kullanım nedeniyle ortaya çıkan yarış durumlarını engellemeye yardımcı olur (yanlış kayıt olan olay işleyicilerinin işlem başladıktan sonra güncellemeleri kaçırabilmesi).  Daha da önemlisi, ilerleme arabirimi ilerlemenin tüketici kodunda belirlendiği üzere farklı uygulamalarını destekleyebilir.  Örneğin, tüketici kod yalnızca en son ilerleme güncellemesini isteyebilir, ya da tüm güncellemeleri arabelleğe koyabilir, ya da her güncelleme için bir eylem çağırabilir, ya da çağrının belirli bir iş parçacığına yönlendirilip yönlendirilmediğini denetlemek isteyebilir. Bütün bu seçenekler belirli tüketicinin ihtiyaçlarına göre arabirimin farklı uygulamalarını kullanarak elde edilebilir.  İptalde olduğu TAP uygulamaları sağlamalıdır gibi bir <xref:System.IProgress%601> sadece API ilerleme bildirimlerini destekliyorsa bir parametre. 
 
 Örneğin, varsa `ReadAsync` bu makalenin önceki bölümlerinde açıklanan yöntemi, ilerleme geri araması olabilir bayt biçiminde Ara ilerlemeyi şimdiye kadar okuma bildirecek bir <xref:System.IProgress%601> arabirimi:  
  
 [!code-csharp[Conceptual.TAP#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#2)]
 [!code-vb[Conceptual.TAP#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#2)]  
  
 Varsa bir `FindFilesAsync` yöntemi belirli bir arama desenine uyan tüm dosyaların listesini döndürür, ilerleme geri araması geçerli kısmi sonuçları kümesini yanı sıra tamamlanmış iş yüzdesini tahmini sağlayabilir.  Bunu ya bir kayıt düzeni ile yapabilir:  
  
 [!code-csharp[Conceptual.TAP#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#3)]
 [!code-vb[Conceptual.TAP#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#3)]  
  
 ya da API'ye özel bir veri türü ile yapabilir:  
  
 [!code-csharp[Conceptual.TAP#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#4)]
 [!code-vb[Conceptual.TAP#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#4)]  
  
 İkinci durumda, özel veri türü genellikle ile soneki `ProgressInfo`.  
  
 Kabul eden aşırı yüklemeler TAP uygulamaları sağlamak, bir `progress` parametresi, bunlar izin vermelidir bağımsız değişken olarak `null`, bu durumda hiçbir ilerleme raporlanmaz. TAP uygulamaları ilerlemeyi raporlamalıdır <xref:System.Progress%601> zaman uyumlu olarak, zaman uyumsuz yöntemin ilerlemeyi çabuk sağlamasına sağlayan nesne ve ilerlemenin tüketicisinin bilgiyi işlemek nasıl ve nerede belirlemek izin verin. Örneğin, ilerleme örneği geri aramaları yönlendirmeyi ve yakalanan bir eşitleme bağlamında olay çağırmayı seçebilir.  
  
## <a name="iprogresst-implementations"></a>Iprogress\<T > uygulamaları  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Tek bir sağlar <xref:System.IProgress%601> uygulama: <xref:System.Progress%601>. <xref:System.Progress%601> Sınıfı gibi bildirilir:  
  
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
  
 Örneği <xref:System.Progress%601> sunan bir <xref:System.Progress%601.ProgressChanged> zaman uyumsuz işlem ilerleme raporları her zaman gerçekleşmek üzereyken olay. <xref:System.Progress%601.ProgressChanged> Olayı yükseltildiğinde <xref:System.Threading.SynchronizationContext> nesnesi başlatıldığında yakalanan <xref:System.Progress%601> örneği. Eğer hiçbir eşitleme bağlamı kullanılabilir değilse, iş parçacığı havuzunu hedefleyen bir varsayılan bağlam kullanılır. İşleyiciler bu olay ile kayıtlı olabilir. Tek bir işleyici için de sağlanabilir <xref:System.Progress%601> oluşturucusuna kolaylık ve için bir olay işleyicisi gibi davranan <xref:System.Progress%601.ProgressChanged> olay. İlerleme güncelleştirmeleri zaman uyumsuz işlemi olay işleyicileri yürütülürken geciktirmemek için zaman uyumsuz olarak harekete geçirilir. Başka bir <xref:System.IProgress%601> uygulama farklı seçebilir.  
  
## <a name="choosing-the-overloads-to-provide"></a>Sağlanacak aşırı yüklemeleri seçme  
 Bir TAP uygulaması hem isteğe bağlı kullanıyorsa <xref:System.Threading.Tasks.TaskFactory.CancellationToken%2A> ve isteğe bağlı <xref:System.IProgress%601> parametreleri, dört taneye kadar aşırı yükleme potansiyel olarak gerekli:  
  
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
  
 Geliştiriciler olan iki ara kombinasyonu eksik dengelemek için iletebilir <xref:System.Threading.CancellationToken.None%2A> veya varsayılan <xref:System.Threading.CancellationToken> için `cancellationToken` parametresi ve `null` için `progress` parametresi.  
  
 Eğer TAP yönteminin her kullanımının iptal veya ilerleme desteklemesini istiyorsanız, ilgili parametreyi kabul etmeyen aşırı yüklemeleri çıkarabilirsiniz.  
  
 İptal ve ilerlemeyi isteğe bağlı yapmak için birden çok aşırı yükleme açığa karar verirseniz, başarılı olursa iptal veya ilerleme desteklemeyen aşırı davranacağı <xref:System.Threading.CancellationToken.None%2A> iptal veya `null` ilerleme aşırı yükleme için Bunlar desteklemiyor.  
  
## <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Zaman Uyumsuz Programlama Desenleri](../../../docs/standard/asynchronous-programming-patterns/index.md)|Zaman uyumsuz işlemler gerçekleştirmek için üç desen tanıtır: Görev-tabanlı Zaman Uyumsuz Desen (TAP), Zaman Uyumsuz Programlama Modeli (APM) ve Olay-tabanlı Uyumsuz Desen (EAP).|  
|[Görev Tabanlı Zaman Uyumsuz Deseni Uygulama](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)|Görev-tabanlı Zaman Uyumsuz Desen (TAP) uygulamak için üç yol açıklar: Visual Studio içindeki C# ve Visual Basic derleyicilerini kullanarak, el yöntemi ile, veya derleyici ve el yönteminin bir kombinasyonu ile.|  
|[Görev Tabanlı Zaman Uyumsuz Desen Kullanma](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)|Engellemeden beklemeyi görevler ve geri aramalar kullanarak nasıl kullanacağınızı açıklar.|  
|[Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)|Zaman Uyumsuz Programlama Modeli (APM) ve Olay-tabanlı Zaman Uyumsuz Model (EAP) uygulamak için Görev-tabanlı Zaman Uyumsuz Model'in nasıl kullanılacağını açıklar.|
