---
title: dllMainReturnsFalse MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eb5de2b1c41d102fbf9fc47db0ff3d8bd72a3bcd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="cc0ce-102">dllMainReturnsFalse MDA</span><span class="sxs-lookup"><span data-stu-id="cc0ce-102">dllMainReturnsFalse MDA</span></span>
<span data-ttu-id="cc0ce-103">`dllMainReturnsFalse` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilirse, yönetilen `DllMain` DLL_PROCESS_ATTACH, sebeple adlı bir kullanıcı derlemesi işlevinin FALSE döndürür.</span><span class="sxs-lookup"><span data-stu-id="cc0ce-103">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="cc0ce-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="cc0ce-104">Symptoms</span></span>  
 <span data-ttu-id="cc0ce-105">`DllMain` İşlevi döndürülen FALSE, onu düzgün yürütmediği olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cc0ce-105">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="cc0ce-106">Bunun nedeni belirlenmemiş sorunlara neden olabilir `DllMain` işlevleri genellikle önemli başlatma kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="cc0ce-106">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="cc0ce-107">Sebep</span><span class="sxs-lookup"><span data-stu-id="cc0ce-107">Cause</span></span>  
 <span data-ttu-id="cc0ce-108">`DllMain` İşlevi DLL başlatma yük üzerine DLL_PROCESS_ATTACH nedeni ile çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="cc0ce-108">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="cc0ce-109">FALSE değeri döndürülürse, bu DLL başlatma başarısız oldu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cc0ce-109">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="cc0ce-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="cc0ce-110">Resolution</span></span>  
 <span data-ttu-id="cc0ce-111">Kodu çözümleme `DllMain` başarısız DLL işlevini ve başlatma hatanın nedenini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="cc0ce-111">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="cc0ce-112">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="cc0ce-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="cc0ce-113">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="cc0ce-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="cc0ce-114">Dönüş değeri hakkında verileri yalnızca raporları `DllMain`.</span><span class="sxs-lookup"><span data-stu-id="cc0ce-114">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="cc0ce-115">Çıkış</span><span class="sxs-lookup"><span data-stu-id="cc0ce-115">Output</span></span>  
 <span data-ttu-id="cc0ce-116">Belirten bir ileti bir `DllMain` DLL_PROCESS_ATTACH, nedeni adlı işlevi, döndürülen FALSE.</span><span class="sxs-lookup"><span data-stu-id="cc0ce-116">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="cc0ce-117">Yalnızca bu MDA etkinleştirildiğine dikkat edin `DllMain` yönetilen kodda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cc0ce-117">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="cc0ce-118">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cc0ce-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cc0ce-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cc0ce-119">See Also</span></span>  
 [<span data-ttu-id="cc0ce-120">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="cc0ce-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
