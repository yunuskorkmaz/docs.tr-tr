---
title: Tür belirleyicilerde dizi sınırları bulunamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: 951f710160ae1023671773c21c73946f5ae94c2b
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512757"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a><span data-ttu-id="03f35-102">Tür belirleyicilerde dizi sınırları bulunamaz</span><span class="sxs-lookup"><span data-stu-id="03f35-102">Array bounds cannot appear in type specifiers</span></span>

<span data-ttu-id="03f35-103">Dizi boyutları bir veri türü belirticisinin parçası olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="03f35-103">Array sizes cannot be declared as part of a data type specifier.</span></span>

<span data-ttu-id="03f35-104">**Hata KIMLIĞI:** BC30638</span><span class="sxs-lookup"><span data-stu-id="03f35-104">**Error ID:** BC30638</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="03f35-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="03f35-105">To correct this error</span></span>

- <span data-ttu-id="03f35-106">Aşağıdaki örnekte gösterildiği gibi, dizi boyutunu türden sonra yerleştirmek yerine değişken adının hemen ardından dizinin boyutunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="03f35-106">Specify the size of the array immediately following the variable name instead of placing the array size after the type, as shown in the following example.</span></span>

  ```vb
  Dim Array(8) As Integer
  ```

- <span data-ttu-id="03f35-107">Aşağıdaki örnekte gösterildiği gibi bir diziyi tanımlayın ve istenen sayıda öğe ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="03f35-107">Define an array and initialize it with the desired number of elements, as shown in the following example.</span></span>

  ```vb
  Dim Array2() As Integer = New Integer(8) {}
  ```

## <a name="see-also"></a><span data-ttu-id="03f35-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03f35-108">See also</span></span>

- [<span data-ttu-id="03f35-109">Diziler</span><span class="sxs-lookup"><span data-stu-id="03f35-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
