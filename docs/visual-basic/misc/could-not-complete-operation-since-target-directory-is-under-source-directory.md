---
title: "Hedef dizin kaynak dizinin altında olduğundan işlem tamamlanamadı"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 429d679157d25655ca73afef14ecd642f7cac37f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="1cd15-102">Hedef dizin kaynak dizinin altında olduğundan işlem tamamlanamadı</span><span class="sxs-lookup"><span data-stu-id="1cd15-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="1cd15-103">Döngüsel bir işlemi başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="1cd15-103">A cyclic operation has failed.</span></span> <span data-ttu-id="1cd15-104">Döngüsel işlemler döngüsü ve bu nedenle tamamlayamıyor.</span><span class="sxs-lookup"><span data-stu-id="1cd15-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="1cd15-105">Örneğin, nesne A sırayla A. nesneden devralır nesne B devralınmalıdır girişiminde bulunabilir</span><span class="sxs-lookup"><span data-stu-id="1cd15-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1cd15-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1cd15-106">To correct this error</span></span>  
  
-   <span data-ttu-id="1cd15-107">Devralırken, döngüsel başvuru olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="1cd15-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cd15-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1cd15-108">See Also</span></span>  
 [<span data-ttu-id="1cd15-109">Hata türleri</span><span class="sxs-lookup"><span data-stu-id="1cd15-109">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="1cd15-110">Hata ayıklama temelleri: kesme noktaları</span><span class="sxs-lookup"><span data-stu-id="1cd15-110">Debugging Basics: Breakpoints</span></span>](http://msdn.microsoft.com/en-us/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)
