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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61874113"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="9512b-102">pInvokeLog MDA</span><span class="sxs-lookup"><span data-stu-id="9512b-102">pInvokeLog MDA</span></span>
<span data-ttu-id="9512b-103">`pInvokeLog` Her benzersiz platform çağırma için yürütme sırasında kullanılan imza yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9512b-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9512b-104">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="9512b-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="9512b-105">Bu mda'nın CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9512b-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9512b-106">Çıkış</span><span class="sxs-lookup"><span data-stu-id="9512b-106">Output</span></span>  
 <span data-ttu-id="9512b-107">Platform belirten bir ileti, yürütme sırasında kullanılan imza çağırın.</span><span class="sxs-lookup"><span data-stu-id="9512b-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9512b-108">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9512b-108">Configuration</span></span>  
 <span data-ttu-id="9512b-109">Hangi platformu .dll dosyaları çağrılarını çağırmak her eşleşme öğesi filtreleri yapılır.</span><span class="sxs-lookup"><span data-stu-id="9512b-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9512b-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9512b-110">See also</span></span>

- [<span data-ttu-id="9512b-111">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="9512b-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="9512b-112">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="9512b-112">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
