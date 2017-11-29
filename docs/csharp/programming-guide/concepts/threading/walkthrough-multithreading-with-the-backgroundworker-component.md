---
title: "İzlenecek yol: BackgroundWorker bileşeni (C#) ile çoklu iş parçacığı kullanımı"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: ff670fbf-a0ac-40c1-ab08-9ed53768f880
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 72d6e9ab42ca270ebe0691be23ebe181b973620d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-c"></a><span data-ttu-id="b75ad-102">İzlenecek yol: BackgroundWorker bileşeni (C#) ile çoklu iş parçacığı kullanımı</span><span class="sxs-lookup"><span data-stu-id="b75ad-102">Walkthrough: Multithreading with the BackgroundWorker Component (C#)</span></span>
<span data-ttu-id="b75ad-103">Bu kılavuz bir metin dosyası için bir sözcük oluşumları arar birden çok iş parçacıklı bir Windows Forms uygulamasının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b75ad-103">This walkthrough demonstrates how to create a multithreaded Windows Forms application that searches a text file for occurrences of a word.</span></span> <span data-ttu-id="b75ad-104">Bunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="b75ad-104">It demonstrates:</span></span>  
  
-   <span data-ttu-id="b75ad-105">Bir sınıf tarafından çağrılabilir bir yöntem tanımlama <xref:System.ComponentModel.BackgroundWorker> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="b75ad-105">Defining a class with a method that can be called by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="b75ad-106">Tarafından oluşturulan olayları işleme <xref:System.ComponentModel.BackgroundWorker> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="b75ad-106">Handling events raised by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="b75ad-107">Başlangıç bir <xref:System.ComponentModel.BackgroundWorker> bir yöntem çalıştırmak için bileşen.</span><span class="sxs-lookup"><span data-stu-id="b75ad-107">Starting a <xref:System.ComponentModel.BackgroundWorker> component to run a method.</span></span>  
  
-   <span data-ttu-id="b75ad-108">Uygulama bir `Cancel` durdurur düğmesi <xref:System.ComponentModel.BackgroundWorker> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="b75ad-108">Implementing a `Cancel` button that stops the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="b75ad-109">Kullanıcı arabirimini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b75ad-109">To create the user interface</span></span>  
  
1.  <span data-ttu-id="b75ad-110">Yeni bir C# Windows Forms uygulaması projesi açın ve adlı bir form oluşturun `Form1`.</span><span class="sxs-lookup"><span data-stu-id="b75ad-110">Open a new C# Windows Forms Application project, and create a form named `Form1`.</span></span>  
  
2.  <span data-ttu-id="b75ad-111">İki düğme ve dört metin kutusu ekleyin `Form1`.</span><span class="sxs-lookup"><span data-stu-id="b75ad-111">Add two buttons and four text boxes to `Form1`.</span></span>  
  
