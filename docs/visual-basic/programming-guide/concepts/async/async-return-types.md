---
title: Zaman uyumsuz dönüş türleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: 7a8bc3ba98da830c8415284771460a25e0927895
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838358"
---
# <a name="async-return-types-visual-basic"></a>Zaman uyumsuz dönüş türleri (Visual Basic)
Zaman uyumsuz yöntemler üç olası dönüş türüne sahiptir: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>ve void. Visual Basic'te, void dönüş türü olarak yazılmış bir [alt](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) yordamı. Zaman uyumsuz yöntemler hakkında daha fazla bilgi için bkz. [Async ve Await ile Zaman Uyumsuz Programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Her dönüş türü aşağıdaki bölümlerden birinde incelenir ve konunun sonunda üç türü kullanan bir tam örnek bulabilirsiniz.  
  
> [!NOTE]
>  Yeni bilgisayarınızda yüklü veya örneği çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.  
  
## <a name="BKMK_TaskTReturnType"></a> Görev(t) dönüş türü  
 <xref:System.Threading.Tasks.Task%601> Dönüş türü içeren zaman uyumsuz yöntemi için kullanılan bir [dönüş](../../../../visual-basic/language-reference/statements/return-statement.md) işlenen türü içeren ifadesi `TResult`.  
  
 Aşağıdaki örnekte, `TaskOfT_MethodAsync` zaman uyumsuz yönteminde tamsayı döndüren bir return deyimi içerir. Bu nedenle, yöntem bildiriminde bir dönüş türü belirtmelisiniz `Task(Of Integer)`.  
  
```vb  
' TASK(OF T) EXAMPLE  
Async Function TaskOfT_MethodAsync() As Task(Of Integer)  
  
    ' The body of an async method is expected to contain an awaited   
    ' asynchronous call.  
    ' Task.FromResult is a placeholder for actual work that returns a string.  
    Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())  
  
    ' The method then can process the result in some way.  
    Dim leisureHours As Integer  
    If today.First() = "S" Then  
        leisureHours = 16  
    Else  
        leisureHours = 5  
    End If  
  
    ' Because the return statement specifies an operand of type Integer, the   
    ' method must have a return type of Task(Of Integer).   
    Return leisureHours  
End Function  
```  
  
 Zaman `TaskOfT_MethodAsync` çağrılır bir await ifadesi içinde await ifadesi tamsayı değerini alır (değerini `leisureHours`) tarafından döndürülen görev depolanan `TaskOfT_MethodAsync`. Hakkında daha fazla bilgi için await ifadeleri, bkz: [Await işleci](../../../../visual-basic/language-reference/operators/await-operator.md).  
  
 Aşağıdaki kodu çağırır ve yöntem bekler `TaskOfT_MethodAsync`. Sonuç atandığı `result1` değişkeni.  
  
```vb  
' Call and await the Task(Of T)-returning async method in the same statement.  
Dim result1 As Integer = Await TaskOfT_MethodAsync()  
```  
  
 Çağrı ayırarak nasıl böyle daha iyi anlamak `TaskOfT_MethodAsync` uygulamasından `Await`aşağıdaki kodda gösterildiği gibi. Yöntemine yapılan bir çağrı `TaskOfT_MethodAsync` hemen beklenmeyen döndürür, değilse bir `Task(Of Integer)`, yöntem bildiriminden beklediğiniz gibi. Görevin atandığı `integerTask` örnekte değişken. Çünkü `integerTask` olduğu bir <xref:System.Threading.Tasks.Task%601>, içerdiği bir <xref:System.Threading.Tasks.Task%601.Result> türünün özelliği `TResult`. Bu durumda, TResult bir tamsayı türünü temsil eder. Zaman `Await` uygulanan `integerTask`, bekleme ifadesi içeriğine göre değerlendirilir <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği `integerTask`. Değeri atanır `result2` değişkeni.  
  
> [!WARNING]
>  <xref:System.Threading.Tasks.Task%601.Result%2A> Özelliği engelleyici bir özelliktir. Kendi görevi bitmeden önce buna erişmeyi denerseniz, şu anda etkin olan iş parçacığı değeri kullanılabilir ve görev tamamlanıncaya kadar engellenir. Çoğu durumda, değeri kullanarak erişmeli `Await` özelliği doğrudan erişmek yerine.  
  
```vb  
' Call and await in separate statements.  
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
' You can do other work that does not rely on resultTask before awaiting.  
textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
Dim result2 As Integer = Await integerTask  
```  
  
 Aşağıdaki kodda yer alan görüntü deyimleri doğrulayın değerlerini `result1` değişken `result2` değişken ve `Result` özelliği aynıdır. Unutmayın `Result` engelleyici bir özelliktir ve görevi beklenmeden önce erişilmemesi.  
  
```vb  
' Display the values of the result1 variable, the result2 variable, and  
' the resultTask.Result property.  
textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
```  
  
