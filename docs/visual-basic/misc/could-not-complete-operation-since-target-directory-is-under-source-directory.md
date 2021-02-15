---
description: 'Hakkında daha fazla bilgi edinin: hedef dizin kaynak dizin altında olduğundan işlem tamamlanamadı'
title: Hedef dizin kaynak dizin altında olduğundan işlem tamamlanamadı
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: 5fb0bf1d761faf9d3d0c64e8815e28e14841b1fd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463526"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="ca963-103">Hedef dizin kaynak dizin altında olduğundan işlem tamamlanamadı</span><span class="sxs-lookup"><span data-stu-id="ca963-103">Could not complete operation since target directory is under source directory</span></span>

<span data-ttu-id="ca963-104">Döngüsel bir işlem başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="ca963-104">A cyclic operation has failed.</span></span> <span data-ttu-id="ca963-105">Döngüsel işlemler çevrimi ve bu nedenle tamamlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="ca963-105">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="ca963-106">Örneğin, A nesnesi B nesnesinden devralma girişiminde bulunabilir ve bu nesne A nesnesinden devralır.</span><span class="sxs-lookup"><span data-stu-id="ca963-106">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ca963-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="ca963-107">To correct this error</span></span>  
  
- <span data-ttu-id="ca963-108">Devralma sırasında, döngüsel başvuru bulunmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="ca963-108">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca963-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca963-109">See also</span></span>

- [<span data-ttu-id="ca963-110">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="ca963-110">Error Types</span></span>](../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="ca963-111">Visual Studio hata ayıklayıcıda kesme noktaları kullanma</span><span class="sxs-lookup"><span data-stu-id="ca963-111">Use breakpoints in the Visual Studio debugger</span></span>](/visualstudio/debugger/using-breakpoints)
