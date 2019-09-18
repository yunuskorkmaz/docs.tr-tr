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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 623aff91eb801b4b32fc180bd97ed3822ad7f163
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052671"
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="2d0b4-102">illegalPrepareConstrainedRegion MDA</span><span class="sxs-lookup"><span data-stu-id="2d0b4-102">illegalPrepareConstrainedRegion MDA</span></span>
<span data-ttu-id="2d0b4-103">Yönetilen hata ayıklama Yardımcısı (MDA), bir <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> Yöntem çağrısı özel durum işleyicisinin `try` ifadesinden hemen önce gelmediğinde etkinleştirilir. `illegalPrepareConstrainedRegion`</span><span class="sxs-lookup"><span data-stu-id="2d0b4-103">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="2d0b4-104">Bu kısıtlama MSIL düzeyindedir, bu nedenle çağrı ile `try`yorum gibi kod oluşturma olmayan kaynağa izin verilir.</span><span class="sxs-lookup"><span data-stu-id="2d0b4-104">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="2d0b4-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="2d0b4-105">Symptoms</span></span>  
 <span data-ttu-id="2d0b4-106">Bu, basit bir özel durum işleme bloğu (`finally` veya `catch`) olarak hiçbir şekilde kabul edilen kısıtlı bir yürütme bölgesi (cer).</span><span class="sxs-lookup"><span data-stu-id="2d0b4-106">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="2d0b4-107">Sonuç olarak, bölge bellek dışı bir koşul veya bir iş parçacığı iptali durumunda çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="2d0b4-107">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="2d0b4-108">Sebep</span><span class="sxs-lookup"><span data-stu-id="2d0b4-108">Cause</span></span>  
 <span data-ttu-id="2d0b4-109">Bir CER için hazırlık deseninin doğru şekilde izlenmiyor.</span><span class="sxs-lookup"><span data-stu-id="2d0b4-109">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="2d0b4-110">Bu bir hata olayıdır.</span><span class="sxs-lookup"><span data-stu-id="2d0b4-110">This is an error event.</span></span> <span data-ttu-id="2d0b4-111">`catch` Özeldurum`finally` işleyicilerini / <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> blok`filter` içindeki birceriletanışınolarakişaretlemekiçinkullanılanyöntemçağrısı,/ `fault` / `try` bildirim.</span><span class="sxs-lookup"><span data-stu-id="2d0b4-111">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="2d0b4-112">Çözüm</span><span class="sxs-lookup"><span data-stu-id="2d0b4-112">Resolution</span></span>  
 <span data-ttu-id="2d0b4-113">Çağrısının <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> ,`try` deyimden hemen önce yapıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="2d0b4-113">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="2d0b4-114">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="2d0b4-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="2d0b4-115">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="2d0b4-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="2d0b4-116">Çıkış</span><span class="sxs-lookup"><span data-stu-id="2d0b4-116">Output</span></span>  
 <span data-ttu-id="2d0b4-117">MDA, <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> yöntemi çağıran yöntemin adını, MSIL farkını ve çağrının try bloğunun başlangıcından hemen önce gelmesini belirten bir iletiyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2d0b4-117">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="2d0b4-118">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2d0b4-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="2d0b4-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="2d0b4-119">Example</span></span>  
 <span data-ttu-id="2d0b4-120">Aşağıdaki kod örneği, bu MDA 'ın etkinleştirilmesini sağlayan bir model gösterir.</span><span class="sxs-lookup"><span data-stu-id="2d0b4-120">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2d0b4-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d0b4-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [<span data-ttu-id="2d0b4-122">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="2d0b4-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="2d0b4-123">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="2d0b4-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
