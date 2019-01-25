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
ms.openlocfilehash: ff026ddd9f9dc7c1556c55b285958dad7139e8eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699317"
---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="ab05c-102">invalidFunctionPointerInDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="ab05c-102">invalidFunctionPointerInDelegate MDA</span></span>
<span data-ttu-id="ab05c-103">`invalidFunctionPointerInDelegate` Yönetilen hata ayıklama Yardımcısı (MDA) bir yerel işlev işaretçisi bir temsilci oluşturmak için bir geçersiz işlev işaretçisi geçtikten sonra etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ab05c-103">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ab05c-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="ab05c-104">Symptoms</span></span>  
 <span data-ttu-id="ab05c-105">Erişim ihlalleri veya bir temsilci bir işlev işaretçisi kullanılırken beklenmeyen Bellek Bozulması.</span><span class="sxs-lookup"><span data-stu-id="ab05c-105">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ab05c-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="ab05c-106">Cause</span></span>  
 <span data-ttu-id="ab05c-107">Geçersiz işlev işaretçi belirtildi.</span><span class="sxs-lookup"><span data-stu-id="ab05c-107">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ab05c-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="ab05c-108">Resolution</span></span>  
 <span data-ttu-id="ab05c-109">Geçerli işlev işaretçisi belirtin</span><span class="sxs-lookup"><span data-stu-id="ab05c-109">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ab05c-110">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="ab05c-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="ab05c-111">Bu mda'nın CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ab05c-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ab05c-112">Çıkış</span><span class="sxs-lookup"><span data-stu-id="ab05c-112">Output</span></span>  
 <span data-ttu-id="ab05c-113">Geçersiz işlev işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ab05c-113">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="ab05c-114">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ab05c-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab05c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab05c-115">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="ab05c-116">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="ab05c-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="ab05c-117">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="ab05c-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
