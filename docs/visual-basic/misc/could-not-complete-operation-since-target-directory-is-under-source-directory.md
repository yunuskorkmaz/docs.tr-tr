---
title: Hedef dizin kaynak dizinin altında olduğundan işlem tamamlanamadı
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: 68217023a980891200c18b5536ef902574d36257
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33638518"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="52975-102">Hedef dizin kaynak dizinin altında olduğundan işlem tamamlanamadı</span><span class="sxs-lookup"><span data-stu-id="52975-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="52975-103">Döngüsel bir işlemi başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="52975-103">A cyclic operation has failed.</span></span> <span data-ttu-id="52975-104">Döngüsel işlemler döngüsü ve bu nedenle tamamlayamıyor.</span><span class="sxs-lookup"><span data-stu-id="52975-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="52975-105">Örneğin, nesne A sırayla A. nesneden devralır nesne B devralınmalıdır girişiminde bulunabilir</span><span class="sxs-lookup"><span data-stu-id="52975-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="52975-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="52975-106">To correct this error</span></span>  
  
-   <span data-ttu-id="52975-107">Devralırken, döngüsel başvuru olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="52975-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52975-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="52975-108">See Also</span></span>  
 [<span data-ttu-id="52975-109">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="52975-109">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="52975-110">Hata ayıklama temelleri: kesme noktaları</span><span class="sxs-lookup"><span data-stu-id="52975-110">Debugging Basics: Breakpoints</span></span>](http://msdn.microsoft.com/library/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)
