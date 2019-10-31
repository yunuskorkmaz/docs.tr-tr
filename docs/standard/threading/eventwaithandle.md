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
ms.openlocfilehash: 80c90254978495a58d228c4302eda84d6165c800
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138070"
---
# <a name="eventwaithandle"></a>EventWaitHandle
<xref:System.Threading.EventWaitHandle> sınıfı, iş parçacıklarının sinyalle ve sinyalleri beklemeden birbirleriyle iletişim kurmasına olanak tanır. Olay bekleme tutamaçları (yalnızca olaylar olarak da bilinir), bir veya daha fazla bekleyen iş parçacığını serbest bırakmak için sinyallenebilir bekleme tanıtıcılardır. Sinyalden sonra bir olay bekleme tutamacı el ile veya otomatik olarak sıfırlanır. <xref:System.Threading.EventWaitHandle> sınıfı, yerel bir olay bekleme tanıtıcısını (yerel olay) veya adlandırılmış bir sistem olay bekleme işleyicisini (tüm işlemlere görünür) temsil edebilir.  
  
> [!NOTE]
> Olay bekleme tanıtıcıları .NET [olayları](../events/index.md)değildir. Dahil edilen temsilci veya olay işleyicisi yok. "Event" sözcüğü, geleneksel olarak işletim sistemi olayları olarak adlandırıldıklarından ve bekleme tanıtıcısını sinyal eden bir olayın gerçekleştiği iş parçacıklarını beklediğini gösterdiği için bunları anlatmak üzere kullanılır.  
  
 Hem yerel hem de adlandırılmış olay bekleme tanıtıcıları, kaynakların serbest bırakılacağını sağlamak üzere <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> sarmalayıcılar tarafından korunan sistem eşitleme nesnelerini kullanır. Nesnesini kullanmayı bitirdiğinizde kaynakları hemen serbest bırakmak için <xref:System.Threading.WaitHandle.Dispose%2A> yöntemini kullanabilirsiniz.  
  
## <a name="event-wait-handles-that-reset-automatically"></a>Olay bekleme tarafından otomatik olarak sıfırlanan Işleyiciler  
 <xref:System.Threading.EventWaitHandle> nesnesini oluştururken <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> belirterek otomatik sıfırlama olayı oluşturursunuz. Adından da anlaşılacağı gibi, tek bir bekleyen iş parçacığı serbest bırakıldıktan sonra bu eşitleme olayı, sinyal edildiğinde otomatik olarak sıfırlanır. <xref:System.Threading.EventWaitHandle.Set%2A> yöntemini çağırarak olayı sinyal edin.  
  
 Otomatik sıfırlama olayları genellikle tek bir iş parçacığı için bir kaynağa tek seferde özel erişim sağlamak için kullanılır. Bir iş parçacığı <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemini çağırarak kaynağı ister. Bekleme tutamacını tutan başka bir iş parçacığı yoksa, yöntem `true` döndürür ve çağıran iş parçacığı kaynağın denetimini içerir.  
  
> [!IMPORTANT]
> Tüm eşitleme mekanizmalarından itibaren, korunan bir kaynağa erişmeden önce tüm kod yollarının uygun bekleme tanıtıcısından beklediğinden emin olmanız gerekir. İş parçacığı eşitlemesi birlikte çalışır.  
  
 Hiçbir iş parçacığı beklenirken otomatik sıfırlama olayı sinyallidir, bir iş parçacığı beklemek istediğinde sinyal kalır. Olay iş parçacığını yayınlar ve sonraki iş parçacıklarını engellemeyi hemen sıfırlar.  
  
## <a name="event-wait-handles-that-reset-manually"></a>Olay bekleme tarafından el Ile sıfırlanan Işleyiciler  
 <xref:System.Threading.EventWaitHandle> nesnesini oluştururken <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> belirterek el ile sıfırlama olayı oluşturursunuz. Adından da anlaşılacağı gibi, bu eşitleme olayının sinyalden sonra el ile sıfırlanması gerekir. Sıfırlanana kadar, <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemini çağırarak olay işleyicide bekleyen iş parçacıkları doğrudan engellenmeksizin devam edilir.  
  
 El ile sıfırlama olayı bir Corral kapısı gibi davranır. Olay sinyalsiz olmadığında, Corral gibi, BT bloğunda bekleyen iş parçacıkları. Olaya işaret edildiğinde, <xref:System.Threading.EventWaitHandle.Set%2A> yöntemini çağırarak, bekleyen tüm iş parçacıkları devam etmek ücretsizdir. Olay <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemi çağrılana kadar sinyal olarak kalır. Bu, el ile sıfırlama olayını, bir iş parçacığının bir görevi bitirene kadar beklemesi gereken iş parçacıklarını tutmak için ideal bir yol haline getirir.  
  
 Corral atmaya benzer şekilde, yayınlanan iş parçacıklarının işletim sistemi tarafından zamanlanması ve yürütmeyi sürdürmek için zaman alır. <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemi, tüm iş parçacıklarının yürütülmesi sürdürülmesinden önce çağrılırsa, kalan iş parçacıkları bir kez daha engellenir. Hangi iş parçacıkları sürdürecek ve hangi iş parçacıklarının engellenmesi, sistemdeki yük, Scheduler için bekleyen iş parçacıklarının sayısı vb. gibi rastgele faktörlere bağlıdır. Bu, olayı işaret eden iş parçacığı, en yaygın kullanım deseninin olduğu sinyalden sonra sona erdiğinde bu bir sorun değildir. Tüm bekleyen iş parçacıkları devam ettirdikten sonra olayı işaret eden bir iş parçacığının yeni bir göreve başlamasını istiyorsanız, tüm bekleyen iş parçacıkları sürdürülene kadar bunu engellemeniz gerekir. Aksi takdirde, bir yarış koşulunuz vardır ve kodunuzun davranışı tahmin edilemez.  
  
