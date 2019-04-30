---
title: -hıghentropyva (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: 2ff63ddc48a4f5c4287fe1badb092a1db93f68dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662861"
---
# <a name="-highentropyva-c-compiler-options"></a><span data-ttu-id="e81b0-102">-hıghentropyva (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e81b0-102">-highentropyva (C# Compiler Options)</span></span>
<span data-ttu-id="e81b0-103">**- Hıghentropyva** derleyici seçeneği, belirli bir yürütülebilir dosya yüksek entropi adres alanı düzeni rastgele seçimini (ASLR) destekleyip desteklemediğini Windows çekirdek söyler.</span><span class="sxs-lookup"><span data-stu-id="e81b0-103">The **-highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e81b0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e81b0-104">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e81b0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e81b0-105">Arguments</span></span>  
 <span data-ttu-id="e81b0-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="e81b0-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="e81b0-107">Bu seçenek belirten bir 64-bit yürütülebilir veya olarak işaretlenmiş bir yürütülebilir dosya [-platform: anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) derleyici seçeneği yüksek entropi sanal adres alanını destekler.</span><span class="sxs-lookup"><span data-stu-id="e81b0-107">This option specifies that a 64-bit executable or an executable that is marked by the [-platform:anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="e81b0-108">Seçeneği, varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="e81b0-108">The option is disabled by default.</span></span> <span data-ttu-id="e81b0-109">Kullanım **- hıghentropyva +** veya **- hıghentropyva** etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="e81b0-109">Use **-highentropyva+** or **-highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e81b0-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e81b0-110">Remarks</span></span>  
 <span data-ttu-id="e81b0-111">**- Hıghentropyva** seçeneği entropi daha yüksek derece ASLR bir parçası olarak bir işlemin adres alanı düzeni rasgeleleştirilirken yapılırken kullanılacak Windows çekirdek uyumlu sürümlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e81b0-111">The **-highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="e81b0-112">Daha yüksek derece entropi kullanarak bellek bölgelere yığınlarını ve Yığınlar gibi çok sayıda adresleri ayrılabilen anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e81b0-112">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="e81b0-113">Sonuç olarak, belirli bir bellek bölgesinin konumunu tahmin edilmesi daha zordur.</span><span class="sxs-lookup"><span data-stu-id="e81b0-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="e81b0-114">Zaman **- hıghentropyva** derleyici seçeneği belirtilmemişse, hedef çalıştırılabilir ve bağımlı tüm modülleri 64-bit işlem olarak çalıştırılırken, 4 gigabayt (GB) büyük bir işaretçi değerleri işleyebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e81b0-114">When the **-highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
