---
title: "'AddressOf' işleneni bir metot adı olmalıdır (parantezler olmadan)"
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: b8c67c2390df91c6a4af66e020365544e6bf369b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59323830"
---
# <a name="addressof-operand-must-be-the-name-of-a-method-without-parentheses"></a>'AddressOf' işleneni bir metot adı olmalıdır (parantezler olmadan)
`AddressOf` İşleci, belirli bir yordam başvuran bir yordam temsilci örneği oluşturur. Söz dizimi aşağıdaki gibidir.  
  
 `AddressOf``procedurename`  
  
 Bağımsız değişkeni aşağıdaki parantez içine eklenen `AddressOf`, burada Hiçbiri gereklidir.  
  
 **Hata Kimliği:** BC30577  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Bağımsız değişkeni aşağıdaki etrafındaki parantezleri kaldırın `AddressOf`.  
  
2. Bağımsız değişken bir yöntem adı olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AddressOf İşleci](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Temsilciler](../../../visual-basic/programming-guide/language-features/delegates/index.md)
