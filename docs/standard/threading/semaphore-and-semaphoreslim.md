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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25121ea2b089df49efa77dcf363e2a0e400b3bff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968429"
---
# <a name="semaphore-and-semaphoreslim"></a>Semafor ve SemaphoreSlim
Sınıf <xref:System.Threading.Semaphore?displayProperty=nameWithType> , adlandırılmış (systemwide) veya yerel semaforu temsil eder. Bu, Win32 semafor nesnesinin etrafında ince bir sarmalayıcıdır. Win32 semaforları, bir kaynak havuzuna erişimi denetlemek için kullanılabilen semafor sayısını saymaktadır.  
  
 Bu <xref:System.Threading.SemaphoreSlim> sınıf, bekleme süreleri çok kısa olması beklendiğinde tek bir işlem içinde bekleme için kullanılabilen hafif ve hızlı bir semaforu temsil eder. <xref:System.Threading.SemaphoreSlim>ortak dil çalışma zamanı (CLR) tarafından belirtilen eşitleme temelleri için mümkün olduğunca fazla kullanır. Bununla birlikte, Ayrıca, birden fazla semaforda beklemeyi desteklemek için gereken geç, çekirdek tabanlı bekleme tanıtıcıları de sağlar. <xref:System.Threading.SemaphoreSlim>Ayrıca, iptal belirteçleri kullanımını destekler, ancak adlandırılmış semaforları veya eşitleme için bir bekleme tanıtıcısının kullanımını desteklemez.  
  
## <a name="managing-a-limited-resource"></a>Sınırlı bir kaynağı yönetme  
 İş parçacıkları, bir nesne söz konusu <xref:System.Threading.WaitHandle.WaitOne%2A> olduğunda <xref:System.Threading.WaitHandle> sınıfından <xref:System.Threading.Semaphore?displayProperty=nameWithType> <xref:System.Threading.SemaphoreSlim.Wait%2A?displayProperty=nameWithType> devralınan yöntemini çağırarak veya bir nesne durumunda <xref:System.Threading.SemaphoreSlim> ya <xref:System.Threading.SemaphoreSlim.WaitAsync%2A?displayProperty=nameWithType> da yöntemi olan semafor girer. Çağrı döndüğünde, semaforda sayı azaltılır. Bir iş parçacığı istediğinde ve sayı sıfır olduğunda, iş parçacığı engeller. İş parçacıkları <xref:System.Threading.Semaphore.Release%2A?displayProperty=nameWithType> veya <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> metodunu çağırarak semaforu serbest bırakarak engellenen iş parçacıklarının girmesine izin verilir. Engellenen iş parçacıkları için semaforu girmesi için ilk giriş, ilk çıkar (FıFO) veya son giriş, ilk çıkar (LıFO) gibi garantili bir sıra yoktur.  
  
 Bir <xref:System.Threading.Semaphore?displayProperty=nameWithType> iş parçacığı <xref:System.Threading.WaitHandle.WaitOne%2A> nesnenin <xref:System.Threading.SemaphoreSlim>metodunuya da nesnenin yönteminisürekliçağıraraksemaforubirdençokkezgirebilir.<xref:System.Threading.SemaphoreSlim.Wait%2A> Semaforu serbest bırakmak için, iş <xref:System.Threading.Semaphore.Release?displayProperty=nameWithType> parçacığı ya <xref:System.Threading.SemaphoreSlim.Release?displayProperty=nameWithType> da yöntem aşırı yüklemesini aynı sayıda çağırabilir veya <xref:System.Threading.Semaphore.Release%28System.Int32%29?displayProperty=nameWithType> ya <xref:System.Threading.SemaphoreSlim.Release%28System.Int32%29?displayProperty=nameWithType> da yöntem aşırı yüklemesini çağırabilir ve yayımlanacak girdi sayısını belirtebilir.  
  
### <a name="semaphores-and-thread-identity"></a>Semaforlar ve Iş parçacığı kimliği  
 İki <xref:System.Threading.WaitHandle.WaitOne%2A>semafor türü <xref:System.Threading.SemaphoreSlim.Wait%2A> <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> ,,, ve yöntemlerine yapılan çağrılar üzerinde iş parçacığı kimliğini zorlamaz. <xref:System.Threading.Semaphore.Release%2A> Örneğin, Semaforlar için ortak bir kullanım senaryosunda bir üretici iş parçacığı ve bir tüketici iş parçacığı ve bir iş parçacığı her zaman semafor sayısını arttırılarak diğer her zaman azaltılır.  
  
 Bir iş parçacığının semaforu çok fazla kez serbest bırakmadığından emin olmak programcı sorumluluğundadır. Örneğin, bir semaforun en fazla iki sayısına sahip olduğunu ve A iş parçacığı A ve iş parçacığı B 'nin her ikisi de semaforu girmelerini sağladığını varsayalım. B iş parçacığında bir programlama hatası, iki kez çağrı `Release` yapmasına neden olursa her iki çağrı de başarılı olur. Semaforda bulunan sayı dolu ve iş parçacığı sonunda çağrı `Release`yaptığı zaman bir <xref:System.Threading.SemaphoreFullException> atılır.  
  
## <a name="named-semaphores"></a>Adlandırılmış Semaforlar  
 Windows işletim sistemi, Semaforlar adlara sahip olmasına izin verir. Adlandırılmış semafor sistem genelinde olur. Diğer bir deyişle, adlandırılmış semafor oluşturulduktan sonra, tüm süreçlerdeki tüm iş parçacıkları tarafından görülebilir. Bu nedenle, adlandırılmış semafor, işlem etkinliklerini ve iş parçacıklarını eşitlemesi için kullanılabilir.  
  
 Bir adı belirten oluşturuculardan birini kullanarak, adlandırılmış bir sistem semaforu temsil eden bir <xref:System.Threading.Semaphore> nesne oluşturabilirsiniz.  
  
> [!NOTE]
> Adlandırılmış Semaforlar sistem genelinde olduğundan, aynı adlı semaforu temsil eden <xref:System.Threading.Semaphore> birden çok nesne olması mümkündür. Her bir oluşturucuyu veya <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> yöntemini her çağırdığınızda yeni <xref:System.Threading.Semaphore> bir nesne oluşturulur. Aynı adın belirtilmesi, aynı adlı semaforu temsil eden birden çok nesne oluşturur.  
  
 Adlandırılmış Semaforlar kullanırken dikkatli olun. Sistem genelinde olduklarından aynı adı kullanan başka bir işlem, semaforu beklenmedik bir şekilde girebilirler. Aynı bilgisayarda çalışan kötü amaçlı kod bunu bir hizmet reddi saldırısı temeli olarak kullanabilir.  
  
 Tercihen bir <xref:System.Threading.Semaphore> <xref:System.Security.AccessControl.SemaphoreSecurity?displayProperty=nameWithType> nesneyi belirten bir Oluşturucu kullanarak adlandırılmış semaforu temsil eden bir nesneyi korumak için erişim denetimi güvenliği ' ni kullanın. <xref:System.Threading.Semaphore.SetAccessControl%2A?displayProperty=nameWithType> Yöntemi kullanarak erişim denetimi güvenliği de uygulayabilirsiniz, ancak bu, semaforun oluşturulduğu zaman ve koruduğu zaman arasında bir güvenlik açığı penceresi bırakır. Erişim denetimi güvenliği ile Semaforlar koruma kötü amaçlı saldırıları önlemeye yardımcı olur, ancak istemeyerek ad çakışmalarının sorununu çözmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Semaphore>
- <xref:System.Threading.SemaphoreSlim>
- [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)
