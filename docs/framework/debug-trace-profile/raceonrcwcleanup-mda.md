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
ms.workload: dotnet
ms.openlocfilehash: 33d1c7d91c33c194353af43deed9329b9b4ec841
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
