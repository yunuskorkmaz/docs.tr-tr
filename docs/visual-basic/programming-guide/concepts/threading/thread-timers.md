---
title: İş parçacığı zamanlayıcılar (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 809cba93-cc93-4e21-afda-f299f9a39818
ms.openlocfilehash: 019b8372be63b9a9fdbcee134834a34f6bef2b74
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646905"
---
# <a name="thread-timers-visual-basic"></a>İş parçacığı zamanlayıcılar (Visual Basic)
<xref:System.Threading.Timer?displayProperty=nameWithType> Sınıfı, bir görev ayrı bir iş parçacığı üzerinde düzenli olarak çalıştırmak için yararlıdır. Örneğin, bir iş parçacığı süreölçer durumunu ve bir veritabanının bütünlüğünü denetlemek için veya kritik dosyalarını yedeklemek için kullanabilirsiniz.  
  
## <a name="thread-timer-example"></a>İş parçacığı Zamanlayıcı örneği  
 Aşağıdaki örnek, her iki saniyede bir görev başlatır ve başlatmak için bir bayrak kullanır <xref:System.IDisposable.Dispose%2A> Zamanlayıcı durdurur yöntemi. Bu örnek çıktı penceresine durum gönderir.  
  
```vb  
Private Class StateObjClass  
    ' Used to hold parameters for calls to TimerTask.  
    Public SomeValue As Integer  
    Public TimerReference As System.Threading.Timer  
    Public TimerCanceled As Boolean  
End Class  
  
Public Sub RunTimer()  
    Dim StateObj As New StateObjClass  
    StateObj.TimerCanceled = False  
    StateObj.SomeValue = 1  
    Dim TimerDelegate As New System.Threading.TimerCallback(AddressOf TimerTask)  
    ' Create a timer that calls a procedure every 2 seconds.  
    ' Note: There is no Start method; the timer starts running as soon as   
    ' the instance is created.  
    Dim TimerItem As New System.Threading.Timer(TimerDelegate, StateObj,  
                                                2000, 2000)  
    ' Save a reference for Dispose.  
    StateObj.TimerReference = TimerItem  
  
    ' Run for ten loops.  
    While StateObj.SomeValue < 10  
        ' Wait one second.  
        System.Threading.Thread.Sleep(1000)  
    End While  
  
    ' Request Dispose of the timer object.  
    StateObj.TimerCanceled = True  
End Sub  
  
Private Sub TimerTask(ByVal StateObj As Object)  
    Dim State As StateObjClass = CType(StateObj, StateObjClass)  
    ' Use the interlocked class to increment the counter variable.  
    System.Threading.Interlocked.Increment(State.SomeValue)  
    System.Diagnostics.Debug.WriteLine("Launched new thread  " & Now.ToString)  
    If State.TimerCanceled Then  
        ' Dispose Requested.  
        State.TimerReference.Dispose()  
        System.Diagnostics.Debug.WriteLine("Done  " & Now)  
    End If  
End Sub  
```  
  
 İş parçacığı zamanlayıcıları özellikle yararlı ne zaman <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> nesnesidir konsol uygulamaları zaman geliştirdiğiniz gibi kullanılamaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading>  
 [Birden çok iş parçacıklı uygulamalar (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)
