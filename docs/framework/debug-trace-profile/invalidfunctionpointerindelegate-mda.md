---
title: invalidFunctionPointerInDelegate MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5e9fd1faacc7be5b95e2bab0d8fdbee105e35498
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="185e4-102">invalidFunctionPointerInDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="185e4-102">invalidFunctionPointerInDelegate MDA</span></span>
<span data-ttu-id="185e4-103">`invalidFunctionPointerInDelegate` Yönetilen hata ayıklama Yardımcısı (MDA) bir yerel işlev işaretçisi bir temsilci oluşturmak için de bir geçersiz işlev işaretçisi geçirildiğinde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="185e4-103">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="185e4-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="185e4-104">Symptoms</span></span>  
 <span data-ttu-id="185e4-105">Erişim ihlalleri veya bir temsilci bir işlev işaretçisi kullanırken beklenmeyen Bellek Bozulması.</span><span class="sxs-lookup"><span data-stu-id="185e4-105">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="185e4-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="185e4-106">Cause</span></span>  
 <span data-ttu-id="185e4-107">Geçersiz işlev işaretçisi belirtildi.</span><span class="sxs-lookup"><span data-stu-id="185e4-107">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="185e4-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="185e4-108">Resolution</span></span>  
 <span data-ttu-id="185e4-109">Geçerli işlev işaretçisi belirtin</span><span class="sxs-lookup"><span data-stu-id="185e4-109">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="185e4-110">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="185e4-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="185e4-111">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="185e4-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="185e4-112">Çıkış</span><span class="sxs-lookup"><span data-stu-id="185e4-112">Output</span></span>  
 <span data-ttu-id="185e4-113">Geçersiz işlev işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="185e4-113">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="185e4-114">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="185e4-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="185e4-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="185e4-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="185e4-116">Yönetilen hata ayıklama Yardımcıları ile hataları tanılama</span><span class="sxs-lookup"><span data-stu-id="185e4-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="185e4-117">Birlikte çalışma hazırlama</span><span class="sxs-lookup"><span data-stu-id="185e4-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
