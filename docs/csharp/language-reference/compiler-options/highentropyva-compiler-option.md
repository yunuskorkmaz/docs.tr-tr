---
description: -highentropyva (C# derleyici seçenekleri)
title: -highentropyva (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: f3cdeb5e63d632fecbbd94501558cc53c28a918a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173210"
---
# <a name="-highentropyva-c-compiler-options"></a><span data-ttu-id="368c5-103">-highentropyva (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="368c5-103">-highentropyva (C# Compiler Options)</span></span>

<span data-ttu-id="368c5-104">**-Highentropyva** derleyici seçeneği Windows çekirdeğine, belirli bir yürütülebilir dosyanın yüksek entropi adres alanı düzeni rastgele SEÇIMINI (ASLR) destekleyip desteklemediğini söyler.</span><span class="sxs-lookup"><span data-stu-id="368c5-104">The **-highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="368c5-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="368c5-105">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="368c5-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="368c5-106">Arguments</span></span>  

 <span data-ttu-id="368c5-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="368c5-107">`+` &#124; `-`</span></span>  
 <span data-ttu-id="368c5-108">Bu seçenek, 64 bitlik bir yürütülebilir dosyanın veya [-Platform: anycpu](./platform-compiler-option.md) derleyicisi seçeneği tarafından işaretlenen bir yürütülebilir dosyanın yüksek bir entropi sanal adres alanını desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="368c5-108">This option specifies that a 64-bit executable or an executable that is marked by the [-platform:anycpu](./platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="368c5-109">Seçenek varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="368c5-109">The option is disabled by default.</span></span> <span data-ttu-id="368c5-110">Etkinleştirmek için **-highentropyva +** veya **-highentropyva** kullanın.</span><span class="sxs-lookup"><span data-stu-id="368c5-110">Use **-highentropyva+** or **-highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="368c5-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="368c5-111">Remarks</span></span>  

 <span data-ttu-id="368c5-112">**-Highentropyva** seçeneği, Windows çekirdeğinin uyumlu sürümlerinin ASLR bir parçası olarak bir işlemin adres alanı yerleşimini rastgele hale getirmek için daha yüksek bir entropi kullanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="368c5-112">The **-highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="368c5-113">Daha yüksek serbestlik derecenin kullanılması, yığınlar ve yığınların gibi bellek bölgelerine daha fazla sayıda adresin ayrılabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="368c5-113">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="368c5-114">Sonuç olarak, belirli bir bellek bölgesinin konumunu tahmin etmek daha zordur.</span><span class="sxs-lookup"><span data-stu-id="368c5-114">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="368c5-115">**-Highentropyva** derleyici seçeneği belirtildiğinde, hedef yürütülebilir dosya ve bağımlı olduğu tüm modüller, 64 bitlik bir işlem olarak çalışırken 4 GIGABAYTTAN (GB) büyük olan işaretçi değerlerini işleyebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="368c5-115">When the **-highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
