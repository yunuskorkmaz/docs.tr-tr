---
title: '&#39;&lt;anahtar sözcüğü&gt; &#39; yalnızca bir örnek yöntemi içinde geçerlidir'
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: a464a059aa2d13e3472b9770960384b6be398092
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595948"
---
# <a name="39ltkeywordgt39-is-valid-only-within-an-instance-method"></a>&#39;&lt;anahtar sözcüğü&gt; &#39; yalnızca bir örnek yöntemi içinde geçerlidir
`Me`, `MyClass`, Ve `MyBase` anahtar sözcükleri belirli bir sınıfın örneklerine bakın. Bunları bir paylaşılan içinde kullanamazsınız `Function` veya `Sub` yordamı.  
  
 **Hata Kimliği:** BC30043  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Anahtar sözcüğü yordamdan kaldırmak veya kaldırmak `Shared` yordam bildirimi from anahtar sözcüğü.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nesne Değişkeni Ataması](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me, My, MyBase ve MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
