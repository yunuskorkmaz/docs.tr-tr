---
title: Devamlılık Görevlerini Kullanarak Görevleri Birbirine Bağlama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, continuations
ms.assetid: 0b45e9a2-de28-46ce-8212-1817280ed42d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 308b834a133798104dcc47a16f8adc068ed937ec
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44188351"
---
# <a name="chaining-tasks-by-using-continuation-tasks"></a>Devamlılık Görevlerini Kullanarak Görevleri Birbirine Bağlama
Zaman uyumsuz programlama, ikinci bir işlem başlatmak ve ona veri aktarmak için tamamlandığında, bir zaman uyumsuz işlem için çok yaygın. Geleneksel olarak, bu geri arama yöntemleri kullanılarak yapılmıştır. Görev paralel Kitaplığı'nda aynı işlevler tarafından sağlanan *devamlılık görevleri*. Devamlılık görevi (sadece devamlılık olarak da bilinir) olarak da bilinen başka bir görev tarafından çağrılan zaman uyumsuz bir görevdir *öncül*, öncül görev tamamlandıktan sonra.  
  
 Devamlılıklar kullanımı oldukça kolaydır ancak yine de oldukça güçlü ve esnektir. Örneğin, şunları yapabilirsiniz:  
  
-   Veri öncülden devama geçirin.  
  
-   Altında devamlılığın çağrılacağı ya çağrılmayacağı kesin koşulları belirtin.  
  
-   Devamlılık, başlamadan önce ya da işbirliği ile çalışırken iptal edin.  
  
-   Devamlılığın nasıl zamanlanması gerektiği hakkında ipuçları sağlayın.  
  
-   Aynı öncülden gelen birden çok devamlılığını çağırır.  
  
-   Tümü veya herhangi birini Öncüllerin tamamlandığında bir devamlılığı çağırır.  
  
-   Birbiri ardına herhangi bir rastgele uzunluktaki zincir devamlılıkları.  
  
-   Öncülün attığı özel durumları işlemek için devamlılığı kullanın.  
  
## <a name="about-continuations"></a>Devamlılıklar hakkında  
 Oluşturulan bir görev devamıdır <xref:System.Threading.Tasks.TaskStatus.WaitingForActivation> durumu. Kendi öncül görevi veya görevler tamamlandığında otomatik olarak etkinleştirilir. Çağırma <xref:System.Threading.Tasks.Task.Start%2A?displayProperty=nameWithType> kullanıcı kodunda bir devamlılık üzerinde oluşturur bir <xref:System.InvalidOperationException?displayProperty=nameWithType> özel durum.  
  
 Devamlılık, kendisi olduğu bir <xref:System.Threading.Tasks.Task> ve üzerinde başlatıldığında iş parçacığını engellemez. Çağrı <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> devamlılık görevi bitene kadar engellemek için yöntemi.  
  
