---
title: illegalPrepareConstrainedRegion MDA
description: İllegalPrepareConstrainedRegion Managed hata ayıklama Yardımcısı ' nı gözden geçirin ve bir PrepareConstrainedRegions çağrısının ardından bir TRY deyiminden sonra çağrılır.
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
ms.openlocfilehash: 7cbf04e8605ccf18e89882dd09b96cc7c59330c9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272793"
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="efa80-103">illegalPrepareConstrainedRegion MDA</span><span class="sxs-lookup"><span data-stu-id="efa80-103">illegalPrepareConstrainedRegion MDA</span></span>

<span data-ttu-id="efa80-104">`illegalPrepareConstrainedRegion`Yönetilen hata ayıklama Yardımcısı (MDA), bir <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> Yöntem çağrısı `try` özel durum işleyicisinin ifadesinden hemen önce gelmediğinde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="efa80-104">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="efa80-105">Bu kısıtlama MSIL düzeyindedir, bu nedenle çağrı ile yorum gibi kod oluşturma olmayan kaynağa izin verilir `try` .</span><span class="sxs-lookup"><span data-stu-id="efa80-105">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="efa80-106">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="efa80-106">Symptoms</span></span>  

 <span data-ttu-id="efa80-107">Bu, basit bir özel durum işleme bloğu (veya) olarak hiçbir şekilde kabul edilen kısıtlı bir yürütme bölgesi (CER `finally` ) `catch` .</span><span class="sxs-lookup"><span data-stu-id="efa80-107">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="efa80-108">Sonuç olarak, bölge bellek dışı bir koşul veya bir iş parçacığı iptali durumunda çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="efa80-108">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="efa80-109">Nedeni</span><span class="sxs-lookup"><span data-stu-id="efa80-109">Cause</span></span>  

 <span data-ttu-id="efa80-110">Bir CER için hazırlık deseninin doğru şekilde izlenmiyor.</span><span class="sxs-lookup"><span data-stu-id="efa80-110">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="efa80-111">Bu bir hata olayıdır.</span><span class="sxs-lookup"><span data-stu-id="efa80-111">This is an error event.</span></span> <span data-ttu-id="efa80-112"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>Özel durum işleyicilerini blok içindeki bir cer ile tanışın olarak işaretlemek için kullanılan yöntem çağrısı `catch` / `finally` / `fault` / `filter` , deyimden hemen önce kullanılmalıdır `try` .</span><span class="sxs-lookup"><span data-stu-id="efa80-112">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="efa80-113">Çözüm</span><span class="sxs-lookup"><span data-stu-id="efa80-113">Resolution</span></span>  

 <span data-ttu-id="efa80-114">Çağrısının <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> , deyimden hemen önce yapıldığından emin olun `try` .</span><span class="sxs-lookup"><span data-stu-id="efa80-114">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="efa80-115">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="efa80-115">Effect on the Runtime</span></span>  

 <span data-ttu-id="efa80-116">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="efa80-116">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="efa80-117">Çıkış</span><span class="sxs-lookup"><span data-stu-id="efa80-117">Output</span></span>  

 <span data-ttu-id="efa80-118">MDA, yöntemi çağıran yöntemin adını <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> , MSIL farkını ve çağrının try bloğunun başlangıcından hemen önce gelmesini belirten bir iletiyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="efa80-118">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="efa80-119">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="efa80-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="efa80-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="efa80-120">Example</span></span>  

 <span data-ttu-id="efa80-121">Aşağıdaki kod örneği, bu MDA 'ın etkinleştirilmesini sağlayan bir model gösterir.</span><span class="sxs-lookup"><span data-stu-id="efa80-121">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="efa80-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="efa80-122">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [<span data-ttu-id="efa80-123">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="efa80-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="efa80-124">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="efa80-124">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
