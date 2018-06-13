---
title: BackgroundWorker bileşeni (Visual Basic) ile çoklu iş parçacığı kullanımı
ms.date: 07/20/2015
ms.assetid: e4cd9b2a-f924-470e-a16e-50274709b40e
ms.openlocfilehash: 07700aa526866729f1ba1a8d846f22ce333c356d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654297"
---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-visual-basic"></a>İzlenecek yol: BackgroundWorker bileşeni (Visual Basic) ile çoklu iş parçacığı kullanımı
Bu kılavuz bir metin dosyası için bir sözcük oluşumları arar birden çok iş parçacıklı bir Windows Forms uygulamasının nasıl oluşturulacağını gösterir. Bunu gösterir:  
  
-   Bir sınıf tarafından çağrılabilir bir yöntem tanımlama <xref:System.ComponentModel.BackgroundWorker> bileşeni.  
  
-   Tarafından oluşturulan olayları işleme <xref:System.ComponentModel.BackgroundWorker> bileşeni.  
  
-   Başlangıç bir <xref:System.ComponentModel.BackgroundWorker> bir yöntem çalıştırmak için bileşen.  
  
-   Uygulama bir `Cancel` durdurur düğmesi <xref:System.ComponentModel.BackgroundWorker> bileşeni.  
  
### <a name="to-create-the-user-interface"></a>Kullanıcı arabirimini oluşturmak için  
  
1.  Yeni bir Visual Basic Windows Forms uygulaması projesi açın ve adlı bir form oluşturun `Form1`.  
  
2.  İki düğme ve dört metin kutusu ekleyin `Form1`.  
  
3.  Aşağıdaki tabloda gösterildiği gibi nesneleri adlandırın.  
  
    |Nesne|Özellik|Ayar|  
    |------------|--------------|-------------|  
    |İlk düğmesi|`Name`, `Text`|Başlangıç, Başlat|  
    |İkinci düğmesi|`Name`, `Text`|İptal, iptal|  
    |İlk metin kutusu|`Name`, `Text`|SourceFile, ""|  
    |İkinci metin kutusu|`Name`, `Text`|CompareString, ""|  
    |Üçüncü metin kutusu|`Name`, `Text`|WordsCounted, "0"|  
    |Dördüncü metin kutusu|`Name`, `Text`|LinesCounted, "0"|  
  
4.  Her metin kutusunun yanında bir etiket ekleyin. Ayarlama `Text` özelliği aşağıdaki tabloda gösterildiği gibi her bir etiket için.  
  
    |Nesne|Özellik|Ayar|  
    |------------|--------------|-------------|  
    |İlk etiketi|`Text`|Kaynak dosya|  
    |İkinci etiketi|`Text`|Dize karşılaştırma|  
    |Üçüncü etiketi|`Text`|Eşleşen sözcükleri|  
    |Dördüncü etiketi|`Text`|Sayılan satırları|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a>BackgroundWorker bileşeni oluşturma ve onun olaylarına abone olma  
  
1.  Ekleme bir <xref:System.ComponentModel.BackgroundWorker> gelen bileşen **bileşenleri** bölümünü **araç** form. Formun bileşen tepsisinde görünür.  
  
2.  BackgroundWorker1 nesnesi için aşağıdaki özellikleri ayarlayın.  
  
    |Özellik|Ayar|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|Doğru|  
    |`WorkerSupportsCancellation`|Doğru|  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a>Ayrı bir iş parçacığı üzerinde çalışacak yöntemi tanımlamak için  
  
1.  Gelen **proje** menüsünde seçin **sınıfı Ekle** projeye bir sınıf eklemek için. **Yeni Öğe Ekle** iletişim kutusu görüntülenir.  
  
2.  Seçin **sınıfı** şablonları penceresinden ve girin `Words.vb` ad alanında.  
  
3.  **Ekle**'yi tıklatın. `Words` Sınıfı görüntülenir.  
  
