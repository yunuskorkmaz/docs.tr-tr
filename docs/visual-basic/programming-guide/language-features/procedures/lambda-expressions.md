---
title: Lambda İfadeleri
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: 1827eb5630ed217527de25fc9d9c2bb8994b9aff
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249675"
---
# <a name="lambda-expressions-visual-basic"></a>Lambda İfadeleri (Visual Basic)

*Lambda ifadesi,* temsilcinin geçerli olduğu her yerde kullanılabilecek bir ad olmayan bir işlev veya alt yordamdır. Lambda ifadeleri işlevler veya alt yordamlar olabilir ve tek satırlı veya çok satırlı olabilir. Değerleri geçerli kapsamdan lambda ifadesine geçirebilirsiniz.

> [!NOTE]
> İfade `RemoveHandler` bir istisnadır. `RemoveHandler`'nin temsilci parametresi için lambda ifadesini geçemezsiniz.

Standart bir işlev veya `Function` `Sub` alt yordam oluşturduğunuz gibi, lambda ifadelerini de standart bir işlev veya alt yordam oluşturduğunuz gibi, anahtar kelimeyi kullanarak lambda ifadeleri oluşturursunuz. Ancak, lambda ifadeler bir açıklamada yer alıyor.

Aşağıdaki örnek, bağımsız değişkenini artan ve değeri döndüren bir lambda ifadesidir. Örnek, bir işlev için hem tek satırlı hem de çok satırlı lambda ifade sözdizimini gösterir.

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

Aşağıdaki örnek, konsola bir değer yazan bir lambda ifadesidir. Örnek, bir alt yordam için hem tek satırlı hem de çok satırlı lambda ifade sözdizimini gösterir.

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

Önceki örneklerde lambda ifadelerinin değişken bir ada atandığını unutmayın. Değişkene her başvuruyaptığınızda, lambda ifadesini çağırırsınız. Ayrıca, aşağıdaki örnekte gösterildiği gibi, aynı anda bir lambda ifadesini beyan edebilir ve çağırabilirsiniz.

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

