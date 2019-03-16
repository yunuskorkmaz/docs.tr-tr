---
title: Hedef dizin kaynak dizini altında olduğundan işlem tamamlanamadı
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: f53ad664b341d4db803dee1f0f008c3918d13d93
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58039433"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="31b95-102">Hedef dizin kaynak dizini altında olduğundan işlem tamamlanamadı</span><span class="sxs-lookup"><span data-stu-id="31b95-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="31b95-103">Döngüsel bir işlem başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="31b95-103">A cyclic operation has failed.</span></span> <span data-ttu-id="31b95-104">Döngüsel operations döngüsü ve bu nedenle tamamlayamıyor.</span><span class="sxs-lookup"><span data-stu-id="31b95-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="31b95-105">Örneğin, nesne bir sırayla a nesneden devralan nesne B devralınacak girişiminde bulunabilir</span><span class="sxs-lookup"><span data-stu-id="31b95-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="31b95-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="31b95-106">To correct this error</span></span>  
  
-   <span data-ttu-id="31b95-107">Devralınırken, döngüsel başvuru olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="31b95-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31b95-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31b95-108">See also</span></span>

- [<span data-ttu-id="31b95-109">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="31b95-109">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="31b95-110">Visual Studio hata ayıklayıcıda kesme noktaları kullanma</span><span class="sxs-lookup"><span data-stu-id="31b95-110">Use breakpoints in the Visual Studio debugger</span></span>](/visualstudio/debugger/using-breakpoints)
