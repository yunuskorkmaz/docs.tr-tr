---
title: Hedef dizin kaynak dizini altında olduğundan işlem tamamlanamadı
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: 253e7ff1d457827a2e1cb9f64eae4bfa971a3798
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645879"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="d4df6-102">Hedef dizin kaynak dizini altında olduğundan işlem tamamlanamadı</span><span class="sxs-lookup"><span data-stu-id="d4df6-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="d4df6-103">Döngüsel bir işlem başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="d4df6-103">A cyclic operation has failed.</span></span> <span data-ttu-id="d4df6-104">Döngüsel operations döngüsü ve bu nedenle tamamlayamıyor.</span><span class="sxs-lookup"><span data-stu-id="d4df6-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="d4df6-105">Örneğin, nesne bir sırayla a nesneden devralan nesne B devralınacak girişiminde bulunabilir</span><span class="sxs-lookup"><span data-stu-id="d4df6-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d4df6-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d4df6-106">To correct this error</span></span>  
  
-   <span data-ttu-id="d4df6-107">Devralınırken, döngüsel başvuru olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d4df6-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4df6-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4df6-108">See also</span></span>
- [<span data-ttu-id="d4df6-109">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="d4df6-109">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="d4df6-110">Hata Ayıklamanın Temelleri: Kesme noktaları</span><span class="sxs-lookup"><span data-stu-id="d4df6-110">Debugging Basics: Breakpoints</span></span>](https://msdn.microsoft.com/library/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)
