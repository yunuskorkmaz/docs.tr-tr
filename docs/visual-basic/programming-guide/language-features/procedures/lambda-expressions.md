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
ms.openlocfilehash: d3c385737d7f3a25009dba3abfffe88a1cf1619a
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524053"
---
# <a name="lambda-expressions-visual-basic"></a>Lambda İfadeleri (Visual Basic)

*Lambda ifadesi* , bir temsilcinin geçerli olduğu her yerde kullanılabilecek bir ada sahip olmayan bir işlev veya alt yordam 'dir. Lambda ifadeleri işlevler veya alt yordamlar olabilir ve tek satırlık veya çok satırlı olabilir. Geçerli kapsamdan bir lambda ifadesine değer geçirebilirsiniz.

> [!NOTE]
> @No__t_0 deyimin bir istisnası vardır. @No__t_0 temsilci parametresi için ' de bir lambda ifadesi geçirilemez.

Bir standart işlev veya alt yordam oluştururken olduğu gibi `Function` veya `Sub` anahtar sözcüğünü kullanarak lambda ifadeleri oluşturursunuz. Ancak, lambda ifadeleri bir ifadeye dahil edilir.

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

- Lambda ifadelerinde `Overloads` veya `Overrides` gibi değiştiriciler olamaz.

- Tek satırlık Lambda işlevleri, dönüş türünü belirlemek için bir `As` yan tümcesi kullanmaz. Bunun yerine, tür lambda ifadesinin gövdesinin değerlendirilen değerden oluşur. Örneğin, lambda ifadesinin gövdesi `cust.City = "London"`, dönüş türü `Boolean`.

- Çok satırlı lambda işlevlerinde bir `As` yan tümcesini kullanarak bir dönüş türü belirtebilir veya dönüş türünün çıkarsanabilmesi için `As` yan tümcesini atlayabilirsiniz. Çok satırlı Lambda işlevi için `As` yan tümcesi atlandığında, dönüş türü, çok satırlı lambda işlevindeki tüm `Return` deyimlerden baskın tür olarak algılanır. *Baskın tür* , diğer tüm türlerin genişletip benzersiz bir türdür. Bu benzersiz tür belirlenemiyorsa, baskın tür, dizideki diğer tüm türlerin daraltabileceği benzersiz türdür. Bu benzersiz türlerden hiçbiri belirlenemiyorsa, baskın tür `Object`. Bu durumda, `Option Strict` `On` olarak ayarlanırsa bir derleyici hatası oluşur.

     Örneğin, `Return` deyimi için sağlanan ifadeler `Integer`, `Long` ve `Double` türünde değerler içeriyorsa, sonuçta elde edilen dizi `Double` türüdür. Hem `Integer` hem de `Long` `Double` ve yalnızca `Double`. Bu nedenle, `Double` baskın türdür. Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).

- Tek satırlık bir işlevin gövdesi bir deyim değil, bir değer döndüren bir ifade olmalıdır. Tek satırlı işlevler için `Return` bir ifade yoktur. Tek satır işlevi tarafından döndürülen değer, işlevin gövdesinde ifadenin değeridir.

- Tek satırlık alt yordamın gövdesi tek satırlık bir ifade olmalıdır.

- Tek satırlı işlevler ve alt yordamlar bir `End Function` veya `End Sub` ifadesini içermez.

- @No__t_0 anahtar sözcüğünü kullanarak bir lambda ifadesi parametresinin veri türünü belirtebilir veya parametresinin veri türü çıkarsanamıyor. Tüm parametrelerin belirtilmiş veri türleri olmalıdır veya hepsi çıkarsanmalıdır.

- `Optional` ve `Paramarray` parametrelere izin verilmiyor.

- Genel parametrelere izin verilmiyor.

## <a name="async-lambdas"></a>Zaman Uyumsuz Lambdalar

[Async](../../../../visual-basic/language-reference/modifiers/async.md) ve [Await işleci](../../../../visual-basic/language-reference/operators/await-operator.md) anahtar sözcüklerini kullanarak zaman uyumsuz işleme içeren lambda ifadeleri ve deyimlerini kolayca oluşturabilirsiniz. Örneğin, aşağıdaki Windows Forms örnek, zaman uyumsuz bir yöntemi çağıran ve bekleden bir olay işleyicisi içerir, `ExampleMethodAsync`.

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

