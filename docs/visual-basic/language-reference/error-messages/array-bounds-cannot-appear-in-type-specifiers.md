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
