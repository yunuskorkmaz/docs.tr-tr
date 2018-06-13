---
title: Yönetilen İş Parçacığı Havuzu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- thread pooling [.NET Framework]
- thread pools [.NET Framework]
- threading [.NET Framework], thread pool
- threading [.NET Framework], pooling
ms.assetid: 2be05b06-a42e-4c9d-a739-96c21d673927
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3894229ff5561e50d42a36f576a89ee7bf01c067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592424"
---
# <a name="the-managed-thread-pool"></a>Yönetilen İş Parçacığı Havuzu
<xref:System.Threading.ThreadPool> Sınıfı yerine uygulama görevlerde yoğunlaşabilirsiniz yönetim iş parçacığı sağlayan sistem tarafından yönetilen çalışan iş parçacığı havuzu ile uygulamanızı sağlar. Arka plan işlemleri gerektiren kısa görevleri varsa, yönetilen iş parçacığı havuzu birden çok iş parçacığı yararlanmak için kolay bir yoludur. Örneğin, başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] oluşturabileceğiniz <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> iş parçacığı havuzu iş parçacıkları üzerinden zaman uyumsuz görevleri nesneleri.  
  
> [!NOTE]
>  İle başlayarak [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)], iş parçacığı havuzu verimini önemli ölçüde performans sorunlarını önceki sürümlerinde olarak tanımlanmış olan üç anahtar alanlarda geliştirilmiş [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]: iş parçacığı havuzu iş parçacıkları göndermeyi ve g/ç göndermeyi queuing görevleri Tamamlanma iş parçacığı sayısı. Bu işlevselliği kullanmak için uygulamanızı hedeflemelidir [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] veya sonraki bir sürümü.  
  
 Ayrıca kullanıcı arabirimiyle etkileşim arka plan görevleri için .NET Framework sürüm 2.0 sağlar <xref:System.ComponentModel.BackgroundWorker> sınıfı kullanıcı arabirimi iş parçacığı üzerinde oluşturulan olaylara kullanarak iletişim kurar.  
  
 .NET Framework zaman uyumsuz g/ç tamamlama dahil olmak üzere birçok amaç için iş parçacığı havuzu iş parçacıkları kullanır, kayıtlı Zamanlayıcı geri çağırmalar işlemleri bekleyin, zaman uyumsuz yöntem çağrıları, kullanma ve <xref:System.Net> yuva bağlantıları.  
  
## <a name="when-not-to-use-thread-pool-threads"></a>İş parçacığı havuzu iş parçacıkları kullanmamayı ne zaman  
 Oluşturmak ve iş parçacığı havuzu iş parçacıkları kullanmak yerine kendi iş parçacığı yönetmek uygun olduğu birkaç senaryo vardır:  
  
-   Bir ön plan iş parçacığı gerektirir.  
  
-   Bir iş parçacığı belirli bir önceliği olmasını gerektirir.  
  
-   Uzun bir süre için engellemek iş parçacığı neden görevleri vardır. İş parçacığı havuzu iş parçacıkları sayısı üst sahiptir, bu nedenle çok sayıda engellenmiş iş parçacığı havuzu iş parçacıkları görevleri başlamasını engelleyebilir.  
  
-   İş parçacığı bir tek iş parçacıklı yerleştirin gerekir. Tüm <xref:System.Threading.ThreadPool> iş parçacığı sayısı olan birden çok iş parçacıklı grupta.  
  
-   İş parçacığı ile ilişkili kararlı bir kimliğe sahip ya da bir iş parçacığı bir göreve ayrılması gerekir.  
  
## <a name="thread-pool-characteristics"></a>İş parçacığı havuzu özellikleri  
 İş parçacığı havuzu iş parçacıkları arka plan iş parçacıkları ' dir. Bkz: [ön plan ve arka plan iş parçacıkları](../../../docs/standard/threading/foreground-and-background-threads.md). Her iş parçacığı varsayılan yığın boyutunu kullanır, varsayılan öncelikte çalışır ve birden çok iş parçacıklı grupta sahiptir.  
  
 İşlem başına yalnızca bir iş parçacığı havuzu yok.  
  
### <a name="exceptions-in-thread-pool-threads"></a>İş parçacığı havuzu iş parçacıklarında özel durumlar  
 İş parçacığı havuzu iş parçacıkları işlenmeyen özel durumları işlemi sonlandırın. Bu kural için üç özel durum vardır:  
  
-   A <xref:System.Threading.ThreadAbortException> bir iş parçacığı havuzu iş parçacığı, çünkü atılır <xref:System.Threading.Thread.Abort%2A> çağrıldı.  
  
-   Bir <xref:System.AppDomainUnloadedException> uygulama etki alanı bellekten çünkü bir iş parçacığı havuzu iş parçacığı içinde oluşturulur.  
  
