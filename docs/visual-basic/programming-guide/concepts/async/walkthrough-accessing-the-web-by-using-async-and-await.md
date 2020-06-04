---
title: "İzlenecek yol: Async ve Await Kullanarak Web'e Erişme"
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: 41ededd4d4335b78b8d7a33e8fe387c7d632cbee
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400751"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a>İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)

Zaman uyumsuz programları, zaman uyumsuz/await özelliklerini kullanarak daha kolay ve daha canlı bir şekilde yazabilirsiniz. Zaman uyumlu kod gibi görünen zaman uyumsuz kod yazabilir ve derleyicinin zaman uyumsuz kodun genellikle sahip olduğu zor geri çağırma işlevlerini ve devamlılığını işlemesini sağlayabilirsiniz.

Async özelliği hakkında daha fazla bilgi için bkz. zaman uyumsuz [programlama, Async ve await (Visual Basic)](index.md).

Bu izlenecek yol, bir Web sitesi listesindeki bayt sayısını toplayan bir zaman uyumlu Windows Presentation Foundation (WPF) uygulamasıyla başlar. İzlenecek yol, yeni özellikleri kullanarak uygulamayı zaman uyumsuz bir çözüme dönüştürür.

Uygulamaları kendiniz derlemek istemiyorsanız, [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)"zaman uyumsuz örnek: Web izlenecek yol (C# ve Visual Basic)" erişimini indirebilirsiniz.

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

## <a name="prerequisites"></a>Önkoşullar

Bilgisayarınızda Visual Studio 2012 veya üzeri yüklü olmalıdır. Daha fazla bilgi için bkz. Visual Studio [İndirmeleri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) sayfası.

## <a name="create-a-wpf-application"></a>WPF uygulaması oluşturma

1. Visual Studio’yu çalıştırın.

2. Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.

    **Yeni proje** iletişim kutusu açılır.

3. **Yüklü şablonlar** bölmesinde Visual Basic öğesini seçin ve ardından Proje türleri listesinden **WPF uygulaması** ' nı seçin.

4. **Ad** metin kutusuna girin `AsyncExampleWPF` ve sonra **Tamam** düğmesini seçin.

    Yeni proje **Çözüm Gezgini**görüntülenir.

## <a name="design-a-simple-wpf-mainwindow"></a>Basit bir WPF MainWindow tasarımı

1. Visual Studio Code düzenleyicisinde **MainWindow. xaml** sekmesini seçin.

2. **Araç kutusu** penceresi görünür değilse, **Görünüm** menüsünü açın ve ardından **araç kutusu**' nu seçin.

3. **MainWindow** penceresine bir **Button** denetimi ve **TextBox** denetimi ekleyin.

4. **TextBox** denetimini vurgulayın ve **Özellikler** penceresinde aşağıdaki değerleri ayarlayın:

    - **Name** özelliğini olarak ayarlayın `resultsTextBox` .

    - **Height** özelliğini 250 olarak ayarlayın.

    - **Width** özelliğini 500 olarak ayarlayın.

    - **Metin** sekmesinde, Lucida Console veya Global tek boşluk gibi tek boşluklu bir yazı tipi belirtin.

5. **Düğme** denetimini vurgulayın ve **Özellikler** penceresinde aşağıdaki değerleri ayarlayın:

    - **Name** özelliğini olarak ayarlayın `startButton` .

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

2. `Imports`Zaten mevcut değilse, kod dosyasının en üstüne aşağıdaki deyimleri ekleyin.

    ```vb
    Imports System.Net.Http
    Imports System.Net
    Imports System.IO
    ```

## <a name="create-a-synchronous-application"></a>Zaman uyumlu uygulama oluşturma

1. MainWindow. xaml tasarım penceresinde, **Start** `startButton_Click` MainWindow. xaml. vb ' de olay Işleyicisini oluşturmak için Başlat düğmesine çift tıklayın.

