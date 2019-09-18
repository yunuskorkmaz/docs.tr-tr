---
title: dirtyCastAndCallOnInterface MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), early bound calls AutoDispatch
- dispatch-only mode
- dirtyCastAndCallOnInterface
- early-bound managed classes
- early bound calls on AutoDispatch
- MDAs (managed debugging assistants), early bound calls AutoDispatch
- EarlyBoundCallOnAutorDispatchClassInteface MDA
ms.assetid: aa388ed3-7e3d-48ea-a0b5-c47ae19cec38
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6ac43f6b92198fec03e722b6cf5e12b86df6f4b8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052872"
---
# <a name="dirtycastandcalloninterface-mda"></a>dirtyCastAndCallOnInterface MDA
Yönetilen `dirtyCastAndCallOnInterface` hata ayıklama Yardımcısı (MDA), bir vtable üzerinden erken bağlanan bir çağrı yalnızca geç bağlanan olarak işaretlenmiş bir sınıf arabiriminde denendiğinde etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir uygulama bir erişim ihlali oluşturur veya COM ile CLR 'ye erken bağlantılı bir çağrı yerleştirirken beklenmedik davranışlara sahiptir.  
  
## <a name="cause"></a>Sebep  
 Kod, bir vtable aracılığıyla yalnızca geç bağlanan bir sınıf arabirimi aracılığıyla erken bağlanan bir çağrı deniyor. Varsayılan sınıf arabirimlerinin yalnızca geç bağlanmakta olduğunu unutmayın. Ayrıca, <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> bir <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> değeri (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`) olan özniteliğiyle geç bağlantılı olarak da tanımlanabilir.  
  
## <a name="resolution"></a>Çözüm  
 Önerilen çözüm, COM tarafından kullanılmak üzere bir açık arabirim tanımlamaktır ve COM istemcilerinin, otomatik olarak oluşturulan sınıf arabirimi yerine bu arabirim aracılığıyla çağırmasını sağlar. Alternatif olarak, COM 'dan yapılan çağrı aracılığıyla `IDispatch`geç bağlı çağrıya dönüştürülebilir.  
  
 Son olarak, <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) sınıfını, erken bağlantılı çağrıların com 'dan yerleştirilmesine izin verecek şekilde belirlemek mümkündür; ancak, içinde <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>açıklanan sürüm oluşturma sınırlamaları <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> nedeniyle kullanılması önemle önerilmez.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur. Yalnızca, Gecikmeli bağlantılı arabirimlerde erken bağlantılı çağrılar hakkındaki verileri raporlar.  
  
## <a name="output"></a>Çıkış  
 Erken bağlanılmakta olan alanın veya metodun adı.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
