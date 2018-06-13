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
ms.openlocfilehash: 697820b01bd629baa306d96002a98d92e44dab51
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592203"
---
# <a name="eventwaithandle"></a>EventWaitHandle
<xref:System.Threading.EventWaitHandle> Sınıfı, sinyal ve sinyalleri için bekleyen birbirleri ile iletişim kurmak için iş parçacığı olanak tanır. Olay bekleme tanıtıcıları (sadece olayları olarak da bilinir) bir veya daha fazla bekleyen iş parçacıklarının yayın için sinyal bekleme tanıtıcılarıdır. İşareti verilen sonra bir olay bekleme tanıtıcısı el ile veya otomatik olarak sıfırlanır. <xref:System.Threading.EventWaitHandle> Sınıfı ya da bir yerel olay bekleme tanıtıcısı (yerel olay) temsil eden veya bir adlandırılmış sistem olayı (olayı veya sistem olayı, tüm işlemler görünür olarak adlandırılır) tanıtıcısı bekleyin.  
  
> [!NOTE]
>  Olay bekleme tanıtıcıları olaylar genellikle bu word .NET Framework tarafından amacı herkese açık değildir. Hiçbir temsilciler veya olay işleyicileri ilgili vardır. Word "olay" çünkü bunlar geleneksel için işletim sistemi olayları olarak adlandırılmıştır ve bekleyen iş parçacığı bekleme tanıtıcısı sinyal eylemi gösterir çünkü tanımlamak için bir olay meydana kullanılır.  
  
 Hem yerel hem adlandırılmış olay bekleme tanıtıcıları tarafından korunan sistem eşitleme nesnelerin kullanımını <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> sarmalayıcıları kaynakları yayımlanan emin olun. Kullanabileceğiniz <xref:System.Threading.WaitHandle.Dispose%2A> zaman nesnesini kullanarak tamamladıktan hemen kaynakları serbest yöntemi.  
  
## <a name="event-wait-handles-that-reset-automatically"></a>Otomatik olarak sıfırla olay bekleme tanıtıcıları  
 Belirterek otomatik sıfırlama olay oluşturma <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> oluştururken <xref:System.Threading.EventWaitHandle> nesnesi. Adından da anlaşılacağı gibi bu eşitleme olay işaret, tek bir bekleyen iş parçacığı bırakılıyor sonra olduğunda otomatik olarak sıfırlar. Olay çağırarak sinyal kendi <xref:System.Threading.EventWaitHandle.Set%2A> yöntemi.  
  
 Otomatik sıfırlama olaylar, genellikle aynı anda tek bir iş parçacığı için özel bir kaynağa erişim sağlamak için kullanılır. Bir iş parçacığı çağırarak kaynak istekleri <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemi. Başka bir iş parçacığı bekleme tanıtıcısı tuttuğunu ise, yöntem `true` ve kaynak denetimi çağıran iş parçacığı vardır.  
  
> [!IMPORTANT]
>  Tüm eşitleme mekanizmaları olduğu gibi ile korunan bir kaynağa erişmeden önce tüm kod yollarının uygun bekleme tutamacı bekleyin emin olmalısınız. İş parçacığı eşitleme işbirlikçi olur.  
  
 İş parçacığı beklenirken otomatik sıfırlama olaya işaret edildiyse bir iş parçacığı üzerinde bekleyin girişiminde bulunmadan iş kalır. Olay iş parçacığı serbest bırakır ve hemen sonraki iş parçacığı engelleme sıfırlanır.  
  
## <a name="event-wait-handles-that-reset-manually"></a>El ile sıfırlama olay bekleme tanıtıcıları  
 Belirterek elle sıfırlama olayı oluşturma <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> oluştururken <xref:System.Threading.EventWaitHandle> nesnesi. Adından da anlaşılacağı gibi işaret edilene sonra bu eşitleme olay el ile sıfırlanması gerekir. Bu, çağırarak sıfırlanana kadar kendi <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemi, olay tutamacı bekleyin iş parçacığı hemen engellenmeden.  
  
 Ağ geçidi gibi bir corral olay olaylardan el ile sıfırlayın. Olay işaret değil, bir corral atları gibi üzerinde bekleyin iş parçacığı engelleyin. Ne zaman olay durdurulma, çağırarak kendi <xref:System.Threading.EventWaitHandle.Set%2A> yöntemi, tüm bekleyen iş parçacıklarının devam etmek boş. Olay kadar iş kalır, <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemi çağrılır. Bu elle sıfırlama olayı bir iş parçacığı bir görev sonlanana kadar beklemeniz gereken iş parçacıklarını tutmak için ideal bir yöntem sağlar.  
  
 Bir corral bırakarak atları gibi yayımlanmış iş parçacıkları işletim sistemi tarafından zamanlanacak ve yürütme devam etmek için zaman alır. Varsa <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemi, tüm iş parçacıklarının yürütülmesine ettirildi önce çağırılır, diğer iş parçacıkları kez yeniden engelleyin. Hangi iş parçacıklarını sürdürme ve hangi iş parçacığı blok rastgele etkenlere bağlıdır, iş parçacığı sayısını sistemindeki yük gibi bekleyen Zamanlayıcı vb. için. Olay sinyalleri iş parçacığı gönderildikten sonra en yaygın kullanım deseniyle olduğu sona ererse, bir sorun değildir. Yeni bir görev olsa başlamak için olay iş parçacığı devam ettirildi bekleme işaret iş parçacığı istiyorsanız, tüm bekleyen iş parçacıklarının devam ettirildi kadar engellemelidir. Aksi halde, bir yarış durumu sahip ve kodunuzu davranışını öngörülemeyen olur.  
  