## <a name="creating-a-continuation-for-a-single-antecedent"></a>Bir devamlılık için tek bir öncül görev oluşturma  
 Çağırarak kendi öncül görevi tamamlandığında yürüten bir devam oluşturmak <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> yöntemi. Aşağıdaki örnek, temel deseni gösterir (Anlaşılsın diye, özel durum işleme atlanmıştır). Öncül görev yürütülmeden `taskA`, döndüren bir <xref:System.DayOfWeek> haftanın geçerli günü adını gösteren nesne. Öncül görev tamamlandığında devamlılık görevi `continuation`, öncül geçirilir ve sonucunu içeren bir dize görüntüler.  
  
 [!code-csharp[TPL_Continuations#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/simple1.cs#1)]
 [!code-vb[TPL_Continuations#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/simple1.vb#1)]  
  
## <a name="creating-a-continuation-for-multiple-antecedents"></a>Bir devamlılık için birden çok öncülün oluşturma  
 Ayrıca, herhangi bir görev grubu biri veya tümü tamamlandığında çalışacak bir devamlılık oluşturabilirsiniz. Öncül tüm görevler tamamlandığında devamlılık yürütmek için statik çağırın (`Shared` Visual Basic'te) <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> yöntemi veya örnek <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> yöntemi. Öncül görevlerden herhangi birini tamamlandığında devamlılık yürütmek için statik çağırın (`Shared` Visual Basic'te) <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> yöntemi veya örnek <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> yöntemi.  
  
 Çağrılar Not <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> aşırı çağıran iş parçacığını engelleme yapmadığından.  Ancak, genellikle arama dışındaki tüm <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WhenAll%28System.Threading.Tasks.Task%5B%5D%29?displayProperty=nameWithType> döndürülen almak için yöntemler <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliği çağıran iş parçacığını engeller.  
  
 Aşağıdaki örnek çağrıları <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> on kendi öncül görevi sonuçlarını gösteren bir devamlılık görevi oluşturmak için yöntemi. Her bir öncül görev, bir ila on aralıkları bir dizin değeri squares. Öncüllerin başarıyla tamamlanırsa (kendi <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> özelliği <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>), <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> devamlılığın özelliği olan bir dizi <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> her bir öncül görev tarafından döndürülen değer. Örneğin, onları bir ve on arasındaki tüm sayılar için kareler toplamı hesaplamak için ekler.  
  
 [!code-csharp[TPL_Continuations#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/whenall1.cs#5)]
 [!code-vb[TPL_Continuations#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/whenall1.vb#5)]  
  
## <a name="continuation-options"></a>Devamlılık seçenekleri  
 Bir tek devamlılık oluştururken kullanabileceğiniz bir <xref:System.Threading.Tasks.Task.ContinueWith%2A> alan aşırı yüklemesini bir <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> devamlılık başlatan koşulları belirtmek için numaralandırma değeri. Örneğin, devamlılığın yalnızca öncül görev başarıyla tamamlanırsa veya yalnızca bir hatalı durumunda tamamlanırsa çalıştırmak üzere olduğunu belirtebilirsiniz. Öncül sürekliliği çağırmaya hazır olduğunda, koşul true değilse, süreklilik doğrudan geçiş <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> belirtin ve sonra işlemi başlatılamıyor.  
  
 Bir dizi aşırı yüklemeleri gibi çoklu görev devamlılığı yöntem <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> yöntemi de dahil bir <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> parametresi. Yalnızca bir alt tüm <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> numaralandırma üyelerini geçerli, ancak. Belirtebileceğiniz <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> ortaklarınıza olmayan değerleri <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=nameWithType> numaralandırma gibi <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskContinuationOptions.LongRunning?displayProperty=nameWithType>, ve <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness?displayProperty=nameWithType>. Herhangi bir belirtirseniz `NotOn` veya `OnlyOn` seçenekler çoklu görev sürekliliği ile bir <xref:System.ArgumentOutOfRangeException> çalışma zamanında özel durum oluşturulur.  
  
 Görev devamlılık seçenekleri hakkında daha fazla bilgi için bkz. <xref:System.Threading.Tasks.TaskContinuationOptions> konu.  
  
## <a name="passing-data-to-a-continuation"></a>Devamlılık veri geçirme  
 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> Yöntemi bağımsız değişken olarak devamlılığın kullanıcı temsilcisine öncül bir başvuru geçirir. Öncül bir <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> nesne yanı sıra, görev çalıştırılmadan tamamlanana kadar devamlılığın erişebilir <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> görevi özelliğidir.  
  
 <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> Özelliği, görev tamamlanıncaya kadar engeller. Görev iptal edildi veya hatalı, ancak erişmeye çalışan <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği oluşturur bir <xref:System.AggregateException> özel durum. Kullanarak bu sorunu önleyebilirsiniz <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnRanToCompletion> seçeneği, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[TPL_Continuations#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result1.cs#2)]
 [!code-vb[TPL_Continuations#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result1.vb#2)]  
  
 Devamlılık, öncül görev için işlemin başarıyla tamamlanmasından çalıştırmadıysanız bile istiyorsanız, özel duruma karşı korumanız gerekir. Test etmek için bir yaklaşım ise <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> öncül ve yalnızca özellik erişme girişiminde <xref:System.Threading.Tasks.Task%601.Result%2A> durum değilse, özelliği <xref:System.Threading.Tasks.TaskStatus.Faulted> veya <xref:System.Threading.Tasks.TaskStatus.Canceled>. Ayrıca inceleyebilirsiniz <xref:System.Threading.Tasks.Task.Exception%2A> öncül özelliğidir. Daha fazla bilgi için [özel durum işleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md). Aşağıdaki örnek önceki örneğe erişim öncülün değiştirir <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> durumunun ise özellik <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result2.cs#7)]
 [!code-vb[TPL_Continuations#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result2.vb#7)]  
  
## <a name="canceling-a-continuation"></a>Devamlılığı iptal etme  
 <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> Özelliği, bir devamlılık <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> aşağıdaki durumlarda:  
  
-   Atar bir <xref:System.OperationCanceledException> bir iptal isteğine yanıt olarak özel durum. Özel durum devamlılığa geçirilen aynı belirteci içeriyorsa gibi herhangi bir görev ile ortak iptali alındı bildirimi kabul edilir.  
  
-   Devamlılığın geçirilen bir <xref:System.Threading.CancellationToken?displayProperty=nameWithType> olan <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği `true`. Bu durumda süreklilik başlatılmaz ve geçer <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> durumu.  
  
-   Koşul belirlediği için devamlılık hiç çalışır, <xref:System.Threading.Tasks.TaskContinuationOptions> bağımsız değişken karşılanmadı. Örneğin, bir öncül görev içine aşması durumunda bir <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> durumuna geçildi devamlılığını <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnFaulted?displayProperty=nameWithType> seçenek çalışmaz, ancak hizmete geçiş <xref:System.Threading.Tasks.TaskStatus.Canceled> durumu.  
  
 Bir görev ve devamlılığını aynı mantık işleminin iki parçasını temsil ediyorsa aynı iptal belirtecini her iki görevleri için aşağıdaki örnekte gösterildiği gibi geçirebilirsiniz. Devamlılık için geçen 33 bölünebilir tamsayılar listesini oluşturan bir öncülü oluşur. Devamlılığın sırayla listesini görüntüler. Düzenli olarak öncül hem devamlılık için rastgele aralıklarda duraklatın. Ayrıca, bir <xref:System.Threading.Timer?displayProperty=nameWithType> yürütmek için kullanılan nesne `Elapsed` 5 saniyelik zaman aşımı aralığından sonra yöntemi. Bu çağrı <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> çağırmak o anda yürütülen görevin neden yöntemi <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A?displayProperty=nameWithType> yöntemi. Olmadığını <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> öncül veya devamlılığını yürüttüğünde yöntemi çağrıldığında rastgele oluşturulmuş duraklamaları süresine bağlıdır. Öncül iptal edildiyse, süreklilik başlatılmaz. Öncül iptal değil, belirteç sürekliliği iptal etmek için yine de kullanılabilir.  
  
 [!code-csharp[TPL_Continuations#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation1.cs#3)]
 [!code-vb[TPL_Continuations#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation1.vb#3)]  
  
 Belirterek bir iptal belirteci devamlılığın sağlamadan kendi öncül görevi iptal edilirse bir devamlılığın yürütülmesini engelleyebilirsiniz <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled?displayProperty=nameWithType> seçeneği devamlılığı oluşturduğunuzda. Basit bir örnek verilmiştir.  
  
 [!code-csharp[TPL_Continuations#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation2.cs#8)]
 [!code-vb[TPL_Continuations#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation2.vb#8)]  
  
 Devamlılık geçtikten sonra <xref:System.Threading.Tasks.TaskStatus.Canceled> durumuna bağlı olarak sonraki devamlılıkları etkileyebilir <xref:System.Threading.Tasks.TaskContinuationOptions> bu devamlılıklar için belirlenen.  
  
 Atılan devamlılıklar başlatılamaz.  
  
## <a name="continuations-and-child-tasks"></a>Alt görevler ve devamlılıklar  
 Devamlılık öncül çalışmaz ve eklenen alt görevlerin hepsi tamamlanmış. Devamlılığın tamamlamak, ayrılmış alt görevlerin tamamlanmasını beklemez. Ekli ve ayrılmış bir devamlılık oluşturan öncül bir görevden alt görevleri aşağıdaki iki örnek gösterilmektedir. Aşağıdaki örnekte, devamlılık, yalnızca tüm alt görevlerini tamamladıktan ve aynı her zaman çıktı örneği birden çok kez üretir çalıştırmadan sonra çalışır. Örnek çağırarak öncül başlatır Not <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> yöntemi olduğundan varsayılan <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> yöntemi oluşturur, varsayılan görev oluşturma seçeneği olan bir üst görev <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/attached1.cs#9)]
 [!code-vb[TPL_Continuations#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/attached1.vb#9)]  
  
 Ancak, alt görevlerin öncülden ayrılırsa, öncül görev sonlandırıldı, alt görevlerin durumunu bakılmaksızın hemen sonra devamlılığın çalıştırır. Sonuç olarak, aşağıdaki örnek, birden fazla çalıştırma, Görev Zamanlayıcısı'nı her bir alt görev işlenme bağlıdır değişken çıktı üretebilir.  
  
 [!code-csharp[TPL_Continuations#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/detached1.cs#10)]
 [!code-vb[TPL_Continuations#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/detached1.vb#10)]  
  
 Öncül görevin son durumu, iliştirilmiş alt görevlerin son durumuna bağlıdır. Ayrılmış alt öğelerin durumu üst öğeyi etkilemez. Daha fazla bilgi için [ekli ve ayrılmış alt görevler](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="associating-state-with-continuations"></a>Devamlılıklarla ilişkilendirme durumu  
 Görev devamlılığıyla rasgele durumu ilişkilendirebilirsiniz. <xref:System.Threading.Tasks.Task.ContinueWith%2A> Yöntem, aşırı yüklü sürümler sağlar her bir <xref:System.Object> birinin devamlılığın durumunu temsil eden değer. Kullanarak daha sonra bu durum nesnesine erişebilirsiniz <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> özelliği. Bu durum nesne `null` bir değer belirtmezseniz.  
  
 Devamlılık durumu, kullanan mevcut kodu dönüştürürken yararlıdır [zaman uyumsuz programlama modeli (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) TPL kullanmak için. APM, genellikle nesne durumunu sağladığınız **başlamak *** yöntemi* yöntemi ve durumunu kullanarak daha sonra erişmek <xref:System.IAsyncResult.AsyncState%2A?displayProperty=nameWithType> özelliği. Kullanarak <xref:System.Threading.Tasks.Task.ContinueWith%2A> yöntemi, bu durumu koruyabilirsiniz TPL kullanmak için APM kullanan kodu dönüştüreceğiniz zaman.  
  
 Devamlılık durumu da yararlı olabilir ile çalışırken <xref:System.Threading.Tasks.Task> Visual Studio hata ayıklayıcısı nesneleri. Örneğin, **Paralel Görevler** penceresinde **görev** sütunu her görevin durum nesnesinin dize gösterimini görüntüler. Hakkında daha fazla bilgi için **Paralel Görevler** penceresinde görmek [Using the Tasks Window](/visualstudio/debugger/using-the-tasks-window).  
  
 Aşağıdaki örnek, devamlılık durumunun nasıl kullanılacağını gösterir. Devamlılık görevleri zinciri oluşturur. Her görev geçerli saati sağlayan bir <xref:System.DateTime> nesnesi için `state` parametresinin <xref:System.Threading.Tasks.Task.ContinueWith%2A> yöntemi. Her <xref:System.DateTime> nesne devamlılık görevi oluşturulduğu zaman temsil eder. İkinci bir sonuç olarak her görevin ürettiği <xref:System.DateTime> başlangıçtan görevinin bittiği zamanı temsil eden nesne. Bu örnek, tüm görevler tamamlandıktan sonra oluşturma zamanını ve her devamlılık görevinin bittiği zamanı görüntüler.  
  
 [!code-csharp[TPL_ContinuationState#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuationstate/cs/continuationstate.cs#1)]
 [!code-vb[TPL_ContinuationState#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuationstate/vb/continuationstate.vb#1)]  
  
## <a name="handling-exceptions-thrown-from-continuations"></a>Devamlılıktan özel durum işleme  
 Önceki devamlılık ilişkisi, üst-alt ilişkisi değildir. Devamlılıklarla atılan özel durumlar öncüle yayılmaz. Bu nedenle, bunları başka herhangi bir görev, şu şekilde gerçekleştirilir gibi devamlılıklarla atılan özel durumları işler:  
  
-   Kullanabileceğiniz <xref:System.Threading.Tasks.Task.Wait%2A>, <xref:System.Threading.Tasks.Task.WaitAll%2A>, veya <xref:System.Threading.Tasks.Task.WaitAny%2A> yöntemi veya beklemek için genel çözümlemesiyle. Bir öncülü ve devamlılığını aynı bekleyebilirsiniz `try` deyimi, aşağıdaki örnekte gösterildiği gibi.  
  
     [!code-csharp[TPL_Continuations#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception1.cs#6)]
     [!code-vb[TPL_Continuations#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception1.vb#6)]  
  
-   Gözlemlemek için ikinci devamlılığı kullanın <xref:System.Threading.Tasks.Task.Exception%2A> ilk devamlılığın özelliği. Aşağıdaki örnekte, bir görev var olmayan dosyasından okumaya çalışır. Ardından devamlılık, öncül görev özel durum hakkındaki bilgileri görüntüler.  
  
     [!code-csharp[TPL_Continuations#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#4)]
     [!code-vb[TPL_Continuations#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#4)]  
  
     İle çalıştığından <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnFaulted?displayProperty=nameWithType> seçeneği, devamlılık yürütür yalnızca öncül görev bir özel durum oluşur ve bu nedenle, kabul edebilirsiniz öncülün <xref:System.Threading.Tasks.Task.Exception%2A> özelliği değil `null`. Devamlılık içinde öncül bir özel durum olup olmadığını yürütür, denetlenecek gerekir yoksa öncülün <xref:System.Threading.Tasks.Task.Exception%2A> özelliği değil `null` özel durumu işlemek üzere çalışmadan önce aşağıdaki kod parçası gösterir.  
  
     [!code-csharp[TPL_Continuations#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#11)]
     [!code-vb[TPL_Continuations#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#11)]  
  
     Daha fazla bilgi için [özel durum işleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
-   Devamlılığın kullanılarak oluşturulmuş bir eklenmiş alt görev ise <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType> seçeneği, ana çağıran iş parçacığı tarafından herhangi bir ekli alt içinde olduğu gibi özel durumlar aktarılacaktır. Daha fazla bilgi için [ekli ve ayrılmış alt görevler](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
