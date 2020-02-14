---
title: invalidFunctionPointerInDelegate MDA
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
ms.openlocfilehash: 723f51e14c314bde40c34d629ba7fc4f6276c633
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217372"
---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="b7031-102">invalidFunctionPointerInDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="b7031-102">invalidFunctionPointerInDelegate MDA</span></span>
<span data-ttu-id="b7031-103">`invalidFunctionPointerInDelegate` yönetilen hata ayıklama Yardımcısı (MDA), bir yerel işlev işaretçisi üzerinden temsilci oluşturmak için geçersiz bir işlev işaretçisi geçirildiğinde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b7031-103">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b7031-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="b7031-104">Symptoms</span></span>  
 <span data-ttu-id="b7031-105">Bir işlev işaretçisi üzerinde bir temsilci kullanılırken erişim ihlalleri veya beklenmedik bellek bozulması.</span><span class="sxs-lookup"><span data-stu-id="b7031-105">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b7031-106">Nedeni</span><span class="sxs-lookup"><span data-stu-id="b7031-106">Cause</span></span>  
 <span data-ttu-id="b7031-107">Geçersiz bir işlev işaretçisi belirtildi.</span><span class="sxs-lookup"><span data-stu-id="b7031-107">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="b7031-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="b7031-108">Resolution</span></span>  
 <span data-ttu-id="b7031-109">Geçerli bir işlev işaretçisi belirtin</span><span class="sxs-lookup"><span data-stu-id="b7031-109">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b7031-110">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="b7031-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="b7031-111">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b7031-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b7031-112">Çıktı</span><span class="sxs-lookup"><span data-stu-id="b7031-112">Output</span></span>  
 <span data-ttu-id="b7031-113">Geçersiz işlev işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b7031-113">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b7031-114">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b7031-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b7031-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7031-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="b7031-116">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="b7031-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="b7031-117">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="b7031-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
