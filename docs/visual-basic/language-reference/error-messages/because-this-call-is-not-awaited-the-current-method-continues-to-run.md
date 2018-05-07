---
title: Bu çağrı beklenmediğinden, çağrı tamamlanmadan geçerli yöntemin çalıştırılması devam eder
ms.date: 07/20/2015
f1_keywords:
- bc42358
- vbc42358
helpviewer_keywords:
- BC42358
ms.assetid: 43342515-c3c8-4155-9263-c302afabcbc2
ms.openlocfilehash: 754fc6750e63f6d9f39da94041fc452829bca46d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="because-this-call-is-not-awaited-the-current-method-continues-to-run-before-the-call-is-completed"></a>Bu çağrı beklenmediğinden, çağrı tamamlanmadan geçerli yöntemin çalıştırılması devam eder
Bu çağrı beklenmediğinden, çağrı tamamlanmadan geçerli yöntemin çalıştırılması devam eder. 'Bekleme' işleci çağrı sonucunu uygulamayı düşünün.  
  
 Geçerli yöntemi döndüren bir zaman uyumsuz yöntem çağırır bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> ve uygulanmaz [bekleme](../../../visual-basic/language-reference/operators/await-operator.md) sonucu işleci. Zaman uyumsuz yöntem çağrısı zaman uyumsuz bir görev başlatır. Ancak, çünkü hiçbir `Await` program görevinin tamamlanmasını beklemeden devam işleci uygulanır. Çoğu durumda, bu davranışı beklenen değil. Genellikle diğer yönlerini arama yöntemi arama sonuçlarına bağlı veya, çağrılan yöntemin çağrı içerir yönteminden döndürmeden önce tamamlamak için en azından beklenir.  
  
 Eşit oranda önemli bir sorun çağrılan zaman uyumsuz yöntemde oluşan özel durumlara sahip olur. Döndüren bir yöntemde oluşan bir özel durum bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> döndürülen görevde depolanır. Görev await yok veya açıkça özel durumlar için denetleyin, özel durum kaybolur. Görev await, kendi özel durum işlenemezse.  
  
 En iyi uygulama, her zaman çağrıyı beklemek.  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC42358  
  
### <a name="to-address-this-warning"></a>Bu uyarıyı gidermek için  
  
