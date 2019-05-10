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
ms.openlocfilehash: 5e59b0284ad1c05c16c33d520bc4c223e6ddace1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623245"
---
# <a name="lambda-expressions-visual-basic"></a>Lambda İfadeleri (Visual Basic)
A *lambda ifadesi* bir işlevi veya alt yordam bir temsilci geçerli olduğu yerlerde kullanılabilmesi için bir ad olmadan. Lambda ifadeleri, işlev veya alt yordamlar olabilir ve tek satır veya çok satırlı olabilir. Bir lambda ifadesi olan geçerli kapsamını değer geçirebilirsiniz.  
  
> [!NOTE]
>  `RemoveHandler` Deyimi, bir özel durum. Temsilci parametresi için bir lambda ifadesinde geçirilemez `RemoveHandler`.  
  
 Lambda ifadeleri kullanarak oluşturduğunuz `Function` veya `Sub` anahtar sözcüğü, bir standart işlevi veya alt yordamlar oluşturma gibi. Ancak, lambda ifadeleri bir deyimde dahil edilir.  
  
 Aşağıdaki örnek bağımsız değişkeni artırır ve değer döndüren bir lambda ifadesidir. Bu örnek, hem tek satır ve çok satırlı lambda ifadesi söz dizimi işlevi için gösterir.  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
 Aşağıdaki örnek bir değer konsola bir lambda ifadesidir. Bu örnek, hem tek satır ve çok satırlı lambda ifadesi sözdizimi bir alt yordam gösterir.  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
 Önceki örneklerde bir değişken lambda ifadeleri atanmış olduğuna dikkat edin. Değişkenine başvuruda bulunduğunuzda, lambda ifadesini çağırmak. Bildirme ve aşağıdaki örnekte gösterildiği gibi aynı zamanda bir lambda ifadesini çağırmak.  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
 Bir lambda ifadesi bir işlev çağrısı değeri olarak döndürülebilir (örnekte gösterildiği gibi [bağlam](#context) bu konunun ilerleyen bölümlerinde), veya bağımsız değişken olarak bir temsilci türü alan parametresi aşağıda gösterildiği gibi geçirilen örnek.  
  
 [!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]  
  
## <a name="lambda-expression-syntax"></a>Lambda İfadesi Sözdizimi  
 Bir lambda ifadesi sözdizimi standart işlevi veya alt yordam benzer. Farklar aşağıdaki gibidir:  
  
- Bir lambda ifadesi, bir adı yok.  
  
- Lambda ifadeleri içeremez değiştiriciler, gibi `Overloads` veya `Overrides`.  
  
- Tek satırlı lambda işlevleri kullanmayın bir `As` dönüş türü belirtmek için yan tümcesi. Bunun yerine, tür lambda ifadesinin gövdesinin değerlendiren değerinden algılanır. Örneğin, lambda ifadesinin gövdesinin ise `cust.City = "London"`, kendi dönüş türü `Boolean`.  
  
- Çok satırlı lambda işlevleri'nde ya da dönüş türü kullanarak belirtebilirsiniz bir `As` yan tümcesi veya çıkarın `As` yan tümcesi böylece dönüş türü algılanır. Zaman `As` çok satırlı lambda işlevi için yan tümcesi atlanırsa, dönüş türü çıkarımı yapılan tüm baskın türü `Return` deyimleri çok satırlı lambda işlevi içinde. *Baskın tür* için diğer tüm türlerin genişleyebileceği benzersiz bir türüdür. Bu benzersiz tür belirlenemiyorsa, baskın tür, dizideki diğer tüm türler için daraltabilirsiniz benzersiz türüdür. Bu benzersiz türlerden hiçbiri belirlenemezse, baskın türdür `Object`. Bu durumda, `Option Strict` ayarlanır `On`, bir derleyici hatası oluşur.  
  
     Örneğin, sağlanan ifadeleri `Return` deyim türü değerleri içeren `Integer`, `Long`, ve `Double`, ortaya çıkan dizi türünde `Double`. Her ikisi de `Integer` ve `Long` genişletmek için `Double` ve yalnızca `Double`. Bu nedenle, `Double` baskın türdür. Daha fazla bilgi için [Widening ve daraltma dönüşümleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
- Tek satırlı bir işlev gövdesini deyim olmayan bir değer döndüren bir ifade olmalıdır. Var olan hiçbir `Return` tek satırlı işlevleri için bildirimi. Tek satırlı işlevi tarafından döndürülen değer işlev gövdesi içindeki ifade bir değerdir.  
  
- Tek satır alt yordam gövdesi tek satır deyim olmalıdır.  
  
- Tek satırlı işlevleri ve alt yordamlar içermez bir `End Function` veya `End Sub` deyimi.  
  
- Bir lambda ifadesi parametre veri türü kullanarak belirtebilirsiniz `As` anahtar sözcük veya parametresinin veri türü nelze odvodit. Tüm parametre ya da veri türleri veya tüm anlaşılmalıdır belirtilmelidir.  
  
- `Optional` ve `Paramarray` parametreleri izin verilmez.  
  
- Genel Parametreler izin verilmez.  
  
## <a name="async-lambdas"></a>Zaman Uyumsuz Lambdalar  
 İçeren kullanarak zaman uyumsuz işleme içeren lambda ifadeleri ve deyimlerini kolayca oluşturabilirsiniz [zaman uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md) ve [Await işleci](../../../../visual-basic/language-reference/operators/await-operator.md) anahtar sözcükleri. Örneğin, aşağıdaki Windows Forms örneği, çağıran ve bekleyen zaman uyumsuz bir yöntem, bir olay işleyici içerir `ExampleMethodAsync`.  
  
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
  
 İçinde zaman uyumsuz lambda kullanarak aynı olay işleyicisini ekleyebilirsiniz bir [AddHandler deyimi](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Bu işleyiciyi eklemek için Ekle bir `Async` aşağıdaki örnekte göründüğü gibi lambda parametre listesinden önce değiştiricisi.  
  
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
  
 Oluşturma ve zaman uyumsuz yöntemler kullanma hakkında daha fazla bilgi için bkz. [Async ve Await ile zaman uyumsuz programlama](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
## <a name="context"></a> Bağlam  
 Bir lambda ifadesi, kendi bağlam içinde tanımlandığı kapsamıyla paylaşır. Bu, kapsayan kapsam içinde yazılan herhangi bir kod aynı erişim haklarına sahiptir. Bu üye değişkenleri, işlevleri ve alt öğeler, erişimi içerir `Me`, parametreleri ve kapsayan kapsamda yerel değişkenlere ve.  
  
 Yerel değişkenler ve parametreler kapsayan kapsamda erişim, kapsamı ömründen uzun genişletebilirsiniz. Bir lambda ifadesi başvuran bir temsilci çöp toplama için kullanılabilir olmayan sürece özgün ortam değişkenlerine erişimi korunur. Aşağıdaki örnekte, değişken `target` için yerel `makeTheGame`, yöntem, lambda ifadesi `playTheGame` tanımlanır. Döndürülen lambda ifadesi, atanan Not `takeAGuess` içinde `Main`, hala yerel değişkene erişimi vardır `target`.  
  
 [!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]  
  
 Aşağıdaki örnek, çeşitli iç içe geçmiş lambda ifadesinin erişim haklarını gösterir. Ne zaman döndürülen lambda ifadesi yürütülmediyse `Main` olarak `aDel`, bu öğeleri erişir:  
  
- İçinde tanımlandığı sınıfının bir alanı: `aField`  
  
- İçinde tanımlandığı sınıfın bir özelliği: `aProp`  
  
- Yönteminin bir parametresi `functionWithNestedLambda`, içinde tanımlandığı: `level1`  
  
- Bir yerel değişken `functionWithNestedLambda`: `localVar`  
  
- Yer alan bir lambda ifadesi parametre: `level2`  
  
 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]  
  
## <a name="converting-to-a-delegate-type"></a>Bir temsilci türüne dönüştürme  
 Bir lambda ifadesi bir uyumlu temsilci türüne örtük olarak dönüştürülebilir. Uyumluluk için genel gereksinimler hakkında daha fazla bilgi için bkz. [gevşek temsilci dönüşümü](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md). Örneğin, aşağıdaki kod örneği dönüştürür örtük olarak bir lambda ifadesi gösterir `Func(Of Integer, Boolean)` veya eşleşen bir temsilci imzası.  
  
 [!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]  
  
 Aşağıdaki kod örneği için örtük olarak dönüştüren bir lambda ifadesi gösterir `Sub(Of Double, String, Double)` veya eşleşen bir temsilci imzası.  
  
 [!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]  
  
 Lambda ifadeleri için temsilci atama ya da yordamlar için bağımsız değişken olarak geçirileceğini parametre adları belirtin ama temsilciden alınması türlerine izin vererek veri türlerini atlayın.  
  
## <a name="examples"></a>Örnekler  
  
- Aşağıdaki örnek döndüren bir lambda ifadesi tanımlar `True` bağımsız değişkeni boş değer atanabilir bir atanan değer varsa ve `False` değerini ise `Nothing`.  
  
     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]  
  
- Aşağıdaki örnek, bir dizi içinde son öğenin dizinini döndüren bir lambda ifadesi tanımlar.  
  
     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Function Deyimi](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub Deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Boş Değer Atanabilen Değer Türleri](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Nasıl yapılır: Visual Basic'de başka bir yordama yordam geçirin](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Nasıl yapılır: Lambda ifadesi oluşturma](./how-to-create-a-lambda-expression.md)
- [Gevşek Temsilci Dönüştürme](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
