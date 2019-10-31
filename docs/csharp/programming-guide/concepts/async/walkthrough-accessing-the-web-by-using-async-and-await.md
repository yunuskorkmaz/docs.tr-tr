---
title: "İzlenecek yol: Async ve await (C#) kullanarak Web 'e erişme"
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: 30677be2299dfa4411263dc5c61093fc0ca0f442
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73195641"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a>İzlenecek yol: Async ve await (C#) kullanarak Web 'e erişme

Zaman uyumsuz programları, zaman uyumsuz/await özelliklerini kullanarak daha kolay ve daha canlı bir şekilde yazabilirsiniz. Zaman uyumlu kod gibi görünen zaman uyumsuz kod yazabilir ve derleyicinin zaman uyumsuz kodun genellikle sahip olduğu zor geri çağırma işlevlerini ve devamlılığını işlemesini sağlayabilirsiniz.

Zaman uyumsuz özellik hakkında daha fazla bilgi için bkz. [Async ve await (C#) Ile zaman uyumsuz programlama](./index.md).

Bu izlenecek yol, bir Web sitesi listesindeki bayt sayısını toplayan bir zaman uyumlu Windows Presentation Foundation (WPF) uygulamasıyla başlar. İzlenecek yol, yeni özellikleri kullanarak uygulamayı zaman uyumsuz bir çözüme dönüştürür.

Uygulamaları kendiniz derlemek istemiyorsanız, [zaman uyumsuz örneği indirebilirsinizC# : Web 'e (ve Visual Basic) erişme](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).

> [!NOTE]
> Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.

## <a name="create-a-wpf-application"></a>WPF uygulaması oluşturma

1. Visual Studio 'Yu başlatın.

2. Menü çubuğunda **dosya**  > **Yeni**  > **Proje**' yi seçin.

     **Yeni proje** iletişim kutusu açılır.

3. **Yüklü şablonlar** bölmesinde, görsel C#' i seçin ve ardından Proje türleri listesinden **WPF uygulaması** ' nı seçin.

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

2. Menü çubuğunda, **proje** > **Başvuru Ekle**' yi seçin.

     **Başvuru Yöneticisi** iletişim kutusu görüntülenir.

3. İletişim kutusunun üst kısmında, projenizin .NET Framework 4,5 veya üstünü hedeflediğinden emin olun.

4. **Derlemeler** kategorisinde, zaten seçili değilse **Framework** ' ü seçin.

5. Ad listesinde, **System .net. http** onay kutusunu seçin.

6. İletişim kutusunu kapatmak için **Tamam** düğmesini seçin.

## <a name="add-necessary-using-directives"></a>Gerekli yönergeleri kullanarak ekleme

1. **Çözüm Gezgini**' de, MainWindow.xaml.cs için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

2. Zaten mevcut değilse, kod dosyasının en üstüne aşağıdaki `using` yönergelerini ekleyin.

    ```csharp
    using System.Net.Http;
    using System.Net;
    using System.IO;
    ```

## <a name="create-a-synchronous-app"></a>Zaman uyumlu uygulama oluşturma

1. Tasarım penceresinde, MainWindow. xaml, MainWindow.xaml.cs içinde `startButton_Click` olay işleyicisini oluşturmak için **Başlat** düğmesine çift tıklayın.

2. MainWindow.xaml.cs ' de, aşağıdaki kodu `startButton_Click`gövdesine kopyalayın:

    ```csharp
    resultsTextBox.Clear();
    SumPageSizes();
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";
    ```

    Kod, uygulamayı yönlendiren yöntemi çağırır, `SumPageSizes`ve denetim `startButton_Click`döndüğünde bir ileti görüntüler.

3. Zaman uyumlu çözüm kodu aşağıdaki dört yöntemi içerir:

    - `SumPageSizes`, `SetUpURLList` Web sayfası URL 'Lerinin bir listesini alır ve sonra her bir URL 'YI işlemek için `GetURLContents` ve `DisplayResults` çağırır.

    - `SetUpURLList`, Web adreslerinin bir listesini oluşturan ve döndüren.

    - Her Web sitesinin içeriğini indiren ve bir bayt dizisi olarak içeriği döndüren `GetURLContents`.

    - her URL için bayt dizisindeki bayt sayısını görüntüleyen `DisplayResults`.

    Aşağıdaki dört yöntemi kopyalayın ve ardından MainWindow.xaml.cs ' de `startButton_Click` olay işleyicisi altına yapıştırın:

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
        resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
    }

    private List<string> SetUpURLList()
    {
        var urls = new List<string>
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
        // Strip off the "https://".
        var displayURL = url.Replace("https://", "");
        resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
    }
    ```

## <a name="test-the-synchronous-solution"></a>Zaman uyumlu çözümü test etme

Programı çalıştırmak için **F5** tuşunu seçin ve sonra **Başlat** düğmesini seçin.

Aşağıdaki listeye benzer bir çıktı görünmelidir:

```text
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

1. Zaman uyumlu çözümü zaman uyumsuz bir çözüme dönüştürmek için en iyi `GetURLContents`, <xref:System.Net.HttpWebRequest> yöntemine <xref:System.Net.HttpWebRequest.GetResponse%2A> ve <xref:System.IO.Stream> <xref:System.IO.Stream.CopyTo%2A> yöntemine yapılan çağrılar uygulamanın Web 'e eriştiği yerdir. .NET Framework, her iki yöntemin de zaman uyumsuz sürümlerini sağlayarak dönüştürmeyi kolaylaştırır.

     `GetURLContents`' de kullanılan yöntemler hakkında daha fazla bilgi için bkz. <xref:System.Net.WebRequest>.

    > [!NOTE]
    > Bu izlenecek yolda bulunan adımları izleyerek bazı derleyici hataları görüntülenir. Bunları yoksayabilir ve İzlenecek yol ile devam edebilirsiniz.

     `GetURLContents` üçüncü satırındaki `GetResponse` zaman uyumsuz, görev tabanlı <xref:System.Net.WebRequest.GetResponseAsync%2A> metoduna olan yöntemi değiştirin.

    ```csharp
    using (WebResponse response = webReq.GetResponseAsync())
    ```

2. `GetResponseAsync` <xref:System.Threading.Tasks.Task%601>döndürür. Bu durumda, *görev dönüş değişkeni*`TResult`, <xref:System.Net.WebResponse>türü vardır. Görev, istenen veriler indirildikten ve görevin tamamlanmasını çalıştırdıktan sonra gerçek bir `WebResponse` nesnesi oluşturmak için bir taahhüddir.

     Görevden `WebResponse` değerini almak için aşağıdaki kodda gösterildiği gibi, `GetResponseAsync`çağrısına bir [await](../../../language-reference/operators/await.md) işleci uygulayın.

    ```csharp
    using (WebResponse response = await webReq.GetResponseAsync())
    ```

     `await` işleci, beklenen görev tamamlanana kadar, `GetURLContents`geçerli metodun yürütülmesini askıya alır. Bu arada, Denetim geçerli yöntemi çağırana döner. Bu örnekte, geçerli yöntem `GetURLContents`ve arayan `SumPageSizes`. Görev tamamlandığında, taahhüt edilen `WebResponse` nesnesi, beklenen görevin değeri olarak üretilir ve `response`değişkenine atanır.

     Önceki deyim, ne olacağını açıklamak için aşağıdaki iki ifadeye ayrılabilir.

    ```csharp
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();
    //using (WebResponse response = await responseTask)
    ```

     `webReq.GetResponseAsync` çağrısı `Task(Of WebResponse)` veya `Task<WebResponse>`döndürür. Sonra, `WebResponse` değerini almak için göreve bir Await işleci uygulanır.

     Zaman uyumsuz yönteminiz görevin tamamlanmasına bağlı değilse, bu iki deyim arasında, zaman uyumsuz metoda yapılan çağrıdan sonra ve `await` işleci uygulanmadan önce bu iki deyim arasında bu işe devam edebilir. Örnekler için bkz. [nasıl yapılır: Async ve await (C#) kullanarak birden çok web isteğini paralel hale getirme](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) ve [nasıl yapılır: Task. WhenAll (C#) kullanarak zaman uyumsuz izlenecek yolu genişletme](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).

3. Önceki adımda `await` işlecini eklediğiniz için bir derleyici hatası oluşur. İşleci yalnızca [zaman uyumsuz](../../../language-reference/keywords/async.md) değiştiriciyle işaretlenen yöntemlerde kullanılabilir. `CopyTo` çağrısını `CopyToAsync`çağrısı ile değiştirmek için dönüştürme adımlarını tekrarlarken hatayı yoksayın.

    - <xref:System.IO.Stream.CopyToAsync%2A>olarak çağrılan metodun adını değiştirin.

    - `CopyTo` veya `CopyToAsync` yöntemi, baytları bağımsız değişkenine `content`, ve anlamlı bir değer döndürmez. Zaman uyumlu sürümde, `CopyTo` çağrısı bir değer döndürmeyen basit bir ifadedir. Zaman uyumsuz sürüm `CopyToAsync`, bir <xref:System.Threading.Tasks.Task>döndürür. Görev, "Task (void)" gibi çalışır ve yöntemin beklenmesine olanak sağlar. Aşağıdaki kodun gösterdiği gibi, `CopyToAsync`çağrısına `Await` veya `await` uygulayın.

        ```csharp
        await responseStream.CopyToAsync(content);
        ```

         Önceki ifade aşağıdaki iki kod satırını abbreviates.

        ```csharp
        // CopyToAsync returns a Task, not a Task<T>.
        //Task copyTask = responseStream.CopyToAsync(content);

        // When copyTask is completed, content contains a copy of
        // responseStream.
        //await copyTask;
        ```

4. `GetURLContents` her şey, yöntem imzasını ayarlamasıdır. `await` işlecini yalnızca [zaman uyumsuz](../../../language-reference/keywords/async.md) değiştiriciyle işaretlenen yöntemlerde kullanabilirsiniz. Aşağıdaki kodun gösterdiği gibi, yöntemi *zaman uyumsuz bir yöntem*olarak işaretlemek için değiştirici ekleyin.

    ```csharp
    private async byte[] GetURLContents(string url)
    ```

5. Zaman uyumsuz bir yöntemin dönüş türü, içinde C#yalnızca <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>veya `void` olabilir. Genellikle, `void` dönüş türü yalnızca bir zaman uyumsuz olay işleyicide kullanılır, burada `void` gereklidir. Diğer durumlarda, tamamlanan yöntemin T türünde bir değer döndüren bir [Return](../../../language-reference/keywords/return.md) ifadesine sahipse ve tamamlanmış Yöntem anlamlı bir değer döndürmezse `Task` kullandığınızda `Task(T)` kullanırsınız. `Task` dönüş türünü anlamı "görev (void)" olarak düşünebilirsiniz.

     Daha fazla bilgi için bkz. [Async Return TypesC#()](./async-return-types.md).

     `GetURLContents` yöntemi bir return ifadesine sahiptir ve ifade bir bayt dizisi döndürür. Bu nedenle, zaman uyumsuz sürümün dönüş türü görev (T), burada T bir bayt dizisidir. Yöntem imzasında aşağıdaki değişiklikleri yapın:

    - Dönüş türünü `Task<byte[]>`değiştirin.

    - Kurala göre, zaman uyumsuz metotların "Async" ile biten adları vardır. `GetURLContentsAsync`yöntemi yeniden adlandırın.

     Aşağıdaki kod bu değişiklikleri gösterir.

    ```csharp
    private async Task<byte[]> GetURLContentsAsync(string url)
    ```

     Bu az değişiklikle, zaman uyumsuz bir metoda `GetURLContents` dönüştürmesi tamamlanmıştır.

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a>Sumpageslikleri zaman uyumsuz bir metoda Dönüştür

1. `SumPageSizes`için önceki yordamdaki adımları tekrarlayın. İlk olarak, `GetURLContents` çağrısını zaman uyumsuz bir çağrıya değiştirin.

    - Daha önce yapmadıysanız, `GetURLContents` `GetURLContentsAsync`olarak çağrılan metodun adını değiştirin.

    - Bayt dizi değerini almak için `GetURLContentsAsync` döndüren göreve `await` uygulayın.

     Aşağıdaki kod bu değişiklikleri gösterir.

    ```csharp
    byte[] urlContents = await GetURLContentsAsync(url);
    ```

     Önceki atama, aşağıdaki iki kod satırını abbreviates.

    ```csharp
    // GetURLContentsAsync returns a Task<T>. At completion, the task
    // produces a byte array.
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //byte[] urlContents = await getContentsTask;
    ```

2. Yöntemin imzasında aşağıdaki değişiklikleri yapın:

    - Yöntemi `async` değiştiricisiyle işaretleyin.

    - Yöntem adına "Async" ekleyin.

    - `SumPageSizesAsync` T için bir değer döndürmediğinden, bu kez bir görev dönüş değişkeni yok. (yöntemin hiçbir `return` bildirisi yok.) Ancak, yönteminin bir `Task` olması gerekir. Bu nedenle, `void` yönteminin dönüş türünü `Task`olarak değiştirin.

    Aşağıdaki kod bu değişiklikleri gösterir.

    ```csharp
    private async Task SumPageSizesAsync()
    ```

     `SumPageSizes` `SumPageSizesAsync` dönüşümü tamamlanmıştır.

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a>StartButton_Click öğesini zaman uyumsuz bir metoda Dönüştür

1. Daha önce yapmadıysanız, olay işleyicisinde `SumPageSizes` çağrılan yöntemin adını `SumPageSizesAsync`olarak değiştirin.

2. `SumPageSizesAsync` zaman uyumsuz bir yöntem olduğundan, olay işleyicisindeki kodu, sonucu beklemek için değiştirin.

     `SumPageSizesAsync` çağrısı, `GetURLContentsAsync``CopyToAsync` çağrısını yansıtır. Çağrı bir `Task(T)`değil `Task`döndürür.

     Önceki yordamlarda olduğu gibi, çağrıyı tek bir deyim veya iki deyim kullanarak dönüştürebilirsiniz. Aşağıdaki kod bu değişiklikleri gösterir.

    ```csharp
    // One-step async call.
    await SumPageSizesAsync();

    // Two-step async call.
    //Task sumTask = SumPageSizesAsync();
    //await sumTask;
    ```

3. İşlemi yanlışlıkla yeniden girmeye engel olmak için, **Başlangıç** düğmesini devre dışı bırakmak üzere `startButton_Click` en üstüne aşağıdaki ifadeyi ekleyin.

    ```csharp
    // Disable the button until the operation is complete.
    startButton.IsEnabled = false;
    ```

     Olay işleyicisinin sonundaki düğmeyi yeniden etkinleştirebilirsiniz.

    ```csharp
    // Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = true;
    ```

     Yeniden giriş hakkında daha fazla bilgi için bkz. [zaman uyumsuz uygulamalarda yeniden girişi işlemeC#()](./handling-reentrancy-in-async-apps.md).

4. Son olarak, `async` değiştiricisini bildirime ekleyerek olay işleyicisinin `SumPagSizesAsync`bekleymasını sağlayabilirsiniz.

    ```csharp
    private async void startButton_Click(object sender, RoutedEventArgs e)
    ```

     Genellikle, olay işleyicilerinin adları değiştirilmez. Olay işleyicilerinin `void`döndürmesi gerektiğinden, dönüş türü `Task` olarak değiştirilmez.

     Projenin zaman uyumlu olarak zaman uyumsuz işlemeye dönüştürülmesi işlemi tamamlanır.

## <a name="test-the-asynchronous-solution"></a>Zaman uyumsuz çözümü test etme

1. Programı çalıştırmak için **F5** tuşunu seçin ve sonra **Başlat** düğmesini seçin.

2. Zaman uyumlu çözümün çıktısına benzeyen çıkış görünmelidir. Ancak, aşağıdaki farklılıklara dikkat edin.

    - İşlem tamamlandıktan sonra sonuçların hepsi aynı anda gerçekleşmiyor. Örneğin, her iki program de `startButton_Click` metin kutusunu temizleyen bir çizgi içerir. Tek bir sonuç kümesi görüntülendikten sonra **Başlat** düğmesini ikinci bir kez seçerseniz, çalıştırmalar arasındaki metin kutusunu temizlemek amaç. Zaman uyumlu sürümde, metin kutusu yalnızca sayımlar ikinci kez görüntülenmeden önce temizlenir, İndirmeler tamamlandığında ve Kullanıcı arabirimi iş parçacığı başka iş yapmak için ücretsizdir. Zaman uyumsuz sürümde, **Başlat** düğmesini seçtikten sonra metin kutusu hemen temizlenir.

    - En önemlisi, indirme sırasında UI iş parçacığı engellenmiyor. Web kaynakları indirilirken, sayıldıkça ve görüntülenirken pencereyi taşıyabilir veya yeniden boyutlandırabilirsiniz. Web sitelerinden biri yavaşsa veya yanıt vermiyorsa, **Kapat** düğmesini (sağ üst köşedeki kırmızı alanda bulunan x) seçerek işlemi iptal edebilirsiniz.

## <a name="replace-method-geturlcontentsasync-with-a-net-framework-method"></a>GetURLContentsAsync yöntemini bir .NET Framework yöntemiyle Değiştir

1. .NET Framework 4,5, kullanabileceğiniz birçok zaman uyumsuz yöntem sağlar. Bunlardan biri olan <xref:System.Net.Http.HttpClient> yöntemi, Bu izlenecek yol için yalnızca ihtiyacınız olan <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>. Bunu, önceki yordamda oluşturduğunuz `GetURLContentsAsync` yöntemi yerine kullanabilirsiniz.

     İlk adım, yöntem `SumPageSizesAsync``HttpClient` bir nesne oluşturmaktır. Yönteminin başlangıcında aşağıdaki bildirimi ekleyin.

    ```csharp
    // Declare an HttpClient object and increase the buffer size. The
    // default buffer size is 65,536.
    HttpClient client =
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };
    ```

2. `SumPageSizesAsync,` `GetURLContentsAsync` yönteminizin çağrısını `HttpClient` yöntemine yönelik bir çağrı ile değiştirin.

    ```csharp
    byte[] urlContents = await client.GetByteArrayAsync(url);
    ```

3. Yazdığınız `GetURLContentsAsync` yöntemi kaldırın veya açıklamayı kaldırın.

4. Programı çalıştırmak için **F5** tuşunu seçin ve sonra **Başlat** düğmesini seçin.

     Projenin bu sürümünün davranışı, "zaman uyumsuz çözümü test etmek Için" yordamının açıklandığı, ancak sizin de daha az çaba gösteren davranışla eşleşmelidir.

## <a name="example-code"></a>Örnek kod

Aşağıdaki kod, yazdığınız zaman uyumsuz `GetURLContentsAsync` yöntemi kullanılarak zaman uyumsuz bir çözüme dönüştürme işleminin tam örneğini içerir. Özgün, zaman uyumlu çözüme kesinlikle benzediğine dikkat edin.

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
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
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
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

Aşağıdaki kod, `GetByteArrayAsync``HttpClient` yöntemini kullanan çözümün tam örneğini içerir.

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
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
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
            };
            return urls;
        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each website. The string format
            // is designed to be used with a monospaced font, such as
            // Lucida Console or Global Monospace.
            var bytes = content.Length;
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Zaman uyumsuz örnek: Web Walkthrough 'A erişmeC# (ve Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
- [Async ve await (C#) ile zaman uyumsuz programlama](./index.md)
- [Zaman uyumsuz dönüş türleriC#()](./async-return-types.md)
- [Görev tabanlı zaman uyumsuz programlama (TAP)](https://www.microsoft.com/download/details.aspx?id=19957)
- [Nasıl yapılır: Task. WhenAll (C#) kullanarak zaman uyumsuz Izlenecek yolu genişletme](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [Nasıl yapılır: Async ve await (C#) kullanarak birden çok Web Isteğini paralel hale getirme](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
