---
title: "&#39; ReDim &#39; en sağdaki boyut yalnızca değiştirebilirsiniz"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 752e0e54c48b3b348a477787e5e911f1b1777667
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a><span data-ttu-id="2167d-102">&#39; ReDim &#39; en sağdaki boyut yalnızca değiştirebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="2167d-102">&#39;ReDim&#39; can only change the right-most dimension</span></span>
<span data-ttu-id="2167d-103">A `ReDim` deyimi çalıştı kullanmak `Preserve` son boyutu değil bir dizinin bir boyutu değiştirmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="2167d-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="2167d-104">Kullanırken `Preserve`, bir dizinin yalnızca son boyutu yeniden boyutlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2167d-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="2167d-105">Diğer tüm boyutları için mevcut dizisini için olduğu gibi aynı boyutta belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2167d-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2167d-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2167d-106">To correct this error</span></span>  
  
-   <span data-ttu-id="2167d-107">Kaldırma `Preserve` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="2167d-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2167d-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2167d-108">See Also</span></span>  
 [<span data-ttu-id="2167d-109">Visual Basic'te Diziler</span><span class="sxs-lookup"><span data-stu-id="2167d-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="2167d-110">Visual Basic'de dizi boyutları</span><span class="sxs-lookup"><span data-stu-id="2167d-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="2167d-111">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="2167d-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="2167d-112">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="2167d-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="2167d-113">Korumak - Sil</span><span class="sxs-lookup"><span data-stu-id="2167d-113">Preserve - delete</span></span>](http://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