3.  <span data-ttu-id="b75ad-112">Aşağıdaki tabloda gösterildiği gibi nesneleri adlandırın.</span><span class="sxs-lookup"><span data-stu-id="b75ad-112">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="b75ad-113">Nesne</span><span class="sxs-lookup"><span data-stu-id="b75ad-113">Object</span></span>|<span data-ttu-id="b75ad-114">Özellik</span><span class="sxs-lookup"><span data-stu-id="b75ad-114">Property</span></span>|<span data-ttu-id="b75ad-115">Ayar</span><span class="sxs-lookup"><span data-stu-id="b75ad-115">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="b75ad-116">İlk düğmesi</span><span class="sxs-lookup"><span data-stu-id="b75ad-116">First button</span></span>|<span data-ttu-id="b75ad-117">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="b75ad-117">`Name`, `Text`</span></span>|<span data-ttu-id="b75ad-118">Başlangıç, Başlat</span><span class="sxs-lookup"><span data-stu-id="b75ad-118">Start, Start</span></span>|  
    |<span data-ttu-id="b75ad-119">İkinci düğmesi</span><span class="sxs-lookup"><span data-stu-id="b75ad-119">Second button</span></span>|<span data-ttu-id="b75ad-120">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="b75ad-120">`Name`, `Text`</span></span>|<span data-ttu-id="b75ad-121">İptal, iptal</span><span class="sxs-lookup"><span data-stu-id="b75ad-121">Cancel, Cancel</span></span>|  
    |<span data-ttu-id="b75ad-122">İlk metin kutusu</span><span class="sxs-lookup"><span data-stu-id="b75ad-122">First text box</span></span>|<span data-ttu-id="b75ad-123">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="b75ad-123">`Name`, `Text`</span></span>|<span data-ttu-id="b75ad-124">SourceFile, ""</span><span class="sxs-lookup"><span data-stu-id="b75ad-124">SourceFile, ""</span></span>|  
    |<span data-ttu-id="b75ad-125">İkinci metin kutusu</span><span class="sxs-lookup"><span data-stu-id="b75ad-125">Second text box</span></span>|<span data-ttu-id="b75ad-126">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="b75ad-126">`Name`, `Text`</span></span>|<span data-ttu-id="b75ad-127">CompareString, ""</span><span class="sxs-lookup"><span data-stu-id="b75ad-127">CompareString, ""</span></span>|  
    |<span data-ttu-id="b75ad-128">Üçüncü metin kutusu</span><span class="sxs-lookup"><span data-stu-id="b75ad-128">Third text box</span></span>|<span data-ttu-id="b75ad-129">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="b75ad-129">`Name`, `Text`</span></span>|<span data-ttu-id="b75ad-130">WordsCounted, "0"</span><span class="sxs-lookup"><span data-stu-id="b75ad-130">WordsCounted, "0"</span></span>|  
    |<span data-ttu-id="b75ad-131">Dördüncü metin kutusu</span><span class="sxs-lookup"><span data-stu-id="b75ad-131">Fourth text box</span></span>|<span data-ttu-id="b75ad-132">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="b75ad-132">`Name`, `Text`</span></span>|<span data-ttu-id="b75ad-133">LinesCounted, "0"</span><span class="sxs-lookup"><span data-stu-id="b75ad-133">LinesCounted, "0"</span></span>|  
  
4.  <span data-ttu-id="b75ad-134">Her metin kutusunun yanında bir etiket ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b75ad-134">Add a label next to each text box.</span></span> <span data-ttu-id="b75ad-135">Ayarlama `Text` özelliği aşağıdaki tabloda gösterildiği gibi her bir etiket için.</span><span class="sxs-lookup"><span data-stu-id="b75ad-135">Set the `Text` property for each label as shown in the following table.</span></span>  
  
    |<span data-ttu-id="b75ad-136">Nesne</span><span class="sxs-lookup"><span data-stu-id="b75ad-136">Object</span></span>|<span data-ttu-id="b75ad-137">Özellik</span><span class="sxs-lookup"><span data-stu-id="b75ad-137">Property</span></span>|<span data-ttu-id="b75ad-138">Ayar</span><span class="sxs-lookup"><span data-stu-id="b75ad-138">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="b75ad-139">İlk etiketi</span><span class="sxs-lookup"><span data-stu-id="b75ad-139">First label</span></span>|`Text`|<span data-ttu-id="b75ad-140">Kaynak dosya</span><span class="sxs-lookup"><span data-stu-id="b75ad-140">Source File</span></span>|  
    |<span data-ttu-id="b75ad-141">İkinci etiketi</span><span class="sxs-lookup"><span data-stu-id="b75ad-141">Second label</span></span>|`Text`|<span data-ttu-id="b75ad-142">Dize karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="b75ad-142">Compare String</span></span>|  
    |<span data-ttu-id="b75ad-143">Üçüncü etiketi</span><span class="sxs-lookup"><span data-stu-id="b75ad-143">Third label</span></span>|`Text`|<span data-ttu-id="b75ad-144">Eşleşen sözcükleri</span><span class="sxs-lookup"><span data-stu-id="b75ad-144">Matching Words</span></span>|  
    |<span data-ttu-id="b75ad-145">Dördüncü etiketi</span><span class="sxs-lookup"><span data-stu-id="b75ad-145">Fourth label</span></span>|`Text`|<span data-ttu-id="b75ad-146">Sayılan satırları</span><span class="sxs-lookup"><span data-stu-id="b75ad-146">Lines Counted</span></span>|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a><span data-ttu-id="b75ad-147">BackgroundWorker bileşeni oluşturma ve onun olaylarına abone olma</span><span class="sxs-lookup"><span data-stu-id="b75ad-147">To create a BackgroundWorker component and subscribe to its events</span></span>  
  
