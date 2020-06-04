---
title: Implements Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.ImplementsClause
helpviewer_keywords:
- interface implementation [Visual Basic], reimplementation
- interface members [Visual Basic], reimplementation
- interface members [Visual Basic], Implements keyword
- interface members
- members [Visual Basic], reimplementation
- interface implementation [Visual Basic], Implements keyword
- interface members [Visual Basic], implementing
- Implements keyword [Visual Basic]
- Implements statement [Visual Basic], about Implements
- members [Visual Basic], implementing
- members [Visual Basic], Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
ms.openlocfilehash: 46ab1a1148e8d73d91293aedfc407e5efdc7cfb4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404569"
---
# <a name="implements-clause-visual-basic"></a>Implements Tümcesi (Visual Basic)
Bir sınıf veya yapı üyesinin, arabirim içinde tanımlanmış bir üye için uygulama sağladığını gösterir.  
  
## <a name="remarks"></a>Açıklamalar  
`Implements`Anahtar sözcüğü, [Implements ifadesiyle](implements-statement.md)aynı değildir. `Implements`Bir sınıf ya da yapının bir veya daha fazla arabirim uyguladığını belirtmek için ifadesini kullanın ve ardından her üye için `Implements` hangi arabirimin ve hangi üyenin uyguladığı, anahtar sözcüğünü kullanırsınız.

Bir sınıf veya yapı bir arabirim uygularsa, `Implements` [sınıf deyimden](class-statement.md) veya [Yapı deyimden](structure-statement.md)hemen sonra ifadesini içermesi gerekir ve arabirim tarafından tanımlanan tüm üyeleri uygulamalıdır.

## <a name="reimplementation"></a>Yeniden uygulama  
Türetilmiş bir sınıfta, temel sınıfın zaten uygulanmış olduğu bir arabirim üyesini yeniden uygulayabilirsiniz. Bu, aşağıdaki gibi temel sınıf üyesini geçersiz kılmadan farklıdır:

- Temel sınıf üyesinin yeniden uygulanması için [geçersiz kılınabilir](../modifiers/overridable.md) olması gerekmez.
- Üyeyi farklı bir adla yeniden uygulayabilirsiniz.

`Implements`Anahtar sözcüğü aşağıdaki bağlamlarda kullanılabilir:

- [Event Deyimi](event-statement.md)
- [Function Deyimi](function-statement.md)
- [Property Deyimi](property-statement.md)
- [Sub Deyimi](sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Implements Deyimi](implements-statement.md)
- [Interface Deyimi](interface-statement.md)
- [Class Deyimi](class-statement.md)
- [Structure Yapısı](structure-statement.md)
