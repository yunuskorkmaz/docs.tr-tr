---
title: Tür belirleyicilerde dizi sınırları bulunamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: f31aea5a98233c8f262a77ba5c99eea389bc33ee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715445"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a><span data-ttu-id="e26d2-102">Tür belirleyicilerde dizi sınırları bulunamaz</span><span class="sxs-lookup"><span data-stu-id="e26d2-102">Array bounds cannot appear in type specifiers</span></span>
<span data-ttu-id="e26d2-103">Dizi boyutları, bir veri türü tanımlayıcısı bir parçası olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="e26d2-103">Array sizes cannot be declared as part of a data type specifier.</span></span>  
  
 <span data-ttu-id="e26d2-104">**Hata Kimliği:** BC30638</span><span class="sxs-lookup"><span data-stu-id="e26d2-104">**Error ID:** BC30638</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e26d2-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e26d2-105">To correct this error</span></span>  
  
-   <span data-ttu-id="e26d2-106">Hemen aşağıdaki örnekte gösterildiği gibi türden sonra dizi boyutu yerleştirme yerine değişken adı aşağıdaki dizinin boyutunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="e26d2-106">Specify the size of the array immediately following the variable name instead of placing the array size after the type, as shown in the following example.</span></span>  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   <span data-ttu-id="e26d2-107">Bir dizi tanımlayın ve istenen öğelerin sayısı ile aşağıdaki örnekte gösterildiği gibi başlatın.</span><span class="sxs-lookup"><span data-stu-id="e26d2-107">Define an array and initialize it with the desired number of elements, as shown in the following example.</span></span>  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e26d2-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e26d2-108">See also</span></span>
- [<span data-ttu-id="e26d2-109">Diziler</span><span class="sxs-lookup"><span data-stu-id="e26d2-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
