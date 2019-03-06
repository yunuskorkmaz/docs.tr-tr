---
title: (C#) zaman uyumsuz uygulamalarda yeniden girişi işleme
ms.date: 07/20/2015
ms.assetid: 47c5075e-c448-45ce-9155-ed4e7e98c677
ms.openlocfilehash: 4f5435dd482a20e1aa5a6e0b93d6222025b05518
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359269"
---
# <a name="handling-reentrancy-in-async-apps-c"></a>(C#) zaman uyumsuz uygulamalarda yeniden girişi işleme
Zaman uyumsuz kod uygulamanıza eklediğinizde, göz önünde bulundurun ve tamamlanmadan önce zaman uyumsuz bir işlem engellemelisiniz yeniden giriş muhtemelen önlemek gerekir. Olasılıklarını tanımlamaz ve yönetmezseniz, beklenmedik sonuçlara neden olabilir.  
  
 **Bu konudaki**  
  
-   [Yeniden giriş tanıma](#BKMK_RecognizingReentrancy)  
  
-   [Yeniden girişi işleme](#BKMK_HandlingReentrancy)  
  
    -   [Başlat düğmesini devre dışı bırak](#BKMK_DisableTheStartButton)  
  
    -   [İptal edip işlemi yeniden başlatın](#BKMK_CancelAndRestart)  
  
    -   [Birden çok işlemi çalıştırın ve çıktıyı sıraya alın](#BKMK_RunMultipleOperations)  
  
-   [Gözden geçirme ve örnek uygulamayı çalıştırma](#BKMD_SettingUpTheExample)  
  
> [!NOTE]
>  Yeni bilgisayarınızda yüklü veya örneği çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.  
  
## <a name="BKMK_RecognizingReentrancy"></a> Yeniden giriş tanıma  
 Bu konudaki örnekte, kullanıcıların seçim bir **Başlat** Web sitesi dizilerini indiren ve indirilen bayt toplam sayısını hesaplayan zaman uyumsuz bir uygulamayı başlatmak için düğme. Zaman uyumlu bir sürümünü örneğin aynı şekilde bakılmaksızın İlk seferden sonra UI iş parçacığı bu olayları Uygulama çalışmayı sonlandırıncaya kadar yok sayar. çünkü, kaç kez bir kullanıcı düğmeyi yanıtlamayı ister. Zaman uyumsuz bir uygulamada, ancak kullanıcı Arabirimi iş parçacığı yanıtlamaya devam eder ve zaman uyumsuz işlem tamamlanmadan önce yeniden.  
  
 Aşağıdaki örnek, beklenen gösterir. Kullanıcı seçtiğinde çıkış **Başlat** düğmesini yalnızca bir defa. İndirilen Web sitelerinin bir listesiyle boyutunu bayt cinsinden her site görünür. Toplam bayt sayısı sonda görünür.  
  
```  
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
  
 Ancak kullanıcı düğmeyi birden fazla kez seçerse olay işleyicisi tekrarlanarak çağrılır ve indirme işlemini, her zaman reentered. Sonuç olarak, birtakım zaman uyumsuz işlemler aynı anda çalışan, çıktı sonuçları karışır ve toplam bayt sayısı karmaşıktır.  
  
```  
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
  
 Bu konunun sonuna kadar giderek bu çıkışı üreten kodu gözden geçirebilirsiniz. Çözümü yerel bilgisayarınıza indirip WebsiteDownload projeyi daha sonra çalışan veya kendi projenizi oluşturmak için bu konunun sonunda kodu kullanarak kodla denemeler yapabilirsiniz. Daha fazla bilgi ve yönergeler için bkz. [inceleme ve örnek uygulamayı çalıştırma](#BKMD_SettingUpTheExample).  
  
## <a name="BKMK_HandlingReentrancy"></a> Yeniden girişi işleme  
 Yolu, uygulamanızı yapmak için istediğinize bağlı olarak çeşitli yollardan yeniden işleyebilirsiniz. Bu konu aşağıdaki örnekleri sunar:  
  
-   [Başlat düğmesini devre dışı bırak](#BKMK_DisableTheStartButton)  
  
     Devre dışı **Başlat** böylece kullanıcı, kesme işlemi devam ederken düğmesi.  
  
-   [İptal edip işlemi yeniden başlatın](#BKMK_CancelAndRestart)  
  
     Kullanıcı seçtiğinde devam eden tüm işlemleri iptal **Başlat** yeniden düğmesini ve ardından let en son İstenen işleme devam edin.  
  
-   [Birden çok işlemi çalıştırın ve çıktıyı sıraya alın](#BKMK_RunMultipleOperations)  
  
     Tüm istenen işlemlerin zaman uyumsuz olarak çalışır, ancak çıktı görünümünü koordine edecek her işlemin sonuçları birlikte ve sıralı görünür izin verir.  
  
### <a name="BKMK_DisableTheStartButton"></a> Başlat düğmesini devre dışı bırak  
 Engelleyebilirsiniz **Başlat** en üstündeki düğmesini devre dışı bırakarak işlem çalışırken `StartButton_Click` olay işleyicisi. İçinden düğmeyi ardından etkinleştirebileceğiniz bir `finally` böylece kullanıcılar uygulamayı yeniden çalıştırabilir işlem tamamlandığında engelleyin.  
  
 Bu senaryoyu ayarlamak için bağlantısında verilen temel kodda aşağıdaki değişiklikleri yapın [inceleme ve örnek uygulamayı çalıştırma](#BKMD_SettingUpTheExample). Bitmiş uygulamayı da indirebilirsiniz [zaman uyumsuz örnekleri: .NET Masaüstü uygulamalarda yeniden girişi](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Proje adı disablestartbutton.  
  
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
  
 Değişikliklerin bir sonucu olarak düğme yanıt vermiyor ancak `AccessTheWebAsync` işlem reentered şekilde Web siteleri yüklüyor.  
  
### <a name="BKMK_CancelAndRestart"></a> İptal edip işlemi yeniden başlatın  
 Devre dışı bırakmak yerine **Başlat** düğmesini kullanabilirsiniz düğmeyi etkin tutabilirsiniz ancak, kullanıcı yeniden bu düğmeyi seçerse, zaten çalışıyor ve en son başlatılan işlemin devam izin işlemi iptal edin.  
  
 İptal işlemleri hakkında daha fazla bilgi için bkz. [Fine-Tuning Async uygulamanızda (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md).  
  
 Bu senaryoyu ayarlamak için bağlantısında verilen temel kodda aşağıdaki değişiklikleri yapın [inceleme ve örnek uygulamayı çalıştırma](#BKMD_SettingUpTheExample). Bitmiş uygulamayı da indirebilirsiniz [zaman uyumsuz örnekleri: .NET Masaüstü uygulamalarda yeniden girişi](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Projenin adı CancelAndRestart'tır.  
  
1.  Bildirme bir <xref:System.Threading.CancellationTokenSource> değişken `cts`, tüm yöntemler için kapsam dahilinde olan.  
  
    ```csharp  
    public partial class MainWindow : Window   // Or class MainPage  
    {  
        // *** Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
    ```  
  
2.  İçinde `StartButton_Click`, bir işlemin zaten çalışıp çalışmadığını belirleyin. Varsa değerini `cts` olan boş, hiçbir işlem zaten etkin. Değer null değilse, zaten çalışan işlemi iptal edildi.  
  
    ```csharp  
    // *** If a download process is already underway, cancel it.  
    if (cts != null)  
    {  
        cts.Cancel();  
    }  
    ```  
  
3.  Ayarlama `cts` geçerli işlemi temsil eden farklı bir değer.  
  
    ```csharp  
    // *** Now set cts to a new value that you can use to cancel the current process  
    // if the button is chosen again.  
    CancellationTokenSource newCTS = new CancellationTokenSource();  
    cts = newCTS;  
    ```  
  
4.  Sonunda `StartButton_Click`, geçerli işlem tamamlanır, bu nedenle ayarlayın `cts` null geri dönün.  
  
    ```csharp  
    // *** When the process is complete, signal that another process can begin.  
    if (cts == newCTS)  
        cts = null;  
    ```  
  
 Aşağıdaki kod tüm değişiklikleri gösterir `StartButton_Click`. Eklentiler yıldız işareti ile işaretlenir.  
  
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
  
 İçinde `AccessTheWebAsync`, aşağıdaki değişiklikleri yapın.  
  
-   Öğesinden iptal belirtecini kabul etmek için bir parametre ekleyin `StartButton_Click`.  
  
-   Kullanım <xref:System.Net.Http.HttpClient.GetAsync%2A> ettiğinden Web sitelerini indirmek için yöntemi `GetAsync` kabul eden bir <xref:System.Threading.CancellationToken> bağımsız değişken.  
  
-   Çağırmadan önce `DisplayResults` her indirilebilir Web sitesi için sonuçları görüntülemek için kontrol `ct` geçerli işlemi iptal edildiğini doğrulamak için.  
  
 Aşağıdaki kod, yıldız ile işaretlenmiş bu değişiklikleri gösterir.  
  
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
  
 Seçerseniz **Başlat** düğmesine birkaç kez bu uygulama çalışırken aşağıdaki çıktıya benzer sonuçlar üretmelidir.  
  
```  
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
  
 Kısmi listelerini ortadan kaldırmak için ilk kod satırı açıklamadan çıkarın `StartButton_Click` kullanıcı her zaman metin kutusunu temizlemek için işlemi yeniden başlatır.  
  
### <a name="BKMK_RunMultipleOperations"></a> Birden çok işlemi çalıştırın ve çıktıyı sıraya alın  
 Başka bir zaman uyumsuz işlemi kullanıcı her zaman uygulama başlatır, bu üçüncü örnek en karmaşık örnektir **Başlat** düğmesi ve tüm işlemler tamamlanmak üzere çalıştığı. Listeden Web siteleri tüm istenen işlemler zaman uyumsuz olarak yükleyin, ancak çıkış işlemlerden çıktılar ardışık olarak sunulur. Diğer bir deyişle, gerçek indirme etkinliği, deki çıkışın gösterdiği gibi aralanmıştır [yeniden giriş tanıma](#BKMK_RecognizingReentrancy) gösterir, ancak her grup için sonuçların listesi ayrı ayrı sunulur.  
  
 İşlemleri genel paylaşım <xref:System.Threading.Tasks.Task>, `pendingWork`, görüntüleme işlemi için bir ağ geçidi olarak görev gören.  

 Bu senaryoyu ayarlamak için bağlantısında verilen temel kodda aşağıdaki değişiklikleri yapın [inceleme ve örnek uygulamayı çalıştırma](#BKMD_SettingUpTheExample). Bitmiş uygulamayı da indirebilirsiniz [zaman uyumsuz örnekleri: .NET Masaüstü uygulamalarda yeniden girişi](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Proje QueueResults adıdır.  
   
 Aşağıdaki çıktı, kullanıcı seçtiğinde görülecek sonucu gösterir **Başlat** düğmesini yalnızca bir defa. Harf etiketi A, sonucun ilk kez gösterir **Başlat** düğmesi seçilir. Sayılar, yükleme hedefleri listesinde URL'lerin sırasını gösterir.  
  
```  
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
  
 Kullanıcı seçerse **Başlat** düğmesine üç kez, uygulama aşağıdaki satırlara benzer bir çıktı üretir. Bir kare ile başlayan bilgi satırları uygulamanın ilerleyişini (#) izleme oturum açın.  
  
```  
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
  
 Grup A tamamlanmadan, ancak her grubun çıktısı ayrı görünür önce Grup B ve C başlatın. Grup A için çıktıların tamamı ardından Grup B için çıktıların tamamı ve sonra tüm çıkış grubu c için ilk olarak, görünür Uygulama her zaman sırayla grupları görüntüler ve her bir grup için her zaman URL'leri URL'lerin listesinde görüntülenen sırayla tek tek Web siteleri hakkındaki bilgileri görüntüler.  
  
 Ancak, hangi indirmelerin gerçekte olduğu sırayı tahmin edemezsiniz. Birden çok grup başlattıktan sonra oluşturdukları indirme görevlerinin tamamı etkindir. Bu A-1 varsayamazsınız önce B-1 indirilir ve bu A-1 varsayamazsınız A-2 önce yüklenir.  
  
#### <a name="global-definitions"></a>Genel tanımlar  
 Örnek kod, tüm yöntemlerden görünen aşağıdaki iki genel bildirimi içerir.  
  
```csharp  
public partial class MainWindow : Window  // Class MainPage in Windows Store app.  
{  
    // ***Declare the following variables where all methods can access them.   
    private Task pendingWork = null;     
    private char group = (char)('A' - 1);  
```  
  
 `Task` Değişken `pendingWork`, görüntüleme işlemini kesmesini ve herhangi bir grubu başka bir grubun görünen çalışmasını önler. Karakter değişkeni `group`, sonuçların beklenen sırada göründüğünü doğrulamak üzere farklı gruplardan çıkış etiketler.  
  
#### <a name="the-click-event-handler"></a>Tıklama olayı işleyicisi  
 Olay işleyicisi `StartButton_Click`, her zaman kullanıcı Grup harfini artırır **Başlat** düğmesi. Ardından işleyici çağrıları `AccessTheWebAsync` indirme işlemini çalıştırmak için.  
  
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
 Bu örnekte böler `AccessTheWebAsync` öğesini iki yöntem. İlk yöntem `AccessTheWebAsync`, bir grup için tüm indirme görevlerini başlatır ve ayarlar `pendingWork` görüntüleme işlemini denetlemek için. Yöntemi, bir dil ile tümleşik sorgu (LINQ sorgusu) kullanır ve <xref:System.Linq.Enumerable.ToArray%2A> tüm indirme görevlerini aynı anda başlatmak için.  
  
 `AccessTheWebAsync` Daha sonra çağırır `FinishOneGroupAsync` her İndirmenin tamamlanmasını beklemek ve uzunluğunu görüntülemek için.  
  
 `FinishOneGroupAsync` atanmış bir görev döndürür `pendingWork` içinde `AccessTheWebAsync`. Değeri, görev önce başka bir işlem tarafından kesintiye engellediğini tamamlanmıştır.  
  
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
 Bu yöntemi izleyerek her birini bekler, karşıdan yüklenen Web sitesi uzunluğunu görüntülemek ve uzunluğu toplama ekleme bir gruptaki indirme görevlerini aracılığıyla geçiş yapar.  
  
 İlk deyimde `FinishOneGroupAsync` kullanan `pendingWork` yöntemin girilmesinin zaten içinde görüntüleme işlemini veya beklemede bir işlemle çakışmamasını sağlamak için. Bu tür bir işlem sürüyorsa, giriş işlemi kendi sırasını beklemelidir.  
  
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
  
   
#### <a name="points-of-interest"></a>İlgi noktaları  
 Çıktıda pound işareti (#) ile başlayan bilgi satırları bu örneğin nasıl çalıştığını açıklamak.  
  
 Çıktı aşağıdaki desenleri gösterir.  
  
-   Bir grubu, bir önceki Grup çıktıyı görüntülerken, ancak görüntü önceki grubun çıktı görünümü kesintiye başlatılabilir.  
  
    ```  
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
  
-   `pendingWork` Görevi başlangıcında NULL'dur `FinishOneGroupAsync` Grup A için yalnızca ilk başlayan a. Grup A taşınmadığından henüz tamamlanmamış bir await deyimindeki ulaştığında `FinishOneGroupAsync`. Bu nedenle, Denetim öğesine dönmemiştir `AccessTheWebAsync`ve ilk atamaya `pendingWork` oluşmamıştır.  
  
-   Her zaman aşağıdaki iki satır çıktıda birlikte görünür. Kod bir grubun çalışmasını başlatma arasında hiçbir zaman kesintiye `StartButton_Click` ve grubun bir görev atama `pendingWork`.  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     Bir grubu girdikten sonra `StartButton_Click`, işlemi işlemi girinceye kadar await ifadesini tamamlamaz değil `FinishOneGroupAsync`. Bu nedenle, başka bir işlem sırasında kod kesiminin denetimi elde edebilirsiniz.  
  
## <a name="BKMD_SettingUpTheExample"></a> Gözden geçirme ve örnek uygulamayı çalıştırma  
 Örnek uygulamayı daha iyi anlamak için indirin, kendiniz derleyebilir veya uygulamayı gerçekleştirmeden, bu konunun sonunda kodu gözden geçirin.  
  
> [!NOTE]
>  Bir veya daha yeni bilgisayarınızda yüklü örneği Windows Presentation Foundation (WPF) masaüstü uygulaması olarak çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 olmalıdır.  
  
### <a name="BKMK_DownloadingTheApp"></a> Uygulamayı karşıdan yükleme  
  
1.  Sıkıştırılmış dosyayı indirin [zaman uyumsuz örnekleri: .NET Masaüstü uygulamalarda yeniden girişi](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).  
  
2.  İndirdiğiniz dosyanın sıkıştırmasını açın ve sonra Visual Studio'yu başlatın.  
  
3.  Menü çubuğunda, **dosya**, **açık**, **proje/çözüm**.  
  
4.  Sıkıştırması açılmış örnek kodun bulunduğu klasöre gidin ve ardından çözüm (.sln) dosyasını açın.  
  
5.  İçinde **Çözüm Gezgini**, çalıştırın ve ardından istediğiniz projenin kısayol menüsünü **StartUpProject olarak ayarla**.  
  
6.  Oluşturun ve projeyi çalıştırmak için CTRL + F5 tuşlarını seçin.  
  
### <a name="BKMK_BuildingTheApp"></a> Uygulama oluşturma  
 Aşağıdaki bölümde, örnek bir WPF uygulaması olarak oluşturmak için kod sağlar.  
  
##### <a name="to-build-a-wpf-app"></a>Bir WPF uygulaması derlemek için  
  
1.  Visual Studio’yu çalıştırın.  
  
2.  Menü çubuğunda, **dosya**, **yeni**, **proje**.  
  
     **Yeni proje** iletişim kutusu açılır.  
  
3.  İçinde **yüklü şablonlar** bölmesini genişletin **Visual C#** ve ardından **Windows**.  
  
4.  Proje türleri listesinde seçin **WPF uygulaması**.  
  
5.  Projeyi adlandırın `WebsiteDownloadWPF`ve ardından **Tamam** düğmesi.  
  
     Yeni Proje görünür **Çözüm Gezgini**.  
  
6.  Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.  
  
     Sekme görünür değilse, nde MainWindow.xaml için kısayol menüsünü açın **Çözüm Gezgini**ve ardından **kodu görüntüle**.  
  
7.  İçinde **XAML** MainWindow.xaml görüntülemek için kodu aşağıdaki kodla değiştirin.  
  
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
  
     Bir metin kutusu ve bir düğme içeren basit bir pencere **tasarım** MainWindow.xaml görünümü.  
  
8.  İçin bir başvuru eklemeniz <xref:System.Net.Http>.  
  
9. İçinde **Çözüm Gezgini**için MainWindow.xaml.cs kısayol menüsünü açın ve ardından **kodu görüntüle**.  
  
10. MainWindow.xaml.cs kodu aşağıdaki kodla değiştirin.  
  
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
  
11. Programı çalıştırın ve ardından CTRL + F5 tuşlarına basın **Başlat** düğmesine birkaç kez.  
  
12. Değişikliklerini yapın [Başlat düğmesini devre dışı](#BKMK_DisableTheStartButton), [iptal edip işlemi yeniden](#BKMK_CancelAndRestart), veya [birden çok işlemi çalıştırın ve çıktıyı sıraya](#BKMK_RunMultipleOperations) yeniden giriş işlemek için.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
