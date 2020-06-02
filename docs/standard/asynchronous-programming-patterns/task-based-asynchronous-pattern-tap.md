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
ms.openlocfilehash: 4a08c8a72116ea509f559e412c5f270f3471bf1c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276445"
---
# <a name="task-based-asynchronous-pattern-tap"></a>Görev tabanlı zaman uyumsuz model (TAP)
Görev tabanlı zaman uyumsuz model (TAP), <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> <xref:System.Threading.Tasks?displayProperty=nameWithType> rasgele zaman uyumsuz işlemleri temsil etmek için kullanılan ad alanındaki ve türlerini temel alır. TAP yeni geliştirme için önerilen zaman uyumsuz tasarım desenidir.  
  
## <a name="naming-parameters-and-return-types"></a>Adlandırma, parametreler ve dönüş türleri

TAP, bir zaman uyumsuz işlemin başlangıcını ve tamamlanmasını temsil etmek için tek bir yöntem kullanır. Bu, hem zaman uyumsuz programlama modeli (APM veya `IAsyncResult` ) modeli hem de olay tabanlı zaman uyumsuz model (EAP) ile karşıttır. APM `Begin` , ve `End` yöntemleri gerektirir. EAP sonekine sahip bir yöntem gerektirir `Async` ve ayrıca bir veya daha fazla olay, olay işleyicisi temsilci türü ve `EventArg` -türetilmiş türler gerektirir. Dokunmada zaman uyumsuz yöntemler,,, `Async` ve gibi agsever türlerini döndüren yöntemler için işlem adından sonra sonek içerir <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.ValueTask> <xref:System.Threading.Tasks.ValueTask%601> . Örneğin, döndüren zaman uyumsuz `Get` bir işlem adlandırılmış olabilir `Task<String>` `GetAsync` . Zaten sonekine sahip bir EAP yöntemi adı içeren bir sınıfa bir TAP yöntemi ekliyorsanız `Async` , `TaskAsync` bunun yerine soneki kullanın. Örneğin, sınıfın zaten bir `GetAsync` yöntemi varsa, adı kullanın `GetTaskAsync` . Bir yöntem zaman uyumsuz bir işlem başlatır ancak bir awasever türü döndürmezse, `Begin` `Start` Bu yöntemin işlemin sonucunu döndürmeyeceğini veya oluşturmadığını önermek için adının, ya da başka bir fiil ile başlaması gerekir.  
  
 Bir TAP metodu <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> , karşılık gelen zaman uyumlu yöntemin void veya bir tür döndürmeksizin bir veya bir döndürür `TResult` .  
  
 Bir TAP yönteminin parametreleri, zaman uyumlu karşılığına ait parametrelerle eşleşmelidir ve aynı sırada sağlanmalıdır.  Ancak, `out` ve `ref` parametreleri bu kuraldan muaf tutulur ve tamamen kaçınılmalıdır. Bir veya parametresi aracılığıyla döndürülen tüm veriler `out` `ref` yerine tarafından döndürülen bir parçası olarak döndürülür `TResult` <xref:System.Threading.Tasks.Task%601> ve birden çok değeri barındırmak için bir tanımlama grubu ya da özel veri yapısı kullanmalıdır. Ayrıca <xref:System.Threading.CancellationToken> yöntemin zaman uyumlu karşılığı bir tane sunmasa bile bir parametre eklemeyi göz önünde bulundurmanız gerekir.

 Özel olarak, görev oluşturma, düzenleme veya görev birleşimine ayrılan Yöntemler (metodun zaman uyumsuz hedefinin Yöntem adı içinde veya yöntemin ait olduğu türün adı) bu adlandırma modelini izlemesi gerekmez; Bu tür yöntemler genellikle *kombinatör*olarak adlandırılır. Ve kombinatör örnekleri <xref:System.Threading.Tasks.Task.WhenAll%2A> <xref:System.Threading.Tasks.Task.WhenAny%2A> , ve [görev tabanlı zaman uyumsuz model](consuming-the-task-based-asynchronous-pattern.md)kullanan makalenin [yerleşik görev tabanlı kombinatör](consuming-the-task-based-asynchronous-pattern.md#combinators) bölümünde açıklanmaktadır.  
  
 DOKUNMA sözdiziminin, zaman uyumsuz programlama modeli (APM) ve olay tabanlı zaman uyumsuz desen (EAP) gibi eski zaman uyumsuz programlama desenlerinde kullanılan sözdiziminden farklı olduğu örnekler için bkz. [zaman uyumsuz programlama desenleri](index.md).  
  
## <a name="initiating-an-asynchronous-operation"></a>Zaman uyumsuz bir işlem başlatılıyor  
 TAP tabanlı bir zaman uyumsuz yöntem elde edilen görevi döndürmeden önce, az miktarda bir işi (bağımsız değişkenleri doğrulamak ya da zaman uyumsuz işlemi başlatmak gibi) zaman uyumlu olarak yapabilir. Zaman uyumsuz yöntemin çabuk dönmesini sağlamak için zaman uyumlu iş olabildiğince az tutulmalıdır. Hızlı dönüş nedenleri şunlardır:  
  
- Zaman uyumsuz yöntemler kullanıcı arabirimi (UI) iş parçacıkları tarafında çağırılabilirler, ve herhangi bir uzun süre çalışan zaman uyumlu iş uygulamanın yanıt verme becerisine zarar verebilir.  
  
- Birden çok zaman uyumsuz yöntem eşzamanlı başlatılabilir. Bu nedenle, bir zaman uyumsuz yöntemin herhangi bir uzun süren zaman uyumlu bölümü diğer zaman uyumsuz işlemlerin başlamasını geciktirerek eşzamanlılığın yararlarını azaltabilir.  
  
 Bazı durumlarda, işlemi tamamlamak için gereken iş, işlemi zaman uyumsuz olarak başlatmak için gereken işten daha azdır. Okuma işleminin bellekte zaten arabelleğe alınmış veri ile tamamlanabileceği bir akıştan okumak bu duruma bir örnektir. Bu gibi durumlarda, işlem zaman uyumlu olarak tamamlanabilir ve zaten tamamlanmış bir görevi döndürebilir.  
  
## <a name="exceptions"></a>Özel durumlar  
 Bir zaman uyumsuz yöntem, zaman uyumsuz yöntem çağrısının dışına atılacak bir özel durumu sadece bir kullanım hatasına yanıt olarak harekete geçirmelidir. Kullanım hataları asla üretim kodunda gerçekleşmemelidir. Örneğin, `Nothing` yöntemin bağımsız değişkenlerinden biri bir hata durumuna neden olursa (genellikle bir özel durumla temsil edilen) bir null başvurusu (Visual Basic) geçirilirse, bir <xref:System.ArgumentNullException> null başvurusunun geçirilmeyeceğinden emin olmak için çağıran kodu değiştirebilirsiniz. Diğer bütün hatalar için, görev döndürülene kadar zaman uyumsuz yöntem zaman uyumlu olarak tamamlansa bile, zaman uyumsuz yöntem yürütülüyorken oluşan özel durumlar döndürülen göreve atanmalıdır. Genel olarak, bir görev en fazla bir özel durum içerir. Ancak, görev birden çok işlemi temsil ediyorsa (örneğin, <xref:System.Threading.Tasks.Task.WhenAll%2A> ), birden çok özel durum tek bir görevle ilişkilendirilebilir.  
  
## <a name="target-environment"></a>Hedef ortam  
 Bir TAP yöntemi oluştururken, zaman uyumsuz yürütülmenin nerede olacağını belirleyebilirsiniz. İş yükünü iş parçacığı havuzunda çalıştırmayı, zaman uyumsuz I/O kullanarak oluşturmayı (işlemin yürütülmesinin çoğunluğunda bir iş parçacığına bağlı kalmayarak), belirli bir iş parçacığında yürütmeyi (örneğin UI iş parçacığı), veya diğer olası bağlamları kullanmayı tercih edebilirsiniz. Bir TAP yönteminin yürütülmesi hiçbir şey olmasa da, bir <xref:System.Threading.Tasks.Task> koşulun sistemde başka bir yerde (örneğin, bir sıraya alınmış veri yapısına ulaşan verileri temsil eden bir görev) oluşumunu temsil eden bir, döndürebilir.

 TAP metodunu çağıran, elde edilen görevde zaman uyumlu olarak bekleyen TAP yönteminin tamamlanmasını beklemeyi engelleyebilir veya zaman uyumsuz işlem tamamlandığında ek (devamlılık) kodu çalıştırabilir. Devam kodunun yaratıcısı kodun nerede çalışacağına dair denetime sahiptir. <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task.ContinueWith%2A> Devamlılığın üzerinde oluşturulmuş dil desteğini kullanarak (örneğin, Visual Basic C# ' de, `await` `Await` `AwaitValue` F # ' da), devam kodunu doğrudan, sınıf üzerinde yöntemler aracılığıyla (örneğin,) veya örtük olarak oluşturabilirsiniz.  
  
## <a name="task-status"></a>Görev durumu  
 <xref:System.Threading.Tasks.Task>Sınıfı, zaman uyumsuz işlemler için bir yaşam döngüsü sağlar ve bu döngüye numaralandırma tarafından temsil edilir <xref:System.Threading.Tasks.TaskStatus> . Ve ' den türetilen türlerin köşe durumlarını desteklemek <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> ve oluşturma işleminden oluşturma ile ayırmayı desteklemek için, <xref:System.Threading.Tasks.Task> sınıfı bir <xref:System.Threading.Tasks.Task.Start%2A> yöntemi gösterir. Ortak oluşturucular tarafından oluşturulan görevler <xref:System.Threading.Tasks.Task> , yaşam döngüsünü zamanlanmamış durumda başladıklarından *cold tasks* <xref:System.Threading.Tasks.TaskStatus.Created> ve yalnızca bu örneklerde çağrıldığında zamanlandıklarından soğuk görevler olarak adlandırılır <xref:System.Threading.Tasks.Task.Start%2A> .

 Diğer tüm görevler yaşam döngülerine etkin bir durumda başlar, bu da temsil ettikleri zaman uyumsuz işlemlerin zaten başlatıldığı ve görev durumlarının dışında bir numaralandırma değeri olduğu anlamına gelir <xref:System.Threading.Tasks.TaskStatus.Created?displayProperty=nameWithType> . TAP yöntemlerinden döndürülen tüm görevler etkinleştirilmelidir. **Bir TAP yöntemi, döndürülecek görevi örneklemek için bir görevin oluşturucusunu dahili olarak kullanıyorsa, dokunarak yöntemi <xref:System.Threading.Tasks.Task.Start%2A> <xref:System.Threading.Tasks.Task> döndürmeden önce nesneyi çağırmalıdır.** Bir TAP yönteminin tüketicileri, döndürülen görevin etkin olduğunu ve <xref:System.Threading.Tasks.Task.Start%2A> <xref:System.Threading.Tasks.Task> bir tap yönteminden döndürülen herhangi bir çağrı yapmayı denemeyeceğini güvenle varsayabilir. <xref:System.Threading.Tasks.Task.Start%2A>Etkin bir görevde çağırma bir <xref:System.InvalidOperationException> özel durumla sonuçlanır.  
  
## <a name="cancellation-optional"></a>İptal (isteğe bağlı)  
 TAP kullanırken, iptal etmek hem zaman uyumsuz yöntem oluşturucuları hem de zaman uyumsuz yöntem tüketicileri için isteğe bağlıdır. Bir işlem iptaline izin veriyorsa, zaman uyumsuz yöntemin bir iptal belirtecini (örnek) kabul eden bir aşırı yüklemesini kullanıma sunar <xref:System.Threading.CancellationToken> . Kuralına göre parametresi olarak adlandırılır `cancellationToken` .  
  
 [!code-csharp[Conceptual.TAP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#1)]
 [!code-vb[Conceptual.TAP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#1)]  
  
 Zaman uyumsuz işlem iptal istekleri için bu belirteci izler. Eğer iptal isteği alırsa, bu isteği dikkate alarak işlemi iptal etmeyi seçebilir. İptal isteğinin çalışması erken sonlanıyorsa, TAP yöntemi durumunda biten bir görev döndürür <xref:System.Threading.Tasks.TaskStatus.Canceled> ; kullanılabilir sonuç yoktur ve hiçbir özel durum oluşturulmaz.  <xref:System.Threading.Tasks.TaskStatus.Canceled>Durum, ve durumları ile birlikte bir görevin son (tamamlandı) durumu olarak değerlendirilir <xref:System.Threading.Tasks.TaskStatus.Faulted> <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> . Bu nedenle, bir görev <xref:System.Threading.Tasks.TaskStatus.Canceled> durumundaysa, <xref:System.Threading.Tasks.Task.IsCompleted%2A> özelliği döndürür `true` . Bir görev <xref:System.Threading.Tasks.TaskStatus.Canceled> durumunda tamamlandığında, görevle kaydedilen tüm <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled> devamlılık, Devamlılığın devre dışı bırakılmasıyla ilgili bir devamlılık seçeneği belirtilmediği sürece zamanlanır veya yürütülür. Zaman uyumsuz bir görev için dil özellikleri kullanımı aracılığıyla bekleyen tüm kodlar çalışmaya devam eder, ancak bir <xref:System.OperationCanceledException> veya ondan türetilmiş bir özel durum alır. , Gibi yöntemler aracılığıyla görevde zaman uyumlu olarak engellenen <xref:System.Threading.Tasks.Task.Wait%2A> ve <xref:System.Threading.Tasks.Task.WaitAll%2A> Ayrıca bir özel durumla çalışmaya devam eden kod.  
  
 Bir iptal belirteci, bu belirteci kabul eden TAP yöntemi çağrılmadan önce iptal isteğinde bulunursa, TAP yöntemi bir <xref:System.Threading.Tasks.TaskStatus.Canceled> görev döndürmelidir.  Ancak, eğer zaman uyumsuz işlem yürütülüyorken bir iptal istenirse, zaman uyumsuz işlem iptal isteğini kabul etmek zorunda değildir.  Döndürülen görev, <xref:System.Threading.Tasks.TaskStatus.Canceled> yalnızca işlem iptal isteğinin sonucu olarak sonlanıyorsa durumunda sona ermelidir. İptal isteniyorsa ancak bir sonuç ya da bir özel durum hala üretildiyse, görevin <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> veya durumunda bitmesi gerekir <xref:System.Threading.Tasks.TaskStatus.Faulted> .

 İlk ve daha sonra iptal etme özelliğini göstermek isteyen zaman uyumsuz yöntemler için, iptal belirtecini kabul etmeyen bir aşırı yükleme sağlamanız gerekmez. İptal edilemeyen yöntemler için iptal belirteci kabul eden bir aşırı yükleme sağlamayın; bu çağırana hedef yöntemin iptal edilip edilemez olduğunu belirtmeye yardımcı olur.  İptal gerektirmeyen tüketici kodu <xref:System.Threading.CancellationToken> <xref:System.Threading.CancellationToken.None%2A> , bağımsız değişken değeri olarak bir ve sağlayan bir yöntemi çağırabilir. <xref:System.Threading.CancellationToken.None%2A>, varsayılan olarak işlevsel olarak eşdeğerdir <xref:System.Threading.CancellationToken> .  
  
## <a name="progress-reporting-optional"></a>İlerleme raporlaması (isteğe bağlı)  
 Bazı zaman uyumsuz işlemler ilerleme bildirimlerinden faydalanır; bunlar genel olarak kullanıcı arayüzünü zaman uyumsuz işlemin ilerlemesi ile ilgili bilgiyle güncelleştirmekte kullanılır.

 TAP, işlem <xref:System.IProgress%601> zaman uyumsuz metoda genellikle adlı bir parametre olarak geçirilen bir arabirim aracılığıyla işlenir `progress` .  Zaman uyumsuz yöntem çağırıldığında ilerleme arabirimini sağlamak yanlış kullanım nedeniyle ortaya çıkan yarış durumlarını engellemeye yardımcı olur (yanlış kayıt olan olay işleyicilerinin işlem başladıktan sonra güncellemeleri kaçırabilmesi).  Daha da önemlisi, ilerleme arabirimi ilerlemenin tüketici kodunda belirlendiği üzere farklı uygulamalarını destekleyebilir.  Örneğin, tüketici kod yalnızca en son ilerleme güncellemesini isteyebilir, ya da tüm güncellemeleri arabelleğe koyabilir, ya da her güncelleme için bir eylem çağırabilir, ya da çağrının belirli bir iş parçacığına yönlendirilip yönlendirilmediğini denetlemek isteyebilir. Bütün bu seçenekler belirli tüketicinin ihtiyaçlarına göre arabirimin farklı uygulamalarını kullanarak elde edilebilir.  İptalde olduğu gibi, dokunma uygulamaları <xref:System.IProgress%601> yalnızca API ilerleme bildirimlerini destekliyorsa bir parametre sağlamalıdır.

 Örneğin, `ReadAsync` Bu makalenin önceki bölümlerinde ele alınan yöntem ara ilerlemeyi, okunan bayt sayısı biçiminde raporlamazsa, ilerleme geri araması bir <xref:System.IProgress%601> arabirim olabilir:  
  
 [!code-csharp[Conceptual.TAP#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#2)]
 [!code-vb[Conceptual.TAP#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#2)]  
  
 Bir `FindFilesAsync` Yöntem belirli bir arama düzenine uyan tüm dosyaların listesini döndürürse, ilerleme durumu geri çağırma işlemi tamamlanan iş yüzdesinin yanı sıra geçerli kısmi sonuç kümesi için bir tahmin sağlayabilir.  Bunu ya bir kayıt düzeni ile yapabilir:  
  
 [!code-csharp[Conceptual.TAP#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#3)]
 [!code-vb[Conceptual.TAP#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#3)]  
  
 ya da API'ye özel bir veri türü ile yapabilir:  
  
 [!code-csharp[Conceptual.TAP#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#4)]
 [!code-vb[Conceptual.TAP#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#4)]  
  
 İkinci durumda, özel veri türü genellikle ile sonlenir `ProgressInfo` .  
  
 TAP uygulamalarında bir parametreyi kabul eden aşırı yüklemeler varsa `progress` , bağımsız değişkenin olması gerekir `null` , bu durumda hiçbir ilerleme bildirilmeyecektir. DOKUNMA uygulamaları, <xref:System.Progress%601> zaman uyumsuz yöntemin hızlı bir şekilde ilerlemesini sağlaması ve ilerleme durumunun, bilgilerin nasıl ve en iyi şekilde işleneceğini belirlemesine olanak tanıyan, ilerlemeyi zaman uyumlu olarak nesneye bildirmelidir. Örneğin, ilerleme örneği geri aramaları yönlendirmeyi ve yakalanan bir eşitleme bağlamında olay çağırmayı seçebilir.  
  
## <a name="iprogresst-implementations"></a>IProgress \<T> uygulamaları  
 .NET Framework 4,5 tek bir uygulama sağlar <xref:System.IProgress%601> : <xref:System.Progress%601> . <xref:System.Progress%601>Sınıfı şu şekilde bildirilmiştir:  
  
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
  
 Bir örneği <xref:System.Progress%601> <xref:System.Progress%601.ProgressChanged> , zaman uyumsuz işlem bir ilerleme güncelleştirmesi raporlayan her seferinde oluşturulan bir olayı ortaya koyar. <xref:System.Progress%601.ProgressChanged>Olay, <xref:System.Threading.SynchronizationContext> örnek örneği oluşturulduğunda yakalanan nesne üzerinde tetiklenir <xref:System.Progress%601> . Eğer hiçbir eşitleme bağlamı kullanılabilir değilse, iş parçacığı havuzunu hedefleyen bir varsayılan bağlam kullanılır. İşleyiciler bu olay ile kayıtlı olabilir. Tek bir işleyici Ayrıca <xref:System.Progress%601> oluşturucuya kolaylık sağlaması için de sağlanmayabilir ve olay için bir olay işleyicisi gibi davranır <xref:System.Progress%601.ProgressChanged> . İlerleme güncelleştirmeleri zaman uyumsuz işlemi olay işleyicileri yürütülürken geciktirmemek için zaman uyumsuz olarak harekete geçirilir. Başka bir <xref:System.IProgress%601> uygulama farklı anlamları uygulamayı seçebilir.  
  
## <a name="choosing-the-overloads-to-provide"></a>Sağlanacak aşırı yüklemeleri seçme  
 Bir dokunma uygulamasında hem isteğe bağlı hem de <xref:System.Threading.Tasks.TaskFactory.CancellationToken%2A> isteğe bağlı <xref:System.IProgress%601> Parametreler kullanılıyorsa, bu muhtemelen en fazla dört aşırı yükleme gerektirebilir:  
  
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
  
 İki eksik ara birleşimi dengelemek için, geliştiriciler <xref:System.Threading.CancellationToken.None%2A> <xref:System.Threading.CancellationToken> `cancellationToken` parametresi için ve parametresi için bir varsayılan değer geçirebilir `null` `progress` .  
  
 Eğer TAP yönteminin her kullanımının iptal veya ilerleme desteklemesini istiyorsanız, ilgili parametreyi kabul etmeyen aşırı yüklemeleri çıkarabilirsiniz.  
  
 İptali veya ilerlemeyi isteğe bağlı hale getirmek için birden çok aşırı yük ortaya çıkarmak isterseniz, iptal veya ilerleme durumunu desteklemeyen aşırı yüklemeler, <xref:System.Threading.CancellationToken.None%2A> iptal için başarılı veya `null` bunları destekleyen aşırı yüklemeye devam ediyor gibi davranır.  
  
## <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Zaman uyumsuz programlama desenleri](index.md)|Zaman uyumsuz işlemler gerçekleştirmek için üç desen tanıtır: Görev-tabanlı Zaman Uyumsuz Desen (TAP), Zaman Uyumsuz Programlama Modeli (APM) ve Olay-tabanlı Uyumsuz Desen (EAP).|  
|[Görev Tabanlı Zaman Uyumsuz Deseni Uygulama](implementing-the-task-based-asynchronous-pattern.md)|Görev-tabanlı Zaman Uyumsuz Desen (TAP) uygulamak için üç yol açıklar: Visual Studio içindeki C# ve Visual Basic derleyicilerini kullanarak, el yöntemi ile, veya derleyici ve el yönteminin bir kombinasyonu ile.|  
|[Görev Tabanlı Zaman Uyumsuz Desen Kullanma](consuming-the-task-based-asynchronous-pattern.md)|Engellemeden beklemeyi görevler ve geri aramalar kullanarak nasıl kullanacağınızı açıklar.|  
|[Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma](interop-with-other-asynchronous-patterns-and-types.md)|Zaman Uyumsuz Programlama Modeli (APM) ve Olay-tabanlı Zaman Uyumsuz Model (EAP) uygulamak için Görev-tabanlı Zaman Uyumsuz Model'in nasıl kullanılacağını açıklar.|