1.  <span data-ttu-id="b75ad-148">Ekleme bir <xref:System.ComponentModel.BackgroundWorker> gelen bileşen **bileşenleri** bölümünü **araç** form.</span><span class="sxs-lookup"><span data-stu-id="b75ad-148">Add a <xref:System.ComponentModel.BackgroundWorker> component from the **Components** section of the **ToolBox** to the form.</span></span> <span data-ttu-id="b75ad-149">Formun bileşen tepsisinde görünür.</span><span class="sxs-lookup"><span data-stu-id="b75ad-149">It will appear in the form's component tray.</span></span>  
  
2.  <span data-ttu-id="b75ad-150">BackgroundWorker1 nesnesi için aşağıdaki özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b75ad-150">Set the following properties for the backgroundWorker1 object.</span></span>  
  
    |<span data-ttu-id="b75ad-151">Özellik</span><span class="sxs-lookup"><span data-stu-id="b75ad-151">Property</span></span>|<span data-ttu-id="b75ad-152">Ayar</span><span class="sxs-lookup"><span data-stu-id="b75ad-152">Setting</span></span>|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|<span data-ttu-id="b75ad-153">Doğru</span><span class="sxs-lookup"><span data-stu-id="b75ad-153">True</span></span>|  
    |`WorkerSupportsCancellation`|<span data-ttu-id="b75ad-154">Doğru</span><span class="sxs-lookup"><span data-stu-id="b75ad-154">True</span></span>|  
  
3.  <span data-ttu-id="b75ad-155">BackgroundWorker1 nesnesinin olaylarına abone olma.</span><span class="sxs-lookup"><span data-stu-id="b75ad-155">Subscribe to the events of the backgroundWorker1 object.</span></span> <span data-ttu-id="b75ad-156">Üstündeki **özellikleri** penceresinde tıklatın **olayları** simgesi.</span><span class="sxs-lookup"><span data-stu-id="b75ad-156">At the top of the **Properties** window, click the **Events** icon.</span></span> <span data-ttu-id="b75ad-157">Çift `RunWorkerCompleted` olay bir olay işleyicisi yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b75ad-157">Double-click the `RunWorkerCompleted` event to create an event handler method.</span></span> <span data-ttu-id="b75ad-158">Aynı işlemi gerçekleştirmek `ProgressChanged` ve `DoWork` olaylar.</span><span class="sxs-lookup"><span data-stu-id="b75ad-158">Do the same for the `ProgressChanged` and `DoWork` events.</span></span>  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a><span data-ttu-id="b75ad-159">Ayrı bir iş parçacığı üzerinde çalışacak yöntemi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="b75ad-159">To define the method that will run on a separate thread</span></span>  
  
1.  <span data-ttu-id="b75ad-160">Gelen **proje** menüsünde seçin **sınıfı Ekle** projeye bir sınıf eklemek için.</span><span class="sxs-lookup"><span data-stu-id="b75ad-160">From the **Project** menu, choose **Add Class** to add a class to the project.</span></span> <span data-ttu-id="b75ad-161">**Yeni Öğe Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b75ad-161">The **Add New Item** dialog box is displayed.</span></span>  
  
2.  <span data-ttu-id="b75ad-162">Seçin **sınıfı** şablonları penceresinden ve girin `Words.cs` ad alanında.</span><span class="sxs-lookup"><span data-stu-id="b75ad-162">Select **Class** from the templates window and enter `Words.cs` in the name field.</span></span>  
  
