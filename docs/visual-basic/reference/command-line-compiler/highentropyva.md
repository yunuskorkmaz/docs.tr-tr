---
title: -highentropyva (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 58026ff84f1ff501bf767adebcfc01f7de5bf4a4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005575"
---
# <a name="-highentropyva-visual-basic"></a><span data-ttu-id="e9670-102">-highentropyva (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9670-102">-highentropyva (Visual Basic)</span></span>
<span data-ttu-id="e9670-103">64 bitlik bir yürütülebilir dosyanın mı yoksa [/Platform: anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) derleyicisi seçeneği tarafından işaretlenen bir yürütülebilir dosyanın yüksek Entrokten adres alanı düzeni rastgele SEÇIMINI (ASLR) destekleyip desteklemediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9670-103">Indicates whether a 64-bit executable or an executable that's marked by the [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9670-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9670-104">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e9670-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e9670-105">Arguments</span></span>  
 <span data-ttu-id="e9670-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="e9670-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="e9670-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e9670-107">Optional.</span></span> <span data-ttu-id="e9670-108">Seçenek varsayılan olarak kapalıdır veya `-highentropyva-` ' yı belirtirseniz.</span><span class="sxs-lookup"><span data-stu-id="e9670-108">The option is off by default or if you specify `-highentropyva-`.</span></span> <span data-ttu-id="e9670-109">@No__t-0 veya `-highentropyva+` ' i belirtirseniz bu seçenek açık olur.</span><span class="sxs-lookup"><span data-stu-id="e9670-109">The option is on if you specify `-highentropyva` or `-highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9670-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9670-110">Remarks</span></span>  
 <span data-ttu-id="e9670-111">Bu seçeneği belirtirseniz, Windows çekirdeğinin uyumlu sürümleri, çekirdek ASLR 'in bir parçası olarak bir işlemin adres alanı yerleşimini rasgele hale geldiğinde daha yüksek sayıda entropi kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="e9670-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="e9670-112">Çekirdek daha yüksek bir entropi kullanıyorsa, yığınlar ve yığınlar gibi bellek bölgelerine daha fazla sayıda adres tahsis edilebilir.</span><span class="sxs-lookup"><span data-stu-id="e9670-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="e9670-113">Sonuç olarak, belirli bir bellek bölgesinin konumunu tahmin etmek daha zordur.</span><span class="sxs-lookup"><span data-stu-id="e9670-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="e9670-114">Seçenek açık olduğunda, hedef yürütülebilir dosya ve bağımlı olduğu tüm modüller, bu modüller 64 bit işlem olarak çalışırken 4 gigabayttan (GB) büyük olan işaretçi değerlerini işleyebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e9670-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9670-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9670-115">See also</span></span>

- [<span data-ttu-id="e9670-116">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="e9670-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e9670-117">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="e9670-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
