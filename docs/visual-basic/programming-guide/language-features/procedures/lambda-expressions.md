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
ms.openlocfilehash: e688beac18e782367bf39ddec8339df2b2735225
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928900"
---
# <a name="lambda-expressions-visual-basic"></a>Lambda İfadeleri (Visual Basic)
*Lambda ifadesi* , bir temsilcinin geçerli olduğu her yerde kullanılabilecek bir ada sahip olmayan bir işlev veya alt yordam 'dir. Lambda ifadeleri işlevler veya alt yordamlar olabilir ve tek satırlık veya çok satırlı olabilir. Geçerli kapsamdan bir lambda ifadesine değer geçirebilirsiniz.  
  
> [!NOTE]
> `RemoveHandler` İfade bir özel durumdur. Temsilci parametresi `RemoveHandler`için içinde bir lambda ifadesi geçirilemez.  
  
 Bir standart işlev veya alt yordam oluştururken `Function` olduğu `Sub` gibi, veya anahtar sözcüğünü kullanarak lambda ifadeleri oluşturursunuz. Ancak, lambda ifadeleri bir ifadeye dahil edilir.  
  
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
  
- Lambda ifadelerinin `Overloads` veya `Overrides`gibi değiştiriciler olamaz.  
  
- Tek satırlık Lambda işlevleri, dönüş türünü belirlemek için `As` bir yan tümce kullanmaz. Bunun yerine, tür lambda ifadesinin gövdesinin değerlendirilen değerden oluşur. Örneğin, lambda ifadesinin gövdesi ise `cust.City = "London"`, dönüş türü olur. `Boolean`  
  
- Çok satırlı lambda işlevlerinde, bir `As` yan tümce kullanarak bir dönüş türü belirtebilir veya dönüş türünün çıkarsanabilmesi için `As` yan tümceyi atlayabilirsiniz. Bir çok satırlı Lambda işlevi için `Return` yantümceatlandığında,dönüştürü,çoksatırlılambdaişlevindekitümdeyimlerdenbaskıntürolarakalgılanır.`As` *Baskın tür* , diğer tüm türlerin genişletip benzersiz bir türdür. Bu benzersiz tür belirlenemiyorsa, baskın tür, dizideki diğer tüm türlerin daraltabileceği benzersiz türdür. Bu benzersiz türlerden hiçbiri belirlenemiyorsa, baskın tür olur `Object`. Bu durumda `Option Strict` , olarak `On`ayarlandıysa, bir derleyici hatası oluşur.  
  
     Örneğin `Return` , deyimi için sağlanan ifadeler, `Long`ve `Double`türünde `Integer`değerler içeriyorsa, sonuç olarak elde edilen dizi türüdür `Double`. Her ikisi `Integer` ve `Double` yalnızca ve`Double`'akadar. `Long` Bu nedenle `Double` , baskın türdür. Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
- Tek satırlık bir işlevin gövdesi bir deyim değil, bir değer döndüren bir ifade olmalıdır. Tek satır işlevleri için bir ifadeyoktur.`Return` Tek satır işlevi tarafından döndürülen değer, işlevin gövdesinde ifadenin değeridir.  
  
- Tek satırlık alt yordamın gövdesi tek satırlık bir ifade olmalıdır.  
  
- Tek satırlı işlevler ve alt yordamlar bir `End Function` veya `End Sub` ifadesini içermez.  
  
- `As` Anahtar sözcüğünü kullanarak bir lambda ifadesi parametresinin veri türünü belirtebilir veya parametresinin veri türü çıkarsanamıyor. Tüm parametrelerin belirtilmiş veri türleri olmalıdır veya hepsi çıkarsanmalıdır.  
  
- `Optional`ve `Paramarray` parametrelerine izin verilmez.  
  
- Genel parametrelere izin verilmiyor.  
  
