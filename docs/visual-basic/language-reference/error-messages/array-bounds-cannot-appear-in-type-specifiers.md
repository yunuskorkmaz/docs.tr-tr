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
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>Tür belirleyicilerde dizi sınırları bulunamaz
Dizi boyutları bir veri türü belirleyici bir parçası olarak bildirilemez.  
  
 **Hata Kimliği:** BC30638  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Aşağıdaki örnekte gösterildiği gibi türü dizi boyutu yerleştirme yerine değişken adı hemen ardından dizinin boyutu belirtin.  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   Aşağıdaki örnekte gösterildiği gibi öğeleri, istenen sayısı ile başlatın ve bir dizi tanımlayın.  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md)
