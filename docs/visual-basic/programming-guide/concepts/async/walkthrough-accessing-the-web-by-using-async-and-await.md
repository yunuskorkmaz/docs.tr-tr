---
title: "İzlenecek yol: Async ve Await Kullanarak Web'e Erişme"
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: 7f649f1f16da545c4587f0ed76b8f1a443ee8744
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715848"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a>İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)

Zaman uyumsuz programları, zaman uyumsuz/await özelliklerini kullanarak daha kolay ve daha canlı bir şekilde yazabilirsiniz. Zaman uyumlu kod gibi görünen zaman uyumsuz kod yazabilir ve derleyicinin zaman uyumsuz kodun genellikle sahip olduğu zor geri çağırma işlevlerini ve devamlılığını işlemesini sağlayabilirsiniz.

Async özelliği hakkında daha fazla bilgi için bkz. zaman uyumsuz [programlama, Async ve await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).

Bu izlenecek yol, bir Web sitesi listesindeki bayt sayısını toplayan bir zaman uyumlu Windows Presentation Foundation (WPF) uygulamasıyla başlar. İzlenecek yol, yeni özellikleri kullanarak uygulamayı zaman uyumsuz bir çözüme dönüştürür.

Uygulamaları kendiniz derlemek istemiyorsanız,C# [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)"zaman uyumsuz örnek: Web 'e (ve Visual Basic) erişme" ' ya erişebilirsiniz.

Bu kılavuzda, aşağıdaki görevleri tamamlayadınız:

