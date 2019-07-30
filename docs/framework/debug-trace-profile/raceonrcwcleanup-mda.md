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
ms.openlocfilehash: e6400986d58fcb5f11d06e371a1b58f5256f4c62
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629372"
---
# <a name="raceonrcwcleanup-mda"></a>raceOnRCWCleanup MDA
Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR), bir [çalışma zamanı çağrılabilir sarmalayıcı](../../../docs/standard/native-interop/runtime-callable-wrapper.md) (RCW), <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> yöntemi gibi bir komut kullanılarak yapıldığında bir çalışma zamanında çağrılabilir sarmalayıcı (RCW) kullanımda olduğunu algıladığında etkinleştirilir. `raceOnRCWCleanup`  
  
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
