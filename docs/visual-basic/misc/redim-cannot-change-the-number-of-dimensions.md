---
description: "Daha fazla bilgi edinin: ' ReDim ' boyut sayısını değiştiremiyor"
title: "' ReDim ' boyut sayısını değiştiremiyor"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: 4552dd6b1cce54813b57e5b8c76a3580b81b8def
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100454644"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="abccf-103">' ReDim ' boyut sayısını değiştiremiyor</span><span class="sxs-lookup"><span data-stu-id="abccf-103">'ReDim' cannot change the number of dimensions</span></span>

<span data-ttu-id="abccf-104">Bir işlem, `ReDim` bir dizinin derecesini (boyut sayısı) değiştirmek için ifadesini kullanmayı dener.</span><span class="sxs-lookup"><span data-stu-id="abccf-104">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="abccf-105">`ReDim` , önceden tanımlanmış bir dizinin bir veya daha fazla boyutunun boyutunu değiştirebilir, ancak bir dizinin derecesini değiştiremez.</span><span class="sxs-lookup"><span data-stu-id="abccf-105">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="abccf-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="abccf-106">To correct this error</span></span>  
  
- <span data-ttu-id="abccf-107">Dizinin sırasını, boyutlarının boyutlarını değil ve mümkünse, `Dim` istenen dereceye sahip yeni bir dizi bildirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="abccf-107">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abccf-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abccf-108">See also</span></span>

- [<span data-ttu-id="abccf-109">Visual Basic'te Diziler</span><span class="sxs-lookup"><span data-stu-id="abccf-109">Arrays in Visual Basic</span></span>](../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="abccf-110">Visual Basic dizi boyutları</span><span class="sxs-lookup"><span data-stu-id="abccf-110">Array dimensions in Visual Basic</span></span>](../programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="abccf-111">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="abccf-111">ReDim Statement</span></span>](../language-reference/statements/redim-statement.md)
- [<span data-ttu-id="abccf-112">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="abccf-112">Dim Statement</span></span>](../language-reference/statements/dim-statement.md)
