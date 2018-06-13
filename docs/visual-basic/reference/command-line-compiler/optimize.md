---
title: -en iyi duruma getirme
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: 2f066835c5f864538f281d4c58772e0e60c132f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649951"
---
# <a name="-optimize"></a><span data-ttu-id="1f251-102">-en iyi duruma getirme</span><span class="sxs-lookup"><span data-stu-id="1f251-102">-optimize</span></span>
<span data-ttu-id="1f251-103">Etkinleştirir veya derleyici iyileştirmelerini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="1f251-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f251-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f251-104">Syntax</span></span>  
  
```  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1f251-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1f251-105">Arguments</span></span>  
  
|<span data-ttu-id="1f251-106">Terim</span><span class="sxs-lookup"><span data-stu-id="1f251-106">Term</span></span>|<span data-ttu-id="1f251-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="1f251-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="1f251-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="1f251-108">`+` &#124; `-`</span></span>|<span data-ttu-id="1f251-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1f251-109">Optional.</span></span> <span data-ttu-id="1f251-110">`-optimize-` Seçeneği, derleyici iyileştirmelerini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="1f251-110">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="1f251-111">`-optimize+` Seçeneği iyileştirmeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f251-111">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="1f251-112">Varsayılan olarak, en iyi duruma getirme devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="1f251-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f251-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f251-113">Remarks</span></span>  
 <span data-ttu-id="1f251-114">Derleyici en iyi duruma getirme, daha küçük, daha hızlı ve daha verimli çıkış dosyanızın olun.</span><span class="sxs-lookup"><span data-stu-id="1f251-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="1f251-115">Ancak, en iyi duruma getirme kodu yeniden düzenleme yapılmasını çıktı dosyasında neden `-optimize+` hata ayıklama zorlaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="1f251-115">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="1f251-116">İle oluşturulan tüm modüllerin `-target:module` bütünleştirilmiş aynı kullanmalıdır `-optimize` derleme gibi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1f251-116">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="1f251-117">Daha fazla bilgi için bkz: [-hedef (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="1f251-117">For more information, see [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="1f251-118">Birleştirebilirsiniz `-optimize` ve `-debug` seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="1f251-118">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="1f251-119">Ayarlanacak - Visual Studio tümleşik geliştirme ortamında en iyi duruma getirme</span><span class="sxs-lookup"><span data-stu-id="1f251-119">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="1f251-120">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="1f251-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1f251-121">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="1f251-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="1f251-122">2.  Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="1f251-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="1f251-123">3.  Tıklatın **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1f251-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="1f251-124">4.  Değiştirme **etkinleştirmek en iyi duruma getirme** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="1f251-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1f251-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f251-125">Example</span></span>  
 <span data-ttu-id="1f251-126">Aşağıdaki kod derlerken `T2.vb` ve derleyici iyileştirmelerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f251-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f251-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1f251-127">See Also</span></span>  
 [<span data-ttu-id="1f251-128">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="1f251-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1f251-129">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f251-129">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [<span data-ttu-id="1f251-130">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="1f251-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="1f251-131">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f251-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