## <a name="features-common-to-automatic-and-manual-events"></a>Otomatik ve el ile olayları ortak özellikler  
 Genellikle, bir veya daha fazla iş parçacığı engelleme üzerinde bir <xref:System.Threading.EventWaitHandle> engellenmemiş bir iş parçacığı çağırır kadar <xref:System.Threading.EventWaitHandle.Set%2A> bekleyen iş parçacıkları (durumunda otomatik sıfırlama olayları) birini veya bunların tümünün bırakır yöntemi (el ile söz konusu olduğunda olayları sıfırlama). Bir iş parçacığı sinyal bir <xref:System.Threading.EventWaitHandle> ve daha sonra bunun üzerinde atomik bir işlem olarak statik çağırarak engelleyebilirsiniz <xref:System.Threading.WaitHandle.SignalAndWait%2A?displayProperty=nameWithType> yöntemi.  
  
 <xref:System.Threading.EventWaitHandle> nesneleri ile statik kullanılabilir <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> yöntemleri. Çünkü <xref:System.Threading.EventWaitHandle> ve <xref:System.Threading.Mutex> sınıflarının her ikisi de türetilen <xref:System.Threading.WaitHandle>, her iki sınıf ile bu yöntemleri kullanabilirsiniz.  
  
### <a name="named-events"></a>Adlandırılmış olayları  
 Windows işletim sistemi olay bekleme tanıtıcıları adları olmasını sağlar. Sistem genelinde bir adlandırılmış olayıdır. Diğer bir deyişle, adlandırılmış olay oluşturulduktan sonra tüm iş parçacıkları, tüm işlemler için görünür durumdadır. Bu nedenle, adlandırılmış olayları etkinlikleri, işlemleri ve bunun yanı sıra iş parçacıklarını eşitleme için kullanılabilir.  
  
 Oluşturabileceğiniz bir <xref:System.Threading.EventWaitHandle> bir olay adı belirtir oluşturucular birini kullanarak bir adlandırılmış sistem olayı temsil eden nesne.  
  
> [!NOTE]
>  Adlandırılmış olayları sistem genelinde olduğundan, birden çok olma olasılığı vardır <xref:System.Threading.EventWaitHandle> aynı temsil eden nesneler adlı olay. Bir oluşturucu her çağırdığında veya <xref:System.Threading.EventWaitHandle.OpenExisting%2A> yöntemi, yeni bir <xref:System.Threading.EventWaitHandle> nesnesi oluşturulur. Aynı adı art arda belirterek aynı adlandırılmış olay temsil eden birden çok nesne oluşturur.  
  
 Uyarı olayları adlı kullanarak önerilir. Aynı adı kullanan başka bir işlem, iş parçacıkları sistem genelinde olduklarından beklenmedik bir şekilde engelleyebilirsiniz. Aynı bilgisayarda çalıştırılan kötü amaçlı kod bunu bir hizmet reddi saldırısı temel olarak kullanabilirsiniz.  
  
 Erişim denetimi güvenliği korumak için kullanmak bir <xref:System.Threading.EventWaitHandle> belirten bir kurucu kullanarak bir adlandırılmış olay tercihen temsil eden nesnesi bir <xref:System.Security.AccessControl.EventWaitHandleSecurity> nesnesi. Erişim denetimi güvenlik kullanarak uygulayabileceğiniz <xref:System.Threading.EventWaitHandle.SetAccessControl%2A> yöntemi, ancak bu bir güvenlik açığı olay bekleme tanıtıcısı oluşturulduğu zaman korunur zaman arasında pencerenin bırakır. Olayları koruma erişim denetimi ile güvenliği kötü amaçlı saldırıların önlenmesine yardımcı olur, ancak istenmeyen ad çakışması sorunu çözmez.  
  
> [!NOTE]
>  Farklı <xref:System.Threading.EventWaitHandle> sınıfı, türetilmiş sınıfları <xref:System.Threading.AutoResetEvent> ve <xref:System.Threading.ManualResetEvent> temsil yalnızca yerel tanıtıcıları bekleyebilirsiniz. Bunlar adlandırılmış sistem olayları temsil edilemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
