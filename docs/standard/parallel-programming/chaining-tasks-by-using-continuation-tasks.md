---
title: "Devamlılık Görevlerini Kullanarak Görevleri Birbirine Bağlama"
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
- tasks, continuations
ms.assetid: 0b45e9a2-de28-46ce-8212-1817280ed42d
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b8e21c338648d5925c8576f76dae3aae43a9ca0d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="chaining-tasks-by-using-continuation-tasks"></a>Devamlılık Görevlerini Kullanarak Görevleri Birbirine Bağlama
Zaman uyumsuz programlama, ikinci bir işlem çağırma ve veri iletmektir tamamlandığında, bir zaman uyumsuz işlemi çok yaygın bir sorundur. Geleneksel olarak, bu geri çağırma yöntemlerini kullanarak gerçekleştirilmedi. Görev paralel kitaplığı aynı işlevselliği tarafından sağlanan *devamlılık görevlerini*. (Yalnızca devamlılığı olarak da bilinir) bir devamlılık görevi olarak bilinen başka bir görev tarafından çağrılan bir zaman uyumsuz bir görevdir *antecedent*, antecedent sona erdiğinde.  
  
 Devamlılıklar görece kolaydır, ancak yine de çok güçlü ve esnektir. Örneğin, şunları yapabilirsiniz:  
  
-   Verileri antecedent devamlılık geçirir.  
  
-   Altında devamlılık çağrılan veya kaldırılacak çağrılamaz kesin koşulları belirtin.  
  
-   Başlamadan önce ya da işbirliği ile çalışır durumda bir devamlılık iptal edin.  
  
-   Devamlılık nasıl zamanlanmalıdır hakkında ipuçları sağlar.  
  
-   Aynı antecedent gelen birden çok devamlılıklar çağırır.  
  
-   Tüm veya herhangi birini birden çok antecedents tamamladığınızda, bir devamlılık çağırır.  
  
-   Devamlılıklar birbiri ardından herhangi bir rastgele uzunlukta zincir.  
  
-   Antecedent tarafından oluşturulan özel durumları işlemek için bir devamlılık kullanır.  
  
## <a name="about-continuations"></a>Devamlılıklar hakkında  
 Bir devamlılık oluşturulan bir görevdir <xref:System.Threading.Tasks.TaskStatus.WaitingForActivation> durumu. Kendi öncül görevi veya görevleri tamamladıktan sonra otomatik olarak etkinleştirilir. Çağırma <xref:System.Threading.Tasks.Task.Start%2A?displayProperty=nameWithType> devamlılık kullanıcı kodu oluşturduğunda bir <xref:System.InvalidOperationException?displayProperty=nameWithType> özel durum.  
  
 Bir devamlılık kendisini olan bir <xref:System.Threading.Tasks.Task> ve üzerinde başlatıldığında iş parçacığı engellemez. Çağrı <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> devamlılık görevi tamamlanana kadar engellemek için yöntem.  
  
