---
title: Yönetilen iş parçacığı havuzu
description: Arka plan çalışan iş parçacıkları sağlayan .NET iş parçacığı havuzu hakkında bilgi edinin
ms.date: 08/02/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- thread pooling [.NET]
- thread pools [.NET]
- threading [.NET], thread pool
- threading [.NET], pooling
ms.assetid: 2be05b06-a42e-4c9d-a739-96c21d673927
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7721ffaebfefadee332c923d867e68204b5205f
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44700865"
---
# <a name="the-managed-thread-pool"></a>Yönetilen iş parçacığı havuzu

<xref:System.Threading.ThreadPool?displayProperty=nameWithType> Sınıfı yerine uygulama görevleri hakkında yoğunlaşabilirsiniz yönetim iş parçacığı olanak tanıyan sistem tarafından yönetilen çalışan iş parçacığı havuzu ile uygulamanızı sağlar. Arka plan işlemleri gerektiren kısa görevler varsa, yönetilen iş parçacığı havuzu birden çok iş parçacığı yararlanmak için kolay bir yoludur. İş parçacığı havuzu kullanımı önemli ölçüde daha kolay Framework 4 ve üzeri, oluşturabileceğiniz bu yana <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> iş parçacığında zaman uyumsuz görevleri gerçekleştiren nesneler iş parçacığı havuzu.  
  
.NET iş parçacığı havuzu iş parçacıkları dahil olmak üzere birçok farklı amaçla kullanan [görev paralel kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md) işlem, zaman uyumsuz g/ç tamamlama [Zamanlayıcı](timers.md) kayıtlı geri çağırmalar bekleyin işlemlerini zaman uyumsuz yöntemi Temsilciler, kullanarak çağırır ve <xref:System.Net?displayProperty=nameWithType> yuva bağlantı.  

## <a name="thread-pool-characteristics"></a>İş parçacığı havuzu özellikleri

İş parçacığı havuzu iş parçacıkları olan [arka plan](foreground-and-background-threads.md) iş parçacıkları. Her iş parçacığı varsayılan yığın boyutu kullanır, varsayılan öncelikli olarak çalışır ve çok iş parçacıklı apartmanda olduğu. Bir iş parçacığının iş parçacığı havuzundaki görevi tamamlandıktan sonra bekleyen iş parçacıklarının kuyruğa döndürülür. Bu andan itibaren yeniden kullanılabilir. Bu yeniden her görev için yeni bir iş parçacığı oluşturma maliyeti önlemek uygulamaları etkinleştirir.
  
İşlem başına yalnızca bir iş parçacığı havuzu yok.  
  
### <a name="exceptions-in-thread-pool-threads"></a>İş parçacığı havuzu iş parçacıklarında özel durumlar

İşlenmeyen özel durumları iş parçacığı havuzu iş parçacıklarında işlemi sonlandırılamıyor. Bu kural için üç özel durum vardır:  
  
- A <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> çünkü bir iş parçacığı havuzu iş parçacığında oluşturulan <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> çağrıldı.  
- A <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> uygulama etki alanı kaldırıldı çünkü bir iş parçacığı havuzu iş parçacığı oluşturulur.  
- Ortak dil çalışma zamanı ya da bir ana bilgisayar işlemi iş parçacığı sonlanır.  
  
Daha fazla bilgi için [yönetilen iş parçacıklarında özel durumlar](exceptions-in-managed-threads.md).  
  
### <a name="maximum-number-of-thread-pool-threads"></a>İş parçacığı havuzu iş parçacıkları sayısı

İş parçacığı havuzu için sıraya işlemlerin sayısı yalnızca kullanılabilir bellekle sınırlıdır. Ancak, iş parçacığı havuzu aynı anda işlemde etkin olabilir, iş parçacığı sayısını sınırlar. Tüm iş parçacığı havuzu iş parçacıkları meşgul ise, bunları çalıştırmak için iş parçacığı kullanılabilir hale kadar ek iş öğelerini kuyruğa alınır. .NET Framework 4 ile başlayarak, bir işlem için iş parçacığı havuzu varsayılan boyutu sanal adres alanı boyutu gibi çeşitli faktörlere bağlıdır. Bir işlemi çağırabilir <xref:System.Threading.ThreadPool.GetMaxThreads%2A?displayProperty=nameWithType> iş parçacığı sayısını belirlemek için yöntemi.  
  
İş parçacığı sayısı kullanarak denetleyebilirsiniz <xref:System.Threading.ThreadPool.GetMaxThreads%2A?displayProperty=nameWithType> ve <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> yöntemleri.  

> [!NOTE]
> Ortak dil çalışma zamanını barındıran kod kullanarak boyutu ayarlayabileceğiniz [ `ICorThreadpool::CorSetMaxThreads` ](../../framework/unmanaged-api/hosting/icorthreadpool-corsetmaxthreads-method.md) yöntemi.  
  
### <a name="thread-pool-minimums"></a>İş parçacığı havuzu alt sınır

Her kategori için belirtilen en az ulaşana kadar iş parçacığı havuzu isteğe bağlı olarak yeni çalışan iş parçacıkları veya g/ç Tamamlama iş parçacıklarını sağlar. Kullanabileceğiniz <xref:System.Threading.ThreadPool.GetMinThreads%2A?displayProperty=nameWithType> bu en düşük değerler elde etmek için yöntemi.  
  
