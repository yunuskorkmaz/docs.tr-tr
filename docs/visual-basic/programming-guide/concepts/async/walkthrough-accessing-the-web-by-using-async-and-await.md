---
title: "İzlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await (Visual Basic)"
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: a9eb9f53b456b309997ef9e6fdb83b770478889b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379126"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a>İzlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await (Visual Basic)
Async ve await özelliklerini kullanarak zaman uyumsuz programları daha kolay ve sezgisel bir şekilde yazabilirsiniz. Zaman uyumlu kod gibi görünen zaman uyumsuz kod yazabilir ve zor geri çağırma işlevleri ve zaman uyumsuz kod genellikle kapsar devamlılıklar derleyici olanak tanır.  
  
 Async özelliği hakkında daha fazla bilgi için bkz. [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Bu izlenecek yol, Web sitelerinin bir listesiyle bayt sayısını toplar. zaman uyumlu bir Windows Presentation Foundation (WPF) uygulaması ile başlar. İzlenecek yol, yeni özellikleri kullanarak zaman uyumsuz bir çözümü uygulamaya ardından dönüştürür.  
  
 Uygulamaları kendiniz yapılandırmak istemiyorsanız indirebilirsiniz "zaman uyumsuz örneği: İzlenecek yol erişme (C# ve Visual Basic) "den [geliştirici kodu örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).  
  
 Bu kılavuzda, aşağıdaki görevleri tamamlayın:  
  
-   [Bir WPF uygulaması oluşturmak için](#CreateWPFApp)  
  
-   [Basit bir WPF MainWindow tasarlamak için](#MainWindow)  
  
-   [Bir başvuru eklemek için](#AddRef)  
  
-   [Gerekli içeri aktarmaları deyimleri ekleme](#ImportsState)  
  
-   [Zaman uyumlu bir uygulama oluşturmak için](#synchronous)  
  
-   [Zaman uyumlu bir çözümü test etmek için](#testSynch)  
  
-   [Zaman uyumsuz bir yöntem GetURLContents dönüştürmek için](#GetURLContents)  
  
-   [Zaman uyumsuz bir yöntem SumPageSizes dönüştürmek için](#SumPageSizes)  
  
-   [Zaman uyumsuz bir yöntem startButton_Click dönüştürmek için](#startButton)  
  
-   [Zaman uyumsuz bir çözümü test etmek için](#testAsynch)  
  
-   [Bir .NET Framework yöntemi ile yöntem GetURLContentsAsync değiştirmek için](#GetURLContentsAsync)  
  
-   [Örnek](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bilgisayarınızda Visual Studio 2012 veya üzeri yüklenmelidir. Daha fazla bilgi için [Microsoft Web sitesi](https://go.microsoft.com/fwlink/?LinkId=235233).  
  
### <a name="CreateWPFApp"></a> Bir WPF uygulaması oluşturmak için  
  
1.  Visual Studio’yu çalıştırın.  
  
2.  Menü çubuğunda, **dosya**, **yeni**, **proje**.  
  
     **Yeni proje** iletişim kutusu açılır.  
  
3.  İçinde **yüklü şablonlar** bölmesinde, Visual Basic seçin ve ardından **WPF uygulaması** proje türleri listesinden.  
  
4.  İçinde **adı** metin kutusuna `AsyncExampleWPF`ve ardından **Tamam** düğmesi.  
  
     Yeni Proje görünür **Çözüm Gezgini**.  
  
## <a name="BKMK_DesignWPFMainWin"></a>   
### <a name="MainWindow"></a> Basit bir WPF MainWindow tasarlamak için  
  
1.  Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.  
  
2.  Varsa **araç kutusu** penceresi görünür ve açık değilse **görünümü** menüsünde ve ardından **araç kutusu**.  
  
3.  Ekleme bir **düğmesi** denetimi ve bir **TextBox** denetimini **MainWindow** penceresi.  
  
4.  Vurgulama **TextBox** denetim hem de **özellikleri** penceresinde aşağıdaki değerleri ayarlayın:  
  
    -   Ayarlama **adı** özelliğini `resultsTextBox`.  
  
    -   Ayarlama **yükseklik** 250 özelliği.  
  
    -   Ayarlama **genişliği** 500 özelliği.  
  
    -   Üzerinde **metin** sekmesinde, Lucida konsol veya genel tek aralıklı gibi sabit genişlikli bir yazı tipi belirtin.  
  
5.  Vurgulama **düğmesi** denetim hem de **özellikleri** penceresinde aşağıdaki değerleri ayarlayın:  
  
    -   Ayarlama **adı** özelliğini `startButton`.  
  
    -   Değiştirin **içerik** özelliğinden **düğmesi** için **Başlat**.  
  
6.  Metin kutusu ve düğme hem görünmesini sağlayacak şekilde konumlandırın **MainWindow** penceresi.  
  
     WPF XAML Tasarımcısı hakkında daha fazla bilgi için bkz. [XAML Tasarımcısını kullanarak kullanıcı Arabirimi oluşturma](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).  
  
## <a name="BKMK_AddReference"></a>   
### <a name="AddRef"></a> Bir başvuru eklemek için  
  
1.  İçinde **Çözüm Gezgini**, projenizin adını vurgulayın.  
  
2.  Menü çubuğunda, **proje**, **Başvuru Ekle**.  
  
     **Başvuru Yöneticisi** iletişim kutusu görüntülenir.  
  
3.  İletişim kutusunun en üstünde, projeniz .NET Framework 4.5 veya üzerini hedeflediğinden doğrulayın.  
  
4.  İçinde **derlemeleri** alanında seçin **Framework** tercih değildir.  
  
5.  Adları listesinde seçin **System.Net.Http** onay kutusu.  
  
6.  Seçin **Tamam** iletişim kutusunu kapatmak için düğme.  
  
## <a name="BKMK_AddStatesandDirs"></a>   
### <a name="ImportsState"></a> Gerekli içeri aktarmaları deyimleri ekleme  
  
1.  İçinde **Çözüm Gezgini**MainWindow.xaml.vb için kısayol menüsünü açın ve ardından **kodu görüntüle**.  
  
2.  Aşağıdaki `Imports` zaten mevcut değillerse kod dosyasının en üstüne deyimlerini.  
  
    ```vb  
    Imports System.Net.Http  
    Imports System.Net  
    Imports System.IO  
    ```  
  
## <a name="BKMK_CreatSynchApp"></a>   
### <a name="synchronous"></a> Zaman uyumlu bir uygulama oluşturmak için  
  
1.  Tasarım penceresinde, MainWindow.xaml **Başlat** oluşturmak için düğmeyi `startButton_Click` MainWindow.xaml.vb olay işleyicisi.  
  
2.  MainWindow.xaml.vb içinde gövdesine aşağıdaki kodu kopyalayın `startButton_Click`:  
  
    ```vb  
    resultsTextBox.Clear()  
    SumPageSizes()  
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."  
    ```  
  
     Kod uygulama sürücüleri yöntemini çağırır `SumPageSizes`ve denetim döndüğünde, bir ileti görüntüler `startButton_Click`.  
  
3.  Aşağıdaki dört yöntemi zaman uyumlu çözüm için kod içerir:  
  
    -   `SumPageSizes`, Web sayfasını URL'lerin bir listesini alır `SetUpURLList` ve `GetURLContents` ve `DisplayResults` her URL işlenecek.  
  
    -   `SetUpURLList`, yapar ve web adreslerinden oluşan bir liste döndürür.  
  
    -   `GetURLContents`, her bir Web sitesinin içeriklerini karşıdan yükler ve içeriği bir bayt dizisi olarak döndürür.  
  
    -   `DisplayResults`, görüntüleyen bayt bayt dizisindeki her URL.  
  
     Aşağıdaki dört yöntemi kopyalayın ve yapıştırın altında `startButton_Click` MainWindow.xaml.vb olay işleyicisinde:  
  
    ```vb  
    Private Sub SumPageSizes()  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            ' GetURLContents returns the contents of url as a byte array.  
            Dim urlContents As Byte() = GetURLContents(url)  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "Total bytes returned:  {0}" & vbCrLf, total)  
    End Sub  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Function GetURLContents(url As String) As Byte()  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        ' Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.  
        Using response As WebResponse = webReq.GetResponse()  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                responseStream.CopyTo(content)  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "https://".  
        Dim displayURL = url.Replace("https://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
    ```  
  
## <a name="BKMK_TestSynchSol"></a>   
### <a name="testSynch"></a> Zaman uyumlu bir çözümü test etmek için  
  
1.  Programı çalıştırın ve ardından F5 tuşuna basın **Başlat** düğmesi.  
  
     Aşağıdaki listede benzer bir çıktı görünmelidir.  
  
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
  
     Sayıları görüntülemek için birkaç saniye sürer dikkat edin. İstenen kaynaklara indirmek beklediği sırada bu süre boyunca, kullanıcı Arabirimi iş parçacığı engellenir. Sonuç olarak, taşıyamazsınız, en üst düzeye çıkarmak, en aza indirmek veya seçtiğiniz sonra bile görüntü penceresini kapatın **Başlat** düğmesi. Görüntülenecek bayt sayısını başlatana kadar bu çalışmaların başarısız. Bir Web sitesi yanıt vermediği takdirde başarısız hangi sitenin herhangi bir gösterge sahip olursunuz. Programı kapatmak ve bile beklemek istemiyorsanız zordur.  
  
## <a name="BKMK_ConvertGtBtArr"></a>   
### <a name="GetURLContents"></a> Zaman uyumsuz bir yöntem GetURLContents dönüştürmek için  
  
1.  Zaman uyumlu çözüm için zaman uyumsuz bir çözümün dönüştürmek için başlatmak için en iyi yeri yer `GetURLContents` çünkü çağrıları <xref:System.Net.HttpWebRequest> yöntemi <xref:System.Net.HttpWebRequest.GetResponse%2A> ve <xref:System.IO.Stream> yöntemi <xref:System.IO.Stream.CopyTo%2A> uygulamaya web eriştiği olan . .NET Framework dönüştürme iki yöntem de zaman uyumsuz sürümlerini sağlanarak kolaylaştırır.  
  
     Kullanılan yöntemleri hakkında daha fazla bilgi için `GetURLContents`, bkz: <xref:System.Net.WebRequest>.  
  
    > [!NOTE]
    >  Bu izlenecek yolda adımları gibi birkaç derleyici hatalar görüntülenir. Bunların yoksayılması ve adım adım kılavuza devam edebilirsiniz.  
  
     Üçüncü satırında çağrılan yöntem Değiştir `GetURLContents` gelen `GetResponse` için zaman uyumsuz, görev tabanlı <xref:System.Net.WebRequest.GetResponseAsync%2A> yöntemi.  
  
    ```vb  
    Using response As WebResponse = webReq.GetResponseAsync()  
    ```  
  
2.  `GetResponseAsync` döndürür bir <xref:System.Threading.Tasks.Task%601>. Bu durumda, *görev dönüş değişkeni*, `TResult`, türünde <xref:System.Net.WebResponse>. Görev bir gerçek üretmek için bir vaattir `WebResponse` istenen veri indirildi ve görevin çalıştırılıp tamamlandıktan sonra nesne.  
  
     Alınacak `WebResponse` görevden değer, geçerli bir [Await](../../../../visual-basic/language-reference/operators/await-operator.md) işleci çağrısına `GetResponseAsync`aşağıdaki kodda gösterildiği gibi.  
  
    ```vb  
    Using response As WebResponse = Await webReq.GetResponseAsync()  
    ```  
  
     `Await` İşleci geçerli yöntemin yürütülmesini askıya `GetURLContents`, beklenen görev tamamlanana kadar. Bu sırada, denetim geçerli yöntemi çağırana döner. Bu örnekte, geçerli bir yöntemdir `GetURLContents`, ve çağıran `SumPageSizes`. Görev tamamlandığında, taahhüt `WebResponse` nesne imzalamasına değeri olarak üretilen ve değişkenine atanan `response`.  
  
     Önceki deyim ne olduğunu açıklamak için aşağıdaki iki ifadeye ayrılabilir.  
  
    ```vb  
    'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()  
    'Using response As WebResponse = Await responseTask  
    ```  
  
     Çağrı `webReq.GetResponseAsync` döndürür bir `Task(Of WebResponse)` veya `Task<WebResponse>`. Ardından bir `Await` işleci almak için göreve uygulanır `WebResponse` değeri.  
  
     Zaman uyumsuz yöntem görev öğesinin tamamlanmasına bağlı olmayan bağımsız yapılacak çalışmaya sahipse yöntemin zaman uyumsuz yöntemin ve await işleci uygulanır önce çağırdıktan sonra bu iki deyimden arasındaki, iş devam edebilirsiniz. Örnekler için bkz [nasıl yapılır: Zaman uyumsuz kullanarak birden çok Web isteğini paralel hale getirme ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) ve [nasıl yapılır: (Visual Basic) Task.WhenAll kullanarak zaman uyumsuz izlenecek yolu genişletme](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
3.  Eklediğiniz çünkü `Await` işleci önceki adımda, bir derleyici hatası oluşur. İşleci ile işaretlenmiş yöntemler kullanılabilir [zaman uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md) değiştiricisi. Çağrısını için dönüştürme adımı yineleyin ancak hatasını görmezden Gel `CopyTo` çağrısıyla `CopyToAsync`.  
  
    -   İçin çağrılan yöntemin adını değiştirmek <xref:System.IO.Stream.CopyToAsync%2A>.  
  
    -   `CopyTo` Veya `CopyToAsync` yöntemi, bağımsız değişkeni için bayt kopyalar `content`ve anlamlı bir değer döndürmüyor. Zaman uyumlu sürümü, çağrı `CopyTo` bir değer döndürmüyor basit bir ifadedir. Zaman uyumsuz sürümü `CopyToAsync`, döndürür bir <xref:System.Threading.Tasks.Task>. Görev "Task(void)" gibi çalışır ve beklenmesini yöntemi sağlar. Uygulama `Await` veya `await` çağrısına `CopyToAsync`aşağıdaki kodda gösterildiği gibi.  
  
        ```vb  
        Await responseStream.CopyToAsync(content)  
        ```  
  
         Önceki deyim, aşağıdaki iki kod satırlarını kısaltmasıdır.  
  
        ```vb  
        ' CopyToAsync returns a Task, not a Task<T>.  
        'Dim copyTask As Task = responseStream.CopyToAsync(content)  
  
        ' When copyTask is completed, content contains a copy of  
        ' responseStream.  
        'Await copyTask  
        ```  
  
4.  Tüm bu yapılması kalır `GetURLContents` yöntem imzası ayarlamak için. Kullanabileceğiniz `Await` ile işaretlenmiş yöntemler işlecinde [zaman uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md) değiştiricisi. Yöntemi olarak işaretlemek için değiştiricisi Ekle bir *zaman uyumsuz yöntem*aşağıdaki kodda gösterildiği gibi.  
  
    ```vb  
    Private Async Function GetURLContents(url As String) As Byte()  
    ```  
  
5.  Zaman uyumsuz bir yöntemin dönüş türü yalnızca olabilir <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>. Visual Basic'te, bir yöntem olmalıdır bir `Function` döndüren bir `Task` veya `Task(Of T)`, ya da yöntem olmalıdır bir `Sub`. Genellikle, bir `Sub` yöntemi yalnızca bir zaman uyumsuz olay işleyicisinde kullanılır nerede `Sub` gereklidir. Diğer durumlarda, kullandığınız `Task(T)` tamamlanmış yöntemi varsa bir [dönüş](../../../../visual-basic/language-reference/statements/return-statement.md) T değeri döndüren bir ifade yazın ve kullandığınız `Task` tamamlanmış yöntemi anlamlı bir değer döndürmezse.  
  
     Daha fazla bilgi için [zaman uyumsuz dönüş türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
     Yöntemi `GetURLContents` bir dönüş ifadesi ve deyim bir bayt dizisi döndürür. Bu nedenle, zaman uyumsuz sürümü dönüş türünü görev(t), burada T bir bayt dizisi, ' dir. Yöntem imzasında aşağıdaki değişiklikleri yapın:  
  
    -   Geri dönüş için değiştirme `Task(Of Byte())`.  
  
    -   Kural gereği, zaman uyumsuz yöntemler "Async," biten sahip. Bu nedenle metodu yeniden adlandırmak `GetURLContentsAsync`.  
  
     Aşağıdaki kod, bu değişiklikleri gösterir.  
  
    ```vb  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
    ```  
  
     Bu birkaç değişiklikle dönüştürülmesi `GetURLContents` zaman uyumsuz bir yöntem tamamlandıktan.  
  
## <a name="BKMK_ConvertSumPagSzs"></a>   
### <a name="SumPageSizes"></a> Zaman uyumsuz bir yöntem SumPageSizes dönüştürmek için  
  
1.  İçin önceki yordamdaki adımları yineleyin `SumPageSizes`. İlk olarak, araması olarak değiştirmelerine `GetURLContents` zaman uyumsuz bir çağrı için.  
  
    -   Yönteminden çağrılan yöntemin adını değiştirmek `GetURLContents` için `GetURLContentsAsync`, zaten yapmadıysanız.  
  
    -   Uygulama `Await` görev, `GetURLContentsAsync` dizi değeri bayt almak için döndürür.  
  
     Aşağıdaki kod, bu değişiklikleri gösterir.  
  
    ```vb  
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
    ```  
  
     Önceki atama aşağıdaki iki kod satırlarını kısaltmasıdır.  
  
    ```vb  
    ' GetURLContentsAsync returns a task. At completion, the task   
    ' produces a byte array.   
    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)   
    'Dim urlContents As Byte() = Await getContentsTask  
    ```  
  
2.  Yöntemin imzası ' aşağıdaki değişiklikleri yapın:  
  
    -   Yöntemi işaretlemek `Async` değiştiricisi.  
  
    -   "Async" yöntem adına ekleyin.  
  
    -   T, hiçbir görev dönüş değişken bu süresi yoktur çünkü `SumPageSizesAsync` t için bir değer döndürmüyor (Yöntemin sahip olmayan `Return` deyimi.) Ancak, yöntem döndürmelidir bir `Task` olması beklenebilir. Bu nedenle, yöntem türü değiştirme `Sub` için `Function`. İşlevin dönüş türü `Task`.  
  
     Aşağıdaki kod, bu değişiklikleri gösterir.  
  
    ```vb  
    Private Async Function SumPageSizesAsync() As Task  
    ```  
  
     Dönüştürme `SumPageSizes` için `SumPageSizesAsync` tamamlandı.  
  
## <a name="BKMK_Cnvrtbttn1"></a>   
### <a name="startButton"></a> Zaman uyumsuz bir yöntem startButton_Click dönüştürmek için  
  
1.  Olay işleyicisi, çağrılan yöntemden adını değiştirmek `SumPageSizes` için `SumPageSizesAsync`, zaten yapmadıysanız.  
  
2.  Çünkü `SumPageSizesAsync` bir zaman uyumsuz yöntem sonucu await için olay işleyicisinde kodu değiştirin.  
  
     Çağrı `SumPageSizesAsync` çağrısı yansıtır `CopyToAsync` içinde `GetURLContentsAsync`. Çağrı döndürür bir `Task`değil bir `Task(T)`.  
  
     Önceki yordamlardan olduğu gibi bir deyim ya da iki ifadeleri kullanarak arama dönüştürebilirsiniz. Aşağıdaki kod, bu değişiklikleri gösterir.  
  
    ```vb  
    '' One-step async call.  
    Await SumPageSizesAsync()  
  
    ' Two-step async call.  
    'Dim sumTask As Task = SumPageSizesAsync()  
    'Await sumTask  
    ```  
  
3.  İşlem yanlışlıkla yeniden girildi önlemek için üstüne aşağıdaki ifadeyi ekleyin `startButton_Click` devre dışı bırakmak için **Başlat** düğmesi.  
  
    ```vb  
    ' Disable the button until the operation is complete.  
    startButton.IsEnabled = False  
    ```  
  
     Olay işleyicisi sonunda düğmeyi yeniden etkinleştirebilirsiniz.  
  
    ```vb  
    ' Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = True  
    ```  
  
     Yeniden giriş hakkında daha fazla bilgi için bkz: [(Visual Basic) zaman uyumsuz uygulamalarda yeniden girişi işleme](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).  
  
4.  Son olarak, ekleme `Async` değiştiricisi bildirimine olay işleyicisi await, böylece `SumPagSizesAsync`.  
  
    ```vb  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
    ```  
  
     Olay işleyicileri adları genellikle değiştirilmez. Dönüş türü için değiştirilmez `Task` olay işleyicileri olması gerektiğinden `Sub` Visual Basic'de yordamlar.  
  
     Proje dönüştürülmesi için zaman uyumsuz zaman uyumlu işlenmesi tamamlanır.  
  
## <a name="BKMK_testAsynchSolution"></a>   
### <a name="testAsynch"></a> Zaman uyumsuz bir çözümü test etmek için  
  
1.  Programı çalıştırın ve ardından F5 tuşuna basın **Başlat** düğmesi.  
  
2.  Zaman uyumlu çözümün çıktıya benzer bir çıktı görünmelidir. Ancak, aşağıdaki farklar dikkat edin.  
  
    -   Sonuçları işleme tamamlandıktan sonra aynı zamanda, tüm oluşmaz. Örneğin, her iki programın bir satır içeren `startButton_Click` , metin kutusuna temizler. Seçerseniz çalıştırmaları arasında metin kutusunu temizlemek için hedefi olan **Başlat** bir sonuç kümesini göründükten sonra ikinci bir kez, düğme. Yalnızca sayıları ne zaman karşıdan yüklemeler tamamlandı ve diğer işlerini gerçekleştirmek kullanıcı Arabirimi iş parçacığı ücretsizdir ikinci kez görünmesi zaman uyumlu bir sürümde, metin kutusu işaretli değildir. Seçtiğiniz hemen sonra metin kutusuna zaman uyumsuz sürümünde temizler **Başlat** düğmesi.  
  
    -   En önemlisi de UI iş parçacığı yüklemeleri sırasında bloke değildir. Geçiş yapabilir veya web kaynakları indirilirken, penceresini yeniden boyutlandırdığınızda sayılan ve görüntülenir. Web sitelerinden birini ise yavaş veya yanıt vermiyor, işlem seçerek iptal edebilirsiniz **Kapat** düğmesine (sağ üst köşesinde kırmızı alanında x).  
  
## <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
### <a name="GetURLContentsAsync"></a> Bir .NET Framework yöntemi ile yöntem GetURLContentsAsync değiştirmek için  
  
1.  .NET Framework 4.5 kullanabileceğiniz pek çok zaman uyumsuz yöntemler sağlar. Bunlardan biri <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, yalnızca bu kılavuz için ihtiyacınız olanları yapar. Bunu yerine `GetURLContentsAsync` bir önceki yordamda oluşturduğunuz yöntemi.  
  
     İlk adım oluşturmaktır bir `HttpClient` yöntemi nesnesinde `SumPageSizesAsync`. Yönteminin başlangıcında aşağıdaki bildirimi ekleyin.  
  
    ```vb  
    ' Declare an HttpClient object and increase the buffer size. The  
    ' default buffer size is 65,536.  
    Dim client As HttpClient =  
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
    ```  
  
2.  İçinde `SumPageSizesAsync,` çağrısını, `GetURLContentsAsync` yöntemi çağrısıyla `HttpClient` yöntemi.  
  
    ```vb  
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ```  
  
3.  Kaldırın veya açıklama `GetURLContentsAsync` yazdığınız yöntemi.  
  
4.  Programı çalıştırın ve ardından F5 tuşuna basın **Başlat** düğmesi.  
  
     Bu sürümü, proje davranışını "zaman uyumsuz bir çözümü test etmek için" yordamı açıklanan davranışı eşleşen ancak sizden daha az çaba ile bile gerekir.  
  
## <a name="BKMK_CompleteCodeExamples"></a> Örnek  
 Zaman uyumsuz kullanarak zaman uyumsuz bir çözüm eş zamanlı dönüştürme tam örneği aşağıdaki kodu içeren `GetURLContentsAsync` yazdığınız yöntemi. Bunu kesinlikle özgün, zaman uyumlu bir çözüm benzer olduğuna dikkat edin.  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        ' Disable the button until the operation is complete.  
        startButton.IsEnabled = False  
  
        resultsTextBox.Clear()  
  
        '' One-step async call.  
        Await SumPageSizesAsync()  
  
        ' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
  
        ' Reenable the button in case you want to run the operation again.  
        startButton.IsEnabled = True  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
            ' The previous line abbreviates the following two assignment statements.  
  
            '//<snippet21>  
            ' GetURLContentsAsync returns a task. At completion, the task  
            ' produces a byte array.  
            'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
            'Dim urlContents As Byte() = Await getContentsTask  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        Using response As WebResponse = Await webReq.GetResponseAsync()  
  
            ' The previous statement abbreviates the following two statements.  
  
            'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()  
            'Using response As WebResponse = Await responseTask  
  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                Await responseStream.CopyToAsync(content)  
  
                ' The previous statement abbreviates the following two statements.  
  
                ' CopyToAsync returns a Task, not a Task<T>.  
                'Dim copyTask As Task = responseStream.CopyToAsync(content)  
  
                ' When copyTask is completed, content contains a copy of  
                ' responseStream.  
                'Await copyTask  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "https://".  
        Dim displayURL = url.Replace("https://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
 Aşağıdaki kod tam örneği kullanan bir çözüm içeren `HttpClient` yöntemi `GetByteArrayAsync`.  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        ' Disable the button until the operation is complete.  
        startButton.IsEnabled = False  
  
        ' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
  
        ' Reenable the button in case you want to run the operation again.  
        startButton.IsEnabled = True  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Declare an HttpClient object and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            ' GetByteArrayAsync returns a task. At completion, the task  
            ' produces a byte array.  
            Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
  
            ' The following two lines can replace the previous assignment statement.  
            'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
            'Dim urlContents As Byte() = Await getContentsTask  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "https://".  
        Dim displayURL = url.Replace("https://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Zaman uyumsuz örneği: İzlenecek yol erişme (C# ve Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [Await İşleci](../../../../visual-basic/language-reference/operators/await-operator.md)
- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
- [Zaman uyumsuz programlama ile Async ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Zaman uyumsuz dönüş türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [Görev tabanlı zaman uyumsuz desen (TAP)](https://go.microsoft.com/fwlink/?LinkId=204847)
- [Nasıl yapılır: (Visual Basic) Task.WhenAll kullanarak zaman uyumsuz izlenecek yolu genişletme](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [Nasıl yapılır: Zaman uyumsuz kullanarak birden çok Web isteğini paralel hale getirme ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
