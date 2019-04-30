---
title: disconnectedContext MDA
ms.date: 03/30/2017
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb42c04df6e02ff43421b7af6bf2d51b53aa3e69
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755135"
---
# <a name="disconnectedcontext-mda"></a>disconnectedContext MDA
`disconnectedContext` Yönetilen hata ayıklama Yardımcısı (MDA), bir COM nesnesi ile ilgili bir istek bakım sırasında geçiş bağlantısı kesilen grubu veya bağlamı CLR girişiminde bulunduğunda etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Üzerinde yapılan çağrıları bir [çalışma zamanı çağrılabilir sarmalayıcı](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) temel alınan bir COM bileşeni geçerli Grup ya da yerine, mevcut bir içerik teslim edilir. Bu, tek iş parçacıklı grup (STA) bileşenleri durumunda olduğu gibi birden çok iş parçacıklı COM bileşeni değilse bozulmasına ve/veya veri kaybına neden olabilir. RCW kendisi bir proxy varsa, alternatif olarak, arama, atma neden olabilir bir <xref:System.Runtime.InteropServices.COMException> , bir HRESULT RPC_E_WRONG_THREAD ile.  
  
## <a name="cause"></a>Sebep  
 İçine geçişi CLR girişiminde bulunduğunda OLE grubu veya bağlamı kapatıldı. Bu genellikle tüm grup tarafından sahip olunan COM bileşenleri tamamen olan bu serbest önce bilgisayarı Kapat kullanıcı kodundan bir RCW veya CLR, COM bileşeni düzenleme sırasında açık bir çağrı sonucu olarak ortaya çıkabilir STA apartmanlar kaynaklanır , örneğin, CLR serbest COM bileşeni ilişkili RCW atık bırakıldığında.  
  
## <a name="resolution"></a>Çözüm  
 Bu sorunu önlemek için uygulama grupta Canlı tüm nesneleri ile bitmeden önce STA sahip iş parçacığının sonlanmamasına emin olun. Aynı bağlamı için geçerlidir; uygulamanın bir bağlam içinde Canlı tüm COM bileşenlerini tamamen tamamlanmış olduğu önce bağlamları kapalı değil emin olun.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu mda'nın CLR üzerinde etkisi yoktur. Yalnızca veri bağlantısı kesilen bağlam hakkında raporlar.  
  
## <a name="output"></a>Çıkış  
 Bağlantısı kesilen grubu veya bağlamı bağlam tanımlama bilgisini bildirir.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
