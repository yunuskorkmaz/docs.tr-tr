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
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>Tür belirleyicilerde dizi sınırları bulunamaz
Dizi boyutları, bir veri türü tanımlayıcısı bir parçası olarak bildirilemez.  
  
 **Hata Kimliği:** BC30638  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Hemen aşağıdaki örnekte gösterildiği gibi türden sonra dizi boyutu yerleştirme yerine değişken adı aşağıdaki dizinin boyutunu belirtin.  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   Bir dizi tanımlayın ve istenen öğelerin sayısı ile aşağıdaki örnekte gösterildiği gibi başlatın.  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md)
