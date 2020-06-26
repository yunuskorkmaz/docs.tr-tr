---
title: dirtyCastAndCallOnInterface MDA
description: Erken bağlı vtable çağrıları yalnızca geç bağlı sınıf arabirimlerinde yapıldığında çağrılan Dirtycastandcallonınterface yönetilen hata ayıklama Yardımcısı ' nı gözden geçirin.
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
ms.openlocfilehash: 2ed5589909915a261a22c48490e469ae52659c8c
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416076"
---
# <a name="dirtycastandcalloninterface-mda"></a>dirtyCastAndCallOnInterface MDA
`dirtyCastAndCallOnInterface`Yönetilen hata ayıklama Yardımcısı (MDA), bir vtable üzerinden erken bağlanan bir çağrı yalnızca geç bağlanan olarak işaretlenmiş bir sınıf arabiriminde denendiğinde etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir uygulama bir erişim ihlali oluşturur veya COM ile CLR 'ye erken bağlantılı bir çağrı yerleştirirken beklenmedik davranışlara sahiptir.  
  
## <a name="cause"></a>Nedeni  
 Kod, bir vtable aracılığıyla yalnızca geç bağlanan bir sınıf arabirimi aracılığıyla erken bağlanan bir çağrı deniyor. Varsayılan sınıf arabirimlerinin yalnızca geç bağlanmakta olduğunu unutmayın. Ayrıca, <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> bir <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> değeri () olan özniteliğiyle geç bağlantılı olarak da tanımlanabilir `[ClassInterface(ClassInterfaceType.AutoDispatch)]` .  
  
## <a name="resolution"></a>Çözüm  
 Önerilen çözüm, COM tarafından kullanılmak üzere bir açık arabirim tanımlamaktır ve COM istemcilerinin, otomatik olarak oluşturulan sınıf arabirimi yerine bu arabirim aracılığıyla çağırmasını sağlar. Alternatif olarak, COM 'dan yapılan çağrı aracılığıyla geç bağlı çağrıya dönüştürülebilir `IDispatch` .  
  
 Son olarak, <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> () sınıfını, `[ClassInterface(ClassInterfaceType.AutoDual)]` erken bağlantılı çağrıların com 'dan yerleştirilmesine izin verecek şekilde belirlemek mümkündür; ancak, <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> içinde açıklanan sürüm oluşturma sınırlamaları nedeniyle kullanılması önemle önerilmez <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> .  
  
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
