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
ms.openlocfilehash: 9a18a6517548bb402e1e3b9ac02e95aae32a8f4a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291142"
---
# <a name="semaphore-and-semaphoreslim"></a>Semafor ve SemaphoreSlim
<xref:System.Threading.Semaphore?displayProperty=nameWithType>Sınıf, adlandırılmış (systemwide) veya yerel semaforu temsil eder. Bu, Win32 semafor nesnesinin etrafında ince bir sarmalayıcıdır. Win32 semaforları, bir kaynak havuzuna erişimi denetlemek için kullanılabilen semafor sayısını saymaktadır.  
  
 Bu <xref:System.Threading.SemaphoreSlim> sınıf, bekleme süreleri çok kısa olması beklendiğinde tek bir işlem içinde bekleme için kullanılabilen hafif ve hızlı bir semaforu temsil eder. <xref:System.Threading.SemaphoreSlim>ortak dil çalışma zamanı (CLR) tarafından belirtilen eşitleme temelleri için mümkün olduğunca fazla kullanır. Bununla birlikte, Ayrıca, birden fazla semaforda beklemeyi desteklemek için gereken geç, çekirdek tabanlı bekleme tanıtıcıları de sağlar. <xref:System.Threading.SemaphoreSlim>Ayrıca, iptal belirteçleri kullanımını destekler, ancak adlandırılmış semaforları veya eşitleme için bir bekleme tanıtıcısının kullanımını desteklemez.  
  
## <a name="managing-a-limited-resource"></a>Sınırlı bir kaynağı yönetme  
 İş parçacıkları, bir nesne söz konusu olduğunda sınıfından devralınan yöntemini çağırarak veya bir nesne <xref:System.Threading.WaitHandle.WaitOne%2A> <xref:System.Threading.WaitHandle> <xref:System.Threading.Semaphore?displayProperty=nameWithType> <xref:System.Threading.SemaphoreSlim.Wait%2A?displayProperty=nameWithType> durumunda ya da <xref:System.Threading.SemaphoreSlim.WaitAsync%2A?displayProperty=nameWithType> yöntemi <xref:System.Threading.SemaphoreSlim> olan semafor girer. Çağrı döndüğünde, semaforda sayı azaltılır. Bir iş parçacığı istediğinde ve sayı sıfır olduğunda, iş parçacığı engeller. İş parçacıkları veya metodunu çağırarak semaforu serbest bırakarak <xref:System.Threading.Semaphore.Release%2A?displayProperty=nameWithType> <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> engellenen iş parçacıklarının girmesine izin verilir. Engellenen iş parçacıkları için semaforu girmesi için ilk giriş, ilk çıkar (FıFO) veya son giriş, ilk çıkar (LıFO) gibi garantili bir sıra yoktur.  
  
 Bir iş parçacığı <xref:System.Threading.Semaphore?displayProperty=nameWithType> nesnenin <xref:System.Threading.WaitHandle.WaitOne%2A> metodunu ya da <xref:System.Threading.SemaphoreSlim> nesnenin <xref:System.Threading.SemaphoreSlim.Wait%2A> yöntemini sürekli çağırarak semaforu birden çok kez girebilir. Semaforu serbest bırakmak için, iş parçacığı <xref:System.Threading.Semaphore.Release?displayProperty=nameWithType> ya da <xref:System.Threading.SemaphoreSlim.Release?displayProperty=nameWithType> yöntem aşırı yüklemesini aynı sayıda çağırabilir veya <xref:System.Threading.Semaphore.Release%28System.Int32%29?displayProperty=nameWithType> ya da <xref:System.Threading.SemaphoreSlim.Release%28System.Int32%29?displayProperty=nameWithType> yöntem aşırı yüklemesini çağırabilir ve yayımlanacak girdi sayısını belirtebilir.  
  
### <a name="semaphores-and-thread-identity"></a>Semaforlar ve Iş parçacığı kimliği  
 İki semafor türü,,, <xref:System.Threading.WaitHandle.WaitOne%2A> <xref:System.Threading.SemaphoreSlim.Wait%2A> <xref:System.Threading.Semaphore.Release%2A> ve yöntemlerine yapılan çağrılar üzerinde iş parçacığı kimliğini zorlamaz <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> . Örneğin, Semaforlar için ortak bir kullanım senaryosunda bir üretici iş parçacığı ve bir tüketici iş parçacığı ve bir iş parçacığı her zaman semafor sayısını arttırılarak diğer her zaman azaltılır.  
  
 Bir iş parçacığının semaforu çok fazla kez serbest bırakmadığından emin olmak programcı sorumluluğundadır. Örneğin, bir semaforun en fazla iki sayısına sahip olduğunu ve A iş parçacığı A ve iş parçacığı B 'nin her ikisi de semaforu girmelerini sağladığını varsayalım. B iş parçacığında bir programlama hatası, iki kez çağrı yapmasına neden olursa `Release` her iki çağrı de başarılı olur. Semaforda bulunan sayı dolu ve iş parçacığı sonunda çağrı yaptığı zaman `Release` bir <xref:System.Threading.SemaphoreFullException> atılır.  
  
## <a name="named-semaphores"></a>Adlandırılmış Semaforlar  
 Windows işletim sistemi, Semaforlar adlara sahip olmasına izin verir. Adlandırılmış semafor sistem genelinde olur. Diğer bir deyişle, adlandırılmış semafor oluşturulduktan sonra, tüm süreçlerdeki tüm iş parçacıkları tarafından görülebilir. Bu nedenle, adlandırılmış semafor, işlem etkinliklerini ve iş parçacıklarını eşitlemesi için kullanılabilir.  
  
 <xref:System.Threading.Semaphore>Bir adı belirten oluşturuculardan birini kullanarak, adlandırılmış bir sistem semaforu temsil eden bir nesne oluşturabilirsiniz.  
  
> [!NOTE]
> Adlandırılmış Semaforlar sistem genelinde olduğundan, <xref:System.Threading.Semaphore> aynı adlı semaforu temsil eden birden çok nesne olması mümkündür. Her bir oluşturucuyu veya yöntemini her çağırdığınızda <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> Yeni bir <xref:System.Threading.Semaphore> nesne oluşturulur. Aynı adın belirtilmesi, aynı adlı semaforu temsil eden birden çok nesne oluşturur.  
  
 Adlandırılmış Semaforlar kullanırken dikkatli olun. Sistem genelinde olduklarından aynı adı kullanan başka bir işlem, semaforu beklenmedik bir şekilde girebilirler. Aynı bilgisayarda çalışan kötü amaçlı kod bunu bir hizmet reddi saldırısı temeli olarak kullanabilir.  
  
 <xref:System.Threading.Semaphore>Tercihen bir nesneyi belirten bir Oluşturucu kullanarak adlandırılmış semaforu temsil eden bir nesneyi korumak için erişim denetimi güvenliği ' ni kullanın <xref:System.Security.AccessControl.SemaphoreSecurity?displayProperty=nameWithType> . Yöntemi kullanarak erişim denetimi güvenliği de uygulayabilirsiniz <xref:System.Threading.Semaphore.SetAccessControl%2A?displayProperty=nameWithType> , ancak bu, semaforun oluşturulduğu zaman ve koruduğu zaman arasında bir güvenlik açığı penceresi bırakır. Erişim denetimi güvenliği ile Semaforlar koruma kötü amaçlı saldırıları önlemeye yardımcı olur, ancak istemeyerek ad çakışmalarının sorununu çözmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Semaphore>
- <xref:System.Threading.SemaphoreSlim>
- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)
