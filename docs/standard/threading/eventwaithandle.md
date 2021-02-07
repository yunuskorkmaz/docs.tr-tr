---
description: 'Daha fazla bilgi edinin: EventWaitHandle'
title: EventWaitHandle
ms.date: 03/30/2017
helpviewer_keywords:
- threading [.NET], EventWaitHandle class
- EventWaitHandle class
- event wait handles [.NET]
- threading [.NET], cross-process synchronization
ms.assetid: 11ee0b38-d663-4617-b793-35eb6c64e9fc
ms.openlocfilehash: a1c5d9741cdcfa1313f0e7f1c0702954a93c6c09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666933"
---
# <a name="eventwaithandle"></a>EventWaitHandle

<xref:System.Threading.EventWaitHandle>Sınıfı, iş parçacıklarının sinyalle ve sinyalleri beklemeden birbirleriyle iletişim kurmasına olanak tanır. Olay bekleme tutamaçları (yalnızca olaylar olarak da bilinir), bir veya daha fazla bekleyen iş parçacığını serbest bırakmak için sinyallenebilir bekleme tanıtıcılardır. Sinyalden sonra bir olay bekleme tutamacı el ile veya otomatik olarak sıfırlanır. <xref:System.Threading.EventWaitHandle>Sınıfı, yerel bir olay bekleme tanıtıcısını (yerel olay) veya adlandırılmış bir sistem olay bekleme işleyicisini (tüm işlemlere görünür) temsil edebilir.  
  
> [!NOTE]
> Olay bekleme tanıtıcıları .NET [olayları](../events/index.md)değildir. Dahil edilen temsilci veya olay işleyicisi yok. "Event" sözcüğü, geleneksel olarak işletim sistemi olayları olarak adlandırıldıklarından ve bekleme tanıtıcısını sinyal eden bir olayın gerçekleştiği iş parçacıklarını beklediğini gösterdiği için bunları anlatmak üzere kullanılır.  
  
 Hem yerel hem de adlandırılmış olay bekleme tanıtıcıları, <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> kaynakların serbest bırakılacağını sağlamak için sarmalayıcılar tarafından korunan sistem eşitleme nesnelerini kullanır. <xref:System.Threading.WaitHandle.Dispose%2A>Nesnesini kullanmayı bitirdiğinizde kaynakları hemen serbest bırakmak için yöntemini kullanabilirsiniz.  
  
## <a name="event-wait-handles-that-reset-automatically"></a>Olay bekleme tarafından otomatik olarak sıfırlanan Işleyiciler  

 <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType>Nesneyi ne zaman oluşturduğunuzda belirterek otomatik sıfırlama olayı oluşturursunuz <xref:System.Threading.EventWaitHandle> . Adından da anlaşılacağı gibi, tek bir bekleyen iş parçacığı serbest bırakıldıktan sonra bu eşitleme olayı, sinyal edildiğinde otomatik olarak sıfırlanır. Yöntemini çağırarak olayı sinyal edin <xref:System.Threading.EventWaitHandle.Set%2A> .  
  
 Otomatik sıfırlama olayları genellikle tek bir iş parçacığı için bir kaynağa tek seferde özel erişim sağlamak için kullanılır. Bir iş parçacığı, yöntemini çağırarak kaynağı ister <xref:System.Threading.WaitHandle.WaitOne%2A> . Bekleme tutamacını tutan başka bir iş parçacığı yoksa, yöntemi döndürür `true` ve çağıran iş parçacığı kaynağın denetimini içerir.  
  
> [!IMPORTANT]
> Tüm eşitleme mekanizmalarından itibaren, korunan bir kaynağa erişmeden önce tüm kod yollarının uygun bekleme tanıtıcısından beklediğinden emin olmanız gerekir. İş parçacığı eşitlemesi birlikte çalışır.  
  
 Hiçbir iş parçacığı beklenirken otomatik sıfırlama olayı sinyallidir, bir iş parçacığı beklemek istediğinde sinyal kalır. Olay iş parçacığını yayınlar ve sonraki iş parçacıklarını engellemeyi hemen sıfırlar.  
  
## <a name="event-wait-handles-that-reset-manually"></a>Olay bekleme tarafından el Ile sıfırlanan Işleyiciler  

 <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType>Nesneyi ne zaman oluşturduğunuzda belirterek el ile sıfırlama olayı oluşturursunuz <xref:System.Threading.EventWaitHandle> . Adından da anlaşılacağı gibi, bu eşitleme olayının sinyalden sonra el ile sıfırlanması gerekir. Sıfırlanana kadar, <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemi çağırarak olay tanıtıcısını bekleyen iş parçacıkları doğrudan engellenmeden devam edilir.  
  
 El ile sıfırlama olayı bir Corral kapısı gibi davranır. Olay sinyalsiz olmadığında, Corral gibi, BT bloğunda bekleyen iş parçacıkları. Olaya işaret edildiğinde, yöntemini çağırarak, <xref:System.Threading.EventWaitHandle.Set%2A> bekleyen tüm iş parçacıkları devam etmek ücretsizdir. Olayı, <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemi çağrılana kadar sinyal olarak kalır. Bu, el ile sıfırlama olayını, bir iş parçacığının bir görevi bitirene kadar beklemesi gereken iş parçacıklarını tutmak için ideal bir yol haline getirir.  
  
 Corral atmaya benzer şekilde, yayınlanan iş parçacıklarının işletim sistemi tarafından zamanlanması ve yürütmeyi sürdürmek için zaman alır. Yöntemi, <xref:System.Threading.EventWaitHandle.Reset%2A> tüm iş parçacıklarının yürütmeyi sürdürmesinden önce çağrılırsa, kalan iş parçacıkları yeniden engellenir. Hangi iş parçacıkları sürdürecek ve hangi iş parçacıklarının engellenmesi, sistemdeki yük, Scheduler için bekleyen iş parçacıklarının sayısı vb. gibi rastgele faktörlere bağlıdır. Bu, olayı işaret eden iş parçacığı, en yaygın kullanım deseninin olduğu sinyalden sonra sona erdiğinde bu bir sorun değildir. Tüm bekleyen iş parçacıkları devam ettirdikten sonra olayı işaret eden bir iş parçacığının yeni bir göreve başlamasını istiyorsanız, tüm bekleyen iş parçacıkları sürdürülene kadar bunu engellemeniz gerekir. Aksi takdirde, bir yarış koşulunuz vardır ve kodunuzun davranışı tahmin edilemez.  
  
