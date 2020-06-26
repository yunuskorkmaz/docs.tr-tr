---
title: dllMainReturnsFalse MDA
description: .NET 'teki dllMainReturnsFalse Managed hata ayıklama Yardımcısı hakkında bilgi edinin. Bu MDA, DLL başlatması başarısız olursa etkinleştirilir.
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
ms.openlocfilehash: 21d5e37d6823876e07cf5b2cbb881c1cf8b47b11
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416063"
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="ca581-104">dllMainReturnsFalse MDA</span><span class="sxs-lookup"><span data-stu-id="ca581-104">dllMainReturnsFalse MDA</span></span>
<span data-ttu-id="ca581-105">`dllMainReturnsFalse`Yönetilen hata ayıklama Yardımcısı (MDA), `DllMain` bir Kullanıcı derlemesinin yönetilen işlevi DLL_PROCESS_ATTACH neden ile çağrıldığında ETKINLEŞTIRILIR, false döndürür.</span><span class="sxs-lookup"><span data-stu-id="ca581-105">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ca581-106">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="ca581-106">Symptoms</span></span>  
 <span data-ttu-id="ca581-107">`DllMain`İşlev, doğru şekilde yürütülmediğini BELIRTEN yanlış olarak döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ca581-107">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="ca581-108">Bu, `DllMain` işlev genellikle önemli başlatma kodu içerdiği için belirlenmeyen sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ca581-108">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ca581-109">Nedeni</span><span class="sxs-lookup"><span data-stu-id="ca581-109">Cause</span></span>  
 <span data-ttu-id="ca581-110">`DllMain`İşlev, yük SıRASıNDA dll başlatması için DLL_PROCESS_ATTACH neden ile çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ca581-110">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="ca581-111">YANLıŞ döndürürse, DLL başlatması başarısız oldu demektir.</span><span class="sxs-lookup"><span data-stu-id="ca581-111">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ca581-112">Çözüm</span><span class="sxs-lookup"><span data-stu-id="ca581-112">Resolution</span></span>  
 <span data-ttu-id="ca581-113">`DllMain`Başarısız olan DLL işlevinin kodunu çözümleyin ve başlatma hatasının nedenini belirler.</span><span class="sxs-lookup"><span data-stu-id="ca581-113">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ca581-114">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="ca581-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="ca581-115">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ca581-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="ca581-116">Yalnızca dönüş değeri ile ilgili verileri raporlar `DllMain` .</span><span class="sxs-lookup"><span data-stu-id="ca581-116">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ca581-117">Çıktı</span><span class="sxs-lookup"><span data-stu-id="ca581-117">Output</span></span>  
 <span data-ttu-id="ca581-118">`DllMain`DLL_PROCESS_ATTACH nedeni için çağrılan bir IŞLEVIN yanlış döndürüldüğünü belirten bir ileti.</span><span class="sxs-lookup"><span data-stu-id="ca581-118">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="ca581-119">Bu MDA 'ın yalnızca `DllMain` yönetilen kodda uygulanmışsa etkinleştirildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ca581-119">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="ca581-120">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ca581-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ca581-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca581-121">See also</span></span>

- [<span data-ttu-id="ca581-122">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="ca581-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
