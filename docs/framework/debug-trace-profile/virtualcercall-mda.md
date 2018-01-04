---
title: virtualCERCall MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- virtualCERCall MDA
- virtual CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 010c5dd082c10556ed264306b7575cbe5399fda3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="virtualcercall-mda"></a>virtualCERCall MDA
`virtualCERCall` Yönetilen hata ayıklama Yardımcısı (MDA) belirten bir uyarı çağrısı site kısıtlı yürütme bölge (CER) arama grafiği içinde sanal bir hedef, diğer bir deyişle, son olmayan sanal bir yöntem veya çağrı kullanarak sanal bir çağrı başvurduğundan emin olarak etkinleştirilmiş bir arabirim. Ortak dil çalışma zamanı (CLR) bu tek başına Ara dil ve meta veri çözümleme çağrılarından hedef yöntemi tahmin edilemez. Sonuç olarak, çağrı ağacı CER grafiğin bir parçası hazırlanamıyor ve iş parçacığı iptalleri o ağaçtaki otomatik olarak engellenemez. Burada bir CER gerekebilir açık çağrılar kullanarak genişletilmesi örneklerinin bu MDA uyarır <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> çağrısı hedef işlem için gereken ek bilgileri zamanında bilinen sonra yöntemi.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir iş parçacığı iptal edildiğinde, çalıştırmayan CERs veya uygulama etki alanı kaldırılır.  
  
## <a name="cause"></a>Sebep  
 Bir CER otomatik olarak hazırlanamıyor sanal bir yöntemine yapılan bir çağrı içerir.  
  
## <a name="resolution"></a>Çözüm  
 Çağrı <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> sanal yöntemi için.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA CLR üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
  
```  
Method 'MethodWithCer', while executing within a constrained execution region, makes a call  
at IL offset 0x0024 to 'VirtualMethod', which is virtual and cannot be prepared automatically  
at compile time. The caller must ensure this method is prepared explicitly at  
runtime before entering the constrained execution region.  
method name="VirtualMethod"  
declaringType name="VirtualCERCall+MyClass"  
  declaringModule name="mda"  
    callsite name="MethodWithCer" offset="0x0024"  
```  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    < VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
  
```  
class MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    virtual void VirtualMethod()  
    {  
        ...  
    }  
}  
  
class MyDerivedClass : MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    override void VirtualMethod()  
    {  
        ...  
    }  
}  
  
void MethodWithCer(MyClass object)  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    try  
    {  
        ...  
    }  
    finally  
    {  
        // Start of the CER.  
  
        // Cannot tell at analysis time whether object is a MyClass  
        // or a MyDerivedClass, so we do not know which version of   
        // VirtualMethod we are going to call.  
        object.VirtualMethod();  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
