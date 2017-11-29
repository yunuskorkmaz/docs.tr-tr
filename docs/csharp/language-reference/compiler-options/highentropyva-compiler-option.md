---
title: "-highentropyva (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5746caed8c1bf61038c97a49987c4c168eef9f3f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="highentropyva-c-compiler-options"></a><span data-ttu-id="c2f96-102">/highentropyva (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="c2f96-102">/highentropyva (C# Compiler Options)</span></span>
<span data-ttu-id="c2f96-103">**/Highentropyva** derleyici seçeneği, belirli bir yürütülebilir dosya yüksek entropi adres alanı düzeni rastgele seçimini (ASLR) destekleyip desteklemediğini Windows Çekirdeği söyler.</span><span class="sxs-lookup"><span data-stu-id="c2f96-103">The **/highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2f96-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2f96-104">Syntax</span></span>  
  
```console  
/highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c2f96-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c2f96-105">Arguments</span></span>  
 <span data-ttu-id="c2f96-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="c2f96-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="c2f96-107">Bu seçenek belirleyen bir 64-bit yürütülebilir dosya veya tarafından işaretlenen yürütülebilir [/platform:anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) derleyici seçeneği yüksek entropi sanal adres alanı destekler.</span><span class="sxs-lookup"><span data-stu-id="c2f96-107">This option specifies that a 64-bit executable or an executable that is marked by the [/platform:anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="c2f96-108">Seçeneği, varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="c2f96-108">The option is disabled by default.</span></span> <span data-ttu-id="c2f96-109">Kullanım **/highentropyva+** veya **/highentropyva** etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="c2f96-109">Use **/highentropyva+** or **/highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2f96-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c2f96-110">Remarks</span></span>  
 <span data-ttu-id="c2f96-111">**/Highentropyva** seçeneği ASLR bir parçası olarak adres alanı düzeni bir işlemin rasgeleleştirilirken entropi yüksek derece kullanacak şekilde Windows çekirdek uyumlu sürümlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2f96-111">The **/highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="c2f96-112">Dağınık yüksek derece kullanarak çok sayıda adresleri bellek bölgelere yığınları ve yığın gibi ayrılabilen anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c2f96-112">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="c2f96-113">Sonuç olarak, belirli bellek bölge konumunu tahmin edilmesi daha zordur.</span><span class="sxs-lookup"><span data-stu-id="c2f96-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="c2f96-114">Zaman **/highentropyva** derleyici seçeneği belirtilmişse, hedef çalıştırılabilir ve bağımlı herhangi bir modül bir 64-bit işlem olarak çalıştırılırken 4 gigabayt (GB) büyük işaretçi değerleri kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="c2f96-114">When the **/highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
