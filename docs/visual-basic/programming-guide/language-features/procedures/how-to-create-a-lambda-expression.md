---
title: 'Nasıl yapılır: Lambda İfadesi Oluşturma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: f437166bc5206b4145d6508aa2131ec94d6eca95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a>Nasıl yapılır: Lambda İfadesi Oluşturma (Visual Basic)
A *lambda ifadesi* bir işlevi veya bir adı yok alt yordam. Lambda ifadesi bir temsilci türü geçerli olduğunda kullanılabilir.  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a>Tek satırlı lambda ifadesi işlevi oluşturmak için  
  
1.  Burada bir temsilci türü kullanılabilirdi, herhangi bir durumda anahtar sözcüğünü yazmanız `Function`, aşağıdaki örnekte olduğu gibi:  
  
     `Dim add1 =`   `Function`  
  
2.  Parantez içindeki hemen sonra `Function`, işlev parametrelerini yazın. Adından sonra belirtmeyin fark `Function`.  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3.  Parametre listesi işlev gövdesi olarak tek bir ifade yazın. İçin ifadeyi hesaplar işlev tarafından döndürülen değer değerdir. Kullanmadığınız bir `As` yan tümcesini dönüş türü belirtin.  
  
     [!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]  
  
     Lambda ifadesi bir tamsayı bağımsız değişken geçirme çağrısı.  
  
     [!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]  
  
4.  Alternatif olarak, aşağıdaki örnekte aynı sonucu elde edilir:  
  
     [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a>Tek satırlı lambda ifadesi alt yordam oluşturmak için  
  
1.  Burada bir temsilci türü kullanılabilirdi, herhangi bir durumda anahtar sözcüğünü yazmanız `Sub`, aşağıdaki örnekte gösterildiği gibi.  
  
     `Dim add1 =`   `Sub`  
  
2.  Parantez içindeki hemen sonra `Sub`, alt yordam parametrelerini yazın. Adından sonra belirtmeyin fark `Sub`.  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3.  Parametre listesi alt yordama gövdesi olarak tek bir deyimde yazın.  
  
     [!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]  
  
     Lambda ifadesi bir dize bağımsız değişkeni geçirme çağrısı.  
  
     [!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a>Çok satırlı lambda ifadesi işlevi oluşturmak için  
  
1.  Burada bir temsilci türü kullanılabilirdi, herhangi bir durumda anahtar sözcüğünü yazmanız `Function`, aşağıdaki örnekte gösterildiği gibi.  
  
     `Dim add1 =`   `Function`  
  
2.  Parantez içindeki hemen sonra `Function`, işlev parametrelerini yazın. Adından sonra belirtmeyin fark `Function`.  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3.  ENTER tuşuna basın. `End Function` Deyimi otomatik olarak eklenir.  
  
4.  İşlev gövdesi içinde bir ifade oluşturun ve değerini döndürmek için aşağıdaki kodu ekleyin. Kullanmadığınız bir `As` yan tümcesini dönüş türü belirtin.  
  
     [!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]  
  
     Lambda ifadesi bir tamsayı bağımsız değişken geçirme çağrısı.  
  
     [!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a>Çok satırlı lambda ifadesi alt yordam oluşturmak için  
  
1.  Burada bir temsilci türü kullanılabilirdi, herhangi bir durumda anahtar sözcüğünü yazmanız `Sub`, aşağıdaki örnekte gösterildiği gibi:  
  
     `Dim add1 =`   `Sub`  
  
2.  Parantez içindeki hemen sonra `Sub`, alt yordam parametrelerini yazın. Adından sonra belirtmeyin fark `Sub`.  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3.  ENTER tuşuna basın. `End Sub` Deyimi otomatik olarak eklenir.  
  
4.  İşlev gövdesi içinde alt yordam çağrıldığında yürütmek için aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]  
  
     Lambda ifadesi bir dize bağımsız değişkeni geçirme çağrısı.  
  
     [!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]  
  
## <a name="example"></a>Örnek  
 Lambda ifadeleri yaygın kullanımı için bağımsız değişken türü olan bir parametre olarak geçirilebilir işlevi tanımlamaktır `Delegate`. Aşağıdaki örnekte, <xref:System.Diagnostics.Process.GetProcesses%2A> yöntemi yerel bilgisayarda çalışan işlemlerin bir dizi döndürür. <xref:System.Linq.Enumerable.Where%2A> Yönteminden <xref:System.Linq.Enumerable> sınıfı gerektiren bir `Boolean` temsilci bağımsız değişken olarak. Örnekte lambda ifadesi bu amaç için kullanılır. Döndürdüğü `True` her işlem için yalnızca bir iş parçacığı sahip ve bu seçili `filteredList`.  
  
 [!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]  
  
 Önceki örnekte yazıldığı aşağıdaki kodu eşdeğerdir [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] sözdizimi:  
  
 [!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq.Enumerable>  
 [Lambda İfadeleri](./lambda-expressions.md)  
 [Function Deyimi](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub Deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Nasıl yapılır: Visual Basic'de başka bir yordama yordam geçirme](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [Delegate Deyimi](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
