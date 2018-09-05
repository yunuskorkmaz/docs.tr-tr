---
title: Await İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: 2094ba308ba384feb8542e896cb1eafcf645947c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524472"
---
# <a name="await-operator-visual-basic"></a>Await İşleci (Visual Basic)
`Await` operatörünü awaited görevi tamamlanıncaya kadar, metodun yürütülmesini askıya almak için bir zaman uyumsuz metod veya lambda ifadesinde bir işlenene uygularsınız. Görev, devam eden çalışmayı temsil eder.  
  
 Yöntem `Await` kullanılan olmalıdır bir [zaman uyumsuz](../../../visual-basic/language-reference/modifiers/async.md) değiştiricisi. Tarafından tanımlanan tür bir yöntem, `Async` değiştiricisi ve genellikle içeren bir veya daha fazla `Await` ifadeleri olarak adlandırılır bir *zaman uyumsuz yöntem*.  
  
> [!NOTE]
>  `Async` Ve `Await` anahtar sözcükleri Visual Studio 2012'de kullanıma sunulmuştur. Zaman uyumsuz programlamaya giriş için bkz [Async ve Await ile zaman uyumsuz programlama](../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Genellikle, uyguladığınız görev `Await` işleci uygulayan bir Metoda bir çağrıdan dönüş değeridir [görev tabanlı zaman uyumsuz desen](https://go.microsoft.com/fwlink/?LinkId=204847), diğer bir deyişle, bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>.  
  
 Aşağıdaki kodda, <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>, `getContentsTask`, bir `Task(Of Byte())` döndürür. Görev, işlem tamamlandığında gerçek bayt dizisini üretmek için bir vaattir. `Await` İşleci uygulanır `getContentsTask` içindeki yürütmeyi askıya almak için `SumPageSizesAsync` kadar `getContentsTask` tamamlandı. Bu sırada, Denetim çağırana döndürülmeden `SumPageSizesAsync`. Zaman `getContentsTask` bittiğinde `Await` ifadesi bir bayt dizisine değerlendirir.  
  
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
>  Tam bir örnek için bkz. [izlenecek yol: Web kullanarak Async ve Await tarafından erişim](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). İçinden örneği karşıdan yükleyebilirsiniz [geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) Microsoft Web sitesinde. Örnek AsyncWalkthrough_HttpClient projesindedir.  
  
 `Await` getiren bir metot çağrısının sonucuna `Task(Of TResult)` uygulanırsa, `Await` ifadesinin türü TResult olur. `Await`, bir `Task` getiren bir metot çağrısının sonucuna uygulanırsa, `Await` ifadesi bir değer getirmez. Fark aşağıdaki örnekte gösterilmiştir.  
  
```vb  
' Await used with a method that returns a Task(Of TResult).  
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()  
  
' Await used with a method that returns a Task.  
Await AsyncMethodThatReturnsTask()  
```  
  
 Bir `Await` ifadesi veya açıklaması, üzerinde yürütme yaptığı iş parçacığını engellemez. Bunun yerine, `Await` ifadesinden sonra, bekleyen görevlerin bir devamı olarak, derleyicinin zaman uyumsuz yöntemin geri kalanını imzalamasına yol açar. Denetim, ardından zaman uyumsuz yöntemini çağırana döner. Görev tamamlandığında, devamlılık ve yürütülmesi kaldığı zaman uyumsuz yöntem sürdürür çağırır.  
  
 Bir `Await` ifadesi yalnızca bir `Async` değiştiricisiyle işaretlenmiş bir anında kapatma metodunun veya lambda ifadesinin gövdesinde gerçekleşebilir. Terim *Await* yalnızca bu bağlamda bir anahtar sözcük görevi görür. Başka bir yerde, tanımlayıcı olarak yorumlanır. Zaman uyumsuz yöntem veya lambda ifadesinde bulunan bir `Await` ifade içinde bir sorgu ifadesinde gerçekleşemez `catch` veya `finally` bloğu bir [deneyin... Catch... Son olarak](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) deyiminde döngü denetimi değişkeni ifadesinde bir `For` veya `For Each` döngü gövdesinde veya bir [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) deyimi.  
  
## <a name="exceptions"></a>Özel Durumlar  
 Çoğu zaman uyumsuz yöntemlerin dönüş bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>. Döndürülen görevin özelliklerini, durumunu ve geçmişini, görevin tam olup olmadığı, zaman uyumsuz yöntemin bir özel duruma neden oldu veya iptal edildi ve nihai sonucun ne olduğu gibi hakkında bilgi getirir. `Await` İşleci, özelliklere erişir.  
  
 Bir özel durum neden olan bir görev döndüren zaman uyumsuz yöntem, `Await` işleci özel durumu yeniden oluşturur.  
  
 İptal edilen bir görev döndüren zaman uyumsuz yöntemi beklerseniz, `Await` operatörü yeniden bir <xref:System.OperationCanceledException> oluşturur.  
  
 Hatalı bir durumda olan tek bir görev birden çok özel durumu yansıtabilir.  Örneğin, görev yapılan bir çağrının sonucu olabilir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Böyle bir görevi beklerken, bekleme işlemi özel durumlardan yalnızca birini yeniden oluşturur. Ancak, özel durumların fırlatılan tahmin edemezsiniz.  
  
 Zaman uyumsuz yöntemlerdeki hata işleme örnekleri için bkz: [deneyin... Catch... Finally deyimini](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Windows Forms örnek kullanımını gösterir `Await` bir zaman uyumsuz yönteminde `WaitAsynchronouslyAsync`. Davranışı ile yöntemin davranışını karşılaştırın `WaitSynchronously`. Bir `Await` operatörü olmadan, `WaitSynchronously` zaman uyumlu olarak çalışır, tanımında `Async` değiştiricisinin ve gövdesinde bir <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> çağrısı kullanılmasına rağmen.  
  
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
 [Async ve Await ile Zaman Uyumsuz Programlama](../../../visual-basic/programming-guide/concepts/async/index.md)  
 [İzlenecek yol: Async ve Await Kullanarak Web'e Erişme](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Async](../../../visual-basic/language-reference/modifiers/async.md)
