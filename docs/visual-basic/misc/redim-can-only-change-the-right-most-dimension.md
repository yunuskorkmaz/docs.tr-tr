---
title: "' ReDim ' yalnızca en sağdaki boyutu değiştirebilir"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: c3a18bb93d1253628d73919b18fe4614d742d280
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077390"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a><span data-ttu-id="714c5-102">' ReDim ' yalnızca en sağdaki boyutu değiştirebilir</span><span class="sxs-lookup"><span data-stu-id="714c5-102">'ReDim' can only change the right-most dimension</span></span>

<span data-ttu-id="714c5-103">Bir `ReDim` ifade, `Preserve` son boyut olmayan bir dizinin boyutunu değiştirmek için anahtar sözcüğünü kullanmayı denedi.</span><span class="sxs-lookup"><span data-stu-id="714c5-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="714c5-104">Kullanırken `Preserve` , yalnızca bir dizinin en son boyutunu yeniden boyutlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="714c5-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="714c5-105">Diğer tüm boyutlar için, var olan dizi için aynı boyutu belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="714c5-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="714c5-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="714c5-106">To correct this error</span></span>  
  
- <span data-ttu-id="714c5-107">`Preserve`Anahtar sözcüğünü kaldırın.</span><span class="sxs-lookup"><span data-stu-id="714c5-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="714c5-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="714c5-108">See also</span></span>

- [<span data-ttu-id="714c5-109">Visual Basic'te Diziler</span><span class="sxs-lookup"><span data-stu-id="714c5-109">Arrays in Visual Basic</span></span>](../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="714c5-110">Visual Basic dizi boyutları</span><span class="sxs-lookup"><span data-stu-id="714c5-110">Array dimensions in Visual Basic</span></span>](../programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="714c5-111">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="714c5-111">ReDim Statement</span></span>](../language-reference/statements/redim-statement.md)
- [<span data-ttu-id="714c5-112">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="714c5-112">Dim Statement</span></span>](../language-reference/statements/dim-statement.md)
