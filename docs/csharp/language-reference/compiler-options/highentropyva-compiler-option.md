---
title: -highentropyva (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: b710bb829f6a7591159d2f2e6bacc670d21c42d1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606851"
---
# <a name="-highentropyva-c-compiler-options"></a><span data-ttu-id="f5cd8-102">-highentropyva (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="f5cd8-102">-highentropyva (C# Compiler Options)</span></span>
<span data-ttu-id="f5cd8-103">**-Highentropyva** derleyici seçeneği Windows çekirdeğine, belirli bir yürütülebilir dosyanın yüksek entropi adres alanı düzeni rastgele SEÇIMINI (ASLR) destekleyip desteklemediğini söyler.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-103">The **-highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5cd8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5cd8-104">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f5cd8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f5cd8-105">Arguments</span></span>  
 <span data-ttu-id="f5cd8-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="f5cd8-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="f5cd8-107">Bu seçenek, 64 bitlik bir yürütülebilir dosyanın veya [-Platform: anycpu](./platform-compiler-option.md) derleyicisi seçeneği tarafından işaretlenen bir yürütülebilir dosyanın yüksek bir entropi sanal adres alanını desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-107">This option specifies that a 64-bit executable or an executable that is marked by the [-platform:anycpu](./platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="f5cd8-108">Seçenek varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-108">The option is disabled by default.</span></span> <span data-ttu-id="f5cd8-109">Etkinleştirmek için **-highentropyva +** veya **-highentropyva** kullanın.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-109">Use **-highentropyva+** or **-highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5cd8-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5cd8-110">Remarks</span></span>  
 <span data-ttu-id="f5cd8-111">**-Highentropyva** seçeneği, Windows çekirdeğinin uyumlu sürümlerinin ASLR bir parçası olarak bir işlemin adres alanı yerleşimini rastgele hale getirmek için daha yüksek bir entropi kullanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-111">The **-highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="f5cd8-112">Daha yüksek serbestlik derecenin kullanılması, yığınlar ve yığınların gibi bellek bölgelerine daha fazla sayıda adresin ayrılabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-112">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="f5cd8-113">Sonuç olarak, belirli bir bellek bölgesinin konumunu tahmin etmek daha zordur.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="f5cd8-114">**-Highentropyva** derleyici seçeneği belirtildiğinde, hedef yürütülebilir dosya ve bağımlı olduğu tüm modüller, 64 bitlik bir işlem olarak çalışırken 4 GIGABAYTTAN (GB) büyük olan işaretçi değerlerini işleyebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="f5cd8-114">When the **-highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
