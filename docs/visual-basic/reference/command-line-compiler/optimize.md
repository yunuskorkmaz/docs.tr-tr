---
title: -en iyi duruma getirme
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: ddb12eb473ce53e60835acb8f1076655f78fafd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574384"
---
# <a name="-optimize"></a><span data-ttu-id="f6793-102">-en iyi duruma getirme</span><span class="sxs-lookup"><span data-stu-id="f6793-102">-optimize</span></span>
<span data-ttu-id="f6793-103">Etkinleştirir veya derleyici iyileştirmeleri devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="f6793-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6793-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6793-104">Syntax</span></span>  
  
```  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f6793-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f6793-105">Arguments</span></span>  
  
|<span data-ttu-id="f6793-106">Terim</span><span class="sxs-lookup"><span data-stu-id="f6793-106">Term</span></span>|<span data-ttu-id="f6793-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="f6793-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="f6793-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="f6793-108">`+` &#124; `-`</span></span>|<span data-ttu-id="f6793-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f6793-109">Optional.</span></span> <span data-ttu-id="f6793-110">`-optimize-` Seçeneği, derleyici iyileştirmeleri devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="f6793-110">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="f6793-111">`-optimize+` Seçeneği iyileştirmeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f6793-111">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="f6793-112">Varsayılan olarak, en iyi duruma getirme devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="f6793-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6793-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f6793-113">Remarks</span></span>  
 <span data-ttu-id="f6793-114">Derleyici iyileştirmeleri çıkış dosyanızı daha küçük, daha hızlı ve daha verimli olun.</span><span class="sxs-lookup"><span data-stu-id="f6793-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="f6793-115">Ancak, çıkış dosyasında, kod yeniden iyileştirmeleri neden `-optimize+` hata ayıklamayı zorlaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="f6793-115">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="f6793-116">İle oluşturulan tüm modülleri `-target:module` bir derleme, aynı kullanmalıdır `-optimize` derleme gibi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f6793-116">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="f6793-117">Daha fazla bilgi için [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="f6793-117">For more information, see [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="f6793-118">Birleştirebilirsiniz `-optimize` ve `-debug` seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="f6793-118">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="f6793-119">Visual Studio tümleşik geliştirme ortamında ayarlamak için - iyileştirin</span><span class="sxs-lookup"><span data-stu-id="f6793-119">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="f6793-120">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="f6793-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f6793-121">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="f6793-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="f6793-122">2.  Tıklayın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="f6793-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="f6793-123">3.  Tıklayın **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="f6793-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="f6793-124">4.  Değiştirme **iyileştirmeleri etkinleştir** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="f6793-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f6793-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6793-125">Example</span></span>  
 <span data-ttu-id="f6793-126">Aşağıdaki kod derlenir `T2.vb` ve derleyici iyileştirmelerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f6793-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6793-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6793-127">See also</span></span>
- [<span data-ttu-id="f6793-128">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="f6793-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="f6793-129">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6793-129">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)
- [<span data-ttu-id="f6793-130">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="f6793-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="f6793-131">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6793-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
