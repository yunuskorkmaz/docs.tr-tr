---
title: Nesne Türünü Belirleme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: 5980549dd063b2c7d5c60ebd4e9762284c072009
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586624"
---
# <a name="determining-object-type-visual-basic"></a>Nesne Türünü Belirleme (Visual Basic)
Genel nesne değişkenleri (diğer bir deyişle, değişkenleri olarak bildirdiğiniz `Object`) herhangi bir sınıftan nesneleri içerebilir. Türü değişkenlerindeki kullanırken `Object`, nesnenin sınıfına göre farklı eylemlerde gerekebilir; örneğin, bazı nesneler belirli bir özelliği veya yöntemi desteklemiyor olabilir. Visual Basic nesne türü bir nesne değişkenine depolandığını belirleyen iki yol sunar: `TypeName` işlevi ve `TypeOf...Is` işleci.  
  
## <a name="typename-and-typeofis"></a>TypeName ve TypeOf... Olduğu  
 `TypeName` İşlevi bir dize döndürür ve aşağıdaki kod parçasını gösterildiği depolamak veya bir nesne sınıfı adını görüntülemek gereken en iyi seçenektir:  
  
 [!code-vb[VbVbalrOOP#92](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]  
  
 `TypeOf...Is` İşleci, bir nesnenin türü, test etmek için en iyi seçenek, bir dize karşılaştırma kullanmaktan çok daha hızlı olduğundan `TypeName`. Aşağıdaki kod parçası kullanan `TypeOf...Is` içinde bir `If...Then...Else` deyimi:  
  
 [!code-vb[VbVbalrOOP#93](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]  
  
 Bir sözcük uyarı son İşte. `TypeOf...Is` İşleci döndürür `True` bir nesne belirli bir tür ya da belirli bir türden türetilir. Hemen Visual Basic ile yaptığınız her şey, normalde, dizeler ve tamsayılar gibi nesneler olarak düşünülebilir bazı öğeleri içeren nesneleri içerir. Bu nesnelerin türetilmiştir ve yöntemleri devralan <xref:System.Object>. Geçirildiğinde bir `Integer` ve ile değerlendirilen `Object`, `TypeOf...Is` işleci döndürür `True`. Aşağıdaki örnek, rapor parametresi `InParam` hem de bir `Object` ve `Integer`:  
  
 [!code-vb[VbVbalrOOP#94](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]  
  
 Aşağıdaki örnek, her ikisi de kullanır `TypeOf...Is` ve `TypeName` kendisine geçirilen nesne türünü belirlemek için `Ctrl` bağımsız değişken. `TestObject` Yordam çağrılarını `ShowType` denetimleri üç farklı tür ile.  
  
#### <a name="to-run-the-example"></a>Örneği çalıştırmak için  
  
1.  Yeni bir Windows uygulaması projesi oluşturma ve ekleme bir <xref:System.Windows.Forms.Button> denetimi, bir <xref:System.Windows.Forms.CheckBox> denetimi ve bir <xref:System.Windows.Forms.RadioButton> forma.  
  
2.  Formunuzdaki düğmesinden çağrı `TestObject` yordamı.  
  
3.  Formunuza aşağıdaki kodu ekleyin:  
  
     [!code-vb[VbVbalrOOP#95](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [Bir Dize Adı Kullanarak Bir Özelliği veya Yöntemi Çağırma](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)
- [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [If...Then...Else Deyimi](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [String Veri Türü](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Integer Veri Türü](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
