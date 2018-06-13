---
title: 'İzlenecek yol: BackgroundWorker bileşeni (C#) ile çoklu iş parçacığı kullanımı'
ms.date: 07/20/2015
ms.assetid: ff670fbf-a0ac-40c1-ab08-9ed53768f880
ms.openlocfilehash: bc334261dbea7759d1bb571cc61a5f00f84531a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339374"
---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-c"></a>İzlenecek yol: BackgroundWorker bileşeni (C#) ile çoklu iş parçacığı kullanımı
Bu kılavuz bir metin dosyası için bir sözcük oluşumları arar birden çok iş parçacıklı bir Windows Forms uygulamasının nasıl oluşturulacağını gösterir. Bunu gösterir:  
  
-   Bir sınıf tarafından çağrılabilir bir yöntem tanımlama <xref:System.ComponentModel.BackgroundWorker> bileşeni.  
  
-   Tarafından oluşturulan olayları işleme <xref:System.ComponentModel.BackgroundWorker> bileşeni.  
  
-   Başlangıç bir <xref:System.ComponentModel.BackgroundWorker> bir yöntem çalıştırmak için bileşen.  
  
-   Uygulama bir `Cancel` durdurur düğmesi <xref:System.ComponentModel.BackgroundWorker> bileşeni.  
  
### <a name="to-create-the-user-interface"></a>Kullanıcı arabirimini oluşturmak için  
  
1.  Yeni bir C# Windows Forms uygulaması projesi açın ve adlı bir form oluşturun `Form1`.  
  
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
  
3.  BackgroundWorker1 nesnesinin olaylarına abone olma. Üstündeki **özellikleri** penceresinde tıklatın **olayları** simgesi. Çift `RunWorkerCompleted` olay bir olay işleyicisi yöntemi oluşturun. Aynı işlemi gerçekleştirmek `ProgressChanged` ve `DoWork` olaylar.  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a>Ayrı bir iş parçacığı üzerinde çalışacak yöntemi tanımlamak için  
  
1.  Gelen **proje** menüsünde seçin **sınıfı Ekle** projeye bir sınıf eklemek için. **Yeni Öğe Ekle** iletişim kutusu görüntülenir.  
  
2.  Seçin **sınıfı** şablonları penceresinden ve girin `Words.cs` ad alanında.  
  
3.  **Ekle**'yi tıklatın. `Words` Sınıfı görüntülenir.  
  
4.  Aşağıdaki kodu ekleyin `Words` sınıfı:  
  
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
  
### <a name="to-handle-events-from-the-thread"></a>İş parçacığı olayları işlemek için  
  
-   Aşağıdaki olay işleyicileri için ana form ekleyin:  
  
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
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a>WordCount yöntemi çalıştıran Başlat ve yeni bir iş parçacığı çağırmak için  
  
1.  Aşağıdaki yordamlar programınıza ekleyin:  
  
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
  
2.  Çağrı `StartThread` yönteminden `Start` formunuzda düğmesini:  
  
    ```csharp  
    private void Start_Click(object sender, EventArgs e)  
    {  
        StartThread();  
    }  
    ```  
  
    ##### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a>İş parçacığı durdurur iptal düğmesi uygulamak için  
  
    -   Çağrı `StopThread` yordamdan `Click` için olay işleyicisini `Cancel` düğmesi.  
  
        ```csharp  
        private void Cancel_Click(object sender, EventArgs e)  
        {  
            // Cancel the asynchronous operation.  
            this.backgroundWorker1.CancelAsync();  
        }  
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
 [İş parçacığı (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [Nasıl yapılır: Olaylara Abone Olma ve Aboneliği Kaldırma](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
