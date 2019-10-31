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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127582"
---
# <a name="semaphore-and-semaphoreslim"></a>Semafor ve SemaphoreSlim
<xref:System.Threading.Semaphore?displayProperty=nameWithType> sınıfı bir adlandırılmış (systemwide) veya yerel semaforu temsil eder. Bu, Win32 semafor nesnesinin etrafında ince bir sarmalayıcıdır. Win32 semaforları, bir kaynak havuzuna erişimi denetlemek için kullanılabilen semafor sayısını saymaktadır.  
  
 <xref:System.Threading.SemaphoreSlim> sınıfı, bekleme süreleri çok kısa olması beklendiğinde tek bir işlem içinde bekleme için kullanılabilen hafif ve hızlı bir semaforu temsil eder. <xref:System.Threading.SemaphoreSlim>, ortak dil çalışma zamanı (CLR) tarafından belirtilen eşitleme temelleri için mümkün olduğunca fazla kullanır. Bununla birlikte, Ayrıca, birden fazla semaforda beklemeyi desteklemek için gereken geç, çekirdek tabanlı bekleme tanıtıcıları de sağlar. <xref:System.Threading.SemaphoreSlim> Ayrıca iptal belirteçleri kullanımını destekler, ancak adlandırılmış semaforları veya eşitleme için bir bekleme tanıtıcısının kullanımını desteklemez.  
  
## <a name="managing-a-limited-resource"></a>Sınırlı bir kaynağı yönetme  
 İş parçacıkları, bir <xref:System.Threading.Semaphore?displayProperty=nameWithType> nesnesi veya <xref:System.Threading.SemaphoreSlim.Wait%2A?displayProperty=nameWithType> ya da <xref:System.Threading.SemaphoreSlim.WaitAsync%2A?displayProperty=nameWithType> yöntemi olması durumunda <xref:System.Threading.WaitHandle> sınıfından devralınan <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemini çağırarak semaforu girer. Çağrı döndüğünde, semaforda sayı azaltılır. Bir iş parçacığı istediğinde ve sayı sıfır olduğunda, iş parçacığı engeller. İş parçacıkları <xref:System.Threading.Semaphore.Release%2A?displayProperty=nameWithType> veya <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> yöntemini çağırarak semaforu serbest bırakarak engellenen iş parçacıklarının girmesine izin verilir. Engellenen iş parçacıkları için semaforu girmesi için ilk giriş, ilk çıkar (FıFO) veya son giriş, ilk çıkar (LıFO) gibi garantili bir sıra yoktur.  
  
 Bir iş parçacığı <xref:System.Threading.Semaphore?displayProperty=nameWithType> nesnenin <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemini veya <xref:System.Threading.SemaphoreSlim> nesnesinin <xref:System.Threading.SemaphoreSlim.Wait%2A> yöntemini tekrar çağırarak semaforu birden çok kez girebilir. Semaforu serbest bırakmak için, iş parçacığı <xref:System.Threading.Semaphore.Release?displayProperty=nameWithType> veya <xref:System.Threading.SemaphoreSlim.Release?displayProperty=nameWithType> metodu aynı sayıda kez aşırı yükleyebilir veya <xref:System.Threading.Semaphore.Release%28System.Int32%29?displayProperty=nameWithType> ya da <xref:System.Threading.SemaphoreSlim.Release%28System.Int32%29?displayProperty=nameWithType> yöntem aşırı yüklemesini çağırabilir ve yayımlanacak girdi sayısını belirtebilir.  
  
### <a name="semaphores-and-thread-identity"></a>Semaforlar ve Iş parçacığı kimliği  
 İki semafor türü, <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.SemaphoreSlim.Wait%2A>, <xref:System.Threading.Semaphore.Release%2A>ve <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> yöntemlerine yapılan çağrılar üzerinde iş parçacığı kimliğini zorlamaz. Örneğin, Semaforlar için ortak bir kullanım senaryosunda bir üretici iş parçacığı ve bir tüketici iş parçacığı ve bir iş parçacığı her zaman semafor sayısını arttırılarak diğer her zaman azaltılır.  
  
 Bir iş parçacığının semaforu çok fazla kez serbest bırakmadığından emin olmak programcı sorumluluğundadır. Örneğin, bir semaforun en fazla iki sayısına sahip olduğunu ve A iş parçacığı A ve iş parçacığı B 'nin her ikisi de semaforu girmelerini sağladığını varsayalım. B iş parçacığı içindeki bir programlama hatası `Release` iki kez çağırıyorsa, her iki çağrı de başarılı olur. Semaforda bulunan sayı dolu ve iş parçacığı sonunda `Release`çağırdığında bir <xref:System.Threading.SemaphoreFullException> oluşturulur.  
  
## <a name="named-semaphores"></a>Adlandırılmış Semaforlar  
 Windows işletim sistemi, Semaforlar adlara sahip olmasına izin verir. Adlandırılmış semafor sistem genelinde olur. Diğer bir deyişle, adlandırılmış semafor oluşturulduktan sonra, tüm süreçlerdeki tüm iş parçacıkları tarafından görülebilir. Bu nedenle, adlandırılmış semafor, işlem etkinliklerini ve iş parçacıklarını eşitlemesi için kullanılabilir.  
  
 Bir adı belirten oluşturuculardan birini kullanarak adlandırılmış bir sistem semaforu temsil eden bir <xref:System.Threading.Semaphore> nesnesi oluşturabilirsiniz.  
  
> [!NOTE]
> Adlandırılmış Semaforlar sistem genelinde olduğundan, aynı adlı semaforu temsil eden birden çok <xref:System.Threading.Semaphore> nesnesi olması mümkündür. Her bir oluşturucuyu veya <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> yöntemini her çağırdığınızda yeni bir <xref:System.Threading.Semaphore> nesnesi oluşturulur. Aynı adın belirtilmesi, aynı adlı semaforu temsil eden birden çok nesne oluşturur.  
  
 Adlandırılmış Semaforlar kullanırken dikkatli olun. Sistem genelinde olduklarından aynı adı kullanan başka bir işlem, semaforu beklenmedik bir şekilde girebilirler. Aynı bilgisayarda çalışan kötü amaçlı kod bunu bir hizmet reddi saldırısı temeli olarak kullanabilir.  
  
 Tercihen bir <xref:System.Security.AccessControl.SemaphoreSecurity?displayProperty=nameWithType> nesnesini belirten bir Oluşturucu kullanarak adlandırılmış semaforu temsil eden bir <xref:System.Threading.Semaphore> nesnesini korumak için erişim denetimi güvenliği kullanın. <xref:System.Threading.Semaphore.SetAccessControl%2A?displayProperty=nameWithType> yöntemi kullanarak erişim denetimi güvenliği de uygulayabilirsiniz, ancak bu, semaforun oluşturulduğu zaman ve koruduğu zaman arasında bir güvenlik açığı penceresi bırakır. Erişim denetimi güvenliği ile Semaforlar koruma kötü amaçlı saldırıları önlemeye yardımcı olur, ancak istemeyerek ad çakışmalarının sorununu çözmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Semaphore>
- <xref:System.Threading.SemaphoreSlim>
- [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)
