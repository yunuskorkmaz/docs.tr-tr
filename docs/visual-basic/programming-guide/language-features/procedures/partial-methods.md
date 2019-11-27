---
title: Kısmi Yöntemler
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
ms.openlocfilehash: 7abf0565a985f1fb44fcf2bb91b9220d57a10f20
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352630"
---
# <a name="partial-methods-visual-basic"></a>Kısmi Yöntemler (Visual Basic)
Kısmi Yöntemler, geliştiricilerin koda özel mantık eklemesini sağlar. Genellikle kod, tasarımcı tarafından üretilen sınıfın bir parçasıdır. Kısmi Yöntemler, bir kod üreticisi tarafından oluşturulan kısmi bir sınıfta tanımlanmıştır ve genellikle bir şeyin değiştirildiğini belirten bildirim sağlamak için kullanılır. Bu, geliştiricinin değişikliğe yanıt olarak özel davranış belirtmesini sağlar.  
  
 Kod oluşturucunun Tasarımcısı yalnızca yöntem imzasını ve metoda bir veya daha fazla çağrı tanımlar. Geliştiriciler daha sonra oluşturulan kodun davranışını özelleştirmek istiyorlarsa yöntemi için uygulamalar sağlayabilir. Hiçbir uygulama sağlanmazsa, metoda yapılan çağrılar derleyici tarafından kaldırılır ve ek performans yükü yoktur.  
  
## <a name="declaration"></a>Bildirim  
 Oluşturulan kod, imza satırının başına `Partial` anahtar sözcüğünü yerleştirerek kısmi bir yöntemin tanımını işaretler.  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 Tanımın aşağıdaki koşullara uyması gerekir:  
  
- Yöntem bir `Function`değil `Sub`olmalıdır.  
  
- Metodun gövdesi boş bırakılmalıdır.  
  
- Erişim değiştiricisi `Private`olmalıdır.  
  
## <a name="implementation"></a>Uygulama  
 Uygulama, birincil olarak kısmi yöntemin gövdesini doldurmayla oluşur. Uygulama genellikle tanımdan ayrı bir kısmi sınıfta bulunur ve oluşturulan kodu genişletmek isteyen bir geliştirici tarafından yazılır.  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 Önceki örnek, bildirimin imzasını tam olarak yinelemediğinde, ancak Çeşitlemeler olasıdır. Özellikle, `Overloads` veya `Overrides`gibi diğer değiştiriciler eklenebilir. Yalnızca bir `Overrides` değiştiricisine izin verilir. Yöntem değiştiriciler hakkında daha fazla bilgi için bkz. [Sub deyimin](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="use"></a>Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında  
 Başka bir `Sub` yordamını çağırırınız gibi kısmi bir yöntemi çağırabilirsiniz. Yöntem uygulanmışsa, bağımsız değişkenler değerlendirilir ve yöntemin gövdesi yürütülür. Ancak, kısmi bir yöntemi uygulama yönteminin isteğe bağlı olduğunu unutmayın. Yöntem uygulanmemişse, bir çağrısının bir etkisi olmaz ve yöntemine bağımsız değişken olarak geçirilen ifadeler değerlendirilmez.  
  
## <a name="example"></a>Örnek  
 Product. Designer. vb adlı bir dosyada, `Quantity` özelliğine sahip bir `Product` sınıfı tanımlayın.  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 Product. vb adlı bir dosyada `QuantityChanged`için bir uygulama sağlayın.  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 Son olarak, bir projenin ana yönteminde, bir `Product` örneği bildirin ve `Quantity` özelliği için bir başlangıç değeri sağlayın.  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 Şu iletiyi görüntüleyen bir ileti kutusu görünür:  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sub Deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Alt Yordamlar](./sub-procedures.md)
- [İsteğe Bağlı Parametreler](./optional-parameters.md)
- [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)
- [LINQ to SQL’de Kod Oluşturma](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [Kısmi Yöntemler Kullanarak İş Mantığı Ekleme](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
