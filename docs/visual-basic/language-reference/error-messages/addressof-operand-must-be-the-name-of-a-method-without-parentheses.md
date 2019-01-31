---
title: "'AddressOf' işleneni bir metot adı olmalıdır (parantezler olmadan)"
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: 37b02ab76730458b757835fda37b8cb145ed93ad
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262120"
---
# <a name="addressof-operand-must-be-the-name-of-a-method-without-parentheses"></a>'AddressOf' işleneni bir metot adı olmalıdır (parantezler olmadan)
`AddressOf` İşleci, belirli bir yordam başvuran bir yordam temsilci örneği oluşturur. Söz dizimi aşağıdaki gibidir.  
  
 `AddressOf``procedurename`  
  
 Bağımsız değişkeni aşağıdaki parantez içine eklenen `AddressOf`, burada Hiçbiri gereklidir.  
  
 **Hata Kimliği:** BC30577  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Bağımsız değişkeni aşağıdaki etrafındaki parantezleri kaldırın `AddressOf`.  
  
2.  Bağımsız değişken bir yöntem adı olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [AddressOf İşleci](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Temsilciler](../../../visual-basic/programming-guide/language-features/delegates/index.md)
