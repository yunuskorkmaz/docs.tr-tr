---
title: raceOnRCWCleanup MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 055ca5a85ca37401107b5cef8f6ff55237c3320b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="raceonrcwcleanup-mda"></a>raceOnRCWCleanup MDA
`raceOnRCWCleanup` Ortak dil çalışma zamanı (CLR) algıladığında, yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş bir [çalışma zamanı aranabilir sarmalayıcısı](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) gibibirkomutkullanarakbunuserbestbırakmakiçinbirçağrıyapılır,bunakullanın<xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>yöntemi.  
  
## <a name="symptoms"></a>Belirtiler  
 Erişim ihlalleri veya Bellek Bozulması sırasında veya sonrasında kullanarak bir RCW boşaltma <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> veya benzer bir yöntem.  
  
## <a name="cause"></a>Sebep  
 RCW boşaltma iş parçacığı yığın veya başka bir iş parçacığı üzerinde kullanılıyor.  Kullanımda olan bir RCW bırakılamıyor.  
  
## <a name="resolution"></a>Çözüm  
 Geçerli veya başka bir iş parçacığı kullanımda olabilir bir RCW boş değil.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA CLR üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Hatayı açıklayan ileti.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte çalışma hazırlama](../../../docs/framework/interop/interop-marshaling.md)
