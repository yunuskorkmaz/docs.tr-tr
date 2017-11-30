---
title: "Zaman uyumsuz dönüş türleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1a62556fb93a3d8547d880e4ea6770b206ead900
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="async-return-types-visual-basic"></a>Zaman uyumsuz dönüş türleri (Visual Basic)
Zaman uyumsuz yöntemleri sahip üç olası dönüş türleri: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>ve void. Visual Basic'te, dönüş türü void olarak yazılmış bir [alt](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) yordamı. Zaman uyumsuz yöntemleri hakkında daha fazla bilgi için bkz: [zaman uyumsuz programlama uyumsuz ve bekleme (Visual Basic) ile](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Her bir dönüş türü aşağıdaki bölümlerde biri incelenir ve konunun sonunda üç kullanan tam bir örnek bulabilirsiniz.  
  
> [!NOTE]
>  Örneği çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınızda yüklü olmalıdır.  
  
##  <a name="BKMK_TaskTReturnType"></a>Task(T) dönüş türü  
 <xref:System.Threading.Tasks.Task%601> Dönüş türü içeren bir zaman uyumsuz yöntem için kullanılan bir [dönmek](../../../../visual-basic/language-reference/statements/return-statement.md) işleneni türüne sahip deyimi `TResult`.  
  
 Aşağıdaki örnekte, `TaskOfT_MethodAsync` async yöntemi bir tamsayı döndürür bir dönüş ifadesi içeriyor. Bu nedenle, yöntem bildirimi dönüş türünü belirtmeniz gerekir `Task(Of Integer)`.  
  
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
  
 Zaman `TaskOfT_MethodAsync` çağrılır bir bekleme ifade içinde bekleme ifade tamsayı değerini alır (değerini `leisureHours`) tarafından döndürülen görev depolanan `TaskOfT_MethodAsync`. Hakkında daha fazla bilgi için ifadeleri await, bkz: [Await işleci](../../../../visual-basic/language-reference/operators/await-operator.md).  
  
 Aşağıdaki kod çağırır ve yöntem bekler `TaskOfT_MethodAsync`. Sonuç atandığı `result1` değişkeni.  
  
```vb  
' Call and await the Task(Of T)-returning async method in the same statement.  
Dim result1 As Integer = Await TaskOfT_MethodAsync()  
```  
  
 Bu çağrı ayırarak nasıl gerçekleştiğini daha iyi anlamak `TaskOfT_MethodAsync` uygulamadan `Await`, aşağıdaki kodda gösterildiği gibi. Yöntemine yapılan bir çağrı `TaskOfT_MethodAsync` hemen beklemenin döndürür değil bir `Task(Of Integer)`yöntemi bildiriminden beklediğiniz gibi. Görev atandığı `integerTask` örnekte değişken. Çünkü `integerTask` olan bir <xref:System.Threading.Tasks.Task%601>, içerdiği bir <xref:System.Threading.Tasks.Task%601.Result> türündeki özelliği `TResult`. Bu durumda, TResult bir tamsayı türünü temsil eder. Zaman `Await` uygulanan `integerTask`, içeriğini bekleme ifadeyi hesaplar <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği `integerTask`. Değer atandığı `result2` değişkeni.  
  
> [!WARNING]
>  <xref:System.Threading.Tasks.Task%601.Result%2A> Özelliği engelleyen bir özelliğidir. Görevini bitmeden önce erişmeyi denerseniz, şu anda etkin olan iş parçacığının görevi tamamlandıktan ve değeri kullanılabilir kadar engellendi. Çoğu durumda, kullanarak değeri erişmelidir `Await` özelliği doğrudan erişimini yerine.  
  
```vb  
' Call and await in separate statements.  
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
' You can do other work that does not rely on resultTask before awaiting.  
textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
Dim result2 As Integer = Await integerTask  
```  
  
 Aşağıdaki kod görüntü deyimlerinde doğrulayın değerlerini `result1` değişkeni, `result2` , değişken ve `Result` özelliği aynıdır. Unutmayın `Result` engelleyen bir özelliktir ve görevini beklemenin önce erişilen döndürmemelidir.  
  
```vb  
' Display the values of the result1 variable, the result2 variable, and  
' the resultTask.Result property.  
textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
```  
  
##  <a name="BKMK_TaskReturnType"></a>Görev dönüş türü  
 Return deyimi içeren yok veya işleneni genellikle döndürmez bir return deyimi içeren zaman uyumsuz yöntemleri dönüş türüne sahip <xref:System.Threading.Tasks.Task>. Bu tür yöntemleri olur [alt](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) eşzamanlı olarak çalışmasına yazılmışsa yordamlar. Kullanırsanız, bir `Task` dönüş türü için bir zaman uyumsuz yöntemi, bir arama yöntemi kullanabilirsiniz bir `Await` çağrılan zaman uyumsuz yöntem tamamlanana kadar arayanın tamamlama askıya almak için işleci.  
  
 Aşağıdaki örnekte, zaman uyumsuz yöntem `Task_MethodAsync` bir dönüş ifadesi içermiyor. Bu nedenle, dönüş türü belirtmek `Task` yönteminde sağlayan `Task_MethodAsync` beklemenin için. Tanımını `Task` türü içermez bir `Result` dönüş değeri depolamak için özellik.  
  
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
  
 `Task_MethodAsync`çağrılan ve arama deyim için bir zaman uyumlu benzer bir bekleme deyim yerine bir bekleme deyimi kullanarak beklemenin `Sub` veya void döndüren yöntemi. Uygulamasının bir `Await` işleci bu durumda bir değer üretmek değil.  
  
 Aşağıdaki kod çağırır ve yöntem bekler `Task_MethodAsync`.  
  
