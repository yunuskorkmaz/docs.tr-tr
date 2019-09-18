---
title: pInvokeLog MDA
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0883849eee12922601e50c2337bb0048d77cab68
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052370"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="fc2fc-102">pInvokeLog MDA</span><span class="sxs-lookup"><span data-stu-id="fc2fc-102">pInvokeLog MDA</span></span>
<span data-ttu-id="fc2fc-103">Yönetilen `pInvokeLog` hata ayıklama Yardımcısı (MDA), yürütme sırasında kullanılan her benzersiz platform çağırma imzası için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fc2fc-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="fc2fc-104">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="fc2fc-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="fc2fc-105">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="fc2fc-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="fc2fc-106">Çıkış</span><span class="sxs-lookup"><span data-stu-id="fc2fc-106">Output</span></span>  
 <span data-ttu-id="fc2fc-107">Yürütme sırasında kullanılan platform çağırma imzasını belirten bir ileti.</span><span class="sxs-lookup"><span data-stu-id="fc2fc-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="fc2fc-108">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fc2fc-108">Configuration</span></span>  
 <span data-ttu-id="fc2fc-109">Her Match öğesi, platform çağırma çağrılarına yapılan. dll dosyalarını filtreler.</span><span class="sxs-lookup"><span data-stu-id="fc2fc-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeLog>  
      <filter>  
        <match dllName="user32.dll"/>  
        <match dllName="kernel32.dll"/>  
      </filter>  
    </pInvokeLog>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc2fc-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc2fc-110">See also</span></span>

- [<span data-ttu-id="fc2fc-111">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="fc2fc-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="fc2fc-112">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="fc2fc-112">Consuming Unmanaged DLL Functions</span></span>](../interop/consuming-unmanaged-dll-functions.md)
