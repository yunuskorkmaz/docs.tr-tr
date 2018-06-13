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
ms.openlocfilehash: 1f9c6df23ae1a142d208672a03ffeb74709a0a05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591318"
---
# <a name="semaphore-and-semaphoreslim"></a>Semafor ve SemaphoreSlim
<xref:System.Threading.Semaphore?displayProperty=nameWithType> Adlandırılmış (yükleyebilecek) veya yerel semafor sınıfı temsil eder. Win32 semafor nesne çevresinde ince bir sarmalayıcı değil. Win32 semafor, kaynak havuzu erişimi denetlemek için kullanılan semaforları sayma.  
  
 <xref:System.Threading.SemaphoreSlim> Sınıfı, bekleme süresini çok kısa olması beklenen zaman, tek bir işlem içinde bekleme için kullanılabilen bir basit, hızlı semafor temsil eder. <xref:System.Threading.SemaphoreSlim> Eşitleme temelleri ortak dil çalışma zamanı tarafından (CLR) sağlanan üzerinde mümkün olduğunca kullanır. Ancak, ayrıca gevşek başlatılmış, çekirdek tabanlı bekleme tanıtıcıları üzerinde birden fazla semafor bekleyen desteklemek için gereken sağlar. <xref:System.Threading.SemaphoreSlim> Semafor veya eşitleme bekleme tanıtıcısı kullanılmak adlı iptal belirteçlerini, ancak kullanımını desteklemediği de destekler.  
  
## <a name="managing-a-limited-resource"></a>Sınırlı kaynak yönetme  
 İş parçacığı çağırarak semafor girin <xref:System.Threading.WaitHandle.WaitOne%2A> kaynağından devralındı yöntemi <xref:System.Threading.WaitHandle> sınıfında durumunda bir <xref:System.Threading.Semaphore?displayProperty=nameWithType> nesnesi veya <xref:System.Threading.SemaphoreSlim.Wait%2A?displayProperty=nameWithType> veya <xref:System.Threading.SemaphoreSlim.WaitAsync%2A?displayProperty=nameWithType> durumunda yöntemi bir <xref:System.Threading.SemaphoreSlim> nesnesi... Semafor sayısına çağrısı döndürüldüğünde düşülür. Bir iş parçacığı sayısı ve girişi isteğinde bulunduğunda, iş parçacığı blokları sıfırdır. İş parçacığı semafor çağırarak çıkardıkça <xref:System.Threading.Semaphore.Release%2A?displayProperty=nameWithType> veya <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> yöntemi, engellenmiş iş parçacığı girin izin verilir. Semafor girmek engellenmiş iş parçacığı için ilk çıkar (FIFO) veya son giren ilk çıkar (LIFO) gibi hiçbir garanti edilen sipariş yoktur.  
  
 Bir iş parçacığı semafor birden çok kez çağırarak girebilirsiniz <xref:System.Threading.Semaphore?displayProperty=nameWithType> nesnenin <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemi veya <xref:System.Threading.SemaphoreSlim> nesnesinin <xref:System.Threading.SemaphoreSlim.Wait%2A> yöntemi art arda. İş parçacığı semafor serbest bırakmak için her iki arama yapabilirsiniz <xref:System.Threading.Semaphore.Release?displayProperty=nameWithType> veya <xref:System.Threading.SemaphoreSlim.Release?displayProperty=nameWithType> yöntemi aşırı aynı sayısı veya arama <xref:System.Threading.Semaphore.Release%28System.Int32%29?displayProperty=nameWithType> veya <xref:System.Threading.SemaphoreSlim.Release%28System.Int32%29?displayProperty=nameWithType> yöntemi aşırı yükleme ve yayımlanacak girdilerinin sayısını belirtin.  
  
### <a name="semaphores-and-thread-identity"></a>Semafor ve iş parçacığı kimliği  
 İki semafor türleri iş parçacığı kimliğine göre çağrıları zorlamaz <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.SemaphoreSlim.Wait%2A>, <xref:System.Threading.Semaphore.Release%2A>, ve <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> yöntemleri. Örneğin, genel bir kullanım senaryosu semafor içerir için bir üretici iş parçacığı ve tüketici bir iş parçacığı, her zaman semafor sayısı ve diğer her zaman azaltma artan bir iş parçacığı ile bu.  
  
 Bir iş parçacığı çok fazla kez semafor bırakmaz sağlamak Programcı sorumluluğundadır. Örneğin, en yüksek sayısı iki ve bu bir iş parçacığı ve iş parçacığı B semafor sahip olduğunu varsayın her ikisi de semafor girin. İş parçacığında B bir programlama hatası çağırmak neden olmadığını `Release` iki kez, her iki çağrılarının başarılı. Semafor sayısına dolu olduğunda ve ne zaman bir iş parçacığı sonunda çağırır `Release`, <xref:System.Threading.SemaphoreFullException> atılır.  
  
## <a name="named-semaphores"></a>Adlandırılmış semafor  
 Windows işletim sisteminin adlara sahip semafor sağlar. Adlandırılmış semafor geniş sistemidir. Diğer bir deyişle, adlandırılmış semafor oluşturulduktan sonra tüm iş parçacıkları, tüm işlemler için görünür durumdadır. Bu nedenle, adlandırılmış semafor etkinlikleri, işlemleri ve bunun yanı sıra iş parçacıklarını eşitleme için kullanılabilir.  
  
 Oluşturabileceğiniz bir <xref:System.Threading.Semaphore> bir ad belirtir oluşturucular birini kullanarak bir adlandırılmış sistem semafor temsil eden nesne.  
  
> [!NOTE]
>  Adlandırılmış semafor sistem genelinde olduğundan, birden çok olma olasılığı vardır <xref:System.Threading.Semaphore> aynı temsil eden nesneler adlı semafor. Her zaman bir oluşturucu çağrısı veya <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> yöntemi, yeni bir <xref:System.Threading.Semaphore> nesnesi oluşturulur. Aynı adı art arda belirterek aynı adlandırılmış semafor temsil eden birden çok nesne oluşturur.  
  
 Adlandırılmış semafor kullanırken dikkatli olun. Sistem genelinde oldukları için aynı adı kullanan başka bir işlem beklenmedik şekilde, semafor girebilirsiniz. Aynı bilgisayarda çalıştırılan kötü amaçlı kod bunu bir hizmet reddi saldırısı temel olarak kullanabilirsiniz.  
  
 Erişim denetimi güvenliği korumak için kullanmak bir <xref:System.Threading.Semaphore> belirten bir oluşturucu kullanılarak adlandırılmış semafor tercihen temsil eden nesnesi bir <xref:System.Security.AccessControl.SemaphoreSecurity?displayProperty=nameWithType> nesnesi. Erişim denetimi güvenlik kullanarak uygulayabileceğiniz <xref:System.Threading.Semaphore.SetAccessControl%2A?displayProperty=nameWithType> yöntemi, ancak bu bir güvenlik açığı semafor oluşturulduğu zaman korunur zaman arasında pencerenin bırakır. Erişim denetimi güvenliği ile semafor koruma kötü amaçlı saldırıların önlenmesine yardımcı olur, ancak istenmeyen ad çakışması sorunu çözmez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Semaphore>  
 <xref:System.Threading.SemaphoreSlim>  
 [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)
