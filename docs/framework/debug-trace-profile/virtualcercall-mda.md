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
ms.openlocfilehash: 49ba4e7ca0b8ed2e433053130bc9ca2742c72ec9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217188"
---
# <a name="virtualcercall-mda"></a><span data-ttu-id="f236c-102">virtualCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="f236c-102">virtualCERCall MDA</span></span>
<span data-ttu-id="f236c-103">`virtualCERCall` yönetilen hata ayıklama Yardımcısı (MDA), kısıtlı yürütme bölgesi (CER) çağrı grafı içindeki bir çağrı sitesinin sanal bir hedefe, yani son olmayan bir sanal yönteme veya bir arabirim kullanarak bir çağrıya işaret ettiği bir uyarı olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f236c-103">The `virtualCERCall` managed debugging assistant (MDA) is activated as a warning indicating that a call site within a constrained execution region (CER) call graph refers to a virtual target, that is, a virtual call to a non-final virtual method or a call using an interface.</span></span> <span data-ttu-id="f236c-104">Ortak dil çalışma zamanı (CLR), bu çağrıların yalnızca ara dil ve meta veri analizinden hedef yöntemini tahmin edemez.</span><span class="sxs-lookup"><span data-stu-id="f236c-104">The common language runtime (CLR) cannot predict the destination method of these calls from the intermediate language and metadata analysis alone.</span></span> <span data-ttu-id="f236c-105">Sonuç olarak, CER grafiğinin bir parçası olarak çağrı ağacı hazırlanamaz ve bu alt ağaçta iş parçacığı iptal etme işlemini otomatik olarak engellenemez.</span><span class="sxs-lookup"><span data-stu-id="f236c-105">As a result, the call tree cannot be prepared as part of the CER graph and thread aborts in that subtree cannot be automatically blocked.</span></span> <span data-ttu-id="f236c-106">Bu MDA, çağrı hedefini hesaplamak için gereken ek bilgiler çalışma zamanında bilindiğinde, bir CER 'nin <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> yöntemine açık çağrılar kullanılarak genişletilmesi gerekebileceği durumları uyarır.</span><span class="sxs-lookup"><span data-stu-id="f236c-106">This MDA warns of cases where a CER might need to be extended by using explicit calls to the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method once the additional information required to compute the call target is known at run time.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f236c-107">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="f236c-107">Symptoms</span></span>  
 <span data-ttu-id="f236c-108">Bir iş parçacığı iptal edildiğinde veya bir uygulama etki alanı kaldırıldığında çalıştırmayan CERs.</span><span class="sxs-lookup"><span data-stu-id="f236c-108">CERs that do not run when a thread is aborted or an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f236c-109">Nedeni</span><span class="sxs-lookup"><span data-stu-id="f236c-109">Cause</span></span>  
 <span data-ttu-id="f236c-110">Bir CER, otomatik olarak hazırlanamadığından sanal bir yönteme yönelik bir çağrı içerir.</span><span class="sxs-lookup"><span data-stu-id="f236c-110">A CER contains a call to a virtual method that cannot be prepared automatically.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f236c-111">Çözüm</span><span class="sxs-lookup"><span data-stu-id="f236c-111">Resolution</span></span>  
 <span data-ttu-id="f236c-112">Sanal yöntem için <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> çağırın.</span><span class="sxs-lookup"><span data-stu-id="f236c-112">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> for the virtual method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f236c-113">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="f236c-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="f236c-114">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f236c-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f236c-115">Çıktı</span><span class="sxs-lookup"><span data-stu-id="f236c-115">Output</span></span>  
  
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
  
## <a name="configuration"></a><span data-ttu-id="f236c-116">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f236c-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="f236c-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="f236c-117">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f236c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f236c-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="f236c-119">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="f236c-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="f236c-120">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="f236c-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
