---
title: Tür belirleyicilerde dizi sınırları bulunamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: f20ed883005641082eb89e2effa5221594910ffe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838787"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a><span data-ttu-id="4a578-102">Tür belirleyicilerde dizi sınırları bulunamaz</span><span class="sxs-lookup"><span data-stu-id="4a578-102">Array bounds cannot appear in type specifiers</span></span>
<span data-ttu-id="4a578-103">Dizi boyutları, bir veri türü tanımlayıcısı bir parçası olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="4a578-103">Array sizes cannot be declared as part of a data type specifier.</span></span>  
  
 <span data-ttu-id="4a578-104">**Hata Kimliği:** BC30638</span><span class="sxs-lookup"><span data-stu-id="4a578-104">**Error ID:** BC30638</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4a578-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="4a578-105">To correct this error</span></span>  
  
-   <span data-ttu-id="4a578-106">Hemen aşağıdaki örnekte gösterildiği gibi türden sonra dizi boyutu yerleştirme yerine değişken adı aşağıdaki dizinin boyutunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="4a578-106">Specify the size of the array immediately following the variable name instead of placing the array size after the type, as shown in the following example.</span></span>  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   <span data-ttu-id="4a578-107">Bir dizi tanımlayın ve istenen öğelerin sayısı ile aşağıdaki örnekte gösterildiği gibi başlatın.</span><span class="sxs-lookup"><span data-stu-id="4a578-107">Define an array and initialize it with the desired number of elements, as shown in the following example.</span></span>  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4a578-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a578-108">See also</span></span>

- [<span data-ttu-id="4a578-109">Diziler</span><span class="sxs-lookup"><span data-stu-id="4a578-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
