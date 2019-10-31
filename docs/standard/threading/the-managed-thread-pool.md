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
ms.openlocfilehash: 2671ce7c9721b15de8a3805da27040e973a62804
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127531"
---
# <a name="the-managed-thread-pool"></a>Yönetilen iş parçacığı havuzu

<xref:System.Threading.ThreadPool?displayProperty=nameWithType> sınıfı, uygulamanızı sistem tarafından yönetilen bir çalışan iş parçacığı havuzu sunarak, iş parçacığı yönetimi yerine uygulama görevlerine odaklanmanızı sağlar. Arka plan işlemesi gerektiren kısa görevleriniz varsa, yönetilen iş parçacığı havuzu, birden çok iş parçacığından faydalanmak için kolay bir yoldur. İş parçacığı havuzu iş parçacıklarında zaman uyumsuz görevler gerçekleştiren <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> nesneleri oluşturabileceğiniz için iş parçacığı havuzunun kullanımı, Framework 4 ve üzeri sürümlerde önemli ölçüde daha kolay.  
  
.NET, [görev paralel kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md) işlemleri, zaman uyumsuz g/ç tamamlama, [süreölçer](timers.md) geri çağırmaları, kayıtlı bekleme işlemleri, temsilciler kullanılarak zaman uyumsuz yöntem çağrıları ve <xref:System.Net?displayProperty=nameWithType> yuva gibi birçok amaçla iş parçacığı havuzu iş parçacıklarını kullanır bağlantının.  

## <a name="thread-pool-characteristics"></a>İş parçacığı havuzu özellikleri

İş parçacığı havuzu iş parçacıkları [arka plan](foreground-and-background-threads.md) iş parçacığıdır. Her bir iş parçacığı varsayılan yığın boyutunu kullanır, varsayılan öncelikte çalışır ve çok iş parçacıklı apartman içinde olur. İş parçacığı havuzundaki bir iş parçacığı görevini tamamladıktan sonra, bir bekleme iş parçacığı kuyruğuna döndürülür. Bu andan itibaren yeniden kullanılabilir. Bu yeniden kullanım, uygulamaların her görev için yeni bir iş parçacığı oluşturma maliyetinden kaçınmasını sağlar.
  
İşlem başına yalnızca bir iş parçacığı havuzu vardır.  
  
### <a name="exceptions-in-thread-pool-threads"></a>İş parçacığı havuzu iş parçacıklarında özel durumlar

İş parçacığı havuzu iş parçacıklarında işlenmeyen özel durumlar işlemi sonlandırır. Bu kuralın üç istisnası vardır:  
  
- <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> çağrıldığı için bir iş parçacığı havuzu iş parçacığında <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> oluşur.  
- Uygulama etki alanı kaldırıldığından bir iş parçacığı havuzu iş parçacığında bir <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> oluşturulur.  
- Ortak dil çalışma zamanı veya bir ana bilgisayar işlemi iş parçacığını sonlandırır.  
  
Daha fazla bilgi için bkz. [yönetilen Iş parçacıklarında özel durumlar](exceptions-in-managed-threads.md).  
  
### <a name="maximum-number-of-thread-pool-threads"></a>En fazla iş parçacığı havuzu iş parçacığı sayısı

İş parçacığı havuzunda sıraya alınabilen işlem sayısı yalnızca kullanılabilir bellekle sınırlıdır. Ancak, iş parçacığı havuzu işlemde etkin olabilecek iş parçacıklarının sayısını aynı anda sınırlandırır. Tüm iş parçacığı havuzu iş parçacıkları meşgulse, bunları yürütmek için iş parçacıkları kullanılabilir hale gelene kadar ek iş öğeleri sıraya alınır. .NET Framework 4 ' ten başlayarak, bir işlem için iş parçacığı havuzunun varsayılan boyutu, sanal adres alanının boyutu gibi çeşitli faktörlere bağlıdır. Bir işlem, iş parçacığı sayısını belirleyebilmek için <xref:System.Threading.ThreadPool.GetMaxThreads%2A?displayProperty=nameWithType> metodunu çağırabilir.  
  
<xref:System.Threading.ThreadPool.GetMaxThreads%2A?displayProperty=nameWithType> ve <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> yöntemlerini kullanarak en fazla iş parçacığı sayısını kontrol edebilirsiniz.  

> [!NOTE]
> Ortak dil çalışma zamanını barındıran kod, [`ICorThreadpool::CorSetMaxThreads`](../../framework/unmanaged-api/hosting/icorthreadpool-corsetmaxthreads-method.md) yöntemini kullanarak boyutu ayarlayabilir.  
  
### <a name="thread-pool-minimums"></a>İş parçacığı havuzu en az UMS

İş parçacığı havuzu, her kategori için belirtilen bir alt sınıra ulaşana kadar isteğe bağlı olarak yeni çalışan iş parçacıkları veya g/ç Tamamlama iş parçacıkları sağlar. Bu minimum değerleri almak için <xref:System.Threading.ThreadPool.GetMinThreads%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.  
  