2. MainWindow. xaml. vb dosyasında aşağıdaki kodu ' ın gövdesine kopyalayın `startButton_Click` :

    ```vb
    resultsTextBox.Clear()
    SumPageSizes()
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."
    ```

    Kod, uygulamayı yönlendiren yöntemini çağırır `SumPageSizes` ve denetim ' e döndüğünde bir ileti görüntüler `startButton_Click` .

3. Zaman uyumlu çözüm kodu aşağıdaki dört yöntemi içerir:

    - `SumPageSizes`, ' den Web sayfası URL 'Lerinin bir listesini alır ve `SetUpURLList` ardından `GetURLContents` `DisplayResults` her URL 'yi çağırır ve işler.

    - `SetUpURLList`, bir Web adresleri listesi oluşturur ve döndürür.

    - `GetURLContents`, her bir Web sitesinin içeriğini indirir ve bir bayt dizisi olarak içeriğini döndürür.

    - `DisplayResults`, her bir URL için bayt dizisindeki bayt sayısını görüntüler.

    Aşağıdaki dört yöntemi kopyalayın ve ardından bunları `startButton_Click` MainWindow. xaml. vb içindeki olay işleyicisinin altına yapıştırın:

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

1. Zaman uyumlu çözümü zaman uyumsuz bir çözüme dönüştürmek için, `GetURLContents` <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> yönteme ve yöntemine yapılan çağrılar <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> uygulamanın Web 'e eriştiği yerdir. .NET Framework, her iki yöntemin de zaman uyumsuz sürümlerini sağlayarak dönüştürmeyi kolaylaştırır.

    İçinde kullanılan yöntemler hakkında daha fazla bilgi için `GetURLContents` bkz <xref:System.Net.WebRequest> ..

    > [!NOTE]
    > Bu izlenecek yolda bulunan adımları izleyerek bazı derleyici hataları görüntülenir. Bunları yoksayabilir ve İzlenecek yol ile devam edebilirsiniz.

    ' In üçüncü satırında çağrılan yöntemi, `GetURLContents` `GetResponse` zaman uyumsuz, görev tabanlı <xref:System.Net.WebRequest.GetResponseAsync%2A> metoda değiştirin.

    ```vb
    Using response As WebResponse = webReq.GetResponseAsync()
    ```