3.  <span data-ttu-id="b75ad-163">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="b75ad-163">Click **Add**.</span></span> <span data-ttu-id="b75ad-164">`Words` Sınıfı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b75ad-164">The `Words` class is displayed.</span></span>  
  
4.  <span data-ttu-id="b75ad-165">Aşağıdaki kodu ekleyin `Words` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="b75ad-165">Add the following code to the `Words` class:</span></span>  
  
    ```csharp  
    public class Words  
    {  
        // Object to store the current state, for passing to the caller.  
        public class CurrentState  
        {  
            public int LinesCounted;  
            public int WordsMatched;  
        }  
  
        public string SourceFile;  
        public string CompareString;  
        private int WordCount;  
        private int LinesCounted;  
  
        public void CountWords(  
            System.ComponentModel.BackgroundWorker worker,  
            System.ComponentModel.DoWorkEventArgs e)  
        {  
            // Initialize the variables.  
            CurrentState state = new CurrentState();  
            string line = "";  
            int elapsedTime = 20;  
            DateTime lastReportDateTime = DateTime.Now;  
  
            if (CompareString == null ||  
                CompareString == System.String.Empty)  
            {  
                throw new Exception("CompareString not specified.");  
            }  
  
            // Open a new stream.  
            using (System.IO.StreamReader myStream = new System.IO.StreamReader(SourceFile))  
            {  
                // Process lines while there are lines remaining in the file.  
                while (!myStream.EndOfStream)  
                {  
                    if (worker.CancellationPending)  
                    {  
                        e.Cancel = true;  
                        break;  
                    }  
                    else  
                    {  
                        line = myStream.ReadLine();  
                        WordCount += CountInString(line, CompareString);  
                        LinesCounted += 1;  
  
                        // Raise an event so the form can monitor progress.  
                        int compare = DateTime.Compare(  
                            DateTime.Now, lastReportDateTime.AddMilliseconds(elapsedTime));  
                        if (compare > 0)  
                        {  
                            state.LinesCounted = LinesCounted;  
                            state.WordsMatched = WordCount;  
                            worker.ReportProgress(0, state);  
                            lastReportDateTime = DateTime.Now;  
                        }  
                    }  
                    // Uncomment for testing.  
                    //System.Threading.Thread.Sleep(5);  
                }  
  
                // Report the final count values.  
                state.LinesCounted = LinesCounted;  
                state.WordsMatched = WordCount;  
                worker.ReportProgress(0, state);  
            }  
        }  
  
        private int CountInString(  
            string SourceString,  
            string CompareString)  
        {  
            // This function counts the number of times  
            // a word is found in a line.  
            if (SourceString == null)  
            {  
                return 0;  
            }  
  
            string EscapedCompareString =  
                System.Text.RegularExpressions.Regex.Escape(CompareString);  
  
            System.Text.RegularExpressions.Regex regex;  
            regex = new System.Text.RegularExpressions.Regex(   
                // To count all occurrences of the string, even within words, remove  
                // both instances of @"\b" from the following line.  
                @"\b" + EscapedCompareString + @"\b",  
                System.Text.RegularExpressions.RegexOptions.IgnoreCase);  
  
            System.Text.RegularExpressions.MatchCollection matches;  
            matches = regex.Matches(SourceString);  
            return matches.Count;  
        }  
  
    }  
    ```  
  
### <a name="to-handle-events-from-the-thread"></a><span data-ttu-id="b75ad-166">İş parçacığı olayları işlemek için</span><span class="sxs-lookup"><span data-stu-id="b75ad-166">To handle events from the thread</span></span>  
  
