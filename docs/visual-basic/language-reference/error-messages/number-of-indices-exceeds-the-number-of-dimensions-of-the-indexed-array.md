---
title: Dizin sayısı, sıralı dizinin boyut sayısını aşıyor
ms.date: 07/20/2015
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
ms.openlocfilehash: 76cf0a997e9ad36ab4b5dfdc7c4bc29c57d309eb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665688"
---
# <a name="number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a><span data-ttu-id="1833f-102">Dizin sayısı, sıralı dizinin boyut sayısını aşıyor</span><span class="sxs-lookup"><span data-stu-id="1833f-102">Number of indices exceeds the number of dimensions of the indexed array</span></span>
<span data-ttu-id="1833f-103">Bir dizi öğesine erişmek için kullanılan dizinlerin sayısı tam olarak diğer bir deyişle, boyut için bildirilen sayısını dizinin boyut ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1833f-103">The number of indices used to access an array element must be exactly the same as the rank of the array, that is, the number of dimensions declared for it.</span></span>  
  
 <span data-ttu-id="1833f-104">**Hata Kimliği:** BC30106</span><span class="sxs-lookup"><span data-stu-id="1833f-104">**Error ID:** BC30106</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1833f-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1833f-105">To correct this error</span></span>  
  
- <span data-ttu-id="1833f-106">Dizi boyut sayısını toplam alt simgeler eşittir kadar alt simgeler dizi başvuruyu kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1833f-106">Remove subscripts from the array reference until the total number of subscripts equals the rank of the array.</span></span> <span data-ttu-id="1833f-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="1833f-107">For example:</span></span>  
  
    ```vb  
    Dim gameBoard(3, 3) As String  
  
    ' Incorrect code. The array has two dimensions.  
    gameBoard(1, 1, 1) = "X"  
    gameBoard(2, 1, 1) = "O"  
  
    ' Correct code.  
    gameBoard(0, 0) = "X"  
    gameBoard(1, 0) = "O"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1833f-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1833f-108">See also</span></span>

- [<span data-ttu-id="1833f-109">Diziler</span><span class="sxs-lookup"><span data-stu-id="1833f-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
