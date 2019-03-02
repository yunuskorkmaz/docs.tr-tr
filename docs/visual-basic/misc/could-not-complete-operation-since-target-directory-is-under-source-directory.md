---
title: Hedef dizin kaynak dizini altında olduğundan işlem tamamlanamadı
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: 39373cd368282f3b109b450189561366b9e74484
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200578"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="f4ac9-102">Hedef dizin kaynak dizini altında olduğundan işlem tamamlanamadı</span><span class="sxs-lookup"><span data-stu-id="f4ac9-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="f4ac9-103">Döngüsel bir işlem başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="f4ac9-103">A cyclic operation has failed.</span></span> <span data-ttu-id="f4ac9-104">Döngüsel operations döngüsü ve bu nedenle tamamlayamıyor.</span><span class="sxs-lookup"><span data-stu-id="f4ac9-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="f4ac9-105">Örneğin, nesne bir sırayla a nesneden devralan nesne B devralınacak girişiminde bulunabilir</span><span class="sxs-lookup"><span data-stu-id="f4ac9-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f4ac9-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f4ac9-106">To correct this error</span></span>  
  
-   <span data-ttu-id="f4ac9-107">Devralınırken, döngüsel başvuru olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f4ac9-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4ac9-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4ac9-108">See also</span></span>
- [<span data-ttu-id="f4ac9-109">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="f4ac9-109">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="f4ac9-110">Visual Studio hata ayıklayıcıda kesme noktaları kullanma</span><span class="sxs-lookup"><span data-stu-id="f4ac9-110">Use breakpoints in the Visual Studio debugger</span></span>](/visualstudio/debugger/using-breakpoints)
