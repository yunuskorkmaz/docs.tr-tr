---
title: Kısmi Yöntemler (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.PartialMethod
- PartialMethod
helpviewer_keywords:
- custom logic into code [Visual Basic]
- partial methods [Visual Basic]
- partial [Visual Basic], methods [Visual Basic]
- methods [Visual Basic], partial methods
- inserting custom logic into code
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
ms.openlocfilehash: 765a667f18340c53909c3ff1e9fcc5f2ffc0f9bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791943"
---
# <a name="partial-methods-visual-basic"></a>Kısmi Yöntemler (Visual Basic)
Kısmi yöntemler, koda Özel mantık eklemek geliştiricilerin sağlar. Genellikle, kod tasarımcı tarafından oluşturulan bir sınıf parçasıdır. Kısmi yöntemler bir kod Oluşturucu tarafından oluşturulan bir kısmi sınıf tanımlanır ve bunlar genellikle bir şey değiştirildiğini bildirim sağlamak için kullanılır. Bunlar Geliştirici değişikliğe yanıt özel davranışını belirtmek etkinleştirin.  
  
 Kod oluşturucunun Tasarımcı yalnızca yöntem imzası ve bir veya daha fazla yöntem çağrısına tanımlar. Oluşturulan kodun davranışını özelleştirmek istiyorsanız geliştiriciler ardından uygulamaları yöntemi sağlar. Hiçbir uygulama sağlandığında yöntemine yönelik çağrılar hiçbir ek performans yükünden kaynaklanan derleyici tarafından kaldırılır.  
  
## <a name="declaration"></a>Bildirim  
 Oluşturulan kodun anahtar sözcüğünü koyarak kısmi bir yöntemin tanımını işaretler `Partial` imza satırın başlangıcında.  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 Tanımı aşağıdaki koşulları karşılaması gerekir:  
  
- Yöntem olmalıdır bir `Sub`değil bir `Function`.  
  
- Yöntemin gövdesi boş bırakılmalıdır.  
  
- Erişim değiştiricisi olmalıdır `Private`.  
  
## <a name="implementation"></a>Uygulama  
 Uygulama, kısmi yöntem gövdesinde doldurma öncelikli olarak oluşur. Uygulama, genellikle ayrı bir kısmi sınıf tanımından olduğundan ve oluşturulan kodun genişletmek isteyen bir geliştirici tarafından yazılan.  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 Önceki örneği bildiriminde imzası tam olarak çoğaltır, ancak çeşitlemeleri mümkündür. Özellikle, diğer değiştiriciler, gibi eklenebilir `Overloads` veya `Overrides`. Yalnızca bir `Overrides` değiştiricisi izin verilir. Yöntemi değiştirici hakkında daha fazla bilgi için bkz: [Sub deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="use"></a>Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında  
 Diğer çağıracak şekilde kısmi bir yöntemin çağrı `Sub` yordamı. Yöntem uygulanmadı, bağımsız değişkenleri değerlendirilir ve yöntemin gövdesi yürütülür. Ancak, kısmi bir yöntemin uygulama isteğe bağlı olduğunu unutmayın. Yöntem uygulanmadı, bir çağrı etkiye sahip değildir ve yönteme bağımsız değişken olarak geçirilen ifade değerlendirilmez.  
  
## <a name="example"></a>Örnek  
 Product.Designer.vb adlı bir dosyada tanımlayan bir `Product` sahip sınıf bir `Quantity` özelliği.  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 Product.vb adlı bir dosyada sağlamak için bir uygulama `QuantityChanged`.  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 Son olarak, bir projenin ana yöntemi bildirmek bir `Product` örneği ve sağlamak için bir başlangıç değeri kendi `Quantity` özelliği.  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 Bir ileti kutusunda Bu ileti görüntüleyen görünmesi gerekir:  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sub Deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Alt Yordamlar](./sub-procedures.md)
- [İsteğe Bağlı Parametreler](./optional-parameters.md)
- [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)
- [LINQ to SQL’de Kod Oluşturma](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [Kısmi Yöntemler Kullanarak İş Mantığı Ekleme](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
