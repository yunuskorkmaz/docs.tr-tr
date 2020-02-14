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
ms.openlocfilehash: 6e4f0074958e8a6a8ca322968e9c29e89481c0c8
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216508"
---
# <a name="dirtycastandcalloninterface-mda"></a>dirtyCastAndCallOnInterface MDA
`dirtyCastAndCallOnInterface` yönetilen hata ayıklama Yardımcısı (MDA), bir vtable üzerinden erken bağlanan bir çağrı yalnızca geç bağlanan olarak işaretlenmiş bir sınıf arabiriminde denendiğinde etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir uygulama bir erişim ihlali oluşturur veya COM ile CLR 'ye erken bağlantılı bir çağrı yerleştirirken beklenmedik davranışlara sahiptir.  
  
## <a name="cause"></a>Nedeni  
 Kod, bir vtable aracılığıyla yalnızca geç bağlanan bir sınıf arabirimi aracılığıyla erken bağlanan bir çağrı deniyor. Varsayılan sınıf arabirimlerinin yalnızca geç bağlanmakta olduğunu unutmayın. Ayrıca, <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> özniteliğiyle bir <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> değeri (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`) ile geç bağlantılı olarak da tanımlanabilir.  
  
## <a name="resolution"></a>Çözüm  
 Önerilen çözüm, COM tarafından kullanılmak üzere bir açık arabirim tanımlamaktır ve COM istemcilerinin, otomatik olarak oluşturulan sınıf arabirimi yerine bu arabirim aracılığıyla çağırmasını sağlar. Alternatif olarak, COM 'dan yapılan çağrı `IDispatch`aracılığıyla geç bağlı çağrıya dönüştürülebilir.  
  
 Son olarak, <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) sınıfı, erken bağlantılı çağrıların COM 'dan yerleştirilmesine izin verecek şekilde tanımlanması mümkündür; Ancak, <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>açıklanan sürüm oluşturma sınırlamaları nedeniyle <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> kullanımı kesinlikle önerilmez.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur. Yalnızca, Gecikmeli bağlantılı arabirimlerde erken bağlantılı çağrılar hakkındaki verileri raporlar.  
  
## <a name="output"></a>Çıktı  
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
