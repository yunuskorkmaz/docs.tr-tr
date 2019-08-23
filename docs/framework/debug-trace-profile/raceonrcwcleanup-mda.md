---
title: raceOnRCWCleanup MDA
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ca3b28d0d27af0a752de894f5856b76939b01e09
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967248"
---
# <a name="raceonrcwcleanup-mda"></a>raceOnRCWCleanup MDA
Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR), bir [çalışma zamanı çağrılabilir sarmalayıcı](../../standard/native-interop/runtime-callable-wrapper.md) (RCW), <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> yöntemi gibi bir komut kullanılarak yapıldığında bir çalışma zamanında çağrılabilir sarmalayıcı (RCW) kullanımda olduğunu algıladığında etkinleştirilir. `raceOnRCWCleanup`  
  
## <a name="symptoms"></a>Belirtiler  
 Ya da benzer bir yöntemi kullanarak <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> bir RCW boşaltmasından veya sonrasında ihlal veya bellek bozulmasına erişin.  
  
## <a name="cause"></a>Sebep  
 RCW, başka bir iş parçacığında veya boşaltma iş parçacığı yığınında kullanılıyor.  Kullanımda olan bir RCW yayımlanamaz.  
  
## <a name="resolution"></a>Çözüm  
 Geçerli ya da diğer iş parçacıklarında kullanımda olabilecek bir RCW boşaltımı yok.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Hatayı açıklayan bir ileti.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