## <a name="features-common-to-automatic-and-manual-events"></a>Otomatik ve El Ile olaylar için ortak özellikler  

 Genellikle, engellenmemiş bir iş parçacığından birini çağıran bir veya daha fazla iş parçacığı, <xref:System.Threading.EventWaitHandle> <xref:System.Threading.EventWaitHandle.Set%2A> bekleyen iş parçacıklarından birini (otomatik sıfırlama olayları durumunda) veya tümünü (el ile sıfırlama olayları durumunda) yayınlar. Bir iş parçacığı bir üzerinde sinyal verebilir <xref:System.Threading.EventWaitHandle> ve sonra statik yöntemi çağırarak atomik bir işlem olarak bunu engelleyebilir <xref:System.Threading.WaitHandle.SignalAndWait%2A?displayProperty=nameWithType> .  
  
 <xref:System.Threading.EventWaitHandle> nesneler statik <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> yöntemlerle kullanılabilir. <xref:System.Threading.EventWaitHandle>Ve <xref:System.Threading.Mutex> sınıflarının her ikisi de öğesinden türetilmediği için <xref:System.Threading.WaitHandle> , her iki sınıfı da bu yöntemlerle kullanabilirsiniz.  
  
### <a name="named-events"></a>Adlandırılmış olaylar  

 Windows işletim sistemi, olay bekleme tanıtıcılarının adlara sahip olmasını sağlar. Adlandırılmış bir olay sistem genelinde olur. Diğer bir deyişle, adlandırılmış olay oluşturulduktan sonra tüm süreçlerdeki tüm iş parçacıkları tarafından görülebilir. Bu nedenle, adlandırılmış olaylar işlem etkinliklerini ve iş parçacıklarını eşitlemesi için kullanılabilir.  
  
 <xref:System.Threading.EventWaitHandle>Bir olay adı belirten oluşturuculardan birini kullanarak, adlandırılmış bir sistem olayını temsil eden bir nesne oluşturabilirsiniz.  
  
> [!NOTE]
> Adlandırılmış olaylar sistem genelinde olduğundan, <xref:System.Threading.EventWaitHandle> aynı adlandırılmış olayı temsil eden birden çok nesne olması mümkündür. Her bir oluşturucuyu veya yöntemini her çağırdığınızda <xref:System.Threading.EventWaitHandle.OpenExisting%2A> Yeni bir <xref:System.Threading.EventWaitHandle> nesne oluşturulur. Aynı adın belirtilmesi, aynı adlandırılmış olayı temsil eden birden çok nesne oluşturur.  
  
 Uyarı, adlandırılmış olayları kullanmanın kullanılması önerilir. Sistem genelinde olduklarından aynı adı kullanan başka bir işlem, iş parçacıklarını beklenmedik şekilde engelleyebilir. Aynı bilgisayarda çalışan kötü amaçlı kod bunu bir hizmet reddi saldırısı temeli olarak kullanabilir.  
  
 <xref:System.Threading.EventWaitHandle>Adlandırılmış bir olayı temsil eden bir nesneyi, tercihen bir nesneyi belirten bir oluşturucuyu kullanarak korumak için erişim denetimi güvenliği ' ni kullanın <xref:System.Security.AccessControl.EventWaitHandleSecurity> . Yöntemi kullanarak erişim denetimi güvenliği de uygulayabilirsiniz <xref:System.Threading.EventWaitHandle.SetAccessControl%2A> , ancak bu, olay bekleme tutamacının oluşturulduğu zaman ve koruduğu zaman arasında bir güvenlik açığı penceresi bırakır. Erişim denetimi güvenliği ile olayları koruma kötü amaçlı saldırıları önlemeye yardımcı olur, ancak istemeden ad çakışmalarının sorununu çözmez.  
  
> [!NOTE]
> Sınıfından farklı olarak <xref:System.Threading.EventWaitHandle> türetilmiş sınıflar <xref:System.Threading.AutoResetEvent> ve <xref:System.Threading.ManualResetEvent> yalnızca yerel bekleme tutamaçlarını temsil edebilir. Adlandırılmış sistem olaylarını temsil edemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.EventWaitHandle>
- <xref:System.Threading.WaitHandle>
- <xref:System.Threading.AutoResetEvent>
- <xref:System.Threading.ManualResetEvent>
