---
title: Dizin sayısı, sıralı dizinin boyut sayısını aşıyor
ms.date: 07/20/2015
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
ms.openlocfilehash: d40a19aefdca65773d3d8e37a43d99178586fb1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593442"
---
# <a name="number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a><span data-ttu-id="26121-102">Dizin sayısı, sıralı dizinin boyut sayısını aşıyor</span><span class="sxs-lookup"><span data-stu-id="26121-102">Number of indices exceeds the number of dimensions of the indexed array</span></span>
<span data-ttu-id="26121-103">Tam olarak bir dizi öğesine erişmek için kullanılan sayısından dizi, başka bir deyişle, bunun için bildirilen dimensions sayısı derecesini ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="26121-103">The number of indices used to access an array element must be exactly the same as the rank of the array, that is, the number of dimensions declared for it.</span></span>  
  
 <span data-ttu-id="26121-104">**Hata Kimliği:** BC30106</span><span class="sxs-lookup"><span data-stu-id="26121-104">**Error ID:** BC30106</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="26121-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="26121-105">To correct this error</span></span>  
  
-   <span data-ttu-id="26121-106">Toplam indisleri dizi derecesini sayısına eşittir kadar indisleri dizi başvurusundan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="26121-106">Remove subscripts from the array reference until the total number of subscripts equals the rank of the array.</span></span> <span data-ttu-id="26121-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="26121-107">For example:</span></span>  
  
    ```vb  
    Dim gameBoard(3, 3) As String  
  
    ' Incorrect code. The array has two dimensions.  
    gameBoard(1, 1, 1) = "X"  
    gameBoard(2, 1, 1) = "O"  
  
    ' Correct code.  
    gameBoard(0, 0) = "X"  
    gameBoard(1, 0) = "O"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="26121-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="26121-108">See Also</span></span>  
 [<span data-ttu-id="26121-109">Diziler</span><span class="sxs-lookup"><span data-stu-id="26121-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
