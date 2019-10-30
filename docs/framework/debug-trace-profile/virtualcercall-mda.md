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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8784d6980d3edb1bbdd7b39a81e7e33bfec81242
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039609"
---
# <a name="virtualcercall-mda"></a>virtualCERCall MDA
`virtualCERCall` yönetilen hata ayıklama Yardımcısı (MDA), kısıtlı yürütme bölgesi (CER) çağrı grafı içindeki bir çağrı sitesinin sanal bir hedefe, yani son olmayan bir sanal yönteme veya bir arabirim kullanarak bir çağrıya işaret ettiği bir uyarı olarak etkinleştirilir. Ortak dil çalışma zamanı (CLR), bu çağrıların yalnızca ara dil ve meta veri analizinden hedef yöntemini tahmin edemez. Sonuç olarak, CER grafiğinin bir parçası olarak çağrı ağacı hazırlanamaz ve bu alt ağaçta iş parçacığı iptal etme işlemini otomatik olarak engellenemez. Bu MDA, çağrı hedefini hesaplamak için gereken ek bilgiler çalışma zamanında bilindiğinde, bir CER 'nin <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> yöntemine açık çağrılar kullanılarak genişletilmesi gerekebileceği durumları uyarır.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir iş parçacığı iptal edildiğinde veya bir uygulama etki alanı kaldırıldığında çalıştırmayan CERs.  
  
## <a name="cause"></a>Sebep  
 Bir CER, otomatik olarak hazırlanamadığından sanal bir yönteme yönelik bir çağrı içerir.  
  
## <a name="resolution"></a>Çözüm  
 Sanal yöntem için <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> çağırın.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
  
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
- [Birlikte Çalışma için Hazırlama](../interop/interop-marshaling.md)
