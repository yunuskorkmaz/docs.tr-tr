---
title: "Nasıl yapılır: Bir İşleci Tanımlama (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 51921ee38204fd528ed19436806fc9433abbdc5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-an-operator-visual-basic"></a>Nasıl yapılır: Bir İşleci Tanımlama (Visual Basic)
Bir sınıf veya yapı tanımladıysanız, standart bir işleç davranışını tanımlayabilirsiniz (gibi `*`, `<>`, veya `And`) birine veya ikisine de işlenenler olduğunda sınıf veya yapı türünü.  
  
 Sınıf veya yapı içinde bir işleç yordamı olarak standart işleci tanımlama. Tüm işleç yordamları olmalıdır `Public` `Shared`.  
  
 Bir sınıf veya yapı bir işleci tanımlama olarak da adlandırılır *aşırı* işleci.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tanımlar `+` işleci bir yapı için adlı `height`. Yükseklik fit ve inç ölçülen yapısı kullanır. Bir *inç* 2,54 santimetreden ve bir *altbilgi* 12 inç'tir. Normalleştirilmiş değerleri (inç < 12.0) sağlamak için Oluşturucusu yapar *modulo* 12 aritmetik. `+` İşleci Oluşturucusu normalleştirilmiş değerlerini oluşturmak için kullanır.  
  
 [!code-vb[VbVbcnProcedures#25](./codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]  
  
 Yapıyı test `height` aşağıdaki kod ile.  
  
 [!code-vb[VbVbcnProcedures#26](./codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]  
  
 Daha fazla bilgi ve örnekler için bkz: [İşleç aşırı yüklemesi Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşleç yordamları](./operator-procedures.md)  
 [Nasıl yapılır: bir dönüşüm işleci tanımlama](./how-to-define-a-conversion-operator.md)  
 [Nasıl yapılır: bir işleç yordamı çağırma](./how-to-call-an-operator-procedure.md)  
 [Nasıl yapılır: işleçleri tanımlayan bir sınıf kullanma](./how-to-use-a-class-that-defines-operators.md)  
 [Operator deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Structure deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Nasıl yapılır: bir yapıyı bildirme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Mod işleci](../../../../visual-basic/language-reference/operators/mod-operator.md)