> [!NOTE]
> İstek düşükse, iş parçacığı havuzu iş parçacıklarının gerçek sayısı en düşük değerlerin altına düşmelidir.  
  
En az bir ulaşıldığında, iş parçacığı havuzu ek iş parçacıkları oluşturabilir veya bazı görevler tamamlanana kadar bekleyebilir. .NET Framework 4 ' ten başlayarak, iş parçacığı havuzu iş parçacıklarını oluşturup yok eder ve bu işlem, zaman birimi başına tamamlanan görev sayısı olarak tanımlanır. Çok az sayıda iş parçacığı kullanılabilir kaynakları en iyi şekilde kullanmayabilir, ancak çok fazla iş parçacığı kaynak çekişmesini artırabilir.  
  
> [!CAUTION]
> En düşük boşta iş parçacığı sayısını artırmak için <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz. Ancak, bu değerleri gereksiz şekilde artırmak performans sorunlarına neden olabilir. Aynı anda çok fazla görev başladıysanız, bunların hepsi yavaş görünüyor olabilir. Çoğu durumda, iş parçacığı havuzu iş parçacığı ayırmak için kendi algoritmasından daha iyi işlem yapar.  

## <a name="using-the-thread-pool"></a>İş parçacığı havuzunu kullanma

.NET Framework 4 ' ten başlayarak, iş parçacığı havuzunu kullanmanın en kolay yolu, [görev paralel kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md)kullanmaktır. Varsayılan olarak, <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> gibi TPL türleri, görevleri çalıştırmak için iş parçacığı havuzu iş parçacıklarını kullanır.

İş parçacığı havuzunu yönetilen koddan <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> çağırarak (veya yönetilmeyen koddan [`ICorThreadpool::CorQueueUserWorkItem`](../../framework/unmanaged-api/hosting/icorthreadpool-corqueueuserworkitem-method.md) ) ve görevi gerçekleştiren yöntemi temsil eden bir <xref:System.Threading.WaitCallback?displayProperty=nameWithType> temsilcisini geçirerek de kullanabilirsiniz.

İş parçacığı havuzunu kullanmanın başka bir yolu da, <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> yöntemini kullanarak bir bekleme işlemiyle ilgili iş öğelerini sıraya almak ve sinyal edildiğinde ya da zaman aşımına uğradıktan sonra, <xref:System.Threading.WaitOrTimerCallback?displayProperty=nameWithType> temsilcisinden temsil edilen yöntemi çağırmalarından <xref:System.Threading.WaitHandle?displayProperty=nameWithType> geçirmektir. İş parçacığı havuzu iş parçacıkları, geri çağırma yöntemlerini çağırmak için kullanılır.  

Örnekler için, başvurulan API sayfalarını denetleyin.
  
## <a name="skipping-security-checks"></a>Güvenlik denetimleri atlanıyor

İş parçacığı havuzu ayrıca <xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=nameWithType> ve <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=nameWithType> yöntemleri de sağlar. Bu yöntemleri yalnızca, arayanın yığınının sıraya alınan görevin yürütülmesi sırasında gerçekleştirilen herhangi bir güvenlik denetimi için ilgisiz olduğundan eminseniz kullanın. <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> ve <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> her ikisi de, iş parçacığı bir görevi yürütmeye başladığında iş parçacığı havuzu iş parçacığının yığınına birleştirilmiş çağıranın yığınını yakalar. Bir güvenlik denetimi gerekiyorsa, yığının tamamının denetlenmesi gerekir. Denetim güvenlik sağlar, ancak performans maliyeti de vardır.  

## <a name="when-not-to-use-thread-pool-threads"></a>İş parçacığı havuzu iş parçacıklarının ne zaman kullanılacağı

İş parçacığı havuzu iş parçacıklarını kullanmak yerine kendi iş parçacıklarınızı oluşturmak ve yönetmek için uygun olan birkaç senaryo vardır:  
  
- Ön plan iş parçacığına ihtiyacınız vardır.  
- Belirli bir önceliğe sahip olması için bir iş parçacığına ihtiyacınız vardır.  
- İş parçacığının uzun süre boyunca engellenmesine neden olan görevleriniz var. İş parçacığı havuzunda en fazla sayıda iş parçacığı bulunur, bu nedenle çok sayıda engellenen iş parçacığı havuzu iş parçacığı görevlerin başlamasını engelleyebilir.  
- İş parçacıklarını tek iş parçacıklı bir gruba yerleştirmeniz gerekir. Tüm <xref:System.Threading.ThreadPool> iş parçacıkları çok iş parçacıklı grupta bulunur.  
- İş parçacığı ile ilişkili kararlı bir kimliğiniz olması veya bir iş parçacığını bir göreve ayırmanız gerekir.  
  
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
