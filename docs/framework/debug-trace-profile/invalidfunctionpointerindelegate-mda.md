---
title: invalidFunctionPointerInDelegate MDA
description: Temsilci oluşturmak için geçersiz bir işlev işaretçisi geçirilirse çağrılan ınvalidfunctionpointerındelegate yönetilen hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- invalidFunctionPointerInDelegate MDA
- managed debugging assistants (MDAs), invalid function pointer to delegates
- MDAs (managed debugging assistants), invalid function pointer to delegates
- function pointers, invalid
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- invalid function pointers
ms.assetid: 99ae44f1-783e-49a9-9009-24f54bbd0f09
ms.openlocfilehash: 8072d35a45cb1e0590aa5533210d0e0f86913164
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272624"
---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="304a1-103">invalidFunctionPointerInDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="304a1-103">invalidFunctionPointerInDelegate MDA</span></span>

<span data-ttu-id="304a1-104">`invalidFunctionPointerInDelegate`Yönetilen hata ayıklama Yardımcısı (MDA), bir yerel işlev işaretçisi üzerinden temsilci oluşturmak için geçersiz bir işlev işaretçisi geçirildiğinde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="304a1-104">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="304a1-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="304a1-105">Symptoms</span></span>  

 <span data-ttu-id="304a1-106">Bir işlev işaretçisi üzerinde bir temsilci kullanılırken erişim ihlalleri veya beklenmedik bellek bozulması.</span><span class="sxs-lookup"><span data-stu-id="304a1-106">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="304a1-107">Nedeni</span><span class="sxs-lookup"><span data-stu-id="304a1-107">Cause</span></span>  

 <span data-ttu-id="304a1-108">Geçersiz bir işlev işaretçisi belirtildi.</span><span class="sxs-lookup"><span data-stu-id="304a1-108">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="304a1-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="304a1-109">Resolution</span></span>  

 <span data-ttu-id="304a1-110">Geçerli bir işlev işaretçisi belirtin</span><span class="sxs-lookup"><span data-stu-id="304a1-110">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="304a1-111">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="304a1-111">Effect on the Runtime</span></span>  

 <span data-ttu-id="304a1-112">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="304a1-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="304a1-113">Çıkış</span><span class="sxs-lookup"><span data-stu-id="304a1-113">Output</span></span>  

 <span data-ttu-id="304a1-114">Geçersiz işlev işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="304a1-114">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="304a1-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="304a1-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="304a1-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="304a1-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="304a1-117">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="304a1-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="304a1-118">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="304a1-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
