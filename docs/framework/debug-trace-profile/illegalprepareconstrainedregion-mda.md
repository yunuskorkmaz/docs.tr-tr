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
ms.openlocfilehash: 23a36d1709f03583ce39af0e7c80bb1ecd7cf809
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754394"
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="75eb5-102">illegalPrepareConstrainedRegion MDA</span><span class="sxs-lookup"><span data-stu-id="75eb5-102">illegalPrepareConstrainedRegion MDA</span></span>
<span data-ttu-id="75eb5-103">`illegalPrepareConstrainedRegion` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş olduğunda bir <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> yöntem çağrısı değil hemen önünde `try` özel durum işleyicisinin bildirimi.</span><span class="sxs-lookup"><span data-stu-id="75eb5-103">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="75eb5-104">Çağrı arasında kaynak kodu oluşturma için izin verilen, bu nedenle bu kısıtlama MSIL düzeyini ve `try`, açıklamalar gibi.</span><span class="sxs-lookup"><span data-stu-id="75eb5-104">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="75eb5-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="75eb5-105">Symptoms</span></span>  
 <span data-ttu-id="75eb5-106">Bu nedenle, ancak basit bir özel durum işleme bloğu asla kabul kısıtlı yürütme bölge (CER) (`finally` veya `catch`).</span><span class="sxs-lookup"><span data-stu-id="75eb5-106">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="75eb5-107">Sonuç olarak, bölge içinde bir bellek yetersiz koşulu veya bir iş parçacığı iptal olması durumunda çalıştırmaz.</span><span class="sxs-lookup"><span data-stu-id="75eb5-107">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="75eb5-108">Sebep</span><span class="sxs-lookup"><span data-stu-id="75eb5-108">Cause</span></span>  
 <span data-ttu-id="75eb5-109">Bir CER hazırlık desenini doğru şekilde izlenmiyor.</span><span class="sxs-lookup"><span data-stu-id="75eb5-109">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="75eb5-110">Bir hata olayı budur.</span><span class="sxs-lookup"><span data-stu-id="75eb5-110">This is an error event.</span></span> <span data-ttu-id="75eb5-111"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> Özel durum işleyicileri içinde bir CER giriş olarak işaretlemek için kullanılan yöntem çağrısı kendi `catch` / `finally` / `fault` / `filter` blokları, hemen önce kullanılmalıdır `try` deyimi.</span><span class="sxs-lookup"><span data-stu-id="75eb5-111">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="75eb5-112">Çözüm</span><span class="sxs-lookup"><span data-stu-id="75eb5-112">Resolution</span></span>  
 <span data-ttu-id="75eb5-113">Çağrı emin <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> hemen önce gerçekleşir `try` deyimi.</span><span class="sxs-lookup"><span data-stu-id="75eb5-113">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="75eb5-114">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="75eb5-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="75eb5-115">Bu mda'nın CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="75eb5-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="75eb5-116">Çıkış</span><span class="sxs-lookup"><span data-stu-id="75eb5-116">Output</span></span>  
 <span data-ttu-id="75eb5-117">MDA yöntem çağırma adını görüntüler <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> yöntemi, MSIL uzaklığı ve çağrı değil hemen önünde try bloğunun başlangıcı belirten bir ileti.</span><span class="sxs-lookup"><span data-stu-id="75eb5-117">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="75eb5-118">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="75eb5-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="75eb5-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="75eb5-119">Example</span></span>  
 <span data-ttu-id="75eb5-120">Aşağıdaki kod örneği, bu mda'nın etkinleştirilmesi neden desenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="75eb5-120">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="75eb5-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75eb5-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [<span data-ttu-id="75eb5-122">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="75eb5-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="75eb5-123">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="75eb5-123">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
