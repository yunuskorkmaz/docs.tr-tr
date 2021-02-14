---
description: "Daha fazla bilgi edinin: ' ReDim ' yalnızca en sağdaki boyutu değiştirebilir"
title: "' ReDim ' yalnızca en sağdaki boyutu değiştirebilir"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 6816e5b2e9c7c079b78ce53e168f46b337831512
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100454696"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a><span data-ttu-id="dea46-103">' ReDim ' yalnızca en sağdaki boyutu değiştirebilir</span><span class="sxs-lookup"><span data-stu-id="dea46-103">'ReDim' can only change the right-most dimension</span></span>

<span data-ttu-id="dea46-104">Bir `ReDim` ifade, `Preserve` son boyut olmayan bir dizinin boyutunu değiştirmek için anahtar sözcüğünü kullanmayı denedi.</span><span class="sxs-lookup"><span data-stu-id="dea46-104">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="dea46-105">Kullanırken `Preserve` , yalnızca bir dizinin en son boyutunu yeniden boyutlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dea46-105">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="dea46-106">Diğer tüm boyutlar için, var olan dizi için aynı boyutu belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dea46-106">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dea46-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="dea46-107">To correct this error</span></span>  
  
- <span data-ttu-id="dea46-108">`Preserve`Anahtar sözcüğünü kaldırın.</span><span class="sxs-lookup"><span data-stu-id="dea46-108">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dea46-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dea46-109">See also</span></span>

- [<span data-ttu-id="dea46-110">Visual Basic'te Diziler</span><span class="sxs-lookup"><span data-stu-id="dea46-110">Arrays in Visual Basic</span></span>](../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="dea46-111">Visual Basic dizi boyutları</span><span class="sxs-lookup"><span data-stu-id="dea46-111">Array dimensions in Visual Basic</span></span>](../programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="dea46-112">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="dea46-112">ReDim Statement</span></span>](../language-reference/statements/redim-statement.md)
- [<span data-ttu-id="dea46-113">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="dea46-113">Dim Statement</span></span>](../language-reference/statements/dim-statement.md)
