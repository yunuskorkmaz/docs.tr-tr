---
title: Hedef dizin kaynak dizin altında olduğundan işlem tamamlanamadı
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: 46ec7ae452d4f8259d0f8ca3a896d1b29151ed61
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84376748"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="6b96e-102">Hedef dizin kaynak dizin altında olduğundan işlem tamamlanamadı</span><span class="sxs-lookup"><span data-stu-id="6b96e-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="6b96e-103">Döngüsel bir işlem başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="6b96e-103">A cyclic operation has failed.</span></span> <span data-ttu-id="6b96e-104">Döngüsel işlemler çevrimi ve bu nedenle tamamlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="6b96e-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="6b96e-105">Örneğin, A nesnesi B nesnesinden devralma girişiminde bulunabilir ve bu nesne A nesnesinden devralır.</span><span class="sxs-lookup"><span data-stu-id="6b96e-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6b96e-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6b96e-106">To correct this error</span></span>  
  
- <span data-ttu-id="6b96e-107">Devralma sırasında, döngüsel başvuru bulunmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="6b96e-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b96e-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b96e-108">See also</span></span>

- [<span data-ttu-id="6b96e-109">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="6b96e-109">Error Types</span></span>](../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="6b96e-110">Visual Studio hata ayıklayıcıda kesme noktaları kullanma</span><span class="sxs-lookup"><span data-stu-id="6b96e-110">Use breakpoints in the Visual Studio debugger</span></span>](/visualstudio/debugger/using-breakpoints)
