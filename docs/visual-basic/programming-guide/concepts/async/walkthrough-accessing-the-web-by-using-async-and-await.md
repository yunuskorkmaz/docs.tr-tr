---
title: "İzlenecek yol: Async kullanarak Web'e erişme ve bekleme (Visual Basic)"
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: 535b431fcf8ab5dafa134b8a3c1e2f7eacd6b427
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696513"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a>İzlenecek yol: Async kullanarak Web'e erişme ve bekleme (Visual Basic)
Zaman uyumsuz ve bekleme özelliklerini kullanarak zaman uyumsuz programlar daha kolay ve sezgisel yazabilirsiniz. Zaman uyumlu kod gibi görünüyor zaman uyumsuz kod yazın ve daha zor geri arama işlevleri ve zaman uyumsuz kod genellikle kapsar devamlılıklar işlemek derleyici sağlayabilirsiniz.  
  
 Async özelliği hakkında daha fazla bilgi için bkz: [zaman uyumsuz programlama uyumsuz ve bekleme (Visual Basic) ile](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Bu kılavuzda Web sitelerinin bir listesiyle bayt sayısını toplar zaman uyumlu bir Windows Presentation Foundation (WPF) uygulama başlar. İzlenecek yol sonra yeni özellikleri kullanarak zaman uyumsuz çözümünü uygulamaya dönüştürür.  
  
 Uygulamaları kendiniz yapılandırmak istemiyorsanız, indirebilirsiniz "zaman uyumsuz örnek: Web gözden geçirme (C# ve Visual Basic) erişme" den [Geliştirici kod örnekleri](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).  
  
 Bu kılavuzda, aşağıdaki görevleri tamamlayın:  
  
-   [Bir WPF uygulaması oluşturmak için](#CreateWPFApp)  
  
-   [Basit bir WPF MainWindow tasarlamak için](#MainWindow)  
  
-   [Bir başvuru eklemek için](#AddRef)  
  
-   [Gerekli içeri aktarmaları deyimleri eklemek için](#ImportsState)  
  
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
  
###  <a name="CreateWPFApp"></a> Bir WPF uygulaması oluşturmak için  
  
1.  Visual Studio'yu başlatın.  
  
2.  Menü çubuğunda seçin **dosya**, **yeni**, **proje**.  
  
     **Yeni proje** iletişim kutusu açılır.  
  
3.  İçinde **yüklü şablonlar** bölmesinde, Visual Basic seçin ve ardından **WPF uygulaması** proje türleri listesinden.  
  
4.  İçinde **adı** metin kutusuna `AsyncExampleWPF`ve ardından **Tamam** düğmesi.  
  
     Yeni Proje görünür **Çözüm Gezgini**.  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <a name="MainWindow"></a> Basit bir WPF MainWindow tasarlamak için  
  
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
###  <a name="AddRef"></a> Bir başvuru eklemek için  
  
1.  İçinde **Çözüm Gezgini**, projenizin adını vurgulayın.  
  
2.  Menü çubuğunda seçin **proje**, **Başvuru Ekle**.  
  
     **Başvuru Yöneticisi** iletişim kutusu görüntülenir.  
  
3.  İletişim kutusunun üstündeki projeniz .NET Framework 4.5 veya üstünü hedefleyen olduğunu doğrulayın.  
  
4.  İçinde **derlemeleri** alanı seçin **Framework** tercih değil.  
  
5.  Adları listesinden seçin **System.Net.Http** onay kutusu.  
  
6.  Seçin **Tamam** düğmesi iletişim kutusunu kapatın.  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <a name="ImportsState"></a> Gerekli içeri aktarmaları deyimleri eklemek için  
  
1.  İçinde **Çözüm Gezgini**MainWindow.xaml.vb için kısayol menüsünü açın ve ardından **görünümü kodu**.  
  
2.  Aşağıdakileri ekleyin `Imports` zaten mevcut değillerse kod dosyasının deyimlerini.  
  
    ```vb  
    Imports System.Net.Http  
    Imports System.Net  
    Imports System.IO  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <a name="synchronous"></a> Zaman uyumlu bir uygulama oluşturmak için  
  
1.  Tasarım penceresinde MainWindow.xaml, çift **Başlat** oluşturmak için düğmesini `startButton_Click` MainWindow.xaml.vb olay işleyicisi.  
  
2.  MainWindow.xaml.vb içinde gövdesine aşağıdaki kodu kopyalayın `startButton_Click`:  
  
    ```vb  
    resultsTextBox.Clear()  
    SumPageSizes()  
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."  
    ```  
  
     Kod uygulama sürücüleri yöntemini çağırır `SumPageSizes`ve denetim döndüğünde bir ileti görüntüler `startButton_Click`.  
  
3.  Zaman uyumlu çözüm için kod aşağıdaki dört yöntemi içerir:  
  
    -   `SumPageSizes`, Web sayfası URL'lerden listesini alır `SetUpURLList` ve çağırır `GetURLContents` ve `DisplayResults` her URL işleyemedi.  
  
    -   `SetUpURLList`, hangi yapar ve web adresleri listesi döndürür.  
  
    -   `GetURLContents`, her Web sitesi içeriğini indirir ve içeriği bir bayt dizisi olarak döndürür.  
  
    -   `DisplayResults`, görüntüleyen bayt sayısı bayt dizisi, her URL için.  
  
     Aşağıdaki dört yöntemi kopyalayın ve yapıştırın altında `startButton_Click` MainWindow.xaml.vb olay işleyicisi:  
  
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
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
    ```  
  
##  <a name="BKMK_TestSynchSol"></a>   
###  <a name="testSynch"></a> Zaman uyumlu çözümü test etmek için  
  
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
###  <a name="GetURLContents"></a> Zaman uyumsuz bir yöntem GetURLContents dönüştürmek için  
  
1.  Zaman uyumsuz bir çözüme zaman uyumlu çözüm dönüştürmek için başlatmak için en iyi yerdir bulunduğu `GetURLContents` çünkü çağrıları <xref:System.Net.HttpWebRequest> yöntemi <xref:System.Net.HttpWebRequest.GetResponse%2A> ve <xref:System.IO.Stream> yöntemi <xref:System.IO.Stream.CopyTo%2A> burada web uygulama erişen olan . .NET Framework dönüştürme her iki yöntem zaman uyumsuz sürümlerini sağlayarak kolaylaştırır.  
  
     Kullanılan yöntemleri hakkında daha fazla bilgi için `GetURLContents`, bkz: <xref:System.Net.WebRequest>.  
  
    > [!NOTE]
    >  Bu izlenecek adımları izlediğiniz gibi birkaç derleyici hataları görünür. Bunları yoksay ve kılavuz ile devam edebilirsiniz.  
  
     Üçüncü satırında adlı yöntemini değiştirme `GetURLContents` gelen `GetResponse` için zaman uyumsuz, görev tabanlı <xref:System.Net.WebRequest.GetResponseAsync%2A> yöntemi.  
  
    ```vb  
    Using response As WebResponse = webReq.GetResponseAsync()  
    ```  
  
2.  `GetResponseAsync` döndüren bir <xref:System.Threading.Tasks.Task%601>. Bu durumda, *görev dönüş değişkeni*, `TResult`, türüne sahip <xref:System.Net.WebResponse>. Gerçek bir üretmek için promise görevdir `WebResponse` istenen veri indirilir ve görevin tamamlanması çalıştıktan sonra nesnesi.  
  
     Alınacak `WebResponse` görevden değer, geçerli bir [bekleme](../../../../visual-basic/language-reference/operators/await-operator.md) çağrısına işleci `GetResponseAsync`, aşağıdaki kodda gösterildiği gibi.  
  
    ```vb  
    Using response As WebResponse = Await webReq.GetResponseAsync()  
    ```  
  
     `Await` İşleci geçerli yönteminin yürütülmesi askıya `GetURLContents`, awaited görevi tamamlanana kadar. Bu arada, denetim geçerli yöntemi çağırana döndürür. Bu örnekte, geçerli bir yöntemdir `GetURLContents`, ve çağrıyı yapan `SumPageSizes`. Görev tamamlandığında taahhüt `WebResponse` nesne awaited görev değeri olarak üretilen ve değişkenine atanan `response`.  
  
     Önceki deyimi ne olacağını açıklamak için aşağıdaki iki deyime ayrılabilir.  
  
    ```vb  
    'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()  
    'Using response As WebResponse = Await responseTask  
    ```  
  
     Çağrı `webReq.GetResponseAsync` döndüren bir `Task(Of WebResponse)` veya `Task<WebResponse>`. Ardından bir `Await` işleci almak için göreve uygulanan `WebResponse` değeri.  
  
     Zaman uyumsuz yöntem görev tamamlanma bağımlı değil yapmak için iş varsa, yöntemi zaman uyumsuz yöntem ve bekleme işleci uygulanmadan önce çağrısından sonra bu iki ifade arasındaki, iş devam edebilirsiniz. Örnekler için bkz: [nasıl yapılır: olun birden çok Web isteğini paralel kullanarak zaman uyumsuz ve bekleme (Visual Basic) tarafından](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) ve [nasıl yapılır: Task.WhenAll kullanarak (Visual Basic) tarafından zaman uyumsuz izlenecek yolu genişletme](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
3.  Eklediğiniz çünkü `Await` işleci önceki adımda, bir derleyici hatası oluşur. İşleç ile işaretlenmiş yöntemleri kullanılabilir [zaman uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md) değiştiricisi. Çağrı değiştirmek için dönüştürme adımları yineleyin sırada hatayı yok sayıp `CopyTo` çağrısıyla `CopyToAsync`.  
  
    -   İçin çağrılan yöntemin adını değiştirmek <xref:System.IO.Stream.CopyToAsync%2A>.  
  
    -   `CopyTo` Veya `CopyToAsync` yöntemi için bağımsız değişkeni, bayt kopyalar `content`ve anlamlı bir değer döndürmüyor. Zaman uyumlu sürümünde, çağrısı `CopyTo` bir değer döndürmüyor basit bir ifadedir. Zaman uyumsuz sürümü `CopyToAsync`, döndüren bir <xref:System.Threading.Tasks.Task>. Görev "Task(void)" gibi çalışır ve yöntem beklemenin sağlar. Uygulama `Await` veya `await` çağrısına `CopyToAsync`, aşağıdaki kodda gösterildiği gibi.  
  
        ```vb  
        Await responseStream.CopyToAsync(content)  
        ```  
  
         Önceki deyimi aşağıdaki iki kod satırı kısaltmasıdır.  
  
        ```vb  
        ' CopyToAsync returns a Task, not a Task<T>.  
        'Dim copyTask As Task = responseStream.CopyToAsync(content)  
  
        ' When copyTask is completed, content contains a copy of  
        ' responseStream.  
        'Await copyTask  
        ```  
  
4.  Tüm bu tamamlandı olarak kalır `GetURLContents` yöntem imzası ayarlamak için. Kullanabileceğiniz `Await` ile işaretlenmiş yöntemleri işlecinde [zaman uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md) değiştiricisi. Yöntemi olarak işaretlemek için değiştiricisi eklemek bir *async yöntemi*, aşağıdaki kodda gösterildiği gibi.  
  
    ```vb  
    Private Async Function GetURLContents(url As String) As Byte()  
    ```  
  
5.  Bir zaman uyumsuz yöntemin dönüş türünü yalnızca olabilir <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>. Visual Basic'te yöntemi olmalıdır bir `Function` döndüren bir `Task` veya `Task(Of T)`, veya bir yöntem olmalıdır bir `Sub`. Genellikle, bir `Sub` yöntemi yalnızca bir zaman uyumsuz olay işleyicisi, kullanılan nerede `Sub` gereklidir. Diğer durumlarda, kullandığınız `Task(T)` tamamlanmış yöntemi varsa bir [dönmek](../../../../visual-basic/language-reference/statements/return-statement.md) T değeri döndüren ifadesi yazın ve kullandığınız `Task` tamamlanmış yöntemi anlamlı bir değere döndürmezse.  
  
     Daha fazla bilgi için bkz: [zaman uyumsuz dönüş türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
     Yöntem `GetURLContents` bir dönüş ifadesi içeriyor ve deyim bir bayt dizisi döndürür. Bu nedenle, zaman uyumsuz sürümü dönüş türü T bir bayt dizisi olduğu Task(T) ' dir. Yöntem imzası aşağıdaki değişiklikleri yapın:  
  
    -   Dönüş türünü değiştir `Task(Of Byte())`.  
  
    -   Kurala göre zaman uyumsuz yöntemleri "Zaman uyumsuz," bitiş adlara sahip şekilde yöntemi yeniden adlandırma `GetURLContentsAsync`.  
  
     Aşağıdaki kod bu değişiklikleri gösterir.  
  
    ```vb  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
    ```  
  
     Dönüştürme işlemi birkaç bu değişikliklerle `GetURLContents` zaman uyumsuz bir yöntem tamamlandığında.  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <a name="SumPageSizes"></a> Zaman uyumsuz bir yöntem SumPageSizes dönüştürmek için  
  
1.  İçin önceki yordamdaki adımları yineleyin `SumPageSizes`. İlk olarak, araması olarak değiştirmelerine `GetURLContents` zaman uyumsuz bir çağrı için.  
  
    -   Yönteminden çağrılan yöntemin adını değiştirmek `GetURLContents` için `GetURLContentsAsync`, zaten yapmadıysanız.  
  
    -   Uygulama `Await` göreve, `GetURLContentsAsync` bayt edinme döndürür dizi değeri.  
  
     Aşağıdaki kod bu değişiklikleri gösterir.  
  
    ```vb  
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
    ```  
  
     Önceki atama kod aşağıdaki iki satırı kısaltmasıdır.  
  
    ```vb  
    ' GetURLContentsAsync returns a task. At completion, the task   
    ' produces a byte array.   
    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)   
    'Dim urlContents As Byte() = Await getContentsTask  
    ```  
  
2.  Yöntemin imzada aşağıdaki değişiklikleri yapın:  
  
    -   Yöntemiyle işaretlemek `Async` değiştiricisi.  
  
    -   "Zaman uyumsuz" yöntem adını ekleyin.  
  
    -   T, hiçbir görev dönüş değişkeni bu süresi yoktur çünkü `SumPageSizesAsync` T. için bir değer döndürmüyor (Yöntem sahip olmayan `Return` deyimi.) Ancak, yöntem döndürmelidir bir `Task` bildirdiğimize olmalıdır. Bu nedenle, yöntemi türünden değiştirme `Sub` için `Function`. İşlev dönüş türü `Task`.  
  
     Aşağıdaki kod bu değişiklikleri gösterir.  
  
    ```vb  
    Private Async Function SumPageSizesAsync() As Task  
    ```  
  
     Dönüştürülmesi `SumPageSizes` için `SumPageSizesAsync` tamamlandı.  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <a name="startButton"></a> Zaman uyumsuz bir yöntem startButton_Click dönüştürmek için  
  
1.  Olay işleyicisinin çağrılan yöntemin adını değiştirmek `SumPageSizes` için `SumPageSizesAsync`, zaten yapmadıysanız.  
  
2.  Çünkü `SumPageSizesAsync` bir zaman uyumsuz yöntem sonucu beklemek için olay işleyicisini kodda değişiklik.  
  
     Çağrı `SumPageSizesAsync` çağrısı yansıtan `CopyToAsync` içinde `GetURLContentsAsync`. Çağrı döndürür bir `Task`değil bir `Task(T)`.  
  
     Önceki yordamları olduğu gibi bir deyim veya iki deyimleri kullanarak çağrı dönüştürebilirsiniz. Aşağıdaki kod bu değişiklikleri gösterir.  
  
    ```vb  
    '' One-step async call.  
    Await SumPageSizesAsync()  
  
    ' Two-step async call.  
    'Dim sumTask As Task = SumPageSizesAsync()  
    'Await sumTask  
    ```  
  
3.  Yanlışlıkla işlemi yeniden girme önlemek için aşağıdaki en üstünde deyimine `startButton_Click` devre dışı bırakmak için **Başlat** düğmesi.  
  
    ```vb  
    ' Disable the button until the operation is complete.  
    startButton.IsEnabled = False  
    ```  
  
     Olay işleyicisinin sonunda düğmesini yeniden etkinleştirebilirsiniz.  
  
    ```vb  
    ' Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = True  
    ```  
  
     Yeniden giriş hakkında daha fazla bilgi için bkz: [(Visual Basic) zaman uyumsuz uygulamalarda yeniden girişi işleme](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).  
  
4.  Son olarak, ekleme `Async` bildirimine değiştiricisi böylece olay işleyicisi await `SumPagSizesAsync`.  
  
    ```vb  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
    ```  
  
     Olay işleyicileri adları genellikle değiştirilmez. Dönüş türü için değiştirilmez `Task` olay işleyicileri olması gerektiğinden `Sub` Visual Basic'de yordamlar.  
  
     Proje dönüştürme için zaman uyumsuz zaman uyumlu işleme işlemi tamamlanır.  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <a name="testAsynch"></a> Zaman uyumsuz çözümü test etmek için  
  
1.  Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.  
  
2.  Zaman uyumlu çözüm çıktısını benzer bir çıktı görüntülenmesi gerekir. Ancak, aşağıdaki farkları dikkat edin.  
  
    -   Sonuçları tüm işleme işlemi tamamlandıktan sonra aynı anda oluşmaz. Örneğin, her iki programı bir satır içeren `startButton_Click` metin kutusu temizler. Seçerseniz çalıştırmaları arasında metin kutusu temizlemek için amacı olan **Başlat** bir sonuç kümesi göründükten sonra ikinci bir kez düğmesi. Yalnızca sayıları zaman indirmeleri tamamlandı ve diğer iş yapmak kullanıcı Arabirimi iş parçacığı ücretsizdir ikinci kez görünmesi zaman uyumlu bir sürümde metin kutusu işaretli değildir. Seçtiğiniz hemen sonra metin kutusuna zaman uyumsuz bir sürümde temizler **Başlat** düğmesi.  
  
    -   En önemlisi, kullanıcı Arabirimi iş parçacığı yüklemeleri sırasında engellenmiş değil. Taşıma veya web kaynakları karşıdan yüklenirken pencereyi yeniden boyutlandırmak sayılan ve görüntülenir. Web sitelerinden birini yavaş veya yanıt vermiyor işlemi seçerek iptal edebilir **Kapat** düğmesi (sağ üst köşesinde kırmızı alanında x).  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <a name="GetURLContentsAsync"></a> .NET Framework yöntemiyle yöntemi GetURLContentsAsync değiştirmek için  
  
1.  .NET Framework 4.5 kullanabileceğiniz birçok zaman uyumsuz yöntemleri sağlar. Bunlardan biri <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, bu kılavuz için gerekenler yalnızca yapar. Bunun yerine kullanabileceğiniz `GetURLContentsAsync` bir önceki yordamda oluşturduğunuz yöntemi.  
  
     İlk adım oluşturmaktır bir `HttpClient` yöntemi nesnesinde `SumPageSizesAsync`. Aşağıdaki bildirimi yöntemi başlangıcında ekleyin.  
  
    ```vb  
    ' Declare an HttpClient object and increase the buffer size. The  
    ' default buffer size is 65,536.  
    Dim client As HttpClient =  
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
    ```  
  
2.  İçinde `SumPageSizesAsync,` çağrısı değiştirin, `GetURLContentsAsync` çağrısıyla yöntemi `HttpClient` yöntemi.  
  
    ```vb  
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ```  
  
3.  Kaldırın veya çıkışı açıklama `GetURLContentsAsync` yazdığınız yöntemi.  
  
4.  Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.  
  
     Bu projenin sürümü davranışını "zaman uyumsuz çözümü test etmek için" yordamı açıklanan davranışı eşleşen ancak sizden daha az çaba ile bile gerekir.  
  
##  <a name="BKMK_CompleteCodeExamples"></a> Örnek  
 Aşağıdaki kod dönüştürme eş zamanlı işlemini zaman uyumsuz bir çözüm için tam örnek içeriyor zaman uyumsuz kullanarak `GetURLContentsAsync` yazdığınız yöntemi. Bunu kesinlikle özgün, zaman uyumlu çözüm benzer dikkat edin.  
  
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
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
 Aşağıdaki kodu kullanan çözüm tam örneği içerir `HttpClient` yöntemi, `GetByteArrayAsync`.  
  
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
            }  
        Return urls  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Zaman uyumsuz örnek: Web gözden geçirme (C# ve Visual Basic) erişme](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)  
 [Await İşleci](../../../../visual-basic/language-reference/operators/await-operator.md)  
 [Async](../../../../visual-basic/language-reference/modifiers/async.md)  
 [Zaman uyumsuz programlama ile Async ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Zaman uyumsuz dönüş türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)  
 [Görev tabanlı zaman uyumsuz programlama (TAP)](http://go.microsoft.com/fwlink/?LinkId=204847)  
 [Nasıl yapılır: Task.WhenAll (Visual Basic) kullanarak zaman uyumsuz izlenecek yolu genişletme](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)  
 [Nasıl yapılır: Async kullanarak birden çok Web isteğini paralel hale ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
