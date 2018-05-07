---
title: Implements Tümcesi (Visual Basic)
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
ms.openlocfilehash: 1e34245ac528e9e2463afbfd07dff91bf693830b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="implements-clause-visual-basic"></a>Implements Tümcesi (Visual Basic)
Sınıf veya yapı üyesi bir arabiriminde tanımlanan üye uygulamasını sağladığını gösterir.  
  
## <a name="remarks"></a>Açıklamalar  
`Implements` Anahtar sözcüğü ile aynı değil [Implements deyimi](../../../visual-basic/language-reference/statements/implements-statement.md). Kullandığınız `Implements` bir sınıf veya yapı bir veya daha fazla arabirimlerini uygular ve ardından her üye için kullandığınız belirtmek için deyimi `Implements` hangi arabirimi ve hangi üye belirtmek için anahtar sözcüğü, uygular.

Bir sınıf veya yapı arabirim uygularsa, içermelidir `Implements` deyimi hemen sonra [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md) veya [Structure deyimi](../../../visual-basic/language-reference/statements/structure-statement.md), ve tüm üyelerin uygulamalıdır arabirim tarafından tanımlanır.

## <a name="reimplementation"></a>Yeniden uygulama  
Türetilen bir sınıfta temel sınıf zaten uyguladı bir arabirim üyesini yeniden uygulamalı. Bu, geçersiz kılmasını temel sınıf üyesi aşağıdaki bakımlardan farklıdır:

- Taban sınıf üyesi olması gerekmez [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) reimplemented için.
- Üye farklı bir adla yeniden uygulamalı.

`Implements` Anahtar sözcüğünü aşağıdaki bağlamlarında kullanılabilir:
- [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Implements Deyimi](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)
