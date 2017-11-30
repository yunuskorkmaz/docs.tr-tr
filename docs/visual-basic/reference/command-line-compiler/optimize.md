---
title: /optimize
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dead17435cd147bdcdf91bdc5b8e0aa651e9e9fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="optimize"></a><span data-ttu-id="0ab24-102">/optimize</span><span class="sxs-lookup"><span data-stu-id="0ab24-102">/optimize</span></span>
<span data-ttu-id="0ab24-103">Etkinleştirir veya derleyici iyileştirmelerini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="0ab24-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ab24-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ab24-104">Syntax</span></span>  
  
```  
/optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0ab24-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0ab24-105">Arguments</span></span>  
  
|<span data-ttu-id="0ab24-106">Terim</span><span class="sxs-lookup"><span data-stu-id="0ab24-106">Term</span></span>|<span data-ttu-id="0ab24-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="0ab24-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="0ab24-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="0ab24-108">`+` &#124; `-`</span></span>|<span data-ttu-id="0ab24-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="0ab24-109">Optional.</span></span> <span data-ttu-id="0ab24-110">`/optimize-` Seçeneği, derleyici iyileştirmelerini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="0ab24-110">The `/optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="0ab24-111">`/optimize+` Seçeneği iyileştirmeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ab24-111">The `/optimize+` option enables optimizations.</span></span> <span data-ttu-id="0ab24-112">Varsayılan olarak, en iyi duruma getirme devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="0ab24-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ab24-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ab24-113">Remarks</span></span>  
 <span data-ttu-id="0ab24-114">Derleyici en iyi duruma getirme, daha küçük, daha hızlı ve daha verimli çıkış dosyanızın olun.</span><span class="sxs-lookup"><span data-stu-id="0ab24-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="0ab24-115">Ancak, en iyi duruma getirme kodu yeniden düzenleme yapılmasını çıktı dosyasında neden `/optimize+` hata ayıklama zorlaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="0ab24-115">However, because optimizations result in code rearrangement in the output file, `/optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="0ab24-116">İle oluşturulan tüm modüllerin `/target:module` bütünleştirilmiş aynı kullanmalıdır `/optimize` derleme gibi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0ab24-116">All modules generated with `/target:module` for an assembly must use the same `/optimize` settings as the assembly.</span></span> <span data-ttu-id="0ab24-117">Daha fazla bilgi için bkz: [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="0ab24-117">For more information, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="0ab24-118">Birleştirebilirsiniz `/optimize` ve `/debug` seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="0ab24-118">You can combine the `/optimize` and `/debug` options.</span></span>  
  
|<span data-ttu-id="0ab24-119">Ayarlamak için Visual Studio tümleşik geliştirme ortamında en iyi duruma getirme</span><span class="sxs-lookup"><span data-stu-id="0ab24-119">To set /optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="0ab24-120">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="0ab24-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0ab24-121">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="0ab24-121">On the **Project** menu, click **Properties**.</span></span><br />     <span data-ttu-id="0ab24-122">Daha fazla bilgi için bkz: [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="0ab24-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="0ab24-123">2.  Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="0ab24-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="0ab24-124">3.  Tıklatın **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="0ab24-124">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="0ab24-125">4.  Değiştirme **etkinleştirmek en iyi duruma getirme** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="0ab24-125">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0ab24-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ab24-126">Example</span></span>  
 <span data-ttu-id="0ab24-127">Aşağıdaki kod derlerken `T2.vb` ve derleyici iyileştirmelerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ab24-127">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```  
vbc t2.vb /optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ab24-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0ab24-128">See Also</span></span>  
 [<span data-ttu-id="0ab24-129">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="0ab24-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="0ab24-130">/ Debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ab24-130">/debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [<span data-ttu-id="0ab24-131">Örnek derleme komut satırları</span><span class="sxs-lookup"><span data-stu-id="0ab24-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="0ab24-132">/ target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ab24-132">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
