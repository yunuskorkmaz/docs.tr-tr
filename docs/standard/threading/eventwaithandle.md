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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138070"
---
# <a name="eventwaithandle"></a>EventWaitHandle
Sınıf, <xref:System.Threading.EventWaitHandle> iş parçacıklarının sinyal vererek ve sinyalleri bekleyerek birbirleriyle iletişim kurmasını sağlar. Olay bekleme tutamaçları (yalnızca olaylar olarak da adlandırılır) bir veya daha fazla bekleyen iş parçacığı serbest bırakmak için sinyal verilebilen bekleme tutamaçlarıdır. Sinyal edildikten sonra, olay bekleme tutamacı el ile veya otomatik olarak sıfırlanır. Sınıf, <xref:System.Threading.EventWaitHandle> yerel bir olay bekleme tanıtıcısını (yerel olay) veya adlandırılmış bir sistem olayı bekleme tutamacını (adı verilen olay veya sistem olayı, tüm işlemler tarafından görülebilir) temsil edebilir.  
  
> [!NOTE]
> Olay bekleme tutamaçları .NET [olayları](../events/index.md)değildir. İşin içinde temsilci veya olay işleyicisi yok. "Olay" sözcüğü, geleneksel olarak işletim sistemi olayları olarak adlandırıldıkları ve bekleme tutamacını işaret etme eylemi bir olayın oluştuğunu bekleyen iş parçacıklarına işaret ettiği için bunları tanımlamak için kullanılır.  
  
 Hem yerel hem de adlandırılmış olay bekleme işleyicileri, <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> kaynakların serbest bırakılmasını sağlamak için sarmalayıcılar tarafından korunan sistem eşitleme nesnelerini kullanır. Nesneyi <xref:System.Threading.WaitHandle.Dispose%2A> kullanmayı bitirdiğinizde kaynakları hemen serbest etmek için yöntemi kullanabilirsiniz.  
  
## <a name="event-wait-handles-that-reset-automatically"></a>Otomatik Olarak Sıfırlanan Olay Bekleme Tutamaçları  
 Nesneyi ne zaman oluşturduğunuzu <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> belirterek otomatik sıfırlama olayı oluşturursunuz. <xref:System.Threading.EventWaitHandle> Adından da anlaşılacağı gibi, bu eşitleme olayı tek bir bekleme iş parçacığı yayımladıktan sonra, sinyal verildiğinde otomatik olarak sıfırlanır. Yöntemini çağırarak <xref:System.Threading.EventWaitHandle.Set%2A> olayı işaret edin.  
  
 Otomatik sıfırlama olayları genellikle aynı anda tek bir iş parçacığı için bir kaynağa özel erişim sağlamak için kullanılır. Bir iş parçacığı <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemi çağırarak kaynak ister. Bekleme tutamacını başka bir iş parçacığı `true` tutmuyorsa, yöntem döndürür ve arama iş parçacığı kaynağın denetimine sahiptir.  
  
> [!IMPORTANT]
> Tüm eşitleme mekanizmalarında olduğu gibi, korumalı bir kaynağa erişmeden önce tüm kod yollarının uygun bekleme tanıtıcıda beklediğinden emin olmalısınız. İş parçacığı senkronizasyonu işbirliği dir.  
  
 İş parçacığı beklemezken otomatik sıfırlama olayı sinyal verirken, bir iş parçacığı üzerinde beklemeye çalışana kadar sinyal olarak kalır. Olay iş parçacığı bültenleri ve hemen sıfırlar, sonraki iş parçacığı engelleme.  
  
## <a name="event-wait-handles-that-reset-manually"></a>Olay Bekle Handles Bu Sıfırlama El Ile  
 Nesneyi ne zaman oluşturduğunuzu <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> belirterek el ile sıfırlama olayı oluşturursunuz. <xref:System.Threading.EventWaitHandle> Adından da anlaşılacağı gibi, bu eşitleme olayı sinyal verildikten sonra el ile sıfırlanmalıdır. Sıfırlanana kadar, <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemini arayarak, olay tutamacında bekleyen iş parçacıkları engellenmeden hemen devam eder.  
  
 El ile sıfırlama olayı bir ağıl kapısı gibi davranır. Olay sinyal verilmediğinde, ağıldaki atlar gibi blokta bekleyen iplikler. Olay sinyal verildiğinde, <xref:System.Threading.EventWaitHandle.Set%2A> yöntemini çağırarak, tüm bekleyen iş parçacıkları devam etmek için ücretsizdir. Olay, yöntemi çağrılana <xref:System.Threading.EventWaitHandle.Reset%2A> kadar sinyal olarak kalır. Bu, el ile sıfırlama olayını, bir iş parçacığı görevi bitirene kadar beklemesi gereken iş parçacıklarını tutmak için ideal bir yol haline getirir.  
  
 Ağıldan çıkan atlar gibi, serbest bırakılan iş parçacıklarının işletim sistemi tarafından zamanlanması ve yürütmeye devam edilmesi zaman alır. <xref:System.Threading.EventWaitHandle.Reset%2A> Tüm iş parçacıkları yürütme devam etmeden önce yöntem çağrılırsa, kalan iş parçacıkları bir kez daha blok. Hangi iş parçacıkları devam eder ve hangi iş parçacıkları bloğu sistemdeki yük, zamanlayıcıyı bekleyen iş parçacığı sayısı ve benzeri gibi rasgele etkenlere bağlıdır. Olayı işaret eden iş parçacığı sinyalden sonra sona ererse, en yaygın kullanım deseni bu sorun değildir. Tüm bekleyen iş parçacıkları devam ettikten sonra olay sinyali veren iş parçacığının yeni bir göreve başlamasını istiyorsanız, tüm bekleyen iş parçacıkları devam edene kadar bunu engellemeniz gerekir. Aksi takdirde, bir Yarış koşulu var ve koddavranış öngörülemeyen.  
  
