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
ms.openlocfilehash: 89c486618729c334bf74f0a1f4f9dd1b3cee8b0e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78158174"
---
# <a name="task-based-asynchronous-pattern-tap"></a>Görev tabanlı eşzamanlı desen (TAP)
Görev tabanlı Eşzamanlı Desen (TAP), rasgele eşzamanlı <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> işlemleri <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> temsil <xref:System.Threading.Tasks?displayProperty=nameWithType> etmek için kullanılan ad alanındaki türleri ve türleri temel alınr. TAP yeni geliştirme için önerilen zaman uyumsuz tasarım desenidir.  
  
## <a name="naming-parameters-and-return-types"></a>Adlandırma, parametreler ve iade türleri

TAP, bir zaman uyumsuz işlemin başlangıcını ve tamamlanmasını temsil etmek için tek bir yöntem kullanır. Bu, hem Asynchronous Programming Model (APM veya) `IAsyncResult`deseni ile hem de Olay tabanlı Asynchronous Deseni (EAP) ile tezat oluşturuyor. APM `Begin` gerektirir `End` ve yöntemleri. EAP, `Async` sonek olan ve bir veya daha fazla olay, olay işleyicisi temsilci türleri ve `EventArg`türetilmiş türleri gerektiren bir yöntem gerektirir. TAP'taki eşsenkronize `Async` yöntemler, işlem adından sonra, , <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask>ve <xref:System.Threading.Tasks.ValueTask%601>. Örneğin, a döndüren `Get` bir `Task<String>` eşzamanlı işlem `GetAsync`adlandırılabilir. `Async` Sonekli bir EAP yöntem adı zaten içeren bir sınıfa TAP yöntemi ekliyorsanız, `TaskAsync` bunun yerine soneki kullanın. Örneğin, sınıfın zaten bir `GetAsync` yöntemi varsa, `GetTaskAsync`adı kullanın. Bir yöntem bir eşzamanlı işlem başlatır ancak bekleyen bir türü döndürmezse, adı , yani `Begin` `Start`başka bir fiille başlamalıdır ve bu yöntemin işlemin sonucunu döndürmediğini veya atmadığını düşündürmelidir.  
  
 TAP yöntemi, karşılık <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> gelen <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>senkron yöntemin geçersiz mi yoksa bir `TResult`tür mü döndürüldünse, a veya a döndürür.  
  
 TAP yönteminin parametreleri senkron muadili parametrelerine uymalı ve aynı sırada sağlanmalıdır.  Ancak, `out` `ref` ve parametreler bu kuraldan muaftır ve tamamen kaçınılmalıdır. Bir `out` veya `ref` parametre aracılığıyla döndürülecek tüm veriler, bunun yerine `TResult` döndürülen <xref:System.Threading.Tasks.Task%601>verilerin bir parçası olarak döndürülmelidir ve birden çok değeri karşılamak için bir tuple veya özel bir veri yapısı kullanmalıdır. TAP yönteminin eşzamanlı <xref:System.Threading.CancellationToken> muadili bir parametre sunmuyorolsa bile bir parametre eklemeyi de düşünmelisiniz.

 Yalnızca görevlerin oluşturulmasına, manipülasyonuna veya birleşimine ayrılmış yöntemler (yöntemin ait olduğu yöntemin asenkron amacının yöntem adında veya yöntemin ait olduğu tür deadında açık olduğu durumlarda) bu adlandırma desenini izlemeniz gerekmez; bu tür yöntemler genellikle *kombinatörler*olarak adlandırılır. Birleştiricilere örnek <xref:System.Threading.Tasks.Task.WhenAll%2A> <xref:System.Threading.Tasks.Task.WhenAny%2A>olarak, Makalenin Görev [Tabanlı Eşzamanlı Deseni Tüketen](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) [Dahili Görev Tabanlı Birleştirmecileri Kullanma](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md#combinators) bölümü yer alır ve ve tartışılır.  
  
 TAP sözdiziminin, Asynchronous Programlama Modeli (APM) ve Olay Tabanlı Eşzamanlı Desen (EAP) gibi eski asynchronöz programlama desenlerinde kullanılan sözdiziminden nasıl farklı olduğunu örnekler için [bkz.](../../../docs/standard/asynchronous-programming-patterns/index.md)  
  
## <a name="initiating-an-asynchronous-operation"></a>Eşzamanlı işlem başlatma  
 TAP tabanlı bir zaman uyumsuz yöntem elde edilen görevi döndürmeden önce, az miktarda bir işi (bağımsız değişkenleri doğrulamak ya da zaman uyumsuz işlemi başlatmak gibi) zaman uyumlu olarak yapabilir. Zaman uyumsuz yöntemin çabuk dönmesini sağlamak için zaman uyumlu iş olabildiğince az tutulmalıdır. Hızlı dönüş nedenleri şunlardır:  
  
- Zaman uyumsuz yöntemler kullanıcı arabirimi (UI) iş parçacıkları tarafında çağırılabilirler, ve herhangi bir uzun süre çalışan zaman uyumlu iş uygulamanın yanıt verme becerisine zarar verebilir.  
  
- Birden çok zaman uyumsuz yöntem eşzamanlı başlatılabilir. Bu nedenle, bir zaman uyumsuz yöntemin herhangi bir uzun süren zaman uyumlu bölümü diğer zaman uyumsuz işlemlerin başlamasını geciktirerek eşzamanlılığın yararlarını azaltabilir.  
  
 Bazı durumlarda, işlemi tamamlamak için gereken iş, işlemi zaman uyumsuz olarak başlatmak için gereken işten daha azdır. Okuma işleminin bellekte zaten arabelleğe alınmış veri ile tamamlanabileceği bir akıştan okumak bu duruma bir örnektir. Bu gibi durumlarda, işlem zaman uyumlu olarak tamamlanabilir ve zaten tamamlanmış bir görevi döndürebilir.  
  
## <a name="exceptions"></a>Özel durumlar  
 Bir zaman uyumsuz yöntem, zaman uyumsuz yöntem çağrısının dışına atılacak bir özel durumu sadece bir kullanım hatasına yanıt olarak harekete geçirmelidir. Kullanım hataları asla üretim kodunda gerçekleşmemelidir. Örneğin, yöntemin bağımsız değişkenlerinden biri olarak bir null reference 'ı (Visual`Nothing` Basic'te) <xref:System.ArgumentNullException> geçmek bir hata durumuna (genellikle bir özel durumla temsil edilir) neden oluyorsa, null başvurusu asla geçirilmediğinden emin olmak için arama kodunu değiştirebilirsiniz. Diğer bütün hatalar için, görev döndürülene kadar zaman uyumsuz yöntem zaman uyumlu olarak tamamlansa bile, zaman uyumsuz yöntem yürütülüyorken oluşan özel durumlar döndürülen göreve atanmalıdır. Genel olarak, bir görev en fazla bir özel durum içerir. Ancak, görev birden çok işlemi temsil <xref:System.Threading.Tasks.Task.WhenAll%2A>ediyorsa (örneğin,), birden çok özel durum tek bir görevle ilişkilendirilebilir.  
  
