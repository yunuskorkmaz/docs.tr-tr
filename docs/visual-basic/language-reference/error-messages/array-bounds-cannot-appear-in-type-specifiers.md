---
title: Tür belirleyicilerde dizi sınırları bulunamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: 45787db51de562f2266c587fd2bb15ef29ebefbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583689"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a><span data-ttu-id="1eee3-102">Tür belirleyicilerde dizi sınırları bulunamaz</span><span class="sxs-lookup"><span data-stu-id="1eee3-102">Array bounds cannot appear in type specifiers</span></span>
<span data-ttu-id="1eee3-103">Dizi boyutları bir veri türü belirleyici bir parçası olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="1eee3-103">Array sizes cannot be declared as part of a data type specifier.</span></span>  
  
 <span data-ttu-id="1eee3-104">**Hata Kimliği:** BC30638</span><span class="sxs-lookup"><span data-stu-id="1eee3-104">**Error ID:** BC30638</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1eee3-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1eee3-105">To correct this error</span></span>  
  
-   <span data-ttu-id="1eee3-106">Aşağıdaki örnekte gösterildiği gibi türü dizi boyutu yerleştirme yerine değişken adı hemen ardından dizinin boyutu belirtin.</span><span class="sxs-lookup"><span data-stu-id="1eee3-106">Specify the size of the array immediately following the variable name instead of placing the array size after the type, as shown in the following example.</span></span>  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   <span data-ttu-id="1eee3-107">Aşağıdaki örnekte gösterildiği gibi öğeleri, istenen sayısı ile başlatın ve bir dizi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="1eee3-107">Define an array and initialize it with the desired number of elements, as shown in the following example.</span></span>  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1eee3-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1eee3-108">See Also</span></span>  
 [<span data-ttu-id="1eee3-109">Diziler</span><span class="sxs-lookup"><span data-stu-id="1eee3-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
