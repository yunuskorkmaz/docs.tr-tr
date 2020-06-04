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
ms.openlocfilehash: 54a9c0cf275a67c77748c32771c3c5dcbdb916d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406709"
---
# <a name="lambda-expressions-visual-basic"></a>Lambda İfadeleri (Visual Basic)

*Lambda ifadesi* , bir temsilcinin geçerli olduğu her yerde kullanılabilecek bir ada sahip olmayan bir işlev veya alt yordam 'dir. Lambda ifadeleri işlevler veya alt yordamlar olabilir ve tek satırlık veya çok satırlı olabilir. Geçerli kapsamdan bir lambda ifadesine değer geçirebilirsiniz.

> [!NOTE]
> `RemoveHandler`İfade bir özel durumdur. Temsilci parametresi için içinde bir lambda ifadesi geçirilemez `RemoveHandler` .

`Function` `Sub` Bir standart işlev veya alt yordam oluştururken olduğu gibi, veya anahtar sözcüğünü kullanarak lambda ifadeleri oluşturursunuz. Ancak, lambda ifadeleri bir ifadeye dahil edilir.

Aşağıdaki örnek, bağımsız değişkenini artıran ve değeri döndüren bir lambda ifadesidir. Örnek, bir işlev için hem tek satırlı hem çok satırlı lambda ifadesi sözdizimini gösterir.

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

Aşağıdaki örnek, konsoluna bir değer yazan bir lambda ifadesidir. Örnek, bir altyordam için hem tek satırlı hem çok satırlı lambda ifadesi sözdizimini gösterir.

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

Önceki örneklerde lambda ifadelerinin bir değişken adına atandığını fark edersiniz. Değişkenine başvurduğunuzda, lambda ifadesini çağırılır. Ayrıca, aşağıdaki örnekte gösterildiği gibi bir lambda ifadesini aynı anda bildirebilir ve çağırabilirsiniz.

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