-   <span data-ttu-id="b75ad-167">Aşağıdaki olay işleyicileri için ana form ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b75ad-167">Add the following event handlers to your main form:</span></span>  
  
    ```csharp  
    private void backgroundWorker1_RunWorkerCompleted(object sender, RunWorkerCompletedEventArgs e)  
    {  
    // This event handler is called when the background thread finishes.  
    // This method runs on the main thread.  
    if (e.Error != null)  
        MessageBox.Show("Error: " + e.Error.Message);  
    else if (e.Cancelled)  
        MessageBox.Show("Word counting canceled.");  
    else  
        MessageBox.Show("Finished counting words.");  
    }  
  
    private void backgroundWorker1_ProgressChanged(object sender, ProgressChangedEventArgs e)  
    {  
        // This method runs on the main thread.  
        Words.CurrentState state =  
            (Words.CurrentState)e.UserState;  
        this.LinesCounted.Text = state.LinesCounted.ToString();  
        this.WordsCounted.Text = state.WordsMatched.ToString();  
    }  
    ```  
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a><span data-ttu-id="b75ad-168">WordCount yöntemi çalıştıran Başlat ve yeni bir iş parçacığı çağırmak için</span><span class="sxs-lookup"><span data-stu-id="b75ad-168">To start and call a new thread that runs the WordCount method</span></span>  
  
1.  <span data-ttu-id="b75ad-169">Aşağıdaki yordamlar programınıza ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b75ad-169">Add the following procedures to your program:</span></span>  
  
    ```csharp  
    private void backgroundWorker1_DoWork(object sender, DoWorkEventArgs e)  
    {  
        // This event handler is where the actual work is done.  
        // This method runs on the background thread.  
  
        // Get the BackgroundWorker object that raised this event.  
        System.ComponentModel.BackgroundWorker worker;  
        worker = (System.ComponentModel.BackgroundWorker)sender;  
  
        // Get the Words object and call the main method.  
        Words WC = (Words)e.Argument;  
        WC.CountWords(worker, e);  
    }  
  
    private void StartThread()  
    {  
        // This method runs on the main thread.  
        this.WordsCounted.Text = "0";  
  
        // Initialize the object that the background worker calls.  
        Words WC = new Words();  
        WC.CompareString = this.CompareString.Text;  
        WC.SourceFile = this.SourceFile.Text;  
  
        // Start the asynchronous operation.  
        backgroundWorker1.RunWorkerAsync(WC);  
    }  
    ```  
  
2.  <span data-ttu-id="b75ad-170">Çağrı `StartThread` yönteminden `Start` formunuzda düğmesini:</span><span class="sxs-lookup"><span data-stu-id="b75ad-170">Call the `StartThread` method from the `Start` button on your form:</span></span>  
  
    ```csharp  
    private void Start_Click(object sender, EventArgs e)  
    {  
        StartThread();  
    }  
    ```  
  
    ##### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a><span data-ttu-id="b75ad-171">İş parçacığı durdurur iptal düğmesi uygulamak için</span><span class="sxs-lookup"><span data-stu-id="b75ad-171">To implement a Cancel button that stops the thread</span></span>  
  
    -   <span data-ttu-id="b75ad-172">Çağrı `StopThread` yordamdan `Click` için olay işleyicisini `Cancel` düğmesi.</span><span class="sxs-lookup"><span data-stu-id="b75ad-172">Call the `StopThread` procedure from the `Click` event handler for the `Cancel` button.</span></span>  
  
        ```csharp  
        private void Cancel_Click(object sender, EventArgs e)  
        {  
            // Cancel the asynchronous operation.  
            this.backgroundWorker1.CancelAsync();  
        }  
        ```  
  
## <a name="testing"></a><span data-ttu-id="b75ad-173">Sınama</span><span class="sxs-lookup"><span data-stu-id="b75ad-173">Testing</span></span>  
 <span data-ttu-id="b75ad-174">Artık doğru çalıştığından emin olmak için uygulamayı test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b75ad-174">You can now test the application to make sure it works correctly.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="b75ad-175">Uygulamayı test etmek için</span><span class="sxs-lookup"><span data-stu-id="b75ad-175">To test the application</span></span>  
  
1.  <span data-ttu-id="b75ad-176">Uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b75ad-176">Press F5 to run the application.</span></span>  
  
