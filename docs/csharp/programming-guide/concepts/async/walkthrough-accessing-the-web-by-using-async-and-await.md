---
title: "İzlenecek yol: async kullanarak Web'e erişme ve await (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: get-started-article
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 85edc87bc8c5183f85618351034c0b043472b530
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a>İzlenecek yol: async kullanarak Web'e erişme ve await (C#)
Zaman uyumsuz ve bekleme özelliklerini kullanarak zaman uyumsuz programlar daha kolay ve sezgisel yazabilirsiniz. Zaman uyumlu kod gibi görünüyor zaman uyumsuz kod yazın ve daha zor geri arama işlevleri ve zaman uyumsuz kod genellikle kapsar devamlılıklar işlemek derleyici sağlayabilirsiniz.  
  
 Async özelliği hakkında daha fazla bilgi için bkz: [zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).  
  
 Bu kılavuzda Web sitelerinin bir listesiyle bayt sayısını toplar zaman uyumlu bir Windows Presentation Foundation (WPF) uygulama başlar. İzlenecek yol sonra yeni özellikleri kullanarak zaman uyumsuz çözümünü uygulamaya dönüştürür.  
  
 Uygulamaları kendiniz yapılandırmak istemiyorsanız, indirebilirsiniz "zaman uyumsuz örnek: Web gözden geçirme (C# ve Visual Basic) erişme" den [Geliştirici kod örnekleri](http://go.microsoft.com/fwlink/?LinkId=255191).  
  
 Bu kılavuzda, aşağıdaki görevleri tamamlayın:  
  
-   [Bir WPF uygulaması oluşturmak için](#CreateWPFApp)  
  
-   [Basit bir WPF MainWindow tasarlamak için](#MainWindow)  
  
-   [Bir başvuru eklemek için](#AddRef)  
  
-   [Eklemek için gerekli yönergeleri kullanma](#usingDir)  
  
-   [Zaman uyumlu bir uygulama oluşturmak için](#synchronous)  
  
-   [Zaman uyumlu çözümü test etmek için](#testSynch)  
  
-   [Zaman uyumsuz bir yöntem GetURLContents dönüştürmek için](#GetURLContents)  
  
-   [Zaman uyumsuz bir yöntem SumPageSizes dönüştürmek için](#SumPageSizes)  
  
-   [Zaman uyumsuz bir yöntem startButton_Click dönüştürmek için](#startButton)  
  
-   [Zaman uyumsuz çözümü test etmek için](#testAsynch)  
  
-   [.NET Framework yöntemiyle yöntemi GetURLContentsAsync değiştirmek için](#GetURLContentsAsync)  
  
-   [Örnek](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2012 veya sonraki sürümünü bilgisayarınızda yüklü olmalıdır. Daha fazla bilgi için bkz: [Microsoft Web sitesi](http://go.microsoft.com/fwlink/?LinkId=235233).  
  
###  <a name="CreateWPFApp"></a>Bir WPF uygulaması oluşturmak için  
  
1.  Visual Studio'yu başlatın.  
  
2.  Menü çubuğunda seçin **dosya**, **yeni**, **proje**.  
  
     **Yeni proje** iletişim kutusu açılır.  
  
3.  İçinde **yüklü şablonlar** bölmesinde, Visual C# ' ı seçin ve ardından **WPF uygulaması** proje türleri listesinden.  
  
4.  İçinde **adı** metin kutusuna `AsyncExampleWPF`ve ardından **Tamam** düğmesi.  
  
     Yeni Proje görünür **Çözüm Gezgini**.  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <a name="MainWindow"></a>Basit bir WPF MainWindow tasarlamak için  
  
1.  Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.  
  
2.  Varsa **araç** pencere görünür, açık olmayan **Görünüm** menüsünde ve ardından **araç**.  
  
3.  Ekleme bir **düğmesini** denetim ve **TextBox** denetimini **MainWindow** penceresi.  
  
4.  Vurgula **TextBox** denetim hem de **özellikleri** penceresinde, aşağıdaki değerleri ayarlayın:  
  
    -   Ayarlama **adı** özelliğine `resultsTextBox`.  
  
    -   Ayarlama **yükseklik** 250 özelliğine.  
  
    -   Ayarlama **genişliği** 500 özelliği.  
  
    -   Üzerinde **metin** sekmesinde, Lucida Console veya genel tek aralıklı gibi aralıklı bir yazı tipi belirtin.  
  
5.  Vurgula **düğmesini** denetim hem de **özellikleri** penceresinde, aşağıdaki değerleri ayarlayın:  
  
    -   Ayarlama **adı** özelliğine `startButton`.  
  
    -   Değerini değiştirme **içerik** özelliğinden **düğmesini** için **Başlat**.  
  
6.  Her ikisi de görünmesini sağlayacak şekilde, metin kutusu ve düğmesi konum **MainWindow** penceresi.  
  
     WPF XAML Tasarımcısı hakkında daha fazla bilgi için bkz: [XAML Tasarımcısını kullanarak bir kullanıcı Arabirimi oluşturma](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).  
  
##  <a name="BKMK_AddReference"></a>   
###  <a name="AddRef"></a>Bir başvuru eklemek için  
  
1.  İçinde **Çözüm Gezgini**, projenizin adını vurgulayın.  
  
2.  Menü çubuğunda seçin **proje**, **Başvuru Ekle**.  
  
     **Başvuru Yöneticisi** iletişim kutusu görüntülenir.  
  
3.  İletişim kutusunun üstündeki projeniz .NET Framework 4.5 veya üstünü hedefleyen olduğunu doğrulayın.  
  
4.  İçinde **derlemeleri** alanı seçin **Framework** tercih değil.  
  
5.  Adları listesinden seçin **System.Net.Http** onay kutusu.  
  
6.  Seçin **Tamam** düğmesi iletişim kutusunu kapatın.  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <a name="usingDir"></a>Eklemek için gerekli yönergeleri kullanma  
  
1.  İçinde **Çözüm Gezgini**MainWindow.xaml.cs için kısayol menüsünü açın ve ardından **görünümü kodu**.  
  
2.  Aşağıdakileri ekleyin `using` zaten mevcut değillerse kod dosyasının üst yönergeleri.  
  
    ```csharp  
    using System.Net.Http;  
    using System.Net;  
    using System.IO;  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <a name="synchronous"></a>Zaman uyumlu bir uygulama oluşturmak için  
  
1.  Tasarım penceresinde MainWindow.xaml, çift **Başlat** oluşturmak için düğmesini `startButton_Click` MainWindow.xaml.cs olay işleyicisi.  
  
2.  MainWindow.xaml.cs içinde gövdesine aşağıdaki kodu kopyalayın `startButton_Click`:  
  
    ```csharp  
    resultsTextBox.Clear();  
    SumPageSizes();  
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";  
    ```  
  
     Kod uygulama sürücüleri yöntemini çağırır `SumPageSizes`ve denetim döndüğünde bir ileti görüntüler `startButton_Click`.  
  
3.  Zaman uyumlu çözüm için kod aşağıdaki dört yöntemi içerir:  
  
    -   `SumPageSizes`, Web sayfası URL'lerden listesini alır `SetUpURLList` ve çağırır `GetURLContents` ve `DisplayResults` her URL işleyemedi.  
  
    -   `SetUpURLList`, hangi yapar ve web adresleri listesi döndürür.  
  
    -   `GetURLContents`, her Web sitesi içeriğini indirir ve içeriği bir bayt dizisi olarak döndürür.  
  
    -   `DisplayResults`, görüntüleyen bayt sayısı bayt dizisi, her URL için.  
  
     Aşağıdaki dört yöntemi kopyalayın ve yapıştırın altında `startButton_Click` MainWindow.xaml.cs olay işleyicisi:  
  
    ```csharp  
    private void SumPageSizes()  
    {  
        // Make a list of web addresses.  
        List<string> urlList = SetUpURLList();   
  
        var total = 0;  
        foreach (var url in urlList)  
        {  
            // GetURLContents returns the contents of url as a byte array.  
            byte[] urlContents = GetURLContents(url);  
  
            DisplayResults(url, urlContents);  
  
            // Update the total.  
            total += urlContents.Length;  
        }  
  
        // Display the total count for all of the web addresses.  
        resultsTextBox.Text +=   
            string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
    }  
  
    private List<string> SetUpURLList()  
    {  
        var urls = new List<string>   
        {   
            "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
            "http://msdn.microsoft.com",  
            "http://msdn.microsoft.com/library/hh290136.aspx",  
            "http://msdn.microsoft.com/library/ee256749.aspx",  
            "http://msdn.microsoft.com/library/hh290138.aspx",  
            "http://msdn.microsoft.com/library/hh290140.aspx",  
            "http://msdn.microsoft.com/library/dd470362.aspx",  
            "http://msdn.microsoft.com/library/aa578028.aspx",  
            "http://msdn.microsoft.com/library/ms404677.aspx",  
            "http://msdn.microsoft.com/library/ff730837.aspx"  
        };  
        return urls;  
    }  
  
    private byte[] GetURLContents(string url)  
    {  
        // The downloaded resource ends up in the variable named content.  
        var content = new MemoryStream();  
  
        // Initialize an HttpWebRequest for the current URL.  
        var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
        // Send the request to the Internet resource and wait for  
        // the response.  
        // Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.  
        using (WebResponse response = webReq.GetResponse())  
        {  
            // Get the data stream that is associated with the specified URL.  
            using (Stream responseStream = response.GetResponseStream())  
            {  
                // Read the bytes in responseStream and copy them to content.    
                responseStream.CopyTo(content);  
            }  
        }  
  
        // Return the result as a byte array.  
        return content.ToArray();  
    }  
  
    private void DisplayResults(string url, byte[] content)  
    {  
        // Display the length of each website. The string format   
        // is designed to be used with a monospaced font, such as  
        // Lucida Console or Global Monospace.  
        var bytes = content.Length;  
        // Strip off the "http://".  
        var displayURL = url.Replace("http://", "");  
        resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
    }  
    ```  
  
##  <a name="BKMK_TestSynchSol"></a>   
###  <a name="testSynch"></a>Zaman uyumlu çözümü test etmek için  
  
1.  Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.  
  
     Aşağıdaki listede benzer bir çıktı görüntülenmesi gerekir.  
  
    ```  
    msdn.microsoft.com/library/windows/apps/br211380.aspx        383832  
    msdn.microsoft.com                                            33964  
    msdn.microsoft.com/library/hh290136.aspx               225793  
    msdn.microsoft.com/library/ee256749.aspx               143577  
    msdn.microsoft.com/library/hh290138.aspx               237372  
    msdn.microsoft.com/library/hh290140.aspx               128279  
    msdn.microsoft.com/library/dd470362.aspx               157649  
    msdn.microsoft.com/library/aa578028.aspx               204457  
    msdn.microsoft.com/library/ms404677.aspx               176405  
    msdn.microsoft.com/library/ff730837.aspx               143474  
  
    Total bytes returned:  1834802  
  
    Control returned to startButton_Click.  
    ```  
  
     Sayıları görüntülemek için birkaç saniye sürer dikkat edin. İstenen kaynaklar indirmek beklerken bu süre içinde kullanıcı Arabirimi iş parçacığı engellendi. Sonuç olarak, taşıyamazsınız, en üst düzeye çıkarmak, simge durumuna küçült veya seçtiğiniz sonra bile görüntü penceresini kapatın **Başlat** düğmesi. Görüntülenecek bayt sayıları başlatana kadar bu çaba başarısız. Bir Web sitesi yanıt vermiyor gösterge olmadan başarısız hangi sitenin varsa. Hatta bekleme durdurmak ve program kapatmak zordur.  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <a name="GetURLContents"></a>Zaman uyumsuz bir yöntem GetURLContents dönüştürmek için  
  
1.  Zaman uyumsuz bir çözüme zaman uyumlu çözüm dönüştürmek için başlatmak için en iyi yerdir bulunduğu `GetURLContents` çünkü çağrıları <xref:System.Net.HttpWebRequest> yöntemi <xref:System.Net.HttpWebRequest.GetResponse%2A> ve <xref:System.IO.Stream> yöntemi <xref:System.IO.Stream.CopyTo%2A> burada web uygulama erişen olan . .NET Framework dönüştürme her iki yöntem zaman uyumsuz sürümlerini sağlayarak kolaylaştırır.  
  
     Kullanılan yöntemleri hakkında daha fazla bilgi için `GetURLContents`, bkz: <xref:System.Net.WebRequest>.  
  
    > [!NOTE]
    >  Bu izlenecek adımları izlediğiniz gibi birkaç derleyici hataları görünür. Bunları yoksay ve kılavuz ile devam edebilirsiniz.  
  
     Üçüncü satırında adlı yöntemini değiştirme `GetURLContents` gelen `GetResponse` için zaman uyumsuz, görev tabanlı <xref:System.Net.WebRequest.GetResponseAsync%2A> yöntemi.  
  
    ```csharp  
    using (WebResponse response = webReq.GetResponseAsync())  
    ```  
  
2.  `GetResponseAsync`döndüren bir <xref:System.Threading.Tasks.Task%601>. Bu durumda, *görev dönüş değişkeni*, `TResult`, türüne sahip <xref:System.Net.WebResponse>. Gerçek bir üretmek için promise görevdir `WebResponse` istenen veri indirilir ve görevin tamamlanması çalıştıktan sonra nesnesi.  
  
     Alınacak `WebResponse` görevden değer, geçerli bir [await](../../../../csharp/language-reference/keywords/await.md) çağrısına işleci `GetResponseAsync`, aşağıdaki kodda gösterildiği gibi.  
  
    ```csharp  
    using (WebResponse response = await webReq.GetResponseAsync())  
    ```  
  
     `await` İşleci geçerli yönteminin yürütülmesi askıya `GetURLContents`, awaited görevi tamamlanana kadar. Bu arada, denetim geçerli yöntemi çağırana döndürür. Bu örnekte, geçerli bir yöntemdir `GetURLContents`, ve çağrıyı yapan `SumPageSizes`. Görev tamamlandığında taahhüt `WebResponse` nesne awaited görev değeri olarak üretilen ve değişkenine atanan `response`.  
  
     Önceki deyimi ne olacağını açıklamak için aşağıdaki iki deyime ayrılabilir.  
  
    ```csharp  
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();  
    //using (WebResponse response = await responseTask)  
    ```  
  
     Çağrı `webReq.GetResponseAsync` döndüren bir `Task(Of WebResponse)` veya `Task<WebResponse>`. Görevi almak için bir bekleme işleç uygulanan sonra `WebResponse` değeri.  
  
     Zaman uyumsuz yöntem görev tamamlanma bağımlı değil yapmak için iş varsa, yöntemi zaman uyumsuz yöntem ve önce çağrısından sonra bu iki ifade arasındaki, iş ile devam edebilirsiniz `await` işleci uygulanır. Örnekler için bkz [nasıl yapılır: zaman uyumsuz kullanarak birden çok Web isteğini paralel hale ve await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) ve [nasıl yapılır: Task.WhenAll kullanarak (C#) tarafından izlenecek zaman uyumsuz genişletmek](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
3.  Eklediğiniz çünkü `await` işleci önceki adımda, bir derleyici hatası oluşur. İşleç ile işaretlenmiş yöntemleri kullanılabilir [zaman uyumsuz](../../../../csharp/language-reference/keywords/async.md) değiştiricisi. Çağrı değiştirmek için dönüştürme adımları yineleyin sırada hatayı yok sayıp `CopyTo` çağrısıyla `CopyToAsync`.  
  
    -   İçin çağrılan yöntemin adını değiştirmek <xref:System.IO.Stream.CopyToAsync%2A>.  
  
    -   `CopyTo` Veya `CopyToAsync` yöntemi için bağımsız değişkeni, bayt kopyalar `content`ve anlamlı bir değer döndürmüyor. Zaman uyumlu sürümünde, çağrısı `CopyTo` bir değer döndürmüyor basit bir ifadedir. Zaman uyumsuz sürümü `CopyToAsync`, döndüren bir <xref:System.Threading.Tasks.Task>. Görev "Task(void)" gibi çalışır ve yöntem beklemenin sağlar. Uygulama `Await` veya `await` çağrısına `CopyToAsync`, aşağıdaki kodda gösterildiği gibi.  
  
        ```csharp  
        await responseStream.CopyToAsync(content);  
        ```  
  
         Önceki deyimi aşağıdaki iki kod satırı kısaltmasıdır.  
  
        ```csharp  
        // CopyToAsync returns a Task, not a Task<T>.  
        //Task copyTask = responseStream.CopyToAsync(content);  
  
        // When copyTask is completed, content contains a copy of  
        // responseStream.  
        //await copyTask;  
        ```  
  
4.  Tüm bu tamamlandı olarak kalır `GetURLContents` yöntem imzası ayarlamak için. Kullanabileceğiniz `await` ile işaretlenmiş yöntemleri işlecinde [zaman uyumsuz](../../../../csharp/language-reference/keywords/async.md) değiştiricisi. Yöntemi olarak işaretlemek için değiştiricisi eklemek bir *async yöntemi*, aşağıdaki kodda gösterildiği gibi.  
  
    ```csharp  
    private async byte[] GetURLContents(string url)  
    ```  
  
5.  Bir zaman uyumsuz yöntemin dönüş türünü yalnızca olabilir <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, veya `void` C#. Genellikle, dönüş türü `void` yalnızca bir zaman uyumsuz olay işleyicisi, kullanılan nerede `void` gereklidir. Diğer durumlarda, kullandığınız `Task(T)` tamamlanmış yöntemi varsa bir [dönmek](../../../../csharp/language-reference/keywords/return.md) T değeri döndüren ifadesi yazın ve kullandığınız `Task` tamamlanmış yöntemi anlamlı bir değere döndürmezse. Düşünebilirsiniz `Task` dönüş türü olarak "Task(void)." anlamına gelir  
  
     Daha fazla bilgi için bkz: [zaman uyumsuz dönüş türleri (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
     Yöntem `GetURLContents` bir dönüş ifadesi içeriyor ve deyim bir bayt dizisi döndürür. Bu nedenle, zaman uyumsuz sürümü dönüş türü T bir bayt dizisi olduğu Task(T) ' dir. Yöntem imzası aşağıdaki değişiklikleri yapın:  
  
    -   Dönüş türünü değiştir `Task<byte[]>`.  
  
    -   Kurala göre zaman uyumsuz yöntemleri "Zaman uyumsuz," bitiş adlara sahip şekilde yöntemi yeniden adlandırma `GetURLContentsAsync`.  
  
     Aşağıdaki kod bu değişiklikleri gösterir.  
  
    ```csharp  
    private async Task<byte[]> GetURLContentsAsync(string url)  
    ```  
  
     Dönüştürme işlemi birkaç bu değişikliklerle `GetURLContents` zaman uyumsuz bir yöntem tamamlandığında.  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <a name="SumPageSizes"></a>Zaman uyumsuz bir yöntem SumPageSizes dönüştürmek için  
  
1.  İçin önceki yordamdaki adımları yineleyin `SumPageSizes`. İlk olarak, araması olarak değiştirmelerine `GetURLContents` zaman uyumsuz bir çağrı için.  
  
    -   Yönteminden çağrılan yöntemin adını değiştirmek `GetURLContents` için `GetURLContentsAsync`, zaten yapmadıysanız.  
  
    -   Uygulama `await` göreve, `GetURLContentsAsync` bayt edinme döndürür dizi değeri.  
  
     Aşağıdaki kod bu değişiklikleri gösterir.  
  
    ```csharp  
    byte[] urlContents = await GetURLContentsAsync(url);  
    ```  
  
     Önceki atama kod aşağıdaki iki satırı kısaltmasıdır.  
  
    ```csharp  
    // GetURLContentsAsync returns a Task<T>. At completion, the task  
    // produces a byte array.  
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
    //byte[] urlContents = await getContentsTask;  
    ```  
  
2.  Yöntemin imzada aşağıdaki değişiklikleri yapın:  
  
    -   Yöntemiyle işaretlemek `async` değiştiricisi.  
  
    -   "Zaman uyumsuz" yöntem adını ekleyin.  
  
    -   T, hiçbir görev dönüş değişkeni bu süresi yoktur çünkü `SumPageSizesAsync` T. için bir değer döndürmüyor (Yöntem sahip olmayan `return` deyimi.) Ancak, yöntem döndürmelidir bir `Task` bildirdiğimize olmalıdır. Bu nedenle, yöntemden dönüş türünü değiştirme `void` için `Task`.  
  
     Aşağıdaki kod bu değişiklikleri gösterir.  
  
    ```csharp  
    private async Task SumPageSizesAsync()  
    ```  
  
     Dönüştürülmesi `SumPageSizes` için `SumPageSizesAsync` tamamlandı.  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <a name="startButton"></a>Zaman uyumsuz bir yöntem startButton_Click dönüştürmek için  
  
1.  Olay işleyicisinin çağrılan yöntemin adını değiştirmek `SumPageSizes` için `SumPageSizesAsync`, zaten yapmadıysanız.  
  
2.  Çünkü `SumPageSizesAsync` bir zaman uyumsuz yöntem sonucu beklemek için olay işleyicisini kodda değişiklik.  
  
     Çağrı `SumPageSizesAsync` çağrısı yansıtan `CopyToAsync` içinde `GetURLContentsAsync`. Çağrı döndürür bir `Task`değil bir `Task(T)`.  
  
     Önceki yordamları olduğu gibi bir deyim veya iki deyimleri kullanarak çağrı dönüştürebilirsiniz. Aşağıdaki kod bu değişiklikleri gösterir.  
  
    ```csharp  
    // One-step async call.  
    await SumPageSizesAsync();  
  
    // Two-step async call.  
    //Task sumTask = SumPageSizesAsync();  
    //await sumTask;  
    ```  
  
3.  Yanlışlıkla işlemi yeniden girme önlemek için aşağıdaki en üstünde deyimine `startButton_Click` devre dışı bırakmak için **Başlat** düğmesi.  
  
    ```csharp  
    // Disable the button until the operation is complete.  
    startButton.IsEnabled = false;  
    ```  
  
     Olay işleyicisinin sonunda düğmesini yeniden etkinleştirebilirsiniz.  
  
    ```csharp  
    // Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = true;  
    ```  
  
     Yeniden giriş hakkında daha fazla bilgi için bkz: [zaman uyumsuz uygulamalarda (C#) yeniden girişi işleme](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).  
  
4.  Son olarak, ekleme `async` bildirimine değiştiricisi böylece olay işleyicisi await `SumPagSizesAsync`.  
  
    ```csharp  
    private async void startButton_Click(object sender, RoutedEventArgs e)  
    ```  
  
     Olay işleyicileri adları genellikle değiştirilmez. Dönüş türü için değiştirilmez `Task` olay işleyicileri dönüştürüldüğünden `void`.  
  
     Proje dönüştürme için zaman uyumsuz zaman uyumlu işleme işlemi tamamlanır.  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <a name="testAsynch"></a>Zaman uyumsuz çözümü test etmek için  
  
1.  Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.  
  
2.  Zaman uyumlu çözüm çıktısını benzer bir çıktı görüntülenmesi gerekir. Ancak, aşağıdaki farkları dikkat edin.  
  
    -   Sonuçları tüm işleme işlemi tamamlandıktan sonra aynı anda oluşmaz. Örneğin, her iki programı bir satır içeren `startButton_Click` metin kutusu temizler. Seçerseniz çalıştırmaları arasında metin kutusu temizlemek için amacı olan **Başlat** bir sonuç kümesi göründükten sonra ikinci bir kez düğmesi. Yalnızca sayıları zaman indirmeleri tamamlandı ve diğer iş yapmak kullanıcı Arabirimi iş parçacığı ücretsizdir ikinci kez görünmesi zaman uyumlu bir sürümde metin kutusu işaretli değildir. Seçtiğiniz hemen sonra metin kutusuna zaman uyumsuz bir sürümde temizler **Başlat** düğmesi.  
  
    -   En önemlisi, kullanıcı Arabirimi iş parçacığı yüklemeleri sırasında engellenmiş değil. Taşıma veya web kaynakları karşıdan yüklenirken pencereyi yeniden boyutlandırmak sayılan ve görüntülenir. Web sitelerinden birini yavaş veya yanıt vermiyor işlemi seçerek iptal edebilir **Kapat** düğmesi (sağ üst köşesinde kırmızı alanında x).  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <a name="GetURLContentsAsync"></a>.NET Framework yöntemiyle yöntemi GetURLContentsAsync değiştirmek için  
  
1.  .NET Framework 4.5 kullanabileceğiniz birçok zaman uyumsuz yöntemleri sağlar. Bunlardan biri <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, bu kılavuz için gerekenler yalnızca yapar. Bunun yerine kullanabileceğiniz `GetURLContentsAsync` bir önceki yordamda oluşturduğunuz yöntemi.  
  
     İlk adım oluşturmaktır bir `HttpClient` yöntemi nesnesinde `SumPageSizesAsync`. Aşağıdaki bildirimi yöntemi başlangıcında ekleyin.  
  
    ```csharp  
    // Declare an HttpClient object and increase the buffer size. The  
    // default buffer size is 65,536.  
    HttpClient client =  
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
    ```  
  
2.  İçinde `SumPageSizesAsync,` çağrısı değiştirin, `GetURLContentsAsync` çağrısıyla yöntemi `HttpClient` yöntemi.  
  
    ```csharp  
    byte[] urlContents = await client.GetByteArrayAsync(url);  
    ```  
  
3.  Kaldırın veya çıkışı açıklama `GetURLContentsAsync` yazdığınız yöntemi.  
  
4.  Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.  
  
     Bu projenin sürümü davranışını "zaman uyumsuz çözümü test etmek için" yordamı açıklanan davranışı eşleşen ancak sizden daha az çaba ile bile gerekir.  
  
##  <a name="BKMK_CompleteCodeExamples"></a>Örnek  
 Aşağıdaki kod dönüştürme eş zamanlı işlemini zaman uyumsuz bir çözüm için tam örnek içeriyor zaman uyumsuz kullanarak `GetURLContentsAsync` yazdığınız yöntemi. Bunu kesinlikle özgün, zaman uyumlu çözüm benzer dikkat edin.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Disable the button until the operation is complete.  
            startButton.IsEnabled = false;  
  
            resultsTextBox.Clear();  
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            // Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
  
            // Reenable the button in case you want to run the operation again.  
            startButton.IsEnabled = true;  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            var total = 0;  
  
            foreach (var url in urlList)  
            {  
                byte[] urlContents = await GetURLContentsAsync(url);  
  
                // The previous line abbreviates the following two assignment statements.  
  
                // GetURLContentsAsync returns a Task<T>. At completion, the task  
                // produces a byte array.  
                //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
                //byte[] urlContents = await getContentsTask;  
  
                DisplayResults(url, urlContents);  
  
                // Update the total.            
                total += urlContents.Length;  
            }  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        private async Task<byte[]> GetURLContentsAsync(string url)  
        {  
            // The downloaded resource ends up in the variable named content.  
            var content = new MemoryStream();  
  
            // Initialize an HttpWebRequest for the current URL.  
            var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
            // Send the request to the Internet resource and wait for  
            // the response.                  
            using (WebResponse response = await webReq.GetResponseAsync())  
  
            // The previous statement abbreviates the following two statements.  
  
            //Task<WebResponse> responseTask = webReq.GetResponseAsync();  
            //using (WebResponse response = await responseTask)  
            {  
                // Get the data stream that is associated with the specified url.  
                using (Stream responseStream = response.GetResponseStream())  
                {  
                    // Read the bytes in responseStream and copy them to content.   
                    await responseStream.CopyToAsync(content);  
  
                    // The previous statement abbreviates the following two statements.  
  
                    // CopyToAsync returns a Task, not a Task<T>.  
                    //Task copyTask = responseStream.CopyToAsync(content);  
  
                    // When copyTask is completed, content contains a copy of  
                    // responseStream.  
                    //await copyTask;  
                }  
            }  
            // Return the result as a byte array.  
            return content.ToArray();  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
 Aşağıdaki kodu kullanan çözüm tam örneği içerir `HttpClient` yöntemi, `GetByteArrayAsync`.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
  
            // Disable the button until the operation is complete.  
            startButton.IsEnabled = false;  
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            //// Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
  
            // Reenable the button in case you want to run the operation again.  
            startButton.IsEnabled = true;  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Declare an HttpClient object and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client =  
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            var total = 0;  
  
            foreach (var url in urlList)  
            {  
                // GetByteArrayAsync returns a task. At completion, the task  
                // produces a byte array.  
                byte[] urlContents = await client.GetByteArrayAsync(url);                 
  
                // The following two lines can replace the previous assignment statement.  
                //Task<byte[]> getContentsTask = client.GetByteArrayAsync(url);  
                //byte[] urlContents = await getContentsTask;  
  
                DisplayResults(url, urlContents);  
  
                // Update the total.  
                total += urlContents.Length;  
            }  
  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Zaman uyumsuz örnek: Web gözden geçirme (C# ve Visual Basic) erişme](http://go.microsoft.com/fwlink/?LinkId=255191)  
 [zaman uyumsuz](../../../../csharp/language-reference/keywords/async.md)  
 [await](../../../../csharp/language-reference/keywords/await.md)  
 [Zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
 [Zaman uyumsuz dönüş türleri (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [Görev tabanlı zaman uyumsuz programlama (TAP)](http://go.microsoft.com/fwlink/?LinkId=204847)  
 [Nasıl yapılır: Task.WhenAll (C#) kullanarak tarafından izlenecek zaman uyumsuz genişletme](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)  
 [Nasıl yapılır: birden çok Web isteğini paralel olarak zaman uyumsuz kullanarak ve olun await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