## <a name="async-lambdas"></a>Zaman Uyumsuz Lambdalar  
 [Async](../../../../visual-basic/language-reference/modifiers/async.md) ve [Await işleci](../../../../visual-basic/language-reference/operators/await-operator.md) anahtar sözcüklerini kullanarak zaman uyumsuz işleme içeren lambda ifadeleri ve deyimlerini kolayca oluşturabilirsiniz. Örneğin, aşağıdaki Windows Forms örnek, zaman uyumsuz bir yöntemi `ExampleMethodAsync`çağıran ve bekleden bir olay işleyicisi içerir.  
  
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
  
 Bir [AddHandler ifadesinde](../../../../visual-basic/language-reference/statements/addhandler-statement.md)zaman uyumsuz lambda kullanarak aynı olay işleyicisini ekleyebilirsiniz. Bu işleyiciyi eklemek için aşağıdaki örnekte gösterildiği `Async` gibi Lambda parametre listesinden önce bir değiştirici ekleyin.  
  
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
 Lambda ifadesi bağlamını kapsam içinde paylaşır. Bu, kapsayan kapsamda yazılan kod ile aynı erişim haklarına sahiptir. Bu, üye değişkenlerine, işlevlere ve alt öğeleri `Me`, ve parametreleri ve kapsayan kapsamdaki yerel değişkenlere erişimi içerir.  
  
 Yerel değişkenlere ve kapsayan kapsamdaki parametrelere erişim, bu kapsamın yaşam süresinden daha fazla uzatabilirler. Lambda ifadesine başvuran bir temsilci çöp toplama için kullanılabilir olmadığından, özgün ortamdaki değişkenlere erişim korunur. Aşağıdaki örnekte, değişkeni `target` `makeTheGame`yereldir, lambda ifadesinin `playTheGame` tanımlandığı yöntem. `target`İçinde `takeAGuess` öğesineatanandöndürülenlambdaifadesininyereldeğişkenehalaerişimiolduğunuunutmayın.`Main`  
  
 [!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]  
  
 Aşağıdaki örnek, iç içe lambda ifadesinin çok çeşitli erişim haklarını gösterir. Döndürülen lambda ifadesi sürümünden `Main` `aDel`yürütüldüğünde, şu öğelere erişir:  
  
- İçinde tanımlandığı sınıfın alanı:`aField`  
  
- İçinde tanımlandığı sınıfın bir özelliği:`aProp`  
  
- Tanımlı yöntemin `functionWithNestedLambda`parametresi:`level1`  
  
- Yerel değişkeni `functionWithNestedLambda`:`localVar`  
  
- İçinde iç içe yerleştirilmiş olan lambda ifadesinin parametresi:`level2`  
  
 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]  
  
## <a name="converting-to-a-delegate-type"></a>Temsilci türüne dönüştürme  
 Lambda ifadesi örtük olarak uyumlu bir temsilci türüne dönüştürülebilir. Uyumluluk için genel gereksinimler hakkında daha fazla bilgi için bkz. [gevşek temsilci dönüştürme](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md). Örneğin, aşağıdaki kod örneği dolaylı olarak `Func(Of Integer, Boolean)` veya eşleşen bir temsilci imzasına dönüştüren bir lambda ifadesi gösterir.  
  
 [!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]  
  
 Aşağıdaki kod örneği, örtülü olarak `Sub(Of Double, String, Double)` veya eşleşen bir temsilci imzasına dönüştüren bir lambda ifadesini gösterir.  
  
 [!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]  
  
 Temsilcilere lambda ifadeleri atadığınızda veya bunları yordamlara bağımsız değişkenler olarak geçirdiğinizde, parametre adlarını belirtebilir, ancak veri türlerini atlayabilirsiniz, böylece türlerin temsilciden alınmasını sağlayabilirsiniz.  
  
## <a name="examples"></a>Örnekler  
  
- Aşağıdaki örnek, null atanabilir bağımsız değişkeni atanan bir `True` değere sahipse ve `False` değeri ise `Nothing`, döndüren bir lambda ifadesini tanımlar.  
  
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
- [Nasıl yapılır: Yordamları Visual Basic başka bir yordama geçirin](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Nasıl yapılır: Lambda Ifadesi oluşturma](./how-to-create-a-lambda-expression.md)
- [Gevşek Temsilci Dönüştürme](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
