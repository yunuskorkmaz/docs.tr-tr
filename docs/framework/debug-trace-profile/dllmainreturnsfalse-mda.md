---
title: dllMainReturnsFalse MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd987cea78d082eee26032d5f98a54dc0cd3e1d5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072629"
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="7a70e-102">dllMainReturnsFalse MDA</span><span class="sxs-lookup"><span data-stu-id="7a70e-102">dllMainReturnsFalse MDA</span></span>
<span data-ttu-id="7a70e-103">`dllMainReturnsFalse` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilirse, yönetilen `DllMain` DLL_PROCESS_ATTACH, sebeple adlı bir kullanıcı derlemesinin işlev FALSE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7a70e-103">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7a70e-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="7a70e-104">Symptoms</span></span>  
 <span data-ttu-id="7a70e-105">`DllMain` İşlevi, düzgün çalıştırılamadı olduğunu belirten FALSE döndürdü.</span><span class="sxs-lookup"><span data-stu-id="7a70e-105">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="7a70e-106">Bunun nedeni belirlenmemiş sorunlarına yol açabilir `DllMain` işlevleri genellikle önemli başlatma kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="7a70e-106">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7a70e-107">Sebep</span><span class="sxs-lookup"><span data-stu-id="7a70e-107">Cause</span></span>  
 <span data-ttu-id="7a70e-108">`DllMain` DLL başlatma sırasında yük DLL_PROCESS_ATTACH nedeni ile işlevi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7a70e-108">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="7a70e-109">FALSE döndürürse, bu DLL başlatma başarısız oldu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7a70e-109">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7a70e-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="7a70e-110">Resolution</span></span>  
 <span data-ttu-id="7a70e-111">Kodu çözümleme `DllMain` başarısız DLL işlevini ve başlatma hatanın nedenini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="7a70e-111">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7a70e-112">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="7a70e-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="7a70e-113">Bu mda'nın CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="7a70e-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="7a70e-114">Dönüş değeri hakkında veri yalnızca raporlar `DllMain`.</span><span class="sxs-lookup"><span data-stu-id="7a70e-114">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7a70e-115">Çıkış</span><span class="sxs-lookup"><span data-stu-id="7a70e-115">Output</span></span>  
 <span data-ttu-id="7a70e-116">Belirten bir ileti bir `DllMain` nedeni DLL_PROCESS_ATTACH, çağrılan işlev, FALSE döndürdü.</span><span class="sxs-lookup"><span data-stu-id="7a70e-116">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="7a70e-117">Yalnızca bu mda'nın etkinleştirilmiş olduğunu Not `DllMain` yönetilen kodda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7a70e-117">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="7a70e-118">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7a70e-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a70e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a70e-119">See also</span></span>

- [<span data-ttu-id="7a70e-120">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="7a70e-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
