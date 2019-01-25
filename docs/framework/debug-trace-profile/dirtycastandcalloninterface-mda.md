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
ms.openlocfilehash: 8a1d8aa391b546d02c813e1f719601b9bff198be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657239"
---
# <a name="dirtycastandcalloninterface-mda"></a>dirtyCastAndCallOnInterface MDA
`dirtyCastAndCallOnInterface` Yönetilen hata ayıklama Yardımcısı (MDA) bir erken bağlanan çağrı bir vtable aracılığıyla geç bağlama yalnızca işaretlenmiş bir sınıf arabirimi çalışırken etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir uygulama bir erişim ihlali oluşturur ya da sahip bir erken bağlanan çağrı yoluyla COM CLR yerleştirirken beklenmeyen davranış.  
  
## <a name="cause"></a>Sebep  
 Kod bir erken bağlanan çağrı bir vtable geç bağlama yalnızca bir sınıf arabirimi üzerinden aracılığıyla çalışıyor. Geç yalnızca bağlama olarak arabirimler varsayılan sınıf tarafından tanımlanan unutmayın. Bunlar gibi geç bağlama ile tanımlanabilir <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> özniteliğini bir <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> değeri (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).  
  
## <a name="resolution"></a>Çözüm  
 Önerilen çözüm, COM tarafından kullanılması için açık bir arabirim tanımlayın ve otomatik olarak oluşturulan sınıf arabirimi üzerinden yerine bu arabirimi aracılığıyla COM istemcileri çağrısı sahip olmaktır. Geç bağlama çağrısıyla COM çağrısından alternatif olarak, dönüştürülebilir `IDispatch`.  
  
 Son olarak, sınıf olarak tanımlamak olası <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`); COM'dan yerleştirilecek erken bağlama çağrıları izin verecek şekilde ancak kullanarak <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> açıklanan sürüm oluşturma sınırlamaları nedeniyle önerilmez <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu mda'nın CLR üzerinde etkisi yoktur. Geç bağlama arabirimleri üzerinde erken bağlanan çağrılar hakkında veri yalnızca raporlar.  
  
## <a name="output"></a>Çıkış  
 Yöntem veya erken bağlanan erişilen alan adı adı.  
  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
