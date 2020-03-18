---
title: "Walkthrough: Async kullanarak Web'e erişim ve bekleme (C#)"
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: 42b09dab26fd514e184163eaf41aff117d3a463f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74281792"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a>Walkthrough: Async kullanarak Web'e erişim ve bekleme (C#)

Async/await özelliklerini kullanarak daha kolay ve sezgisel bir şekilde asynchronous programları yazabilirsiniz. Senkron koda benzeyen bir senkron kod yazabilir ve derleyicinin asynchronous kodunun genellikle gerektirdiği zor geri arama işlevlerini ve devamlarını işlemesine izin verebilirsiniz.

Async özelliği hakkında daha fazla bilgi [için, async ile Asynchronous Programming'e bakın ve (C#) bekleyin.](./index.md)

Bu gözden geçirme, web siteleri listesindeki bayt sayısını özetleyen eşzamanlı bir Windows Presentation Foundation (WPF) uygulamasıyla başlar. İzthrough daha sonra yeni özellikleri kullanarak uygulamayı asynchronous çözüme dönüştürür.

Uygulamaları kendiniz oluşturmak istemiyorsanız, [Async Örnek: Web Walkthrough (C# ve Visual Basic) erişim](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)indirebilirsiniz.

> [!NOTE]
> Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınıza yüklü olması gerekir.

## <a name="create-a-wpf-application"></a>WPF uygulaması oluşturma

1. Visual Studio’yu çalıştırın.

2. Menü çubuğunda**Yeni** > **Proje** **yi seçin.** > 

     **Yeni Proje** iletişim kutusu açılır.

3. Yüklü **Şablonlar** bölmesinde Visual C#'ı seçin ve ardından proje türleri listesinden **WPF Uygulamasını** seçin.

4. **Ad** metin kutusuna `AsyncExampleWPF`girin ve **ardından Tamam** düğmesini seçin.

     Yeni proje Çözüm **Gezgini'nde**görünür.

## <a name="design-a-simple-wpf-mainwindow"></a>Basit bir WPF MainWindow tasarla

1. Visual Studio Code Editor'da **MainWindow.xaml** sekmesini seçin.

2. Araç **Kutusu** penceresi görünmüyorsa, **Görünüm** menüsünü açın ve ardından **Araç Kutusu'nu**seçin.

3. **MainWindow** penceresine **düğme** denetimi ve **TextBox** denetimi ekleyin.

4. **TextBox** denetimini vurgulayın ve **Özellikler** penceresinde aşağıdaki değerleri ayarlayın:

    - **Ad** özelliğini `resultsTextBox`' ' ye ayarlama

    - **Yükseklik** özelliğini 250 olarak ayarlayın.

    - **Genişlik** özelliğini 500 olarak ayarlayın.

    - **Metin** sekmesinde, Lucida Console veya Global Monospace gibi tek boşluklu bir yazı tipi belirtin.

5. **Düğme** denetimini vurgulayın ve **Özellikler** penceresinde aşağıdaki değerleri ayarlayın:

    - **Ad** özelliğini `startButton`' ' ye ayarlama

    - **İçerik** özelliğinin değerini **Düğme'den** **Başlangıç**ekranına değiştirin.

6. Metin kutusunu ve düğmeyi, her ikisi de **Ana Pencere** penceresinde görünecek şekilde konumlandırın.

     WPF XAML Tasarımcısı hakkında daha fazla bilgi için Bkz. [XAML Designer kullanarak bir kullanıcı arabirimi oluşturma.](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio)

## <a name="add-a-reference"></a>Referans ekleme

1. **Çözüm Gezgini'nde**projenizin adını vurgulayın.

2. Menü çubuğunda, **Project** > **Add Reference'ı**seçin.

     **Başvuru Yöneticisi** iletişim kutusu görüntülenir.

3. İletişim kutusunun üst kısmında, projenizin .NET Framework 4.5 veya daha yüksek hedeflediğini doğrulayın.

4. **Derlemeler** kategorisinde, henüz seçilmemişse **Çerçeve'yi** seçin.

5. Adlar listesinde **System.Net.Http** onay kutusunu seçin.

6. İletişim kutusunu kapatmak için **Tamam** düğmesini seçin.

## <a name="add-necessary-using-directives"></a>Yönergeleri kullanarak gerekli ekleme

1. **Çözüm Gezgini'nde,** MainWindow.xaml.cs için kısayol menüsünü açın ve ardından **Kodu Görüntüle'yi**seçin.

2. Zaten mevcut `using` değillerse kod dosyasının en üstüne aşağıdaki yönergeleri ekleyin.

    ```csharp
    using System.Net.Http;
    using System.Net;
    using System.IO;
    ```

## <a name="create-a-synchronous-app"></a>Eşzamanlı bir uygulama oluşturma

1. Tasarım penceresinde, MainWindow.xaml, MainWindow.xaml.cs olay **Start** işleyicisi `startButton_Click` oluşturmak için Başlat düğmesini çift tıklatın.

2. MainWindow.xaml.cs, aşağıdaki kodu gövdeye `startButton_Click`kopyalayın:

    ```csharp
    resultsTextBox.Clear();
    SumPageSizes();
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";
    ```

    Kod, `SumPageSizes`uygulamayı yönlendiren yöntemi çağırır ve denetim `startButton_Click`.

3. Senkron çözümün kodu aşağıdaki dört yöntemi içerir:

    - `SumPageSizes`, web sayfası URL'lerinin bir `SetUpURLList` listesini alır `GetURLContents` `DisplayResults` ve daha sonra aramaları ve her URL işlemek için.

    - `SetUpURLList`, web adreslerinin listesini yapar ve döndürür.

    - `GetURLContents`, her web sitesinin içeriğini indirir ve bir bayt dizisi olarak içeriğini döndürür.

    - `DisplayResults`, her URL için bayt dizisindebayt sayısını görüntüler.

    Aşağıdaki dört yöntemi kopyalayın ve MainWindow.xaml.cs `startButton_Click` olay işleyicisinin altına yapıştırın:

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

## <a name="test-the-synchronous-solution"></a>Senkron çözümü test edin

Programı çalıştırmak için **F5** tuşunu seçin ve ardından **Başlat** düğmesini seçin.

Aşağıdaki listeye benzeyen çıktı görünmelidir:

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

Sayımların görüntülenmesinin birkaç saniye sürdüğünü unutmayın. Bu süre zarfında, istenen kaynakların karşıdan yüklenmesini beklerken UI iş parçacığı engellenir. Sonuç olarak, **Başlat** düğmesini seçtikten sonra ekran penceresini taşıyamaz, en üst düzeye çıkaramaz, simge durumuna indiremez ve hatta kapatamazsınız. Bu çabalar, bayt sayıları görünmeye başlayana kadar başarısız dır. Bir web sitesi yanıt vermiyorsa, hangi sitenin başarısız olduğuna dair bir belirti yoktur. Beklemeyi bırakıp programı kapatmak bile zordur.

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a>GetURLContents'i eşzamanlı bir yönteme dönüştürme

1. Senkron çözümü bir asynchronous çözüme dönüştürmek için, başlbaşlamak için en <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebRequest.GetResponse%2A> iyi yer, <xref:System.IO.Stream.CopyTo%2A> `GetURLContents` çünkü yönteme ve <xref:System.IO.Stream> yönteme yapılan çağrılar uygulamanın web'e eriştiği yerdir. .NET Framework, her iki yöntemin eşzamanlı sürümlerini sağlayarak dönüşümü kolaylaştırır.

     Kullanılan `GetURLContents`yöntemler hakkında daha fazla bilgi <xref:System.Net.WebRequest>için bkz.

    > [!NOTE]
    > Bu izbindeki adımları izlediğiniz de, birkaç derleyici hatası görüntülenir. Bunları yok sayabilir ve izliğe devam edebilirsiniz.

     Üçüncü satırda `GetURLContents` çağrılan yöntemi asynchronous, görev tabanlı `GetResponse` <xref:System.Net.WebRequest.GetResponseAsync%2A> yönteme değiştirin.

    ```csharp
    using (WebResponse response = webReq.GetResponseAsync())
    ```

2. `GetResponseAsync`bir <xref:System.Threading.Tasks.Task%601>' yi döndürür. Bu durumda, *görev iade değişkeni*, , `TResult`türü <xref:System.Net.WebResponse>vardır. Görev, istenen veriler karşıdan `WebResponse` yüklendikten ve görev tamamlanmak üzere çalıştırıldıktan sonra gerçek bir nesne oluşturma sözüdür.

     Görevden `WebResponse` değeri almak için, `GetResponseAsync`aşağıdaki kodun gösterdiği gibi çağrıya bir [bekleyen](../../../language-reference/operators/await.md) işleci uygulayın.

    ```csharp
    using (WebResponse response = await webReq.GetResponseAsync())
    ```

     İşleç, `await` `GetURLContents`beklenen görev tamamlanana kadar geçerli yöntemin yürütülmesini askıya adatır. Bu arada, denetim geçerli yöntemin arayan döndürür. Bu örnekte, geçerli `GetURLContents`yöntem ve arayan `SumPageSizes`. Görev tamamlandığında, vaat edilen `WebResponse` nesne beklenen görevin değeri olarak üretilir ve `response`değişkene atanır.

     Önceki deyim, ne olduğunu açıklığa kavuşturmak için aşağıdaki iki ifadeye ayrılabilir.

    ```csharp
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();
    //using (WebResponse response = await responseTask)
    ```

     Arama bir `webReq.GetResponseAsync` `Task(Of WebResponse)` veya `Task<WebResponse>`. Daha sonra `WebResponse` değeri almak için göreve bir bekleme işleci uygulanır.

     Async yönteminizin görevi tamamlamasına bağlı olmayan bir çalışması varsa, yöntem bu iki deyim arasında, async yöntemine yapılan çağrıdan `await` sonra ve işleç uygulanmadan önce bu çalışmaya devam edebilir. Örneğin, [async ve await (C#) kullanarak paralel olarak birden çok web isteği nasıl yapılır](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) ve [Task.WhenAll (C#) kullanarak async walkthrough genişletmek için nasıl](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)bakın.

3. Önceki adımda `await` işleci eklediğiniz için derleyici hatası oluşur. İşleç yalnızca [async](../../../language-reference/keywords/async.md) değiştirici ile işaretlenmiş yöntemlerde kullanılabilir. Çağrıyı bir çağrıyla değiştirmek için `CopyTo` dönüşüm adımlarını yinelerken hatayı `CopyToAsync`yoksay.

    - 'ye çağrılan yöntemin adını <xref:System.IO.Stream.CopyToAsync%2A>değiştirin.

    - Veya `CopyTo` `CopyToAsync` yöntem bağımsız değişkenine `content`bayt kopyalar ve anlamlı bir değer döndürmez. Senkron sürümde, çağrı bir `CopyTo` değer döndürmeyen basit bir ifadedir. Asynchronous sürümü, `CopyToAsync`bir <xref:System.Threading.Tasks.Task>. Görev "Görev(void)" gibi işlevgörür ve yöntemin beklenen olmasını sağlar. Aşağıdaki `Await` `await` kodun gösterdiği `CopyToAsync`gibi, çağrıya uygulayın veya çağrıya uygulayın.

        ```csharp
        await responseStream.CopyToAsync(content);
        ```

         Önceki deyim, aşağıdaki iki kod satırını kısaltır.

        ```csharp
        // CopyToAsync returns a Task, not a Task<T>.
        //Task copyTask = responseStream.CopyToAsync(content);

        // When copyTask is completed, content contains a copy of
        // responseStream.
        //await copyTask;
        ```

4. Yapılması gereken tek `GetURLContents` şey yöntem imzasını ayarlamaktır. İşleç'i `await` yalnızca [async](../../../language-reference/keywords/async.md) değiştirici ile işaretlenmiş yöntemlerde kullanabilirsiniz. Aşağıdaki kodun gösterdiği gibi, yöntemi *bir async yöntemi*olarak işaretlemek için değiştirici ekleyin.

    ```csharp
    private async byte[] GetURLContents(string url)
    ```

5. Bir async yönteminin dönüş türü <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>yalnızca `void` , veya C# olabilir. Genellikle, bir dönüş `void` türü yalnızca gerekli olduğu bir `void` async olay işleyicisi kullanılır. Diğer durumlarda, tamamlanan `Task(T)` yöntemde T türü bir değer döndüren bir [iade](../../../language-reference/keywords/return.md) deyimi varsa ve tamamlanan yöntem anlamlı bir değer döndürmüyorsa kullanırsınız. `Task` `Task` İade türünü "Görev(boşluk)" anlamında düşünebilirsiniz.

     Daha fazla bilgi için [Bkz. Async İade Türleri (C#)](./async-return-types.md).

     Yöntemin `GetURLContents` bir iade deyimi vardır ve deyim bir bayt dizisini döndürür. Bu nedenle, async sürümünün dönüş türü, T'nin bir bayt dizisi olduğu Görev(T) türüdür. Yöntem imzasında aşağıdaki değişiklikleri yapın:

    - İade türünü `Task<byte[]>`' le değiştirin

    - Kural olarak, eşişme yöntemleri "Async" ile biten adlar `GetURLContentsAsync`vardır, bu nedenle yöntemi yeniden adlandırın.

     Aşağıdaki kod bu değişiklikleri gösterir.

    ```csharp
    private async Task<byte[]> GetURLContentsAsync(string url)
    ```

     Bu birkaç değişiklikle, `GetURLContents` eşzamanlı bir yönteme dönüştürme tamamlandı.

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a>SumPageSizes'ı eşzamanlı bir yönteme dönüştürme

1. Önceki `SumPageSizes`yordamdan gelen adımları yineleyin. İlk olarak, aramayı `GetURLContents` eşzamanlı çağrıya çevirin.

    - Daha önce `GetURLContents` `GetURLContentsAsync`yapmadıysanız, "bu yöntemden" olarak çağrılan yöntemin adını değiştirin.

    - Bayt dizi `GetURLContentsAsync` değerini elde etmek için dönen göreve uygulayın. `await`

     Aşağıdaki kod bu değişiklikleri gösterir.

    ```csharp
    byte[] urlContents = await GetURLContentsAsync(url);
    ```

     Önceki atama, aşağıdaki iki kod satırını kısaltır.

    ```csharp
    // GetURLContentsAsync returns a Task<T>. At completion, the task
    // produces a byte array.
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //byte[] urlContents = await getContentsTask;
    ```

2. Yöntemin imzasında aşağıdaki değişiklikleri yapın:

    - Yöntemi `async` değiştirici ile işaretleyin.

    - Yöntem adına "Async" ekleyin.

    - T. için bir değer `SumPageSizesAsync` döndürmediği için bu sefer görev iade değişkeni yoktur, T, bu sefer (Yöntemin deyimi yoktur.) `return` Ancak, yöntem beklenilebilir bir dönmek `Task` gerekir. Bu nedenle, yöntemin dönüş `void` türünü `Task`' den ' e değiştirin.

    Aşağıdaki kod bu değişiklikleri gösterir.

    ```csharp
    private async Task SumPageSizesAsync()
    ```

     `SumPageSizes` Dönüştürme `SumPageSizesAsync` tamamlandı.

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a>startButton_Click bir eşzamanlı yönteme dönüştürme

1. Olay işleyicisinde, çağrılan yöntemin `SumPageSizes` adını `SumPageSizesAsync`, henüz yapmadıysanız değiştirin.

2. Bir `SumPageSizesAsync` async yöntemi olduğundan, sonucu beklemek için olay işleyicisi kodu değiştirin.

     Çağrıyı `SumPageSizesAsync` yansıtmak için `CopyToAsync` `GetURLContentsAsync`çağrı. Arama bir `Task`döndürür, bir `Task(T)`.

     Önceki yordamlarda olduğu gibi, bir veya iki deyim kullanarak aramayı dönüştürebilirsiniz. Aşağıdaki kod bu değişiklikleri gösterir.

    ```csharp
    // One-step async call.
    await SumPageSizesAsync();

    // Two-step async call.
    //Task sumTask = SumPageSizesAsync();
    //await sumTask;
    ```

3. İşleme yanlışlıkla yeniden girmesini önlemek için **Başlat** düğmesini `startButton_Click` devre dışı katmak için en üstteki ifadeyi ekleyin.

    ```csharp
    // Disable the button until the operation is complete.
    startButton.IsEnabled = false;
    ```

     Olay işleyicisinin sonundaki düğmeyi yeniden etkinleştirebilirsiniz.

    ```csharp
    // Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = true;
    ```

     Reentrancy hakkında daha fazla bilgi için, [Async Apps (C#) içinde Reentrancy Işleme](./handling-reentrancy-in-async-apps.md)bakın.

4. Son olarak, `async` olay işleyicisi bekliyor `SumPagSizesAsync`böylece bildirime değiştirici ekleyin.

    ```csharp
    private async void startButton_Click(object sender, RoutedEventArgs e)
    ```

     Genellikle, olay işleyicilerinin adları değiştirilmez. Olay işleyicileri döndürmesi `Task` `void`gerektiğinden, iade türü değiştirilmez.

     Projenin senkron işlemden asynchronous işleme ye dönüştürülmesi tamamlandı.

## <a name="test-the-asynchronous-solution"></a>Asynchronous çözeltisini test edin

1. Programı çalıştırmak için **F5** tuşunu seçin ve ardından **Başlat** düğmesini seçin.

2. Senkron çözeltinin çıktısını andıran çıktı görünmelidir. Ancak, aşağıdaki farklılıklara dikkat edin.

    - İşlem tamamlandıktan sonra tüm sonuçlar aynı anda oluşmaz. Örneğin, her iki program `startButton_Click` da metin kutusunu temizleyen bir satır içerir. Amaç, bir sonuç kümesi ortaya çıktıktan sonra ikinci kez **Başlat** düğmesini seçerseniz, çalıştırmalar arasındaki metin kutusunu temizlemektir. Senkron sürümde, metin kutusu, karşıdan yüklemeler tamamlandığında ve Kullanıcı Arabirimi iş parçacığı başka işler yapmakta özgür olduğunda, sayımlar ikinci kez görünmeden hemen önce temizlenir. Eşzamanlı sürümde, **başlat** düğmesini seçtikten hemen sonra metin kutusu temizlenir.

    - En önemlisi, UI iş parçacığı indirme sırasında engellenmez. Web kaynakları karşıdan yüklenirken, sayılırken ve görüntülenirken pencereyi taşıyabilir veya yeniden boyutlandırabilirsiniz. Web sitelerinden biri yavaşsa veya yanıt vermiyorsa, **Kapat** düğmesini (sağ üst köşedeki kırmızı alandaki x) seçerek işlemi iptal edebilirsiniz.

## <a name="replace-method-geturlcontentsasync-with-a-net-framework-method"></a>GetURLContentsAsync yöntemini bir .NET Framework yöntemiyle değiştirin

1. .NET Framework 4.5, kullanabileceğiniz birçok async yöntemi sağlar. Bunlardan biri, <xref:System.Net.Http.HttpClient> yöntem <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, bu walkthrough için gereken sadece ne yapar. Daha önceki bir yordamda oluşturduğunuz `GetURLContentsAsync` yöntem yerine kullanabilirsiniz.

     İlk adım yöntemde `HttpClient` `SumPageSizesAsync`bir nesne oluşturmaktır. Yöntemin başında aşağıdaki bildirimi ekleyin.

    ```csharp
    // Declare an HttpClient object and increase the buffer size. The
    // default buffer size is 65,536.
    HttpClient client =
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };
    ```

2. Yönteme `SumPageSizesAsync,` `GetURLContentsAsync` yapılan çağrıyı `HttpClient` yönteme yapılan bir çağrıyla değiştirin.

    ```csharp
    byte[] urlContents = await client.GetByteArrayAsync(url);
    ```

3. Yazdığınız `GetURLContentsAsync` yöntemi kaldırın veya yorum yapın.

4. Programı çalıştırmak için **F5** tuşunu seçin ve ardından **Başlat** düğmesini seçin.

     Projenin bu sürümünün davranışı, "Asynchronous çözümünü sınamak için" yordamının açıkladığı davranışla eşleşmelidir, ancak sizden daha az çaba göstermelidir.

## <a name="example-code"></a>Örnek kod

Aşağıdaki kod, yazdığınız eşzamanlı `GetURLContentsAsync` yöntemi kullanarak eşzamanlı bir çözümden eşzamanlı bir çözüme dönüştürmenin tam örneğini içerir. Orijinal, eşzamanlı çözüme güçlü bir şekilde benzediğine dikkat edin.

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

Aşağıdaki kod, `GetByteArrayAsync`yöntemi kullanan çözümün tam `HttpClient` örneğini içerir.

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

- [Async Örnek: Web Walkthrough (C # ve Visual Basic) erişim](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hh300224(v=vs.110))
- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
- [Async ve await ile Asynchronous Programlama (C#)](./index.md)
- [Async İade Türleri (C#)](./async-return-types.md)
- [Görev Tabanlı Eşzamanlı Programlama (TAP)](https://www.microsoft.com/download/details.aspx?id=19957)
- [Task.WhenAll (C#) kullanarak async walkthrough nasıl genişletilir](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [Async ve await (C#) kullanarak paralel olarak birden fazla web istekleri yapmak için nasıl](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
