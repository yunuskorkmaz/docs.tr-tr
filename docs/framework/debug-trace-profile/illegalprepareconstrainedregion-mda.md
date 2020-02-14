---
title: illegalPrepareConstrainedRegion MDA
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
ms.openlocfilehash: b80d6160876834b22e8d9d1eb7112b8b67c15fcc
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216472"
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="4f9b7-102">illegalPrepareConstrainedRegion MDA</span><span class="sxs-lookup"><span data-stu-id="4f9b7-102">illegalPrepareConstrainedRegion MDA</span></span>
<span data-ttu-id="4f9b7-103">`illegalPrepareConstrainedRegion` yönetilen hata ayıklama Yardımcısı (MDA), bir <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> yöntemi çağrısı özel durum işleyicisinin `try` deyimiyle hemen önce olmadığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4f9b7-103">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="4f9b7-104">Bu kısıtlama MSIL düzeyindedir; bu nedenle, çağrı ve `try`arasında kod oluşturma dışı kaynağa (Yorumlar gibi) izin verilir.</span><span class="sxs-lookup"><span data-stu-id="4f9b7-104">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="4f9b7-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="4f9b7-105">Symptoms</span></span>  
 <span data-ttu-id="4f9b7-106">Bu şekilde hiçbir şekilde kabul edilen kısıtlı bir yürütme bölgesi (CER), ancak basit bir özel durum işleme bloğu (`finally` veya `catch`).</span><span class="sxs-lookup"><span data-stu-id="4f9b7-106">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="4f9b7-107">Sonuç olarak, bölge bellek dışı bir koşul veya bir iş parçacığı iptali durumunda çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="4f9b7-107">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="4f9b7-108">Nedeni</span><span class="sxs-lookup"><span data-stu-id="4f9b7-108">Cause</span></span>  
 <span data-ttu-id="4f9b7-109">Bir CER için hazırlık deseninin doğru şekilde izlenmiyor.</span><span class="sxs-lookup"><span data-stu-id="4f9b7-109">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="4f9b7-110">Bu bir hata olayıdır.</span><span class="sxs-lookup"><span data-stu-id="4f9b7-110">This is an error event.</span></span> <span data-ttu-id="4f9b7-111">Özel durum işleyicilerini, `catch`/`finally`/`fault`/`filter` blokları üzerinde bir CER 'ye giriş olarak işaretlemek için kullanılan <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> yöntemi çağrısı `try` deyimlerinden hemen önce kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4f9b7-111">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="4f9b7-112">Çözüm</span><span class="sxs-lookup"><span data-stu-id="4f9b7-112">Resolution</span></span>  
 <span data-ttu-id="4f9b7-113"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> çağrısının `try` deyimden hemen önce yapıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="4f9b7-113">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4f9b7-114">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="4f9b7-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="4f9b7-115">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="4f9b7-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4f9b7-116">Çıktı</span><span class="sxs-lookup"><span data-stu-id="4f9b7-116">Output</span></span>  
 <span data-ttu-id="4f9b7-117">MDA, <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> yöntemini çağıran yöntemin adını, MSIL sapmasını ve çağrının, try bloğunun başlangıcından hemen önce gelmediğini belirten bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4f9b7-117">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="4f9b7-118">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4f9b7-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="4f9b7-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f9b7-119">Example</span></span>  
 <span data-ttu-id="4f9b7-120">Aşağıdaki kod örneği, bu MDA 'ın etkinleştirilmesini sağlayan bir model gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f9b7-120">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
```csharp
void MethodWithInvalidPCR()  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    Object o = new Object();  
    try  
    {  
        …  
    }  
    finally  
    {  
        …  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f9b7-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f9b7-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [<span data-ttu-id="4f9b7-122">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="4f9b7-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="4f9b7-123">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="4f9b7-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
