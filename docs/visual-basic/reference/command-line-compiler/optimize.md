---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: eb84e0a7038e7ff8cb399ac7222b6ac1661b5bc1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842167"
---
# <a name="-optimize"></a><span data-ttu-id="26f51-102">-optimize</span><span class="sxs-lookup"><span data-stu-id="26f51-102">-optimize</span></span>
<span data-ttu-id="26f51-103">Etkinleştirir veya derleyici iyileştirmeleri devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="26f51-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26f51-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26f51-104">Syntax</span></span>  
  
```  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="26f51-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="26f51-105">Arguments</span></span>  
  
|<span data-ttu-id="26f51-106">Terim</span><span class="sxs-lookup"><span data-stu-id="26f51-106">Term</span></span>|<span data-ttu-id="26f51-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="26f51-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="26f51-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="26f51-108">`+` &#124; `-`</span></span>|<span data-ttu-id="26f51-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="26f51-109">Optional.</span></span> <span data-ttu-id="26f51-110">`-optimize-` Seçeneği, derleyici iyileştirmeleri devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="26f51-110">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="26f51-111">`-optimize+` Seçeneği iyileştirmeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="26f51-111">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="26f51-112">Varsayılan olarak, en iyi duruma getirme devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="26f51-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26f51-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26f51-113">Remarks</span></span>  
 <span data-ttu-id="26f51-114">Derleyici iyileştirmeleri çıkış dosyanızı daha küçük, daha hızlı ve daha verimli olun.</span><span class="sxs-lookup"><span data-stu-id="26f51-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="26f51-115">Ancak, çıkış dosyasında, kod yeniden iyileştirmeleri neden `-optimize+` hata ayıklamayı zorlaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="26f51-115">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="26f51-116">İle oluşturulan tüm modülleri `-target:module` bir derleme, aynı kullanmalıdır `-optimize` derleme gibi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="26f51-116">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="26f51-117">Daha fazla bilgi için [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="26f51-117">For more information, see [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="26f51-118">Birleştirebilirsiniz `-optimize` ve `-debug` seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="26f51-118">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="26f51-119">Visual Studio tümleşik geliştirme ortamında ayarlamak için - iyileştirin</span><span class="sxs-lookup"><span data-stu-id="26f51-119">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="26f51-120">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="26f51-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="26f51-121">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="26f51-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="26f51-122">2.  Tıklayın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="26f51-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="26f51-123">3.  Tıklayın **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="26f51-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="26f51-124">4.  Değiştirme **iyileştirmeleri etkinleştir** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="26f51-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="26f51-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="26f51-125">Example</span></span>  
 <span data-ttu-id="26f51-126">Aşağıdaki kod derlenir `T2.vb` ve derleyici iyileştirmelerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="26f51-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="26f51-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26f51-127">See also</span></span>

- [<span data-ttu-id="26f51-128">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="26f51-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="26f51-129">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26f51-129">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)
- [<span data-ttu-id="26f51-130">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="26f51-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="26f51-131">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26f51-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
