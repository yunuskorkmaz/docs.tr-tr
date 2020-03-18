---
title: -highentropyva (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: b710bb829f6a7591159d2f2e6bacc670d21c42d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606851"
---
# <a name="-highentropyva-c-compiler-options"></a><span data-ttu-id="98a6f-102">-highentropyva (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="98a6f-102">-highentropyva (C# Compiler Options)</span></span>
<span data-ttu-id="98a6f-103">**-highentropyva** derleyici seçeneği, Windows çekirdeğine belirli bir çalıştırılabilirin yüksek entropi Adres Alanı Düzeni Randomization'ı (ASLR) destekleyip desteklemediğini söyler.</span><span class="sxs-lookup"><span data-stu-id="98a6f-103">The **-highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98a6f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98a6f-104">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="98a6f-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="98a6f-105">Arguments</span></span>  
 <span data-ttu-id="98a6f-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="98a6f-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="98a6f-107">Bu seçenek, 64 bit çalıştırılabilir veya [-platform:anycpu](./platform-compiler-option.md) derleyici seçeneği ile işaretlenmiş bir yürütülebilir yüksek entropi sanal adres alanını desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="98a6f-107">This option specifies that a 64-bit executable or an executable that is marked by the [-platform:anycpu](./platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="98a6f-108">Seçenek varsayılan olarak devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="98a6f-108">The option is disabled by default.</span></span> <span data-ttu-id="98a6f-109">Bunu etkinleştirmek için **-highentropyva+** veya **-highentropyva** kullanın.</span><span class="sxs-lookup"><span data-stu-id="98a6f-109">Use **-highentropyva+** or **-highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98a6f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98a6f-110">Remarks</span></span>  
 <span data-ttu-id="98a6f-111">**-highentropyva** seçeneği, ASLR'Nin bir parçası olarak bir işlemin adres alanı düzenini rasgele belirlerken Windows çekirdeğinin uyumlu sürümlerinin daha yüksek derecede entropi kullanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="98a6f-111">The **-highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="98a6f-112">Daha yüksek entropi derecelerinin kullanılması, yığınlar ve yığınlar gibi bellek bölgelerine daha fazla sayıda adres ayrılabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="98a6f-112">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="98a6f-113">Sonuç olarak, belirli bir bellek bölgesinin konumunu tahmin etmek daha zordur.</span><span class="sxs-lookup"><span data-stu-id="98a6f-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="98a6f-114">**-highentropyva** derleyicisi seçeneği belirtildiğinde, hedef çalıştırılabilir ve bağlı olduğu tüm modüller, 64 bit işlem olarak çalışırken 4 gigabayttan (GB) daha büyük işaretçi değerlerini işleyebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="98a6f-114">When the **-highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
