---
title: -hıghentropyva (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 5d948817d4bc71aa31c5890f6740248f4c309588
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181507"
---
# <a name="-highentropyva-visual-basic"></a><span data-ttu-id="84a30-102">-hıghentropyva (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84a30-102">-highentropyva (Visual Basic)</span></span>
<span data-ttu-id="84a30-103">Belirten bir 64-bit yürütülebilir dosya ya da tarafından işaretlenen bir yürütülebilir dosya [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) derleyici seçeneği yüksek entropi adres alanı düzeni rastgele seçimini (ASLR) destekler.</span><span class="sxs-lookup"><span data-stu-id="84a30-103">Indicates whether a 64-bit executable or an executable that's marked by the [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84a30-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84a30-104">Syntax</span></span>  
  
```  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="84a30-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="84a30-105">Arguments</span></span>  
 <span data-ttu-id="84a30-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="84a30-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="84a30-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="84a30-107">Optional.</span></span> <span data-ttu-id="84a30-108">Bu seçenek varsayılan olarak kapalıdır veya belirtirseniz `-highentropyva-`.</span><span class="sxs-lookup"><span data-stu-id="84a30-108">The option is off by default or if you specify `-highentropyva-`.</span></span> <span data-ttu-id="84a30-109">Belirtirseniz seçeneği açıktır `-highentropyva` veya `-highentropyva+`.</span><span class="sxs-lookup"><span data-stu-id="84a30-109">The option is on if you specify `-highentropyva` or `-highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84a30-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84a30-110">Remarks</span></span>  
 <span data-ttu-id="84a30-111">Bu seçeneği belirtirseniz, çekirdek bir işlemin adres alanı düzeni ASLR bir parçası olarak rasgele olarak belirler, daha yüksek derece entropi Windows çekirdek uyumlu sürümlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84a30-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="84a30-112">Çekirdek entropi daha yüksek derece kullanıyorsa, çok sayıda adresleri yığınlarını ve Yığınlar gibi bölgelere bellek ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="84a30-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="84a30-113">Sonuç olarak, belirli bir bellek bölgesinin konumunu tahmin edilmesi daha zordur.</span><span class="sxs-lookup"><span data-stu-id="84a30-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="84a30-114">Seçeneği, hedef çalıştırılabilir ve modüllerin açık olduğunda, bağımlı modüller 64-bit işlem çalışırken, 4 gigabayt (GB) büyük bir işaretçi değerleri işleyebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="84a30-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84a30-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="84a30-115">See Also</span></span>  
 [<span data-ttu-id="84a30-116">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="84a30-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="84a30-117">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="84a30-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