> [!div class="checklist"]
>
> - [WPF uygulaması oluşturma](#create-a-wpf-application)
> - [Basit bir WPF MainWindow tasarımı](#design-a-simple-wpf-mainwindow)
> - [Başvuru ekleme](#add-a-reference)
> - [Gerekli Imports deyimlerini Ekle](#add-necessary-imports-statements)
> - [Zaman uyumlu uygulama oluşturma](#create-a-synchronous-application)
> - [Zaman uyumlu çözümü test etme](#test-the-synchronous-solution)
> - [GetURLContents öğesini zaman uyumsuz bir metoda Dönüştür](#convert-geturlcontents-to-an-asynchronous-method)
> - [Sumpageslikleri zaman uyumsuz bir metoda Dönüştür](#convert-sumpagesizes-to-an-asynchronous-method)
> - [StartButton_Click zaman uyumsuz bir metoda Dönüştür](#convert-startbutton_click-to-an-asynchronous-method)
> - [Zaman uyumsuz çözümü test etme](#test-the-asynchronous-solution)
> - [GetURLContentsAsync yöntemini bir .NET Framework yöntemiyle değiştirin](#replace-the-geturlcontentsasync-method-with-a-net-framework-method)

Tüm zaman uyumsuz örnek için [örnek](#example) bölümüne bakın.

## <a name="prerequisites"></a>Prerequisites

Bilgisayarınızda Visual Studio 2012 veya üzeri yüklü olmalıdır. Daha fazla bilgi için bkz. Visual Studio [İndirmeleri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) sayfası.

## <a name="create-a-wpf-application"></a>WPF uygulaması oluşturma

1. Visual Studio 'Yu başlatın.

2. Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.

    **Yeni proje** iletişim kutusu açılır.

3. **Yüklü şablonlar** bölmesinde Visual Basic öğesini seçin ve ardından Proje türleri listesinden **WPF uygulaması** ' nı seçin.

4. **Ad** metin kutusuna `AsyncExampleWPF`girin ve sonra **Tamam** düğmesini seçin.

    Yeni proje **Çözüm Gezgini**görüntülenir.

## <a name="design-a-simple-wpf-mainwindow"></a>Basit bir WPF MainWindow tasarımı

1. Visual Studio Code düzenleyicisinde **MainWindow. xaml** sekmesini seçin.

2. **Araç kutusu** penceresi görünür değilse, **Görünüm** menüsünü açın ve ardından **araç kutusu**' nu seçin.

3. **MainWindow** penceresine bir **Button** denetimi ve **TextBox** denetimi ekleyin.

4. **TextBox** denetimini vurgulayın ve **Özellikler** penceresinde aşağıdaki değerleri ayarlayın:

    - **Name** özelliğini `resultsTextBox`olarak ayarlayın.

    - **Height** özelliğini 250 olarak ayarlayın.

    - **Width** özelliğini 500 olarak ayarlayın.

    - **Metin** sekmesinde, Lucida Console veya Global tek boşluk gibi tek boşluklu bir yazı tipi belirtin.

5. **Düğme** denetimini vurgulayın ve **Özellikler** penceresinde aşağıdaki değerleri ayarlayın:

    - **Name** özelliğini `startButton`olarak ayarlayın.

    - **İçerik** özelliğinin değerini **düğmeden** **başla**olarak değiştirin.

6. Metin kutusunu ve düğmeyi her ikisinin de **MainWindow** penceresinde görünmesi için konumlandırın.

    WPF XAML Tasarımcısı hakkında daha fazla bilgi için, bkz. [XAML Tasarımcısı kullanarak Kullanıcı arabirimi oluşturma](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).

## <a name="add-a-reference"></a>Başvuru ekleme

1. **Çözüm Gezgini**, projenizin adını vurgulayın.

2. Menü çubuğunda **Proje**, **Başvuru Ekle**' yi seçin.

    **Başvuru Yöneticisi** iletişim kutusu görüntülenir.

3. İletişim kutusunun üst kısmında, projenizin .NET Framework 4,5 veya üstünü hedeflediğinden emin olun.

4. **Derlemeler** alanında, zaten seçili değilse **Framework** ' ü seçin.

5. Ad listesinde, **System .net. http** onay kutusunu seçin.

6. İletişim kutusunu kapatmak için **Tamam** düğmesini seçin.

## <a name="add-necessary-imports-statements"></a>Gerekli Imports deyimlerini Ekle

1. **Çözüm Gezgini**, MainWindow. xaml. vb için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

2. Zaten mevcut değilse, kod dosyasının en üstüne aşağıdaki `Imports` deyimlerini ekleyin.

    ```vb
    Imports System.Net.Http
    Imports System.Net
    Imports System.IO
    ```

## <a name="create-a-synchronous-application"></a>Zaman uyumlu uygulama oluşturma

1. MainWindow. xaml tasarım penceresinde, MainWindow. xaml. vb ' de `startButton_Click` olay işleyicisini oluşturmak için **Başlat** düğmesine çift tıklayın.

2. MainWindow. xaml. vb dosyasında aşağıdaki kodu `startButton_Click`gövdesine kopyalayın:

    ```vb
    resultsTextBox.Clear()
    SumPageSizes()
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."
    ```

    Kod, uygulamayı yönlendiren yöntemi çağırır, `SumPageSizes`ve denetim `startButton_Click`döndüğünde bir ileti görüntüler.

3. Zaman uyumlu çözüm kodu aşağıdaki dört yöntemi içerir:

    - `SumPageSizes`, `SetUpURLList` Web sayfası URL 'Lerinin bir listesini alır ve sonra her bir URL 'YI işlemek için `GetURLContents` ve `DisplayResults` çağırır.

    - `SetUpURLList`, Web adreslerinin bir listesini oluşturan ve döndüren.

    - Her Web sitesinin içeriğini indiren ve bir bayt dizisi olarak içeriği döndüren `GetURLContents`.

    - her URL için bayt dizisindeki bayt sayısını görüntüleyen `DisplayResults`.

    Aşağıdaki dört yöntemi kopyalayın ve sonra MainWindow. xaml. vb ' de `startButton_Click` olay işleyicisi altına yapıştırın:

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

## <a name="test-the-synchronous-solution"></a>Zaman uyumlu çözümü test etme

1. Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.

    Aşağıdaki listeye benzer bir çıktı görünmelidir:

    ```console
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

    Sayıları görüntülemenin birkaç saniye sürdiğine dikkat edin. Bu süre boyunca, Kullanıcı arabirimi iş parçacığı istenen kaynakların indirilmesini beklerken engellenir. Sonuç olarak, **Başlat** düğmesini seçtikten sonra görüntü penceresini taşıyamaz, ekranı kaplamaz, simge durumuna küçültebilir ya da kapatabilirsiniz. Bu çalışmalar, bayt sayıları görünene kadar başarısız olur. Bir Web sitesi yanıt vermiyorsa, hangi sitenin başarısız olduğunun belirtii olmaz. Beklemeyi durdurup programı kapatmanız zordur.

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a>GetURLContents öğesini zaman uyumsuz bir metoda Dönüştür

1. Zaman uyumlu çözümü zaman uyumsuz bir çözüme dönüştürmek için, <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> yöntemine ve <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> yöntemine yapılan çağrılar uygulamanın Web 'e eriştiği yer olduğundan, başlamak için en iyi yer `GetURLContents`. .NET Framework, her iki yöntemin de zaman uyumsuz sürümlerini sağlayarak dönüştürmeyi kolaylaştırır.

    `GetURLContents`' de kullanılan yöntemler hakkında daha fazla bilgi için bkz. <xref:System.Net.WebRequest>.

    > [!NOTE]
    > Bu izlenecek yolda bulunan adımları izleyerek bazı derleyici hataları görüntülenir. Bunları yoksayabilir ve İzlenecek yol ile devam edebilirsiniz.

    `GetURLContents` üçüncü satırındaki `GetResponse` zaman uyumsuz, görev tabanlı <xref:System.Net.WebRequest.GetResponseAsync%2A> metoduna olan yöntemi değiştirin.

    ```vb
    Using response As WebResponse = webReq.GetResponseAsync()
    ```

2. `GetResponseAsync` <xref:System.Threading.Tasks.Task%601>döndürür. Bu durumda, *görev dönüş değişkeni*`TResult`, <xref:System.Net.WebResponse>türü vardır. Görev, istenen veriler indirildikten ve görevin tamamlanmasını çalıştırdıktan sonra gerçek bir `WebResponse` nesnesi oluşturmak için bir taahhüddir.

    Görevden `WebResponse` değerini almak için aşağıdaki kodda gösterildiği gibi, `GetResponseAsync`çağrısına bir [await](../../../../visual-basic/language-reference/operators/await-operator.md) işleci uygulayın.

    ```vb
    Using response As WebResponse = Await webReq.GetResponseAsync()
    ```

    `Await` işleci, beklenen görev tamamlanana kadar, `GetURLContents`geçerli metodun yürütülmesini askıya alır. Bu arada, Denetim geçerli yöntemi çağırana döner. Bu örnekte, geçerli yöntem `GetURLContents`ve arayan `SumPageSizes`. Görev tamamlandığında, taahhüt edilen `WebResponse` nesnesi, beklenen görevin değeri olarak üretilir ve `response`değişkenine atanır.

    Önceki deyim, ne olacağını açıklamak için aşağıdaki iki ifadeye ayrılabilir.

    ```vb
    Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
    Using response As WebResponse = Await responseTask
    ```

    `webReq.GetResponseAsync` çağrısı `Task(Of WebResponse)` veya `Task<WebResponse>`döndürür. Sonra, `WebResponse` değerini almak için göreve bir `Await` işleci uygulanır.

    Zaman uyumsuz yönteminizin, görevin tamamlanmasına bağlı olmaması durumunda, zaman uyumsuz metoda yapılan çağrıdan sonra ve Await işleci uygulanmadan önce bu iki deyim arasında bu işe devam edebilir. Örnekler için bkz. [nasıl yapılır: Async ve await kullanarak birden çok Web Isteğini paralel hale getirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) ve [nasıl yapılır: Task. whenall (Visual Basic) kullanarak zaman uyumsuz izlenecek yolu genişletme](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).

3. Önceki adımda `Await` işlecini eklediğiniz için bir derleyici hatası oluşur. İşleci yalnızca [zaman uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md) değiştiriciyle işaretlenen yöntemlerde kullanılabilir. `CopyTo` çağrısını `CopyToAsync`çağrısı ile değiştirmek için dönüştürme adımlarını tekrarlarken hatayı yoksayın.

    - <xref:System.IO.Stream.CopyToAsync%2A>olarak çağrılan metodun adını değiştirin.

    - `CopyTo` veya `CopyToAsync` yöntemi, baytları bağımsız değişkenine `content`, ve anlamlı bir değer döndürmez. Zaman uyumlu sürümde, `CopyTo` çağrısı bir değer döndürmeyen basit bir ifadedir. Zaman uyumsuz sürüm `CopyToAsync`, bir <xref:System.Threading.Tasks.Task>döndürür. Görev, "Task (void)" gibi çalışır ve yöntemin beklenmesine olanak sağlar. Aşağıdaki kodun gösterdiği gibi, `CopyToAsync`çağrısına `Await` veya `await` uygulayın.

        ```vb
        Await responseStream.CopyToAsync(content)
        ```

         Önceki ifade aşağıdaki iki kod satırını abbreviates.

        ```vb
        ' CopyToAsync returns a Task, not a Task<T>.
        Dim copyTask As Task = responseStream.CopyToAsync(content)

        ' When copyTask is completed, content contains a copy of
        ' responseStream.
        Await copyTask
        ```

4. `GetURLContents` her şey, yöntem imzasını ayarlamasıdır. `Await` işlecini yalnızca [zaman uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md) değiştiriciyle işaretlenen yöntemlerde kullanabilirsiniz. Aşağıdaki kodun gösterdiği gibi, yöntemi *zaman uyumsuz bir yöntem*olarak işaretlemek için değiştirici ekleyin.

    ```vb
    Private Async Function GetURLContents(url As String) As Byte()
    ```

5. Zaman uyumsuz bir yöntemin dönüş türü yalnızca <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>olabilir. Visual Basic, yönteminin bir `Task` veya `Task(Of T)`döndüren bir `Function` olması veya metodun bir `Sub`olması gerekir. Genellikle, bir `Sub` yöntemi yalnızca `Sub` gerekli olduğu zaman uyumsuz olay işleyicide kullanılır. Diğer durumlarda, tamamlanan yöntemin T türünde bir değer döndüren bir [Return](../../../../visual-basic/language-reference/statements/return-statement.md) ifadesine sahipse ve tamamlanmış Yöntem anlamlı bir değer döndürmezse `Task` kullandığınızda `Task(T)` kullanırsınız.

    Daha fazla bilgi için bkz. [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

    `GetURLContents` yöntemi bir return ifadesine sahiptir ve ifade bir bayt dizisi döndürür. Bu nedenle, zaman uyumsuz sürümün dönüş türü görev (T), burada T bir bayt dizisidir. Yöntem imzasında aşağıdaki değişiklikleri yapın:

    - Dönüş türünü `Task(Of Byte())`değiştirin.

    - Kurala göre, zaman uyumsuz metotların "Async" ile biten adları vardır. `GetURLContentsAsync`yöntemi yeniden adlandırın.

    Aşağıdaki kod bu değişiklikleri gösterir.

    ```vb
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())
    ```

    Bu az değişiklikle, zaman uyumsuz bir metoda `GetURLContents` dönüştürmesi tamamlanmıştır.

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a>Sumpageslikleri zaman uyumsuz bir metoda Dönüştür

1. `SumPageSizes`için önceki yordamdaki adımları tekrarlayın. İlk olarak, `GetURLContents` çağrısını zaman uyumsuz bir çağrıya değiştirin.

    - Daha önce yapmadıysanız, `GetURLContents` `GetURLContentsAsync`olarak çağrılan metodun adını değiştirin.

    - Bayt dizi değerini almak için `GetURLContentsAsync` döndüren göreve `Await` uygulayın.

    Aşağıdaki kod bu değişiklikleri gösterir.

    ```vb
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)
    ```

    Önceki atama, aşağıdaki iki kod satırını abbreviates.

    ```vb
    ' GetURLContentsAsync returns a task. At completion, the task
    ' produces a byte array.
    Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
    Dim urlContents As Byte() = Await getContentsTask
    ```

2. Yöntemin imzasında aşağıdaki değişiklikleri yapın:

    - Yöntemi `Async` değiştiricisiyle işaretleyin.

    - Yöntem adına "Async" ekleyin.

    - `SumPageSizesAsync` T için bir değer döndürmediğinden, bu kez bir görev dönüş değişkeni yok. (yöntemin hiçbir `Return` bildirisi yok.) Ancak, yönteminin bir `Task` olması gerekir. Bu nedenle, `Sub` yöntem türünü `Function`olarak değiştirin. İşlevin dönüş türü `Task`.

    Aşağıdaki kod bu değişiklikleri gösterir.

    ```vb
    Private Async Function SumPageSizesAsync() As Task
    ```

    `SumPageSizes` `SumPageSizesAsync` dönüşümü tamamlanmıştır.

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a>StartButton_Click zaman uyumsuz bir metoda Dönüştür

1. Daha önce yapmadıysanız, olay işleyicisinde `SumPageSizes` çağrılan yöntemin adını `SumPageSizesAsync`olarak değiştirin.

2. `SumPageSizesAsync` zaman uyumsuz bir yöntem olduğundan, olay işleyicisindeki kodu, sonucu beklemek için değiştirin.

    `SumPageSizesAsync` çağrısı, `GetURLContentsAsync``CopyToAsync` çağrısını yansıtır. Çağrı bir `Task(T)`değil `Task`döndürür.

    Önceki yordamlarda olduğu gibi, çağrıyı tek bir deyim veya iki deyim kullanarak dönüştürebilirsiniz. Aşağıdaki kod bu değişiklikleri gösterir.

    ```vb
    ' One-step async call.
    Await SumPageSizesAsync()

    ' Two-step async call.
    Dim sumTask As Task = SumPageSizesAsync()
    Await sumTask
    ```

3. İşlemi yanlışlıkla yeniden girmeye engel olmak için, **Başlangıç** düğmesini devre dışı bırakmak üzere `startButton_Click` en üstüne aşağıdaki ifadeyi ekleyin.

    ```vb
    ' Disable the button until the operation is complete.
    startButton.IsEnabled = False
    ```

    Olay işleyicisinin sonundaki düğmeyi yeniden etkinleştirebilirsiniz.

    ```vb
    ' Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = True
    ```

    Yeniden giriş hakkında daha fazla bilgi için bkz. [zaman uyumsuz uygulamalarda yeniden girişi işleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).

4. Son olarak, `Async` değiştiricisini bildirime ekleyerek olay işleyicisinin `SumPagSizesAsync`bekleymasını sağlayabilirsiniz.

    ```vb
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
    ```

    Genellikle, olay işleyicilerinin adları değiştirilmez. Olay işleyicilerinin Visual Basic `Sub` yordamlar olması gerektiğinden, dönüş türü `Task` olarak değiştirilmez.

    Projenin zaman uyumlu olarak zaman uyumsuz işlemeye dönüştürülmesi işlemi tamamlanır.

## <a name="test-the-asynchronous-solution"></a>Zaman uyumsuz çözümü test etme

1. Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.

2. Zaman uyumlu çözümün çıktısına benzeyen çıkış görünmelidir. Ancak, aşağıdaki farklılıklara dikkat edin.

    - İşlem tamamlandıktan sonra sonuçların hepsi aynı anda gerçekleşmiyor. Örneğin, her iki program de `startButton_Click` metin kutusunu temizleyen bir çizgi içerir. Tek bir sonuç kümesi görüntülendikten sonra **Başlat** düğmesini ikinci bir kez seçerseniz, çalıştırmalar arasındaki metin kutusunu temizlemek amaç. Zaman uyumlu sürümde, metin kutusu yalnızca sayımlar ikinci kez görüntülenmeden önce temizlenir, İndirmeler tamamlandığında ve Kullanıcı arabirimi iş parçacığı başka iş yapmak için ücretsizdir. Zaman uyumsuz sürümde, **Başlat** düğmesini seçtikten sonra metin kutusu hemen temizlenir.

    - En önemlisi, indirme sırasında UI iş parçacığı engellenmiyor. Web kaynakları indirilirken, sayıldıkça ve görüntülenirken pencereyi taşıyabilir veya yeniden boyutlandırabilirsiniz. Web sitelerinden biri yavaşsa veya yanıt vermiyorsa, **Kapat** düğmesini (sağ üst köşedeki kırmızı alanda bulunan x) seçerek işlemi iptal edebilirsiniz.

## <a name="replace-the-geturlcontentsasync-method-with-a-net-framework-method"></a>GetURLContentsAsync yöntemini bir .NET Framework yöntemiyle değiştirin

1. .NET Framework kullanabileceğiniz birçok zaman uyumsuz yöntem sağlar. Bunlardan biri, <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> yöntemi Bu izlenecek yol için yalnızca ihtiyacınız olanları yapar. Bunu, önceki yordamda oluşturduğunuz `GetURLContentsAsync` yöntemi yerine kullanabilirsiniz.

    İlk adım `SumPageSizesAsync` yönteminde bir <xref:System.Net.Http.HttpClient> nesnesi oluşturmaktır. Yönteminin başlangıcında aşağıdaki bildirimi ekleyin.

    ```vb
    ' Declare an HttpClient object and increase the buffer size. The
    ' default buffer size is 65,536.
    Dim client As HttpClient =
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}
    ```

2. `SumPageSizesAsync,` `GetURLContentsAsync` yönteminizin çağrısını `HttpClient` yöntemine yönelik bir çağrı ile değiştirin.

    ```vb
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ```

3. Yazdığınız `GetURLContentsAsync` yöntemi kaldırın veya açıklamayı kaldırın.

4. Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.

    Projenin bu sürümünün davranışı, "zaman uyumsuz çözümü test etmek Için" yordamının açıklandığı, ancak sizin de daha az çaba gösteren davranışla eşleşmelidir.

## <a name="example"></a>Örnek

Zaman uyumsuz `GetURLContentsAsync` yöntemini kullanan dönüştürülmüş zaman uyumsuz çözümün tam örneği aşağıda verilmiştir. Özgün, zaman uyumlu çözüme kesinlikle benzediğine dikkat edin.

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

Aşağıdaki kod, `GetByteArrayAsync``HttpClient` yöntemini kullanan çözümün tam örneğini içerir.

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

        ' Two-step async call.
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

- [Zaman uyumsuz örnek: Web Walkthrough 'A erişmeC# (ve Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [Await İşleci](../../../language-reference/operators/await-operator.md)
- [Async](../../../language-reference/modifiers/async.md)
- [Async ve await ile zaman uyumsuz programlama (Visual Basic)](index.md)
- [Zaman uyumsuz dönüş türleri (Visual Basic)](async-return-types.md)
- [Görev tabanlı zaman uyumsuz programlama (TAP)](https://www.microsoft.com/download/details.aspx?id=19957)
- [Nasıl yapılır: Task. WhenAll kullanarak zaman uyumsuz Izlenecek yolu genişletme (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [Nasıl yapılır: Async ve await kullanarak birden çok Web Isteğini paralel hale getirme (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
