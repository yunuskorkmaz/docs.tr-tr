---
title: Semafor ve SemaphoreSlim
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- counting semaphores
- semaphores
- threading [.NET Framework], cross-process synchronization
- Semaphore class, about Semaphore class
- SemaphoreSlim class, about SemaphoreSlim class
- threading [.NET Framework], Semaphore class
ms.assetid: 7722a333-b974-47a2-a7c0-f09097fb644e
ms.openlocfilehash: b9f7c122ac8acf34f740aca5f0fafc162edcea82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127582"
---
# <a name="semaphore-and-semaphoreslim"></a>Semafor ve SemaphoreSlim
Sınıf <xref:System.Threading.Semaphore?displayProperty=nameWithType> adlı (sistem çapında) veya yerel semafor temsil eder. Win32 semafor nesnesinin etrafında ince bir sarmalayıcıdır. Win32 semaforlar, kaynak havuzuna erişimi kontrol etmek için kullanılabilecek semaforları sayıyor.  
  
 Sınıf, <xref:System.Threading.SemaphoreSlim> bekleme sürelerinin çok kısa olması beklendiği tek bir işlem de beklemek için kullanılabilecek hafif ve hızlı bir semaforu temsil eder. <xref:System.Threading.SemaphoreSlim>ortak dil çalışma zamanı (CLR) tarafından sağlanan eşitleme ilkel mümkün olduğunca dayanır. Ancak, aynı zamanda birden fazla semafor bekleyen desteklemek için gerekli olarak lazily başharfli, çekirdek tabanlı bekleme kolları sağlar. <xref:System.Threading.SemaphoreSlim>ayrıca iptal belirteçlerinin kullanımını destekler, ancak semaforlar veya senkronizasyon için bir bekleme tutamacı kullanımını desteklemez.  
  
## <a name="managing-a-limited-resource"></a>Sınırlı Kaynak Yönetme  
 İş <xref:System.Threading.WaitHandle.WaitOne%2A> parçacıkları, bir <xref:System.Threading.WaitHandle> <xref:System.Threading.Semaphore?displayProperty=nameWithType> <xref:System.Threading.SemaphoreSlim.Wait%2A?displayProperty=nameWithType> <xref:System.Threading.SemaphoreSlim.WaitAsync%2A?displayProperty=nameWithType> <xref:System.Threading.SemaphoreSlim> nesne veya yöntem durumunda, bir nesne durumunda, sınıftan devralınan yöntemi çağırarak semaforgirine girer. Çağrı geri döndüğünde, semafor sayısı azat edilir. Bir iş parçacığı giriş istediğinde ve sayım sıfır olduğunda, iş parçacığı engeller. İş parçacıkları semaforu <xref:System.Threading.Semaphore.Release%2A?displayProperty=nameWithType> veya <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> yöntemi arayarak serbest kattıkça, engellenen iş parçacıklarının girmesine izin verilir. Engellenen iş parçacıklarının semafora girmesi için ilk giriş, ilk çıkış (FIFO) veya son,ilk çıkış (LIFO) gibi garantili bir sipariş yoktur.  
  
 Bir iş parçacığı, <xref:System.Threading.Semaphore?displayProperty=nameWithType> nesnenin <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemini veya nesnenin <xref:System.Threading.SemaphoreSlim> <xref:System.Threading.SemaphoreSlim.Wait%2A> yöntemini tekrar tekrar çağırarak semafora birden çok kez girebilir. Semaforu serbest bırakmak için, iş <xref:System.Threading.Semaphore.Release?displayProperty=nameWithType> parçacığı <xref:System.Threading.SemaphoreSlim.Release?displayProperty=nameWithType> veya yöntemin aynı sayıda aşırı <xref:System.Threading.Semaphore.Release%28System.Int32%29?displayProperty=nameWithType> yüklenmesini arayabilir veya veya <xref:System.Threading.SemaphoreSlim.Release%28System.Int32%29?displayProperty=nameWithType> yöntemi aşırı yükleyebilir ve serbest bırakılacak giriş sayısını belirtebilir.  
  
### <a name="semaphores-and-thread-identity"></a>Semaforlar ve İplik Kimliği  
 <xref:System.Threading.WaitHandle.WaitOne%2A>İki semafor türü, , , <xref:System.Threading.SemaphoreSlim.Wait%2A> <xref:System.Threading.Semaphore.Release%2A>, , ve <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> yöntemleri aramalarda iş parçacığı kimliğini zorlamaz. Örneğin, semaforlar için ortak bir kullanım senaryosu, bir iş parçacığı her zaman semafor sayısını artımlı ve diğeri her zaman onu yok eden bir üretici iş parçacığı ve tüketici iş parçacığı içerir.  
  
 Bir iş parçacığının semaforu çok fazla serbest bırakmamasını sağlamak programcının sorumluluğundadır. Örneğin, bir semaforun en fazla iki sayısı olduğunu ve a ve iş parçacığı B'nin semafora girdiğini varsayalım. B iş parçacığındaki bir programlama hatası `Release` iki kez çağrılmasını neden olursa, her iki çağrı da başarılı olur. Semafor sayısı dolu ve iş parçacığı A sonunda `Release`çağırır, <xref:System.Threading.SemaphoreFullException> bir atılır.  
  
## <a name="named-semaphores"></a>Adı Semaforlar  
 Windows işletim sistemi semaforların adlarını olmasını sağlar. Semafor adı sistem çapındadır. Diğer bir deyişle, semafor adlı oluşturulduktan sonra, tüm işlemlerde tüm iş parçacıkları tarafından görülebilir. Böylece semafor adı verilen işlemlerin ve iş parçacıklarının etkinliklerini senkronize etmek için kullanılabilir.  
  
 Adlandırılmış bir <xref:System.Threading.Semaphore> sistem semaforu temsil eden bir nesne oluşturabilirsiniz, bir ad belirten yapıcılardan birini kullanarak.  
  
> [!NOTE]
> Adlandırılmış semaforlar sistem genelinde olduğundan, semafor <xref:System.Threading.Semaphore> adlı aynı temsil eden birden çok nesneye sahip olmak mümkündür. Bir oluşturucuyu veya <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> yöntemi her çağırdığınızda, yeni <xref:System.Threading.Semaphore> bir nesne oluşturulur. Aynı adı belirtme, semafor adı verilen aynı temsil eden birden çok nesne oluşturur.  
  
 Semaforlar kullanılırken dikkatli olun. Sistem genelinde olduklarından, aynı adı kullanan başka bir işlem beklenmedik bir şekilde semaforunuzu girebilir. Aynı bilgisayarda çalıştırılabilen kötü amaçlı kod, bunu hizmet reddi saldırısının temeli olarak kullanabilir.  
  
 Adlandırılmış semaforu <xref:System.Threading.Semaphore> temsil eden bir nesneyi korumak için erişim denetimi güvenliğini kullanın, <xref:System.Security.AccessControl.SemaphoreSecurity?displayProperty=nameWithType> tercihen bir nesneyi belirten bir oluşturucu kullanarak. Bu <xref:System.Threading.Semaphore.SetAccessControl%2A?displayProperty=nameWithType> yöntemkullanarak erişim denetimi güvenliğini de uygulayabilirsiniz, ancak bu, semaforun oluşturulduğu saat ile korunduğu saat arasında bir güvenlik açığı penceresi bırakır. Semaforların erişim denetimi güvenliğiyle korunması kötü amaçlı saldırıları önlemeye yardımcı olur, ancak istenmeyen ad çakışmasorununu çözmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Semaphore>
- <xref:System.Threading.SemaphoreSlim>
- [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)