Bir [AddHandler ifadesinde](../../../../visual-basic/language-reference/statements/addhandler-statement.md)zaman uyumsuz lambda kullanarak aynı olay işleyicisini ekleyebilirsiniz. Bu işleyiciyi eklemek için aşağıdaki örnekte gösterildiği gibi Lambda parametre listesinden önce bir `Async` değiştirici ekleyin.

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

Zaman uyumsuz yöntemlerin nasıl oluşturulacağı ve kullanılacağı hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama](../../../../visual-basic/programming-guide/concepts/async/index.md).

## <a name="context"></a>Bağlam

Lambda ifadesi bağlamını kapsam içinde paylaşır. Bu, kapsayan kapsamda yazılan kod ile aynı erişim haklarına sahiptir. Bu, üye değişkenlerine, işlevlere ve alt öğeleri, `Me` ve parametreleri ve kapsayan kapsamdaki yerel değişkenlere erişimi içerir.

Yerel değişkenlere ve kapsayan kapsamdaki parametrelere erişim, bu kapsamın yaşam süresinden daha fazla uzatabilirler. Lambda ifadesine başvuran bir temsilci çöp toplama için kullanılabilir olmadığından, özgün ortamdaki değişkenlere erişim korunur. Aşağıdaki örnekte, değişken `target`, lambda ifadesinin `playTheGame` tanımlanan yöntemi `makeTheGame` yereldir. @No__t_1 `takeAGuess` atanan, döndürülen lambda ifadesinin `target` yerel değişkenine erişimi olduğunu unutmayın.

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

Aşağıdaki örnek, iç içe lambda ifadesinin çok çeşitli erişim haklarını gösterir. Döndürülen lambda ifadesi `aDel` olarak `Main` yürütüldüğünde, bu öğelere erişir:

- İçinde tanımlandığı sınıfın alanı: `aField`

- İçinde tanımlandığı sınıfın bir özelliği: `aProp`

- @No__t_0 yönteminin tanımlandığı bir parametre: `level1`

- Yerel bir `functionWithNestedLambda` değişkeni: `localVar`

- İçinde iç içe yerleştirilmiş olan lambda ifadesinin parametresi: `level2`

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a>Temsilci türüne dönüştürme

Lambda ifadesi örtük olarak uyumlu bir temsilci türüne dönüştürülebilir. Uyumluluk için genel gereksinimler hakkında daha fazla bilgi için bkz. [gevşek temsilci dönüştürme](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md). Örneğin, aşağıdaki kod örneği dolaylı olarak `Func(Of Integer, Boolean)` veya eşleşen bir temsilci imzasına dönüştüren bir lambda ifadesi gösterir.

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

Aşağıdaki kod örneği, örtülü olarak `Sub(Of Double, String, Double)` veya eşleşen bir temsilci imzasına dönüştüren bir lambda ifadesini gösterir.

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

Temsilcilere lambda ifadeleri atadığınızda veya bunları yordamlara bağımsız değişkenler olarak geçirdiğinizde, parametre adlarını belirtebilir, ancak veri türlerini atlayabilirsiniz, böylece türlerin temsilciden alınmasını sağlayabilirsiniz.

## <a name="examples"></a>Örnekler

- Aşağıdaki örnek, null yapılabilir bağımsız değişkeni atanan bir değere sahipse ve değeri `Nothing` ise `False` `True` döndüren bir lambda ifadesini tanımlar.

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- Aşağıdaki örnek, bir dizideki son öğenin dizinini döndüren bir lambda ifadesini tanımlar.

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Visual Basic LINQ 'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Function Deyimi](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub Deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Boş Değer Atanabilen Değer Türleri](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Nasıl yapılır: yordamları Visual Basic başka bir yordama geçirme](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Nasıl yapılır: Lambda İfadesi Oluşturma](./how-to-create-a-lambda-expression.md)
- [Gevşek Temsilci Dönüştürme](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
