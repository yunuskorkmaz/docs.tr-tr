---
title: Zaman Uyumsuz
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: 73d433c66750ead3a97b1c283cc26b4c43f078df
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351633"
---
# <a name="async-visual-basic"></a>Zaman Uyumsuz (Visual Basic)

`Async` değiştirici, değiştirdiği yöntemin veya [lambda ifadesinin](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) zaman uyumsuz olduğunu gösterir. Bu tür yöntemler *zaman uyumsuz yöntemler*olarak adlandırılır.

Zaman uyumsuz bir yöntem, çağıranın iş parçacığını engellemeden uzun süre çalışan bir iş yapmak için kullanışlı bir yol sağlar. Zaman uyumsuz bir yöntemi çağıran, zaman uyumsuz yöntemin tamamlanmasını beklemeden işini sürdürür.

> [!NOTE]
> `Async` ve `Await` anahtar sözcükleri Visual Studio 2012 ' de tanıtılmıştı. Zaman uyumsuz programlamaya giriş için bkz. [Async ve await Ile zaman uyumsuz programlama](../../../visual-basic/programming-guide/concepts/async/index.md).

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

Genellikle, `Async` anahtar sözcüğü tarafından değiştirilen bir yöntem en az bir [await](../../../visual-basic/language-reference/modifiers/async.md) ifadesi veya deyimi içerir. Bekleyen görev tamamlanıncaya kadar bekletilen nokta olan ilk `Await`'a ulaşana kadar metot zaman uyumlu olarak çalışır. Bu sırada, denetim, metodu çağırana döner. Yöntem bir `Await` ifadesi veya deyimi içermiyorsa, yöntem askıya alınmaz ve zaman uyumlu bir yöntem olarak yürütülür. Bir derleyici uyarısı, `Await` içermeyen tüm zaman uyumsuz yöntemlere sizi uyarır çünkü bu durum bir hata gösteriyor olabilir. Daha fazla bilgi için bkz. [derleyici hatası](../error-messages/bc42358.md).

`Async` anahtar kelimesi ayrılmamış bir anahtar sözcüktür. Bir metot veya lambda ifadesi değiştirdiği zaman bir anahtar sözcüktür. Diğer tüm bağlamlarda bu, bir tanımlayıcı olarak yorumlanır.

## <a name="return-types"></a>Dönüş türleri

Zaman uyumsuz bir yöntem, bir [alt](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) yordamdır veya <xref:System.Threading.Tasks.Task> ya da <xref:System.Threading.Tasks.Task%601>dönüş türüne sahip bir [işlev](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) yordamdır. Yöntem herhangi bir [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parametresi bildiremez.

Metodun [Return](../../../visual-basic/language-reference/statements/return-statement.md) Ifadesinin TResult türünde bir işleneni varsa, zaman uyumsuz bir yöntemin dönüş türü için `Task(Of TResult)` belirtirsiniz. Yöntem tamamlandığında anlamlı bir değer döndürülmezse `Task` kullanırsınız. Yani, yönteme bir çağrı, `Task`'i geri getirir, ancak `Task` tamamlandığı zaman, `Await`'i bekleyen herhangi bir `Task` deyimi bir sonuç değeri üretemez.

Zaman uyumsuz alt rutinler, öncelikle bir `Sub` yordamının gerekli olduğu yerde olay işleyicilerini tanımlamak için kullanılır Zaman uyumsuz bir alt rutinin çağırıcısı onu bekleyemez ve metodun oluşturduğu özel durumları yakalayamaz.

Daha fazla bilgi ve örnek için bkz. [zaman uyumsuz dönüş türleri](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekler, zaman uyumsuz bir olay işleyicisi, bir zaman uyumsuz lambda ifadesi ve bir zaman uyumsuz metot gösterir. Bu öğeleri kullanan tam bir örnek için bkz. [Izlenecek yol: Async ve await kullanarak Web 'e erişme](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)izlenecek yol kodunu indirebilirsiniz.

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
'      Dim result As Byte() = Await GetURLContents("https://msdn.com")
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
- [İzlenecek yol: Async ve Await Kullanarak Web'e Erişme](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