-   Ortak dil çalışma zamanı ya da bir ana bilgisayar işlemi iş parçacığı sonlanır.  
  
 Daha fazla bilgi için bkz: [yönetilen iş parçacıklarında özel durumlar](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
> [!NOTE]
>  .NET Framework sürüm 1.0 ve 1.1, ortak dil çalışma zamanı sessizce iş parçacığı havuzu iş parçacıkları işlenmeyen özel durumları yakalar. Bu uygulama durumu bozuk ve hata ayıklamak oldukça zor olabilir askıda kalmasına uygulamaları neden.  
  
### <a name="maximum-number-of-thread-pool-threads"></a>İş parçacığı havuzu iş parçacıkları sayısı  
 İş parçacığı havuzunun sıraya işlemlerinin sayısı yalnızca kullanılabilir bellek tarafından sınırlıdır; Ancak, iş parçacığı havuzu aynı anda işlemde etkin olabilir iş parçacığı sayısını sınırlar. İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], iş parçacığı havuzunun bir işlem için varsayılan boyutunu, sanal adres alanının boyutunu gibi birçok faktöre bağlıdır. Bir işlem çağırabilirsiniz <xref:System.Threading.ThreadPool.GetMaxThreads%2A> iş parçacığı sayısını belirlemek amacıyla yöntemi.  
  
 İş parçacığı sayısını kullanarak denetleyebilirsiniz <xref:System.Threading.ThreadPool.GetMaxThreads%2A> ve <xref:System.Threading.ThreadPool.SetMaxThreads%2A> yöntemleri.  
  
> [!NOTE]
>  .NET Framework sürüm 1.0 ve 1.1, iş parçacığı havuzunun boyutunu yönetilen koddan ayarlanamıyor. Ortak dil çalışma zamanı barındıran kod boyutu kullanarak ayarlayabilirsiniz `CorSetMaxThreads`, mscoree.h içinde tanımlı.  
  
### <a name="thread-pool-minimums"></a>İş parçacığı havuzu zamanlayıcısındaki  
 Her kategori için belirtilen en az ulaşana kadar iş parçacığı havuzu isteğe bağlı olarak yeni çalışan iş parçacığı veya g/ç Tamamlama iş parçacığı sağlar. Kullanabileceğiniz <xref:System.Threading.ThreadPool.GetMinThreads%2A> bu en düşük değerleri elde etmek için yöntemi.  
  
> [!NOTE]
>  İsteğe bağlı düşük olduğunda, gerçek iş parçacığı havuzu iş parçacıkları sayısı en düşük değerleri dönebilir.  
  
 En az ulaşıldığında, iş parçacığı havuzu ek iş parçacığı oluşturabilir veya bazı görevlerin tamamlanmasını bekleyin. İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], iş parçacığı havuzu oluşturur ve tamamlanmış zaman birimi görev sayısı olarak tanımlanan verimliliği en iyi duruma getirmek için çalışan iş parçacığı yok eder. Çok fazla iş parçacığı kaynak çekişmesini artırabilir ancak çok az iş parçacığı kullanılabilir kaynakları en iyi şekilde kullanılmasını yapabilir değil.  
  
> [!CAUTION]
>  Kullanabileceğiniz <xref:System.Threading.ThreadPool.SetMinThreads%2A> minimum boş iş parçacığı sayısını artırmak için yöntem. Ancak, bu değerleri gereksiz yere artan performans sorunlarına neden olabilir. Çok fazla görev aynı anda başlatırsanız, bunların tümünün yavaş görünebilir. Çoğu durumda iş parçacığı havuzu iş parçacıkları ayırma için kendi algoritması ile daha iyi gerçekleştirir.  
  
## <a name="skipping-security-checks"></a>Güvenlik denetimlerini atlanıyor  
 İş parçacığı havuzu de sağlar <xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=nameWithType> ve <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=nameWithType> yöntemleri. Bu yöntemleri yalnızca, çağıranın yığını kuyruğa alınmış görev yürütme sırasında gerçekleştirilen tüm güvenlik denetimleri için önemli olduğundan emin olduğunuzda kullanın. <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> ve <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> hem de iş parçacığının görevi yürütmek başladığında, iş parçacığı havuzu iş parçacığı yığına birleştirilmiş arayanın yığını yakalama. Güvenlik denetimi gereklidir, tüm yığın denetlenmesi gerekir. Onay güvenliğini sağlasa da, bir performans maliyetiyle da sahiptir.  
  