## <a name="features-common-to-automatic-and-manual-events"></a>Otomatik ve Manuel Etkinliklerde Ortak Özellikler  
 Genellikle, engellenmemiş bir iş parçacığı <xref:System.Threading.EventWaitHandle> bekleyen iş parçacığı (otomatik sıfırlama olayları durumunda) veya hepsi (el ile sıfırlama olayları durumunda) bültenleri <xref:System.Threading.EventWaitHandle.Set%2A> yöntemi çağıran kadar bir veya daha fazla iş parçacığı blok. Bir iş parçacığı <xref:System.Threading.EventWaitHandle> statik <xref:System.Threading.WaitHandle.SignalAndWait%2A?displayProperty=nameWithType> yöntemi çağırarak, atomik bir işlem olarak bir sinyal ve sonra onu bloke edebilir.  
  
 <xref:System.Threading.EventWaitHandle>nesneler statik <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> yöntemlerle kullanılabilir. Hem <xref:System.Threading.EventWaitHandle> sınıflar <xref:System.Threading.Mutex> hem de <xref:System.Threading.WaitHandle>sınıflar bu yöntemlerle her iki sınıfı da kullanabilirsiniz.  
  
### <a name="named-events"></a>Adlandırılmış Etkinlikler  
 Windows işletim sistemi olay bekleme tutamaçlarının adlara sahip olmasını sağlar. Adlandırılmış bir olay sistem genelindedir. Diğer bir deyişle, adlandırılmış olay oluşturulduktan sonra, tüm işlemlerdeki tüm iş parçacıkları tarafından görülebilir. Böylece, adlandırılmış olaylar iş parçacıkları nın yanı sıra işlemlerin etkinliklerini eşitlemek için de kullanılabilir.  
  
 Bir olay <xref:System.Threading.EventWaitHandle> adını belirten oluşturuculardan birini kullanarak adlandırılmış bir sistem olayını temsil eden bir nesne oluşturabilirsiniz.  
  
> [!NOTE]
> Adlandırılmış olaylar sistem genelinde olduğundan, aynı <xref:System.Threading.EventWaitHandle> adlı olayı temsil eden birden çok nesne olması mümkündür. Bir oluşturucuyu veya <xref:System.Threading.EventWaitHandle.OpenExisting%2A> yöntemi her çağırdığınızda yeni <xref:System.Threading.EventWaitHandle> bir nesne oluşturulur. Aynı adı belirtme, aynı adı taşıyan olayı temsil eden birden çok nesne oluşturur.  
  
 Adlandırılmış olayları kullanırken dikkatli olunması önerilir. Sistem genelinde olduklarından, aynı adı kullanan başka bir işlem iş parçacığınızı beklenmedik bir şekilde engelleyebilir. Aynı bilgisayarda çalıştırılabilen kötü amaçlı kod, bunu hizmet reddi saldırısının temeli olarak kullanabilir.  
  
 Adlandırılmış bir olayı <xref:System.Threading.EventWaitHandle> temsil eden bir nesneyi korumak için erişim denetimi güvenliğini <xref:System.Security.AccessControl.EventWaitHandleSecurity> kullanın, tercihen bir nesne belirten bir oluşturucu kullanarak. <xref:System.Threading.EventWaitHandle.SetAccessControl%2A> Bu yöntemkullanarak erişim denetimi güvenliği de uygulayabilirsiniz, ancak bu olay bekleme tanıtıcısı oluşturulduğu zaman ve korunduğu zaman arasında bir güvenlik açığı penceresi bırakır. Olayları erişim denetimi güvenliğiyle korumak kötü amaçlı saldırıları önlemeye yardımcı olur, ancak istenmeyen ad çakışmasorununu çözmez.  
  
> [!NOTE]
> <xref:System.Threading.EventWaitHandle> Sınıfın aksine, türetilmiş sınıflar <xref:System.Threading.AutoResetEvent> ve <xref:System.Threading.ManualResetEvent> yalnızca yerel bekleme tutamaçları temsil edebilir. Adlandırılmış sistem olaylarını temsil edemezler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.EventWaitHandle>
- <xref:System.Threading.WaitHandle>
- <xref:System.Threading.AutoResetEvent>
- <xref:System.Threading.ManualResetEvent>
