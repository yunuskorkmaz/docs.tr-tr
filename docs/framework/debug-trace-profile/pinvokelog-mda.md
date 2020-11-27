---
title: pInvokeLog MDA
description: .NET ' te yürütme sırasında kullanılan her benzersiz platform çağırma imzası için etkinleştirilen pInvokeLog Managed hata ayıklama Yardımcısı 'nı (MDA) anlayın.
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
ms.openlocfilehash: b8cb4805663a2b28a133f98503730199af695c4f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271466"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="e33e8-103">pInvokeLog MDA</span><span class="sxs-lookup"><span data-stu-id="e33e8-103">pInvokeLog MDA</span></span>

<span data-ttu-id="e33e8-104">`pInvokeLog`Yönetilen hata ayıklama Yardımcısı (MDA), yürütme sırasında kullanılan her benzersiz platform çağırma imzası için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e33e8-104">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e33e8-105">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="e33e8-105">Effect on the Runtime</span></span>  

 <span data-ttu-id="e33e8-106">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e33e8-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e33e8-107">Çıkış</span><span class="sxs-lookup"><span data-stu-id="e33e8-107">Output</span></span>  

 <span data-ttu-id="e33e8-108">Yürütme sırasında kullanılan platform çağırma imzasını belirten bir ileti.</span><span class="sxs-lookup"><span data-stu-id="e33e8-108">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e33e8-109">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e33e8-109">Configuration</span></span>  

 <span data-ttu-id="e33e8-110">Her Match öğesi, platform çağırma çağrılarına yapılan. dll dosyalarını filtreler.</span><span class="sxs-lookup"><span data-stu-id="e33e8-110">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e33e8-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e33e8-111">See also</span></span>

- [<span data-ttu-id="e33e8-112">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="e33e8-112">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e33e8-113">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="e33e8-113">Consuming Unmanaged DLL Functions</span></span>](../interop/consuming-unmanaged-dll-functions.md)
