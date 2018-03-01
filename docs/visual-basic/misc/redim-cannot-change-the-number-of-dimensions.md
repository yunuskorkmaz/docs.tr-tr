---
title: "&#39; ReDim &#39; dimensions sayısı değiştirilemiyor"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8cf3713c72bd07803935065780e894c130911a6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="39redim39-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="60819-102">&#39; ReDim &#39; dimensions sayısı değiştirilemiyor</span><span class="sxs-lookup"><span data-stu-id="60819-102">&#39;ReDim&#39; cannot change the number of dimensions</span></span>
<span data-ttu-id="60819-103">Bir işlem kullanma girişiminde `ReDim` bir dizi (dimensions sayısı) derecesini değiştirmek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="60819-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="60819-104">`ReDim`bir veya daha fazla boyutları zaten resmi olarak bildirilmiş bir dizinin boyutunu değiştirebilirsiniz, ancak bir dizinin derece değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="60819-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="60819-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="60819-105">To correct this error</span></span>  
  
-   <span data-ttu-id="60819-106">Mümkünse, kullanın ve dizinin derece ve boyutları boyutlarını değiştirmek istiyorsanız olun `Dim` istenen dereceye sahip yeni bir dizi bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="60819-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60819-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="60819-107">See Also</span></span>  
 [<span data-ttu-id="60819-108">Visual Basic'de diziler</span><span class="sxs-lookup"><span data-stu-id="60819-108">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="60819-109">Visual Basic'de dizi boyutları</span><span class="sxs-lookup"><span data-stu-id="60819-109">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="60819-110">ReDim deyimi</span><span class="sxs-lookup"><span data-stu-id="60819-110">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="60819-111">Dim deyimi</span><span class="sxs-lookup"><span data-stu-id="60819-111">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
