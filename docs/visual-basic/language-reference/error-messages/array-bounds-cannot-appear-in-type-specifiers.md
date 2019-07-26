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
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>Tür belirleyicilerde dizi sınırları bulunamaz

Dizi boyutları bir veri türü belirticisinin parçası olarak bildirilemez.

**Hata KIMLIĞI:** BC30638

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Aşağıdaki örnekte gösterildiği gibi, dizi boyutunu türden sonra yerleştirmek yerine değişken adının hemen ardından dizinin boyutunu belirtin.

  ```vb
  Dim Array(8) As Integer
  ```

- Aşağıdaki örnekte gösterildiği gibi bir diziyi tanımlayın ve istenen sayıda öğe ile başlatın.

  ```vb
  Dim Array2() As Integer = New Integer(8) {}
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [Diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md)
