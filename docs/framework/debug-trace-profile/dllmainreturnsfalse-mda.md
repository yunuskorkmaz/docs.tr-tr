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
ms.openlocfilehash: adc05ae9bd357c142ff09de069aff446b5ea60e8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052853"
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="eb083-102">dllMainReturnsFalse MDA</span><span class="sxs-lookup"><span data-stu-id="eb083-102">dllMainReturnsFalse MDA</span></span>
<span data-ttu-id="eb083-103">Yönetilen hata ayıklama Yardımcısı (MDA), DLL_PROCESS_ATTACH nedeni ile çağrılan `DllMain` bir Kullanıcı derlemesinin yönetilen işlevi false değerini döndürürse etkinleştirilir. `dllMainReturnsFalse`</span><span class="sxs-lookup"><span data-stu-id="eb083-103">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="eb083-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="eb083-104">Symptoms</span></span>  
 <span data-ttu-id="eb083-105">`DllMain` İşlev, doğru şekilde yürütülmediğini belirten yanlış olarak döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="eb083-105">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="eb083-106">Bu, `DllMain` işlev genellikle önemli başlatma kodu içerdiği için belirlenmeyen sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="eb083-106">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="eb083-107">Sebep</span><span class="sxs-lookup"><span data-stu-id="eb083-107">Cause</span></span>  
 <span data-ttu-id="eb083-108">İşlev `DllMain` , yükleme sonrasında DLL_PROCESS_ATTACH for dll başlatması nedeniyle çağrılır.</span><span class="sxs-lookup"><span data-stu-id="eb083-108">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="eb083-109">YANLıŞ döndürürse, DLL başlatması başarısız oldu demektir.</span><span class="sxs-lookup"><span data-stu-id="eb083-109">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="eb083-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="eb083-110">Resolution</span></span>  
 <span data-ttu-id="eb083-111">Başarısız olan dll `DllMain` işlevinin kodunu çözümleyin ve başlatma hatasının nedenini belirler.</span><span class="sxs-lookup"><span data-stu-id="eb083-111">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="eb083-112">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="eb083-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="eb083-113">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="eb083-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="eb083-114">Yalnızca dönüş değeri `DllMain`ile ilgili verileri raporlar.</span><span class="sxs-lookup"><span data-stu-id="eb083-114">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="eb083-115">Çıkış</span><span class="sxs-lookup"><span data-stu-id="eb083-115">Output</span></span>  
 <span data-ttu-id="eb083-116">DLL_PROCESS_ATTACH nedeni için çağrılan bir `DllMain` işlevin yanlış döndürüldüğünü belirten bir ileti.</span><span class="sxs-lookup"><span data-stu-id="eb083-116">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="eb083-117">Bu mda 'ın yalnızca `DllMain` yönetilen kodda uygulanmışsa etkinleştirildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="eb083-117">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="eb083-118">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="eb083-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb083-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb083-119">See also</span></span>

- [<span data-ttu-id="eb083-120">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="eb083-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
