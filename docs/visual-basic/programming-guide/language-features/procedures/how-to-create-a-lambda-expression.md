---
title: 'Nasıl yapılır: Lambda İfadesi Oluşturma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: f437166bc5206b4145d6508aa2131ec94d6eca95
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244904"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a>Nasıl yapılır: Lambda İfadesi Oluşturma (Visual Basic)
A *lambda ifadesi* bir işlev veya bir ada sahip bir alt yordam. Bir lambda ifadesi, bir temsilci türü geçerli olduğu her yerde kullanılabilir.  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a>Tek satırlı lambda ifadesi işlevi oluşturmak için  
  
1.  Burada bir temsilci türü kullanılabilir herhangi bir durumda anahtar sözcüğü yazın `Function`, aşağıdaki örnekte olduğu gibi:  
  
     `Dim add1 =`   `Function`  
  
2.  Parantez içinde hemen sonra `Function`, işlev parametrelerini yazın. Sonra adı belirtmeyin fark `Function`.  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3.  Parametre listesi işlev gövdesi olarak tek bir ifade yazın. İfadeyi değerlendiren işlevi tarafından döndürülen değer değerdir. Kullanmadığınız bir `As` dönüş türü belirtmek için yan tümcesi.  
  
     [!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]  
  
     Lambda ifadesi tamsayı bağımsız değişken geçirme çağrı.  
  
     [!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]  
  
4.  Alternatif olarak, aşağıdaki örnekte aynı sonucu elde edilir:  
  
     [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a>Tek satırlı lambda ifadesi alt yordam oluşturmak için  
  
1.  Burada bir temsilci türü kullanılabilir herhangi bir durumda anahtar sözcüğü yazın `Sub`, aşağıdaki örnekte gösterildiği gibi.  
  
     `Dim add1 =`   `Sub`  
  
2.  Parantez içinde hemen sonra `Sub`, alt yordam parametreleri yazın. Sonra adı belirtmeyin fark `Sub`.  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3.  Parametre listesi tek deyimde alt yordam gövdesi olarak yazın.  
  
     [!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]  
  
     Lambda ifadesi bir dize bağımsız değişkeni geçirme çağrı.  
  
     [!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a>Çok satırlı lambda ifadesi işlevi oluşturmak için  
  
1.  Burada bir temsilci türü kullanılabilir herhangi bir durumda anahtar sözcüğü yazın `Function`, aşağıdaki örnekte gösterildiği gibi.  
  
     `Dim add1 =`   `Function`  
  
2.  Parantez içinde hemen sonra `Function`, işlev parametrelerini yazın. Sonra adı belirtmeyin fark `Function`.  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3.  ENTER tuşuna basın. `End Function` Deyimi otomatik olarak eklenir.  
  
4.  İşlev gövdesi içinde bir ifade oluşturun ve değeri döndürmek için aşağıdaki kodu ekleyin. Kullanmadığınız bir `As` dönüş türü belirtmek için yan tümcesi.  
  
     [!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]  
  
     Lambda ifadesi tamsayı bağımsız değişken geçirme çağrı.  
  
     [!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a>Çok satırlı lambda ifadesi alt yordam oluşturmak için  
  
1.  Burada bir temsilci türü kullanılabilir herhangi bir durumda anahtar sözcüğü yazın `Sub`, aşağıdaki örnekte gösterildiği gibi:  
  
     `Dim add1 =`   `Sub`  
  
2.  Parantez içinde hemen sonra `Sub`, alt yordam parametreleri yazın. Sonra adı belirtmeyin fark `Sub`.  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3.  ENTER tuşuna basın. `End Sub` Deyimi otomatik olarak eklenir.  
  
4.  İşlev gövdesi içinde alt yordam çağrıldığında yürütmek için aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]  
  
     Lambda ifadesi bir dize bağımsız değişkeni geçirme çağrı.  
  
     [!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]  
  
## <a name="example"></a>Örnek  
 Lambda ifadeleri yaygın kullanımı bir işlev için bağımsız değişken türü olan bir parametre olarak geçirilebilir tanımlamaktır `Delegate`. Aşağıdaki örnekte, <xref:System.Diagnostics.Process.GetProcesses%2A> yöntem, yerel bilgisayarda çalışan işlemlerin bir dizi döndürür. <xref:System.Linq.Enumerable.Where%2A> Yönteminden <xref:System.Linq.Enumerable> sınıfı gerektirir bir `Boolean` temsilci bağımsız değişken olarak. Bu örnek, lambda ifadesi bu amaç için kullanılır. Döndürür `True` her işlem için yalnızca bir iş parçacığı olan ve bu seçili `filteredList`.  
  
 [!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]  
  
 Önceki örnekte, yazıldığı aşağıdaki koda eşdeğerdir [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] söz dizimi:  
  
 [!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq.Enumerable>  
 [Lambda İfadeleri](./lambda-expressions.md)  
 [Function Deyimi](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub Deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Nasıl yapılır: Visual Basic'de başka bir yordama Visual Basic'te](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [Delegate Deyimi](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
