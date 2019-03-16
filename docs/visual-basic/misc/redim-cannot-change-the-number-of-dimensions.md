---
title: Boyutların sayısı 'ReDim' değiştirilemiyor
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: b6bb78c3f1d7224e6e4b432fd3aef4589f2f1cd4
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58019400"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="09886-102">Boyutların sayısı 'ReDim' değiştirilemiyor</span><span class="sxs-lookup"><span data-stu-id="09886-102">'ReDim' cannot change the number of dimensions</span></span>
<span data-ttu-id="09886-103">Bir işlem kullanmayı dener `ReDim` dizi boyut (boyut sayısı) değiştirileceğini deyimi.</span><span class="sxs-lookup"><span data-stu-id="09886-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="09886-104">`ReDim` bir veya daha fazla boyut zaten resmi olarak bildirilmiş bir dizinin boyutunu değiştirebilirsiniz, ancak bir dizinin derecesi değiştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="09886-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="09886-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="09886-105">To correct this error</span></span>  
  
-   <span data-ttu-id="09886-106">Dizinin boyut sayısı ve boyutlar boyutlarını değiştirmek ve mümkün olduğunda, kullanmak istediğiniz olun `Dim` istenen boyut olan yeni bir dizi bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="09886-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09886-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09886-107">See also</span></span>

- [<span data-ttu-id="09886-108">Visual Basic'te Diziler</span><span class="sxs-lookup"><span data-stu-id="09886-108">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="09886-109">Visual Basic'de dizi boyutları</span><span class="sxs-lookup"><span data-stu-id="09886-109">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="09886-110">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="09886-110">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="09886-111">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="09886-111">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
