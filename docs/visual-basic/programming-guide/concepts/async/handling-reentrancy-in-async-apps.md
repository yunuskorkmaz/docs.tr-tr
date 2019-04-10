---
title: (Visual Basic) zaman uyumsuz uygulamalarda yeniden girişi işleme
ms.date: 07/20/2015
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
ms.openlocfilehash: 0913a8b422d8ea3d6b38680a26bac143087dd2c8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324792"
---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a>(Visual Basic) zaman uyumsuz uygulamalarda yeniden girişi işleme
Zaman uyumsuz kod uygulamanıza eklediğinizde, göz önünde bulundurun ve tamamlanmadan önce zaman uyumsuz bir işlem engellemelisiniz yeniden giriş muhtemelen önlemek gerekir. Olasılıklarını tanımlamaz ve yönetmezseniz, beklenmedik sonuçlara neden olabilir.  
  
 **Bu konuda**  
  
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
  
 Bu konunun sonuna kadar giderek bu çıkışı üreten kodu gözden geçirebilirsiniz. Çözümü yerel bilgisayarınıza indirerek ve WebsiteDownload proje çalıştırarak kodla denemeler yapın ya da daha fazla bilgi ve yönergeler için kendi projenizi oluşturmak için bu konunun sonunda kodu kullanma tarafından [ Gözden geçirme ve örnek uygulamayı çalıştırma](#BKMD_SettingUpTheExample).  
  
## <a name="BKMK_HandlingReentrancy"></a> Yeniden girişi işleme  
 Yolu, uygulamanızı yapmak için istediğinize bağlı olarak çeşitli yollardan yeniden işleyebilirsiniz. Bu konu aşağıdaki örnekleri sunar:  
  
-   [Başlat düğmesini devre dışı bırak](#BKMK_DisableTheStartButton)  
  
     Devre dışı **Başlat** böylece kullanıcı, kesme işlemi devam ederken düğmesi.  
  
-   [İptal edip işlemi yeniden başlatın](#BKMK_CancelAndRestart)  
  
     Kullanıcı seçtiğinde devam eden tüm işlemleri iptal **Başlat** yeniden düğmesini ve ardından let en son İstenen işleme devam edin.  
  
-   [Birden çok işlemi çalıştırın ve çıktıyı sıraya alın](#BKMK_RunMultipleOperations)  
  
     Tüm istenen işlemlerin zaman uyumsuz olarak çalışır, ancak çıktı görünümünü koordine edecek her işlemin sonuçları birlikte ve sıralı görünür izin verir.  
  
### <a name="BKMK_DisableTheStartButton"></a> Başlat düğmesini devre dışı bırak  
 Engelleyebilirsiniz **Başlat** en üstündeki düğmesini devre dışı bırakarak işlem çalışırken `StartButton_Click` olay işleyicisi. İçinden düğmeyi ardından etkinleştirebileceğiniz bir `Finally` böylece kullanıcılar uygulamayı yeniden çalıştırabilir işlem tamamlandığında engelleyin.  
  
 Aşağıdaki kod, yıldız ile işaretlenmiş bu değişiklikleri gösterir. Bu konunun sonunda kodu değişiklikleri ekleyebilir veya bitmiş uygulamayı indirebilirsiniz [zaman uyumsuz örnekleri: .NET Masaüstü uygulamalarda yeniden girişi](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Proje adı disablestartbutton.  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
    ' This line is commented out to make the results clearer in the output.  
    'ResultsTextBox.Text = ""  
  
    ' ***Disable the Start button until the downloads are complete.   
    StartButton.IsEnabled = False  
  
    Try  
        Await AccessTheWebAsync()  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
    ' ***Enable the Start button in case you want to run the program again.   
    Finally  
        StartButton.IsEnabled = True  
  
    End Try  
End Sub  
```  
  
 Değişikliklerin bir sonucu olarak düğme yanıt vermiyor ancak `AccessTheWebAsync` işlem reentered şekilde Web siteleri yüklüyor.  
  
### <a name="BKMK_CancelAndRestart"></a> İptal edip işlemi yeniden başlatın  
 Devre dışı bırakmak yerine **Başlat** düğmesini kullanabilirsiniz düğmeyi etkin tutabilirsiniz ancak, kullanıcı yeniden bu düğmeyi seçerse, zaten çalışıyor ve en son başlatılan işlemin devam izin işlemi iptal edin.  
  
 İptal işlemleri hakkında daha fazla bilgi için bkz. [Fine-Tuning Async uygulamanızda (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).  
  
 Bu senaryoyu ayarlamak için bağlantısında verilen temel kodda aşağıdaki değişiklikleri yapın [inceleme ve örnek uygulamayı çalıştırma](#BKMD_SettingUpTheExample). Bitmiş uygulamayı da indirebilirsiniz [zaman uyumsuz örnekleri: .NET Masaüstü uygulamalarda yeniden girişi](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Bu projenin adı CancelAndRestart'tır.  
  
1. Bildirme bir <xref:System.Threading.CancellationTokenSource> değişken `cts`, tüm yöntemler için kapsam dahilinde olan.  
  
    ```vb  
    Class MainWindow // Or Class MainPage  
  
        ' *** Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2. İçinde `StartButton_Click`, bir işlemin zaten çalışıp çalışmadığını belirleyin. Varsa değerini `cts` olduğu `Nothing`, hiçbir işlem zaten etkin. Değer yoksa `Nothing`, zaten çalışan işlemi iptal edildi.  
  
    ```vb  
    ' *** If a download process is already underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
    ```  
  
3. Ayarlama `cts` geçerli işlemi temsil eden farklı bir değer.  
  
    ```vb  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
    ```  
  
4. Sonunda `StartButton_Click`, geçerli işlem tamamlanır, bu nedenle ayarlayın `cts` geri `Nothing`.  
  
    ```vb  
    ' *** When the process completes, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
    ```  
  
 Aşağıdaki kod tüm değişiklikleri gösterir `StartButton_Click`. Eklentiler yıldız işareti ile işaretlenir.  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
  
    ' This line is commented out to make the results clearer.   
    'ResultsTextBox.Text = ""  
  
    ' *** If a download process is underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
  
    Try  
        ' *** Send a token to carry the message if the operation is canceled.  
        Await AccessTheWebAsync(cts.Token)  
  
    Catch ex As OperationCanceledException  
        ResultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
    End Try  
  
    ' *** When the process is complete, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
End Sub  
```  
  
 İçinde `AccessTheWebAsync`, aşağıdaki değişiklikleri yapın.  
  
-   Öğesinden iptal belirtecini kabul etmek için bir parametre ekleyin `StartButton_Click`.  
  
-   Kullanım <xref:System.Net.Http.HttpClient.GetAsync%2A> ettiğinden Web sitelerini indirmek için yöntemi `GetAsync` kabul eden bir <xref:System.Threading.CancellationToken> bağımsız değişken.  
  
-   Çağırmadan önce `DisplayResults` her indirilebilir Web sitesi için sonuçları görüntülemek için kontrol `ct` geçerli işlemi iptal edildiğini doğrulamak için.  
  
 Aşağıdaki kod, yıldız ile işaretlenmiş bu değişiklikleri gösterir.  
  
```vb  
' *** Provide a parameter for the CancellationToken from StartButton_Click.  
Private Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
    ' Declare an HttpClient object.  
    Dim client = New HttpClient()  
  
    ' Make a list of web addresses.  
    Dim urlList As List(Of String) = SetUpURLList()  
  
    Dim total = 0  
    Dim position = 0  
  
    For Each url In urlList  
        ' *** Use the HttpClient.GetAsync method because it accepts a   
        ' cancellation token.  
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' *** Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' *** Check for cancellations before displaying information about the   
        ' latest site.   
        ct.ThrowIfCancellationRequested()  
  
        position += 1  
        DisplayResults(url, urlContents, position)  
  
        ' Update the total.  
        total += urlContents.Length  
    Next  
  
    ' Display the total count for all of the websites.  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
End Function  
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
  
 Bu örnek koda değişiklikleri yapıştırarak çalıştırabilirsiniz [uygulama](#BKMK_BuildingTheApp), veya'ndaki yönergeleri takip edebilirsiniz [uygulamayı indirmeye](#BKMK_DownloadingTheApp) örneği indirip QueueResults projesini'ı çalıştırmak için.  
  
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
  
```vb  
Class MainWindow    ' Class MainPage in Windows Store app.  
  
    ' ***Declare the following variables where all methods can access them.   
    Private pendingWork As Task = Nothing  
    Private group As Char = ChrW(AscW("A") - 1)  
```  
  
 `Task` Değişken `pendingWork`, görüntüleme işlemini kesmesini ve herhangi bir grubu başka bir grubun görünen çalışmasını önler. Karakter değişkeni `group`, sonuçların beklenen sırada göründüğünü doğrulamak üzere farklı gruplardan çıkış etiketler.  
  
#### <a name="the-click-event-handler"></a>Tıklama olayı işleyicisi  
 Olay işleyicisi `StartButton_Click`, her zaman kullanıcı Grup harfini artırır **Başlat** düğmesi. Ardından işleyici çağrıları `AccessTheWebAsync` indirme işlemini çalıştırmak için.  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
    ' ***Verify that each group's results are displayed together, and that  
    ' the groups display in order, by marking each group with a letter.  
    group = ChrW(AscW(group) + 1)  
    ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Starting group {0}.", group)  
  
    Try  
        ' *** Pass the group value to AccessTheWebAsync.  
        Dim finishedGroup As Char = Await AccessTheWebAsync(group)  
  
        ' The following line verifies a successful return from the download and   
        ' display procedures.   
        ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Group {0} is complete." & vbCrLf, finishedGroup)  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
  
    End Try  
End Sub  
```  
  
#### <a name="the-accessthewebasync-method"></a>AccessTheWebAsync yöntemi  
 Bu örnekte böler `AccessTheWebAsync` öğesini iki yöntem. İlk yöntem `AccessTheWebAsync`, bir grup için tüm indirme görevlerini başlatır ve ayarlar `pendingWork` görüntüleme işlemini denetlemek için. Yöntemi, bir dil ile tümleşik sorgu (LINQ sorgusu) kullanır ve <xref:System.Linq.Enumerable.ToArray%2A> tüm indirme görevlerini aynı anda başlatmak için.  
  
 `AccessTheWebAsync` Daha sonra çağırır `FinishOneGroupAsync` her İndirmenin tamamlanmasını beklemek ve uzunluğunu görüntülemek için.  
  
 `FinishOneGroupAsync` atanmış bir görev döndürür `pendingWork` içinde `AccessTheWebAsync`. Değeri, görev önce başka bir işlem tarafından kesintiye engellediğini tamamlanmıştır.  
  
```vb  
Private Async Function AccessTheWebAsync(grp As Char) As Task(Of Char)  
  
    Dim client = New HttpClient()  
  
    ' Make a list of the web addresses to download.  
    Dim urlList As List(Of String) = SetUpURLList()  
  
    ' ***Kick off the downloads. The application of ToArray activates all the download tasks.  
    Dim getContentTasks As Task(Of Byte())() =  
        urlList.Select(Function(addr) client.GetByteArrayAsync(addr)).ToArray()  
  
    ' ***Call the method that awaits the downloads and displays the results.  
    ' Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.  
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp)  
  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & "#Task assigned for group {0}. Download tasks are active." & vbCrLf, grp)  
  
    ' ***This task is complete when a group has finished downloading and displaying.  
    Await pendingWork  
  
    ' You can do other work here or just return.  
    Return grp  
End Function  
```  
  
#### <a name="the-finishonegroupasync-method"></a>FinishOneGroupAsync yöntemi  
 Bu yöntemi izleyerek her birini bekler, karşıdan yüklenen Web sitesi uzunluğunu görüntülemek ve uzunluğu toplama ekleme bir gruptaki indirme görevlerini aracılığıyla geçiş yapar.  
  
 İlk deyimde `FinishOneGroupAsync` kullanan `pendingWork` yöntemin girilmesinin zaten içinde görüntüleme işlemini veya beklemede bir işlemle çakışmamasını sağlamak için. Bu tür bir işlem sürüyorsa, giriş işlemi kendi sırasını beklemelidir.  
  
```vb  
Private Async Function FinishOneGroupAsync(urls As List(Of String), contentTasks As Task(Of Byte())(), grp As Char) As Task  
  
    ' Wait for the previous group to finish displaying results.  
    If pendingWork IsNot Nothing Then  
        Await pendingWork  
    End If  
  
    Dim total = 0  
  
    ' contentTasks is the array of Tasks that was created in AccessTheWebAsync.  
    For i As Integer = 0 To contentTasks.Length - 1  
        ' Await the download of a particular URL, and then display the URL and  
        ' its length.  
        Dim content As Byte() = Await contentTasks(i)  
        DisplayResults(urls(i), content, i, grp)  
        total += content.Length  
    Next  
  
    ' Display the total count for all of the websites.  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
End Function  
```  
  
 Bu örnek koda değişiklikleri yapıştırarak çalıştırabilirsiniz [uygulama](#BKMK_BuildingTheApp), veya'ndaki yönergeleri takip edebilirsiniz [uygulamayı indirmeye](#BKMK_DownloadingTheApp) örneği indirip QueueResults projesini'ı çalıştırmak için.  
  
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
  
-   `pendingWork` Görev `Nothing` başlangıcında `FinishOneGroupAsync` Grup A için yalnızca ilk başlayan a. Grup A taşınmadığından henüz tamamlanmamış bir await deyimindeki ulaştığında `FinishOneGroupAsync`. Bu nedenle, Denetim öğesine dönmemiştir `AccessTheWebAsync`ve ilk atamaya `pendingWork` oluşmamıştır.  
  
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
  
1. Sıkıştırılmış dosyayı indirin [zaman uyumsuz örnekleri: .NET Masaüstü uygulamalarda yeniden girişi](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).  
  
2. İndirdiğiniz dosyanın sıkıştırmasını açın ve sonra Visual Studio'yu başlatın.  
  
3. Menü çubuğunda, **dosya**, **açık**, **proje/çözüm**.  
  
4. Sıkıştırması açılmış örnek kodun bulunduğu klasöre gidin ve ardından çözüm (.sln) dosyasını açın.  
  
5. İçinde **Çözüm Gezgini**, çalıştırın ve ardından istediğiniz projenin kısayol menüsünü **StartUpProject olarak ayarla**.  
  
6. Oluşturun ve projeyi çalıştırmak için CTRL + F5 tuşlarını seçin.  
  
### <a name="BKMK_BuildingTheApp"></a> Uygulama oluşturma  
 Aşağıdaki bölümde, örnek bir WPF uygulaması olarak oluşturmak için kod sağlar.  
  
##### <a name="to-build-a-wpf-app"></a>Bir WPF uygulaması derlemek için  
  
1. Visual Studio’yu çalıştırın.  
  
2. Menü çubuğunda, **dosya**, **yeni**, **proje**.  
  
     **Yeni proje** iletişim kutusu açılır.  
  
3. İçinde **yüklü şablonlar** bölmesini genişletin **Visual Basic**ve ardından **Windows**.  
  
4. Proje türleri listesinde seçin **WPF uygulaması**.  
  
5. Projeyi adlandırın `WebsiteDownloadWPF`ve ardından **Tamam** düğmesi.  
  
     Yeni Proje görünür **Çözüm Gezgini**.  
  
6. Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.  
  
     Sekme görünür değilse, nde MainWindow.xaml için kısayol menüsünü açın **Çözüm Gezgini**ve ardından **kodu görüntüle**.  
  
7. İçinde **XAML** MainWindow.xaml görüntülemek için kodu aşağıdaki kodla değiştirin.  
  
    ```vb  
    <Window x:Class="MainWindow"  
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
  
8. İçin bir başvuru eklemeniz <xref:System.Net.Http>.  
  
9. İçinde **Çözüm Gezgini**MainWindow.xaml.vb için kısayol menüsünü açın ve ardından **kodu görüntüle**.  
  
10. MainWindow.xaml.vb kodu aşağıdaki kodla değiştirin.  
  
    ```vb  
    ' Add the following Imports statements, and add a reference for System.Net.Http.  
    Imports System.Net.Http  
    Imports System.Threading  
  
    Class MainWindow  
  
        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
            ' This line is commented out to make the results clearer in the output.  
            'ResultsTextBox.Text = ""  
  
            Try  
                Await AccessTheWebAsync()  
  
            Catch ex As Exception  
                ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
  
            End Try  
        End Sub  
  
        Private Async Function AccessTheWebAsync() As Task  
  
            ' Declare an HttpClient object.  
            Dim client = New HttpClient()  
  
            ' Make a list of web addresses.  
            Dim urlList As List(Of String) = SetUpURLList()  
  
            Dim total = 0  
            Dim position = 0  
  
            For Each url In urlList  
                ' GetByteArrayAsync returns a task. At completion, the task  
                ' produces a byte array.  
                Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
  
                position += 1  
                DisplayResults(url, urlContents, position)  
  
                ' Update the total.  
                total += urlContents.Length  
            Next  
  
            ' Display the total count for all of the websites.  
            ResultsTextBox.Text &=  
                String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
        End Function  
  
        Private Function SetUpURLList() As List(Of String)  
            Dim urls = New List(Of String) From  
            {  
                "https://msdn.microsoft.com/library/hh191443.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/jj155761.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/hh524395.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
            Return urls  
        End Function  
  
        Private Sub DisplayResults(url As String, content As Byte(), pos As Integer)  
            ' Display the length of each website. The string format is designed  
            ' to be used with a monospaced font, such as Lucida Console or  
            ' Global Monospace.  
  
            ' Strip off the "http:'".  
            Dim displayURL = url.Replace("https://", "")  
            ' Display position in the URL list, the URL, and the number of bytes.  
            ResultsTextBox.Text &= String.Format(vbCrLf & "{0}. {1,-58} {2,8}", pos, displayURL, content.Length)  
        End Sub  
    End Class  
    ```  
  
11. Programı çalıştırın ve ardından CTRL + F5 tuşlarına basın **Başlat** düğmesine birkaç kez.  
  
12. Değişikliklerini yapın [Başlat düğmesini devre dışı](#BKMK_DisableTheStartButton), [iptal edip işlemi yeniden](#BKMK_CancelAndRestart), veya [birden çok işlemi çalıştırın ve çıktıyı sıraya](#BKMK_RunMultipleOperations) yeniden giriş işlemek için.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Zaman uyumsuz programlama ile Async ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
