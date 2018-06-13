---
title: -hıghentropyva (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fef3f922d3089eaca1762ffe35fa38cfe94baf22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656345"
---
# <a name="-highentropyva-visual-basic"></a><span data-ttu-id="666a2-102">-hıghentropyva (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="666a2-102">-highentropyva (Visual Basic)</span></span>
<span data-ttu-id="666a2-103">Gösteren bir 64-bit yürütülebilir dosya veya tarafından işaretlenen yürütülebilir bir dosya olup olmadığını [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) derleyici seçeneği yüksek entropi adres alanı düzeni rastgele seçimini (ASLR) destekler.</span><span class="sxs-lookup"><span data-stu-id="666a2-103">Indicates whether a 64-bit executable or an executable that's marked by the [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="666a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="666a2-104">Syntax</span></span>  
  
```  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="666a2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="666a2-105">Arguments</span></span>  
 <span data-ttu-id="666a2-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="666a2-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="666a2-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="666a2-107">Optional.</span></span> <span data-ttu-id="666a2-108">Seçeneği varsayılan olarak kapalıdır veya belirtirseniz `-highentropyva-`.</span><span class="sxs-lookup"><span data-stu-id="666a2-108">The option is off by default or if you specify `-highentropyva-`.</span></span> <span data-ttu-id="666a2-109">Seçenek açıksa belirtirseniz, `-highentropyva` veya `-highentropyva+`.</span><span class="sxs-lookup"><span data-stu-id="666a2-109">The option is on if you specify `-highentropyva` or `-highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="666a2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="666a2-110">Remarks</span></span>  
 <span data-ttu-id="666a2-111">Bu seçeneği belirtirseniz, çekirdek ASLR bir parçası olarak adres alanı düzeni bir işlemin randomizes zaman uyumlu sürümlerini Windows Çekirdeği entropi yüksek derece kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="666a2-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="666a2-112">Çekirdek entropi yüksek derece kullanıyorsa, çok sayıda adresleri yığınları ve yığın gibi bellek bölgelere ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="666a2-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="666a2-113">Sonuç olarak, belirli bellek bölge konumunu tahmin edilmesi daha zordur.</span><span class="sxs-lookup"><span data-stu-id="666a2-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="666a2-114">Seçenek hedef çalıştırılabilir ve herhangi bir modül, etkinleştirildiğinde, bağlı olduğu bu modüller, 64 bit işlemleri olarak çalıştırırken 4 gigabayt (GB) büyük işaretçi değerleri kaldırabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="666a2-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="666a2-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="666a2-115">See Also</span></span>  
 [<span data-ttu-id="666a2-116">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="666a2-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="666a2-117">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="666a2-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
