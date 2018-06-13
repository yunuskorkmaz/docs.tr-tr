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
ms.openlocfilehash: c2f2104768144da244679e5d0be884d70a3ba6b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386658"
---
# <a name="virtualcercall-mda"></a><span data-ttu-id="e23e1-102">virtualCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="e23e1-102">virtualCERCall MDA</span></span>
<span data-ttu-id="e23e1-103">`virtualCERCall` Yönetilen hata ayıklama Yardımcısı (MDA) belirten bir uyarı çağrısı site kısıtlı yürütme bölge (CER) arama grafiği içinde sanal bir hedef, diğer bir deyişle, son olmayan sanal bir yöntem veya çağrı kullanarak sanal bir çağrı başvurduğundan emin olarak etkinleştirilmiş bir arabirim.</span><span class="sxs-lookup"><span data-stu-id="e23e1-103">The `virtualCERCall` managed debugging assistant (MDA) is activated as a warning indicating that a call site within a constrained execution region (CER) call graph refers to a virtual target, that is, a virtual call to a non-final virtual method or a call using an interface.</span></span> <span data-ttu-id="e23e1-104">Ortak dil çalışma zamanı (CLR) bu tek başına Ara dil ve meta veri çözümleme çağrılarından hedef yöntemi tahmin edilemez.</span><span class="sxs-lookup"><span data-stu-id="e23e1-104">The common language runtime (CLR) cannot predict the destination method of these calls from the intermediate language and metadata analysis alone.</span></span> <span data-ttu-id="e23e1-105">Sonuç olarak, çağrı ağacı CER grafiğin bir parçası hazırlanamıyor ve iş parçacığı iptalleri o ağaçtaki otomatik olarak engellenemez.</span><span class="sxs-lookup"><span data-stu-id="e23e1-105">As a result, the call tree cannot be prepared as part of the CER graph and thread aborts in that subtree cannot be automatically blocked.</span></span> <span data-ttu-id="e23e1-106">Burada bir CER gerekebilir açık çağrılar kullanarak genişletilmesi örneklerinin bu MDA uyarır <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> çağrısı hedef işlem için gereken ek bilgileri zamanında bilinen sonra yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e23e1-106">This MDA warns of cases where a CER might need to be extended by using explicit calls to the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method once the additional information required to compute the call target is known at run time.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e23e1-107">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="e23e1-107">Symptoms</span></span>  
 <span data-ttu-id="e23e1-108">Bir iş parçacığı iptal edildiğinde, çalıştırmayan CERs veya uygulama etki alanı kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="e23e1-108">CERs that do not run when a thread is aborted or an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e23e1-109">Sebep</span><span class="sxs-lookup"><span data-stu-id="e23e1-109">Cause</span></span>  
 <span data-ttu-id="e23e1-110">Bir CER otomatik olarak hazırlanamıyor sanal bir yöntemine yapılan bir çağrı içerir.</span><span class="sxs-lookup"><span data-stu-id="e23e1-110">A CER contains a call to a virtual method that cannot be prepared automatically.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e23e1-111">Çözüm</span><span class="sxs-lookup"><span data-stu-id="e23e1-111">Resolution</span></span>  
 <span data-ttu-id="e23e1-112">Çağrı <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> sanal yöntemi için.</span><span class="sxs-lookup"><span data-stu-id="e23e1-112">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> for the virtual method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e23e1-113">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="e23e1-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="e23e1-114">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e23e1-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e23e1-115">Çıkış</span><span class="sxs-lookup"><span data-stu-id="e23e1-115">Output</span></span>  
  
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
  
## <a name="configuration"></a><span data-ttu-id="e23e1-116">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e23e1-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    < VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="e23e1-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="e23e1-117">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e23e1-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e23e1-118">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="e23e1-119">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="e23e1-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="e23e1-120">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="e23e1-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
