---
title: '&#39;ReDim&#39; yalnızca en sağdaki boyut değiştirebilirsiniz'
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 94e0fe81f7e750a67943b68f2db700e3a7831da1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482723"
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a><span data-ttu-id="c5024-102">&#39;ReDim&#39; yalnızca en sağdaki boyut değiştirebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="c5024-102">&#39;ReDim&#39; can only change the right-most dimension</span></span>
<span data-ttu-id="c5024-103">A `ReDim` deyimi çalıştı kullanılacak `Preserve` son boyutu değil bir dizinin boyutunu değiştirmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="c5024-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="c5024-104">Kullanırken `Preserve`, sadece son boyutu bir dizinin yeniden boyutlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5024-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="c5024-105">Diğer tüm boyutlar için aynı boyutta varolan bir diziye sunamıyoruz belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5024-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c5024-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c5024-106">To correct this error</span></span>  
  
-   <span data-ttu-id="c5024-107">Kaldırma `Preserve` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="c5024-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5024-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5024-108">See Also</span></span>  
 [<span data-ttu-id="c5024-109">Visual Basic'te Diziler</span><span class="sxs-lookup"><span data-stu-id="c5024-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="c5024-110">Visual Basic'de dizi boyutları</span><span class="sxs-lookup"><span data-stu-id="c5024-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="c5024-111">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="c5024-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="c5024-112">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="c5024-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="c5024-113">Preserve - Sil</span><span class="sxs-lookup"><span data-stu-id="c5024-113">Preserve - delete</span></span>](https://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