## <a name="features-common-to-automatic-and-manual-events"></a>Otomatik ve El Ile olaylar için ortak özellikler  
 Genellikle, bir veya daha fazla iş parçacığı, engeli kaldırılmış bir iş parçacığından (otomatik sıfırlama olayları durumunda) veya tümünün (el ile sıfırlama olayları durumunda) bir tane olan <xref:System.Threading.EventWaitHandle.Set%2A> yöntemini çağırana kadar bir <xref:System.Threading.EventWaitHandle> engeller. Bir iş parçacığı bir <xref:System.Threading.EventWaitHandle> işaret edebilir ve ardından statik <xref:System.Threading.WaitHandle.SignalAndWait%2A?displayProperty=nameWithType> yöntemini çağırarak atomik bir işlem olarak bunu engelleyebilir.  
  
 <xref:System.Threading.EventWaitHandle> nesneleri statik <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> yöntemleriyle birlikte kullanılabilir. <xref:System.Threading.EventWaitHandle> ve <xref:System.Threading.Mutex> sınıfları her ikisi de <xref:System.Threading.WaitHandle>türetiğinden, bu yöntemlerle her iki sınıfı da kullanabilirsiniz.  
  
### <a name="named-events"></a>Adlandırılmış olaylar  
 Windows işletim sistemi, olay bekleme tanıtıcılarının adlara sahip olmasını sağlar. Adlandırılmış bir olay sistem genelinde olur. Diğer bir deyişle, adlandırılmış olay oluşturulduktan sonra tüm süreçlerdeki tüm iş parçacıkları tarafından görülebilir. Bu nedenle, adlandırılmış olaylar işlem etkinliklerini ve iş parçacıklarını eşitlemesi için kullanılabilir.  
  
 Bir olay adı belirten oluşturuculardan birini kullanarak, adlandırılmış bir sistem olayını temsil eden bir <xref:System.Threading.EventWaitHandle> nesnesi oluşturabilirsiniz.  
  
> [!NOTE]
> Adlandırılmış olaylar sistem genelinde olduğundan, aynı adlandırılmış olayı temsil eden birden çok <xref:System.Threading.EventWaitHandle> nesnesi olması mümkündür. Her bir oluşturucuyu veya <xref:System.Threading.EventWaitHandle.OpenExisting%2A> yöntemini her çağırdığınızda yeni bir <xref:System.Threading.EventWaitHandle> nesnesi oluşturulur. Aynı adın belirtilmesi, aynı adlandırılmış olayı temsil eden birden çok nesne oluşturur.  
  
 Uyarı, adlandırılmış olayları kullanmanın kullanılması önerilir. Sistem genelinde olduklarından aynı adı kullanan başka bir işlem, iş parçacıklarını beklenmedik şekilde engelleyebilir. Aynı bilgisayarda çalışan kötü amaçlı kod bunu bir hizmet reddi saldırısı temeli olarak kullanabilir.  
  
 Adlandırılmış bir olayı temsil eden bir <xref:System.Threading.EventWaitHandle> nesnesini, tercihen bir <xref:System.Security.AccessControl.EventWaitHandleSecurity> nesnesini belirten bir oluşturucuyu kullanarak korumak için erişim denetimi güvenliği ' ni kullanın. <xref:System.Threading.EventWaitHandle.SetAccessControl%2A> yöntemi kullanarak erişim denetimi güvenliği de uygulayabilirsiniz, ancak bu durum, olay bekleme tutamacının oluşturulduğu zaman ve koruduğu zaman arasında bir güvenlik açığı penceresi bırakır. Erişim denetimi güvenliği ile olayları koruma kötü amaçlı saldırıları önlemeye yardımcı olur, ancak istemeden ad çakışmalarının sorununu çözmez.  
  
> [!NOTE]
> <xref:System.Threading.EventWaitHandle> sınıfından farklı olarak, türetilmiş sınıflar <xref:System.Threading.AutoResetEvent> ve <xref:System.Threading.ManualResetEvent> yalnızca yerel bekleme tutamaçlarını temsil edebilir. Adlandırılmış sistem olaylarını temsil edemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.EventWaitHandle>
- <xref:System.Threading.WaitHandle>
- <xref:System.Threading.AutoResetEvent>
- <xref:System.Threading.ManualResetEvent>
