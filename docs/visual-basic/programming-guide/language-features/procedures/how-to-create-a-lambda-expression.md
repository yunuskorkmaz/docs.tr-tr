---
title: 'Nasıl yapılır: Lambda İfadesi Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: 7affc84fa501ba98bdfa93835f0b0e381580b9bd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388393"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a>Nasıl yapılır: Lambda İfadesi Oluşturma (Visual Basic)
*Lambda ifadesi* , adı olmayan bir işlev veya alt yordam. Bir lambda ifadesi, bir temsilci türünün geçerli olduğu her yerde kullanılabilir.  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a>Tek satırlık lambda ifadesi işlevi oluşturmak için  
  
1. Temsilci türünün kullanılabileceği herhangi bir durumda, `Function` Aşağıdaki örnekte olduğu gibi anahtar sözcüğünü yazın:  
  
     `Dim add1 =`   `Function`  
  
2. Parantez içinde doğrudan sonra, `Function` işlevin parametrelerini yazın. Sonrasında bir ad belirtmediğine dikkat edin `Function` .  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3. Parametre listesini izleyerek işlevin gövdesi olarak tek bir ifade yazın. İfadenin değerlendirme değeri, işlev tarafından döndürülen değerdir. `As`Dönüş türünü belirtmek için bir yan tümce kullanmayın.  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     Bir tamsayı bağımsız değişkeni geçirerek lambda ifadesini çağırabilirsiniz.  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. Alternatif olarak, aynı sonuç aşağıdaki örnek tarafından gerçekleştirilir:  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a>Tek satırlık lambda ifadesi alt yordamı oluşturmak için  
  
1. Temsilci türünün kullanılabileceği herhangi bir durumda, `Sub` Aşağıdaki örnekte gösterildiği gibi anahtar sözcüğünü yazın.  
  
     `Dim add1 =`   `Sub`  
  
2. Parantez içinde doğrudan sonrasında `Sub` , alt yordamın parametrelerini yazın. Sonrasında bir ad belirtmediğine dikkat edin `Sub` .  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3. Parametre listesini takip eden alt yordamın gövdesi olarak tek bir ifade yazın.  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     Bir dize bağımsız değişkenine geçirerek lambda ifadesini çağırabilirsiniz.  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a>Çok satırlı lambda ifadesi işlevi oluşturmak için  
  
1. Temsilci türünün kullanılabileceği herhangi bir durumda, `Function` Aşağıdaki örnekte gösterildiği gibi anahtar sözcüğünü yazın.  
  
     `Dim add1 =`   `Function`  
  
2. Parantez içinde doğrudan sonra, `Function` işlevin parametrelerini yazın. Sonrasında bir ad belirtmediğine dikkat edin `Function` .  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3. ENTER tuşuna basın. `End Function`Ekstre otomatik olarak eklenir.  
  
4. İşlevin gövdesinde, bir ifade oluşturmak ve değeri döndürmek için aşağıdaki kodu ekleyin. `As`Dönüş türünü belirtmek için bir yan tümce kullanmayın.  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     Bir tamsayı bağımsız değişkeni geçirerek lambda ifadesini çağırabilirsiniz.  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a>Çok satırlı lambda ifadesi alt yordamı oluşturmak için  
  
1. Temsilci türünün kullanılabileceği herhangi bir durumda, `Sub` Aşağıdaki örnekte gösterildiği gibi anahtar sözcüğünü yazın:  
  
     `Dim add1 =`   `Sub`  
  
2. Parantez içinde doğrudan sonrasında `Sub` , alt yordamın parametrelerini yazın. Sonrasında bir ad belirtmediğine dikkat edin `Sub` .  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3. ENTER tuşuna basın. `End Sub`Ekstre otomatik olarak eklenir.  
  
4. İşlevin gövdesinde, alt yordam çağrıldığında yürütülecek aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     Bir dize bağımsız değişkenine geçirerek lambda ifadesini çağırabilirsiniz.  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a>Örnek  
 Lambda ifadelerinin yaygın kullanımı, türü olan bir parametre için bağımsız değişken olarak geçirilebilecek bir işlev tanımlamaktır `Delegate` . Aşağıdaki örnekte, <xref:System.Diagnostics.Process.GetProcesses%2A> yöntemi yerel bilgisayarda çalışan işlemlerin dizisini döndürür. <xref:System.Linq.Enumerable.Where%2A>Sınıfından yöntemi, <xref:System.Linq.Enumerable> `Boolean` bağımsız değişkeni olarak bir temsilci gerektirir. Örnekteki lambda ifadesi bu amaçla kullanılır. `True`Yalnızca bir iş parçacığına sahip olan ve ' de seçili olan her işlem için döndürür `filteredList` .  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 Önceki örnek, dil ile tümleşik sorgu (LINQ) sözdiziminde yazılan aşağıdaki koda eşdeğerdir:  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable>
- [Lambda Ifadeleri](./lambda-expressions.md)
- [Function Deyimi](../../../language-reference/statements/function-statement.md)
- [Sub Deyimi](../../../language-reference/statements/sub-statement.md)
- [Temsilciler](../delegates/index.md)
- [Nasıl yapılır: Visual Basic'de Başka Bir Yordama Yordam Geçirme](../delegates/how-to-pass-procedures-to-another-procedure.md)
- [Delegate Deyimi](../../../language-reference/statements/delegate-statement.md)
- [Visual Basic'de LINQ'e Giriş](../linq/introduction-to-linq.md)
