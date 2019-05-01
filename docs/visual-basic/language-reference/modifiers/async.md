---
title: Zaman Uyumsuz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: ad6d671a45cee7d534347d23963bb5035ecc8dac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802719"
---
# <a name="async-visual-basic"></a>Zaman Uyumsuz (Visual Basic)
`Async` Değiştiricisi gösterir yöntemi veya [lambda ifadesi](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) olduğunu değiştirdiği zaman uyumsuzdur. Bu tür yöntemler olarak adlandırılır *zaman uyumsuz yöntemler*.  
  
 Zaman uyumsuz yöntemin arayanın, iş parçacığını engellemeden muhtemelen uzun süren iş yapmak için kullanışlı bir yol sağlar. Zaman uyumsuz yöntemi çağıran kişi, zaman uyumsuz yöntemin tamamlanmasını beklemeden işine devam edebilir.  
  
> [!NOTE]
>  `Async` Ve `Await` anahtar sözcükleri Visual Studio 2012'de kullanıma sunulmuştur. Zaman uyumsuz programlamaya giriş için bkz [Async ve Await ile zaman uyumsuz programlama](../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Aşağıdaki örnek, bir zaman uyumsuz metodun yapısını gösterir. Kural olarak, zaman uyumsuz metot adları "Async." ile biter.  
  
```vb  
Public Async Function ExampleMethodAsync() As Task(Of Integer)  
    ' . . .  
  
    ' At the Await expression, execution in this method is suspended and,  
    ' if AwaitedProcessAsync has not already finished, control returns  
    ' to the caller of ExampleMethodAsync. When the awaited task is   
    ' completed, this method resumes execution.   
    Dim exampleInt As Integer = Await AwaitedProcessAsync()  
  
    ' . . .  
  
    ' The return statement completes the task. Any method that is   
    ' awaiting ExampleMethodAsync can now get the integer result.  
    Return exampleInt  
End Function  
```  
  
 Genellikle, bir yöntem tarafından değiştirildi `Async` anahtar sözcüğü içeren en az bir [Await](../../../visual-basic/language-reference/modifiers/async.md) ifadesi veya deyimi. Bekleyen görev tamamlanıncaya kadar bekletilen nokta olan ilk `Await`'a ulaşana kadar metot zaman uyumlu olarak çalışır. Bu sırada, denetim, metodu çağırana döner. Metot bir `Await` ifade veya deyimi içermiyorsa, metot askıya alınmaz ve zaman uyumlu bir yöntem olarak yürütülür. Bir derleyici uyarısı içermeyen zaman uyumsuz yöntemler konusunda uyarır `Await` çünkü bu durumda bir hata gösterebilir. Daha fazla bilgi için [derleyici hatası](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md).  
  
 `Async` anahtar kelimesi ayrılmamış bir anahtar sözcüktür. Bir metot veya lambda ifadesi değiştirdiği zaman bir anahtar sözcüktür. Diğer tüm bağlamlarda bu, bir tanımlayıcı olarak yorumlanır.  
  
## <a name="return-types"></a>Dönüş Türleri  
 Zaman uyumsuz bir yöntem geçerli bir [alt](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) yordamı veya [işlevi](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) dönüş türüne sahip yordamı <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>. Herhangi bir yöntemi bildiremezsiniz [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parametreleri.  
  
 Belirttiğiniz `Task(Of TResult)` zaman uyumsuz bir yöntemin dönüş türü, [dönüş](../../../visual-basic/language-reference/statements/return-statement.md) deyimi TResult türünde bir işlenene sahipse. Kullandığınız `Task` yöntem tamamlandığında anlamlı bir değer döndürülürse. Yani, yönteme bir çağrı, `Task`'i geri getirir, ancak `Task` tamamlandığı zaman, `Await`'i bekleyen herhangi bir `Task` deyimi bir sonuç değeri üretemez.  
  
 Zaman uyumsuz alt rutinler, öncelikle bir `Sub` yordamının gerekli olduğu yerde olay işleyicilerini tanımlamak için kullanılır Zaman uyumsuz bir alt rutinin çağırıcısı onu bekleyemez ve metodun oluşturduğu özel durumları yakalayamaz.  
  
 Daha fazla bilgi ve örnekler için bkz. [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekler, zaman uyumsuz bir olay işleyicisi, bir zaman uyumsuz lambda ifadesi ve bir zaman uyumsuz metot gösterir. Bu öğeleri kullanan tam bir örnek için bkz. [izlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). İzlenecek yol koddan indirebileceğiniz [geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).  
  
```vb  
' An event handler must be a Sub procedure.  
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
    textBox1.Clear()  
    ' SumPageSizesAsync is a method that returns a Task.  
    Await SumPageSizesAsync()  
    textBox1.Text = vbCrLf & "Control returned to button1_Click."  
End Sub  
  
' The following async lambda expression creates an equivalent anonymous  
' event handler.  
AddHandler button1.Click, Async Sub(sender, e)  
                              textBox1.Clear()  
                              ' SumPageSizesAsync is a method that returns a Task.  
                              Await SumPageSizesAsync()  
                              textBox1.Text = vbCrLf & "Control returned to button1_Click."  
                          End Sub  
  
' The following async method returns a Task(Of T).  
' A typical call awaits the Byte array result:  
'      Dim result As Byte() = Await GetURLContents("http://msdn.com")  
Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
    ' The downloaded resource ends up in the variable named content.  
    Dim content = New MemoryStream()  
  
    ' Initialize an HttpWebRequest for the current URL.  
    Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
    ' Send the request to the Internet resource and wait for  
    ' the response.  
    Using response As WebResponse = Await webReq.GetResponseAsync()  
        ' Get the data stream that is associated with the specified URL.  
        Using responseStream As Stream = response.GetResponseStream()  
            ' Read the bytes in responseStream and copy them to content.    
            ' CopyToAsync returns a Task, not a Task<T>.  
            Await responseStream.CopyToAsync(content)  
        End Using  
    End Using  
  
    ' Return the result as a byte array.  
    Return content.ToArray()  
End Function  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [Await İşleci](../../../visual-basic/language-reference/operators/await-operator.md)
- [Async ve Await ile Zaman Uyumsuz Programlama](../../../visual-basic/programming-guide/concepts/async/index.md)
- [İzlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
