---
title: dllMainReturnsFalse MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
ms.openlocfilehash: 0b413521e0a2dc06c2ff0be642f080eaf541202f
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216441"
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="610d9-102">dllMainReturnsFalse MDA</span><span class="sxs-lookup"><span data-stu-id="610d9-102">dllMainReturnsFalse MDA</span></span>
<span data-ttu-id="610d9-103">`dllMainReturnsFalse` yönetilen hata ayıklama Yardımcısı (MDA), bir Kullanıcı derlemesinin yönetilen `DllMain` işlevi, neden DLL_PROCESS_ATTACH çağrıldığında etkinleştirilir, FALSE döndürür.</span><span class="sxs-lookup"><span data-stu-id="610d9-103">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="610d9-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="610d9-104">Symptoms</span></span>  
 <span data-ttu-id="610d9-105">`DllMain` işlevi, doğru şekilde yürütülmediğini belirten yanlış döndürdü.</span><span class="sxs-lookup"><span data-stu-id="610d9-105">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="610d9-106">`DllMain` işlevler tipik olarak önemli başlatma kodu içerdiği için bu, belirlenmemiş sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="610d9-106">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="610d9-107">Nedeni</span><span class="sxs-lookup"><span data-stu-id="610d9-107">Cause</span></span>  
 <span data-ttu-id="610d9-108">`DllMain` işlevi, yükleme sonrasında DLL başlatma için DLL_PROCESS_ATTACH neden ile çağırılır.</span><span class="sxs-lookup"><span data-stu-id="610d9-108">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="610d9-109">YANLıŞ döndürürse, DLL başlatması başarısız oldu demektir.</span><span class="sxs-lookup"><span data-stu-id="610d9-109">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="610d9-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="610d9-110">Resolution</span></span>  
 <span data-ttu-id="610d9-111">Başarısız DLL 'nin `DllMain` işlevinin kodunu çözümleyin ve başlatma hatasının nedenini belirler.</span><span class="sxs-lookup"><span data-stu-id="610d9-111">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="610d9-112">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="610d9-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="610d9-113">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="610d9-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="610d9-114">Yalnızca `DllMain`için dönüş değeri hakkındaki verileri raporlar.</span><span class="sxs-lookup"><span data-stu-id="610d9-114">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="610d9-115">Çıktı</span><span class="sxs-lookup"><span data-stu-id="610d9-115">Output</span></span>  
 <span data-ttu-id="610d9-116">DLL_PROCESS_ATTACH nedeni için çağrılan `DllMain` işlevinin yanlış döndürüldüğünü belirten bir ileti.</span><span class="sxs-lookup"><span data-stu-id="610d9-116">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="610d9-117">Bu MDA 'ın yalnızca `DllMain` yönetilen kodda uygulanmışsa etkinleştirildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="610d9-117">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="610d9-118">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="610d9-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="610d9-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="610d9-119">See also</span></span>

- [<span data-ttu-id="610d9-120">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="610d9-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
