---
title: Await İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: 9d55ba82547dfcb0336c3a3fd12521c0dcb3eb58
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371836"
---
# <a name="await-operator-visual-basic"></a>Await İşleci (Visual Basic)

`Await` operatörünü awaited görevi tamamlanıncaya kadar, metodun yürütülmesini askıya almak için bir zaman uyumsuz metod veya lambda ifadesinde bir işlenene uygularsınız. Görev, devam eden işi temsil eder.

' In kullanıldığı yöntemin `Await` [zaman uyumsuz](../modifiers/async.md) değiştiricisi olmalıdır. Bu tür bir yöntem, değiştirici kullanılarak tanımlanır `Async` ve genellikle bir veya daha fazla ifade içeren bir `Await` *zaman uyumsuz yöntem*olarak adlandırılır.

> [!NOTE]
> `Async`Ve `Await` anahtar sözcükleri Visual Studio 2012 ' de tanıtılmıştı. Zaman uyumsuz programlamaya giriş için bkz. [Async ve await Ile zaman uyumsuz programlama](../../programming-guide/concepts/async/index.md).

Genellikle, işlecini uyguladığınız görev, `Await` [görev tabanlı zaman uyumsuz model](https://www.microsoft.com/download/details.aspx?id=19957), yani, bir veya olarak uygulayan bir yönteme yapılan çağrıdan dönüş değeridir <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> .

Aşağıdaki kodda, <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>, `getContentsTask`, bir `Task(Of Byte())` döndürür. Görev, işlem tamamlandığında gerçek bayt dizisini üretmek için bir vaattir. `Await`İşleci `getContentsTask` tamamlanana kadar içinde yürütmeyi askıya almak için öğesine `SumPageSizesAsync` uygulanır `getContentsTask` . Bu sırada denetim, çağıran öğesine döndürülür `SumPageSizesAsync` . `getContentsTask`Bittiğinde, `Await` ifade bir bayt dizisi olarak değerlendirilir.

```vb
Private Async Function SumPageSizesAsync() As Task

    ' To use the HttpClient type in desktop apps, you must include a using directive and add a
    ' reference for the System.Net.Http namespace.
    Dim client As HttpClient = New HttpClient()
    ' . . .
    Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
    Dim urlContents As Byte() = Await getContentsTask

    ' Equivalently, now that you see how it works, you can write the same thing in a single line.
    'Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ' . . .
End Function
```

> [!IMPORTANT]
> Tüm örnek için bkz. [Izlenecek yol: Async ve await kullanarak Web 'e erişme](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Örneği, Microsoft Web sitesindeki [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) indirebilirsiniz. Örnek, AsyncWalkthrough_HttpClient projem.

`Await` getiren bir metot çağrısının sonucuna `Task(Of TResult)` uygulanırsa, `Await` ifadesinin türü TResult olur. `Await`, bir `Task` getiren bir metot çağrısının sonucuna uygulanırsa, `Await` ifadesi bir değer getirmez. Aşağıdaki örnek, farkı göstermektedir.

```vb
' Await used with a method that returns a Task(Of TResult).
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()

' Await used with a method that returns a Task.
Await AsyncMethodThatReturnsTask()
```

Bir `Await` ifadesi veya açıklaması, üzerinde yürütme yaptığı iş parçacığını engellemez. Bunun yerine, `Await` ifadesinden sonra, bekleyen görevlerin bir devamı olarak, derleyicinin zaman uyumsuz yöntemin geri kalanını imzalamasına yol açar. Sonra Denetim zaman uyumsuz yöntemi çağırana döner. Görev tamamlandığında, devamlılığını çağırır ve zaman uyumsuz yöntemin yürütülmesi kaldığınız yerden devam eder.

Bir `Await` ifadesi yalnızca bir `Async` değiştiricisiyle işaretlenmiş bir anında kapatma metodunun veya lambda ifadesinin gövdesinde gerçekleşebilir. *Await* terimi yalnızca söz konusu bağlamda anahtar sözcük olarak işlev görür. Başka bir yerde, tanımlayıcı olarak yorumlanır. `Async`Yöntem veya lambda ifadesinde bir `Await` ifade, `Catch` `Finally` bir [TRY... içinde veya bloğunda bir sorgu ifadesinde gerçekleşemez. Yakala... Finally deyimi](../statements/try-catch-finally-statement.md), bir veya döngüsünün döngü denetim değişkeni ifadesinde `For` `For Each` veya bir [SyncLock](../statements/synclock-statement.md) deyiminin gövdesinde.

## <a name="exceptions"></a>Özel durumlar

En zaman uyumsuz yöntemler bir <xref:System.Threading.Tasks.Task> veya döndürür <xref:System.Threading.Tasks.Task%601> . Döndürülen görevin özellikleri, görevin tamamlanıp tamamlanmayacağı, zaman uyumsuz yöntemin bir özel durum mi olduğunu, yoksa iptal edildiğini mi olduğunu ve nihai sonucun ne olduğunu belirtir gibi durum ve geçmişi hakkındaki bilgileri taşır. `Await`İşleci bu özelliklere erişir.

Bir özel duruma neden olan bir görev döndüren zaman uyumsuz yöntemi beklelerseniz, `Await` işleç özel durumu yeniden oluşturur.

İptal edilen bir görev döndüren zaman uyumsuz yöntemi beklerseniz, `Await` operatörü yeniden bir <xref:System.OperationCanceledException> oluşturur.

Hatalı durumda olan tek bir görev birden çok özel durumu yansıtabilir.  Örneğin, görev bir çağrısının sonucu olabilir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> . Böyle bir görevi beklelerseniz, await işlemi özel durumların yalnızca birini yeniden oluşturur. Ancak, özel durumların hangisinin yeniden oluşturulduğu tahmin edebilirsiniz.

Zaman uyumsuz yöntemlerde hata işleme örnekleri için bkz [. TRY... Yakala... Finally ekstresi](../statements/try-catch-finally-statement.md).

## <a name="example"></a>Örnek

Aşağıdaki Windows Forms örnek, `Await` zaman uyumsuz bir yöntemde kullanımını gösterir `WaitAsynchronouslyAsync` . Davranışı ile bu yöntemin davranışını kontrast `WaitSynchronously` . Bir `Await` operatörü olmadan, `WaitSynchronously` zaman uyumlu olarak çalışır, tanımında `Async` değiştiricisinin ve gövdesinde bir <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> çağrısı kullanılmasına rağmen.

```vb
Private Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
    ' Call the method that runs asynchronously.
    Dim result As String = Await WaitAsynchronouslyAsync()

    ' Call the method that runs synchronously.
    'Dim result As String = Await WaitSynchronously()

    ' Display the result.
    TextBox1.Text &= result
End Sub

' The following method runs asynchronously. The UI thread is not
' blocked during the delay. You can move or resize the Form1 window
' while Task.Delay is running.
Public Async Function WaitAsynchronouslyAsync() As Task(Of String)
    Await Task.Delay(10000)
    Return "Finished"
End Function

' The following method runs synchronously, despite the use of Async.
' You cannot move or resize the Form1 window while Thread.Sleep
' is running because the UI thread is blocked.
Public Async Function WaitSynchronously() As Task(Of String)
    ' Import System.Threading for the Sleep method.
    Thread.Sleep(10000)
    Return "Finished"
End Function
```

## <a name="see-also"></a>Ayrıca bkz.

- [Async ve await ile zaman uyumsuz programlama](../../programming-guide/concepts/async/index.md)
- [İzlenecek yol: Async ve await kullanarak Web 'e erişme](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Eş](../modifiers/async.md)
