---
description: Daha fazla bilgi edinin:-highentropyva (Visual Basic)
title: -highentropyva
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 90fc3713ae4f9a073a63a57c5b35114548e26cbb
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100470271"
---
# <a name="-highentropyva-visual-basic"></a><span data-ttu-id="c58d9-103">-highentropyva (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c58d9-103">-highentropyva (Visual Basic)</span></span>

<span data-ttu-id="c58d9-104">64 bitlik bir yürütülebilirin veya [-Platform: anycpu](platform.md) derleyici seçeneği tarafından işaretlenen bir yürütülebilir dosyanın yüksek Entroksiz adres alanı düzeni rastgele SEÇIMINI (ASLR) destekleyip desteklemediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c58d9-104">Indicates whether a 64-bit executable or an executable that's marked by the [-platform:anycpu](platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c58d9-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c58d9-105">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c58d9-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="c58d9-106">Arguments</span></span>  

 <span data-ttu-id="c58d9-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="c58d9-107">`+` &#124; `-`</span></span>  
 <span data-ttu-id="c58d9-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c58d9-108">Optional.</span></span> <span data-ttu-id="c58d9-109">Seçeneği varsayılan olarak veya öğesini belirtirseniz kapalıdır `-highentropyva-` .</span><span class="sxs-lookup"><span data-stu-id="c58d9-109">The option is off by default or if you specify `-highentropyva-`.</span></span> <span data-ttu-id="c58d9-110">Veya belirtirseniz seçeneği açık olur `-highentropyva` `-highentropyva+` .</span><span class="sxs-lookup"><span data-stu-id="c58d9-110">The option is on if you specify `-highentropyva` or `-highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c58d9-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c58d9-111">Remarks</span></span>  

 <span data-ttu-id="c58d9-112">Bu seçeneği belirtirseniz, Windows çekirdeğinin uyumlu sürümleri, çekirdek ASLR 'in bir parçası olarak bir işlemin adres alanı yerleşimini rasgele hale geldiğinde daha yüksek sayıda entropi kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="c58d9-112">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="c58d9-113">Çekirdek daha yüksek bir entropi kullanıyorsa, yığınlar ve yığınlar gibi bellek bölgelerine daha fazla sayıda adres tahsis edilebilir.</span><span class="sxs-lookup"><span data-stu-id="c58d9-113">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="c58d9-114">Sonuç olarak, belirli bir bellek bölgesinin konumunu tahmin etmek daha zordur.</span><span class="sxs-lookup"><span data-stu-id="c58d9-114">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="c58d9-115">Seçenek açık olduğunda, hedef yürütülebilir dosya ve bağımlı olduğu tüm modüller, bu modüller 64 bit işlem olarak çalışırken 4 gigabayttan (GB) büyük olan işaretçi değerlerini işleyebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="c58d9-115">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c58d9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c58d9-116">See also</span></span>

- [<span data-ttu-id="c58d9-117">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="c58d9-117">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="c58d9-118">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="c58d9-118">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
