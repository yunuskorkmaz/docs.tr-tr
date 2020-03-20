---
title: virtualCERCall MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- virtualCERCall MDA
- virtual CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
ms.openlocfilehash: a2112baed863b1035cbee4e956c1b6e271ff6e3c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181718"
---
# <a name="virtualcercall-mda"></a>virtualCERCall MDA
Yönetilen `virtualCERCall` hata ayıklama yardımcısı (MDA), kısıtlı bir yürütme bölgesi (CER) çağrı grafiği içindeki bir çağrı sitesinin sanal bir hedefe, yani son sanal olmayan bir yönteme veya arabirim kullanan bir çağrıya sanal çağrı anlamına geldiğini belirten bir uyarı olarak etkinleştirilir. Ortak dil çalışma süresi (CLR), bu çağrıların hedef yöntemini yalnızca ara dilden ve meta veri çözümlemesi ile tahmin edemez. Sonuç olarak, çağrı ağacı CER grafiğinin bir parçası olarak hazırlanamaz ve bu alt ağaçtaki iş parçacığı iptalleri otomatik olarak engellenemez. Bu MDA, arama hedefini hesaplamak için gereken ek bilgiler <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> çalışma zamanında bilindiğinde yönteme açık çağrılar kullanılarak CER'in genişletilmesi gerekebileceği durumlar konusunda uyarır.  
  
## <a name="symptoms"></a>Belirtiler  
 İş parçacığı iptal edildiğinde veya uygulama etki alanı kaldırılınca çalışmayan CER'ler.  
  
## <a name="cause"></a>Nedeni  
 CER, otomatik olarak hazırlanamayan sanal bir yönteme çağrı içerir.  
  
## <a name="resolution"></a>Çözüm  
 Sanal <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> yöntem için arayın.  
  
## <a name="effect-on-the-runtime"></a>Çalışma Süresi üzerindeki etkisi  
 Bu MDA'nın CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıktı  
  
```output
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
    <VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
  
```csharp
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma Hazırlama](../interop/interop-marshaling.md)
