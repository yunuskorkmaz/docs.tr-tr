---
title: 'Nasıl yapılır: Lambda İfadesi Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: bb0bdb3c10a7df2ca954fbdb9382a25bf805068d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349751"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a>Nasıl yapılır: Lambda İfadesi Oluşturma (Visual Basic)
*Lambda ifadesi* , adı olmayan bir işlev veya alt yordam. Bir lambda ifadesi, bir temsilci türünün geçerli olduğu her yerde kullanılabilir.  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a>Tek satırlık lambda ifadesi işlevi oluşturmak için  
  
1. Temsilci türünün kullanılabileceği herhangi bir durumda, aşağıdaki örnekte olduğu gibi `Function`anahtar sözcüğünü yazın:  
  
     `Dim add1 =`   `Function`  
  
2. Parantez içinde, `Function`doğrudan sonra, işlevin parametrelerini yazın. `Function`sonra bir ad belirtmediğine dikkat edin.  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3. Parametre listesini izleyerek işlevin gövdesi olarak tek bir ifade yazın. İfadenin değerlendirme değeri, işlev tarafından döndürülen değerdir. Dönüş türünü belirtmek için bir `As` yan tümcesi kullanmayın.  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     Bir tamsayı bağımsız değişkeni geçirerek lambda ifadesini çağırabilirsiniz.  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. Alternatif olarak, aynı sonuç aşağıdaki örnek tarafından gerçekleştirilir:  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a>Tek satırlık lambda ifadesi alt yordamı oluşturmak için  
  
1. Temsilci türünün kullanılabileceği herhangi bir durumda, aşağıdaki örnekte gösterildiği gibi `Sub`anahtar sözcüğünü yazın.  
  
     `Dim add1 =`   `Sub`  
  
2. Parantez içinde, `Sub`doğrudan sonrasında, alt yordamın parametrelerini yazın. `Sub`sonra bir ad belirtmediğine dikkat edin.  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3. Parametre listesini takip eden alt yordamın gövdesi olarak tek bir ifade yazın.  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     Bir dize bağımsız değişkenine geçirerek lambda ifadesini çağırabilirsiniz.  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a>Çok satırlı lambda ifadesi işlevi oluşturmak için  
  
1. Temsilci türünün kullanılabileceği herhangi bir durumda, aşağıdaki örnekte gösterildiği gibi `Function`anahtar sözcüğünü yazın.  
  
     `Dim add1 =`   `Function`  
  
2. Parantez içinde, `Function`doğrudan sonra, işlevin parametrelerini yazın. `Function`sonra bir ad belirtmediğine dikkat edin.  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3. ENTER tuşuna basın. `End Function` deyimleri otomatik olarak eklenir.  
  
4. İşlevin gövdesinde, bir ifade oluşturmak ve değeri döndürmek için aşağıdaki kodu ekleyin. Dönüş türünü belirtmek için bir `As` yan tümcesi kullanmayın.  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     Bir tamsayı bağımsız değişkeni geçirerek lambda ifadesini çağırabilirsiniz.  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a>Çok satırlı lambda ifadesi alt yordamı oluşturmak için  
  
1. Temsilci türünün kullanılabileceği herhangi bir durumda, aşağıdaki örnekte gösterildiği gibi `Sub`anahtar sözcüğünü yazın:  
  
     `Dim add1 =`   `Sub`  
  
2. Parantez içinde, `Sub`doğrudan sonrasında, alt yordamın parametrelerini yazın. `Sub`sonra bir ad belirtmediğine dikkat edin.  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3. ENTER tuşuna basın. `End Sub` deyimleri otomatik olarak eklenir.  
  
4. İşlevin gövdesinde, alt yordam çağrıldığında yürütülecek aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     Bir dize bağımsız değişkenine geçirerek lambda ifadesini çağırabilirsiniz.  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a>Örnek  
 Lambda ifadelerinin yaygın kullanımı, türü `Delegate`olan bir parametre için bağımsız değişken olarak geçirilebilecek bir işlev tanımlamaktır. Aşağıdaki örnekte <xref:System.Diagnostics.Process.GetProcesses%2A> yöntemi, yerel bilgisayarda çalışan işlemlerin dizisini döndürür. <xref:System.Linq.Enumerable> sınıfındaki <xref:System.Linq.Enumerable.Where%2A> yöntemi bağımsız değişkeni olarak bir `Boolean` temsilcisi gerektirir. Örnekteki lambda ifadesi bu amaçla kullanılır. Yalnızca bir iş parçacığına sahip olan her işlem için `True` döndürür ve bunlar `filteredList`seçilir.  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 Önceki örnek, [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] sözdiziminde yazılan aşağıdaki koda eşdeğerdir:  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable>
- [Lambda İfadeleri](./lambda-expressions.md)
- [Function Deyimi](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub Deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Nasıl yapılır: yordamları Visual Basic başka bir yordama geçirme](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Delegate Deyimi](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Visual Basic LINQ 'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
