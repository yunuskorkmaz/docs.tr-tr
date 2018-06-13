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
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-visual-basic"></a><span data-ttu-id="271d4-102">İzlenecek yol: BackgroundWorker bileşeni (Visual Basic) ile çoklu iş parçacığı kullanımı</span><span class="sxs-lookup"><span data-stu-id="271d4-102">Walkthrough: Multithreading with the BackgroundWorker Component (Visual Basic)</span></span>
<span data-ttu-id="271d4-103">Bu kılavuz bir metin dosyası için bir sözcük oluşumları arar birden çok iş parçacıklı bir Windows Forms uygulamasının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="271d4-103">This walkthrough demonstrates how to create a multithreaded Windows Forms application that searches a text file for occurrences of a word.</span></span> <span data-ttu-id="271d4-104">Bunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="271d4-104">It demonstrates:</span></span>  
  
-   <span data-ttu-id="271d4-105">Bir sınıf tarafından çağrılabilir bir yöntem tanımlama <xref:System.ComponentModel.BackgroundWorker> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="271d4-105">Defining a class with a method that can be called by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="271d4-106">Tarafından oluşturulan olayları işleme <xref:System.ComponentModel.BackgroundWorker> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="271d4-106">Handling events raised by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="271d4-107">Başlangıç bir <xref:System.ComponentModel.BackgroundWorker> bir yöntem çalıştırmak için bileşen.</span><span class="sxs-lookup"><span data-stu-id="271d4-107">Starting a <xref:System.ComponentModel.BackgroundWorker> component to run a method.</span></span>  
  
-   <span data-ttu-id="271d4-108">Uygulama bir `Cancel` durdurur düğmesi <xref:System.ComponentModel.BackgroundWorker> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="271d4-108">Implementing a `Cancel` button that stops the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="271d4-109">Kullanıcı arabirimini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="271d4-109">To create the user interface</span></span>  
  
1.  <span data-ttu-id="271d4-110">Yeni bir Visual Basic Windows Forms uygulaması projesi açın ve adlı bir form oluşturun `Form1`.</span><span class="sxs-lookup"><span data-stu-id="271d4-110">Open a new Visual Basic Windows Forms Application project, and create a form named `Form1`.</span></span>  
  
2.  <span data-ttu-id="271d4-111">İki düğme ve dört metin kutusu ekleyin `Form1`.</span><span class="sxs-lookup"><span data-stu-id="271d4-111">Add two buttons and four text boxes to `Form1`.</span></span>  
  
3.  <span data-ttu-id="271d4-112">Aşağıdaki tabloda gösterildiği gibi nesneleri adlandırın.</span><span class="sxs-lookup"><span data-stu-id="271d4-112">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="271d4-113">Nesne</span><span class="sxs-lookup"><span data-stu-id="271d4-113">Object</span></span>|<span data-ttu-id="271d4-114">Özellik</span><span class="sxs-lookup"><span data-stu-id="271d4-114">Property</span></span>|<span data-ttu-id="271d4-115">Ayar</span><span class="sxs-lookup"><span data-stu-id="271d4-115">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="271d4-116">İlk düğmesi</span><span class="sxs-lookup"><span data-stu-id="271d4-116">First button</span></span>|<span data-ttu-id="271d4-117">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="271d4-117">`Name`, `Text`</span></span>|<span data-ttu-id="271d4-118">Başlangıç, Başlat</span><span class="sxs-lookup"><span data-stu-id="271d4-118">Start, Start</span></span>|  
    |<span data-ttu-id="271d4-119">İkinci düğmesi</span><span class="sxs-lookup"><span data-stu-id="271d4-119">Second button</span></span>|<span data-ttu-id="271d4-120">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="271d4-120">`Name`, `Text`</span></span>|<span data-ttu-id="271d4-121">İptal, iptal</span><span class="sxs-lookup"><span data-stu-id="271d4-121">Cancel, Cancel</span></span>|  
    |<span data-ttu-id="271d4-122">İlk metin kutusu</span><span class="sxs-lookup"><span data-stu-id="271d4-122">First text box</span></span>|<span data-ttu-id="271d4-123">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="271d4-123">`Name`, `Text`</span></span>|<span data-ttu-id="271d4-124">SourceFile, ""</span><span class="sxs-lookup"><span data-stu-id="271d4-124">SourceFile, ""</span></span>|  
    |<span data-ttu-id="271d4-125">İkinci metin kutusu</span><span class="sxs-lookup"><span data-stu-id="271d4-125">Second text box</span></span>|<span data-ttu-id="271d4-126">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="271d4-126">`Name`, `Text`</span></span>|<span data-ttu-id="271d4-127">CompareString, ""</span><span class="sxs-lookup"><span data-stu-id="271d4-127">CompareString, ""</span></span>|  
    |<span data-ttu-id="271d4-128">Üçüncü metin kutusu</span><span class="sxs-lookup"><span data-stu-id="271d4-128">Third text box</span></span>|<span data-ttu-id="271d4-129">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="271d4-129">`Name`, `Text`</span></span>|<span data-ttu-id="271d4-130">WordsCounted, "0"</span><span class="sxs-lookup"><span data-stu-id="271d4-130">WordsCounted, "0"</span></span>|  
    |<span data-ttu-id="271d4-131">Dördüncü metin kutusu</span><span class="sxs-lookup"><span data-stu-id="271d4-131">Fourth text box</span></span>|<span data-ttu-id="271d4-132">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="271d4-132">`Name`, `Text`</span></span>|<span data-ttu-id="271d4-133">LinesCounted, "0"</span><span class="sxs-lookup"><span data-stu-id="271d4-133">LinesCounted, "0"</span></span>|  
  