Bir lambda ifadesi, bir işlev çağrısının değeri olarak döndürülebilir (Bu konunun ilerleyen bölümlerinde yer alan [bağlam](#context) bölümünde gösterildiği gibi) veya aşağıdaki örnekte gösterildiği gibi bir temsilci türü alan parametreye bağımsız değişken olarak geçirilmiş olabilir.

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a>Lambda İfadesi Sözdizimi

Bir lambda ifadesinin sözdizimi, standart bir işlev veya alt yordamın sözdizimine benzer. Farklar şunlardır:

- Lambda ifadesinin adı yoktur.

- Lambda ifadelerinin veya gibi değiştiriciler olamaz `Overloads` `Overrides` .

- Tek satırlık Lambda işlevleri `As` , dönüş türünü belirlemek için bir yan tümce kullanmaz. Bunun yerine, tür lambda ifadesinin gövdesinin değerlendirilen değerden oluşur. Örneğin, lambda ifadesinin gövdesi ise, `cust.City = "London"` dönüş türü olur `Boolean` .

- Çok satırlı lambda işlevlerinde, bir yan tümce kullanarak bir dönüş türü belirtebilir `As` veya `As` dönüş türünün çıkarsanabilmesi için yan tümceyi atlayabilirsiniz. `As`Bir çok satırlı Lambda işlevi için yan tümce atlandığında, dönüş türü, `Return` çok satırlı lambda işlevindeki tüm deyimlerden baskın tür olarak algılanır. *Baskın tür* , diğer tüm türlerin genişletip benzersiz bir türdür. Bu benzersiz tür belirlenemiyorsa, baskın tür, dizideki diğer tüm türlerin daraltabileceği benzersiz türdür. Bu benzersiz türlerden hiçbiri belirlenemiyorsa, baskın tür olur `Object` . Bu durumda, `Option Strict` olarak ayarlandıysa `On` , bir derleyici hatası oluşur.

     Örneğin, deyimi için sağlanan ifadeler `Return` , ve türünde değerler içeriyorsa, sonuç olarak `Integer` `Long` `Double` elde edilen dizi türüdür `Double` . Her ikisi ve `Integer` `Long` `Double` yalnızca ve ' a kadar `Double` . Bu nedenle, `Double` baskın türdür. Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../data-types/widening-and-narrowing-conversions.md).

- Tek satırlık bir işlevin gövdesi bir deyim değil, bir değer döndüren bir ifade olmalıdır. `Return`Tek satır işlevleri için bir ifade yoktur. Tek satır işlevi tarafından döndürülen değer, işlevin gövdesinde ifadenin değeridir.

- Tek satırlık alt yordamın gövdesi tek satırlık bir ifade olmalıdır.

- Tek satırlı işlevler ve alt yordamlar bir `End Function` veya `End Sub` ifadesini içermez.

- Anahtar sözcüğünü kullanarak bir lambda ifadesi parametresinin veri türünü belirtebilir `As` veya parametresinin veri türü çıkarsanamıyor. Tüm parametrelerin belirtilmiş veri türleri olmalıdır veya hepsi çıkarsanmalıdır.

- `Optional`ve `Paramarray` parametrelerine izin verilmez.

- Genel parametrelere izin verilmiyor.

## <a name="async-lambdas"></a>Zaman Uyumsuz Lambdalar

[Async](../../../language-reference/modifiers/async.md) ve [Await işleci](../../../language-reference/operators/await-operator.md) anahtar sözcüklerini kullanarak zaman uyumsuz işleme içeren lambda ifadeleri ve deyimlerini kolayca oluşturabilirsiniz. Örneğin, aşağıdaki Windows Forms örnek, zaman uyumsuz bir yöntemi çağıran ve bekleden bir olay işleyicisi içerir `ExampleMethodAsync` .

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

Bir [AddHandler ifadesinde](../../../language-reference/statements/addhandler-statement.md)zaman uyumsuz lambda kullanarak aynı olay işleyicisini ekleyebilirsiniz. Bu işleyiciyi eklemek için `Async` Aşağıdaki örnekte gösterildiği gibi Lambda parametre listesinden önce bir değiştirici ekleyin.

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

Zaman uyumsuz yöntemlerin nasıl oluşturulacağı ve kullanılacağı hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama](../../concepts/async/index.md).

## <a name="context"></a>Bağlam

Lambda ifadesi bağlamını kapsam içinde paylaşır. Bu, kapsayan kapsamda yazılan kod ile aynı erişim haklarına sahiptir. Bu, üye değişkenlerine, işlevlere ve alt öğeleri, `Me` ve parametreleri ve kapsayan kapsamdaki yerel değişkenlere erişimi içerir.

Yerel değişkenlere ve kapsayan kapsamdaki parametrelere erişim, bu kapsamın yaşam süresinden daha fazla uzatabilirler. Lambda ifadesine başvuran bir temsilci çöp toplama için kullanılabilir olmadığından, özgün ortamdaki değişkenlere erişim korunur. Aşağıdaki örnekte, değişkeni `target` yereldir `makeTheGame` , lambda ifadesinin `playTheGame` tanımlandığı yöntem. İçinde öğesine atanan döndürülen lambda ifadesinin `takeAGuess` `Main` yerel değişkene hala erişimi olduğunu unutmayın `target` .

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

Aşağıdaki örnek, iç içe lambda ifadesinin çok çeşitli erişim haklarını gösterir. Döndürülen lambda ifadesi sürümünden yürütüldüğünde `Main` `aDel` , şu öğelere erişir:

- İçinde tanımlandığı sınıfın alanı:`aField`

- İçinde tanımlandığı sınıfın bir özelliği:`aProp`

- Tanımlı yöntemin parametresi `functionWithNestedLambda` :`level1`

- Yerel değişkeni `functionWithNestedLambda` :`localVar`

- İçinde iç içe yerleştirilmiş olan lambda ifadesinin parametresi:`level2`

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a>Temsilci türüne dönüştürme

Lambda ifadesi örtük olarak uyumlu bir temsilci türüne dönüştürülebilir. Uyumluluk için genel gereksinimler hakkında daha fazla bilgi için bkz. [gevşek temsilci dönüştürme](../delegates/relaxed-delegate-conversion.md). Örneğin, aşağıdaki kod örneği dolaylı olarak `Func(Of Integer, Boolean)` veya eşleşen bir temsilci imzasına dönüştüren bir lambda ifadesi gösterir.

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

Aşağıdaki kod örneği, örtülü olarak `Sub(Of Double, String, Double)` veya eşleşen bir temsilci imzasına dönüştüren bir lambda ifadesini gösterir.

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

Temsilcilere lambda ifadeleri atadığınızda veya bunları yordamlara bağımsız değişkenler olarak geçirdiğinizde, parametre adlarını belirtebilir, ancak veri türlerini atlayabilirsiniz, böylece türlerin temsilciden alınmasını sağlayabilirsiniz.

## <a name="examples"></a>Örnekler

- Aşağıdaki örnek, `True` null yapılabilir değer türü bağımsız değişkenine atanan bir değer varsa ve değeri ise döndüren bir lambda ifadesini tanımlar `False` `Nothing` .

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- Aşağıdaki örnek, bir dizideki son öğenin dizinini döndüren bir lambda ifadesini tanımlar.

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Visual Basic'de LINQ'e Giriş](../linq/introduction-to-linq.md)
- [Temsilciler](../delegates/index.md)
- [Function Deyimi](../../../language-reference/statements/function-statement.md)
- [Sub Deyimi](../../../language-reference/statements/sub-statement.md)
- [Null yapılabilir değer türleri](../data-types/nullable-value-types.md)
- [Nasıl yapılır: Visual Basic'de Başka Bir Yordama Yordam Geçirme](../delegates/how-to-pass-procedures-to-another-procedure.md)
- [Nasıl yapılır: Lambda İfadesi Oluşturma](./how-to-create-a-lambda-expression.md)
- [Gevşek Temsilci Dönüştürme](../delegates/relaxed-delegate-conversion.md)
