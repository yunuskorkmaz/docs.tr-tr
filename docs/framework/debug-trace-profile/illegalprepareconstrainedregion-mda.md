---
title: illegalPrepareConstrainedRegion MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: dad43859e6bec288b66c6c10256a6b2cbc1bbe0d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="a83af-102">illegalPrepareConstrainedRegion MDA</span><span class="sxs-lookup"><span data-stu-id="a83af-102">illegalPrepareConstrainedRegion MDA</span></span>
<span data-ttu-id="a83af-103">`illegalPrepareConstrainedRegion` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş olduğunda bir <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> yöntem çağrısı yok hemen önünde `try` özel durum işleyici ifadesi.</span><span class="sxs-lookup"><span data-stu-id="a83af-103">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="a83af-104">Kaynak kodu oluşturma çağrısı arasında sahip izin verilebilir mi bu kısıtlama MSIL düzeyi, olduğundan ve `try`, Yorumlar gibi.</span><span class="sxs-lookup"><span data-stu-id="a83af-104">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a83af-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="a83af-105">Symptoms</span></span>  
 <span data-ttu-id="a83af-106">Hiçbir zaman, bu nedenle ancak blok işleme basit bir özel durum olarak kabul edilir kısıtlı yürütme bölge (CER) (`finally` veya `catch`).</span><span class="sxs-lookup"><span data-stu-id="a83af-106">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="a83af-107">Sonuç olarak, bölge bellek yetersiz koşul veya bir iş parçacığı iptal olayında çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="a83af-107">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a83af-108">Sebep</span><span class="sxs-lookup"><span data-stu-id="a83af-108">Cause</span></span>  
 <span data-ttu-id="a83af-109">Bir CER için hazırlık deseni doğru gelmez.</span><span class="sxs-lookup"><span data-stu-id="a83af-109">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="a83af-110">Bir hata olayı budur.</span><span class="sxs-lookup"><span data-stu-id="a83af-110">This is an error event.</span></span> <span data-ttu-id="a83af-111"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> Özel durum işleyicileri bir CER giriş olarak işaretlemek için kullanılan yöntem çağrısı kendi `catch` / `finally` / `fault` / `filter` blokları kullanılan, hemen önce `try` deyimi.</span><span class="sxs-lookup"><span data-stu-id="a83af-111">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a83af-112">Çözüm</span><span class="sxs-lookup"><span data-stu-id="a83af-112">Resolution</span></span>  
 <span data-ttu-id="a83af-113">Çağrı emin <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> hemen önce gerçekleşir `try` deyimi.</span><span class="sxs-lookup"><span data-stu-id="a83af-113">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a83af-114">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="a83af-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="a83af-115">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a83af-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a83af-116">Çıkış</span><span class="sxs-lookup"><span data-stu-id="a83af-116">Output</span></span>  
 <span data-ttu-id="a83af-117">Yöntem çağırma adını MDA görüntüler <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> yöntemi, MSIL uzaklık ve çağrı değil hemen önünde deneyin blok başlangıcı belirten bir ileti.</span><span class="sxs-lookup"><span data-stu-id="a83af-117">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a83af-118">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a83af-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="a83af-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="a83af-119">Example</span></span>  
 <span data-ttu-id="a83af-120">Aşağıdaki kod örneği, bu mda'nın etkinleştirilmesi neden düzeni gösterir.</span><span class="sxs-lookup"><span data-stu-id="a83af-120">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="a83af-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a83af-121">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>  
 [<span data-ttu-id="a83af-122">Yönetilen hata ayıklama Yardımcıları ile hataları tanılama</span><span class="sxs-lookup"><span data-stu-id="a83af-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="a83af-123">Birlikte çalışma hazırlama</span><span class="sxs-lookup"><span data-stu-id="a83af-123">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