## <a name="target-environment"></a>Hedef çevre  
 Bir TAP yöntemi oluştururken, zaman uyumsuz yürütülmenin nerede olacağını belirleyebilirsiniz. İş yükünü iş parçacığı havuzunda çalıştırmayı, zaman uyumsuz I/O kullanarak oluşturmayı (işlemin yürütülmesinin çoğunluğunda bir iş parçacığına bağlı kalmayarak), belirli bir iş parçacığında yürütmeyi (örneğin UI iş parçacığı), veya diğer olası bağlamları kullanmayı tercih edebilirsiniz. Bir TAP yönteminin yürütülecek hiçbir şeyi <xref:System.Threading.Tasks.Task> olmayabilir ve yalnızca sistemin başka bir yerinde ki bir koşulun oluşumunu temsil eden bir durum döndürebilir (örneğin, sıraya alınan veri yapısına gelen verileri temsil eden bir görev).

 TAP yöntemini arayan kişi, ortaya çıkan görevi eşzamanlı olarak bekleyerek TAP yönteminin tamamlanmasını engelleyebilir veya eşzamanlı işlem tamamlandığında ek (devamı) kodu çalıştırabilir. Devam kodunun yaratıcısı kodun nerede çalışacağına dair denetime sahiptir. Devam <xref:System.Threading.Tasks.Task> kodunu, devamların üzerine inşa edilmiş dil desteğini kullanarak <xref:System.Threading.Tasks.Task.ContinueWith%2A>(örneğin, sınıf üzerindeki yöntemlerle (örneğin) veya dolaylı `await` olarak (örneğin, C#, `Await` Visual Basic'te, `AwaitValue` F#'da) kullanarak devam kodunu oluşturabilirsiniz.  
  
## <a name="task-status"></a>Görev durumu  
 Sınıf, <xref:System.Threading.Tasks.Task> eşzamanlı işlemler için bir yaşam döngüsü sağlar ve bu <xref:System.Threading.Tasks.TaskStatus> döngü numaralandırma ile temsil edilir. Türlerden türeyen köşe <xref:System.Threading.Tasks.Task> durumlarını <xref:System.Threading.Tasks.Task%601>desteklemek ve inşaatın zamanlamadan ayrılmasını <xref:System.Threading.Tasks.Task> desteklemek için <xref:System.Threading.Tasks.Task.Start%2A> sınıf bir yöntem ortaya çıkarır. Genel <xref:System.Threading.Tasks.Task> oluşturucular tarafından oluşturulan *görevler,* zamanlanmamış <xref:System.Threading.Tasks.TaskStatus.Created> durumda yaşam döngülerine başladıkları ve yalnızca bu örneklerde <xref:System.Threading.Tasks.Task.Start%2A> çağrıldığında zamanlandıkları için soğuk görevler olarak adlandırılır.

 Diğer tüm görevler yaşam döngülerine sıcak bir durumda başlar, bu da temsil ettikleri eşzamanlı işlemlerin zaten başlatıldığı ve görev <xref:System.Threading.Tasks.TaskStatus.Created?displayProperty=nameWithType>durumlarının . TAP yöntemlerinden döndürülen tüm görevler etkinleştirilmelidir. **Bir TAP yöntemi, görevin döndürülmesi için bir görevin oluşturucusu dahili olarak <xref:System.Threading.Tasks.Task.Start%2A> kullanıyorsa, TAP yöntemini iade etmeden önce <xref:System.Threading.Tasks.Task> nesneyi çağırmalıdır.** BIR TAP yönteminin tüketicileri, döndürülen görevin etkin olduğunu <xref:System.Threading.Tasks.Task.Start%2A> güvenli <xref:System.Threading.Tasks.Task> bir şekilde varsayabilir ve TAP yönteminden döndürülenleri çağırmaya çalışmamalıdır. Etkin <xref:System.Threading.Tasks.Task.Start%2A> bir görevin çağrılarak bir <xref:System.InvalidOperationException> özel durumla sonuçlanmaktadır.  
  
## <a name="cancellation-optional"></a>İptal (isteğe bağlı)  
 TAP kullanırken, iptal etmek hem zaman uyumsuz yöntem oluşturucuları hem de zaman uyumsuz yöntem tüketicileri için isteğe bağlıdır. Bir işlem iptale izin veriyorsa, iptal jetonu (örneğin)<xref:System.Threading.CancellationToken> kabul eden eşzamanlı yöntemin aşırı yüklenmesini ortaya çıkarır. Kural olarak, parametre `cancellationToken`.  
  
 [!code-csharp[Conceptual.TAP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#1)]
 [!code-vb[Conceptual.TAP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#1)]  
  
 Zaman uyumsuz işlem iptal istekleri için bu belirteci izler. Eğer iptal isteği alırsa, bu isteği dikkate alarak işlemi iptal etmeyi seçebilir. İptal isteği, çalışmanın zamanından önce sona erdirildiğine neden olursa, TAP yöntemi <xref:System.Threading.Tasks.TaskStatus.Canceled> eyalette sona eren bir görevi döndürür; kullanılabilir bir sonuç yoktur ve özel bir durum atılmaz.  Durum, <xref:System.Threading.Tasks.TaskStatus.Canceled> <xref:System.Threading.Tasks.TaskStatus.Faulted> <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> bir görev için son (tamamlanmış) durum olarak kabul edilir. Bu nedenle, bir görev <xref:System.Threading.Tasks.TaskStatus.Canceled> durumdaysa, <xref:System.Threading.Tasks.Task.IsCompleted%2A> `true`özelliği döndürür. Bir görev <xref:System.Threading.Tasks.TaskStatus.Canceled> durumda tamamlandığında, devam seçeneğinin devamı devre dışı bırakmak için <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled> belirtilmedikçe, göreve kaydedilen devamlar zamanlanır veya yürütülür. Dil özelliklerini kullanarak iptal edilmiş bir görevi eş senkronize olarak bekleyen tüm <xref:System.OperationCanceledException> kodlar çalıştırmaya devam eder, ancak ondan türetilen bir veya özel durum alır. Gibi yöntemlerle görevde eşzamanlı olarak bekleyen <xref:System.Threading.Tasks.Task.Wait%2A> ve <xref:System.Threading.Tasks.Task.WaitAll%2A> ayrıca bir özel durum la çalışmaya devam eden kod.  
  
 Bir iptal belirteci, belirteci olarak adlandırılan TAP yönteminden önce iptal talebinde <xref:System.Threading.Tasks.TaskStatus.Canceled> bulunduysa, TAP yöntemi bir görevi döndürmelidir.  Ancak, eğer zaman uyumsuz işlem yürütülüyorken bir iptal istenirse, zaman uyumsuz işlem iptal isteğini kabul etmek zorunda değildir.  Döndürülen görev, yalnızca <xref:System.Threading.Tasks.TaskStatus.Canceled> iptal isteği sonucunda işlem sona erdiğinde eyalette sona ermelidir. İptal istenirse, ancak bir sonuç veya özel durum hala <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> üretilirse, görev veya <xref:System.Threading.Tasks.TaskStatus.Faulted> durum sona ermelidir.

 Her şeyden önce iptal edilme yeteneğini ortaya çıkarmak isteyen eşzamanlı yöntemler için, iptal jetonu kabul etmeyen bir aşırı yükleme sağlamanız gerekmez. İptal edilemeyen yöntemler için iptal belirteci kabul eden bir aşırı yükleme sağlamayın; bu çağırana hedef yöntemin iptal edilip edilemez olduğunu belirtmeye yardımcı olur.  İptal isteğinde olmayan tüketici kodu, a <xref:System.Threading.CancellationToken> kabul eden <xref:System.Threading.CancellationToken.None%2A> ve bağımsız değişken değeri sağlayan bir yöntem arayabilir. <xref:System.Threading.CancellationToken.None%2A>işlevsel olarak varsayılana <xref:System.Threading.CancellationToken>eşdeğerdir.  
  
## <a name="progress-reporting-optional"></a>İlerleme raporlaması (isteğe bağlı)  
 Bazı zaman uyumsuz işlemler ilerleme bildirimlerinden faydalanır; bunlar genel olarak kullanıcı arayüzünü zaman uyumsuz işlemin ilerlemesi ile ilgili bilgiyle güncelleştirmekte kullanılır.

 TAP'de ilerleme, genellikle <xref:System.IProgress%601> adı verilen `progress`bir parametre olarak asynchronous yöntemine geçirilen bir arabirim aracılığıyla işlenir.  Zaman uyumsuz yöntem çağırıldığında ilerleme arabirimini sağlamak yanlış kullanım nedeniyle ortaya çıkan yarış durumlarını engellemeye yardımcı olur (yanlış kayıt olan olay işleyicilerinin işlem başladıktan sonra güncellemeleri kaçırabilmesi).  Daha da önemlisi, ilerleme arabirimi ilerlemenin tüketici kodunda belirlendiği üzere farklı uygulamalarını destekleyebilir.  Örneğin, tüketici kod yalnızca en son ilerleme güncellemesini isteyebilir, ya da tüm güncellemeleri arabelleğe koyabilir, ya da her güncelleme için bir eylem çağırabilir, ya da çağrının belirli bir iş parçacığına yönlendirilip yönlendirilmediğini denetlemek isteyebilir. Bütün bu seçenekler belirli tüketicinin ihtiyaçlarına göre arabirimin farklı uygulamalarını kullanarak elde edilebilir.  İptalde olduğu gibi, TAP <xref:System.IProgress%601> uygulamaları yalnızca API ilerleme bildirimlerini destekliyorsa bir parametre sağlamalıdır.

 Örneğin, bu `ReadAsync` makalede daha önce tartışılan yöntem, şimdiye kadar okunan bayt sayısı şeklinde ara ilerlemeyi bildirebiliyorsa, ilerleme geri araması bir <xref:System.IProgress%601> arabirim olabilir:  
  
 [!code-csharp[Conceptual.TAP#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#2)]
 [!code-vb[Conceptual.TAP#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#2)]  
  
 Bir `FindFilesAsync` yöntem belirli bir arama deseni karşılayan tüm dosyaların listesini döndürürse, ilerleme geri araması tamamlanan çalışma yüzdesinin yanı sıra geçerli kısmi sonuç kümesinin bir tahminini sağlayabilir.  Bunu ya bir kayıt düzeni ile yapabilir:  
  
 [!code-csharp[Conceptual.TAP#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#3)]
 [!code-vb[Conceptual.TAP#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#3)]  
  
 ya da API'ye özel bir veri türü ile yapabilir:  
  
 [!code-csharp[Conceptual.TAP#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap/cs/examples1.cs#4)]
 [!code-vb[Conceptual.TAP#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap/vb/examples1.vb#4)]  
  
 İkinci durumda, özel veri türü genellikle suffixed olduğunu `ProgressInfo`.  
  
 TAP uygulamaları bir `progress` parametre kabul eden aşırı yüklemeler sağlıyorsa, bağımsız değişkenin (bu durumda hiçbir ilerleme bildirilmeyeceğini) bağımsız değişkene `null`izin vermeleri gerekir. TAP uygulamaları, ilerlemeyi <xref:System.Progress%601> nesneye eşzamanlı olarak bildirmelidir, bu da asenkron yöntemin ilerlemeyi hızlı bir şekilde sağlamasına olanak sağlamalı ve ilerlemenin tüketicisinin bilgileri en iyi şekilde nasıl ve nerede işleyeceğini belirlemesine olanak tanır. Örneğin, ilerleme örneği geri aramaları yönlendirmeyi ve yakalanan bir eşitleme bağlamında olay çağırmayı seçebilir.  
  
## <a name="iprogresst-implementations"></a>IProgress\<T> uygulamaları  
 .NET Framework 4.5 tek <xref:System.IProgress%601> bir <xref:System.Progress%601>uygulama sağlar: . Sınıf <xref:System.Progress%601> aşağıdaki gibi bildirilir:  
  
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
  
 Eş zamanlı <xref:System.Progress%601> işlem <xref:System.Progress%601.ProgressChanged> her ilerleme güncelleştirmesi bildirdiğinde ortaya çıkan bir olayı ortaya çıkarır. Olay, <xref:System.Progress%601.ProgressChanged> örnek anında <xref:System.Threading.SynchronizationContext> yakalandığında yakalanan <xref:System.Progress%601> nesne üzerinde yükseltilir. Eğer hiçbir eşitleme bağlamı kullanılabilir değilse, iş parçacığı havuzunu hedefleyen bir varsayılan bağlam kullanılır. İşleyiciler bu olay ile kayıtlı olabilir. Tek bir işleyici de kolaylık <xref:System.Progress%601> sağlamak için oluşturucuya sağlanabilir ve <xref:System.Progress%601.ProgressChanged> olay için bir olay işleyicisi gibi olur. İlerleme güncelleştirmeleri zaman uyumsuz işlemi olay işleyicileri yürütülürken geciktirmemek için zaman uyumsuz olarak harekete geçirilir. Başka <xref:System.IProgress%601> bir uygulama farklı semantik uygulamak için seçebilirsiniz.  
  
## <a name="choosing-the-overloads-to-provide"></a>Sağlamak için aşırı yüklemeleri seçme  
 Bir TAP uygulaması hem <xref:System.Threading.Tasks.TaskFactory.CancellationToken%2A> isteğe <xref:System.IProgress%601> bağlı hem de isteğe bağlı parametreleri kullanıyorsa, en fazla dört aşırı yükleme gerektirebilir:  
  
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
  
 İki eksik ara birleşimi telafi etmek için, <xref:System.Threading.CancellationToken.None%2A> geliştiriciler <xref:System.Threading.CancellationToken> parametre ve `null` `progress` parametre için `cancellationToken` varsayılan geçiş yapabilir.  
  
 Eğer TAP yönteminin her kullanımının iptal veya ilerleme desteklemesini istiyorsanız, ilgili parametreyi kabul etmeyen aşırı yüklemeleri çıkarabilirsiniz.  
  
 İptal veya ilerlemeyi isteğe bağlı hale getirmek için birden fazla aşırı yükleme yi ortaya çıkarmaya karar <xref:System.Threading.CancellationToken.None%2A> verirseniz, iptal veya ilerlemeyi desteklemeyen aşırı yükler, iptal için geçmiş `null` gibi veya bunları destekleyen aşırı yüke ilerleme için geçmiş gibi kullanılmalıdır.  
  
## <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Asynchronous Programlama Desenleri](../../../docs/standard/asynchronous-programming-patterns/index.md)|Zaman uyumsuz işlemler gerçekleştirmek için üç desen tanıtır: Görev-tabanlı Zaman Uyumsuz Desen (TAP), Zaman Uyumsuz Programlama Modeli (APM) ve Olay-tabanlı Uyumsuz Desen (EAP).|  
|[Görev Tabanlı Zaman Uyumsuz Deseni Uygulama](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)|Görev-tabanlı Zaman Uyumsuz Desen (TAP) uygulamak için üç yol açıklar: Visual Studio içindeki C# ve Visual Basic derleyicilerini kullanarak, el yöntemi ile, veya derleyici ve el yönteminin bir kombinasyonu ile.|  
|[Görev Tabanlı Zaman Uyumsuz Desen Kullanma](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)|Engellemeden beklemeyi görevler ve geri aramalar kullanarak nasıl kullanacağınızı açıklar.|  
|[Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)|Zaman Uyumsuz Programlama Modeli (APM) ve Olay-tabanlı Zaman Uyumsuz Model (EAP) uygulamak için Görev-tabanlı Zaman Uyumsuz Model'in nasıl kullanılacağını açıklar.|
