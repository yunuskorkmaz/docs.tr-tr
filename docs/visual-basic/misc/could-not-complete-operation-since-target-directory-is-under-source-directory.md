---
title: Hedef dizin kaynak dizin altında olduğundan işlem tamamlanamadı
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: d159b9bb3a765a2fefe99fa15dff42e979fda9e3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91079145"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="5ca09-102">Hedef dizin kaynak dizin altında olduğundan işlem tamamlanamadı</span><span class="sxs-lookup"><span data-stu-id="5ca09-102">Could not complete operation since target directory is under source directory</span></span>

<span data-ttu-id="5ca09-103">Döngüsel bir işlem başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="5ca09-103">A cyclic operation has failed.</span></span> <span data-ttu-id="5ca09-104">Döngüsel işlemler çevrimi ve bu nedenle tamamlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="5ca09-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="5ca09-105">Örneğin, A nesnesi B nesnesinden devralma girişiminde bulunabilir ve bu nesne A nesnesinden devralır.</span><span class="sxs-lookup"><span data-stu-id="5ca09-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5ca09-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5ca09-106">To correct this error</span></span>  
  
- <span data-ttu-id="5ca09-107">Devralma sırasında, döngüsel başvuru bulunmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="5ca09-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ca09-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ca09-108">See also</span></span>

- [<span data-ttu-id="5ca09-109">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="5ca09-109">Error Types</span></span>](../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="5ca09-110">Visual Studio hata ayıklayıcıda kesme noktaları kullanma</span><span class="sxs-lookup"><span data-stu-id="5ca09-110">Use breakpoints in the Visual Studio debugger</span></span>](/visualstudio/debugger/using-breakpoints)
