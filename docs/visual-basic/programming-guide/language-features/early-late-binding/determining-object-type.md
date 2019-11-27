---
title: Nesne Türünü Belirleme
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: a77cc0603a0b61f58a4aa703c4b1e6ef4c26729c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345193"
---
# <a name="determining-object-type-visual-basic"></a>Nesne Türünü Belirleme (Visual Basic)
Genel nesne değişkenleri (yani, `Object`olarak bildirdiğiniz değişkenler) herhangi bir sınıftan nesne tutabilir. `Object`değişkenleri kullanırken, nesnenin sınıfına göre farklı eylemler gerçekleştirmeniz gerekebilir; Örneğin, bazı nesneler belirli bir özelliği veya yöntemi desteklemiyor. Visual Basic, nesne değişkeninde hangi tür nesnenin depolandığını belirlemek için iki yol sunar: `TypeName` işlevi ve `TypeOf...Is` işleci.  
  
## <a name="typename-and-typeofis"></a>TypeName ve TypeOf... Eklenir  
 `TypeName` işlevi bir dize döndürür ve aşağıdaki kod parçasında gösterildiği gibi bir nesnenin sınıf adını depolamanız veya görüntüetmeniz gerektiğinde en iyi seçenektir:  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 `TypeOf...Is` işleci, bir nesnenin türünü test etmek için en iyi seçimdir, çünkü `TypeName`kullanılarak denk dize karşılaştırmasının çok daha hızlıdır. Aşağıdaki kod parçası bir `If...Then...Else` deyimindeki `TypeOf...Is` kullanır:  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 Burada dikkatli bir sözcük verilmiştir. `TypeOf...Is` işleci, bir nesne belirli bir tür veya belirli bir türden türetildiyse `True` döndürür. Visual Basic ile yaptığınız neredeyse her şey, genellikle dizeler ve tamsayılar gibi nesneler olarak düşünmeden bazı öğeleri içeren nesneler içerir. Bu nesneler, ' den türetilir ve <xref:System.Object>yöntemlerden devralınır. Bir `Integer` geçirildiğinde ve `Object`ile değerlendirildiğinde `TypeOf...Is` işleci `True`döndürür. Aşağıdaki örnek, `InParam` parametresinin hem `Object` hem de `Integer`olduğunu bildiriyor:  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 Aşağıdaki örnek, `Ctrl` bağımsız değişkeninde kendisine geçirilen nesne türünü belirleyebilmek için hem `TypeOf...Is` hem de `TypeName` kullanır. `TestObject` yordamı üç farklı denetim türüyle `ShowType` çağırır.  
  
#### <a name="to-run-the-example"></a>Örneği çalıştırmak için  
  
1. Yeni bir Windows uygulaması projesi oluşturun ve forma bir <xref:System.Windows.Forms.Button> denetimi, <xref:System.Windows.Forms.CheckBox> denetimi ve bir <xref:System.Windows.Forms.RadioButton> denetimi ekleyin.  
  
2. Formunuzdaki düğmeden `TestObject` yordamını çağırın.  
  
3. Formunuza aşağıdaki kodu ekleyin:  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [Bir Dize Adı Kullanarak Bir Özelliği veya Yöntemi Çağırma](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)
- [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [If...Then...Else Deyimi](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [String Veri Türü](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Integer Veri Türü](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
