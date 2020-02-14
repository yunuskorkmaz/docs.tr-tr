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
ms.openlocfilehash: edf1fe3ee5be631f7f3c42f4a6cdb17f1be722cf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216191"
---
# <a name="raceonrcwcleanup-mda"></a>raceOnRCWCleanup MDA
`raceOnRCWCleanup` yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR), bir çalışma zamanı çağrılabilir sarmalayıcı (RCW), <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> yöntemi gibi bir komut kullanılarak yapıldığında bir [çalışma zamanı çağrılabilir sarmalayıcı](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) kullanımda olduğunu algıladığında etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> veya benzer bir yöntem kullanarak bir RCW boşaltılırken veya sonrasında ihlal veya bellek bozulmasına erişin.  
  
## <a name="cause"></a>Nedeni  
 RCW, başka bir iş parçacığında veya boşaltma iş parçacığı yığınında kullanılıyor.  Kullanımda olan bir RCW yayımlanamaz.  
  
## <a name="resolution"></a>Çözüm  
 Geçerli ya da diğer iş parçacıklarında kullanımda olabilecek bir RCW boşaltımı yok.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıktı  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../interop/interop-marshaling.md)