4.  Aşağıdaki kodu ekleyin `Words` sınıfı:  
  
    ```vb  
    Public Class Words  
        ' Object to store the current state, for passing to the caller.  
        Public Class CurrentState  
            Public LinesCounted As Integer  
            Public WordsMatched As Integer  
        End Class  
  
        Public SourceFile As String  
        Public CompareString As String  
        Private WordCount As Integer = 0  
        Private LinesCounted As Integer = 0  
  
        Public Sub CountWords(  
            ByVal worker As System.ComponentModel.BackgroundWorker,  
            ByVal e As System.ComponentModel.DoWorkEventArgs  
        )  
            ' Initialize the variables.  
            Dim state As New CurrentState  
            Dim line = ""  
            Dim elapsedTime = 20  
            Dim lastReportDateTime = Now  
  
            If CompareString Is Nothing OrElse  
               CompareString = System.String.Empty Then  
  
               Throw New Exception("CompareString not specified.")  
            End If  
  
            Using myStream As New System.IO.StreamReader(SourceFile)  
  
                ' Process lines while there are lines remaining in the file.  
                Do While Not myStream.EndOfStream  
                    If worker.CancellationPending Then  
                        e.Cancel = True  
                        Exit Do  
                    Else  
                        line = myStream.ReadLine  
                        WordCount += CountInString(line, CompareString)  
                        LinesCounted += 1  
  
                        ' Raise an event so the form can monitor progress.  
                        If Now > lastReportDateTime.AddMilliseconds(elapsedTime) Then  
                            state.LinesCounted = LinesCounted  
                            state.WordsMatched = WordCount  
                            worker.ReportProgress(0, state)  
                            lastReportDateTime = Now  
                        End If  
  
                        ' Uncomment for testing.  
                        'System.Threading.Thread.Sleep(5)  
                    End If  
                Loop  
  
                ' Report the final count values.  
                state.LinesCounted = LinesCounted  
                state.WordsMatched = WordCount  
                worker.ReportProgress(0, state)  
            End Using  
        End Sub  
  
        Private Function CountInString(  
            ByVal SourceString As String,  
            ByVal CompareString As String  
        ) As Integer  
            ' This function counts the number of times  
            ' a word is found in a line.  
            If SourceString Is Nothing Then  
                Return 0  
            End If  
  
            Dim EscapedCompareString =  
                System.Text.RegularExpressions.Regex.Escape(CompareString)  
  
            ' To count all occurrences of the string, even within words, remove  
            ' both instances of "\b".  
            Dim regex As New System.Text.RegularExpressions.Regex(  
                "\b" + EscapedCompareString + "\b",  
                System.Text.RegularExpressions.RegexOptions.IgnoreCase)  
  
            Dim matches As System.Text.RegularExpressions.MatchCollection  
            matches = regex.Matches(SourceString)  
            Return matches.Count  
        End Function  
    End Class  
    ```  
  
### <a name="to-handle-events-from-the-thread"></a>İş parçacığı olayları işlemek için  
  
-   Aşağıdaki olay işleyicileri için ana form ekleyin:  
  
    ```vb  
    Private Sub BackgroundWorker1_RunWorkerCompleted(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.RunWorkerCompletedEventArgs  
      ) Handles BackgroundWorker1.RunWorkerCompleted  
  
        ' This event handler is called when the background thread finishes.  
        ' This method runs on the main thread.  
        If e.Error IsNot Nothing Then  
            MessageBox.Show("Error: " & e.Error.Message)  
        ElseIf e.Cancelled Then  
            MessageBox.Show("Word counting canceled.")  
        Else  
            MessageBox.Show("Finished counting words.")  
        End If  
    End Sub  
  
    Private Sub BackgroundWorker1_ProgressChanged(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.ProgressChangedEventArgs  
      ) Handles BackgroundWorker1.ProgressChanged  
  
        ' This method runs on the main thread.  
        Dim state As Words.CurrentState =   
            CType(e.UserState, Words.CurrentState)  
        Me.LinesCounted.Text = state.LinesCounted.ToString  
        Me.WordsCounted.Text = state.WordsMatched.ToString  
    End Sub  
    ```  
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a>WordCount yöntemi çalıştıran Başlat ve yeni bir iş parçacığı çağırmak için  
  