2.  <span data-ttu-id="b75ad-177">Form görüntülendiğinde, test istediğiniz dosya için dosya yolu girin `sourceFile` kutusu.</span><span class="sxs-lookup"><span data-stu-id="b75ad-177">When the form is displayed, enter the file path for the file you want to test in the `sourceFile` box.</span></span> <span data-ttu-id="b75ad-178">Örneğin, test dosyanız sınama.txt adlı varsayıldığında, C:\Test.txt girin.</span><span class="sxs-lookup"><span data-stu-id="b75ad-178">For example, assuming your test file is named Test.txt, enter C:\Test.txt.</span></span>  
  
3.  <span data-ttu-id="b75ad-179">İkinci metin kutusuna bir sözcük veya tümcecik metin dosyasında aramak uygulamanın girin.</span><span class="sxs-lookup"><span data-stu-id="b75ad-179">In the second text box, enter a word or phrase for the application to search for in the text file.</span></span>  
  
4.  <span data-ttu-id="b75ad-180">Tıklatın `Start` düğmesi.</span><span class="sxs-lookup"><span data-stu-id="b75ad-180">Click the `Start` button.</span></span> <span data-ttu-id="b75ad-181">`LinesCounted` Düğmesi hemen artırma başlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b75ad-181">The `LinesCounted` button should begin incrementing immediately.</span></span> <span data-ttu-id="b75ad-182">Bu işlem sona erdiğinde uygulama "sayım tamamlandı" iletisi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b75ad-182">The application displays the message "Finished Counting" when it is done.</span></span>  
  
#### <a name="to-test-the-cancel-button"></a><span data-ttu-id="b75ad-183">İptal düğmesi sınamak için</span><span class="sxs-lookup"><span data-stu-id="b75ad-183">To test the Cancel button</span></span>  
  
1.  <span data-ttu-id="b75ad-184">Uygulama başlatma ve önceki yordamda açıklandığı gibi dosya adını ve arama sözcüğü girin için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b75ad-184">Press F5 to start the application, and enter the file name and search word as described in the previous procedure.</span></span> <span data-ttu-id="b75ad-185">Seçtiğiniz dosya tamamlanmadan önce yordamı iptal etmek için zaman sahip emin olmak için yeterince büyük olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b75ad-185">Make sure that the file you choose is large enough to ensure you will have time to cancel the procedure before it is finished.</span></span>  
  
2.  <span data-ttu-id="b75ad-186">Tıklatın `Start` uygulamayı başlatmak için düğmesi.</span><span class="sxs-lookup"><span data-stu-id="b75ad-186">Click the `Start` button to start the application.</span></span>  
  
3.  <span data-ttu-id="b75ad-187">Tıklatın `Cancel` düğmesi.</span><span class="sxs-lookup"><span data-stu-id="b75ad-187">Click the `Cancel` button.</span></span> <span data-ttu-id="b75ad-188">Uygulama hemen sayım durdurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b75ad-188">The application should stop counting immediately.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b75ad-189">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="b75ad-189">Next Steps</span></span>  
 <span data-ttu-id="b75ad-190">Bu uygulama, bazı temel hata işleme içerir.</span><span class="sxs-lookup"><span data-stu-id="b75ad-190">This application contains some basic error handling.</span></span> <span data-ttu-id="b75ad-191">Boş arama dizelerini algılar.</span><span class="sxs-lookup"><span data-stu-id="b75ad-191">It detects blank search strings.</span></span> <span data-ttu-id="b75ad-192">Sözcükleri veya sayılamaz satır sayısını aşan gibi diğer hataları işleyerek bu programı daha sağlam yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b75ad-192">You can make this program more robust by handling other errors, such as exceeding the maximum number of words or lines that can be counted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b75ad-193">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b75ad-193">See Also</span></span>  
 [<span data-ttu-id="b75ad-194">İş parçacığı (C#)</span><span class="sxs-lookup"><span data-stu-id="b75ad-194">Threading (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="b75ad-195">Nasıl yapılır: abone olaylara ve aboneliği kaldırma</span><span class="sxs-lookup"><span data-stu-id="b75ad-195">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