## <a name="creating-a-continuation-for-a-single-antecedent"></a>Devamlılık tek antecedent için oluşturma  
 Kendi antecedent çağırarak tamamlandığında, yürüten bir devamlılık oluşturduğunuz <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> yöntemi. Aşağıdaki örnek, temel düzeni gösterir (daha anlaşılır olması için özel durum işleme atlanır). Öncül bir görev yürütülmeden `taskA`, döndüren bir <xref:System.DayOfWeek> haftanın geçerli adını gösteren nesne. Antecedent tamamlandığında devamlılık görevi `taskB`antecedent geçirilir ve sonucunu içeren bir dize görüntüler.  
  
 [!code-csharp[TPL_Continuations#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/simple1.cs#1)]
 [!code-vb[TPL_Continuations#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/simple1.vb#1)]  
  
## <a name="creating-a-continuation-for-multiple-antecedents"></a>Devamlılık birden çok antecedents için oluşturma  
 Herhangi bir grup görevlerin biri veya tümü tamamlandığında, çalışacak bir devamlılık de oluşturabilirsiniz. Tüm öncül görevleri tamamladıktan sonra bir devamlılık yürütmek için statik çağrı (`Shared` Visual Basic'te) <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> yöntemi veya örnek <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> yöntemi. Öncül görevlerden herhangi birini tamamlandı zaman bir devamlılık yürütmek için statik çağrı (`Shared` Visual Basic'te) <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> yöntemi veya örnek <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> yöntemi.  
  
 Çağrılar Not <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> aşırı çağıran iş parçacığı engelleme değil.  Ancak, genellikle arama dışındaki tüm <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WhenAll%28System.Threading.Tasks.Task%5B%5D%29?displayProperty=nameWithType> döndürülen almak için yöntemleri <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> çağıran iş parçacığı engelleme özelliği.  
  
 Aşağıdaki örnek çağrıları <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> on öncül görevlerinin sonuçlarını yansıtan bir devamlılık görevi oluşturmak için yöntemi. Her öncül görev bir on ile aralıkları bir dizin değeri karesini alır. Antecedents başarılı şekilde gerçekleştirirseniz (kendi <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> özelliği <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>), <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> devamlılık özelliği olan bir dizi <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> her antecedent tarafından döndürülen değer. Örnek bir ile on arasındaki tüm numaraları için kareler toplamı işlem eklenmektedir.  
  
 [!code-csharp[TPL_Continuations#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/whenall1.cs#5)]
 [!code-vb[TPL_Continuations#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/whenall1.vb#5)]  
  
## <a name="continuation-options"></a>Devamlılık seçenekleri  
 Tek görev devamlılığı oluştururken kullanabileceğiniz bir <xref:System.Threading.Tasks.Task.ContinueWith%2A> alan aşırı bir <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> devamlılık başlatan koşulları belirtmek için numaralandırma değeri. Örneğin, devamlılık yalnızca antecedent başarıyla tamamlarsa ya da yalnızca hatalı bir durumda tamamlarsa çalıştırmak üzere olduğunu belirtebilirsiniz. Devamlılık antecedent devamlılık çağırmak hazır olduğunda koşul doğru değilse, doğrudan geçiş <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> belirtin ve sonra başlatılamıyor.  
  
 Aşırı gibi birden çok görev devamlılığı yöntemleri sayısı <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> yöntemi de dahil bir <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> parametresi. Yalnızca bir alt tüm <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> numaralandırma üyeleri geçerlidir, ancak. Belirleyebileceğiniz <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> ortaklarınıza sahip değerlerini <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=nameWithType> numaralandırma, gibi <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskContinuationOptions.LongRunning?displayProperty=nameWithType>, ve <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness?displayProperty=nameWithType>. Herhangi bir belirtirseniz, `NotOn` veya `OnlyOn` çok görev devamlılığı seçeneklerle bir <xref:System.ArgumentOutOfRangeException> özel çalışma zamanında durum.  
  
 Görev devamlılığı seçenekleri hakkında daha fazla bilgi için bkz: <xref:System.Threading.Tasks.TaskContinuationOptions> konu.  
  
## <a name="passing-data-to-a-continuation"></a>Bir devamlılık veri geçirme  
 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> Yöntemi için bağımsız değişken olarak devamlılık kullanıcı temsilci antecedent başvuru geçirir. Antecedent ise bir <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> nesne ve görev çalıştırılmadan tamamlanıp tamamlanmadığını kadar devamlılık erişebilirsiniz sonra <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> görev özelliği.  
  
 <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> Özelliği, görevin tamamlanmasını engeller. Görev iptal ya da hatalı, ancak erişmeye <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği atar bir <xref:System.AggregateException> özel durum. Kullanarak bu sorunu önlemek <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnRanToCompletion> , aşağıdaki örnekte gösterildiği gibi seçeneği.  
  
 [!code-csharp[TPL_Continuations#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result1.cs#2)]
 [!code-vb[TPL_Continuations#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result1.vb#2)]  
  
 Antecedent başarılı tamamlanıncaya kadar çalıştırmadıysanız bile çalışmaya devam istiyorsanız, özel durum karşı koruma gerekir. Bir yaklaşım ise test etmek için <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> öncül ve yalnızca özelliği denemek erişmek <xref:System.Threading.Tasks.Task%601.Result%2A> durum değilse özelliği <xref:System.Threading.Tasks.TaskStatus.Faulted> veya <xref:System.Threading.Tasks.TaskStatus.Canceled>. Ayrıca inceleyebilirsiniz <xref:System.Threading.Tasks.Task.Exception%2A> nın özelliği. Daha fazla bilgi için bkz: [özel durum işleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md). Aşağıdaki örnekte erişim antecedent'ın önceki örneği değiştiren <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> yalnızca durumunu ise özelliği <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result2.cs#7)]
 [!code-vb[TPL_Continuations#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result2.vb#7)]  
  
## <a name="canceling-a-continuation"></a>Bir devamlılık iptal etme  
 <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> Bir devamlılık özelliği ayarlanmış <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> aşağıdaki durumlarda:  
  
-   Bunu oluşturur bir <xref:System.OperationCanceledException> iptal isteğine yanıt olarak özel durum. Özel durum devamlılık için geçirilen aynı belirteci içeriyorsa gibi herhangi bir görev ile işbirlikçi iptal onay işlem görür.  
  
-   Devamlılık geçirilen bir <xref:System.Threading.CancellationToken?displayProperty=nameWithType> , <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği `true`. Bu durumda, devamlılık başlatılmaz ve için geçiş <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> durumu.  
  
-   Tarafından belirlenen koşul nedeniyle devamlılık hiçbir zaman çalışır, <xref:System.Threading.Tasks.TaskContinuationOptions> bağımsız değişkeni karşılanmadı. Örneğin, bir antecedent girmeyeceğini bir <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> durumunda, geçirilen devamlılığını <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnFaulted?displayProperty=nameWithType> seçeneği çalışmaz ancak için geçirecektir <xref:System.Threading.Tasks.TaskStatus.Canceled> durumu.  
  
 Bir görevi ve devamlılığını aynı mantıksal işlemi iki bölümden temsil ediyorsa, hem görevler, aşağıdaki örnekte gösterildiği gibi aynı iptal belirtecini geçirebilirsiniz. Devamlılık geçirir 33 bölünebilir tamsayılar listesini oluşturan bir antecedent oluşur. Devamlılık sırayla listesini görüntüler. Düzenli olarak antecedent ve devamlılık için rastgele aralıkları duraklatın. Ayrıca, bir <xref:System.Threading.Timer?displayProperty=nameWithType> yürütmek için kullanılan nesne `Elapsed` beş saniyelik zaman aşımı aralığından sonra yöntemi. Bu çağrı <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> çağırmak şu anda yürütülen görev neden yöntemi <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A?displayProperty=nameWithType> yöntemi. Olup olmadığını <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> antecedent veya devamlılığını yürütülürken zaman yöntemi çağrıldığında rastgele oluşturulmuş duraklatma süresi üzerinde bağlıdır. Antecedent iptal ederseniz, devamlılık başlatılmaz. Antecedent iptal değil, belirteç hala devamlılık iptal etmek için kullanılabilir.  
  
 [!code-csharp[TPL_Continuations#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation1.cs#3)]
 [!code-vb[TPL_Continuations#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation1.vb#3)]  
  
 Belirterek bir iptal belirteci devamlılık girmeden kendi antecedent iptal edilirse yürütme gelen bir devamlılık engelleyebilir <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled?displayProperty=nameWithType> seçeneği devamlılık oluşturduğunuzda. Basit bir örnek verilmiştir.  
  
 [!code-csharp[TPL_Continuations#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation2.cs#8)]
 [!code-vb[TPL_Continuations#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation2.vb#8)]  
  
 İçine bir devamlılık göründükten sonra <xref:System.Threading.Tasks.TaskStatus.Canceled> durumunda, izleyin, bağlı olarak devamlılıklar etkileyebilir <xref:System.Threading.Tasks.TaskContinuationOptions> bu devamlılıklar için belirtildi.  
  
 Elden devamlılıklar başlatılmaz.  
  
## <a name="continuations-and-child-tasks"></a>Devamlılıklar ve alt görevler  
 Bir devamlılık antecedent kadar çalışmaz ve tüm bağlı alt görevleri tamamladınız. Devamlılık ayrılmış alt görevin bitmesini beklemez. Aşağıdaki iki örnek bağlı ve ayrılmış bir devamlılık oluşturan bir antecedent alt görevler gösterilmektedir. Aşağıdaki örnekte, yalnızca tüm alt görevleri tamamladıktan ve aynı her çıktı örneği birden çok kez üretir çalıştırmadan sonra devamlılık çalışır. Örnek çağırarak antecedent başlatır Not <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> yöntemi, bu yana varsayılan <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> yöntemi oluşturur, varsayılan görev oluşturma seçeneği üst göreve <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/attached1.cs#9)]
 [!code-vb[TPL_Continuations#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/attached1.vb#9)]  
  
 Ancak, alt görevler antecedent ayrılmış, devamlılık antecedent sonlandırıldı, alt görevler durumuna bakılmaksızın hemen sonra çalışır. Sonuç olarak, aşağıdaki örnekte birden çok çalıştırılan Görev Zamanlayıcısı'nı her alt görevin nasıl işleneceğini bağlıdır değişken çıkışı oluşturabilir.  
  
 [!code-csharp[TPL_Continuations#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/detached1.cs#10)]
 [!code-vb[TPL_Continuations#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/detached1.vb#10)]  
  
 Son durum öncül görevin tüm ekli alt görevler son durumlarına göre bağlıdır. Ayrılan alt görevler durumunu üst etkilemez. Daha fazla bilgi için bkz: [eklenen ve ayrılan alt görevler](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="associating-state-with-continuations"></a>Durum devamlılıklar ile ilişkilendirme  
 Rastgele durumu görev devamlılığı ile ilişkilendirebilirsiniz. <xref:System.Threading.Tasks.Task.ContinueWith%2A> Yöntemi sağlar aşırı yüklenmiş sürümleri, her Al bir <xref:System.Object> devamlılık durumunu gösteren bir değer. Bu durum nesnesi kullanarak daha sonra erişebileceğiniz <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> özelliği. Bu durum nesne `null` bir değer belirtmezseniz.  
  
 Devamlılık durumunda yararlı kullanan var olan kodu dönüştürürken [zaman uyumsuz programlama modeli (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) TPL kullanılacak. APM, genellikle nesne durumda sağladığınız **başlamak *** yöntemi* yöntemi ve kullanarak durum sonraki erişim <xref:System.IAsyncResult.AsyncState%2A?displayProperty=nameWithType> özelliği. Kullanarak <xref:System.Threading.Tasks.Task.ContinueWith%2A> yöntemi, korumak bu durum TPL kullanmak için APM kullanan kodu dönüştürürken.  
  
 Devamlılık durumu da yararlı olabilir ile çalışırken <xref:System.Threading.Tasks.Task> nesnelerini [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] hata ayıklayıcı. Örneğin, **Paralel Görevler** penceresinde **görev** sütunu her görev için durum nesnenin dize gösterimini görüntüler. Hakkında daha fazla bilgi için **Paralel Görevler** penceresinde bkz [görevleri penceresini kullanma](/visualstudio/debugger/using-the-tasks-window).  
  
 Aşağıdaki örnek devamlılık durumu kullanmayı gösterir. Devamlılık görevlerini zinciri oluşturur. Her görev geçerli zaman tanır bir <xref:System.DateTime> nesnesi için `state` parametresinin <xref:System.Threading.Tasks.Task.ContinueWith%2A> yöntemi. Her <xref:System.DateTime> nesnesi devamlılık görevi oluşturulur süreyi temsil eder. İkinci bir sonuç olarak her görev üreten <xref:System.DateTime> görev tamamlandıktan zamanı temsil eden nesne. Tüm görevleri tamamladıktan sonra bu örnek oluşturma saat ve her hangi bir devamlılık görev tamamlandığında saati görüntüler.  
  
 [!code-csharp[TPL_ContinuationState#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuationstate/cs/continuationstate.cs#1)]
 [!code-vb[TPL_ContinuationState#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuationstate/vb/continuationstate.vb#1)]  
  
## <a name="handling-exceptions-thrown-from-continuations"></a>Devamlılıklar oluşturulan özel durumları işleme  
 Antecedent devamlılık ilişki üst-alt ilişkisinde değil. Devamlılıklar tarafından oluşturulan özel durumları antecedent yayılmaz. Bu nedenle, bunları başka herhangi bir görev, aşağıdaki gibi gerçekleştirilir gibi devamlılıklar tarafından oluşturulan özel durumları işler:  
  
-   Kullanabileceğiniz <xref:System.Threading.Tasks.Task.Wait%2A>, <xref:System.Threading.Tasks.Task.WaitAll%2A>, veya <xref:System.Threading.Tasks.Task.WaitAny%2A> yöntemi veya üzerinde devamlılık beklenecek genel karşılığı,. Bir antecedent ve kendi devamlılıklar aynı bekleyebilirsiniz `try` aşağıdaki örnekte gösterildiği gibi deyimi.  
  
     [!code-csharp[TPL_Continuations#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception1.cs#6)]
     [!code-vb[TPL_Continuations#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception1.vb#6)]  
  
-   İkinci bir devamlılık izlemek için kullanabileceğiniz <xref:System.Threading.Tasks.Task.Exception%2A> ilk devamlılık özelliği. Aşağıdaki örnekte, bir görev bir mevcut olmayan dosyasını okumaya çalışır. Devamlılık sonra öncül görev özel durum bilgilerini görüntüler.  
  
     [!code-csharp[TPL_Continuations#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#4)]
     [!code-vb[TPL_Continuations#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#4)]  
  
     İle çalıştırıldığından <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnFaulted?displayProperty=nameWithType> seçeneğini devamlılık yürütür yalnızca antecedent içinde bir özel durum oluşur ve bu nedenle bu, kabul edilebilir antecedent's <xref:System.Threading.Tasks.Task.Exception%2A> özelliği `null`. Antecedent içinde bir özel durum olup olmadığına bakılmaksızın devamlılık yürütülürse denetlemek olurdu olup olmadığını antecedent's <xref:System.Threading.Tasks.Task.Exception%2A> özelliği `null` özel durumu işlemek üzere çalışmadan önce aşağıdaki kod parçası gösterir.  
  
     [!code-csharp[TPL_Continuations#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#11)]
     [!code-vb[TPL_Continuations#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#11)]  
  
     Daha fazla bilgi için bkz: [özel durum işleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md) ve [NIB: nasıl yapılır: görevler tarafından özel durum işleme](http://msdn.microsoft.com/library/d6c47ec8-9de9-4880-beb3-ff19ae51565d).  
  
-   Devamlılık kullanılarak oluşturulmuş bir ekli alt görev olup olmadığını <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType> seçeneği, üst çağıran iş parçacığı tarafından eklenen herhangi bir alt durumda olduğu gibi özel durumlar yayılır. Daha fazla bilgi için bkz: [eklenen ve ayrılan alt görevler](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
