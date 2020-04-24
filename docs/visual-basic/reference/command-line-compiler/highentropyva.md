---
title: -highentropyva
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 7934dcaada4675bf687624bef5ed1ea25e842832
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344245"
---
# <a name="-highentropyva-visual-basic"></a><span data-ttu-id="bf83d-102">-highentropyva (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf83d-102">-highentropyva (Visual Basic)</span></span>
<span data-ttu-id="bf83d-103">64 bitlik bir yürütülebilirin veya [-Platform: anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) derleyici seçeneği tarafından işaretlenen bir yürütülebilir dosyanın yüksek Entroksiz adres alanı düzeni rastgele SEÇIMINI (ASLR) destekleyip desteklemediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf83d-103">Indicates whether a 64-bit executable or an executable that's marked by the [-platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf83d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf83d-104">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="bf83d-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="bf83d-105">Arguments</span></span>  
 <span data-ttu-id="bf83d-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="bf83d-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="bf83d-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bf83d-107">Optional.</span></span> <span data-ttu-id="bf83d-108">Seçeneği varsayılan olarak veya öğesini belirtirseniz `-highentropyva-`kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf83d-108">The option is off by default or if you specify `-highentropyva-`.</span></span> <span data-ttu-id="bf83d-109">Veya `-highentropyva` `-highentropyva+`belirtirseniz seçeneği açık olur.</span><span class="sxs-lookup"><span data-stu-id="bf83d-109">The option is on if you specify `-highentropyva` or `-highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf83d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf83d-110">Remarks</span></span>  
 <span data-ttu-id="bf83d-111">Bu seçeneği belirtirseniz, Windows çekirdeğinin uyumlu sürümleri, çekirdek ASLR 'in bir parçası olarak bir işlemin adres alanı yerleşimini rasgele hale geldiğinde daha yüksek sayıda entropi kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="bf83d-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="bf83d-112">Çekirdek daha yüksek bir entropi kullanıyorsa, yığınlar ve yığınlar gibi bellek bölgelerine daha fazla sayıda adres tahsis edilebilir.</span><span class="sxs-lookup"><span data-stu-id="bf83d-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="bf83d-113">Sonuç olarak, belirli bir bellek bölgesinin konumunu tahmin etmek daha zordur.</span><span class="sxs-lookup"><span data-stu-id="bf83d-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="bf83d-114">Seçenek açık olduğunda, hedef yürütülebilir dosya ve bağımlı olduğu tüm modüller, bu modüller 64 bit işlem olarak çalışırken 4 gigabayttan (GB) büyük olan işaretçi değerlerini işleyebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="bf83d-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf83d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf83d-115">See also</span></span>

- [<span data-ttu-id="bf83d-116">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="bf83d-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="bf83d-117">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="bf83d-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
