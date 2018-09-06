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
ms.openlocfilehash: 8e98862aba937724c799adef597260a06ed495f6
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871283"
---
# <a name="semaphore-and-semaphoreslim"></a>Semafor ve SemaphoreSlim
<xref:System.Threading.Semaphore?displayProperty=nameWithType> Adlandırılmış (yükleyebilecek) veya yerel semafor sınıfını temsil eder. Win32 semafor nesne çevresinde ince bir sarmalayıcıdır. Win32 semaforları bir kaynak havuzu erişimi denetlemek için kullanılabilen semaforları sayma.  
  
 <xref:System.Threading.SemaphoreSlim> Sınıf bekleme süresini çok kısa olması beklendiğinde, tek bir işlem içinde bekleme için kullanılabilecek basit ve hızlı bir semaforu temsil eder. <xref:System.Threading.SemaphoreSlim> Eşitleme temellerine ortak dil çalışma (CLR) tarafından sağlanan üzerinde mümkün olduğunca kullanır. Ancak, ayrıca gevşek başlatılmış, çekirdek tabanlı bekleme tanıtıcıları üzerinde birden fazla semaforları bekleyen desteklemek için gerekli olarak sağlar. <xref:System.Threading.SemaphoreSlim> Semafor veya eşitleme bekleme tanıtıcısı kullanımını adlı iptal belirteçlerini, ancak kullanımını desteklemediği de destekler.  
  
## <a name="managing-a-limited-resource"></a>Sınırlı kaynak yönetme  
 İş parçacıkları çağırarak semafor girin <xref:System.Threading.WaitHandle.WaitOne%2A> devralındı yöntemi <xref:System.Threading.WaitHandle> durumunda sınıfı bir <xref:System.Threading.Semaphore?displayProperty=nameWithType> nesnesi veya <xref:System.Threading.SemaphoreSlim.Wait%2A?displayProperty=nameWithType> veya <xref:System.Threading.SemaphoreSlim.WaitAsync%2A?displayProperty=nameWithType> yönteminde büyük bir <xref:System.Threading.SemaphoreSlim> nesne... Semafor sayısına çağrısı döndürüldüğünde azaltılır. Bir iş parçacığı girişini ve sayısı istediğinde, iş parçacığı blokları sıfırdır. İş parçacıkları semafor çağırarak serbest olarak <xref:System.Threading.Semaphore.Release%2A?displayProperty=nameWithType> veya <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> yöntemi, engellenen iş parçacıkları girin izin verilir. Semafor girmek engellenen iş parçacıkları için ilk giren ilk çıkar (FIFO) veya son giren ilk çıkar (LIFO) gibi yürütülme sırası yoktur.  
  
 Bir iş parçacığı semafor birden çok kez çağırarak girebilirsiniz <xref:System.Threading.Semaphore?displayProperty=nameWithType> nesnenin <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemi veya <xref:System.Threading.SemaphoreSlim> nesnenin <xref:System.Threading.SemaphoreSlim.Wait%2A> yöntemi tekrar tekrar. İş parçacığı semafor yayımlamayı çağrısı yapabilirsiniz <xref:System.Threading.Semaphore.Release?displayProperty=nameWithType> veya <xref:System.Threading.SemaphoreSlim.Release?displayProperty=nameWithType> yöntemi aşırı yüklemek, aynı sayıda veya çağrı <xref:System.Threading.Semaphore.Release%28System.Int32%29?displayProperty=nameWithType> veya <xref:System.Threading.SemaphoreSlim.Release%28System.Int32%29?displayProperty=nameWithType> yöntemi aşırı yüklemesini ve yayımlanacak giriş sayısını belirtin.  
  
### <a name="semaphores-and-thread-identity"></a>Semafor ve iş parçacığı kimliği  
 İki semafor türleri için çağrılar üzerinde iş parçacığı kimliğini zorlama <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.SemaphoreSlim.Wait%2A>, <xref:System.Threading.Semaphore.Release%2A>, ve <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> yöntemleri. Örneğin, genel bir kullanım senaryosu semaforları içerir için bir üretici iş parçacığı ve tüketici bir iş parçacığı, her zaman semafor sayı ve diğer her zaman azaltma artan bir iş parçacığı ile.  
  
 Bir iş parçacığı çok fazla kez semafor bırakmaz olun programcının sorumluluğundadır. Örneğin, en fazla iki ve bu iş parçacığı A ve B iş parçacığı sayısını semafor sahip olduğunu varsayın hem semafor girin. Bir programlama hatası iş parçacığında B çağıracak şekilde neden olursa `Release` iki kez, her iki çağrıda başarısız. Semafor sayısına dolu olduğu ve ne zaman bir iş parçacığı sonunda çağırır `Release`, <xref:System.Threading.SemaphoreFullException> oluşturulur.  
  
## <a name="named-semaphores"></a>Adlandırılmış semafor  
 Windows işletim sistemi adlara sahip semaforları sağlar. Adlandırılmış semafor geniş sistemidir. Diğer bir deyişle, adlandırılmış semafor oluşturulduktan sonra tüm iş parçacıklarının tüm işlemler için görünür. Bu nedenle, adlandırılmış semafor işlemlerin yanı sıra iş parçacıkları etkinlikleri eşitlemek için kullanılabilir.  
  
 Oluşturabileceğiniz bir <xref:System.Threading.Semaphore> bir ad belirtir oluşturucular birini kullanarak bir adlandırılmış sistem semaforu temsil eden nesne.  
  
> [!NOTE]
>  Adlandırılmış semaforları sistem genelinde olduğundan, birden çok mümkün <xref:System.Threading.Semaphore> adlı semafor aynı temsil eden nesneleri. Her zaman bir oluşturucu çağırmanız veya <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> yöntemi, yeni bir <xref:System.Threading.Semaphore> nesnesi oluşturulur. Tekrar tekrar aynı adı belirterek, aynı adlı semaforu temsil eden birden çok nesneleri oluşturur.  
  
 Adlandırılmış semaforları kullanırken dikkatli olun. Sistem genelinde oldukları için aynı adı kullanan başka bir işlem, semafor beklenmedik bir şekilde girebilirsiniz. Kötü amaçlı kod aynı bilgisayarda çalıştırıldığında bu bir hizmet reddi saldırısı temel olarak kullanabilirsiniz.  
  
 Erişim denetimi güvenliği korumak için kullanmak bir <xref:System.Threading.Semaphore> tercihen belirten bir kurucu kullanarak adlandırılmış bir semaforu temsil eden nesne bir <xref:System.Security.AccessControl.SemaphoreSecurity?displayProperty=nameWithType> nesne. Erişim denetimi güvenlik kullanarak uygulayabilirsiniz <xref:System.Threading.Semaphore.SetAccessControl%2A?displayProperty=nameWithType> yöntemi, ancak bu bir pencere semafor oluşturulduğu zaman korunur zaman arasında güvenlik açığı bırakır. Erişim denetimi güvenliği ile semaforları koruma kötü amaçlı saldırıları önlemeye yardımcı olur, ancak yanlışlıkla ad çakışmalarının sorunu çözmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Semaphore>  
- <xref:System.Threading.SemaphoreSlim>  
- [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)
