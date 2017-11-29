---
title: disconnectedContext MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1bbcd4a1058c4202a3de7b8eecb05caad7730ce5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte çalışma hazırlama](../../../docs/framework/interop/interop-marshaling.md)
