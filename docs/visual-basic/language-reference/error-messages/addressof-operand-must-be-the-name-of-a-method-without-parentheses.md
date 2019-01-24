---
title: '&#39;AddressOf&#39; işlenen olmalıdır (parantezler olmadan) bir yöntemin adı.'
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: 6f9827d885996ffab8bdab91d0f774a57073e4a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565156"
---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a>&#39;AddressOf&#39; işlenen olmalıdır (parantezler olmadan) bir yöntemin adı.
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