4.  <span data-ttu-id="271d4-134">Her metin kutusunun yanında bir etiket ekleyin.</span><span class="sxs-lookup"><span data-stu-id="271d4-134">Add a label next to each text box.</span></span> <span data-ttu-id="271d4-135">Ayarlama `Text` özelliği aşağıdaki tabloda gösterildiği gibi her bir etiket için.</span><span class="sxs-lookup"><span data-stu-id="271d4-135">Set the `Text` property for each label as shown in the following table.</span></span>  
  
    |<span data-ttu-id="271d4-136">Nesne</span><span class="sxs-lookup"><span data-stu-id="271d4-136">Object</span></span>|<span data-ttu-id="271d4-137">Özellik</span><span class="sxs-lookup"><span data-stu-id="271d4-137">Property</span></span>|<span data-ttu-id="271d4-138">Ayar</span><span class="sxs-lookup"><span data-stu-id="271d4-138">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="271d4-139">İlk etiketi</span><span class="sxs-lookup"><span data-stu-id="271d4-139">First label</span></span>|`Text`|<span data-ttu-id="271d4-140">Kaynak dosya</span><span class="sxs-lookup"><span data-stu-id="271d4-140">Source File</span></span>|  
    |<span data-ttu-id="271d4-141">İkinci etiketi</span><span class="sxs-lookup"><span data-stu-id="271d4-141">Second label</span></span>|`Text`|<span data-ttu-id="271d4-142">Dize karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="271d4-142">Compare String</span></span>|  
    |<span data-ttu-id="271d4-143">Üçüncü etiketi</span><span class="sxs-lookup"><span data-stu-id="271d4-143">Third label</span></span>|`Text`|<span data-ttu-id="271d4-144">Eşleşen sözcükleri</span><span class="sxs-lookup"><span data-stu-id="271d4-144">Matching Words</span></span>|  
    |<span data-ttu-id="271d4-145">Dördüncü etiketi</span><span class="sxs-lookup"><span data-stu-id="271d4-145">Fourth label</span></span>|`Text`|<span data-ttu-id="271d4-146">Sayılan satırları</span><span class="sxs-lookup"><span data-stu-id="271d4-146">Lines Counted</span></span>|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a><span data-ttu-id="271d4-147">BackgroundWorker bileşeni oluşturma ve onun olaylarına abone olma</span><span class="sxs-lookup"><span data-stu-id="271d4-147">To create a BackgroundWorker component and subscribe to its events</span></span>  
  
1.  <span data-ttu-id="271d4-148">Ekleme bir <xref:System.ComponentModel.BackgroundWorker> gelen bileşen **bileşenleri** bölümünü **araç** form.</span><span class="sxs-lookup"><span data-stu-id="271d4-148">Add a <xref:System.ComponentModel.BackgroundWorker> component from the **Components** section of the **ToolBox** to the form.</span></span> <span data-ttu-id="271d4-149">Formun bileşen tepsisinde görünür.</span><span class="sxs-lookup"><span data-stu-id="271d4-149">It will appear in the form's component tray.</span></span>  
  