> [!NOTE]
> Talep azaldığında, gerçek iş parçacığı havuzu iş parçacıkları sayısı aşağıdaki en düşük değerleri gelebilir.  
  
En az ulaşıldığında, iş parçacığı havuzu ek iş parçacığı oluşturabilir veya bazı görevler tamamlanana kadar bekleyin. .NET Framework 4 ile başlayarak, iş parçacığı havuzu oluşturur ve zaman birimi tamamlayan görev sayısı olarak tanımlanan aktarım hızını iyileştirmek için çalışan iş parçacığı yok eder. Çok fazla iş parçacığı kaynak çekişmesini artırabilen ise çok az iş parçacığı kullanılabilir kaynakların en iyi kullanımı yapabileceğiniz değil.  
  
> [!CAUTION]
> Kullanabileceğiniz <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> en az boşta iş parçacığı sayısını artırmak için yöntemi. Ancak, bu değerleri gereksiz yere artan performans sorunlarına neden olabilir. Çok fazla görev aynı anda başlatırsanız, bunların tümünün yavaş görünebilir. Çoğu durumda iş parçacığı havuzu iş parçacıkları tahsis etmek için kendi algoritması ile daha iyi sonuç verecektir.  

## <a name="using-the-thread-pool"></a>İş parçacığı havuzu kullanma

.NET Framework 4 ile başlayarak, kullanılacak iş parçacığı havuzu kullanmak için en kolay yolu olan [görev paralel kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md). Varsayılan olarak, TPL türleri ister <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> iş parçacığı havuzu iş parçacıkları, görevleri çalıştırmak için kullanın.

Çağırarak iş parçacığı havuzu kullanabilirsiniz <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> yönetilen koddan (veya [ `ICorThreadpool::CorQueueUserWorkItem` ](../../framework/unmanaged-api/hosting/icorthreadpool-corqueueuserworkitem-method.md) , yönetilmeyen koddan) ve bir <xref:System.Threading.WaitCallback?displayProperty=nameWithType> görevi gerçekleştiren bir yöntemi temsil eden temsilci.

Sıra için bir bekleme işlemini kullanarak ilgili iş öğeleri için iş parçacığı havuzu kullanma başka bir yolu ise <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> yöntemi ve geçirme bir <xref:System.Threading.WaitHandle?displayProperty=nameWithType> , sinyal veya zaman aşımına uğradı, çağıran tarafından temsil edilen yönteme <xref:System.Threading.WaitOrTimerCallback?displayProperty=nameWithType> temsilci. İş parçacığı havuzu iş parçacıkları, geri çağırma yöntemlerini çağırmak için kullanılır.  

Örneğin, başvurulan API sayfaları denetleyin.
  
## <a name="skipping-security-checks"></a>Güvenlik denetimleri atlanıyor

Ayrıca, iş parçacığı havuzu sağlar <xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=nameWithType> ve <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=nameWithType> yöntemleri. Bu yöntem, yalnızca, arayanın yığın sıraya alınan görevin yürütülmesi sırasında gerçekleştirilen herhangi bir güvenlik denetimi için ilgisiz geldiğinden emin olduğunuzda kullanın. <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> ve <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> hem de bir görev yürütmek iş parçacığı başladığında, iş parçacığı havuzu iş parçacığı yığın halinde birleştirilir arayanın yığın yakalayın. Güvenlik denetimi gereklidir, tüm yığını denetlenmesi gerekir. Güvenlik denetimi sağlar, ancak ayrıca performans maliyetine sahiptir.  

## <a name="when-not-to-use-thread-pool-threads"></a>İş parçacığı havuzu iş parçacıkları kullanmayı ne zaman

Oluşturmak ve iş parçacığı havuzu iş parçacıkları yerine kendi iş parçacığı yönetmek uygun olan birkaç senaryo vardır:  
  
- Ön plan iş parçacığı gerektirir.  
- Belirli bir önceliğe sahip bir iş parçacığı gerektirir.  
- İş parçacığı uzun sürelerle engellemek neden görevleri var. İş parçacığı havuzu iş parçacıkları, en fazla olduğundan çok sayıda engellenmiş iş parçacığı havuzu iş parçacıkları görevleri başlamasını engelleyebilir.  
- İş parçacığı bir tek iş parçacıklı grup yerleştirmek gerekir. Tüm <xref:System.Threading.ThreadPool> birden çok iş parçacıklı apartmanda akışlardır.  
- İş parçacığıyla ilişkilendirilmiş kararlı bir kimliğe sahip veya bir görev için bir iş parçacığı ayrılması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>  
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>  
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>  
- [Görev Paralel Kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md)  
- [Nasıl yapılır: Bir Görevden Değer Döndürme](../parallel-programming/how-to-return-a-value-from-a-task.md)  
- [İş Parçacığı Nesneleri ve Özellikleri](threading-objects-and-features.md)  
- [İş Parçacıkları ve İş Parçacığı Oluşturma](threads-and-threading.md)  
- [Zaman Uyumsuz Dosya G/Ç](../io/asynchronous-file-i-o.md)  
- [Süreölçerler](timers.md)  
