---
title: "'ReDim' yalnızca en sağdaki boyut değiştirebilirsiniz"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 584370f356180fe8b1710a9e145018be7f2d8a0f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592302"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a><span data-ttu-id="ceed9-102">'ReDim' yalnızca en sağdaki boyut değiştirebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="ceed9-102">'ReDim' can only change the right-most dimension</span></span>
<span data-ttu-id="ceed9-103">A `ReDim` deyimi çalıştı kullanılacak `Preserve` son boyutu değil bir dizinin boyutunu değiştirmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="ceed9-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="ceed9-104">Kullanırken `Preserve`, sadece son boyutu bir dizinin yeniden boyutlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ceed9-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="ceed9-105">Diğer tüm boyutlar için aynı boyutta varolan bir diziye sunamıyoruz belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ceed9-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ceed9-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="ceed9-106">To correct this error</span></span>  
  
- <span data-ttu-id="ceed9-107">Kaldırma `Preserve` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="ceed9-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceed9-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ceed9-108">See also</span></span>

- [<span data-ttu-id="ceed9-109">Visual Basic'te Diziler</span><span class="sxs-lookup"><span data-stu-id="ceed9-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="ceed9-110">Visual Basic'de dizi boyutları</span><span class="sxs-lookup"><span data-stu-id="ceed9-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="ceed9-111">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="ceed9-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="ceed9-112">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="ceed9-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