2.  <span data-ttu-id="271d4-150">BackgroundWorker1 nesnesi için aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="271d4-150">Set the following properties for the BackgroundWorker1 object.</span></span>  
  
    |<span data-ttu-id="271d4-151">Özellik</span><span class="sxs-lookup"><span data-stu-id="271d4-151">Property</span></span>|<span data-ttu-id="271d4-152">Ayar</span><span class="sxs-lookup"><span data-stu-id="271d4-152">Setting</span></span>|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|<span data-ttu-id="271d4-153">Doğru</span><span class="sxs-lookup"><span data-stu-id="271d4-153">True</span></span>|  
    |`WorkerSupportsCancellation`|<span data-ttu-id="271d4-154">Doğru</span><span class="sxs-lookup"><span data-stu-id="271d4-154">True</span></span>|  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a><span data-ttu-id="271d4-155">Ayrı bir iş parçacığı üzerinde çalışacak yöntemi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="271d4-155">To define the method that will run on a separate thread</span></span>  
  
1.  <span data-ttu-id="271d4-156">Gelen **proje** menüsünde seçin **sınıfı Ekle** projeye bir sınıf eklemek için.</span><span class="sxs-lookup"><span data-stu-id="271d4-156">From the **Project** menu, choose **Add Class** to add a class to the project.</span></span> <span data-ttu-id="271d4-157">**Yeni Öğe Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="271d4-157">The **Add New Item** dialog box is displayed.</span></span>  
  
2.  <span data-ttu-id="271d4-158">Seçin **sınıfı** şablonları penceresinden ve girin `Words.vb` ad alanında.</span><span class="sxs-lookup"><span data-stu-id="271d4-158">Select **Class** from the templates window and enter `Words.vb` in the name field.</span></span>  
  
3.  <span data-ttu-id="271d4-159">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="271d4-159">Click **Add**.</span></span> <span data-ttu-id="271d4-160">`Words` Sınıfı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="271d4-160">The `Words` class is displayed.</span></span>  
  
4.  <span data-ttu-id="271d4-161">Aşağıdaki kodu ekleyin `Words` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="271d4-161">Add the following code to the `Words` class:</span></span>  
  
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
  
### <a name="to-handle-events-from-the-thread"></a><span data-ttu-id="271d4-162">İş parçacığı olayları işlemek için</span><span class="sxs-lookup"><span data-stu-id="271d4-162">To handle events from the thread</span></span>  
  
-   <span data-ttu-id="271d4-163">Aşağıdaki olay işleyicileri için ana form ekleyin:</span><span class="sxs-lookup"><span data-stu-id="271d4-163">Add the following event handlers to your main form:</span></span>  
  
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
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a><span data-ttu-id="271d4-164">WordCount yöntemi çalıştıran Başlat ve yeni bir iş parçacığı çağırmak için</span><span class="sxs-lookup"><span data-stu-id="271d4-164">To start and call a new thread that runs the WordCount method</span></span>  
  
1.  <span data-ttu-id="271d4-165">Aşağıdaki yordamlar programınıza ekleyin:</span><span class="sxs-lookup"><span data-stu-id="271d4-165">Add the following procedures to your program:</span></span>  
  
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
  
2.  <span data-ttu-id="271d4-166">Çağrı `StartThread` yönteminden `Start` formunuzda düğmesini:</span><span class="sxs-lookup"><span data-stu-id="271d4-166">Call the `StartThread` method from the `Start` button on your form:</span></span>  
  
    ```vb  
    Private Sub Start_Click() Handles Start.Click  
        StartThread()  
    End Sub  
    ```  
  
### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a><span data-ttu-id="271d4-167">İş parçacığı durdurur iptal düğmesi uygulamak için</span><span class="sxs-lookup"><span data-stu-id="271d4-167">To implement a Cancel button that stops the thread</span></span>  
  
-   <span data-ttu-id="271d4-168">Çağrı `StopThread` yordamdan `Click` için olay işleyicisini `Cancel` düğmesi.</span><span class="sxs-lookup"><span data-stu-id="271d4-168">Call the `StopThread` procedure from the `Click` event handler for the `Cancel` button.</span></span>  
  
    ```vb  
    Private Sub Cancel_Click() Handles Cancel.Click  
        ' Cancel the asynchronous operation.  
        Me.BackgroundWorker1.CancelAsync()  
    End Sub  
    ```  
  
## <a name="testing"></a><span data-ttu-id="271d4-169">Sınama</span><span class="sxs-lookup"><span data-stu-id="271d4-169">Testing</span></span>  
 <span data-ttu-id="271d4-170">Artık doğru çalıştığından emin olmak için uygulamayı test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="271d4-170">You can now test the application to make sure it works correctly.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="271d4-171">Uygulamayı test etmek için</span><span class="sxs-lookup"><span data-stu-id="271d4-171">To test the application</span></span>  
  
