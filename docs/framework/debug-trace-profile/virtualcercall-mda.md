---
title: virtualCERCall MDA
description: Bir CER tarafından otomatik olarak Hazırlanmayacak bir sanal yönteme çağrı içeriyorsa çağrılan virtualCERCall yönetilen hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- virtualCERCall MDA
- virtual CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
ms.openlocfilehash: fab0686b1c7d2fbb1485f6e4b82d008495a553cd
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803566"
---
# <a name="virtualcercall-mda"></a><span data-ttu-id="e1171-103">virtualCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="e1171-103">virtualCERCall MDA</span></span>
<span data-ttu-id="e1171-104">`virtualCERCall`Yönetilen hata ayıklama Yardımcısı (MDA), kısıtlı bir yürütme bölgesi (cer) çağrı grafı içindeki bir çağrı sitesinin sanal bir hedefe, yani son olmayan bir sanal yönteme veya bir arabirim kullanarak bir çağrıya işaret ettiği bir uyarı olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e1171-104">The `virtualCERCall` managed debugging assistant (MDA) is activated as a warning indicating that a call site within a constrained execution region (CER) call graph refers to a virtual target, that is, a virtual call to a non-final virtual method or a call using an interface.</span></span> <span data-ttu-id="e1171-105">Ortak dil çalışma zamanı (CLR), bu çağrıların yalnızca ara dil ve meta veri analizinden hedef yöntemini tahmin edemez.</span><span class="sxs-lookup"><span data-stu-id="e1171-105">The common language runtime (CLR) cannot predict the destination method of these calls from the intermediate language and metadata analysis alone.</span></span> <span data-ttu-id="e1171-106">Sonuç olarak, CER grafiğinin bir parçası olarak çağrı ağacı hazırlanamaz ve bu alt ağaçta iş parçacığı iptal etme işlemini otomatik olarak engellenemez.</span><span class="sxs-lookup"><span data-stu-id="e1171-106">As a result, the call tree cannot be prepared as part of the CER graph and thread aborts in that subtree cannot be automatically blocked.</span></span> <span data-ttu-id="e1171-107">Bu MDA <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> , çağrı hedefini hesaplamak için gereken ek bilgiler çalışma zamanında bilindiğinde, BIR cer 'nin yönteme açık çağrılar kullanılarak genişletilmesi gerekebileceği durumları uyarır.</span><span class="sxs-lookup"><span data-stu-id="e1171-107">This MDA warns of cases where a CER might need to be extended by using explicit calls to the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method once the additional information required to compute the call target is known at run time.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e1171-108">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="e1171-108">Symptoms</span></span>  
 <span data-ttu-id="e1171-109">Bir iş parçacığı iptal edildiğinde veya bir uygulama etki alanı kaldırıldığında çalıştırmayan CERs.</span><span class="sxs-lookup"><span data-stu-id="e1171-109">CERs that do not run when a thread is aborted or an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e1171-110">Nedeni</span><span class="sxs-lookup"><span data-stu-id="e1171-110">Cause</span></span>  
 <span data-ttu-id="e1171-111">Bir CER, otomatik olarak hazırlanamadığından sanal bir yönteme yönelik bir çağrı içerir.</span><span class="sxs-lookup"><span data-stu-id="e1171-111">A CER contains a call to a virtual method that cannot be prepared automatically.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e1171-112">Çözüm</span><span class="sxs-lookup"><span data-stu-id="e1171-112">Resolution</span></span>  
 <span data-ttu-id="e1171-113"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>Sanal yöntem için çağrı.</span><span class="sxs-lookup"><span data-stu-id="e1171-113">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> for the virtual method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e1171-114">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="e1171-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="e1171-115">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e1171-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e1171-116">Çıktı</span><span class="sxs-lookup"><span data-stu-id="e1171-116">Output</span></span>  
  
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
  
## <a name="configuration"></a><span data-ttu-id="e1171-117">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e1171-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="e1171-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="e1171-118">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e1171-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1171-119">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="e1171-120">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="e1171-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e1171-121">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="e1171-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
