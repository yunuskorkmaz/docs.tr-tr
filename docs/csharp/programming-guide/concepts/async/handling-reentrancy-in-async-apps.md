---
title: "Zaman uyumsuz uygulamalarda (C#) yeniden girişi işleme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 47c5075e-c448-45ce-9155-ed4e7e98c677
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a917f88d3d6105f836dc67ef8a9ec92efc300d7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="handling-reentrancy-in-async-apps-c"></a>Zaman uyumsuz uygulamalarda (C#) yeniden girişi işleme
Zaman uyumsuz kodu, uygulamanızda eklediğinizde göz önünde bulundurun ve büyük olasılıkla, tamamlanmadan önce zaman uyumsuz bir işlem yeniden girme için başvuruyor yeniden giriş önlemek gerekir. Tanımlamak ve yeniden giriş olasılıklarını işlemek yok, beklenmeyen sonuçlara neden olabilir.  
  
 **Bu konudaki**  
  
-   [Yeniden giriş tanıma](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [Yeniden girişi işleme](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [Başlat düğmesi devre dışı bırak](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [İptal edin ve işlemi yeniden deneyin](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [Birden çok işlemleri çalıştırın ve çıkış sırası](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [Gözden geçirme ve örnek uygulamayı çalıştırma](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
> [!NOTE]
>  Örneği çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınızda yüklü olmalıdır.  
  
##  <a name="BKMK_RecognizingReentrancy"></a>Yeniden giriş tanıma  
 Bu konudaki örnek kullanıcıları seçin bir **Başlat** bir dizi Web siteleri yükler ve yüklenen bayt sayısı toplam hesaplar zaman uyumsuz bir uygulamayı başlatmak için düğmesi. Örnek zaman uyumlu bir sürümü aynı şekilde bakılmaksızın ilk kez sonra kullanıcı Arabirimi iş parçacığı çalışan uygulama sonlanana kadar bu olayları yoksayar çünkü kaç kez bir kullanıcı düğmesini seçer. yanıt. Zaman uyumsuz bir uygulamada ancak, kullanıcı Arabirimi iş parçacığı yanıt vermeye devam eder ve onu tamamlanmadan önce zaman uyumsuz işlemi yeniden girmeniz.  
  
 Aşağıdaki örnek, beklenen gösterir kullanıcı seçtiğinde çıktı **Başlat** yalnızca bir kez düğmesine tıklayın. Her sitenin bayt cinsinden boyutu ile indirilen Web siteleri listesi görüntülenir. Toplam bayt sayısı sonunda görüntülenir.  
  
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
  
 Ancak, kullanıcı düğmesi birden çok kez seçerse, olay işleyici tekrar çağrılır ve indirme işlemini her seferinde reentered. Sonuç olarak, birkaç zaman uyumsuz işlemler aynı anda çalıştırıyorsanız, çıktısı sonuçlara interleaves ve toplam bayt sayısı karmaşıktır.  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/en-us/library/jj155761.aspx                29019  
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
  
 Bu konuda sonuna kaydırarak bu çıkışı üretir kodu gözden geçirebilirsiniz. Yerel bilgisayarınıza çözümü indirme ve WebsiteDownload proje çalıştıran koduyla denemek ya da daha fazla bilgi ve yönergeler için kendi projesi oluşturmak için bu konunun sonunda kodu kullanarak tarafından bkz [ Gözden geçirme ve örnek uygulamayı çalıştıran](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).  
  
##  <a name="BKMK_HandlingReentrancy"></a>Yeniden girişi işleme  
 Yeniden giriş yapmak için uygulamanızın istediğinize bağlı olarak yolları, çeşitli işleyebilir. Bu konuda aşağıdaki örnekler sunulmaktadır:  
  
-   [Başlat düğmesi devre dışı bırak](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     Devre dışı **Başlat** böylece kullanıcı onu kesme işlemi çalışırken düğmesine tıklayın.  
  
-   [İptal edin ve işlemi yeniden deneyin](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     Kullanıcı seçtiğinde hala çalıştıran herhangi bir işlem iptal **Başlat** yeniden düğmesine ve ardından let en yakın zamanda istenen işlem devam edin.  
  
-   [Birden çok işlemleri çalıştırın ve çıkış sırası](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     Tüm işlemlerini zaman uyumsuz olarak çalıştırın, ancak her işlemi sonuçlarından birlikte ve sırada görünmesini sağlayacak şekilde çıkış görüntüsünü koordine etmek için istenen izin verir.  
  
###  <a name="BKMK_DisableTheStartButton"></a>Başlat düğmesi devre dışı bırak  
 Engelleyebilir **Başlat** en üstündeki düğmesi devre dışı bırakarak bir işlem devam ederken düğmesini `StartButton_Click` olay işleyicisi. İçinden düğmesini sonra etkinleştirebileceğiniz bir `finally` engelleme kullanıcıların uygulamayı yeniden çalıştırabilmeniz için işlem sona erdiğinde.  
  
 Aşağıdaki kod yıldız işaretiyle işaretli bu değişiklikleri gösterir. Bu konunun sonunda kod değişiklikleri ekleyebilirsiniz veya tamamlanmış uygulamadan indirebilirsiniz [zaman uyumsuz örnekleri: .NET Masaüstü uygulamalarda yeniden girişi](http://go.microsoft.com/fwlink/?LinkId=266571). Proje adı DisableStartButton ' dir.  
  
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
  
 Değişikliklerin sonucu olarak, düğme yanıt vermiyor sırada `AccessTheWebAsync` işlemi girilmesi edilemez şekilde Web siteleri yüklüyor.  
  
###  <a name="BKMK_CancelAndRestart"></a>İptal edin ve işlemi yeniden deneyin  
 Devre dışı bırakma yerine **Başlat** düğmesini kullanabilirsiniz düğmesi etkin tutmak ancak, kullanıcı bu düğme yeniden seçerse zaten çalışan ve en son başlatılan işlemin devam etmesine izin vermek işlemi iptal edin.  
  
 İptal etme hakkında daha fazla bilgi için bkz: [Fine-Tuning zaman uyumsuz uygulamanız (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md).  
  
 Bu senaryonun kurulumunu yapmak için aşağıdaki sağlanan temel kod değişiklik [gözden geçirme ve örnek uygulamayı çalıştıran](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645). Tamamlanan uygulama aynı zamanda indirebilirsiniz [zaman uyumsuz örnekleri: .NET Masaüstü uygulamalarda yeniden girişi](http://go.microsoft.com/fwlink/?LinkId=266571). Bu proje CancelAndRestart adıdır.  
  
1.  Bildirme bir <xref:System.Threading.CancellationTokenSource> değişkeni, `cts`, kapsamdaki tüm yöntemleri için olmasıdır.  
  
    ```csharp  
    public partial class MainWindow : Window   // Or class MainPage  
    {  
        // *** Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
    ```  
  
2.  İçinde `StartButton_Click`, bir işlemi zaten devam ettiğinden olup olmadığını belirler. Varsa değerini `cts` olan null, hiçbir zaten etkin bir işlemdir. Değer null değilse, zaten çalışıyor işlemi iptal edildi.  
  
    ```csharp  
    // *** If a download process is already underway, cancel it.  
    if (cts != null)  
    {  
        cts.Cancel();  
    }  
    ```  
  
3.  Ayarlama `cts` için geçerli işlem temsil eden farklı bir değer.  
  
    ```csharp  
    // *** Now set cts to a new value that you can use to cancel the current process  
    // if the button is chosen again.  
    CancellationTokenSource newCTS = new CancellationTokenSource();  
    cts = newCTS;  
    ```  
  
4.  Sonunda `StartButton_Click`, geçerli işlemi tamamlandığında, böylece değerini ayarlayın `cts` null dön.  
  
    ```csharp  
    // *** When the process is complete, signal that another process can begin.  
    if (cts == newCTS)  
        cts = null;  
    ```  
  
 Aşağıdaki kod tüm değişiklikleri gösterir `StartButton_Click`. Eklemeleri yıldız işaretiyle işaretlenir.  
  
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
  
-   Gelen iptal belirteci kabul etmek için bir parametre eklemek `StartButton_Click`.  
  
-   Kullanım <xref:System.Net.Http.HttpClient.GetAsync%2A> çünkü Web sitelerini yüklemeye yöntemi `GetAsync` kabul bir <xref:System.Threading.CancellationToken> bağımsız değişkeni.  
  
-   Çağırmadan önce `DisplayResults` indirilen her Web sitesi için sonuçları görüntülemek için kontrol `ct` geçerli işlem iptal edildi değiştirilmediğini doğrulayın.  
  
 Aşağıdaki kod yıldız işaretiyle işaretli bu değişiklikleri gösterir.  
  
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
        string.Format("\r\n\r\nTOTAL bytes returned:  {0}\r\n", total);  
}     
```  
  
 Seçerseniz **Başlat** birkaç kez düğmesini bu uygulama çalışırken, aşağıdaki çıkış benzer sonuçlar üretmesi gerekir.  
  
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
  
 Kısmi listeleri ortadan kaldırmak için ilk kod satırı açıklamadan kaldırmasına `StartButton_Click` kullanıcı işlemi yeniden her zaman metin kutusunun işaretini kaldırın.  
  
###  <a name="BKMK_RunMultipleOperations"></a>Birden çok işlemleri çalıştırın ve çıkış sırası  
 Uygulama başka bir zaman uyumsuz işlemi kullanıcının seçtiği her zaman başlatır, bu üçüncü en karmaşık örneğidir **Başlat** düğmesi ve tüm işlemleri tamamlanıncaya kadar çalıştırın. Listeden Web sitelerini istenen tüm işlemleri zaman uyumsuz olarak indirebilir, ancak işlem çıkışı sıralı olarak sunulur. Diğer bir deyişle, gerçek indirme etkinliği, çıktı olarak araya eklemeli [algılamayı yeniden giriş](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) gösterir, ancak her grup için sonuçlardan sunulur ayrı olarak.  
  
 Operations genel paylaşmak <xref:System.Threading.Tasks.Task>, `pendingWork`, hangi görüntü işlemi için bir ağ geçidi olarak hizmet verir.  
  
 Bu örnek kodda içine değişiklikleri yapıştırılarak çalıştırabilirsiniz [uygulaması oluşturmaya](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), veya'ndaki yönergeleri izleyin [uygulaması indiriliyor](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) örneği indirmek ve ardından QueueResults proje çalıştırın.  
  
 Kullanıcı seçtiğinde sonuç aşağıdaki çıktı gösterir **Başlat** yalnızca bir kez düğmesine tıklayın. Harf etiketi, A, sonuç ilk saati gösterir **Başlat** düğmesi seçilidir. Sayıları URL'leri sırasını indirme hedefler listesinde gösterir.  
  
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
  
 Kullanıcı seçerse **Başlat** düğmesine üç kez, uygulamanın aşağıdaki satırları benzer bir çıktı üretir. Kare ile başlayan bilgi satırları (#) izleme uygulama ilerlemesini oturum açın.  
  
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
  
 Grup B ve C gruba tamamlandı, ancak her grup için çıktı ayrı olarak görünür önce başlatın. Grup a tüm çıktı ardından B grubu için tüm çıkış ve ardından tüm çıktı grubu c için ilk olarak, görünür Uygulama her zaman sıraya göre grupları görüntüler ve her grup için her zaman tek tek Web siteleri hakkında bilgi URL'leri URL'leri listede sırada görüntüler.  
  
 Ancak, indirmeleri gerçekten durum meydana sipariş tahmin edilemez. Birden çok grubu başlatıldıktan sonra oluşturdukları indirme tüm etkin görevlerdir. Bu A-1 varsayın olamaz B-1 önce indirilir ve o A-1 varsayın olamaz A-2 önce yüklenir.  
  
#### <a name="global-definitions"></a>Genel tanımları  
 Örnek kod tüm yöntemleri görünür olan aşağıdaki iki genel bildirimlerini içerir.  
  
```csharp  
public partial class MainWindow : Window  // Class MainPage in Windows Store app.  
{  
    // ***Declare the following variables where all methods can access them.   
    private Task pendingWork = null;     
    private char group = (char)('A' - 1);  
```  
  
 `Task` Değişkeni `pendingWork`, görüntüleme işlemini denetleyen ve herhangi bir grubu başka bir grubun görüntü işlemi önler. Karakter değişkeni `group`, sonuçları beklenen sırada göründüğünü doğrulamak için farklı gruplar çıktısını etiketler.  
  
#### <a name="the-click-event-handler"></a>Click olay işleyicisi  
 Olay işleyicisi `StartButton_Click`, kullanıcının seçtiği her defasında grup harf artırır **Başlat** düğmesi. Ardından işleyicisi çağrılarını `AccessTheWebAsync` indirme işlemi çalıştıramadı.  
  
```csharp  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // ***Verify that each group's results are displayed together, and that  
    // the groups display in order, by marking each group with a letter.  
    group = (char)(group + 1);  
    ResultsTextBox.Text += string.Format("\r\n\r\n#Starting group {0}.", group);  
  
    try  
    {  
        // *** Pass the group value to AccessTheWebAsync.  
        char finishedGroup = await AccessTheWebAsync(group);  
  
        // The following line verifies a successful return from the download and  
        // display procedures.   
        ResultsTextBox.Text += string.Format("\r\n\r\n#Group {0} is complete.\r\n", finishedGroup);  
    }  
    catch (Exception)  
    {  
        ResultsTextBox.Text += "\r\nDownloads failed.";  
    }  
}  
```  
  
#### <a name="the-accessthewebasync-method"></a>AccessTheWebAsync yöntemi  
 Bu örnek böler `AccessTheWebAsync` iki yöntemlerde. İlk yöntem `AccessTheWebAsync`, bir grup için tüm yükleme görevleri başlatır ve ayarlayan `pendingWork` görüntüleme işlemini kontrol eden. Bir dil ile tümleşik sorgu (LINQ sorgusu) yöntemini kullanır ve <xref:System.Linq.Enumerable.ToArray%2A> aynı anda tüm yükleme görevleri başlatılamıyor.  
  
 `AccessTheWebAsync`Daha sonra çağırır `FinishOneGroupAsync` her indirme tamamlanmasını bekler ve uzunluğu görüntülemek için.  
  
 `FinishOneGroupAsync`atanmış bir görev döndürür `pendingWork` içinde `AccessTheWebAsync`. Görev tamamlanmadan önce değer kesinti başka bir işlem tarafından engellediğini.  
  
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
  
    ResultsTextBox.Text += string.Format("\r\n#Task assigned for group {0}. Download tasks are active.\r\n", grp);  
  
    // ***This task is complete when a group has finished downloading and displaying.  
    await pendingWork;  
  
    // You can do other work here or just return.  
    return grp;  
}  
```  
  
#### <a name="the-finishonegroupasync-method"></a>FinishOneGroupAsync yöntemi  
 Bu yöntem, gruptaki her biri bekleniyor, indirilen Web sitesi uzunluğu görüntüleyerek ve toplam uzunluğu ekleyerek, indirme görevleri boyunca geçiş yapar.  
  
 İlk ifade, `FinishOneGroupAsync` kullanan `pendingWork` yöntemi girme zaten görüntü işleminde veya, zaten bekleyen bir işlem ile engellemez emin olmak için. Böyle bir işlem devam ediyor, kendi dönüş girme işlemi beklemeniz gerekir.  
  
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
        string.Format("\r\n\r\nTOTAL bytes returned:  {0}\r\n", total);  
}  
```  
  
 Bu örnek kodda içine değişiklikleri yapıştırılarak çalıştırabilirsiniz [uygulaması oluşturmaya](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), veya'ndaki yönergeleri izleyin [uygulaması indiriliyor](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) örneği indirmek ve ardından QueueResults proje çalıştırın.  
  
#### <a name="points-of-interest"></a>İlgilenilen noktaları  
 Bu örnek nasıl çalıştığını çıktıda pound işareti (#) ile başlayan bilgi satırları açıklayın.  
  
 Çıktı aşağıdaki desenleri gösterir.  
  
-   Bir grup, bir önceki Grup çıktısını görüntüleme, ancak önceki grubun çıkış görüntüsünü kesintiye değil başlatılabilir.  
  
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
  
-   `pendingWork` Görev null başlangıcında `FinishOneGroupAsync` yalnızca Grup A, başlatılan ilk. Grup A kurmadı henüz tamamlanmamış bir bekleme ifade ulaştığında `FinishOneGroupAsync`. Bu nedenle, denetim için döndürülen kurmadı `AccessTheWebAsync`ve ilk atama `pendingWork` oluştu kurmadı.  
  
-   Aşağıdaki iki satırı birlikte her zaman çıkışında görünür. Kod bir grubun işlemi başlatılıyor arasında hiçbir zaman kesintiye `StartButton_Click` ve bir görev için grubunun atama `pendingWork`.  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     Bir grup girdikten sonra `StartButton_Click`, işlemi işlemi girene kadar bir bekleme ifade işlemini tamamlamazsa `FinishOneGroupAsync`. Bu nedenle, başka bir işlem denetimi, kod kesimi sırasında kaynaklara erişebilir.  
  
##  <a name="BKMD_SettingUpTheExample"></a>Gözden geçirme ve örnek uygulamayı çalıştırma  
 Örnek uygulama daha iyi anlamak için indirir, kendiniz oluşturabilir veya uygulama uygulamadan bu konunun sonunda kodu gözden.  
  
> [!NOTE]
>  Örnek bir Windows Presentation Foundation (WPF) masaüstü uygulaması çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 olmalıdır veya daha yeni bilgisayarınızda yüklü.  
  
###  <a name="BKMK_DownloadingTheApp"></a>Uygulama indiriliyor  
  
1.  Sıkıştırılmış dosya indirme [zaman uyumsuz örnekleri: .NET Masaüstü uygulamalarda yeniden girişi](http://go.microsoft.com/fwlink/?LinkId=266571).  
  
2.  İndirdiğiniz dosyanın sıkıştırmasını ve Visual Studio'yu başlatın.  
  
3.  Menü çubuğunda seçin **dosya**, **açık**, **proje/çözüm**.  
  
4.  Açılmış örnek kodu içeren klasöre gidin ve ardından çözüm (.sln) dosyasını açın.  
  
5.  İçinde **Çözüm Gezgini**, çalıştırın ve ardından istediğiniz proje için kısayol menüsünü açın **StartUpProject ayarlamak**.  
  
6.  CTRL + F5 anahtarları projesini derlemeyi ve çalıştırmayı seçin.  
  
###  <a name="BKMK_BuildingTheApp"></a>Uygulama oluşturma  
 Aşağıdaki bölümde, örnek olarak bir WPF uygulaması oluşturmak için kod sağlar.  
  
##### <a name="to-build-a-wpf-app"></a>Bir WPF uygulaması oluşturmak için  
  
1.  Visual Studio'yu başlatın.  
  
2.  Menü çubuğunda seçin **dosya**, **yeni**, **proje**.  
  
     **Yeni proje** iletişim kutusu açılır.  
  
3.  İçinde **yüklü şablonlar** bölmesini genişletin **Visual C#**, genişletin ve ardından **Windows**.  
  
4.  Proje türleri listesinden seçip **WPF uygulaması**.  
  
5.  Proje adı `WebsiteDownloadWPF`ve ardından **Tamam** düğmesi.  
  
     Yeni Proje görünür **Çözüm Gezgini**.  
  
6.  Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.  
  
     Sekme görünür değilse, kısayol menüsünde MainWindow.xaml içinde açık **Çözüm Gezgini**ve ardından **görünümü kodu**.  
  
7.  İçinde **XAML** görüntülemek MainWindow.xaml, kodu aşağıdaki kodla değiştirin.  
  
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
  
     Bir düğmeyi ve bir metin kutusu içeren basit bir pencere görünür **tasarım** MainWindow.xaml görünümü.  
  
8.  İçin bir başvuru ekleyin <xref:System.Net.Http>.  
  
9. İçinde **Çözüm Gezgini**MainWindow.xaml.cs için kısayol menüsünü açın ve ardından **görünümü kodu**.  
  
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
                    string.Format("\r\n\r\nTOTAL bytes returned:  {0}\r\n", total);  
            }  
  
            private List<string> SetUpURLList()  
            {  
                List<string> urls = new List<string>   
                {   
                    "http://msdn.microsoft.com/library/hh191443.aspx",  
                    "http://msdn.microsoft.com/library/aa578028.aspx",  
                    "http://msdn.microsoft.com/library/jj155761.aspx",  
                    "http://msdn.microsoft.com/library/hh290140.aspx",  
                    "http://msdn.microsoft.com/library/hh524395.aspx",  
                    "http://msdn.microsoft.com/library/ms404677.aspx",  
                    "http://msdn.microsoft.com",  
                    "http://msdn.microsoft.com/library/ff730837.aspx"  
                };  
                return urls;  
            }  
  
            private void DisplayResults(string url, byte[] content, int pos)  
            {  
                // Display the length of each website. The string format is designed  
                // to be used with a monospaced font, such as Lucida Console or   
                // Global Monospace.  
  
                // Strip off the "http://".  
                var displayURL = url.Replace("http://", "");  
                // Display position in the URL list, the URL, and the number of bytes.  
                ResultsTextBox.Text += string.Format("\n{0}. {1,-58} {2,8}", pos, displayURL, content.Length);  
            }  
        }  
    }  
    ```  
  
11. Programını çalıştırın ve ardından seçmek için CTRL + F5 anahtarlar **Başlat** birkaç kez düğmesine tıklayın.  
  
12. Öğesinden değişiklikler yapmak [Başlat düğmesi devre dışı](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), [iptal edin ve işlemi yeniden](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), veya [birden çok işlemler çalıştırın ve çıkış sırası](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) yeniden giriş işlemek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: async kullanarak Web'e erişme ve await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
