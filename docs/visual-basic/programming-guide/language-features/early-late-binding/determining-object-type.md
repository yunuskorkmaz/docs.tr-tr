---
title: Nesne Türünü Belirleme (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6d24be68ea4a9872f8f4fe89c1aabb943fbcb91
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="determining-object-type-visual-basic"></a>Nesne Türünü Belirleme (Visual Basic)
Genel nesne değişkenleri (diğer bir deyişle, değişkenleri olarak bildirdiğiniz `Object`) herhangi bir sınıftan nesneleri içerebilir. Tür değişkenler kullanırken `Object`, nesne sınıfına göre farklı eylemleri gerekebilir; örneğin, bazı nesneler belirli özelliği veya yöntemi desteklemiyor olabilir. Visual Basic sağlayan bir nesne değişkeninin hangi nesne türünü depolanan belirleme iki anlamına gelir: `TypeName` işlevi ve `TypeOf...Is` işleci.  
  
## <a name="typename-and-typeofis"></a>TypeName ve TypeOf... Değil  
 `TypeName` İşlev bir dize döndürür ve aşağıdaki kod parçasında gösterildiği gibi bir nesne sınıf adını görüntülemek veya depolamak gereken en iyi seçimdir:  
  
 [!code-vb[VbVbalrOOP#92](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]  
  
 `TypeOf...Is` İşlecidir nesnenin türü, test etmek için en iyi seçenek, bir eşdeğer dize karşılaştırma kullanmaktan çok daha hızlı olduğundan `TypeName`. Aşağıdaki kod parçası kullanan `TypeOf...Is` içinde bir `If...Then...Else` deyimi:  
  
 [!code-vb[VbVbalrOOP#93](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]  
  
 Bir uyarı notu buraya son sözcüktür. `TypeOf...Is` Operatörü döndürür `True` bir nesne belirli bir tür ya da belirli bir türden türetilmiş. Hemen Visual Basic ile bunu her şeyi normalde dizeler ve tamsayılar gibi nesneler olarak düşünülen bazı öğeler içerir nesneleri içerir. Bu nesneler türetilmiş ve yöntemleri devralır <xref:System.Object>. Geçirildiğinde bir `Integer` ve ile değerlendirilen `Object`, `TypeOf...Is` operatörü döndürür `True`. Aşağıdaki örnek, rapor parametresi `InParam` hem de bir `Object` ve bir `Integer`:  
  
 [!code-vb[VbVbalrOOP#94](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]  
  
 Aşağıdaki örnek, her ikisi de kullanır `TypeOf...Is` ve `TypeName` kendisine geçirilen nesne türünü belirlemek için `Ctrl` bağımsız değişkeni. `TestObject` Yordam çağrıları `ShowType` üç farklı türde denetimleri ile.  
  
#### <a name="to-run-the-example"></a>Örneği çalıştırmak için  
  
1.  Yeni bir Windows uygulama projesi oluşturun ve ekleyin bir <xref:System.Windows.Forms.Button> denetimi, bir <xref:System.Windows.Forms.CheckBox> denetimi ve <xref:System.Windows.Forms.RadioButton> forma denetim.  
  
2.  Formunuzda düğmesinden çağrı `TestObject` yordamı.  
  
3.  Formunuz için aşağıdaki kodu ekleyin:  
  
     [!code-vb[VbVbalrOOP#95](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Information.TypeName%2A>  
 [Bir Dize Adı Kullanarak Bir Özelliği veya Yöntemi Çağırma](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)  
 [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [If...Then...Else Deyimi](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [String Veri Türü](../../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [Integer Veri Türü](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
