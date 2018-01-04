---
title: dirtyCastAndCallOnInterface MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), early bound calls AutoDispatch
- dispatch-only mode
- dirtyCastAndCallOnInterface
- early-bound managed classes
- early bound calls on AutoDispatch
- MDAs (managed debugging assistants), early bound calls AutoDispatch
- EarlyBoundCallOnAutorDispatchClassInteface MDA
ms.assetid: aa388ed3-7e3d-48ea-a0b5-c47ae19cec38
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1dcb3e5088b8dbc5b1d803ff042e363ec6e389a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="dirtycastandcalloninterface-mda"></a>dirtyCastAndCallOnInterface MDA
`dirtyCastAndCallOnInterface` Yönetilen hata ayıklama Yardımcısı (MDA) bir vtable erken bağlama çağrısıyla geç bağlama yalnızca işaretlenmiş bir sınıf arabiriminde çalışırken etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir uygulama bir erişim ihlali oluşturur veya sahip COM erken bağlama çağrısıyla CLR yerleştirme sırasında beklenmeyen bir davranış.  
  
## <a name="cause"></a>Sebep  
 Kod vtable geç bağlama yalnızca bir sınıf arabirimi aracılığıyla erken bağlama çağrısıyla deniyor. Geç yalnızca bağlı olarak arabirimler varsayılan sınıf tarafından tanımlanan unutmayın. Olarak geç bağlama ile de tanımlanabilir <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> ile öznitelik bir <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> değeri (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).  
  
## <a name="resolution"></a>Çözüm  
 Önerilen çözüm COM tarafından kullanım için açık bir arabirim tanımlayın ve otomatik olarak oluşturulan sınıf arabirimi aracılığıyla yerine bu arabiriminden COM istemcileri çağrısı sahip olmaktır. Geç bağlama çağrısıyla COM çağrısından alternatif olarak, dönüştürülebilir `IDispatch`.  
  
 Son olarak, bu sınıf olarak tanımlamak mümkündür <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) COM; yerleştirilecek erken bağlama çağrıları izin vermek için ancak kullanarak <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> açıklanan sürüm oluşturma sınırlamaları nedeniyle kesinlikle önerilmez <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA CLR üzerinde etkisi yoktur. Erken bağlama çağrıları geç bağlama arabirimlerinde hakkında veri yalnızca raporlar.  
  
## <a name="output"></a>Çıkış  
 Erken bağlama erişilen alanının adı ve yöntemi adı.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