## <a name="BKMK_TaskReturnType"></a> Görev dönüş türü  
 Return deyimi içermeyen veya bir işleç genellikle döndürmeyen bir return deyimi içeren zaman uyumsuz yöntemlerin dönüş türüne sahip <xref:System.Threading.Tasks.Task>. Bu tür yöntemler olacaktır [alt](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) eşzamanlı çalışacak biçimde yazılmışsa yordamları. Kullanıyorsanız bir `Task` dönüş türü için zaman uyumsuz yöntemi çağıran bir yöntemi kullanabilirsiniz bir `Await` çağrılan zaman uyumsuz yöntemi bitene kadar çağıranın tamamlanmasını bekletmek için işleci.  
  
 Aşağıdaki örnekte, zaman uyumsuz yöntem `Task_MethodAsync` bir return deyimi yok. Bu nedenle, dönüş türü belirttiğiniz `Task` sağlayan yöntem için `Task_MethodAsync` beklenmesini. Tanımı `Task` türü içermez bir `Result` dönüş değerini depolamak için özellik.  
  
```vb  
' TASK EXAMPLE  
Async Function Task_MethodAsync() As Task  
  
    ' The body of an async method is expected to contain an awaited   
    ' asynchronous call.  
    ' Task.Delay is a placeholder for actual work.  
    Await Task.Delay(2000)  
    textBox1.Text &= String.Format(vbCrLf & "Sorry for the delay. . . ." & vbCrLf)  
  
    ' This method has no return statement, so its return type is Task.   
End Function  
```  
  
 `Task_MethodAsync` çağrılan ve bir zaman uyumlu için çağırma deyimine benzer bir await ifadesi yerine await deyimi kullanılarak bekleniyor `Sub` veya void döndüren yöntem. Uygulamayı bir `Await` işleci Bu örnekte bir değer üreten değil.  
  
 Aşağıdaki kodu çağırır ve yöntem bekler `Task_MethodAsync`.  
  
```vb  
' Call and await the Task-returning async method in the same statement.  
Await Task_MethodAsync()  
```  
  
 Önceki olduğu gibi <xref:System.Threading.Tasks.Task%601> örnek, çağrı ayırabilirsiniz `Task_MethodAsync` uygulamasından bir `Await` işleci, aşağıdaki kodun gösterdiği olarak. Ancak, unutmayın bir `Task` sahip olmayan bir `Result` özelliği ve bir await işleci uygulandığında, değer üretilmediğini bir `Task`.  
  
 Aşağıdaki kod ayırır `Task_MethodAsync` görevi bekleme işleminden, `Task_MethodAsync` döndürür.  
  
```vb  
' Call and await in separate statements.  
Dim simpleTask As Task = Task_MethodAsync()  
  
' You can do other work that does not rely on simpleTask before awaiting.  
textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
Await simpleTask  
```  
  
