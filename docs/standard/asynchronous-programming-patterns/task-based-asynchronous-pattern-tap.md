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
ms.openlocfilehash: f61ad49753da9d96e733ea667095722ddc238fe1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121107"
---
# <a name="task-based-asynchronous-pattern-tap"></a>Görev tabanlı zaman uyumsuz model (TAP)
Görev tabanlı zaman uyumsuz model (TAP), rastgele zaman uyumsuz işlemleri temsil etmek için kullanılan <xref:System.Threading.Tasks?displayProperty=nameWithType> ad alanındaki <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> türlerini temel alır. TAP yeni geliştirme için önerilen zaman uyumsuz tasarım desenidir.  
  
## <a name="naming-parameters-and-return-types"></a>Adlandırma, parametreler ve dönüş türleri

TAP, bir zaman uyumsuz işlemin başlangıcını ve tamamlanmasını temsil etmek için tek bir yöntem kullanır. Bu, hem zaman uyumsuz programlama modeli (APM veya `IAsyncResult`) düzeniyle hem de olay tabanlı zaman uyumsuz model (EAP) ile karşıttır. APM `Begin` ve `End` yöntemleri gerektirir. EAP `Async` sonekine sahip bir yöntem gerektirir ve ayrıca bir veya daha fazla olay, olay işleyicisi temsilci türü ve `EventArg`türetilmiş türler gerektirir. DOKUNMADA zaman uyumsuz yöntemler, <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask>ve <xref:System.Threading.Tasks.ValueTask%601>gibi, bir işlem adından sonra `Async` sonekini içerir. Örneğin, bir `Task<String>` döndüren zaman uyumsuz `Get` işlemi `GetAsync`olarak adlandırılabilir. Zaten `Async` sonekine sahip bir EAP yöntemi adı içeren bir sınıfa bir TAP yöntemi ekliyorsanız, bunun yerine sonek `TaskAsync` kullanın. Örneğin, sınıfın zaten bir `GetAsync` yöntemi varsa, `GetTaskAsync`adı kullanın. Bir yöntem zaman uyumsuz bir işlem başlatır ancak bir awasever türü döndürmezse, bu yöntemin işlemin sonucunu döndürmeyeceğini veya oluşturmadığını önermek için, adının `Begin`, `Start`veya başka bir fiil ile başlaması gerekir.  
  
 TAP metodu, karşılık gelen zaman uyumlu yöntemin void veya bir tür `TResult`döndürmeksizin <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> ya da <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>döndürür.  
  
 Bir TAP yönteminin parametreleri, zaman uyumlu karşılığına ait parametrelerle eşleşmelidir ve aynı sırada sağlanmalıdır.  Ancak, `out` ve `ref` parametreleri bu kuraldan muaf tutulur ve tamamen kaçınılmalıdır. Bir `out` veya `ref` parametresi aracılığıyla döndürülen tüm veriler yerine <xref:System.Threading.Tasks.Task%601>tarafından döndürülen `TResult` parçası olarak döndürülmelidir ve birden çok değere uyum sağlamak için bir tanımlama grubu ya da özel veri yapısı kullanmalıdır. Ayrıca, yöntemin zaman uyumlu karşılığı bir tane sunmasa bile <xref:System.Threading.CancellationToken> parametresi eklemeyi göz önünde bulundurmanız gerekir.
 
 Özel olarak, görev oluşturma, düzenleme veya görev birleşimine ayrılan Yöntemler (metodun zaman uyumsuz hedefinin Yöntem adı içinde veya yöntemin ait olduğu türün adı) bu adlandırma modelini izlemesi gerekmez; Bu tür yöntemler genellikle *kombinatör*olarak adlandırılır. Kombinatör örnekleri <xref:System.Threading.Tasks.Task.WhenAll%2A> ve <xref:System.Threading.Tasks.Task.WhenAny%2A>içerir ve [görev tabanlı zaman uyumsuz model](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)kullanan makalenin [yerleşik görev tabanlı kombinatör](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md#combinators) bölümünde açıklanmaktadır.  
  
 DOKUNMA sözdiziminin, zaman uyumsuz programlama modeli (APM) ve olay tabanlı zaman uyumsuz desen (EAP) gibi eski zaman uyumsuz programlama desenlerinde kullanılan sözdiziminden farklı olduğu örnekler için bkz. [zaman uyumsuz programlama desenleri](../../../docs/standard/asynchronous-programming-patterns/index.md).  
  
## <a name="initiating-an-asynchronous-operation"></a>Zaman uyumsuz bir işlem başlatılıyor  
 TAP tabanlı bir zaman uyumsuz yöntem elde edilen görevi döndürmeden önce, az miktarda bir işi (bağımsız değişkenleri doğrulamak ya da zaman uyumsuz işlemi başlatmak gibi) zaman uyumlu olarak yapabilir. Zaman uyumsuz yöntemin çabuk dönmesini sağlamak için zaman uyumlu iş olabildiğince az tutulmalıdır. Hızlı dönüş nedenleri şunlardır:  
  
- Zaman uyumsuz yöntemler kullanıcı arabirimi (UI) iş parçacıkları tarafında çağırılabilirler, ve herhangi bir uzun süre çalışan zaman uyumlu iş uygulamanın yanıt verme becerisine zarar verebilir.  
  
- Birden çok zaman uyumsuz yöntem eşzamanlı başlatılabilir. Bu nedenle, bir zaman uyumsuz yöntemin herhangi bir uzun süren zaman uyumlu bölümü diğer zaman uyumsuz işlemlerin başlamasını geciktirerek eşzamanlılığın yararlarını azaltabilir.  
  
 Bazı durumlarda, işlemi tamamlamak için gereken iş, işlemi zaman uyumsuz olarak başlatmak için gereken işten daha azdır. Okuma işleminin bellekte zaten arabelleğe alınmış veri ile tamamlanabileceği bir akıştan okumak bu duruma bir örnektir. Bu gibi durumlarda, işlem zaman uyumlu olarak tamamlanabilir ve zaten tamamlanmış bir görevi döndürebilir.  
  
## <a name="exceptions"></a>Özel Durumlar  
 Bir zaman uyumsuz yöntem, zaman uyumsuz yöntem çağrısının dışına atılacak bir özel durumu sadece bir kullanım hatasına yanıt olarak harekete geçirmelidir. Kullanım hataları asla üretim kodunda gerçekleşmemelidir. Örneğin, yöntemin bağımsız değişkenlerinden biri bir hata durumuna neden olursa (genellikle bir <xref:System.ArgumentNullException> özel durumu tarafından temsil edilir) bir null başvurusu (Visual Basic`Nothing`) geçirilirse, bir null başvurusunun hiçbir şekilde geçirilmeyeceğinden emin olmak için çağıran kodu değiştirebilirsiniz. Diğer bütün hatalar için, görev döndürülene kadar zaman uyumsuz yöntem zaman uyumlu olarak tamamlansa bile, zaman uyumsuz yöntem yürütülüyorken oluşan özel durumlar döndürülen göreve atanmalıdır. Genel olarak, bir görev en fazla bir özel durum içerir. Ancak, görev birden çok işlemi temsil ediyorsa (örneğin, <xref:System.Threading.Tasks.Task.WhenAll%2A>), birden çok özel durum tek bir görevle ilişkilendirilebilir.  
  
## <a name="target-environment"></a>Hedef ortam  
 Bir TAP yöntemi oluştururken, zaman uyumsuz yürütülmenin nerede olacağını belirleyebilirsiniz. İş yükünü iş parçacığı havuzunda çalıştırmayı, zaman uyumsuz I/O kullanarak oluşturmayı (işlemin yürütülmesinin çoğunluğunda bir iş parçacığına bağlı kalmayarak), belirli bir iş parçacığında yürütmeyi (örneğin UI iş parçacığı), veya diğer olası bağlamları kullanmayı tercih edebilirsiniz. Bir TAP yönteminin yürütülmesi hiçbir şey olmayabilir ve yalnızca sistemde başka bir yerde (örneğin, bir sıraya alınmış veri yapısına ulaşan verileri temsil eden bir görev) bir koşulun oluşumunu temsil eden bir <xref:System.Threading.Tasks.Task> döndürebilir.
 
 TAP metodunu çağıran, elde edilen görevde zaman uyumlu olarak bekleyen TAP yönteminin tamamlanmasını beklemeyi engelleyebilir veya zaman uyumsuz işlem tamamlandığında ek (devamlılık) kodu çalıştırabilir. Devam kodunun yaratıcısı kodun nerede çalışacağına dair denetime sahiptir. Devamlılığın üzerinde yerleşik olarak bulunan dil desteğini kullanarak (örneğin, <xref:System.Threading.Tasks.Task.ContinueWith%2A>) veya örtük olarak, Devamlılığın üzerinde yerleşik olarak (örneğin, `await` C#`Await` Visual Basic <xref:System.Threading.Tasks.Task> _5_ inç F#).  
  
## <a name="task-status"></a>Görev durumu  
 <xref:System.Threading.Tasks.Task> sınıfı, zaman uyumsuz işlemler için bir yaşam döngüsü sağlar ve bu döngüyle <xref:System.Threading.Tasks.TaskStatus> numaralandırması gösterilir. <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601>türetilen türlerin köşe durumlarını desteklemek ve oluşturma işleminden elde edilen ayırmanın ayrılmasını desteklemek için, <xref:System.Threading.Tasks.Task> sınıfı bir <xref:System.Threading.Tasks.Task.Start%2A> yöntemi sunar. Ortak <xref:System.Threading.Tasks.Task> oluşturucular tarafından oluşturulan görevler, yaşam döngüsünü zamanlanmamış <xref:System.Threading.Tasks.TaskStatus.Created> durumunda başladıklarından ve yalnızca bu örneklerde <xref:System.Threading.Tasks.Task.Start%2A> çağrıldığında zamanlandıklarından *soğuk görevler*olarak adlandırılır. 
 
 Diğer tüm görevler yaşam döngüsünü etkin bir durumda başlatır. Bu, temsil ettikleri zaman uyumsuz işlemlerin zaten başlatıldığı ve görev durumlarının <xref:System.Threading.Tasks.TaskStatus.Created?displayProperty=nameWithType>dışında bir numaralandırma değeri olduğu anlamına gelir. TAP yöntemlerinden döndürülen tüm görevler etkinleştirilmelidir. **Bir TAP yöntemi, döndürülecek görevi örneklemek için bir görevin oluşturucusunu dahili olarak kullanıyorsa, TAP yöntemi döndürmeden önce <xref:System.Threading.Tasks.Task> nesnesi üzerinde <xref:System.Threading.Tasks.Task.Start%2A> çağırmalıdır.** Bir TAP yönteminin tüketicileri, döndürülen görevin etkin olduğunu ve bir TAP yönteminden döndürülen <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task.Start%2A> çağırmayı denememelidir. Etkin bir görevde <xref:System.Threading.Tasks.Task.Start%2A> çağırmak, <xref:System.InvalidOperationException> özel durumuyla sonuçlanır.  
  
## <a name="cancellation-optional"></a>İptal (isteğe bağlı)  
 TAP kullanırken, iptal etmek hem zaman uyumsuz yöntem oluşturucuları hem de zaman uyumsuz yöntem tüketicileri için isteğe bağlıdır. Bir işlem iptaline izin veriyorsa, zaman uyumsuz yöntemin bir iptal belirtecini kabul eden bir aşırı yüklemesi sunar (<xref:System.Threading.CancellationToken> örneği). Kural gereği, parametre `cancellationToken`olarak adlandırılır.  
  
 [!code-csharp[Conceptual.TAP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#1)]
 [!code-vb[Conceptual.TAP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#1)]  
  
 Zaman uyumsuz işlem iptal istekleri için bu belirteci izler. Eğer iptal isteği alırsa, bu isteği dikkate alarak işlemi iptal etmeyi seçebilir. İptal isteğinin çalışması erken sonlanıyorsa, TAP yöntemi <xref:System.Threading.Tasks.TaskStatus.Canceled> durumunda biten bir görev döndürür; kullanılabilir sonuç yok ve hiçbir özel durum oluşturulmaz.  <xref:System.Threading.Tasks.TaskStatus.Canceled> durum, <xref:System.Threading.Tasks.TaskStatus.Faulted> ve <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> durumlarıyla birlikte bir görevin son (tamamlandı) durumu olarak değerlendirilir. Bu nedenle, bir görev <xref:System.Threading.Tasks.TaskStatus.Canceled> durumundaysa, <xref:System.Threading.Tasks.Task.IsCompleted%2A> özelliği `true`döndürür. Bir görev <xref:System.Threading.Tasks.TaskStatus.Canceled> durumunda tamamlandığında, görevle kaydedilen tüm devamlılık, devamlılığı geri çevirmek için <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled> gibi bir devamlılık seçeneği belirtilmediği sürece zamanlanır veya yürütülür. Dil özellikleri kullanılarak iptal edilen bir görevin zaman uyumsuz olarak beklediği tüm kodlar çalışmaya devam eder, ancak bir <xref:System.OperationCanceledException> veya ondan türetilmiş bir özel durum alır. <xref:System.Threading.Tasks.Task.Wait%2A> ve <xref:System.Threading.Tasks.Task.WaitAll%2A> gibi yöntemler aracılığıyla görevde zaman uyumlu olarak engellenen kod ayrıca bir özel durumla çalışmaya devam eder.  
  
 Bir iptal belirteci, bu belirteci kabul eden TAP yöntemi çağrılmadan önce iptal isteğinde bulunursa, TAP yöntemi bir <xref:System.Threading.Tasks.TaskStatus.Canceled> görevi döndürmelidir.  Ancak, eğer zaman uyumsuz işlem yürütülüyorken bir iptal istenirse, zaman uyumsuz işlem iptal isteğini kabul etmek zorunda değildir.  Döndürülen görevin, yalnızca işlem iptal isteğinin sonucu olarak sonlanıyorsa <xref:System.Threading.Tasks.TaskStatus.Canceled> durumunda bitmesi gerekir. İptal isteniyorsa ancak bir sonuç ya da bir özel durum hala üretildiyse, görevin <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> veya <xref:System.Threading.Tasks.TaskStatus.Faulted> durumunda bitmesi gerekir. 
 
 İlk ve daha sonra iptal etme özelliğini göstermek isteyen zaman uyumsuz yöntemler için, iptal belirtecini kabul etmeyen bir aşırı yükleme sağlamanız gerekmez. İptal edilemeyen yöntemler için iptal belirteci kabul eden bir aşırı yükleme sağlamayın; bu çağırana hedef yöntemin iptal edilip edilemez olduğunu belirtmeye yardımcı olur.  İptal gerektirmeyen tüketici kodu, bir <xref:System.Threading.CancellationToken> kabul eden ve bağımsız değişken değeri olarak <xref:System.Threading.CancellationToken.None%2A> sağlayan bir yöntemi çağırabilir. <xref:System.Threading.CancellationToken.None%2A>, varsayılan <xref:System.Threading.CancellationToken>işlevsel olarak eşdeğerdir.  
  
## <a name="progress-reporting-optional"></a>İlerleme raporlaması (isteğe bağlı)  
 Bazı zaman uyumsuz işlemler ilerleme bildirimlerinden faydalanır; bunlar genel olarak kullanıcı arayüzünü zaman uyumsuz işlemin ilerlemesi ile ilgili bilgiyle güncelleştirmekte kullanılır. 
 
 TAP, işlem zaman uyumsuz metoda genellikle `progress`adlı bir parametre olarak geçirilen bir <xref:System.IProgress%601> arabirimi aracılığıyla işlenir.  Zaman uyumsuz yöntem çağırıldığında ilerleme arabirimini sağlamak yanlış kullanım nedeniyle ortaya çıkan yarış durumlarını engellemeye yardımcı olur (yanlış kayıt olan olay işleyicilerinin işlem başladıktan sonra güncellemeleri kaçırabilmesi).  Daha da önemlisi, ilerleme arabirimi ilerlemenin tüketici kodunda belirlendiği üzere farklı uygulamalarını destekleyebilir.  Örneğin, tüketici kod yalnızca en son ilerleme güncellemesini isteyebilir, ya da tüm güncellemeleri arabelleğe koyabilir, ya da her güncelleme için bir eylem çağırabilir, ya da çağrının belirli bir iş parçacığına yönlendirilip yönlendirilmediğini denetlemek isteyebilir. Bütün bu seçenekler belirli tüketicinin ihtiyaçlarına göre arabirimin farklı uygulamalarını kullanarak elde edilebilir.  İptalde olduğu gibi, dokunma uygulamaları yalnızca API ilerleme bildirimlerini destekliyorsa <xref:System.IProgress%601> bir parametre sağlamalıdır. 
 
 Örneğin, bu makalenin önceki bölümlerinde ele alınan `ReadAsync` yöntemi ara ilerlemeyi, bu nedenle şimdiye kadar okunan bayt sayısı biçiminde raporlamazsa, ilerleme geri araması bir <xref:System.IProgress%601> arabirimi olabilir:  
  
 [!code-csharp[Conceptual.TAP#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#2)]
 [!code-vb[Conceptual.TAP#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#2)]  
  
 Bir `FindFilesAsync` yöntemi belirli bir arama düzenine uyan tüm dosyaların listesini döndürürse, ilerleme durumu geri çağırma işlemi tamamlanan iş yüzdesinin yanı sıra geçerli kısmi sonuç kümesi için bir tahmin sağlayabilir.  Bunu ya bir kayıt düzeni ile yapabilir:  
  
 [!code-csharp[Conceptual.TAP#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#3)]
 [!code-vb[Conceptual.TAP#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#3)]  
  
 ya da API'ye özel bir veri türü ile yapabilir:  
  
 [!code-csharp[Conceptual.TAP#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#4)]
 [!code-vb[Conceptual.TAP#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#4)]  
  
 İkinci durumda, özel veri türü genellikle `ProgressInfo`ile sonlenir.  
  
 TAP uygulamalarında bir `progress` parametresi kabul eden aşırı yüklemeler varsa, bağımsız değişkenin `null`izin vermesi gerekir, bu durumda hiçbir ilerleme bildirilmeyecektir. DOKUNMA uygulamaları, zaman uyumsuz yöntemin hızlı bir şekilde ilerlemesini sağlaması ve ilerleme durumunun, bilgilerin nasıl ve en iyi şekilde işleneceğini belirlemesine olanak sağlayan <xref:System.Progress%601> nesnesine zaman uyumlu olarak rapor etmelidir. Örneğin, ilerleme örneği geri aramaları yönlendirmeyi ve yakalanan bir eşitleme bağlamında olay çağırmayı seçebilir.  
  
## <a name="iprogresst-implementations"></a>IProgress\<T > uygulamalar  
 .NET Framework 4,5, tek bir <xref:System.IProgress%601> uygulama sağlar: <xref:System.Progress%601>. <xref:System.Progress%601> sınıfı şu şekilde bildirilmiştir:  
  
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
  
 Bir <xref:System.Progress%601> örneği, zaman uyumsuz işlem bir ilerleme güncelleştirmesi raporlayan her seferinde oluşturulan <xref:System.Progress%601.ProgressChanged> olayını gösterir. <xref:System.Progress%601.ProgressChanged> olay, <xref:System.Progress%601> örneği örneği oluşturulduğunda yakalanan <xref:System.Threading.SynchronizationContext> nesnesi üzerinde oluşturulur. Eğer hiçbir eşitleme bağlamı kullanılabilir değilse, iş parçacığı havuzunu hedefleyen bir varsayılan bağlam kullanılır. İşleyiciler bu olay ile kayıtlı olabilir. Tek bir işleyici, <xref:System.Progress%601> oluşturucusuna kolaylık sağlaması için de sağlanmış olabilir ve yalnızca <xref:System.Progress%601.ProgressChanged> olayı için bir olay işleyicisi gibi davranır. İlerleme güncelleştirmeleri zaman uyumsuz işlemi olay işleyicileri yürütülürken geciktirmemek için zaman uyumsuz olarak harekete geçirilir. Başka bir <xref:System.IProgress%601> uygulaması farklı anlamları uygulamayı seçebilir.  
  
## <a name="choosing-the-overloads-to-provide"></a>Sağlanacak aşırı yüklemeleri seçme  
 Bir dokunma uygulamasında hem isteğe bağlı <xref:System.Threading.Tasks.TaskFactory.CancellationToken%2A> hem de isteğe bağlı <xref:System.IProgress%601> parametreleri kullanılıyorsa, bu muhtemelen dört adede kadar aşırı yükleme gerektirebilir:  
  
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
  
 İki eksik ara birleşimi dengelemek için, geliştiriciler `cancellationToken` parametresi için <xref:System.Threading.CancellationToken.None%2A> veya varsayılan <xref:System.Threading.CancellationToken> ve `progress` parametresi için `null` geçirebilir.  
  
 Eğer TAP yönteminin her kullanımının iptal veya ilerleme desteklemesini istiyorsanız, ilgili parametreyi kabul etmeyen aşırı yüklemeleri çıkarabilirsiniz.  
  
 İptali veya ilerlemeyi isteğe bağlı hale getirmek için birden çok aşırı yük sunmaya karar verirseniz, iptal veya ilerlemeyi desteklemeyen aşırı yüklemeler, iptal için <xref:System.Threading.CancellationToken.None%2A> veya destek sağlayan aşırı yüklemeye ilerleme için `null` gibi davranır. Bu.  
  
## <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Zaman Uyumsuz Programlama Desenleri](../../../docs/standard/asynchronous-programming-patterns/index.md)|Zaman uyumsuz işlemler gerçekleştirmek için üç desen tanıtır: Görev-tabanlı Zaman Uyumsuz Desen (TAP), Zaman Uyumsuz Programlama Modeli (APM) ve Olay-tabanlı Uyumsuz Desen (EAP).|  
|[Görev Tabanlı Zaman Uyumsuz Deseni Uygulama](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)|Görev-tabanlı Zaman Uyumsuz Desen (TAP) uygulamak için üç yol açıklar: Visual Studio içindeki C# ve Visual Basic derleyicilerini kullanarak, el yöntemi ile, veya derleyici ve el yönteminin bir kombinasyonu ile.|  
|[Görev Tabanlı Zaman Uyumsuz Desen Kullanma](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)|Engellemeden beklemeyi görevler ve geri aramalar kullanarak nasıl kullanacağınızı açıklar.|  
|[Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)|Zaman Uyumsuz Programlama Modeli (APM) ve Olay-tabanlı Zaman Uyumsuz Model (EAP) uygulamak için Görev-tabanlı Zaman Uyumsuz Model'in nasıl kullanılacağını açıklar.|
