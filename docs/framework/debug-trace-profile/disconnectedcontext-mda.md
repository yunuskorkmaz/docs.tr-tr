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
ms.openlocfilehash: b5232a01d877484591df63afc68f672327d4b9d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="disconnectedcontext-mda"></a>disconnectedContext MDA
`disconnectedContext` Yönetilen hata ayıklama Yardımcısı (MDA) bir COM nesnesi ile ilgili bir istek bakım sırasında geçiş bağlantısı kesilen grubu veya bağlamı CLR girişiminde bulunduğunda etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Üzerinde yapılan çağrılar bir [çalışma zamanı aranabilir sarmalayıcısı](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) geçerli grubu veya bağlamı yerine, mevcut bir temel alınan COM bileşeni teslim edilir. COM bileşeni, tek iş parçacıklı (STA) bileşenleri durumda olduğu gibi birden çok iş parçacıklı değilse bu bozulması ve/veya veri kaybına neden olabilir. RCW kendisini bir proxy ise, alternatif olarak, arama, atma sonuçlanabilir bir <xref:System.Runtime.InteropServices.COMException> , bir HRESULT RPC_E_WRONG_THREAD ile.  
  
## <a name="cause"></a>Sebep  
 Geçiş içine CLR girişiminde bulunduğunda OLE grubu veya bağlamı kapatıldı. Bunun en yaygın olarak tüm grup tarafından sahip olunan COM bileşenleri tamamen olan bu serbest önce bilgisayarı Kapat kullanıcı kodundan bir RCW veya COM bileşeni CLR işleme sırasında açık bir çağrı sonucu olarak ortaya çıkabilir STA grupların nedeni , örneğin ne zaman CLR serbest COM bileşeninin ilişkili RCW toplanan atık kaldığında.  
  
## <a name="resolution"></a>Çözüm  
 Bu sorunu önlemek için uygulama grupta Canlı tüm nesneler bitmeden önce STA sahip iş parçacığı sonlandırma değil emin olun. Aynı bağlamları için geçerlidir; uygulama bağlamı içinde dinamik herhangi COM bileşenleri ile tamamen tamamlanmış önce bağlamları kapalı değil emin olun.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA CLR üzerinde etkisi yoktur. Yalnızca veri bağlantısı kesilen bağlam hakkında raporlar.  
  
## <a name="output"></a>Çıkış  
 Bağlantısı kesilen grubu veya bağlamı bağlam tanımlama bilgisini raporlar.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