## <a name="using-the-thread-pool"></a>İş parçacığı havuzu kullanma  
 İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], iş parçacığı havuzu kullanmak için en kolay yolu kullanmaktır [görev paralel kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md). Varsayılan olarak, paralel kitaplık türleri ister <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> iş parçacığı havuzu iş parçacıkları görevleri çalıştırmak için kullanın. İş parçacığı havuzu çağırarak kullanabilirsiniz <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> yönetilen koddan (veya `CorQueueUserWorkItem` yönetilmeyen koddan) ve geçirme bir <xref:System.Threading.WaitCallback> görevi gerçekleştiren yöntemi temsil eden temsilci. İş parçacığı havuzu kullanmak üzere başka bir bekleme işlemini kullanarak ilişkili iş öğeleri sıraya almak için yoludur <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> yöntemi ve geçirerek bir <xref:System.Threading.WaitHandle> , işaret veya ne zaman, zaman aşımına uğradı tarafından temsil edilen yöntemini çağırır <xref:System.Threading.WaitOrTimerCallback> temsilci. İş parçacığı havuzu iş parçacıkları geri arama yöntemleri çağırmak için kullanılır.  
  
## <a name="threadpool-examples"></a>İş parçacığı havuzu örnekleri  
 Bu bölümdeki kod örnekleri kullanarak iş parçacığı havuzu göstermek <xref:System.Threading.Tasks.Task> sınıfı, <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> yöntemi ve <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> yöntemi.  
  
-   [Görev paralel kitaplığı ile zaman uyumsuz görevleri çalıştırma](#TaskParallelLibrary)  
  
-   [QueueUserWorkItem ile zaman uyumsuz olarak yürütülen kod](#ExecuteCodeWithQUWI)  
  
-   [QueueUserWorkItem görev verilerini sağlama](#TaskDataForQUWI)  
  
-   [RegisterWaitForSingleObject kullanma](#RegisterWaitForSingleObject)  
  
<a name="TaskParallelLibrary"></a>   
### <a name="executing-asynchronous-tasks-with-the-task-parallel-library"></a>Görev paralel kitaplığı ile zaman uyumsuz görevleri çalıştırma  
 Aşağıdaki örnekte, oluşturma ve kullanma gösterilmektedir bir <xref:System.Threading.Tasks.Task> çağırarak nesne <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> yöntemi. Kullanan bir örnek <xref:System.Threading.Tasks.Task%601> zaman uyumsuz bir görevden değer döndürme, görmek için sınıf [nasıl yapılır: bir görevden değer döndürme](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md).  
  
 [!code-csharp[System.Threading.Tasks.Task#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.task/cs/startnew.cs#01)]
 [!code-vb[System.Threading.Tasks.Task#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.task/vb/startnew.vb#01)]  
  
<a name="ExecuteCodeWithQUWI"></a>   
### <a name="executing-code-asynchronously-with-queueuserworkitem"></a>QueueUserWorkItem ile zaman uyumsuz olarak yürütülen kod  
 Aşağıdaki örneği tarafından temsil edilen çok basit bir görev kuyruklar `ThreadProc` yöntemini kullanarak <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> yöntemi.  
  
 [!code-cpp[Conceptual.ThreadPool#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.ThreadPool#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source1.cs#1)]
 [!code-vb[Conceptual.ThreadPool#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source1.vb#1)]  
  
<a name="TaskDataForQUWI"></a>   
### <a name="supplying-task-data-for-queueuserworkitem"></a>QueueUserWorkItem görev verilerini sağlama  
 Aşağıdaki kod örneğinde <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> bir görev sırası ve görev verilerini sağlamak için yöntem.  
  
 [!code-cpp[Conceptual.ThreadPool#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.ThreadPool#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source2.cs#2)]
 [!code-vb[Conceptual.ThreadPool#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source2.vb#2)]  
  
<a name="RegisterWaitForSingleObject"></a>   
### <a name="using-registerwaitforsingleobject"></a>RegisterWaitForSingleObject kullanma  
 Aşağıdaki örnek, birkaç iş parçacığı özellikleri gösterir.  
  
-   Bir görev tarafından yürütülmek queuing <xref:System.Threading.ThreadPool> iş parçacıklarını ile <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> yöntemi.  
  
-   Çalıştırılacak görev sinyal ile <xref:System.Threading.AutoResetEvent>. Bkz: [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md).  
  
-   Zaman aşımları ve sinyalleri işleme bir <xref:System.Threading.WaitOrTimerCallback> temsilci.  
  
-   Sıraya alınan görev iptal etme <xref:System.Threading.RegisteredWaitHandle>.  
  
 [!code-cpp[Conceptual.ThreadPool#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.ThreadPool#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source3.cs#3)]
 [!code-vb[Conceptual.ThreadPool#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.ThreadPool>  
 <xref:System.Threading.Tasks.Task>  
 <xref:System.Threading.Tasks.Task%601>  
 [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [Nasıl yapılır: Bir Görevden Değer Döndürme](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)  
 [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)  
 [İş Parçacıkları ve İş Parçacığı Oluşturma](../../../docs/standard/threading/threads-and-threading.md)  
 [Zaman Uyumsuz Dosya G/Ç](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [Süreölçerler](../../../docs/standard/threading/timers.md)
