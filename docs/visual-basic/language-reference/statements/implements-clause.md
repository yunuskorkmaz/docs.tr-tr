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
ms.openlocfilehash: cb0ea5ce52effad4df541e6a9196b1faf279262e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522521"
---
# <a name="implements-clause-visual-basic"></a>Implements Tümcesi (Visual Basic)
Bir sınıf veya yapı üyesine bir arabirim içinde tanımlanmış bir üye için uygulama sağladığını gösterir.  
  
## <a name="remarks"></a>Açıklamalar  
`Implements` Anahtar sözcüğü ile aynı değil [Implements deyimi](../../../visual-basic/language-reference/statements/implements-statement.md). Kullandığınız `Implements` bir sınıf veya yapı, bir veya daha fazla arabirimlerini uygular ve sonra her üyesi için kullanırsınız belirtmek için deyimini `Implements` hangi arabirimi ve hangi belirtmek için anahtar sözcüğü uygular.

Bir sınıf veya yapı bir arabirim uygularsa, içermelidir `Implements` deyimi hemen sonra [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md) veya [Structure deyimi](../../../visual-basic/language-reference/statements/structure-statement.md), ve tüm üyelerini uygulamalıdır arabirim tarafından tanımlanan.

## <a name="reimplementation"></a>Reimplementation  
Türetilen bir sınıfta temel sınıf zaten uygulamıştır bir arabirim üyesi yeniden uygulayın. Bu aşağıdaki bakımdan bir temel sınıf üyesinin geçersiz kılan kaynaklardan farklı.

- Temel sınıf üyesi olması gerekmez. [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) reimplemented için.
- Üyesi farklı bir adla yeniden uygulayın.

`Implements` Anahtar sözcüğü aşağıdaki bağlamlarında kullanılabilir:
- [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Implements Deyimi](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)
- [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)
