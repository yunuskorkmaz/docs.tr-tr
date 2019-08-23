---
title: EventWaitHandle
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], EventWaitHandle class
- EventWaitHandle class
- event wait handles [.NET Framework]
- threading [.NET Framework], cross-process synchronization
ms.assetid: 11ee0b38-d663-4617-b793-35eb6c64e9fc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d9c90a3bd272b54d2884d013e62123dd67d836e3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960047"
---
# <a name="eventwaithandle"></a>EventWaitHandle
Sınıfı <xref:System.Threading.EventWaitHandle> , iş parçacıklarının sinyalle ve sinyalleri beklemeden birbirleriyle iletişim kurmasına olanak tanır. Olay bekleme tutamaçları (yalnızca olaylar olarak da bilinir), bir veya daha fazla bekleyen iş parçacığını serbest bırakmak için sinyallenebilir bekleme tanıtıcılardır. Sinyalden sonra bir olay bekleme tutamacı el ile veya otomatik olarak sıfırlanır. <xref:System.Threading.EventWaitHandle> Sınıfı, yerel bir olay bekleme tanıtıcısını (yerel olay) veya adlandırılmış bir sistem olay bekleme işleyicisini (tüm işlemlere görünür) temsil edebilir.  
  
> [!NOTE]
> Olay bekleme tanıtıcıları .NET [olayları](../events/index.md)değildir. Dahil edilen temsilci veya olay işleyicisi yok. "Event" sözcüğü, geleneksel olarak işletim sistemi olayları olarak adlandırıldıklarından ve bekleme tanıtıcısını sinyal eden bir olayın gerçekleştiği iş parçacıklarını beklediğini gösterdiği için bunları anlatmak üzere kullanılır.  
  
 Hem yerel hem de adlandırılmış olay bekleme tanıtıcıları, kaynakların serbest bırakılacağını sağlamak için sarmalayıcılar <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> tarafından korunan sistem eşitleme nesnelerini kullanır. Nesnesini kullanmayı bitirdiğinizde kaynakları <xref:System.Threading.WaitHandle.Dispose%2A> hemen serbest bırakmak için yöntemini kullanabilirsiniz.  
  
## <a name="event-wait-handles-that-reset-automatically"></a>Olay bekleme tarafından otomatik olarak sıfırlanan Işleyiciler  
 <xref:System.Threading.EventWaitHandle> Nesneyi ne zaman oluşturduğunuzda belirterek <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> otomatik sıfırlama olayı oluşturursunuz. Adından da anlaşılacağı gibi, tek bir bekleyen iş parçacığı serbest bırakıldıktan sonra bu eşitleme olayı, sinyal edildiğinde otomatik olarak sıfırlanır. <xref:System.Threading.EventWaitHandle.Set%2A> Yöntemini çağırarak olayı sinyal edin.  
  
 Otomatik sıfırlama olayları genellikle tek bir iş parçacığı için bir kaynağa tek seferde özel erişim sağlamak için kullanılır. Bir iş parçacığı, <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemini çağırarak kaynağı ister. Bekleme tutamacını tutan başka bir iş parçacığı yoksa, yöntemi döndürür `true` ve çağıran iş parçacığı kaynağın denetimini içerir.  
  
> [!IMPORTANT]
> Tüm eşitleme mekanizmalarından itibaren, korunan bir kaynağa erişmeden önce tüm kod yollarının uygun bekleme tanıtıcısından beklediğinden emin olmanız gerekir. İş parçacığı eşitlemesi birlikte çalışır.  
  
 Hiçbir iş parçacığı beklenirken otomatik sıfırlama olayı sinyallidir, bir iş parçacığı beklemek istediğinde sinyal kalır. Olay iş parçacığını yayınlar ve sonraki iş parçacıklarını engellemeyi hemen sıfırlar.  
  
## <a name="event-wait-handles-that-reset-manually"></a>Olay bekleme tarafından el Ile sıfırlanan Işleyiciler  
 <xref:System.Threading.EventWaitHandle> Nesneyi ne zaman oluşturduğunuzda belirterek <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> el ile sıfırlama olayı oluşturursunuz. Adından da anlaşılacağı gibi, bu eşitleme olayının sinyalden sonra el ile sıfırlanması gerekir. Sıfırlanana kadar, <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemi çağırarak olay tanıtıcısını bekleyen iş parçacıkları doğrudan engellenmeden devam edilir.  
  
 El ile sıfırlama olayı bir Corral kapısı gibi davranır. Olay sinyalsiz olmadığında, Corral gibi, BT bloğunda bekleyen iş parçacıkları. Olaya işaret edildiğinde, <xref:System.Threading.EventWaitHandle.Set%2A> yöntemini çağırarak, bekleyen tüm iş parçacıkları devam etmek ücretsizdir. Olayı, <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemi çağrılana kadar sinyal olarak kalır. Bu, el ile sıfırlama olayını, bir iş parçacığının bir görevi bitirene kadar beklemesi gereken iş parçacıklarını tutmak için ideal bir yol haline getirir.  
  
 Corral atmaya benzer şekilde, yayınlanan iş parçacıklarının işletim sistemi tarafından zamanlanması ve yürütmeyi sürdürmek için zaman alır. <xref:System.Threading.EventWaitHandle.Reset%2A> Yöntemi, tüm iş parçacıklarının yürütmeyi sürdürmesinden önce çağrılırsa, kalan iş parçacıkları yeniden engellenir. Hangi iş parçacıkları sürdürecek ve hangi iş parçacıklarının engellenmesi, sistemdeki yük, Scheduler için bekleyen iş parçacıklarının sayısı vb. gibi rastgele faktörlere bağlıdır. Bu, olayı işaret eden iş parçacığı, en yaygın kullanım deseninin olduğu sinyalden sonra sona erdiğinde bu bir sorun değildir. Tüm bekleyen iş parçacıkları devam ettirdikten sonra olayı işaret eden bir iş parçacığının yeni bir göreve başlamasını istiyorsanız, tüm bekleyen iş parçacıkları sürdürülene kadar bunu engellemeniz gerekir. Aksi takdirde, bir yarış koşulunuz vardır ve kodunuzun davranışı tahmin edilemez.  
  
