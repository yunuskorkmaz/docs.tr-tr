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
ms.openlocfilehash: a7fe0b33bbd77143da6d2f4a26b170e4d7afe1fb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104474"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="ccd03-102">pInvokeLog MDA</span><span class="sxs-lookup"><span data-stu-id="ccd03-102">pInvokeLog MDA</span></span>
<span data-ttu-id="ccd03-103">`pInvokeLog` Her benzersiz platform çağırma için yürütme sırasında kullanılan imza yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ccd03-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ccd03-104">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="ccd03-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="ccd03-105">Bu mda'nın CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ccd03-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ccd03-106">Çıkış</span><span class="sxs-lookup"><span data-stu-id="ccd03-106">Output</span></span>  
 <span data-ttu-id="ccd03-107">Platform belirten bir ileti, yürütme sırasında kullanılan imza çağırın.</span><span class="sxs-lookup"><span data-stu-id="ccd03-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="ccd03-108">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ccd03-108">Configuration</span></span>  
 <span data-ttu-id="ccd03-109">Hangi platformu .dll dosyaları çağrılarını çağırmak her eşleşme öğesi filtreleri yapılır.</span><span class="sxs-lookup"><span data-stu-id="ccd03-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ccd03-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccd03-110">See also</span></span>

- [<span data-ttu-id="ccd03-111">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="ccd03-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="ccd03-112">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="ccd03-112">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
