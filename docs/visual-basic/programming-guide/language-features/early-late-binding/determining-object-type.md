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
ms.openlocfilehash: ae338bc9bad9646abc045a652d4ef33a8863354b
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086068"
---
# <a name="determining-object-type-visual-basic"></a>Nesne Türünü Belirleme (Visual Basic)

Genel nesne değişkenleri (diğer bir deyişle, olarak bildirdiğiniz değişkenler `Object` ) herhangi bir sınıftan nesne tutabilir. Türündeki değişkenleri kullanırken `Object` , nesnenin sınıfına göre farklı eylemler gerçekleştirmeniz gerekebilir; Örneğin, bazı nesneler belirli bir özelliği veya yöntemi desteklemiyor olabilir. Visual Basic, nesne değişkeninde hangi tür nesnenin depolandığını belirlemek için iki yol sunar: `TypeName` işlev ve `TypeOf...Is` işleç.  
  
## <a name="typename-and-typeofis"></a>TypeName ve TypeOf... Eklenir  

 `TypeName`İşlevi bir dize döndürür ve aşağıdaki kod parçasında gösterildiği gibi bir nesnenin sınıf adını depolamanız veya görüntüetmeniz gerektiğinde en iyi seçenektir:  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 `TypeOf...Is`İşleci, kullanılarak denk dize karşılaştırmasının çok daha hızlı olduğu için bir nesnenin türünü test etmek için en iyi seçimdir `TypeName` . Aşağıdaki kod parçası `TypeOf...Is` bir deyimin içinde kullanır `If...Then...Else` :  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 Burada dikkatli bir sözcük verilmiştir. `TypeOf...Is`İşleci bir `True` nesne belirli bir tür ise veya belirli bir türden türetildiyse döndürür. Visual Basic ile yaptığınız neredeyse her şey, genellikle dizeler ve tamsayılar gibi nesneler olarak düşünmeden bazı öğeleri içeren nesneler içerir. Bu nesneler öğesinden türetilir ve öğesinden yöntemleri alır <xref:System.Object> . Bir ile geçirildiğinde `Integer` ve ile değerlendirildiğinde `Object` `TypeOf...Is` işleç döndürülür `True` . Aşağıdaki örnek, parametresinin hem a hem `InParam` de bir olduğunu bildirir `Object` `Integer` :  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 Aşağıdaki örnek, `TypeOf...Is` `TypeName` bağımsız değişkeninde kendisine geçirilen nesne türünü belirleyebilmek için ve ikisini kullanır `Ctrl` . `TestObject`Yordam `ShowType` üç farklı denetim türüyle çağrı yapılır.  
  
#### <a name="to-run-the-example"></a>Örneği çalıştırmak için  
  
1. Yeni bir Windows uygulaması projesi oluşturun ve forma bir <xref:System.Windows.Forms.Button> Denetim, <xref:System.Windows.Forms.CheckBox> Denetim ve <xref:System.Windows.Forms.RadioButton> denetim ekleyin.  
  
2. Formunuzdaki düğmeden `TestObject` yordamını çağırın.  
  
3. Formunuza aşağıdaki kodu ekleyin:  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [Bir Dize Adı Kullanarak Bir Özelliği veya Yöntemi Çağırma](calling-a-property-or-method-using-a-string-name.md)
- [Nesne Veri Türü](../../../language-reference/data-types/object-data-type.md)
- [If...Then...Else Deyimi](../../../language-reference/statements/if-then-else-statement.md)
- [Dize Veri Türü](../../../language-reference/data-types/string-data-type.md)
- [Integer Veri Türü](../../../language-reference/data-types/integer-data-type.md)
