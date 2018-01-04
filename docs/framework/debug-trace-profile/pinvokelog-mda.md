---
title: pInvokeLog MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 343ec424105d1c775592aba316b50da4010f7c8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="69f4b-102">pInvokeLog MDA</span><span class="sxs-lookup"><span data-stu-id="69f4b-102">pInvokeLog MDA</span></span>
<span data-ttu-id="69f4b-103">`pInvokeLog` Yönetilen hata ayıklama Yardımcısı (MDA) her benzersiz platform çağırma için yürütme sırasında kullanılan imzayı etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="69f4b-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="69f4b-104">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="69f4b-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="69f4b-105">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="69f4b-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="69f4b-106">Çıkış</span><span class="sxs-lookup"><span data-stu-id="69f4b-106">Output</span></span>  
 <span data-ttu-id="69f4b-107">Platform belirten bir ileti yürütme sırasında kullanılan imzayı çağırır.</span><span class="sxs-lookup"><span data-stu-id="69f4b-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="69f4b-108">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="69f4b-108">Configuration</span></span>  
 <span data-ttu-id="69f4b-109">Çağrıları .dll dosyaları için hangi platform çağırma her eşleme öğesi filtreleri yapılır.</span><span class="sxs-lookup"><span data-stu-id="69f4b-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="69f4b-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="69f4b-110">See Also</span></span>  
 [<span data-ttu-id="69f4b-111">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="69f4b-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="69f4b-112">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="69f4b-112">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