1.  Aşağıdaki yordamlar programınıza ekleyin:  
  
    ```vb  
    Private Sub BackgroundWorker1_DoWork(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.DoWorkEventArgs  
      ) Handles BackgroundWorker1.DoWork  
  
        ' This event handler is where the actual work is done.  
        ' This method runs on the background thread.  
  
        ' Get the BackgroundWorker object that raised this event.  
        Dim worker As System.ComponentModel.BackgroundWorker  
        worker = CType(sender, System.ComponentModel.BackgroundWorker)  
  
        ' Get the Words object and call the main method.  
        Dim WC As Words = CType(e.Argument, Words)  
        WC.CountWords(worker, e)  
    End Sub  
  
    Sub StartThread()  
        ' This method runs on the main thread.  
        Me.WordsCounted.Text = "0"  
  
        ' Initialize the object that the background worker calls.  
        Dim WC As New Words  
        WC.CompareString = Me.CompareString.Text  
        WC.SourceFile = Me.SourceFile.Text  
  
        ' Start the asynchronous operation.  
        BackgroundWorker1.RunWorkerAsync(WC)  
    End Sub  
    ```  
  
2.  Çağrı `StartThread` yönteminden `Start` formunuzda düğmesini:  
  
    ```vb  
    Private Sub Start_Click() Handles Start.Click  
        StartThread()  
    End Sub  
    ```  
  
### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a>İş parçacığı durdurur iptal düğmesi uygulamak için  
  
-   Çağrı `StopThread` yordamdan `Click` için olay işleyicisini `Cancel` düğmesi.  
  
    ```vb  
    Private Sub Cancel_Click() Handles Cancel.Click  
        ' Cancel the asynchronous operation.  
        Me.BackgroundWorker1.CancelAsync()  
    End Sub  
    ```  
  
## <a name="testing"></a>Sınama  
 Artık doğru çalıştığından emin olmak için uygulamayı test edebilirsiniz.  
  
#### <a name="to-test-the-application"></a>Uygulamayı test etmek için  
  
1.  Uygulamayı çalıştırmak için F5 tuşuna basın.  
  
2.  Form görüntülendiğinde, test istediğiniz dosya için dosya yolu girin `sourceFile` kutusu. Örneğin, test dosyanız sınama.txt adlı varsayıldığında, C:\Test.txt girin.  
  
3.  İkinci metin kutusuna bir sözcük veya tümcecik metin dosyasında aramak uygulamanın girin.  
  
4.  Tıklatın `Start` düğmesi. `LinesCounted` Düğmesi hemen artırma başlamalıdır. Bu işlem sona erdiğinde uygulama "sayım tamamlandı" iletisi görüntüler.  
  
#### <a name="to-test-the-cancel-button"></a>İptal düğmesi sınamak için  
  
1.  Uygulama başlatma ve önceki yordamda açıklandığı gibi dosya adını ve arama sözcüğü girin için F5 tuşuna basın. Seçtiğiniz dosya tamamlanmadan önce yordamı iptal etmek için zaman sahip emin olmak için yeterince büyük olduğundan emin olun.  
  
2.  Tıklatın `Start` uygulamayı başlatmak için düğmesi.  
  
3.  Tıklatın `Cancel` düğmesi. Uygulama hemen sayım durdurmanız gerekir.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu uygulama, bazı temel hata işleme içerir. Boş arama dizelerini algılar. Sözcükleri veya sayılamaz satır sayısını aşan gibi diğer hataları işleyerek bu programı daha sağlam yapabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş parçacığı oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [İzlenecek yol: Visual Basic ile basit bir birden çok iş parçacıklı bileşen yazma](http://msdn.microsoft.com/library/05693b70-3566-4d91-9f2c-c9bc4ccb3001)  
 [Nasıl yapılır: Olaylara Abone Olma ve Aboneliği Kaldırma](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
