---
description: 'Şu konuda daha fazla bilgi edinin: BC30106: Dizin sayısı, dizinlenmiş dizinin boyut sayısını aşıyor'
title: Dizin sayısı, sıralı dizinin boyut sayısını aşıyor
ms.date: 07/20/2015
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
ms.openlocfilehash: 35ec1ea106e67022046179412b142cd92712c822
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795618"
---
# <a name="bc30106-number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a><span data-ttu-id="9803d-103">BC30106: Dizin sayısı, dizinlenmiş dizinin boyut sayısını aşıyor</span><span class="sxs-lookup"><span data-stu-id="9803d-103">BC30106: Number of indices exceeds the number of dimensions of the indexed array</span></span>

<span data-ttu-id="9803d-104">Bir dizi öğesine erişmek için kullanılan dizin sayısı, dizi sırasıyla tam olarak aynı olmalıdır, diğer bir deyişle, kendisi için belirtilen boyut sayısı.</span><span class="sxs-lookup"><span data-stu-id="9803d-104">The number of indices used to access an array element must be exactly the same as the rank of the array, that is, the number of dimensions declared for it.</span></span>

 <span data-ttu-id="9803d-105">**Hata kimliği:** BC30106</span><span class="sxs-lookup"><span data-stu-id="9803d-105">**Error ID:** BC30106</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="9803d-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="9803d-106">To correct this error</span></span>

- <span data-ttu-id="9803d-107">Alt simgelerin toplam sayısı dizi derecesine eşit olana kadar alt simgeleri dizi başvurusundan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="9803d-107">Remove subscripts from the array reference until the total number of subscripts equals the rank of the array.</span></span> <span data-ttu-id="9803d-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9803d-108">For example:</span></span>

    ```vb
    Dim gameBoard(3, 3) As String

    ' Incorrect code. The array has two dimensions.
    gameBoard(1, 1, 1) = "X"
    gameBoard(2, 1, 1) = "O"

    ' Correct code.
    gameBoard(0, 0) = "X"
    gameBoard(1, 0) = "O"
    ```

## <a name="see-also"></a><span data-ttu-id="9803d-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9803d-109">See also</span></span>

- [<span data-ttu-id="9803d-110">Diziler</span><span class="sxs-lookup"><span data-stu-id="9803d-110">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