Lambda ifadesi işlev çağrısının değeri olarak döndürülebilir (bu konunun ilerleyen bölümünde [Bağlam](#context) bölümünde gösterildiği gibi) veya aşağıdaki örnekte gösterildiği gibi, temsilci türünü alan bir parametreye bağımsız değişken olarak geçirilebilir.

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a>Lambda İfadesi Sözdizimi

Lambda ifadesinin sözdizimi standart bir işlevin veya alt yordamınkine benzer. Farklar şunlardır:

- Lambda ifadesinin bir adı yoktur.

- Lambda ifadeleri gibi `Overloads` değiştiriciler olamaz, `Overrides`ya da .

- Tek satırlı lambda işlevleri, `As` dönüş türünü belirlemek için bir yan tümce kullanmaz. Bunun yerine, tür lambda ifadesinin gövdesinin değerlendirdığı değerden çıkarılır. Örneğin, lambda ifadesinin gövdesi `cust.City = "London"`ise, dönüş türü `Boolean`.

- Çok satırlı lambda işlevlerinde, bir yan tümce `As` kullanarak bir iade `As` türü belirtebilir veya iade türünün çıkarılaması için yan tümceyi atlayabilirsiniz. Çok `As` satırlı lambda işlevi için yan tümce atlandığında, dönüş türü çok satırlı lambda işlevindeki tüm `Return` ifadelerden baskın tür olarak çıkarılır. *Baskın türü,* diğer tüm türlerin genişletebileceği benzersiz bir türdür. Bu benzersiz tür belirlenemiyorsa, baskın tür dizideki tüm diğer türlerin daraltabileceği benzersiz türüdür. Bu benzersiz türlerden hiçbiri belirlenemezse, `Object`baskın tür . Bu durumda, `Option Strict` olarak ayarlanırsa, `On`bir derleyici hatası oluşur.

     Örneğin, `Return` deyime verilen ifadeler , `Integer`, , `Long`ve `Double`, ortaya çıkan dizi değerleri `Double`içeriyorsa. Hem `Integer` `Long` genişletmek `Double` ve sadece `Double`. Bu `Double` nedenle, baskın türüdür. Daha fazla bilgi için [Dönüşümleri Genişletme ve Daraltma'ya](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)bakın.

- Tek satırlı bir işlevin gövdesi, bir ifade değil, bir değer döndüren bir ifade olmalıdır. Tek satırlı işlevler için ifade yok. `Return` Tek satırlı işlev tarafından döndürülen değer, işlevin gövdesindeki ifadenin değeridir.

- Tek satırlı bir alt yordamın gövdesi tek satırlı ifade olmalıdır.

- Tek satırlı işlevler ve alt `End Function` yordamlar bir veya `End Sub` deyim içermez.

- Bir lambda ifade parametresinin veri türünü `As` anahtar sözcüğü kullanarak belirtebilirsiniz veya parametrenin veri türü çıkarılabilir. Tüm parametrelerin belirtilen veri türleri olmalı veya tüm bunlar çıkarılmalıdır.

- `Optional`ve `Paramarray` parametrelere izin verilmez.

- Genel parametrelere izin verilmez.

## <a name="async-lambdas"></a>Zaman Uyumsuz Lambdalar

[Async](../../../../visual-basic/language-reference/modifiers/async.md) ve [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) anahtar kelimelerini kullanarak asynchronous işlemeiçeren lambda ifadeleri ve deyimleri kolayca oluşturabilirsiniz. Örneğin, aşağıdaki Windows Forms örneği çağıran ve bir async yöntemi ni `ExampleMethodAsync`bekleyen bir olay işleyicisi içerir.

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

[AddHandler Deyimi'nde](../../../../visual-basic/language-reference/statements/addhandler-statement.md)bir async lambda kullanarak aynı olay işleyicisi ekleyebilirsiniz. Bu işleyiciyi eklemek `Async` için, aşağıdaki örnekte görüldüğü gibi lambda parametre listesinden önce bir değiştirici ekleyin.

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

Async yöntemlerinin nasıl oluşturulup kullanılacağı hakkında daha fazla bilgi için [Async ve Await ile Asynchronous Programming'e](../../../../visual-basic/programming-guide/concepts/async/index.md)bakın.

## <a name="context"></a>Bağlam

Bir lambda ifadesi, bağlamını tanımlandığı kapsamla paylaşır. Bu kapsamda yazılmış herhangi bir kod olarak aynı erişim haklarına sahiptir. Bu, üye değişkenlere, işlevlere ve `Me`alt lara, parametrelere ve yerel değişkenlere erişimi içerir.

İçerdeki kapsamdaki yerel değişkenlere ve parametrelere erişim, bu kapsamın ömrünün ötesine uzanabilir. Çöp toplama için lambda ifadesine atıfta bulunan bir temsilci kullanılamadığı sürece, özgün ortamdaki değişkenlere erişim korunur. Aşağıdaki örnekte, `target` değişken , `makeTheGame`lambda ifade `playTheGame` tanımlanan yöntem için yereldir. Döndürülen lambda ifadesinin, `takeAGuess` yerel `Main`değişkene `target`hala erişebilen bir ifadeolduğunu unutmayın.

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

Aşağıdaki örnek, iç içe lambda ifadesinin geniş erişim haklarını göstermektedir. Döndürülen lambda ifadesi `Main` şu `aDel`şekilde yürütüldüğünde, şu unsurlara erişir:

- Tanımlandığı sınıfın bir alanı:`aField`

- Tanımlandığı sınıfın özelliği:`aProp`

- Yöntemin bir `functionWithNestedLambda`parametresi , hangi tanımlanır:`level1`

- Yerel bir `functionWithNestedLambda`değişken:`localVar`

- İç içe olduğu lambda ifadesinin bir parametresi:`level2`

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a>Temsilci Türüne Dönüştürme

Lambda ifadesi örtülü olarak uyumlu bir temsilci türüne dönüştürülebilir. Uyumluluk için genel gereksinimler hakkında bilgi için [bkz.](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md) Örneğin, aşağıdaki kod örneği, örtülü olarak veya eşleşen `Func(Of Integer, Boolean)` bir temsilci imzasına dönüştüren bir lambda ifadesini gösterir.

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

Aşağıdaki kod örneği, örtülü olarak veya eşleşen `Sub(Of Double, String, Double)` bir temsilci imzasına dönüştüren bir lambda ifadesini gösterir.

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

Lambda ifadelerini temsilcilere atadığınızda veya bunları yordamlara bağımsız değişken olarak aktardığınızda, parametre adlarını belirtebilirsiniz, ancak veri türlerini atlayarak türlerin inden alınmasına izin verebilirsiniz.

## <a name="examples"></a>Örnekler

- Aşağıdaki örnekte, nullable değer `True` türü bağımsız değişkeninin atanmış bir değeri `False` varsa ve `Nothing`değeri .

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- Aşağıdaki örnek, bir dizideki son öğenin dizinini döndüren bir lambda ifadesini tanımlar.

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Visual Basic'de LINQ'e Giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Fonksiyon Bildirimi](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub Deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Boş Değer Atanabilen Değer Türleri](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Nasıl yapılır: Visual Basic'de Başka Bir Yordama Yordam Geçirme](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Nasıl yapılır: Lambda İfadesi Oluşturma](./how-to-create-a-lambda-expression.md)
- [Gevşek Temsilci Dönüştürme](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
