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
ms.openlocfilehash: fe1d783017369a78074e5abf278ac2facf6ee32b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734071"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="9a303-102">pInvokeLog MDA</span><span class="sxs-lookup"><span data-stu-id="9a303-102">pInvokeLog MDA</span></span>
<span data-ttu-id="9a303-103">`pInvokeLog` Her benzersiz platform çağırma için yürütme sırasında kullanılan imza yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9a303-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9a303-104">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="9a303-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="9a303-105">Bu mda'nın CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9a303-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9a303-106">Çıkış</span><span class="sxs-lookup"><span data-stu-id="9a303-106">Output</span></span>  
 <span data-ttu-id="9a303-107">Platform belirten bir ileti, yürütme sırasında kullanılan imza çağırın.</span><span class="sxs-lookup"><span data-stu-id="9a303-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9a303-108">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9a303-108">Configuration</span></span>  
 <span data-ttu-id="9a303-109">Hangi platformu .dll dosyaları çağrılarını çağırmak her eşleşme öğesi filtreleri yapılır.</span><span class="sxs-lookup"><span data-stu-id="9a303-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9a303-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a303-110">See also</span></span>
- [<span data-ttu-id="9a303-111">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="9a303-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="9a303-112">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="9a303-112">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
