---
title: "' ReDim ' boyut sayısını değiştiremiyor"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: 8d80af7682f27b403e0f463fdbebbcac71f18b01
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077377"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="9d03a-102">' ReDim ' boyut sayısını değiştiremiyor</span><span class="sxs-lookup"><span data-stu-id="9d03a-102">'ReDim' cannot change the number of dimensions</span></span>

<span data-ttu-id="9d03a-103">Bir işlem, `ReDim` bir dizinin derecesini (boyut sayısı) değiştirmek için ifadesini kullanmayı dener.</span><span class="sxs-lookup"><span data-stu-id="9d03a-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="9d03a-104">`ReDim` , önceden tanımlanmış bir dizinin bir veya daha fazla boyutunun boyutunu değiştirebilir, ancak bir dizinin derecesini değiştiremez.</span><span class="sxs-lookup"><span data-stu-id="9d03a-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9d03a-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="9d03a-105">To correct this error</span></span>  
  
- <span data-ttu-id="9d03a-106">Dizinin sırasını, boyutlarının boyutlarını değil ve mümkünse, `Dim` istenen dereceye sahip yeni bir dizi bildirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d03a-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d03a-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d03a-107">See also</span></span>

- [<span data-ttu-id="9d03a-108">Visual Basic'te Diziler</span><span class="sxs-lookup"><span data-stu-id="9d03a-108">Arrays in Visual Basic</span></span>](../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="9d03a-109">Visual Basic dizi boyutları</span><span class="sxs-lookup"><span data-stu-id="9d03a-109">Array dimensions in Visual Basic</span></span>](../programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="9d03a-110">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="9d03a-110">ReDim Statement</span></span>](../language-reference/statements/redim-statement.md)
- [<span data-ttu-id="9d03a-111">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="9d03a-111">Dim Statement</span></span>](../language-reference/statements/dim-statement.md)