## <a name="BKMK_VoidReturnType"></a> Void dönüş türü  
 Birincil kullanım alanının `Sub` yordamları, olay işleyicileri olan (diğer dillerdeki void dönüş türü olarak adlandırılır) herhangi bir döndürme türü olduğu. Void dönüş void döndüren yöntemleri geçersiz kılmak için de kullanılabilir veya kategorilere ayrılabilir etkinlikleri gerçekleştiren yöntemler için olarak "Başlat ve unut." Ancak, döndürmelidir bir `Task` mümkün olduğunda, çünkü bir void döndüren zaman uyumsuz yöntem beklenemez. Tüm bu yöntemi çağıran kişi çağrılan zaman uyumsuz yöntemin tamamlanmasını beklemeden tamamlanana kadar devam edebilir ve çağıran zaman uyumsuz yöntemin oluşturduğu özel durumları veya değerlerden bağımsız olmalıdır.  
  
 Void döndüren zaman uyumsuz yöntemi çağıran kişi yöntemden atılan özel durumları yakalayamaz ve böyle işlenmeyen özel durumların, uygulamanızın başarısız olmasına neden olabilecek. Döndüren zaman uyumsuz yöntemde özel durum oluşursa bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>, özel durum getirilen görevde depolanır ve görev beklenirken yeniden atılır. Bu nedenle, bir özel durum oluşturabilecek herhangi bir zaman uyumsuz yöntem dönüş türüne sahip olduğundan emin olun <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> ve yöntemine yönelik çağrılar beklediğinden.  
  
 Zaman uyumsuz yöntemlerde özel durumları yakalama hakkında daha fazla bilgi için bkz. [deneyin... Catch... Finally deyimini](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Aşağıdaki kod, zaman uyumsuz olay işleyicisi tanımlar.  
  
```vb  
' SUB EXAMPLE  
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
  
    textBox1.Clear()  
  
    ' Start the process and await its completion. DriverAsync is a   
    ' Task-returning async method.  
    Await DriverAsync()  
  
    ' Say goodbye.  
    textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."  
End Sub  
```  
  
## <a name="BKMK_Example"></a> Tam örnek  
 Aşağıdaki Windows Presentation Foundation (WPF) projesi bu konudan kod örnekleri içermektedir.  
  
 Projeyi çalıştırmak için aşağıdaki adımları gerçekleştirin:  
  
1.  Visual Studio’yu çalıştırın.  
  
2.  Menü çubuğunda, **dosya**, **yeni**, **proje**.  
  
     **Yeni proje** iletişim kutusu açılır.  
  
3.  İçinde **yüklü**, **şablonları** kategorisi seçin **Visual Basic**ve ardından **Windows**. Seçin **WPF uygulaması** proje türleri listesinden.  
  
4.  Girin `AsyncReturnTypes` projesinin adı olarak seçip **Tamam** düğmesi.  
  
     Yeni Proje görünür **Çözüm Gezgini**.  
  
5.  Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.  
  
     Sekme görünür değilse nde MainWindow.xaml için kısayol menüsünü açın **Çözüm Gezgini**ve ardından **açın**.  
  
6.  İçinde **XAML** MainWindow.xaml penceresinde kodu aşağıdaki kodla değiştirin.  
  
    ```vb  
    <Window x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            Title="MainWindow" Height="350" Width="525">  
        <Grid>  
            <Button x:Name="button1" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="button1_Click"/>  
            <TextBox x:Name="textBox1" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>  
  
        </Grid>  
    </Window>  
    ```  
  
     Bir metin kutusu ve bir düğme içeren basit bir pencere **tasarım** MainWindow.xaml penceresi.  
  
7.  İçinde **Çözüm Gezgini**MainWindow.xaml.vb için kısayol menüsünü açın ve ardından **kodu görüntüle**.  
  
8.  MainWindow.xaml.vb kodu aşağıdaki kodla değiştirin.  
  
    ```vb  
    Class MainWindow  
  
        ' SUB EXAMPLE  
        Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
  
            textBox1.Clear()  
  
            ' Start the process and await its completion. DriverAsync is a   
            ' Task-returning async method.  
            Await DriverAsync()  
  
            ' Say goodbye.  
            textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."  
        End Sub  
  
        Async Function DriverAsync() As Task  
  
            ' Task(Of T)   
            ' Call and await the Task(Of T)-returning async method in the same statement.  
            Dim result1 As Integer = Await TaskOfT_MethodAsync()  
  
            ' Call and await in separate statements.  
            Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
            ' You can do other work that does not rely on resultTask before awaiting.  
            textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
            Dim result2 As Integer = Await integerTask  
  
            ' Display the values of the result1 variable, the result2 variable, and  
            ' the resultTask.Result property.  
            textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
            textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
            textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
  
            ' Task   
            ' Call and await the Task-returning async method in the same statement.  
            Await Task_MethodAsync()  
  
            ' Call and await in separate statements.  
            Dim simpleTask As Task = Task_MethodAsync()  
  
            ' You can do other work that does not rely on simpleTask before awaiting.  
            textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
            Await simpleTask  
        End Function  
  
        ' TASK(OF T) EXAMPLE  
        Async Function TaskOfT_MethodAsync() As Task(Of Integer)  
  
            ' The body of an async method is expected to contain an awaited   
            ' asynchronous call.  
            ' Task.FromResult is a placeholder for actual work that returns a string.  
            Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())  
  
            ' The method then can process the result in some way.  
            Dim leisureHours As Integer  
            If today.First() = "S" Then  
                leisureHours = 16  
            Else  
                leisureHours = 5  
            End If  
  
            ' Because the return statement specifies an operand of type Integer, the   
            ' method must have a return type of Task(Of Integer).   
            Return leisureHours  
        End Function  
  
        ' TASK EXAMPLE  
        Async Function Task_MethodAsync() As Task  
  
            ' The body of an async method is expected to contain an awaited   
            ' asynchronous call.  
            ' Task.Delay is a placeholder for actual work.  
            Await Task.Delay(2000)  
            textBox1.Text &= String.Format(vbCrLf & "Sorry for the delay. . . ." & vbCrLf)  
  
            ' This method has no return statement, so its return type is Task.   
        End Function  
  
    End Class  
    ```  
  
9. Programı çalıştırın ve ardından F5 tuşuna basın **Başlat** düğmesi.  
  
     Aşağıdaki çıktı görünmelidir.  
  
    ```  
    Application can continue working while the Task<T> runs. . . .   
  
    Value of result1 variable:   5  
    Value of result2 variable:   5  
    Value of integerTask.Result: 5  
  
    Sorry for the delay. . . .  
  
    Application can continue working while the Task runs. . . .  
  
    Sorry for the delay. . . .  
  
    All done, exiting button-click event handler.  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [İzlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Zaman uyumsuz programlarda (Visual Basic) denetim akışı](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
- [Await İşleci](../../../../visual-basic/language-reference/operators/await-operator.md)
