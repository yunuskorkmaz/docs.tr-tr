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
ms.openlocfilehash: 86376919d7456167c58ada4145d213b39e050e33
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46489113"
---
# <a name="eventwaithandle"></a>EventWaitHandle
<xref:System.Threading.EventWaitHandle> Sinyal ve sinyalleri için bekleyen birbirleri ile iletişim kurmak için iş parçacığı sınıfı sağlar. Olay bekleme tanıtıcıları (yalnızca olaylar olarak da bilinir) bir veya daha fazla bekleyen iş parçacıklarının serbest bırakmak için işareti bekleme tanıtıcıları ' dir. Bu sinyal sonra bir olay bekleme tanıtıcısı el ile veya otomatik olarak sıfırlanır. <xref:System.Threading.EventWaitHandle> Sınıfı ya da bir yerel olay bekleme tanıtıcısı (yerel olay) temsil edebilir veya adlandırılmış sistem olay işleyici (veya sistem olayın, tüm işlemler için görünür olarak adlandırılır) bekleyin.  
  
> [!NOTE]
>  Olay bekleme tanıtıcıları .NET olmayan [olayları](../events/index.md). Temsilciler ya da olay işleyicileri kullanılan vardır. "Olay" sözcük olduğundan, bunlar geleneksel için işletim sistemi olaylar olarak adlandırılmıştır ve bekleyen iş parçacığı bekleme tanıtıcısı sinyal eylemi belirttiğinden tanımlamak için bir olayın oluştuğunu kullanılır.  
  
 Sistem tarafından korunan eşitleme nesneleri hem yerel hem de adlandırılmış olay bekleme tanıtıcıları kullanan <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> sarmalayıcıları kaynakların serbest bırakıldığından emin olmak için. Kullanabileceğiniz <xref:System.Threading.WaitHandle.Dispose%2A> ne zaman, nesneyi kullanmayı bitirdikten hemen ücretsiz kaynaklar için yöntem.  
  
## <a name="event-wait-handles-that-reset-automatically"></a>Otomatik sıfırlama olay bekleme tanıtıcıları  
 Otomatik sıfırlama olay belirterek oluşturma <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> oluşturduğunuzda <xref:System.Threading.EventWaitHandle> nesne. Adından da anlaşılacağı gibi bu eşitleme olay tek bir bekleyen iş parçacığı bırakılıyor sonra sinyal olduğunda otomatik olarak sıfırlar. Çağırarak olayın sinyal kendi <xref:System.Threading.EventWaitHandle.Set%2A> yöntemi.  
  
 Otomatik sıfırlama olaylar genellikle bir kerede tek bir iş parçacığı için özel bir kaynağa erişim sağlamak için kullanılır. Bir iş parçacığı çağrı yaparak kaynak isteklerini <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemi. Başka bir iş parçacığı bekleme tanıtıcısı bulunduran ise, yöntem döndürür `true` ve çağıran iş parçacığını kaynak denetime sahiptir.  
  
> [!IMPORTANT]
>  Tüm eşitleme mekanizmaları gibi ile korunan bir kaynağa erişmeden önce tüm kod yolları üzerinde uygun bekleme tanıtıcısı bekleyin emin olmanız gerekir. İş parçacığı eşitleme ortaktır.  
  
 İş parçacığı beklenirken otomatik sıfırlama olaya sinyal vermediyse, bir iş parçacığı üzerinde bekleyin girişiminde bulunmadan sinyal kalır. Olay iş parçacığını serbest bırakır ve hemen sıfırlar, sonraki iş parçacığı engelleme.  
  
## <a name="event-wait-handles-that-reset-manually"></a>El ile Sıfırlanan olay bekleme tanıtıcıları  
 Belirterek elle sıfırlama olayı oluşturma <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> oluşturduğunuzda <xref:System.Threading.EventWaitHandle> nesne. Adından da anlaşılacağı gibi sinyal sonra bu eşitleme olay el ile sıfırlamanız gerekir. Bu, çağırarak sıfırlanana kadar kendi <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemi, olay tutamacı bekleyin iş parçacığı devam hemen engellemeden.  
  
 El ile bir corral, ağ geçidi gibi olay davranır sıfırlayın. Olaya sinyal gönderilmedi, içinde bir corral atları gibi iş parçacığı üzerinde bekleyin engelleyin. Ne zaman olayın sinyal, çağırarak kendi <xref:System.Threading.EventWaitHandle.Set%2A> yöntemi, tüm bekleyen iş parçacığı devam etmek ücretsiz. Olay kadar sinyal kalır, <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemi çağrılır. Bu elle sıfırlama olayı bir iş parçacığı bir görev bitene kadar beklemeniz gereken iş parçacıklarını tutmak için ideal bir yol sağlar.  
  
 Bir corral bırakarak atları gibi yayımlanmış iş parçacığı işletim sistemi tarafından zamanlanması ve yürütme devam etmek için zaman alır. Varsa <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemi, tüm iş parçacıklarının yürütülmesine devam ettirildi önce çağrılır, diğer iş parçacıkları yine engelleyin. Hangi iş parçacıklarını sürdürme ve hangi iş parçacıkları blok rastgele etkenlere bağlıdır, bu iş parçacığı sayısını sistemdeki yük gibi bekleyen Zamanlayıcı ve benzeri için. Olay sinyalini verir iş parçacığı en yaygın kullanım desenini olduğu sinyali sonra sona ererse, bir sorun değildir. Tüm bekleyen iş parçacığı devam ettirildi kadar tüm yeni göreve başlamak için bir olay iş parçacığı devam ettirildi bekleme sinyal iş parçacığı istiyorsanız engellemelidir. Aksi takdirde bir yarış durumu olması ve kodunuzu davranışını tahmin edilemez.  
  
