---
title: Await İşleci (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d639d1398c0f783fcfa40ee9ff278922fd6fc7b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="await-operator-visual-basic"></a>Await İşleci (Visual Basic)
`Await` operatörünü awaited görevi tamamlanıncaya kadar, metodun yürütülmesini askıya almak için bir zaman uyumsuz metod veya lambda ifadesinde bir işlenene uygularsınız. Görev devam eden iş temsil eder.  
  
 Yönteminde `Await` kullanılan olmalıdır bir [zaman uyumsuz](../../../visual-basic/language-reference/modifiers/async.md) değiştiricisi. Kullanılarak tanımlanmış böyle bir yöntemi, `Async` değiştiricisi ve genellikle içeren bir veya daha fazla `Await` ifadeleri olarak adlandırılır bir *async yöntemi*.  
  
> [!NOTE]
>  `Async` Ve `Await` anahtar sözcükler, Visual Studio 2012'de sunulmuştur. Zaman uyumsuz programlamaya giriş için bkz: [uyumsuz ve bekleme ile zaman uyumsuz programlama](../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Genellikle, uygulama, görev `Await` işlecidir uygulayan bir yöntem çağrısından dönüş değeri [görev tabanlı zaman uyumsuz desen](http://go.microsoft.com/fwlink/?LinkId=204847), diğer bir deyişle, bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>.  
  
 Aşağıdaki kodda, <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>, `getContentsTask`, bir `Task(Of Byte())` döndürür. Görev, işlem tamamlandığında gerçek bayt dizisini üretmek için bir vaattir. `Await` İşleci uygulanan `getContentsTask` yürütme askıya almak için `SumPageSizesAsync` kadar `getContentsTask` tamamlandı. Bu arada, Denetim çağırana döndürülen `SumPageSizesAsync`. Zaman `getContentsTask` tamamlandı, `Await` ifadeyi hesaplar bir bayt dizisi.  
  
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
>  Tam bir örnek için bkz: [izlenecek yol: Web kullanarak zaman uyumsuz ve bekleme tarafından erişme](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Örnekten indirebilirsiniz [Geliştirici kod örnekleri](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) Microsoft Web sitesinde. AsyncWalkthrough_HttpClient projesinde örnektir.  
  
 `Await` getiren bir metot çağrısının sonucuna `Task(Of TResult)` uygulanırsa, `Await` ifadesinin türü TResult olur. `Await`, bir `Task` getiren bir metot çağrısının sonucuna uygulanırsa, `Await` ifadesi bir değer getirmez. Aşağıdaki örnek fark gösterilmektedir.  
  
```vb  
' Await used with a method that returns a Task(Of TResult).  
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()  
  
' Await used with a method that returns a Task.  
Await AsyncMethodThatReturnsTask()  
```  
  
 Bir `Await` ifadesi veya açıklaması, üzerinde yürütme yaptığı iş parçacığını engellemez. Bunun yerine, `Await` ifadesinden sonra, bekleyen görevlerin bir devamı olarak, derleyicinin zaman uyumsuz yöntemin geri kalanını imzalamasına yol açar. Denetim ardından async yöntemi çağırana döndürür. Görev tamamlandığında, devamlılık ve kaldığı yerden zaman uyumsuz yöntem sürdürür yürütülmesi çağırır.  
  
 Bir `Await` ifadesi yalnızca bir `Async` değiştiricisiyle işaretlenmiş bir anında kapatma metodunun veya lambda ifadesinin gövdesinde gerçekleşebilir. Terim *bekleme* bu bağlamda yalnızca bir anahtar sözcük görevi görür. Başka bir yerde bir tanımlayıcı olarak yorumlanır. Zaman uyumsuz yöntem veya lambda ifadesinde bulunan bir `Await` ifadesi bir sorgu ifadesinde gerçekleşemez `catch` veya `finally` , engelleme bir [deneyin... Catch... Son olarak](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) ifadesinde döngüsü denetim değişkeni deyimi bir `For` veya `For Each` döngüsü veya gövdesinde bir [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) deyimi.  
  
## <a name="exceptions"></a>Özel Durumlar  
 Çoğu zaman uyumsuz yöntemleri döndürür bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>. Döndürülen görev özelliklerini durumunu ve görevin tam olup, async yöntemi bir özel durum nedeniyle veya iptal edildi ve son sonucu gibi geçmişi hakkında bilgi taşır. `Await` İşleci bu özellikleri erişir.  
  
 Bir özel duruma neden olan görev döndüren bir zaman uyumsuz yöntem bekleme durumunda `Await` işleci özel durumu yeniden oluşturur.  
  
 İptal edilen bir görev döndüren zaman uyumsuz yöntemi beklerseniz, `Await` operatörü yeniden bir <xref:System.OperationCanceledException> oluşturur.  
  
 Hatalı durumda tek bir görevi birden fazla özel yansıtabilirsiniz.  Örneğin, görev için bir çağrı sonucunu olabilir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Bu tür bir görev bekleme zaman bekleme işlemi yalnızca bir özel durum yeniden oluşturur. Ancak, özel durumlar hangisinin işlenemezse tahmin edilemez.  
  
 Zaman uyumsuz yöntemleri işleme hatası örnekleri için bkz: [deneyin... Catch... Finally ifadesi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Windows Forms örnek kullanımını göstermektedir `Await` bir zaman uyumsuz yöntem `WaitAsynchronouslyAsync`. Bu yöntem davranışını davranışını ile karşılaştırın `WaitSynchronously`. Bir `Await` operatörü olmadan, `WaitSynchronously` zaman uyumlu olarak çalışır, tanımında `Async` değiştiricisinin ve gövdesinde bir <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> çağrısı kullanılmasına rağmen.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Zaman uyumsuz programlama ile zaman uyumsuz ve bekleme](../../../visual-basic/programming-guide/concepts/async/index.md)  
 [İzlenecek yol: Async kullanarak Web'e erişme ve bekler](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Zaman uyumsuz](../../../visual-basic/language-reference/modifiers/async.md)
