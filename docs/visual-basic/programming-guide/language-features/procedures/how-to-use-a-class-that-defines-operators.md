---
title: "Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 223b3fc84fe75d1d530cd182c9332e5c663aa519
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma (Visual Basic)
Bir sınıf veya kendi işleçleri tanımlayan yapı kullanıyorsanız, bu işleçler öğesinden erişebilirsiniz [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
 Bir sınıf veya yapı bir işleci tanımlama olarak da adlandırılır *aşırı* işleci.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek SQL yapısı erişen <xref:System.Data.SqlTypes.SqlString>, dönüşüm işleçleri tanımlar ([CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md)) bir SQL dizesi arasında iki yönlü ve [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dize. Kullanım `CType(` *SQL dizesi ifadesini*, `String)` SQL dizeye dönüştürmek için bir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dize ve `CType(` *Visual Basic dize ifadesi*, <xref:System.Data.SqlTypes.SqlString> `)` ters yönde dönüştürülemiyor.  
  
 [!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 <xref:System.Data.SqlTypes.SqlString> Yapısını tanımlayan bir dönüşüm işleci ([CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md)) gelen `String` için <xref:System.Data.SqlTypes.SqlString> ve başka bir <xref:System.Data.SqlTypes.SqlString> için `String`. Atayan deyimi `title` için `jobTitle` ilk işleci kullanır ve <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> işlev çağrısı kullanır ikinci.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Sınıf veya yapı kullanmakta olduğunuz kullanmak istediğiniz işleci tanımlar emin olun. Sınıf veya yapı her işleci aşırı yükleme için kullanılabilir tanımlanmış varsayalım değil. Kullanılabilir operatörler listesi için bkz: [Operator deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 Uygun dahil `Imports` başında SQL dizesi bildirimi kaynak dosyasının (Bu durumda <xref:System.Data.SqlTypes>).  
  
 Projenizi System.Data ve System.XML başvuruları olması gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşleç yordamları](./operator-procedures.md)  
 [Nasıl yapılır: bir işleci tanımlama](./how-to-define-an-operator.md)  
 [Nasıl yapılır: bir dönüşüm işleci tanımlama](./how-to-define-a-conversion-operator.md)  
 [Nasıl yapılır: bir işleç yordamı çağırma](./how-to-call-an-operator-procedure.md)  
 [Genişletme](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [Daraltma](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Structure deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Nasıl yapılır: bir yapıyı bildirme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Örtük ve açık dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Genişletme ve daraltma dönüşümleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
