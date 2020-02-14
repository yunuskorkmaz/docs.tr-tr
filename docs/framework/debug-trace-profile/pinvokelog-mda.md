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
ms.openlocfilehash: 12d7f60bcaedc5a97a7718610f40188547f87050
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216125"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="038e6-102">pInvokeLog MDA</span><span class="sxs-lookup"><span data-stu-id="038e6-102">pInvokeLog MDA</span></span>
<span data-ttu-id="038e6-103">`pInvokeLog` yönetilen hata ayıklama Yardımcısı (MDA), yürütme sırasında kullanılan her bir benzersiz platform çağırma imzası için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="038e6-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="038e6-104">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="038e6-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="038e6-105">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="038e6-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="038e6-106">Çıktı</span><span class="sxs-lookup"><span data-stu-id="038e6-106">Output</span></span>  
 <span data-ttu-id="038e6-107">Yürütme sırasında kullanılan platform çağırma imzasını belirten bir ileti.</span><span class="sxs-lookup"><span data-stu-id="038e6-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="038e6-108">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="038e6-108">Configuration</span></span>  
 <span data-ttu-id="038e6-109">Her Match öğesi, platform çağırma çağrılarına yapılan. dll dosyalarını filtreler.</span><span class="sxs-lookup"><span data-stu-id="038e6-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="038e6-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="038e6-110">See also</span></span>

- [<span data-ttu-id="038e6-111">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="038e6-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="038e6-112">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="038e6-112">Consuming Unmanaged DLL Functions</span></span>](../interop/consuming-unmanaged-dll-functions.md)
