---
title: "İzlenecek yol: async kullanarak Web'e erişme ve await (C#)"
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: 24ce1e405019ef83ff6bcbb61552d6fc5d911935
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46529852"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a>İzlenecek yol: async kullanarak Web'e erişme ve await (C#)

Async ve await özelliklerini kullanarak zaman uyumsuz programları daha kolay ve sezgisel bir şekilde yazabilirsiniz. Zaman uyumlu kod gibi görünen zaman uyumsuz kod yazabilir ve zor geri çağırma işlevleri ve zaman uyumsuz kod genellikle kapsar devamlılıklar derleyici olanak tanır.

Async özelliği hakkında daha fazla bilgi için bkz. [Asynchronous Programming with async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).

Bu izlenecek yol, Web sitelerinin bir listesiyle bayt sayısını toplar. zaman uyumlu bir Windows Presentation Foundation (WPF) uygulaması ile başlar. İzlenecek yol, yeni özellikleri kullanarak zaman uyumsuz bir çözümü uygulamaya ardından dönüştürür.

Uygulamaları kendiniz yapılandırmak istemiyorsanız, indirebileceğiniz [zaman uyumsuz örneği: izlenecek yol (C# ve Visual Basic) erişme](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).

> [!NOTE]
> Yeni bilgisayarınızda yüklü veya örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.

## <a name="create-a-wpf-application"></a>WPF uygulaması oluşturma

1.  Visual Studio'yu başlatın.

2.  Menü çubuğunda, **dosya** > **yeni** > **proje**.

     **Yeni proje** iletişim kutusu açılır.

3.  İçinde **yüklü şablonlar** bölmesinde, Visual C# ' ı seçin ve ardından **WPF uygulaması** proje türleri listesinden.

4.  İçinde **adı** metin kutusuna `AsyncExampleWPF`ve ardından **Tamam** düğmesi.

     Yeni Proje görünür **Çözüm Gezgini**.

## <a name="design-a-simple-wpf-mainwindow"></a>Basit bir WPF MainWindow tasarlama

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

## <a name="add-a-reference"></a>Bir başvuru ekleyin

1.  İçinde **Çözüm Gezgini**, projenizin adını vurgulayın.

2.  Menü çubuğunda, **proje** > **Başvuru Ekle**.

     **Başvuru Yöneticisi** iletişim kutusu görüntülenir.

3.  İletişim kutusunun en üstünde, projeniz .NET Framework 4.5 veya üzerini hedeflediğinden doğrulayın.

4.  İçinde **derlemeleri** kategorisi seçin **Framework** tercih değildir.

5.  Adları listesinde seçin **System.Net.Http** onay kutusu.

6.  Seçin **Tamam** iletişim kutusunu kapatmak için düğme.

## <a name="add-necessary-using-directives"></a>Ekleme yönergeleri kullanarak gerekli

1.  İçinde **Çözüm Gezgini**için MainWindow.xaml.cs kısayol menüsünü açın ve ardından **kodu görüntüle**.

2.  Aşağıdaki `using` zaten mevcut değillerse kod dosyanın üst kısmındaki yönergeleri.

    ```csharp
    using System.Net.Http;
    using System.Net;
    using System.IO;
    ```

## <a name="create-a-synchronous-app"></a>Zaman uyumlu bir uygulama oluşturma

1.  Tasarım penceresinde, MainWindow.xaml **Başlat** oluşturmak için düğmeyi `startButton_Click` MainWindow.xaml.cs olay işleyicisi.

2.  MainWindow.xaml.cs içinde gövdesine aşağıdaki kodu kopyalayın `startButton_Click`:

    ```csharp
    resultsTextBox.Clear();
    SumPageSizes();
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";
    ```

    Kod uygulama sürücüleri yöntemini çağırır `SumPageSizes`ve denetim döndüğünde, bir ileti görüntüler `startButton_Click`.

3.  Aşağıdaki dört yöntemi zaman uyumlu çözüm için kod içerir:

    -   `SumPageSizes`, Web sayfasını URL'lerin bir listesini alır `SetUpURLList` ve `GetURLContents` ve `DisplayResults` her URL işlenecek.

    -   `SetUpURLList`, yapar ve web adreslerinden oluşan bir liste döndürür.

    -   `GetURLContents`, her bir Web sitesinin içeriklerini karşıdan yükler ve içeriği bir bayt dizisi olarak döndürür.

    -   `DisplayResults`, görüntüleyen bayt bayt dizisindeki her URL.

    Aşağıdaki dört yöntemi kopyalayın ve yapıştırın altında `startButton_Click` MainWindow.xaml.cs olay işleyicisinde:

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

## <a name="test-the-synchronous-solution"></a>Zaman uyumlu çözümü test

Seçin **F5** programı çalıştırmak için anahtar ve ardından **Başlat** düğmesi.

Aşağıdaki listede benzer bir çıktı görünmelidir:

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

Sayıları görüntülemek için birkaç saniye sürer dikkat edin. İstenen kaynaklara indirmek beklediği sırada bu süre boyunca, kullanıcı Arabirimi iş parçacığı engellenir. Sonuç olarak, taşıyamazsınız, en üst düzeye çıkarmak, en aza indirmek veya seçtiğiniz sonra bile görüntü penceresini kapatın **Başlat** düğmesi. Görüntülenecek bayt sayısını başlatana kadar bu çalışmaların başarısız. Bir Web sitesi yanıt vermediği takdirde başarısız hangi sitenin herhangi bir gösterge sahip olursunuz. Programı kapatmak ve bile beklemek istemiyorsanız zordur.

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a>Zaman uyumsuz bir yöntem GetURLContents Dönüştür

1.  Zaman uyumlu çözüm için zaman uyumsuz bir çözümün dönüştürmek için başlatmak için en iyi yeri yer `GetURLContents` çünkü çağrıları <xref:System.Net.HttpWebRequest> yöntemi <xref:System.Net.HttpWebRequest.GetResponse%2A> ve <xref:System.IO.Stream> yöntemi <xref:System.IO.Stream.CopyTo%2A> uygulamaya web eriştiği olan . .NET Framework dönüştürme iki yöntem de zaman uyumsuz sürümlerini sağlanarak kolaylaştırır.

     Kullanılan yöntemleri hakkında daha fazla bilgi için `GetURLContents`, bkz: <xref:System.Net.WebRequest>.

    > [!NOTE]
    > Bu izlenecek yolda adımları gibi birkaç derleyici hatalar görüntülenir. Bunların yoksayılması ve adım adım kılavuza devam edebilirsiniz.

     Üçüncü satırında çağrılan yöntem Değiştir `GetURLContents` gelen `GetResponse` için zaman uyumsuz, görev tabanlı <xref:System.Net.WebRequest.GetResponseAsync%2A> yöntemi.

    ```csharp
    using (WebResponse response = webReq.GetResponseAsync())
    ```

2.  `GetResponseAsync` döndürür bir <xref:System.Threading.Tasks.Task%601>. Bu durumda, *görev dönüş değişkeni*, `TResult`, türünde <xref:System.Net.WebResponse>. Görev bir gerçek üretmek için bir vaattir `WebResponse` istenen veri indirildi ve görevin çalıştırılıp tamamlandıktan sonra nesne.

     Alınacak `WebResponse` görevden değer, geçerli bir [await](../../../../csharp/language-reference/keywords/await.md) işleci çağrısına `GetResponseAsync`aşağıdaki kodda gösterildiği gibi.

    ```csharp
    using (WebResponse response = await webReq.GetResponseAsync())
    ```

     `await` İşleci geçerli yöntemin yürütülmesini askıya `GetURLContents`, beklenen görev tamamlanana kadar. Bu sırada, denetim geçerli yöntemi çağırana döner. Bu örnekte, geçerli bir yöntemdir `GetURLContents`, ve çağıran `SumPageSizes`. Görev tamamlandığında, taahhüt `WebResponse` nesne imzalamasına değeri olarak üretilen ve değişkenine atanan `response`.

     Önceki deyim ne olduğunu açıklamak için aşağıdaki iki ifadeye ayrılabilir.

    ```csharp
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();
    //using (WebResponse response = await responseTask)
    ```

     Çağrı `webReq.GetResponseAsync` döndürür bir `Task(Of WebResponse)` veya `Task<WebResponse>`. Alınacak göreve await işleci uygulanır `WebResponse` değeri.

     Zaman uyumsuz yöntem görev öğesinin tamamlanmasına bağlı olmayan bağımsız yapılacak çalışmaya sahipse yöntem çağrısından önce zaman uyumsuz yöntem ve sonra bu iki deyimden arasında bu çalışmalar ile devam edebilir `await` işleci uygulanır. Örnekler için bkz [nasıl yapılır: zaman uyumsuz kullanarak birden çok Web isteğini paralel hale getirme ve await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) ve [nasıl yapılır: zaman uyumsuz izlenecek yolu Task.WhenAll (C#) kullanarak genişletme](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).

3.  Eklediğiniz çünkü `await` işleci önceki adımda, bir derleyici hatası oluşur. İşleci ile işaretlenmiş yöntemler kullanılabilir [zaman uyumsuz](../../../../csharp/language-reference/keywords/async.md) değiştiricisi. Çağrısını için dönüştürme adımı yineleyin ancak hatasını görmezden Gel `CopyTo` çağrısıyla `CopyToAsync`.

    -   İçin çağrılan yöntemin adını değiştirmek <xref:System.IO.Stream.CopyToAsync%2A>.

    -   `CopyTo` Veya `CopyToAsync` yöntemi, bağımsız değişkeni için bayt kopyalar `content`ve anlamlı bir değer döndürmüyor. Zaman uyumlu sürümü, çağrı `CopyTo` bir değer döndürmüyor basit bir ifadedir. Zaman uyumsuz sürümü `CopyToAsync`, döndürür bir <xref:System.Threading.Tasks.Task>. Görev "Task(void)" gibi çalışır ve beklenmesini yöntemi sağlar. Uygulama `Await` veya `await` çağrısına `CopyToAsync`aşağıdaki kodda gösterildiği gibi.

        ```csharp
        await responseStream.CopyToAsync(content);
        ```

         Önceki deyim, aşağıdaki iki kod satırlarını kısaltmasıdır.

        ```csharp
        // CopyToAsync returns a Task, not a Task<T>.
        //Task copyTask = responseStream.CopyToAsync(content);

        // When copyTask is completed, content contains a copy of
        // responseStream.
        //await copyTask;
        ```

4.  Tüm bu yapılması kalır `GetURLContents` yöntem imzası ayarlamak için. Kullanabileceğiniz `await` ile işaretlenmiş yöntemler işlecinde [zaman uyumsuz](../../../../csharp/language-reference/keywords/async.md) değiştiricisi. Yöntemi olarak işaretlemek için değiştiricisi Ekle bir *zaman uyumsuz yöntem*aşağıdaki kodda gösterildiği gibi.

    ```csharp
    private async byte[] GetURLContents(string url)
    ```

5.  Zaman uyumsuz bir yöntemin dönüş türü yalnızca olabilir <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, veya `void` C#. Genellikle, dönüş türü `void` yalnızca zaman uyumsuz olay işleyicisi kullanılan burada `void` gereklidir. Diğer durumlarda, kullandığınız `Task(T)` tamamlanmış yöntemi varsa bir [dönüş](../../../../csharp/language-reference/keywords/return.md) T değeri döndüren bir ifade yazın ve kullandığınız `Task` tamamlanmış yöntemi anlamlı bir değer döndürmezse. Düşünebilirsiniz `Task` dönüş türü olarak "Task(void)." anlamına gelir.

     Daha fazla bilgi için [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).

     Yöntemi `GetURLContents` bir dönüş ifadesi ve deyim bir bayt dizisi döndürür. Bu nedenle, zaman uyumsuz sürümü dönüş türünü görev(t), burada T bir bayt dizisi, ' dir. Yöntem imzasında aşağıdaki değişiklikleri yapın:

    -   Geri dönüş için değiştirme `Task<byte[]>`.

    -   Kural gereği, zaman uyumsuz yöntemler "Async," biten sahip. Bu nedenle metodu yeniden adlandırmak `GetURLContentsAsync`.

     Aşağıdaki kod, bu değişiklikleri gösterir.

    ```csharp
    private async Task<byte[]> GetURLContentsAsync(string url)
    ```

     Bu birkaç değişiklikle dönüştürülmesi `GetURLContents` zaman uyumsuz bir yöntem tamamlandıktan.

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a>Zaman uyumsuz bir yöntem SumPageSizes Dönüştür

1.  İçin önceki yordamdaki adımları yineleyin `SumPageSizes`. İlk olarak, araması olarak değiştirmelerine `GetURLContents` zaman uyumsuz bir çağrı için.

    -   Yönteminden çağrılan yöntemin adını değiştirmek `GetURLContents` için `GetURLContentsAsync`, zaten yapmadıysanız.

    -   Uygulama `await` görev, `GetURLContentsAsync` dizi değeri bayt almak için döndürür.

     Aşağıdaki kod, bu değişiklikleri gösterir.

    ```csharp
    byte[] urlContents = await GetURLContentsAsync(url);
    ```

     Önceki atama aşağıdaki iki kod satırlarını kısaltmasıdır.

    ```csharp
    // GetURLContentsAsync returns a Task<T>. At completion, the task
    // produces a byte array.
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //byte[] urlContents = await getContentsTask;
    ```

2.  Yöntemin imzası ' aşağıdaki değişiklikleri yapın:

    -   Yöntemi işaretlemek `async` değiştiricisi.

    -   "Async" yöntem adına ekleyin.

    -   T, hiçbir görev dönüş değişken bu süresi yoktur çünkü `SumPageSizesAsync` t için bir değer döndürmüyor (Yöntemin sahip olmayan `return` deyimi.) Ancak, yöntem döndürmelidir bir `Task` olması beklenebilir. Bu nedenle, metodun dönüş türü değiştirme `void` için `Task`.

    Aşağıdaki kod, bu değişiklikleri gösterir.

    ```csharp
    private async Task SumPageSizesAsync()
    ```

     Dönüştürme `SumPageSizes` için `SumPageSizesAsync` tamamlandı.

## <a name="convert-startbuttonclick-to-an-asynchronous-method"></a>Zaman uyumsuz bir yöntem startButton_Click Dönüştür

1.  Olay işleyicisi, çağrılan yöntemden adını değiştirmek `SumPageSizes` için `SumPageSizesAsync`, zaten yapmadıysanız.

2.  Çünkü `SumPageSizesAsync` bir zaman uyumsuz yöntem sonucu await için olay işleyicisinde kodu değiştirin.

     Çağrı `SumPageSizesAsync` çağrısı yansıtır `CopyToAsync` içinde `GetURLContentsAsync`. Çağrı döndürür bir `Task`değil bir `Task(T)`.

     Önceki yordamlardan olduğu gibi bir deyim ya da iki ifadeleri kullanarak arama dönüştürebilirsiniz. Aşağıdaki kod, bu değişiklikleri gösterir.

    ```csharp
    // One-step async call.
    await SumPageSizesAsync();

    // Two-step async call.
    //Task sumTask = SumPageSizesAsync();
    //await sumTask;
    ```

3.  İşlem yanlışlıkla yeniden girildi önlemek için üstüne aşağıdaki ifadeyi ekleyin `startButton_Click` devre dışı bırakmak için **Başlat** düğmesi.

    ```csharp
    // Disable the button until the operation is complete.
    startButton.IsEnabled = false;
    ```

     Olay işleyicisi sonunda düğmeyi yeniden etkinleştirebilirsiniz.

    ```csharp
    // Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = true;
    ```

     Yeniden giriş hakkında daha fazla bilgi için bkz: [(C#) zaman uyumsuz uygulamalarda yeniden girişi işleme](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).

4.  Son olarak, ekleme `async` değiştiricisi bildirimine olay işleyicisi await, böylece `SumPagSizesAsync`.

    ```csharp
    private async void startButton_Click(object sender, RoutedEventArgs e)
    ```

     Olay işleyicileri adları genellikle değiştirilmez. Dönüş türü için değiştirilmez `Task` olay işleyicileri dönüştürüldüğünden `void`.

     Proje dönüştürülmesi için zaman uyumsuz zaman uyumlu işlenmesi tamamlanır.

## <a name="test-the-asynchronous-solution"></a>Zaman uyumsuz bir çözümü test etme

1.  Seçin **F5** programı çalıştırmak için anahtar ve ardından **Başlat** düğmesi.

2.  Zaman uyumlu çözümün çıktıya benzer bir çıktı görünmelidir. Ancak, aşağıdaki farklar dikkat edin.

    -   Sonuçları işleme tamamlandıktan sonra aynı zamanda, tüm oluşmaz. Örneğin, her iki programın bir satır içeren `startButton_Click` , metin kutusuna temizler. Seçerseniz çalıştırmaları arasında metin kutusunu temizlemek için hedefi olan **Başlat** bir sonuç kümesini göründükten sonra ikinci bir kez, düğme. Yalnızca sayıları ne zaman karşıdan yüklemeler tamamlandı ve diğer işlerini gerçekleştirmek kullanıcı Arabirimi iş parçacığı ücretsizdir ikinci kez görünmesi zaman uyumlu bir sürümde, metin kutusu işaretli değildir. Seçtiğiniz hemen sonra metin kutusuna zaman uyumsuz sürümünde temizler **Başlat** düğmesi.

    -   En önemlisi de UI iş parçacığı yüklemeleri sırasında bloke değildir. Geçiş yapabilir veya web kaynakları indirilirken, penceresini yeniden boyutlandırdığınızda sayılan ve görüntülenir. Web sitelerinden birini ise yavaş veya yanıt vermiyor, işlem seçerek iptal edebilirsiniz **Kapat** düğmesine (sağ üst köşesinde kırmızı alanında x).

## <a name="replace-method-geturlcontentsasync-with-a-net-framework-method"></a>Bir .NET Framework yöntemi ile yöntem GetURLContentsAsync değiştirin

1.  .NET Framework 4.5 kullanabileceğiniz pek çok zaman uyumsuz yöntemler sağlar. Bunlardan biri <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, yalnızca bu kılavuz için ihtiyacınız olanları yapar. Bunu yerine `GetURLContentsAsync` bir önceki yordamda oluşturduğunuz yöntemi.

     İlk adım oluşturmaktır bir `HttpClient` yöntemi nesnesinde `SumPageSizesAsync`. Yönteminin başlangıcında aşağıdaki bildirimi ekleyin.

    ```csharp
    // Declare an HttpClient object and increase the buffer size. The
    // default buffer size is 65,536.
    HttpClient client =
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };
    ```

2.  İçinde `SumPageSizesAsync,` çağrısını, `GetURLContentsAsync` yöntemi çağrısıyla `HttpClient` yöntemi.

    ```csharp
    byte[] urlContents = await client.GetByteArrayAsync(url);
    ```

3.  Kaldırın veya açıklama `GetURLContentsAsync` yazdığınız yöntemi.

4.  Seçin **F5** programı çalıştırmak için anahtar ve ardından **Başlat** düğmesi.

     Bu sürümü, proje davranışını "zaman uyumsuz bir çözümü test etmek için" yordamı açıklanan davranışı eşleşen ancak sizden daha az çaba ile bile gerekir.

## <a name="example-code"></a>Örnek kod

Zaman uyumsuz kullanarak zaman uyumsuz bir çözüm eş zamanlı dönüştürme tam örneği aşağıdaki kodu içeren `GetURLContentsAsync` yazdığınız yöntemi. Bunu kesinlikle özgün, zaman uyumlu bir çözüm benzer olduğuna dikkat edin.

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

Aşağıdaki kod tam örneği kullanan bir çözüm içeren `HttpClient` yöntemi `GetByteArrayAsync`.

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

## <a name="see-also"></a>Ayrıca bkz.

- [Zaman uyumsuz örneği: izlenecek yol (C# ve Visual Basic) erişme](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [async](../../../../csharp/language-reference/keywords/async.md)
- [await](../../../../csharp/language-reference/keywords/await.md)
- [Zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
- [Zaman uyumsuz dönüş türleri (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)
- [Görev tabanlı zaman uyumsuz desen (TAP)](https://www.microsoft.com/en-us/download/details.aspx?id=19957)
- [Nasıl yapılır: zaman uyumsuz izlenecek yolu Task.WhenAll (C#) kullanarak genişletme](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [Nasıl yapılır: birden çok Web isteğini paralel olarak zaman uyumsuz kullanarak ve olun await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
