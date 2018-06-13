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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 847ec4d861136b46383ce7d3801764f3d962049e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390880"
---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="eddb7-102">invalidFunctionPointerInDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="eddb7-102">invalidFunctionPointerInDelegate MDA</span></span>
<span data-ttu-id="eddb7-103">`invalidFunctionPointerInDelegate` Yönetilen hata ayıklama Yardımcısı (MDA) bir yerel işlev işaretçisi bir temsilci oluşturmak için de bir geçersiz işlev işaretçisi geçirildiğinde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="eddb7-103">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="eddb7-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="eddb7-104">Symptoms</span></span>  
 <span data-ttu-id="eddb7-105">Erişim ihlalleri veya bir temsilci bir işlev işaretçisi kullanırken beklenmeyen Bellek Bozulması.</span><span class="sxs-lookup"><span data-stu-id="eddb7-105">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="eddb7-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="eddb7-106">Cause</span></span>  
 <span data-ttu-id="eddb7-107">Geçersiz işlev işaretçisi belirtildi.</span><span class="sxs-lookup"><span data-stu-id="eddb7-107">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="eddb7-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="eddb7-108">Resolution</span></span>  
 <span data-ttu-id="eddb7-109">Geçerli işlev işaretçisi belirtin</span><span class="sxs-lookup"><span data-stu-id="eddb7-109">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="eddb7-110">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="eddb7-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="eddb7-111">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="eddb7-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="eddb7-112">Çıkış</span><span class="sxs-lookup"><span data-stu-id="eddb7-112">Output</span></span>  
 <span data-ttu-id="eddb7-113">Geçersiz işlev işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="eddb7-113">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="eddb7-114">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="eddb7-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eddb7-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eddb7-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="eddb7-116">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="eddb7-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="eddb7-117">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="eddb7-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
