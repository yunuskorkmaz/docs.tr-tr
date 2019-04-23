---
title: 'Nasıl yapılır: Bir Lambda ifadesi (Visual Basic) oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: fc2b7ed2004b842116d051b393f00506428def61
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344552"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a>Nasıl yapılır: Bir Lambda ifadesi (Visual Basic) oluşturma
A *lambda ifadesi* bir işlev veya bir ada sahip bir alt yordam. Bir lambda ifadesi, bir temsilci türü geçerli olduğu her yerde kullanılabilir.  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a>Tek satırlı lambda ifadesi işlevi oluşturmak için  
  
1. Burada bir temsilci türü kullanılabilir herhangi bir durumda anahtar sözcüğü yazın `Function`, aşağıdaki örnekte olduğu gibi:  
  
     `Dim add1 =`   `Function`  
  
2. Parantez içinde hemen sonra `Function`, işlev parametrelerini yazın. Sonra adı belirtmeyin fark `Function`.  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3. Parametre listesi işlev gövdesi olarak tek bir ifade yazın. İfadeyi değerlendiren işlevi tarafından döndürülen değer değerdir. Kullanmadığınız bir `As` dönüş türü belirtmek için yan tümcesi.  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     Lambda ifadesi tamsayı bağımsız değişken geçirme çağrı.  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. Alternatif olarak, aşağıdaki örnekte aynı sonucu elde edilir:  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a>Tek satırlı lambda ifadesi alt yordam oluşturmak için  
  
1. Burada bir temsilci türü kullanılabilir herhangi bir durumda anahtar sözcüğü yazın `Sub`, aşağıdaki örnekte gösterildiği gibi.  
  
     `Dim add1 =`   `Sub`  
  
2. Parantez içinde hemen sonra `Sub`, alt yordam parametreleri yazın. Sonra adı belirtmeyin fark `Sub`.  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3. Parametre listesi tek deyimde alt yordam gövdesi olarak yazın.  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     Lambda ifadesi bir dize bağımsız değişkeni geçirme çağrı.  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a>Çok satırlı lambda ifadesi işlevi oluşturmak için  
  
1. Burada bir temsilci türü kullanılabilir herhangi bir durumda anahtar sözcüğü yazın `Function`, aşağıdaki örnekte gösterildiği gibi.  
  
     `Dim add1 =`   `Function`  
  
2. Parantez içinde hemen sonra `Function`, işlev parametrelerini yazın. Sonra adı belirtmeyin fark `Function`.  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3. Press ENTER. `End Function` Deyimi otomatik olarak eklenir.  
  
4. İşlev gövdesi içinde bir ifade oluşturun ve değeri döndürmek için aşağıdaki kodu ekleyin. Kullanmadığınız bir `As` dönüş türü belirtmek için yan tümcesi.  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     Lambda ifadesi tamsayı bağımsız değişken geçirme çağrı.  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a>Çok satırlı lambda ifadesi alt yordam oluşturmak için  
  
1. Burada bir temsilci türü kullanılabilir herhangi bir durumda anahtar sözcüğü yazın `Sub`, aşağıdaki örnekte gösterildiği gibi:  
  
     `Dim add1 =`   `Sub`  
  
2. Parantez içinde hemen sonra `Sub`, alt yordam parametreleri yazın. Sonra adı belirtmeyin fark `Sub`.  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3. Press ENTER. `End Sub` Deyimi otomatik olarak eklenir.  
  
4. İşlev gövdesi içinde alt yordam çağrıldığında yürütmek için aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     Lambda ifadesi bir dize bağımsız değişkeni geçirme çağrı.  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a>Örnek  
 Lambda ifadeleri yaygın kullanımı bir işlev için bağımsız değişken türü olan bir parametre olarak geçirilebilir tanımlamaktır `Delegate`. Aşağıdaki örnekte, <xref:System.Diagnostics.Process.GetProcesses%2A> yöntem, yerel bilgisayarda çalışan işlemlerin bir dizi döndürür. <xref:System.Linq.Enumerable.Where%2A> Yönteminden <xref:System.Linq.Enumerable> sınıfı gerektirir bir `Boolean` temsilci bağımsız değişken olarak. Bu örnek, lambda ifadesi bu amaç için kullanılır. Döndürür `True` her işlem için yalnızca bir iş parçacığı olan ve bu seçili `filteredList`.  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 Önceki örnekte, yazıldığı aşağıdaki koda eşdeğerdir [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] söz dizimi:  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable>
- [Lambda İfadeleri](./lambda-expressions.md)
- [Function Deyimi](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub Deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Nasıl yapılır: Visual Basic'de başka bir yordama yordam geçirin](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Delegate Deyimi](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
