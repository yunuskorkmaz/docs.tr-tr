---
title: "Nasıl yapılır: Deyimler (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 190ec9fc2392e6e4adae9b2b612edd69d73cedfd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-label-statements-visual-basic"></a>Nasıl yapılır: Deyimler (Visual Basic)
Deyim blokları virgüllerle ayrılmış kod satırlarını oluşur. Öncesinde bir tanımlayıcı string veya tamsayı kod satırlarını olmasını denirse *etiketli*. Deyimi etiketleri kullanılmak üzere ifadelerle gibi tanımlamak için kod satırı işaretlemek için kullanılan `On Error Goto`.  
  
 Etiketleri ya da geçerli Visual Basic tanımlayıcıları olabilir — programlama öğeleri tanımlamak olanlar gibi — veya tamsayı değişmez değerleri. Bir etiket bir kaynak kod satırı başında görünmesi gerekir ve olup, aynı satırda bir deyimi tarafından izlenir bakılmaksızın bir iki nokta gelmelidir.  
  
 Derleyici satırının başına, önceden tanımlanan bir tanımlayıcı eşleşip eşleşmediğini kontrol ederek etiketleri tanımlar. Yoksa, derleyici bir etiket olduğunu varsayar.  
  
 Etiketler kendi bildirimi alanınız ve diğer tanımlayıcıları ile engel olmaz. Bir etiketin yönteminin gövdesi kapsamıdır. Etiket bildirimi herhangi bir belirsiz durumda önceliklidir.  
  
> [!NOTE]
>  Etiketleri yalnızca executable deyimleri yöntemleri içinde kullanılabilir.  
  
### <a name="to-label-a-line-of-code"></a>Etiket bir kod satırı  
  
-   Kaynak kodu satır başında, iki nokta arkasından bir tanımlayıcı yerleştirin.  
  
     Örneğin, aşağıdaki kod satırlarını ile etiketlenir `Jump` ve `120`sırasıyla:  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Deyimleri](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Program yapısı ve kod kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
