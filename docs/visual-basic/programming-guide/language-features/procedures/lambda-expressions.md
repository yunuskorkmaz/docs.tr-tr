---
title: Lambda İfadeleri (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: c45500dc7a1e59a7ac83d43b826ca4cbfca6efb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="lambda-expressions-visual-basic"></a>Lambda İfadeleri (Visual Basic)
A *lambda ifadesi* bir işlevi veya alt yordama bir temsilci geçerli olduğu yerlerde, kullanılabilecek bir ad olmadan. Lambda ifadeleri işlevleri veya alt yordamlar olabilir ve tek satırlı veya çok satırlı olabilir. Değerleri bir lambda ifadesi geçerli kapsamdan geçirebilirsiniz.  
  
> [!NOTE]
>  `RemoveHandler` Açıklamadır bir özel durum. Temsilci parametresi için bir lambda ifadesinde geçiremezsiniz `RemoveHandler`.  
  
 Lambda ifadeleri kullanarak oluşturduğunuz `Function` veya `Sub` anahtar sözcüğü, standart işlev veya alt yordama oluşturmak gibi. Ancak, lambda ifadeleri bir deyimde dahil edilir.  
  
 Aşağıdaki örnek, bağımsız değişkeni artırır ve değer döndüren bir lambda ifadesi ' dir. Aşağıdaki örnekte, hem tek satırlı ve çok satırlı lambda ifadesi sözdizimi işlevi için gösterilir.  
  
 [!code-vb[VbVbalrLambdas#14](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]  
  
 Aşağıdaki örnek bir değer konsola bir lambda ifadesi ' dir. Aşağıdaki örnekte, hem tek satırlı ve çok satırlı lambda ifadesi sözdizimi alt yordam için gösterilir.  
  
 [!code-vb[VbVbalrLambdas#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]  
  
 Önceki örneklerde bir değişken adı lambda ifadeleri atandığını dikkat edin. Değişkene başvurduğunuzda lambda ifadesi çağırır. Bildirme ve aşağıdaki örnekte gösterildiği gibi bir lambda ifadesi aynı anda çağırma.  
  
 [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]  
  
 Lambda ifadesi bir işlev çağrısı değeri olarak döndürülebilecek (örnekte gösterildiği gibi [bağlamı](#context) bu konunun ilerleyen bölümlerinde), veya bir bağımsız değişken bir temsilci türü alan parametresi aşağıda gösterildiği gibi geçirildi örnek.  
  
 [!code-vb[VbVbalrLambdas#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]  
  
## <a name="lambda-expression-syntax"></a>Lambda İfadesi Sözdizimi  
 Lambda ifadesi sözdizimi, standart işlev veya alt yordama benzer. Farkları aşağıdaki gibidir:  
  
-   Lambda ifadesi bir adı yok.  
  
-   Lambda ifadeleri olamaz değiştiriciler, gibi `Overloads` veya `Overrides`.  
  
-   Tek satırlı lambda işlevleri kullanmayın bir `As` dönüş türü atamak yan tümcesi. Bunun yerine, türü lambda ifadesi gövdesi değerlendiren değerinden algılanır. Örneğin, lambda ifadesi gövdesi ise `cust.City = "London"`, kendi dönüş türü `Boolean`.  
  
-   Çok satırlı lambda işlevlerde ya da bir dönüş türü kullanarak belirleyebileceğiniz bir `As` yan tümcesi veya çıkarın `As` yan tümcesi dönüş türü çıkarımı yapılan böylece. Zaman `As` yan tümcesi için çok satırlı lambda işlevi atlanırsa, dönüş türü tüm baskın türü çıkarımı yapılan `Return` çok satırlı lambda işlevi deyimlerinde. *Baskın türü* tüm diğer türleri için genişletebilirsiniz benzersiz bir türüdür. Bu benzersiz türü belirlenemiyorsa baskın dizisindeki tüm diğer türleri için daraltabilirsiniz benzersiz türü türüdür. Bu benzersiz türlerinden hiçbiri belirlenebilir baskın türü varsa, `Object`. Bu durumda, `Option Strict` ayarlanır `On`, bir derleyici hatası oluşur.  
  
     Örneğin, ifadeler için sağlanan `Return` deyimi türü değerleri içeren `Integer`, `Long`, ve `Double`, sonuç dizisi türünde `Double`. Her ikisi de `Integer` ve `Long` için genişletmek `Double` ve yalnızca `Double`. Bu nedenle, `Double` baskın türüdür. Daha fazla bilgi için bkz: [Widening ve daraltma dönüşümleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
-   Tek satırlı işlevinin gövdesini bir deyim bir değer döndüren bir ifade olması gerekir. Var olan hiçbir `Return` tek satırlı işlevler için deyimi. Tek satırlı işlevi tarafından döndürülen değeri işlevinin gövdesini ifadesinde değeridir.  
  
-   Tek satırlı alt yordama gövdesi tek satırlı deyim olmalıdır.  
  
-   Tek satırlı işlevler ve alt yordamlar içermeyen bir `End Function` veya `End Sub` deyimi.  
  
-   Kullanarak bir lambda ifadesi parametresinin veri türü belirtebilirsiniz `As` anahtar sözcüğü ya da parametresinin veri türü sonuçlandı. Veri türleri veya tüm olayla gerekir ya da tüm parametreleri belirledikten gerekir.  
  
-   `Optional` ve `Paramarray` parametreleri izin verilmez.  
  
-   Genel Parametreler izin verilmez.  
  
## <a name="async-lambdas"></a>Zaman Uyumsuz Lambdalar  
 Lambda ifadeleri ve kullanarak zaman uyumsuz işleme dahil deyimleri kolayca oluşturabilirsiniz [zaman uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md) ve [Await işleci](../../../../visual-basic/language-reference/operators/await-operator.md) anahtar sözcükler. Örneğin, aşağıdaki Windows Forms örnek çağırır ve bir zaman uyumsuz yöntem bekler bir olay işleyiciyi içeriyor `ExampleMethodAsync`.  
  
```vb  
Public Class Form1  
  
    Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' ExampleMethodAsync returns a Task.  
        Await ExampleMethodAsync()  
        TextBox1.Text = vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 Bir zaman uyumsuz lambda kullanarak aynı olay işleyicisi ekleyebilirsiniz bir [AddHandler deyimi](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Bu işleyici eklemek için Ekle bir `Async` lambda parametre listesi, aşağıdaki örnekte gösterildiği gibi önce değiştiricisi.  
  
```vb  
Public Class Form1  
  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
        AddHandler Button1.Click,   
            Async Sub(sender1, e1)  
                ' ExampleMethodAsync returns a Task.  
                Await ExampleMethodAsync()  
                TextBox1.Text = vbCrLf & "Control returned to Button1_ Click."  
            End Sub  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 Oluşturma ve zaman uyumsuz yöntemler kullanma hakkında daha fazla bilgi için bkz: [uyumsuz ve bekleme ile zaman uyumsuz programlama](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
##  <a name="context"></a> bağlam  
 Lambda ifadesi ile bağlamı içinde tanımlanan kapsamıyla paylaşır. İçeren kapsamı içinde yazılmış herhangi bir kod aynı erişim haklarına sahiptir. Üye değişkenleri, işlevleri ve alt öğeler, erişim dahildir `Me`, parametreleri ve içeren kapsamdaki yerel değişkenleri ve.  
  
 Yerel değişkenleri ve parametreleri içeren kapsamında erişim, kapsamı ömür genişletebilirsiniz. Lambda ifadesi olarak başvuran bir temsilci çöp toplama kullanılamaz olduğu sürece, özgün ortam değişkenlerine erişim korunur. Aşağıdaki örnekte, değişken `target` için yerel olan `makeTheGame`, yönteminde lambda ifadesi `playTheGame` tanımlanır. Döndürülen lambda ifadesi atanan Not `takeAGuess` içinde `Main`, hala yerel değişken erişimi `target`.  
  
 [!code-vb[VbVbalrLambdas#12](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]  
  
 Aşağıdaki örnek, çeşitli iç içe geçmiş lambda ifadesi erişim haklarını gösterir. Ne zaman döndürülen lambda ifadesi yürütüldüğünde gelen `Main` olarak `aDel`, bu öğeler erişen:  
  
-   İçinde tanımlandığı sınıfının bir alanı: `aField`  
  
-   İçinde tanımlandığı sınıfın özelliği: `aProp`  
  
-   Yönteminin bir parametresi `functionWithNestedLambda`, tanımlandığı içinde: `level1`  
  
-   Yerel bir değişken `functionWithNestedLambda`: `localVar`  
  
-   Yer alan lambda ifadesi parametresinin: `level2`  
  
 [!code-vb[VbVbalrLambdas#9](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]  
  
## <a name="converting-to-a-delegate-type"></a>Bir temsilci türüne dönüştürme  
 Lambda ifadesi bir uyumlu temsilci türü örtük olarak dönüştürülebilir. Uyumluluk için genel gereksinimler hakkında daha fazla bilgi için bkz: [gevşek temsilci dönüşümü](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md). Örneğin, aşağıdaki kod örneğinde örtük olarak dönüştürür bir lambda ifadesi gösterilir `Func(Of Integer, Boolean)` veya eşleşen bir temsilci imzası.  
  
 [!code-vb[VbVbalrLambdas#16](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]  
  
 Aşağıdaki kod örneğinde örtük olarak dönüştürür bir lambda ifadesi gösterilir `Sub(Of Double, String, Double)` veya eşleşen bir temsilci imzası.  
  
 [!code-vb[VbVbalrLambdas#23](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]  
  
 Lambda ifadeleri temsilcileri atayın ya da bunları yordamları bağımsız değişken olarak geçirmek parametre adları belirtin ama temsilciden alınması türleri izin vererek kendi veri türleri atlayın.  
  
## <a name="examples"></a>Örnekler  
  
-   Aşağıdaki örnek döndüren bir lambda ifadesi tanımlar `True` boş değer atanabilir bağımsız değişkeni atanan bir değeri varsa ve `False` değerini ise `Nothing`.  
  
     [!code-vb[VbVbalrLambdas#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]  
  
-   Aşağıdaki örnek, bir dizi son öğenin dizinini döndürür bir lambda ifadesi tanımlar.  
  
     [!code-vb[VbVbalrLambdas#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](./index.md)  
 [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Function Deyimi](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub Deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Boş Değer Atanabilen Değer Türleri](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Nasıl yapılır: Visual Basic'de başka bir yordama yordam geçirme](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [Nasıl yapılır: Lambda İfadesi Oluşturma](./how-to-create-a-lambda-expression.md)  
 [Gevşek Temsilci Dönüştürme](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
