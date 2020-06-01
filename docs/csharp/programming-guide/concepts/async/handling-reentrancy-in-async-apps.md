---
title: Zaman uyumsuz uygulamalarda yeniden girişi işleme (C#)
ms.date: 07/20/2015
ms.assetid: 47c5075e-c448-45ce-9155-ed4e7e98c677
ms.openlocfilehash: e03e0f6ecd8e74dd8518f84ec03c76c1ef5b9ee6
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241818"
---
# <a name="handling-reentrancy-in-async-apps-c"></a>Zaman uyumsuz uygulamalarda yeniden girişi işleme (C#)

Uygulamanıza zaman uyumsuz kod eklediğinizde, işlem tamamlanmadan önce zaman uyumsuz bir işlemi yeniden girmeye işaret eden yeniden giriş yapmayı göz önünde bulundurmalı ve muhtemelen engellemeniz gerekir. Yeniden giriş için olanaklar tanımlamazsanız ve işleyemezseniz, bu durum beklenmedik sonuçlara neden olabilir.

**Bu konuda**

- [Yeniden giriş tanıma](#BKMK_RecognizingReentrancy)

- [Yeniden giriş işleme](#BKMK_HandlingReentrancy)

  - [Başlat düğmesini devre dışı bırak](#BKMK_DisableTheStartButton)

  - [Işlemi iptal edin ve yeniden başlatın](#BKMK_CancelAndRestart)

  - [Birden çok Işlemi çalıştırma ve çıktıyı sıraya alma](#BKMK_RunMultipleOperations)

- [Örnek uygulamayı inceleme ve çalıştırma](#BKMD_SettingUpTheExample)

> [!NOTE]
> Örneği çalıştırmak için bilgisayarınızda Visual Studio 2012 veya sonraki bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.

> [!NOTE]
> Aktarım Katmanı Güvenliği (TLS) sürüm 1,2 artık uygulama geliştirmede kullanılacak en düşük sürümdür. Uygulamanız 4,7 sürümünden önceki bir .NET Framework sürümünü hedefliyorsa, [.NET Framework birlikte Aktarım Katmanı Güvenliği (TLS) en iyi uygulamaları](../../../../framework/network-programming/tls.md)için aşağıdaki makaleye bakın.

## <a name="recognizing-reentrancy"></a><a name="BKMK_RecognizingReentrancy"></a>Yeniden giriş tanıma

Bu konudaki örnekte, kullanıcılar bir dizi Web sitesini indiren ve indirilen toplam bayt sayısını hesaplayan bir zaman uyumsuz uygulamayı başlatmak için bir **Başlat** düğmesi seçer. Örneğin zaman uyumlu bir sürümü, bir kullanıcının düğmeyi kaç kez seçtiğinden bağımsız olarak aynı şekilde yanıt verir, çünkü ilk kez sonra, uygulama çalışmaya bitene kadar UI iş parçacığı bu olayları yoksayar. Ancak zaman uyumsuz bir uygulamada, UI iş parçacığı yanıt vermeye devam eder ve tamamlanmadan önce zaman uyumsuz işlemi yeniden girebilirsiniz.

Aşağıdaki örnek, Kullanıcı **Başlat** düğmesini yalnızca bir kez seçerse beklenen çıktıyı gösterir. İndirilen Web sitelerinin listesi, her sitenin bayt cinsinden boyutu ile görüntülenir. Toplam bayt sayısı sonda görüntülenir.

```output
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

Ancak Kullanıcı düğmeyi birden çok kez seçerse, olay işleyicisi sürekli olarak çağrılır ve yükleme işlemi her seferinde yeniden girilir. Sonuç olarak, birkaç zaman uyumsuz işlem aynı anda çalışır, çıkış sonuçları birbirine bırakır ve toplam bayt sayısı kafa karıştırıcı olur.

```output
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
6. msdn.microsoft.com/library/ms404677.aspx               197325
3. msdn.microsoft.com/library/jj155761.aspx                29019
7. msdn.microsoft.com                                            42972
4. msdn.microsoft.com/library/hh290140.aspx               117152
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591

5. msdn.microsoft.com/library/hh524395.aspx                68959
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
6. msdn.microsoft.com/library/ms404677.aspx               197325
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
7. msdn.microsoft.com                                            42972
5. msdn.microsoft.com/library/hh524395.aspx                68959
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591

6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

Bu çıkışın sonuna kadar kayarak bu çıktıyı üreten kodu gözden geçirebilirsiniz. Çözümü yerel bilgisayarınıza indirerek ve ardından WebsiteDownload projesini çalıştırarak veya kendi projenizi oluşturmak için bu konunun sonundaki kodu kullanarak kodu deneyebilirsiniz. Daha fazla bilgi ve yönergeler için bkz. [Örnek uygulamayı inceleme ve çalıştırma](#BKMD_SettingUpTheExample).

## <a name="handling-reentrancy"></a><a name="BKMK_HandlingReentrancy"></a>Yeniden giriş işleme

Uygulamanızın ne yaptığını istediğinize bağlı olarak çeşitli yollarla yeniden giriş gerçekleştirebilirsiniz. Bu konu aşağıdaki örnekleri sunmaktadır:

- [Başlat düğmesini devre dışı bırak](#BKMK_DisableTheStartButton)

  İşlem çalışırken kullanıcının kesintiye uğramaması için **Başlat** düğmesini devre dışı bırakın.

- [Işlemi iptal edin ve yeniden başlatın](#BKMK_CancelAndRestart)

  Kullanıcı **Başlat** düğmesini yeniden seçtiğinde çalışmaya devam eden tüm işlemleri iptal edin ve son istenen işlemin devam etmesine izin verin.

- [Birden çok Işlemi çalıştırma ve çıktıyı sıraya alma](#BKMK_RunMultipleOperations)

  Tüm istenen işlemlerin zaman uyumsuz olarak çalışmasına izin verin, ancak her bir işlemin sonuçlarının bir arada ve sırayla görünmesi için çıktının görüntülenmesini koordine edin.

### <a name="disable-the-start-button"></a><a name="BKMK_DisableTheStartButton"></a>Başlat düğmesini devre dışı bırak

Olay işleyicisinin en üstündeki düğmeyi devre dışı bırakarak, bir işlem çalışırken **Başlat** düğmesini engelleyebilirsiniz `StartButton_Click` . Böylece, `finally` Kullanıcılar uygulamayı yeniden çalıştırabilmeleri için işlem bittiğinde düğmeyi bir blok içinden yeniden etkinleştirebilirsiniz.

Bu senaryoyu ayarlamak için, [Örnek uygulamayı gözden geçirmek ve çalıştırmak](#BKMD_SettingUpTheExample)için belirtilen temel kodda aşağıdaki değişiklikleri yapın. Tamamlanmış uygulamayı [zaman uyumsuz örneklerden de indirebilirsiniz: .net masaüstü uygulamalarında yeniden giriş](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Projenin adı DisableStartButton olur.

```csharp
private async void StartButton_Click(object sender, RoutedEventArgs e)
{
    // This line is commented out to make the results clearer in the output.
    //ResultsTextBox.Text = "";

    // ***Disable the Start button until the downloads are complete.
    StartButton.IsEnabled = false;

    try
    {
        await AccessTheWebAsync();
    }
    catch (Exception)
    {
        ResultsTextBox.Text += "\r\nDownloads failed.";
    }
    // ***Enable the Start button in case you want to run the program again.
    finally
    {
        StartButton.IsEnabled = true;
    }
}
```

Değişikliklerin bir sonucu olarak, `AccessTheWebAsync` Web siteleri indirilirken düğme yanıt vermez, bu nedenle işlem yeniden girilemez.

### <a name="cancel-and-restart-the-operation"></a><a name="BKMK_CancelAndRestart"></a>Işlemi iptal edin ve yeniden başlatın

**Başlat** düğmesini devre dışı bırakmak yerine düğmeyi etkin tutabilirsiniz, ancak kullanıcı bu düğmeyi yeniden seçerse, zaten çalışmakta olan işlemi iptal edin ve en son başlatılan işlemin devam etmesine izin verin.

İptal hakkında daha fazla bilgi için bkz. [zaman uyumsuz uygulamanızda Ince ayar yapma (C#)](./fine-tuning-your-async-application.md).

Bu senaryoyu ayarlamak için, [Örnek uygulamayı gözden geçirmek ve çalıştırmak](#BKMD_SettingUpTheExample)için belirtilen temel kodda aşağıdaki değişiklikleri yapın. Tamamlanmış uygulamayı [zaman uyumsuz örneklerden de indirebilirsiniz: .net masaüstü uygulamalarında yeniden giriş](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Projenin adı, geçersiz bir şekilde başlatılır.

1. <xref:System.Threading.CancellationTokenSource> `cts` Tüm yöntemler için kapsam içinde olan bir değişken bildirin.

    ```csharp
    public partial class MainWindow : Window   // Or class MainPage
    {
        // *** Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. ' De `StartButton_Click` , bir işlemin zaten devam edilip edilmeyeceğini saptayın. Değeri `cts` null ise, zaten etkin olan bir işlem yoktur. Değer null değilse, zaten çalışmakta olan işlem iptal edilir.

    ```csharp
    // *** If a download process is already underway, cancel it.
    if (cts != null)
    {
        cts.Cancel();
    }
    ```

3. `cts`Geçerli işlemi temsil eden farklı bir değere ayarlayın.

    ```csharp
    // *** Now set cts to a new value that you can use to cancel the current process
    // if the button is chosen again.
    CancellationTokenSource newCTS = new CancellationTokenSource();
    cts = newCTS;
    ```

4. Öğesinin sonunda `StartButton_Click` , geçerli işlem tamamlanmıştır, bu yüzden `cts` geri değerini null olarak ayarlayın.

    ```csharp
    // *** When the process is complete, signal that another process can begin.
    if (cts == newCTS)
        cts = null;
    ```

Aşağıdaki kod, içindeki tüm değişiklikleri gösterir `StartButton_Click` . Ekler yıldız işaretiyle işaretlenir.

```csharp
private async void StartButton_Click(object sender, RoutedEventArgs e)
{
    // This line is commented out to make the results clearer in the output.
    //ResultsTextBox.Clear();

    // *** If a download process is already underway, cancel it.
    if (cts != null)
    {
        cts.Cancel();
    }

    // *** Now set cts to cancel the current process if the button is chosen again.
    CancellationTokenSource newCTS = new CancellationTokenSource();
    cts = newCTS;

    try
    {
        // ***Send cts.Token to carry the message if there is a cancellation request.
        await AccessTheWebAsync(cts.Token);

    }
    // *** Catch cancellations separately.
    catch (OperationCanceledException)
    {
        ResultsTextBox.Text += "\r\nDownloads canceled.\r\n";
    }
    catch (Exception)
    {
        ResultsTextBox.Text += "\r\nDownloads failed.\r\n";
    }
    // *** When the process is complete, signal that another process can proceed.
    if (cts == newCTS)
        cts = null;
}
```

' De `AccessTheWebAsync` , aşağıdaki değişiklikleri yapın.

- İptal belirtecini kabul etmek için bir parametre ekleyin `StartButton_Click` .

- <xref:System.Net.Http.HttpClient.GetAsync%2A> `GetAsync` Bir bağımsız değişkeni kabul ettiğinden Web sitelerini indirmek için yöntemini kullanın <xref:System.Threading.CancellationToken> .

- `DisplayResults`İndirilen her Web sitesinin sonuçlarını göstermek için çağrılmadan önce, `ct` geçerli işlemin iptal edildiğini doğrulamak için denetleyin.

Aşağıdaki kod, yıldız işaretiyle işaretlenen bu değişiklikleri gösterir.

```csharp
// *** Provide a parameter for the CancellationToken from StartButton_Click.
async Task AccessTheWebAsync(CancellationToken ct)
{
    // Declare an HttpClient object.
    HttpClient client = new HttpClient();

    // Make a list of web addresses.
    List<string> urlList = SetUpURLList();

    var total = 0;
    var position = 0;

    foreach (var url in urlList)
    {
        // *** Use the HttpClient.GetAsync method because it accepts a
        // cancellation token.
        HttpResponseMessage response = await client.GetAsync(url, ct);

        // *** Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        // *** Check for cancellations before displaying information about the
        // latest site.
        ct.ThrowIfCancellationRequested();

        DisplayResults(url, urlContents, ++position);

        // Update the total.
        total += urlContents.Length;
    }

    // Display the total count for all of the websites.
    ResultsTextBox.Text +=
        $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
}
```

Bu uygulama çalışırken **Başlat** düğmesini birkaç kez seçerseniz, aşağıdaki çıktıya benzeyen sonuçlar üretmelidir.

```output
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               122505
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
Download canceled.

1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
Download canceled.

1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

Kısmi listeleri ortadan kaldırmak için, `StartButton_Click` kullanıcının işlemi her yeniden başlatışında metin kutusunu temizlemek için içindeki ilk kod satırının açıklamasını kaldırın.

### <a name="run-multiple-operations-and-queue-the-output"></a><a name="BKMK_RunMultipleOperations"></a>Birden çok Işlemi çalıştırma ve çıktıyı sıraya alma

Bu üçüncü örnek, Kullanıcı **Başlat** düğmesini her seçtiğinde uygulamanın başka bir zaman uyumsuz işlem başlatması ve tüm işlemlerin tamamlamada çalışması için en karmaşıktır. Tüm istenen işlemler, listeden zaman uyumsuz olarak Web sitelerini indirir, ancak işlemlerden alınan çıkış sıralı olarak sunulur. Diğer bir deyişle, gerçek indirme etkinliği araya eklemeli, bu da bir yandan [yeniden](#BKMK_RecognizingReentrancy) giriş, ancak her grup için sonuçların listesi ayrı olarak sunulur.

İşlemler, <xref:System.Threading.Tasks.Task> `pendingWork` görüntüleme işlemi için bir ağ geçidi denetleyicisi görevi gören küresel bir şekilde paylaşır.

Bu senaryoyu ayarlamak için, [Örnek uygulamayı gözden geçirmek ve çalıştırmak](#BKMD_SettingUpTheExample)için belirtilen temel kodda aşağıdaki değişiklikleri yapın. Tamamlanmış uygulamayı [zaman uyumsuz örneklerden de indirebilirsiniz: .net masaüstü uygulamalarında yeniden giriş](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Projenin adı örneği indirip queueresults.

Aşağıdaki çıktıda, Kullanıcı **Başlat** düğmesini yalnızca bir kez seçerse sonuç gösterilmektedir. Harf etiketi,, sonucun **Başlangıç** düğmesinin seçildiği ilk sefer olduğunu gösterir. Sayılar, indirme hedefleri listesindeki URL 'lerin sırasını gösterir.

```output
#Starting group A.
#Task assigned for group A.

A-1. msdn.microsoft.com/library/hh191443.aspx                87389
A-2. msdn.microsoft.com/library/aa578028.aspx               209858
A-3. msdn.microsoft.com/library/jj155761.aspx                30870
A-4. msdn.microsoft.com/library/hh290140.aspx               119027
A-5. msdn.microsoft.com/library/hh524395.aspx                71260
A-6. msdn.microsoft.com/library/ms404677.aspx               199186
A-7. msdn.microsoft.com                                            53266
A-8. msdn.microsoft.com/library/ff730837.aspx               148020

TOTAL bytes returned:  918876

#Group A is complete.
```

Kullanıcı **Başlat** düğmesini üç kez seçerse, uygulama aşağıdaki satırlara benzer bir çıktı üretir. Numara işareti (#) ile başlayan bilgi satırları, uygulamanın ilerlemesini izler.

```output
#Starting group A.
#Task assigned for group A.

A-1. msdn.microsoft.com/library/hh191443.aspx                87389
A-2. msdn.microsoft.com/library/aa578028.aspx               207089
A-3. msdn.microsoft.com/library/jj155761.aspx                30870
A-4. msdn.microsoft.com/library/hh290140.aspx               119027
A-5. msdn.microsoft.com/library/hh524395.aspx                71259
A-6. msdn.microsoft.com/library/ms404677.aspx               199185

#Starting group B.
#Task assigned for group B.

A-7. msdn.microsoft.com                                            53266

#Starting group C.
#Task assigned for group C.

A-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  916095

B-1. msdn.microsoft.com/library/hh191443.aspx                87389
B-2. msdn.microsoft.com/library/aa578028.aspx               207089
B-3. msdn.microsoft.com/library/jj155761.aspx                30870
B-4. msdn.microsoft.com/library/hh290140.aspx               119027
B-5. msdn.microsoft.com/library/hh524395.aspx                71260
B-6. msdn.microsoft.com/library/ms404677.aspx               199186

#Group A is complete.

B-7. msdn.microsoft.com                                            53266
B-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  916097

C-1. msdn.microsoft.com/library/hh191443.aspx                87389
C-2. msdn.microsoft.com/library/aa578028.aspx               207089

#Group B is complete.

C-3. msdn.microsoft.com/library/jj155761.aspx                30870
C-4. msdn.microsoft.com/library/hh290140.aspx               119027
C-5. msdn.microsoft.com/library/hh524395.aspx                72765
C-6. msdn.microsoft.com/library/ms404677.aspx               199186
C-7. msdn.microsoft.com                                            56190
C-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  920526

#Group C is complete.
```

Grup A tamamlanmadan önce B ve C grupları başlar, ancak her grubun çıktısı ayrı olarak görünür. Önce Grup A 'nın tüm çıktıları, ardından Grup B için tüm çıktılar ve sonra Grup C için tüm çıktılar görüntülenir. Uygulama her zaman grupları sırayla görüntüler ve her grup için her zaman tek tek Web siteleri hakkındaki bilgileri URL 'Ler listesinde görünecek şekilde görüntüler.

Ancak, indirmelerin gerçekten gerçekleştiği sırayı tahmin edemezseniz. Birden çok grup başlatıldıktan sonra, oluşturdukları yükleme görevlerinin hepsi etkindir. -1 ' in B-1 ' den önce indirileceğini varsaymazsınız ve-1 ' in-2 ' den önce indirildiğini varsaymazsınız.

#### <a name="global-definitions"></a>Genel tanımlar

Örnek kod, tüm metotlardan görülebilen aşağıdaki iki genel bildirimi içerir.

```csharp
public partial class MainWindow : Window  // Class MainPage in Windows Store app.
{
    // ***Declare the following variables where all methods can access them.
    private Task pendingWork = null;
    private char group = (char)('A' - 1);
```

`Task`Değişkeni, `pendingWork` görüntüleme sürecini fazla görür ve herhangi bir grubun başka bir grubun görüntüleme işlemini kesintiye uğramasını önler. Karakter değişkeni, `group` sonuçların beklenen sırada göründüğünü doğrulamak için farklı gruplardan çıktıyı Etiketler.

#### <a name="the-click-event-handler"></a>Click olay Işleyicisi

Olay işleyicisi, `StartButton_Click` Kullanıcı **Başlat** düğmesini her seçtiğinde grup harfini artırır. Ardından işleyici, `AccessTheWebAsync` indirme işlemini çalıştırmak için çağırır.

```csharp
private async void StartButton_Click(object sender, RoutedEventArgs e)
{
    // ***Verify that each group's results are displayed together, and that
    // the groups display in order, by marking each group with a letter.
    group = (char)(group + 1);
    ResultsTextBox.Text += $"\r\n\r\n#Starting group {group}.";

    try
    {
        // *** Pass the group value to AccessTheWebAsync.
        char finishedGroup = await AccessTheWebAsync(group);

        // The following line verifies a successful return from the download and
        // display procedures.
        ResultsTextBox.Text += $"\r\n\r\n#Group {finishedGroup} is complete.\r\n";
    }
    catch (Exception)
    {
        ResultsTextBox.Text += "\r\nDownloads failed.";
    }
}
```

#### <a name="the-accessthewebasync-method"></a>AccessTheWebAsync yöntemi

Bu örnek `AccessTheWebAsync` iki yönteme böler. İlk yöntem, `AccessTheWebAsync` bir grup için tüm indirme görevlerini başlatır ve `pendingWork` görüntüleme işlemini denetlemek için ayarlar. Yöntemi, bir dil ile tümleşik sorgu (LINQ sorgusu) kullanır ve <xref:System.Linq.Enumerable.ToArray%2A> tüm indirme görevlerini aynı anda başlatır.

`AccessTheWebAsync`ardından `FinishOneGroupAsync` , her indirmenin tamamlanmasını beklemek için çağırır ve uzunluğunu görüntüler.

`FinishOneGroupAsync`içinde öğesine atanan bir görev döndürür `pendingWork` `AccessTheWebAsync` . Bu değer, görev tamamlanmadan önce başka bir işlem kesintiye uğramasını önler.

```csharp
private async Task<char> AccessTheWebAsync(char grp)
{
    HttpClient client = new HttpClient();

    // Make a list of the web addresses to download.
    List<string> urlList = SetUpURLList();

    // ***Kick off the downloads. The application of ToArray activates all the download tasks.
    Task<byte[]>[] getContentTasks = urlList.Select(url => client.GetByteArrayAsync(url)).ToArray();

    // ***Call the method that awaits the downloads and displays the results.
    // Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp);

    ResultsTextBox.Text += $"\r\n#Task assigned for group {grp}. Download tasks are active.\r\n";

    // ***This task is complete when a group has finished downloading and displaying.
    await pendingWork;

    // You can do other work here or just return.
    return grp;
}
```

#### <a name="the-finishonegroupasync-method"></a>FinishOneGroupAsync yöntemi

Bu yöntem bir gruptaki indirme görevleri boyunca geçiş yapar, her birini bekliyor, indirilen Web sitesinin uzunluğunu görüntülüyor ve uzunluğu toplamına ekliyor.

' Deki ilk ifade `FinishOneGroupAsync` , `pendingWork` yöntemi girerken, zaten görüntüleme işleminde olan veya zaten bekleyen bir işlemi etkilemediğinden emin olmak için kullanır. Bu tür bir işlem devam ediyorsa, giriş işleminin tamamlanmasını beklemesi gerekir.

```csharp
private async Task FinishOneGroupAsync(List<string> urls, Task<byte[]>[] contentTasks, char grp)
{
    // ***Wait for the previous group to finish displaying results.
    if (pendingWork != null) await pendingWork;

    int total = 0;

    // contentTasks is the array of Tasks that was created in AccessTheWebAsync.
    for (int i = 0; i < contentTasks.Length; i++)
    {
        // Await the download of a particular URL, and then display the URL and
        // its length.
        byte[] content = await contentTasks[i];
        DisplayResults(urls[i], content, i, grp);
        total += content.Length;
    }

    // Display the total count for all of the websites.
    ResultsTextBox.Text +=
        $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
}
```

#### <a name="points-of-interest"></a>Ilgi çekici noktaları

Çıktıda diyez işareti (#) ile başlayan bilgi satırları bu örneğin nasıl çalıştığını açıklığa kavuşturacak.

Çıktıda aşağıdaki desenler gösterilmektedir.

- Bir grup, önceki bir grup çıktısını görüntülerken başlatılabilir, ancak önceki grubun çıktısının görüntülenmediği kesintiye uğramaz.

    ```output
    #Starting group A.
    #Task assigned for group A. Download tasks are active.

    A-1. msdn.microsoft.com/library/hh191443.aspx                87389
    A-2. msdn.microsoft.com/library/aa578028.aspx               207089
    A-3. msdn.microsoft.com/library/jj155761.aspx                30870
    A-4. msdn.microsoft.com/library/hh290140.aspx               119037
    A-5. msdn.microsoft.com/library/hh524395.aspx                71260

    #Starting group B.
    #Task assigned for group B. Download tasks are active.

    A-6. msdn.microsoft.com/library/ms404677.aspx               199186
    A-7. msdn.microsoft.com                                            53078
    A-8. msdn.microsoft.com/library/ff730837.aspx               148010

    TOTAL bytes returned:  915919

    B-1. msdn.microsoft.com/library/hh191443.aspx                87388
    B-2. msdn.microsoft.com/library/aa578028.aspx               207089
    B-3. msdn.microsoft.com/library/jj155761.aspx                30870

    #Group A is complete.

    B-4. msdn.microsoft.com/library/hh290140.aspx               119027
    B-5. msdn.microsoft.com/library/hh524395.aspx                71260
    B-6. msdn.microsoft.com/library/ms404677.aspx               199186
    B-7. msdn.microsoft.com                                            53078
    B-8. msdn.microsoft.com/library/ff730837.aspx               148010

    TOTAL bytes returned:  915908
    ```

- `pendingWork`Bu görev, `FinishOneGroupAsync` yalnızca Ilk başlatılan A grubuna yönelik olarak null olur. A grubu, ulaştığı zaman bir await ifadesini henüz tamamlamamıştı `FinishOneGroupAsync` . Bu nedenle, denetim öğesine döndürülmemiştir `AccessTheWebAsync` ve ilk atama `pendingWork` gerçekleşmemiştir.

- Aşağıdaki iki satır, her zaman çıktıda birlikte görüntülenir. Bu kod, içindeki bir grubun işlemini başlatma `StartButton_Click` ve grup için bir görev atama arasında hiçbir şekilde kesintiye uğramaz `pendingWork` .

    ```output
    #Starting group B.
    #Task assigned for group B. Download tasks are active.
    ```

    Bir grup girdikten sonra işlem, `StartButton_Click` işlem girene kadar await ifadesi tamamlanmaz `FinishOneGroupAsync` . Bu nedenle, başka hiçbir işlem bu kod segmenti sırasında denetim elde edebilir.

## <a name="reviewing-and-running-the-example-app"></a><a name="BKMD_SettingUpTheExample"></a>Örnek uygulamayı inceleme ve çalıştırma

Örnek uygulamayı daha iyi anlamak için indirebilir, kendiniz derleyebilir veya uygulamayı uygulamadan bu konunun sonundaki kodu inceleyebilirsiniz.

> [!NOTE]
> Örneği bir Windows Presentation Foundation (WPF) masaüstü uygulaması olarak çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.

### <a name="downloading-the-app"></a><a name="BKMK_DownloadingTheApp"></a>Uygulama indiriliyor

1. [Zaman uyumsuz örneklerden sıkıştırılmış dosyayı indirin: .net masaüstü uygulamalarında yeniden giriş](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).

2. İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.

3. Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin.

4. Sıkıştırması açılmış örnek kodun bulunduğu klasöre gidin ve çözüm (. sln) dosyasını açın.

5. **Çözüm Gezgini**' de, çalıştırmak istediğiniz projenin kısayol menüsünü açın ve ardından **StartupProject olarak ayarla**' yı seçin.

6. Projeyi derlemek ve çalıştırmak için CTRL + F5 tuşlarını seçin.

### <a name="building-the-app"></a><a name="BKMK_BuildingTheApp"></a>Uygulamayı oluşturma

Aşağıdaki bölümde, örneği WPF uygulaması olarak derlemek için kod sağlanmaktadır.

##### <a name="to-build-a-wpf-app"></a>WPF uygulaması derlemek için

1. Visual Studio’yu çalıştırın.

2. Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.

     **Yeni proje** iletişim kutusu açılır.

3. **Yüklü şablonlar** bölmesinde, **Visual C#**' ı genişletin ve ardından **Windows**' u genişletin.

4. Proje türleri listesinde **WPF uygulaması**' nı seçin.

5. Projeyi adlandırın `WebsiteDownloadWPF` , 4,6 veya üzeri bir sürüm .NET Framework seçin ve **Tamam** düğmesine tıklayın.

     Yeni proje **Çözüm Gezgini**görüntülenir.

6. Visual Studio Code düzenleyicisinde **MainWindow. xaml** sekmesini seçin.

     Sekme görünür değilse, **Çözüm Gezgini**' de MainWindow. xaml için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

7. MainWindow. xaml ' nin **xaml** görünümünde, kodu aşağıdaki kodla değiştirin.

    ```csharp
    <Window x:Class="WebsiteDownloadWPF.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WebsiteDownloadWPF"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Width="517" Height="360">
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="-1,0,0,0" VerticalAlignment="Top" Click="StartButton_Click" Height="53" Background="#FFA89B9B" FontSize="36" Width="518"  />
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" Margin="-1,53,0,-36" TextWrapping="Wrap" VerticalAlignment="Top" Height="343" FontSize="10" ScrollViewer.VerticalScrollBarVisibility="Visible" Width="518" FontFamily="Lucida Console" />
        </Grid>
    </Window>
    ```

     Bir metin kutusu ve bir düğme içeren basit bir pencere, MainWindow. xaml **Tasarım** görünümünde görünür.

8. **Çözüm Gezgini**, **Başvurular** ' a sağ tıklayın ve **Başvuru Ekle**' yi seçin.

     Henüz seçilmemişse, için bir başvuru ekleyin <xref:System.Net.Http> .

9. **Çözüm Gezgini**' de, MainWindow.xaml.cs için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

10. MainWindow.xaml.cs ' de, kodu aşağıdaki kodla değiştirin.

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
    using System.Threading;

    namespace WebsiteDownloadWPF
    {
        public partial class MainWindow : Window
        {
            public MainWindow()
            {
                System.Net.ServicePointManager.SecurityProtocol |= System.Net.SecurityProtocolType.Tls12;
                InitializeComponent();
            }

            private async void StartButton_Click(object sender, RoutedEventArgs e)
            {
                // This line is commented out to make the results clearer in the output.
                //ResultsTextBox.Text = "";

                try
                {
                    await AccessTheWebAsync();
                }
                catch (Exception)
                {
                    ResultsTextBox.Text += "\r\nDownloads failed.";
                }
            }

            private async Task AccessTheWebAsync()
            {
                // Declare an HttpClient object.
                HttpClient client = new HttpClient();

                // Make a list of web addresses.
                List<string> urlList = SetUpURLList();

                var total = 0;
                var position = 0;

                foreach (var url in urlList)
                {
                    // GetByteArrayAsync returns a task. At completion, the task
                    // produces a byte array.
                    byte[] urlContents = await client.GetByteArrayAsync(url);

                    DisplayResults(url, urlContents, ++position);

                    // Update the total.
                    total += urlContents.Length;
                }

                // Display the total count for all of the websites.
                ResultsTextBox.Text +=
                    $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
            }

            private List<string> SetUpURLList()
            {
                List<string> urls = new List<string>
                {
                    "https://msdn.microsoft.com/library/hh191443.aspx",
                    "https://msdn.microsoft.com/library/aa578028.aspx",
                    "https://msdn.microsoft.com/library/jj155761.aspx",
                    "https://msdn.microsoft.com/library/hh290140.aspx",
                    "https://msdn.microsoft.com/library/hh524395.aspx",
                    "https://msdn.microsoft.com/library/ms404677.aspx",
                    "https://msdn.microsoft.com",
                    "https://msdn.microsoft.com/library/ff730837.aspx"
                };
                return urls;
            }

            private void DisplayResults(string url, byte[] content, int pos)
            {
                // Display the length of each website. The string format is designed
                // to be used with a monospaced font, such as Lucida Console or
                // Global Monospace.

                // Strip off the "https://".
                var displayURL = url.Replace("https://", "");
                // Display position in the URL list, the URL, and the number of bytes.
                ResultsTextBox.Text += $"\n{pos}. {displayURL,-58} {content.Length,8}";
            }
        }
    }
    ```

11. Programı çalıştırmak için CTRL + F5 tuşlarını seçin ve sonra **Başlat** düğmesini birkaç kez seçin.

12. [Başlat düğmesini devre dışı bırak](#BKMK_DisableTheStartButton)' dan değişiklikleri yapın, [işlemi Iptal edin ve yeniden başlatın](#BKMK_CancelAndRestart)ya da [birden çok işlem çalıştırın ve çıktıyı kuyruğa](#BKMK_RunMultipleOperations) alarak yeniden giriş işlemini idare edin.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Async ve await kullanarak Web 'e erişme (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async ve await ile zaman uyumsuz programlama (C#)](./index.md)