-   Yalnızca zaman uyumsuz çağrının tamamlanmasını beklemek istemiyorsanız ve çağrılan yöntemin özel durumlar Yükselt olmaz eminseniz, uyarı gizleme göz önünde bulundurmalısınız. Bu durumda, bir değişken çağrısı görev sonucu atayarak uyarı gizleyebilirsiniz.  
  
     Aşağıdaki örnekte nasıl uyarı neden, onu gizlemek nasıl ve çağrı beklemek nasıl gösterir.  
  
    ```vb  
    Async Function CallingMethodAsync() As Task  
  
        ResultsTextBox.Text &= vbCrLf & "  Entering calling method."  
  
        ' Variable delay is used to slow down the called method so that you  
        ' can distinguish between awaiting and not awaiting in the program's output.   
        ' You can adjust the value to produce the output that this topic shows   
        ' after the code.  
        Dim delay = 5000  
  
        ' Call #1.  
        ' Call an async method. Because you don't await it, its completion isn't   
        ' coordinated with the current method, CallingMethodAsync.  
        ' The following line causes the warning.  
        CalledMethodAsync(delay)  
  
        ' Call #2.  
        ' To suppress the warning without awaiting, you can assign the   
        ' returned task to a variable. The assignment doesn't change how  
        ' the program runs. However, the recommended practice is always to  
        ' await a call to an async method.  
        ' Replace Call #1 with the following line.  
        'Task delayTask = CalledMethodAsync(delay)  
  
        ' Call #3  
        ' To contrast with an awaited call, replace the unawaited call   
        ' (Call #1 or Call #2) with the following awaited call. The best   
        ' practice is to await the call.  
  
        'Await CalledMethodAsync(delay)  
  
        ' If the call to CalledMethodAsync isn't awaited, CallingMethodAsync  
        ' continues to run and, in this example, finishes its work and returns  
        ' to its caller.  
        ResultsTextBox.Text &= vbCrLf & "  Returning from calling method."  
    End Function  
  
    Async Function CalledMethodAsync(howLong As Integer) As Task  
  
        ResultsTextBox.Text &= vbCrLf & "    Entering called method, starting and awaiting Task.Delay."  
        ' Slow the process down a little so you can distinguish between awaiting  
        ' and not awaiting. Adjust the value for howLong if necessary.  
        Await Task.Delay(howLong)  
        ResultsTextBox.Text &= vbCrLf & "    Task.Delay is finished--returning from called method."  
    End Function  
    ```  
  
     Örnekte çağrı #1 veya çağrı #2 unawaited async yöntemi seçerseniz, (`CalledMethodAsync`) tamamlandıktan sonra her iki arayan (`CallingMethodAsync`) ve arayanın arayan (`StartButton_Click`) tamamlandığından. Aşağıdaki çıkış son satırında çağrılan Yöntem sonlandığında gösterir. İçin giriş ve çıkış çağırır olay işleyicisinden `CallingMethodAsync` tam örnek çıktıda işaretlenir.  
  
    ```  
    Entering the Click event handler.  
      Entering calling method.  
        Entering called method, starting and awaiting Task.Delay.  
      Returning from calling method.  
    Exiting the Click event handler.  
        Task.Delay is finished--returning from called method.  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Windows Presentation Foundation (WPF) uygulama önceki örnekten yöntemler içerir. Aşağıdaki adımları uygulama ayarlama.  
  
1.  WPF uygulaması oluşturun ve adlandırın `AsyncWarning`.  
  
2.  Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.  
  
     Sekme görünür değilse, kısayol menüsünde MainWindow.xaml içinde açık **Çözüm Gezgini**ve ardından **görünümü kodu**.  
  
3.  Kodla **XAML** MainWindow.xaml görünümünü aşağıdaki kod ile.  
  
    ```vb  
    <Window x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            Title="MainWindow" Height="350" Width="525">  
        <Grid>  
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="StartButton_Click" />  
            <TextBox x:Name="ResultsTextBox" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>  
        </Grid>  
    </Window>  
    ```  
  
     Bir düğme ve bir metin kutusu içeren basit bir pencere görünür **tasarım** MainWindow.xaml görünümü.  
  
     XAML Tasarımcısı hakkında daha fazla bilgi için bkz: [XAML Tasarımcısını kullanarak bir kullanıcı Arabirimi oluşturma](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio). Basit kendi kullanıcı Arabirimi oluşturma hakkında daha fazla bilgi için bkz: "WPF uygulaması oluşturmak için" ve "Basit bir WPF MainWindow tasarlamak için" bölümlerini [izlenecek yol: Web kullanarak zaman uyumsuz ve bekleme tarafından erişme](http://msdn.microsoft.com/library/25879a6d-fdee-4a38-bc98-bb8c24d16042).  
  
4.  MainWindow.xaml.vb kodu aşağıdaki kodla değiştirin.  
  
    ```vb  
    Class MainWindow   
  
        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
  
            ResultsTextBox.Text &= vbCrLf & "Entering the Click event handler."  
            Await CallingMethodAsync()  
            ResultsTextBox.Text &= vbCrLf & "Exiting the Click event handler."  
        End Sub  
  
        Async Function CallingMethodAsync() As Task  
  
            ResultsTextBox.Text &= vbCrLf & "  Entering calling method."  
  
            ' Variable delay is used to slow down the called method so that you  
            ' can distinguish between awaiting and not awaiting in the program's output.   
            ' You can adjust the value to produce the output that this topic shows   
            ' after the code.  
            Dim delay = 5000  
  
            ' Call #1.  
            ' Call an async method. Because you don't await it, its completion isn't   
            ' coordinated with the current method, CallingMethodAsync.  
            ' The following line causes the warning.  
            CalledMethodAsync(delay)  
  
            ' Call #2.  
            ' To suppress the warning without awaiting, you can assign the   
            ' returned task to a variable. The assignment doesn't change how  
            ' the program runs. However, the recommended practice is always to  
            ' await a call to an async method.  
  
            ' Replace Call #1 with the following line.  
            'Task delayTask = CalledMethodAsync(delay)  
  
            ' Call #3  
            ' To contrast with an awaited call, replace the unawaited call   
            ' (Call #1 or Call #2) with the following awaited call. The best   
            ' practice is to await the call.  
  
            'Await CalledMethodAsync(delay)  
  
            ' If the call to CalledMethodAsync isn't awaited, CallingMethodAsync  
            ' continues to run and, in this example, finishes its work and returns  
            ' to its caller.  
            ResultsTextBox.Text &= vbCrLf & "  Returning from calling method."  
        End Function  
  
        Async Function CalledMethodAsync(howLong As Integer) As Task  
  
            ResultsTextBox.Text &= vbCrLf & "    Entering called method, starting and awaiting Task.Delay."  
            ' Slow the process down a little so you can distinguish between awaiting  
            ' and not awaiting. Adjust the value for howLong if necessary.  
            Await Task.Delay(howLong)  
            ResultsTextBox.Text &= vbCrLf & "    Task.Delay is finished--returning from called method."  
        End Function  
  
    End Class  
  
    ' Output  
  
    ' Entering the Click event handler.  
    '   Entering calling method.  
    '     Entering called method, starting and awaiting Task.Delay.  
    '   Returning from calling method.  
    ' Exiting the Click event handler.  
    '     Task.Delay is finished--returning from called method.  
  
    ' Output  
  
    ' Entering the Click event handler.  
    '   Entering calling method.  
    '     Entering called method, starting and awaiting Task.Delay.  
    '     Task.Delay is finished--returning from called method.  
    '   Returning from calling method.  
    ' Exiting the Click event handler.  
    ```  
  
5.  Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.  
  
     Beklenen çıkış kodu sonunda görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Await İşleci](../../../visual-basic/language-reference/operators/await-operator.md)  
 [Async ve Await ile Zaman Uyumsuz Programlama](../../../visual-basic/programming-guide/concepts/async/index.md)