## <a name="features-common-to-automatic-and-manual-events"></a>Otomatik ve El Ile olaylar için ortak özellikler  
 Genellikle, engellenmemiş bir iş parçacığından birini <xref:System.Threading.EventWaitHandle> <xref:System.Threading.EventWaitHandle.Set%2A> çağıran bir veya daha fazla iş parçacığı, bekleyen iş parçacıklarından birini (otomatik sıfırlama olayları durumunda) veya tümünü (el ile sıfırlama olayları durumunda) yayınlar. Bir iş parçacığı bir <xref:System.Threading.EventWaitHandle> üzerinde sinyal verebilir ve sonra statik <xref:System.Threading.WaitHandle.SignalAndWait%2A?displayProperty=nameWithType> yöntemi çağırarak atomik bir işlem olarak bunu engelleyebilir.  
  
 <xref:System.Threading.EventWaitHandle>nesneler statik <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> yöntemlerle kullanılabilir. Ve <xref:System.Threading.WaitHandle> <xref:System.Threading.EventWaitHandle> sınıflarının<xref:System.Threading.Mutex> her ikisi de öğesinden türetilmediği için, her iki sınıfı da bu yöntemlerle kullanabilirsiniz.  
  
### <a name="named-events"></a>Adlandırılmış olaylar  
 Windows işletim sistemi, olay bekleme tanıtıcılarının adlara sahip olmasını sağlar. Adlandırılmış bir olay sistem genelinde olur. Diğer bir deyişle, adlandırılmış olay oluşturulduktan sonra tüm süreçlerdeki tüm iş parçacıkları tarafından görülebilir. Bu nedenle, adlandırılmış olaylar işlem etkinliklerini ve iş parçacıklarını eşitlemesi için kullanılabilir.  
  
 Bir olay adı belirten <xref:System.Threading.EventWaitHandle> oluşturuculardan birini kullanarak, adlandırılmış bir sistem olayını temsil eden bir nesne oluşturabilirsiniz.  
  
> [!NOTE]
> Adlandırılmış olaylar sistem genelinde olduğundan, aynı adlandırılmış olayı temsil eden birden çok <xref:System.Threading.EventWaitHandle> nesne olması mümkündür. Her bir oluşturucuyu veya <xref:System.Threading.EventWaitHandle.OpenExisting%2A> yöntemini her çağırdığınızda yeni <xref:System.Threading.EventWaitHandle> bir nesne oluşturulur. Aynı adın belirtilmesi, aynı adlandırılmış olayı temsil eden birden çok nesne oluşturur.  
  
 Uyarı, adlandırılmış olayları kullanmanın kullanılması önerilir. Sistem genelinde olduklarından aynı adı kullanan başka bir işlem, iş parçacıklarını beklenmedik şekilde engelleyebilir. Aynı bilgisayarda çalışan kötü amaçlı kod bunu bir hizmet reddi saldırısı temeli olarak kullanabilir.  
  
 Adlandırılmış bir olayı temsil eden bir <xref:System.Threading.EventWaitHandle> nesneyi, tercihen bir <xref:System.Security.AccessControl.EventWaitHandleSecurity> nesneyi belirten bir oluşturucuyu kullanarak korumak için erişim denetimi güvenliği ' ni kullanın. <xref:System.Threading.EventWaitHandle.SetAccessControl%2A> Yöntemi kullanarak erişim denetimi güvenliği de uygulayabilirsiniz, ancak bu, olay bekleme tutamacının oluşturulduğu zaman ve koruduğu zaman arasında bir güvenlik açığı penceresi bırakır. Erişim denetimi güvenliği ile olayları koruma kötü amaçlı saldırıları önlemeye yardımcı olur, ancak istemeden ad çakışmalarının sorununu çözmez.  
  
> [!NOTE]
> Sınıfından farklı olarak türetilmiş sınıflar <xref:System.Threading.AutoResetEvent> ve <xref:System.Threading.ManualResetEvent> yalnızca yerel bekleme tutamaçlarını temsil edebilir. <xref:System.Threading.EventWaitHandle> Adlandırılmış sistem olaylarını temsil edemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.EventWaitHandle>
- <xref:System.Threading.WaitHandle>
- <xref:System.Threading.AutoResetEvent>
- <xref:System.Threading.ManualResetEvent>