2. `GetResponseAsync`döndürür <xref:System.Threading.Tasks.Task%601> . Bu durumda, *görev dönüş değişkeni*, `TResult` türündedir <xref:System.Net.WebResponse> . Görev, `WebResponse` istenen veriler indirildikten ve görevin tamamlanmasını çalıştırdıktan sonra gerçek bir nesne oluşturmak için bir taahhüddir.

    `WebResponse`Görevden değeri almak için, aşağıdaki kodda gösterildiği gibi çağrısına bir [await](../../../language-reference/operators/await-operator.md) işleci uygulayın `GetResponseAsync` .

    ```vb
    Using response As WebResponse = Await webReq.GetResponseAsync()
    ```

    `Await`İşleç, beklenen görev tamamlanana kadar geçerli yöntemin yürütülmesini askıya alır `GetURLContents` . Bu arada, Denetim geçerli yöntemi çağırana döner. Bu örnekte, geçerli yöntem `GetURLContents` ve arayan ' dır `SumPageSizes` . Görev tamamlandığında, taahhüt edilen `WebResponse` nesne, beklenen görevin değeri olarak üretilir ve değişkenine atanır `response` .

    Önceki deyim, ne olacağını açıklamak için aşağıdaki iki ifadeye ayrılabilir.

    ```vb
    Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
    Using response As WebResponse = Await responseTask
    ```

    Çağrısı `webReq.GetResponseAsync` bir `Task(Of WebResponse)` veya döndürür `Task<WebResponse>` . Sonra `Await` değeri almak için göreve bir işleç uygulanır `WebResponse` .

    Zaman uyumsuz yönteminizin, görevin tamamlanmasına bağlı olmaması durumunda, zaman uyumsuz metoda yapılan çağrıdan sonra ve Await işleci uygulanmadan önce bu iki deyim arasında bu işe devam edebilir. Örnekler için bkz. [nasıl yapılır: Async ve await kullanarak birden çok Web Isteğini paralel hale getirme (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) ve [nasıl yapılır: Task. whenall (Visual Basic) kullanarak zaman uyumsuz izlenecek yolu genişletme](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).

3. `Await`Önceki adımda işleci eklediğiniz için bir derleyici hatası oluşur. İşleci yalnızca [zaman uyumsuz](../../../language-reference/modifiers/async.md) değiştiriciyle işaretlenen yöntemlerde kullanılabilir. Çağrısını ' a ' çağrısı ile değiştirmek için dönüştürme adımlarını tekrarlarken hatayı yoksayın `CopyTo` `CopyToAsync` .

    - Olarak çağrılan metodun adını değiştirin <xref:System.IO.Stream.CopyToAsync%2A> .

    - `CopyTo`Ya da `CopyToAsync` yöntemi, bayt bağımsız değişkenine bayt kopyalar, `content` ve anlamlı bir değer döndürmez. Zaman uyumlu sürümde, çağrısı `CopyTo` bir değer döndürmeyen basit bir ifadedir. Zaman uyumsuz sürüm, `CopyToAsync` bir döndürür <xref:System.Threading.Tasks.Task> . Görev, "Task (void)" gibi çalışır ve yöntemin beklenmesine olanak sağlar. `Await` `await` `CopyToAsync` Aşağıdaki kodda gösterildiği gibi, çağrısına yönelik veya çağrısı yapın.

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

4. Tüm bunlar ' de yapılacak şekilde, `GetURLContents` yöntem imzasını ayarlamasıdır. `Await`İşlecini yalnızca [zaman uyumsuz](../../../language-reference/modifiers/async.md) değiştiriciyle işaretlenen yöntemlerde kullanabilirsiniz. Aşağıdaki kodun gösterdiği gibi, yöntemi *zaman uyumsuz bir yöntem*olarak işaretlemek için değiştirici ekleyin.

    ```vb
    Private Async Function GetURLContents(url As String) As Byte()
    ```

5. Zaman uyumsuz bir yöntemin dönüş türü yalnızca <xref:System.Threading.Tasks.Task> , olabilir <xref:System.Threading.Tasks.Task%601> . Visual Basic, yöntemi `Function` bir veya döndüren bir `Task` `Task(Of T)` , ya da yönteminin bir olması gerekir `Sub` . Genellikle, bir `Sub` Yöntem yalnızca zaman uyumsuz olay işleyicide kullanılır, burada `Sub` gereklidir. Diğer durumlarda, `Task(T)` Tamamlanan yöntemin T türünde bir değer döndüren bir [Return](../../../language-reference/statements/return-statement.md) ifadesine sahip olması ve `Task` Tamamlanan yöntemin anlamlı bir değer döndürmemesi durumunda kullanmanız gerekir.

    Daha fazla bilgi için bkz. [Async Return Types (Visual Basic)](async-return-types.md).

    Yöntem `GetURLContents` bir return ifadesine sahiptir ve ifade bir bayt dizisi döndürür. Bu nedenle, zaman uyumsuz sürümün dönüş türü görev (T), burada T bir bayt dizisidir. Yöntem imzasında aşağıdaki değişiklikleri yapın:

    - Dönüş türünü olarak değiştirin `Task(Of Byte())` .

    - Kurala göre, zaman uyumsuz metotların "Async" ile biten adları vardır. bu nedenle, yöntemi yeniden adlandırın `GetURLContentsAsync` .

    Aşağıdaki kod bu değişiklikleri gösterir.

    ```vb
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())
    ```

    Bu az değişiklikle, `GetURLContents` zaman uyumsuz bir metoda dönüştürme işlemi tamamlanmıştır.

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a>Sumpageslikleri zaman uyumsuz bir metoda Dönüştür

1. İçin önceki yordamdaki adımları tekrarlayın `SumPageSizes` . İlk olarak, çağrısını `GetURLContents` zaman uyumsuz bir çağrıya değiştirin.

    - `GetURLContents` `GetURLContentsAsync` Daha önce yapmadıysanız, ' dan ' a çağrılan metodun adını değiştirin.

    - `Await` `GetURLContentsAsync` Bayt dizi değerini almak için döndüren göreve uygulanır.

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

    - Yöntemi `Async` değiştiriciyle işaretleyin.

    - Yöntem adına "Async" ekleyin.

    - Bir görev dönüş değişkeni yok, T, bu kez `SumPageSizesAsync` t için bir değer döndürmüyor. (yöntemin hiçbir yöntemi yoktur `Return` .) Ancak, yöntemi bir `Task` olarak bir olarak döndürmelidir. Bu nedenle, yöntem türünü olarak değiştirin `Sub` `Function` . İşlevin dönüş türü `Task` .

    Aşağıdaki kod bu değişiklikleri gösterir.

    ```vb
    Private Async Function SumPageSizesAsync() As Task
    ```

    ' A dönüştürme `SumPageSizes` `SumPageSizesAsync` işlemi tamamlanmıştır.

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a>StartButton_Click zaman uyumsuz bir metoda Dönüştür

1. Daha önce yapmadıysanız, olay işleyicisinde, çağrılan yöntemin adını `SumPageSizes` olarak olarak değiştirin `SumPageSizesAsync` .

2. `SumPageSizesAsync`Zaman uyumsuz bir yöntem olduğundan, olay işleyicisindeki kodu, sonucu bekleme olarak değiştirin.

    `SumPageSizesAsync`İçindeki çağrısını yansıtan çağrı `CopyToAsync` `GetURLContentsAsync` . Çağrı `Task` a değil, döndürür `Task(T)` .

    Önceki yordamlarda olduğu gibi, çağrıyı tek bir deyim veya iki deyim kullanarak dönüştürebilirsiniz. Aşağıdaki kod bu değişiklikleri gösterir.

    ```vb
    ' One-step async call.
    Await SumPageSizesAsync()

    ' Two-step async call.
    Dim sumTask As Task = SumPageSizesAsync()
    Await sumTask
    ```

3. İşlemi yanlışlıkla yeniden girmeye engel olmak için, `startButton_Click` **Başlangıç** düğmesini devre dışı bırakmak için aşağıdaki ifadeyi ' ın üst kısmına ekleyin.

    ```vb
    ' Disable the button until the operation is complete.
    startButton.IsEnabled = False
    ```

    Olay işleyicisinin sonundaki düğmeyi yeniden etkinleştirebilirsiniz.

    ```vb
    ' Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = True
    ```

    Yeniden giriş hakkında daha fazla bilgi için bkz. [zaman uyumsuz uygulamalarda yeniden girişi işleme (Visual Basic)](handling-reentrancy-in-async-apps.md).

4. Son olarak, `Async` olay işleyicisinin beklebilmesi için değiştiricisini bildirime ekleyin `SumPagSizesAsync` .

    ```vb
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
    ```

    Genellikle, olay işleyicilerinin adları değiştirilmez. `Task`Olay işleyicilerinin Visual Basic yordamlar olması gerektiğinden, dönüş türü olarak değiştirilmez `Sub` .

    Projenin zaman uyumlu olarak zaman uyumsuz işlemeye dönüştürülmesi işlemi tamamlanır.

## <a name="test-the-asynchronous-solution"></a>Zaman uyumsuz çözümü test etme

1. Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.

2. Zaman uyumlu çözümün çıktısına benzeyen çıkış görünmelidir. Ancak, aşağıdaki farklılıklara dikkat edin.

    - İşlem tamamlandıktan sonra sonuçların hepsi aynı anda gerçekleşmiyor. Örneğin, her iki program içinde `startButton_Click` metin kutusunu temizleyen bir satır içerir. Tek bir sonuç kümesi görüntülendikten sonra **Başlat** düğmesini ikinci bir kez seçerseniz, çalıştırmalar arasındaki metin kutusunu temizlemek amaç. Zaman uyumlu sürümde, metin kutusu yalnızca sayımlar ikinci kez görüntülenmeden önce temizlenir, İndirmeler tamamlandığında ve Kullanıcı arabirimi iş parçacığı başka iş yapmak için ücretsizdir. Zaman uyumsuz sürümde, **Başlat** düğmesini seçtikten sonra metin kutusu hemen temizlenir.

    - En önemlisi, indirme sırasında UI iş parçacığı engellenmiyor. Web kaynakları indirilirken, sayıldıkça ve görüntülenirken pencereyi taşıyabilir veya yeniden boyutlandırabilirsiniz. Web sitelerinden biri yavaşsa veya yanıt vermiyorsa, **Kapat** düğmesini (sağ üst köşedeki kırmızı alanda bulunan x) seçerek işlemi iptal edebilirsiniz.

## <a name="replace-the-geturlcontentsasync-method-with-a-net-framework-method"></a>GetURLContentsAsync yöntemini bir .NET Framework yöntemiyle değiştirin

1. .NET Framework kullanabileceğiniz birçok zaman uyumsuz yöntem sağlar. Bunlardan biri, <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> yöntemi Bu izlenecek yol için yalnızca ihtiyacınız olanları yapar. `GetURLContentsAsync`Daha önceki bir yordamda oluşturduğunuz yöntemi yerine kullanabilirsiniz.

    İlk adım <xref:System.Net.Http.HttpClient> yönteminde bir nesne oluşturmaktır `SumPageSizesAsync` . Yönteminin başlangıcında aşağıdaki bildirimi ekleyin.

    ```vb
    ' Declare an HttpClient object and increase the buffer size. The
    ' default buffer size is 65,536.
    Dim client As HttpClient =
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}
    ```

2. İçinde, yöntemine yapılan çağrıyı yöntemine `SumPageSizesAsync,` `GetURLContentsAsync` bir çağrı ile değiştirin `HttpClient` .

    ```vb
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ```

3. Yazdığınız yöntemi kaldırın veya not edin `GetURLContentsAsync` .

4. Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.

    Projenin bu sürümünün davranışı, "zaman uyumsuz çözümü test etmek Için" yordamının açıklandığı, ancak sizin de daha az çaba gösteren davranışla eşleşmelidir.

## <a name="example"></a>Örnek

Aşağıda, zaman uyumsuz yöntemi kullanan dönüştürülmüş zaman uyumsuz çözümün tam örneği verilmiştir `GetURLContentsAsync` . Özgün, zaman uyumlu çözüme kesinlikle benzediğine dikkat edin.

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

Aşağıdaki kod, yöntemini kullanan çözümün tam örneğini içerir `HttpClient` `GetByteArrayAsync` .

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

- [Zaman uyumsuz örnek: Web 'e yönelik Izlenecek yol (C# ve Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [Await Işleci](../../../language-reference/operators/await-operator.md)
- [Eş](../../../language-reference/modifiers/async.md)
- [Async ve await ile zaman uyumsuz programlama (Visual Basic)](index.md)
- [Zaman uyumsuz dönüş türleri (Visual Basic)](async-return-types.md)
- [Görev tabanlı zaman uyumsuz programlama (TAP)](https://www.microsoft.com/download/details.aspx?id=19957)
- [Nasıl yapılır: Task. WhenAll kullanarak zaman uyumsuz Izlenecek yolu genişletme (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [Nasıl yapılır: Async ve await kullanarak birden çok Web Isteğini paralel hale getirme (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