1.  <span data-ttu-id="271d4-172">Uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="271d4-172">Press F5 to run the application.</span></span>  
  
2.  <span data-ttu-id="271d4-173">Form görüntülendiğinde, test istediğiniz dosya için dosya yolu girin `sourceFile` kutusu.</span><span class="sxs-lookup"><span data-stu-id="271d4-173">When the form is displayed, enter the file path for the file you want to test in the `sourceFile` box.</span></span> <span data-ttu-id="271d4-174">Örneğin, test dosyanız sınama.txt adlı varsayıldığında, C:\Test.txt girin.</span><span class="sxs-lookup"><span data-stu-id="271d4-174">For example, assuming your test file is named Test.txt, enter C:\Test.txt.</span></span>  
  
3.  <span data-ttu-id="271d4-175">İkinci metin kutusuna bir sözcük veya tümcecik metin dosyasında aramak uygulamanın girin.</span><span class="sxs-lookup"><span data-stu-id="271d4-175">In the second text box, enter a word or phrase for the application to search for in the text file.</span></span>  
  
4.  <span data-ttu-id="271d4-176">Tıklatın `Start` düğmesi.</span><span class="sxs-lookup"><span data-stu-id="271d4-176">Click the `Start` button.</span></span> <span data-ttu-id="271d4-177">`LinesCounted` Düğmesi hemen artırma başlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="271d4-177">The `LinesCounted` button should begin incrementing immediately.</span></span> <span data-ttu-id="271d4-178">Bu işlem sona erdiğinde uygulama "sayım tamamlandı" iletisi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="271d4-178">The application displays the message "Finished Counting" when it is done.</span></span>  
  
#### <a name="to-test-the-cancel-button"></a><span data-ttu-id="271d4-179">İptal düğmesi sınamak için</span><span class="sxs-lookup"><span data-stu-id="271d4-179">To test the Cancel button</span></span>  
  
1.  <span data-ttu-id="271d4-180">Uygulama başlatma ve önceki yordamda açıklandığı gibi dosya adını ve arama sözcüğü girin için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="271d4-180">Press F5 to start the application, and enter the file name and search word as described in the previous procedure.</span></span> <span data-ttu-id="271d4-181">Seçtiğiniz dosya tamamlanmadan önce yordamı iptal etmek için zaman sahip emin olmak için yeterince büyük olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="271d4-181">Make sure that the file you choose is large enough to ensure you will have time to cancel the procedure before it is finished.</span></span>  
  
2.  <span data-ttu-id="271d4-182">Tıklatın `Start` uygulamayı başlatmak için düğmesi.</span><span class="sxs-lookup"><span data-stu-id="271d4-182">Click the `Start` button to start the application.</span></span>  
  
3.  <span data-ttu-id="271d4-183">Tıklatın `Cancel` düğmesi.</span><span class="sxs-lookup"><span data-stu-id="271d4-183">Click the `Cancel` button.</span></span> <span data-ttu-id="271d4-184">Uygulama hemen sayım durdurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="271d4-184">The application should stop counting immediately.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="271d4-185">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="271d4-185">Next Steps</span></span>  
 <span data-ttu-id="271d4-186">Bu uygulama, bazı temel hata işleme içerir.</span><span class="sxs-lookup"><span data-stu-id="271d4-186">This application contains some basic error handling.</span></span> <span data-ttu-id="271d4-187">Boş arama dizelerini algılar.</span><span class="sxs-lookup"><span data-stu-id="271d4-187">It detects blank search strings.</span></span> <span data-ttu-id="271d4-188">Sözcükleri veya sayılamaz satır sayısını aşan gibi diğer hataları işleyerek bu programı daha sağlam yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="271d4-188">You can make this program more robust by handling other errors, such as exceeding the maximum number of words or lines that can be counted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="271d4-189">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="271d4-189">See Also</span></span>  
 [<span data-ttu-id="271d4-190">İş parçacığı oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="271d4-190">Threading (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="271d4-191">İzlenecek yol: Visual Basic ile basit bir birden çok iş parçacıklı bileşen yazma</span><span class="sxs-lookup"><span data-stu-id="271d4-191">Walkthrough: Authoring a Simple Multithreaded Component with Visual Basic</span></span>](http://msdn.microsoft.com/library/05693b70-3566-4d91-9f2c-c9bc4ccb3001)  
 [<span data-ttu-id="271d4-192">Nasıl yapılır: Olaylara Abone Olma ve Aboneliği Kaldırma</span><span class="sxs-lookup"><span data-stu-id="271d4-192">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
