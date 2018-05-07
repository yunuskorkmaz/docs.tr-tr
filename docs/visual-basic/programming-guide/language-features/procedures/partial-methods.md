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
ms.openlocfilehash: a1708c1d953a60429c1bd87fd858da5c50a3e759
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="partial-methods-visual-basic"></a>Kısmi Yöntemler (Visual Basic)
Kısmi yöntemler koda Özel mantık ekleme geliştiricilerin. Genellikle, bir tasarımcı tarafından oluşturulan sınıfın parçası kodudur. Kısmi yöntemler Kod Oluşturucu tarafından oluşturulan bir parçalı sınıf tanımlanır ve bunlar genellikle bir şey değiştirildiğini bildirim sağlamak için kullanılır. Bunlar değişikliğe yanıt özel davranış belirlemek Geliştirici etkinleştirin.  
  
 Kod oluşturucunun Tasarımcı yalnızca yöntem imzası ve yöntemine yönelik bir veya daha fazla çağrılar tanımlar. Oluşturulan kod davranışını özelleştirmek istiyorsanız geliştiriciler sonra uygulamaları yöntemi sağlar. Hiçbir uygulama sağlandığında yöntemine yönelik çağrılar hiçbir ek performans ek yükünün kaynaklanan derleyici tarafından kaldırılır.  
  
## <a name="declaration"></a>Bildirim  
 Oluşturulan kodun anahtar sözcüğünü girerek kısmi bir yöntemin tanımı işaretler `Partial` imza satırın başındaki.  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 Tanımı aşağıdaki koşulları karşılaması gerekir:  
  
-   Yöntem olmalıdır bir `Sub`değil bir `Function`.  
  
-   Yönteminin gövdesi boş bırakılması gerekir.  
  
-   Erişim değiştiricisi olmalıdır `Private`.  
  
## <a name="implementation"></a>Uygulama  
 Uygulama, öncelikle kısmi yöntemin gövdesine doldurma oluşur. Uygulama tanımından ayrı bir parçalı sınıf genellikle bulunduğu ve oluşturulan kod genişletmek isteyen bir geliştirici tarafından yazılan.  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 Önceki örneği bildiriminde imza tam olarak çoğaltır, ancak Çeşitlemeler mümkündür. Özellikle, diğer değiştiricileri gibi eklenebilir `Overloads` veya `Overrides`. Yalnızca bir `Overrides` değiştiricisi izin verilir. Yöntemi değiştirici hakkında daha fazla bilgi için bkz: [Sub deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="use"></a>Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında  
 Diğer çağırırdı gibi kısmi bir yöntem çağrısı `Sub` yordamı. Yöntem uygulanmadı, bağımsız olarak değerlendirilir ve yönteminin gövdesi yürütülür. Ancak, kısmi yöntemi uygulama isteğe bağlı olduğunu unutmayın. Yöntem uygulanmadı, bir çağrısına hiçbir etkisi olmaz ve yöntemi için bağımsız değişken olarak geçirilen ifade değerlendirilmez.  
  
## <a name="example"></a>Örnek  
 Product.Designer.vb adındaki bir dosyada tanımlayan bir `Product` olan sınıfı bir `Quantity` özelliği.  
  
 [!code-vb[VbVbalrPartialMeths#4](./codesnippet/VisualBasic/partial-methods_1.vb)]  
  
 Product.vb adındaki bir dosyada için bir uygulama sunmak `QuantityChanged`.  
  
 [!code-vb[VbVbalrPartialMeths#5](./codesnippet/VisualBasic/partial-methods_2.vb)]  
  
 Son olarak, bir proje ana yönteminde bildirme bir `Product` örneği ve sağlamak için bir başlangıç değeri kendi `Quantity` özelliği.  
  
 [!code-vb[VbVbalrPartialMeths#6](./codesnippet/VisualBasic/partial-methods_3.vb)]  
  
 Bir ileti kutusu bu iletiyi görüntüleyen görünmelidir:  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sub Deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Alt Yordamlar](./sub-procedures.md)  
 [İsteğe Bağlı Parametreler](./optional-parameters.md)  
 [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [LINQ to SQL’de Kod Oluşturma](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [Kısmi Yöntemler Kullanarak İş Mantığı Ekleme](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
