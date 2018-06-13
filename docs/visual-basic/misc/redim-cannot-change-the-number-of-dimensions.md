---
title: '&#39;ReDim&#39; dimensions sayısı değiştirilemiyor'
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: bfd4096141833b85a2126340ef549e1e1d1f8e3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33640387"
---
# <a name="39redim39-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="a06c4-102">&#39;ReDim&#39; dimensions sayısı değiştirilemiyor</span><span class="sxs-lookup"><span data-stu-id="a06c4-102">&#39;ReDim&#39; cannot change the number of dimensions</span></span>
<span data-ttu-id="a06c4-103">Bir işlem kullanma girişiminde `ReDim` bir dizi (dimensions sayısı) derecesini değiştirmek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="a06c4-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="a06c4-104">`ReDim` bir veya daha fazla boyutları zaten resmi olarak bildirilmiş bir dizinin boyutunu değiştirebilirsiniz, ancak bir dizinin derece değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="a06c4-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a06c4-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a06c4-105">To correct this error</span></span>  
  
-   <span data-ttu-id="a06c4-106">Mümkünse, kullanın ve dizinin derece ve boyutları boyutlarını değiştirmek istiyorsanız olun `Dim` istenen dereceye sahip yeni bir dizi bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="a06c4-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a06c4-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a06c4-107">See Also</span></span>  
 [<span data-ttu-id="a06c4-108">Visual Basic'te Diziler</span><span class="sxs-lookup"><span data-stu-id="a06c4-108">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="a06c4-109">Visual Basic'de dizi boyutları</span><span class="sxs-lookup"><span data-stu-id="a06c4-109">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="a06c4-110">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="a06c4-110">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="a06c4-111">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="a06c4-111">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