```vb  
' Call and await the Task-returning async method in the same statement.  
Await Task_MethodAsync()  
```  
  
 Önceki gibi <xref:System.Threading.Tasks.Task%601> örnek, çağrısı ayırabilirsiniz `Task_MethodAsync` uygulamadan bir `Await` aşağıdaki gösterildiği gibi kod işleci. Ancak, unutmayın bir `Task` sahip olmayan bir `Result` özelliği ve bekleme operatörün uygulandığında herhangi bir değer üretilir bir `Task`.  
  
 Aşağıdaki kod arama ayıran `Task_MethodAsync` görev bekleyen gelen, `Task_MethodAsync` döndürür.  
  
```vb  
' Call and await in separate statements.  
Dim simpleTask As Task = Task_MethodAsync()  
  
' You can do other work that does not rely on simpleTask before awaiting.  
textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
Await simpleTask  
```  
  
##  <a name="BKMK_VoidReturnType"></a>Dönüş türü void  
 Birincil kullanımını `Sub` yordamları olan olay işleyicileri ile söz konusu olduğunda (diğer dillerdeki dönüş türü void olarak adlandırılır) bir dönüş türü. Void dönüş void döndüren yöntemleri geçersiz kılmak için de kullanılabilir veya kategorilere ayrılabilir etkinliklerini gerçekleştiren yöntemleri için farklı "yangın ve unuttunuz." Ancak, döndürmelidir bir `Task` mümkün olduğunda, bir geçersiz kılma döndüren zaman uyumsuz yöntem beklemenin olduğundan. Böyle bir yöntemin herhangi bir çağırıcı tamamlanması için çağrılan zaman uyumsuz yöntemi beklemeden tamamlanıncaya kadar devam edebilirsiniz ve çağıranın tüm değerleri veya zaman uyumsuz yöntem oluşturur özel durumlar bağımsız olması gerekir.  
  
 Bir geçersiz kılma döndüren zaman uyumsuz yöntem arayan yönteminden oluşturulan özel durumları yakalamak olamaz ve böyle işlenmeyen özel durumlar, uygulamanızın başarısız olmasına yol açabilir. Bir özel durum döndüren bir zaman uyumsuz yöntem oluşursa bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>, özel durum döndürülen görevde depolanır ve görev beklemenin zaman işlenemezse. Bu nedenle, bir özel durum oluşturmak üzere herhangi bir zaman uyumsuz yöntemi dönüş türüne sahip olduğundan emin olun <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> ve yöntemine yönelik çağrılar beklemenin.  
  
 Zaman uyumsuz yöntemleri özel durumlarını yakalama hakkında daha fazla bilgi için bkz: [deneyin... Catch... Finally ifadesi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Aşağıdaki kod bir zaman uyumsuz olay işleyicisini tanımlar.  
  
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
  
##  <a name="BKMK_Example"></a>Tam örnek  
 Aşağıdaki Windows Presentation Foundation (WPF) projesi, bu konudaki kod örnekleri içerir.  
  
 Projeyi çalıştırmak için aşağıdaki adımları gerçekleştirin:  
  
1.  Visual Studio'yu başlatın.  
  
2.  Menü çubuğunda seçin **dosya**, **yeni**, **proje**.  
  
     **Yeni proje** iletişim kutusu açılır.  
  
3.  İçinde **yüklü**, **şablonları** kategorisi seçin **Visual Basic**ve ardından **Windows**. Seçin **WPF uygulaması** proje türleri listesinden.  
  
4.  Girin `AsyncReturnTypes` projesinin adı olarak ve ardından **Tamam** düğmesi.  
  
     Yeni Proje görünür **Çözüm Gezgini**.  
  
5.  Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.  
  
     Sekme görünür durumda değilse, kısayol menüsünde MainWindow.xaml içinde açık **Çözüm Gezgini**ve ardından **açmak**.  
  
6.  İçinde **XAML** MainWindow.xaml, pencerenin kodu aşağıdaki kodla değiştirin.  
  
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
  
     Bir düğmeyi ve bir metin kutusu içeren basit bir pencere görünür **tasarım** MainWindow.xaml penceresi.  
  
7.  İçinde **Çözüm Gezgini**MainWindow.xaml.vb için kısayol menüsünü açın ve ardından **görünümü kodu**.  
  
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
  
9. Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.  
  
     Şu çıktı görünür.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Tasks.Task.FromResult%2A>  
 [İzlenecek yol: Async kullanarak Web'e erişme ve bekleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [(Visual Basic) zaman uyumsuz programlarda denetim akışı](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)  
 [Zaman uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md)  
 [Await işleci](../../../../visual-basic/language-reference/operators/await-operator.md)
