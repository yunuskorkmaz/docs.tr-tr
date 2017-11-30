---
title: "Implements Tümcesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ImplementsClause
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 73f66eda29e37fda15b4c838da5a0458684131da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
- [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md)
- [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Implements deyimi](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Interface deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Structure deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)