## <a name="features-common-to-automatic-and-manual-events"></a>Otomatik ve el ile olaylar ortak özellikleri  
 Genellikle, bir veya daha fazla iş parçacığı engelleme üzerinde bir <xref:System.Threading.EventWaitHandle> engeli bir iş parçacığı çağrı kadar <xref:System.Threading.EventWaitHandle.Set%2A> bekleyen iş parçacıklarının (durumunda otomatik sıfırlama olayları) birini veya tümünü serbest yöntemi (olaylar olması durumunda el ile sıfırlama). Bir iş parçacığı sinyal verebilirsiniz bir <xref:System.Threading.EventWaitHandle> ve ardından bunun üzerinde bir atomik işlem olarak statik çağırarak engelle <xref:System.Threading.WaitHandle.SignalAndWait%2A?displayProperty=nameWithType> yöntemi.  
  
 <xref:System.Threading.EventWaitHandle> nesneleri ile statik kullanılabilir <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> yöntemleri. Çünkü <xref:System.Threading.EventWaitHandle> ve <xref:System.Threading.Mutex> sınıflarının her ikisi de türetilen <xref:System.Threading.WaitHandle>, bu yöntemlerle hem sınıflarını kullanabilirsiniz.  
  
### <a name="named-events"></a>Adlandırılmış olayları  
 Windows işletim sistemi olay bekleme tanıtıcıları adları olmasını sağlar. Sistem genelinde bir adlandırılmış olayıdır. Diğer bir deyişle, adlandırılmış olayı oluşturulduktan sonra tüm iş parçacıklarının tüm işlemler için görünür. Bu nedenle, adlandırılmış olaylar, işlemler ve bunun yanı sıra iş parçacıkları etkinlikleri eşitlemek için kullanılabilir.  
  
 Oluşturabileceğiniz bir <xref:System.Threading.EventWaitHandle> belirten bir olay adı oluşturucular birini kullanarak bir adlandırılmış sistem olayı temsil eden nesne.  
  
> [!NOTE]
>  Adlandırılmış olaylar Sistem genelinde olduğundan, birden çok mümkün <xref:System.Threading.EventWaitHandle> adlı olay aynı temsil eden nesneleri. Bir oluşturucu çağırmak her zaman veya <xref:System.Threading.EventWaitHandle.OpenExisting%2A> yöntemi, yeni bir <xref:System.Threading.EventWaitHandle> nesnesi oluşturulur. Tekrar tekrar aynı adı belirterek aynı adlandırılmış olayı temsil eden birden çok nesneleri oluşturur.  
  
 Olayları adlı kullanırken dikkatli olmanız önerilir. Aynı adı kullanan başka bir işlem, iş parçacıkları sistem genelinde olduklarından beklenmedik bir şekilde engelleyebilirsiniz. Kötü amaçlı kod aynı bilgisayarda çalıştırıldığında bu bir hizmet reddi saldırısı temel olarak kullanabilirsiniz.  
  
 Erişim denetimi güvenliği korumak için kullanmak bir <xref:System.Threading.EventWaitHandle> belirten bir kurucu kullanarak adlandırılmış bir olay tercihen temsil eden nesne bir <xref:System.Security.AccessControl.EventWaitHandleSecurity> nesne. Erişim denetimi güvenlik kullanarak uygulayabilirsiniz <xref:System.Threading.EventWaitHandle.SetAccessControl%2A> yöntemi, ancak bu bir güvenlik açığı korumalı zaman arasında olay bekleme tanıtıcısı oluşturulduğu zaman penceresi bırakır. Olayları koruma erişim denetimi ile güvenlik kötü amaçlı saldırıların önlenmesine yardımcı olur, ancak yanlışlıkla ad çakışması sorunu çözmez.  
  
> [!NOTE]
>  Farklı <xref:System.Threading.EventWaitHandle> türetilen sınıflar, sınıf <xref:System.Threading.AutoResetEvent> ve <xref:System.Threading.ManualResetEvent> temsil yalnızca yerel tutamaçlarını bekleyebileceği. Bunlar, adlandırılmış sistem olaylarını temsil edemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.EventWaitHandle>  
- <xref:System.Threading.WaitHandle>  
- <xref:System.Threading.AutoResetEvent>  
- <xref:System.Threading.ManualResetEvent>  
- [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
