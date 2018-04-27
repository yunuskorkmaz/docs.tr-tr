---
title: 'Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
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
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e0bcfaeca638dfabb841a9e935b872f76fdf957
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma (Visual Basic)
Bir sınıf veya kendi işleçleri tanımlayan yapı kullanıyorsanız, bu işleçler Visual Basic'ten erişebilir.  
  
 Bir sınıf veya yapı bir işleci tanımlama olarak da adlandırılır *aşırı* işleci.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek SQL yapısı erişen <xref:System.Data.SqlTypes.SqlString>, dönüşüm işleçleri tanımlar ([CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md)) bir SQL dizesi ve Visual Basic dize arasında iki yönlü. Kullanım `CType(` *SQL dizesi ifadesini*, `String)` SQL dizesi bir Visual Basic dizeye dönüştürmek için ve `CType(` *Visual Basic dize ifadesi*, <xref:System.Data.SqlTypes.SqlString> `)` ters yönde dönüştürülemiyor.  
  
 [!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 <xref:System.Data.SqlTypes.SqlString> Yapısını tanımlayan bir dönüşüm işleci ([CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md)) gelen `String` için <xref:System.Data.SqlTypes.SqlString> ve başka bir <xref:System.Data.SqlTypes.SqlString> için `String`. Atayan deyimi `title` için `jobTitle` ilk işleci kullanır ve <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> işlev çağrısı kullanır ikinci.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Sınıf veya yapı kullanmakta olduğunuz kullanmak istediğiniz işleci tanımlar emin olun. Sınıf veya yapı her işleci aşırı yükleme için kullanılabilir tanımlanmış varsayalım değil. Kullanılabilir operatörler listesi için bkz: [Operator deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 Uygun dahil `Imports` başında SQL dizesi bildirimi kaynak dosyasının (Bu durumda <xref:System.Data.SqlTypes>).  
  
 Projenizi System.Data ve System.XML başvuruları olması gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşleç Yordamları](./operator-procedures.md)  
 [Nasıl yapılır: İşleç Tanımlama](./how-to-define-an-operator.md)  
 [Nasıl yapılır: Dönüştürme İşleci Tanımlama](./how-to-define-a-conversion-operator.md)  
 [Nasıl yapılır: Bir İşleç Yordamı Çağırma](./how-to-call-an-operator-procedure.md)  
 [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Structure Deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Nasıl yapılır: Bir Yapıyı Bildirme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Örtük ve Açık Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Genişletme ve Daraltma Dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
