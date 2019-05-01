---
title: "'ReDim' yalnızca en sağdaki boyut değiştirebilirsiniz"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 86d639e70e85b19a91f89fa4e0cab330af07dccf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61943370"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a><span data-ttu-id="8309a-102">'ReDim' yalnızca en sağdaki boyut değiştirebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="8309a-102">'ReDim' can only change the right-most dimension</span></span>
<span data-ttu-id="8309a-103">A `ReDim` deyimi çalıştı kullanılacak `Preserve` son boyutu değil bir dizinin boyutunu değiştirmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="8309a-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="8309a-104">Kullanırken `Preserve`, sadece son boyutu bir dizinin yeniden boyutlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8309a-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="8309a-105">Diğer tüm boyutlar için aynı boyutta varolan bir diziye sunamıyoruz belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8309a-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8309a-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="8309a-106">To correct this error</span></span>  
  
- <span data-ttu-id="8309a-107">Kaldırma `Preserve` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="8309a-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8309a-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8309a-108">See also</span></span>

- [<span data-ttu-id="8309a-109">Visual Basic'te Diziler</span><span class="sxs-lookup"><span data-stu-id="8309a-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="8309a-110">Visual Basic'de dizi boyutları</span><span class="sxs-lookup"><span data-stu-id="8309a-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="8309a-111">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="8309a-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="8309a-112">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="8309a-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
