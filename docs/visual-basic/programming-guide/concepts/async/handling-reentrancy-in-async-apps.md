---
title: Zaman Uyumsuz Uygulamalarda Yeniden Girişi İşleme
ms.date: 07/20/2015
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
ms.openlocfilehash: 110298a2ca937dbf39c94cfe9df29afb2e76a91c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021498"
---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a>Async Apps 'da Reentrancy Işleme (Visual Basic)

Uygulamanıza eşzamanlı kod eklediğinizde, yeniden işlem tamamlanmadan önce yeniden girmeyi ifade eden yeniden canlandırmayı düşünmelisiniz ve muhtemelen önlemeniz gerekir. Yeniden canlandırma olasılıklarını tanımlamaz ve işlemezseniz, beklenmeyen sonuçlara neden olabilir.

> [!NOTE]
> Örneği çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınıza yüklü olması gerekir.

> [!NOTE]
> Aktarım Katmanı Güvenliği (TLS) sürüm 1.2 artık uygulama geliştirmenizde kullanılacak minimum sürümdür. Uygulamanız 4,7'den önce bir .NET Framework sürümünü hedefliyorsa, .NET Framework ile birlikte [Taşıma Katmanı Güvenliği (TLS) en iyi uygulamaları](../../../../framework/network-programming/tls.md)için aşağıdaki makaleye bakın.

## <a name="recognizing-reentrancy"></a><a name="BKMK_RecognizingReentrancy"></a>Reentrancy Tanıma

Bu konudaki örnekte, kullanıcılar bir dizi web sitesi indiren ve indirilen toplam bayt sayısını hesaplayan bir eşzamanlı uygulama başlatmak için bir **Başlat** düğmesi seçer. Örneğin eşzamanlı sürümü, ilk kez kullanıcının düğmeyi kaç kez seçtiğine bakılmaksızın aynı şekilde yanıt verir, çünkü ilk kez kullanıcı işi, uygulama çalışan bitene kadar bu olayları yok sayar. Ancak, bir eşzamanlı uygulamada, Kullanıcı Birsonucu iş parçacığı yanıt vermeye devam eder ve tamamlanmadan önce eşzamanlı işlemi yeniden girebilirsiniz.

Aşağıdaki örnekte, kullanıcı **Başlat** düğmesini yalnızca bir kez seçerse beklenen çıktı yı gösterir. İndirilen web sitelerinin listesi, her sitenin boyutu, baytlar halinde görüntülenir. Sonunda toplam bayt sayısı görünür.

```console
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

Ancak, kullanıcı düğmeyi birden çok kez seçerse, olay işleyicisi tekrar tekrar çağrılır ve indirme işlemi her seferinde yeniden girilir. Sonuç olarak, aynı anda birkaç eşzamanlı işlem yürütülür, çıktı sonuçları birbirine bırakır ve toplam bayt sayısı kafa karıştırıcıdır.

```console
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

Bu konunun sonuna kaydırarak bu çıktıyı üreten kodu gözden geçirebilirsiniz. Çözümü yerel bilgisayarınıza indirip ardından WebsiteDownload projesini çalıştırarak veya kendi projenizi oluşturmak için bu konunun sonundaki kodu kullanarak kodu deneyebilirsiniz Daha fazla bilgi ve talimatlar için [Örnek Uygulamayı Gözden Geçirme ve Çalıştırma](#BKMD_SettingUpTheExample)bölümüne bakın.

## <a name="handling-reentrancy"></a><a name="BKMK_HandlingReentrancy"></a>Reentrancy işleme

Uygulamanızın ne yapmasını istediğinize bağlı olarak, yeniden canlandırma işlemlerini çeşitli şekillerde işleyebilirsiniz. Bu konu aşağıdaki örnekleri sunar:

- [Başlat Düğmesini Devre Dışı](#BKMK_DisableTheStartButton)

  İşlem çalışırken **Başlat** düğmesini devre dışı kalarak kullanıcı nın sözünü kesemeyecek şekilde devre dışı edin.

- [İşlemi İptal Etme ve Yeniden Başlatma](#BKMK_CancelAndRestart)

  Kullanıcı **Başlat** düğmesini yeniden seçtiğinde çalışmaya devam eden tüm işlemleri iptal edin ve en son istenen işlemin devam etmesine izin verin.

- [Birden Çok İşlem çalıştırın ve Çıktıyı Sıraya](#BKMK_RunMultipleOperations)

  İstenen tüm işlemlerin eşzamanlı olarak çalışmasına izin verin, ancak her işlemden elde edilen sonuçların birlikte ve sırayla görünmesi için çıktının görüntülenmesini koordine edin.

### <a name="disable-the-start-button"></a><a name="BKMK_DisableTheStartButton"></a>Başlat Düğmesini Devre Dışı

Olay işleyicisinin üst kısmındaki düğmeyi devre dışı bırakarak işlem çalışırken Başlat düğmesini engelleyebilirsiniz. **Start** `StartButton_Click` Daha sonra, işlem bittiğinde düğmeyi bir `Finally` blok içinden yeniden etkinleştirebilirsiniz, böylece kullanıcılar uygulamayı yeniden çalıştırabilir.

Aşağıdaki kod, yıldız işaretleriyle işaretlenmiş bu değişiklikleri gösterir. Bu konunun sonunda koda değişiklikleri ekleyebilirsiniz veya bitmiş uygulamayı [Async Samples: Reentrancy in .NET Desktop Apps'tan](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)indirebilirsiniz. Proje adı DisableStartButton'dur.

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

Değişikliklerin bir sonucu olarak, düğme web sitelerini indirirken `AccessTheWebAsync` yanıt vermez, bu nedenle işlem yeniden girilemez.

### <a name="cancel-and-restart-the-operation"></a><a name="BKMK_CancelAndRestart"></a>İşlemi İptal Etme ve Yeniden Başlatma

**Başlat** düğmesini devre dışı bırakmak yerine düğmeyi etkin tutabilirsiniz, ancak kullanıcı bu düğmeyi tekrar seçerse, zaten çalışan işlemi iptal edin ve en son başlatılan işlemin devam etmesine izin verin.

İptal hakkında daha fazla bilgi için [Async Uygulamanızı (Visual Basic) İnce Ayarla'ya](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)bakın.

Bu senaryoyu ayarlamak için, Örnek Uygulamayı Gözden Geçirme [ve Çalıştırma'da](#BKMD_SettingUpTheExample)sağlanan temel kodda aşağıdaki değişiklikleri yapın. Ayrıca bitmiş uygulamayı [Async Samples: Reentrancy in .NET Desktop Apps'tan](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)da indirebilirsiniz. Bu projenin adı CancelAndRestart olduğunu.

1. Tüm <xref:System.Threading.CancellationTokenSource> yöntemler `cts`için kapsamda olan bir değişken bildirin.

    ```vb
    Class MainWindow // Or Class MainPage

        ' *** Declare a System.Threading.CancellationTokenSource.
        Dim cts As CancellationTokenSource
    ```

2. In `StartButton_Click`, bir işlemin devam edip etmediğini belirleyin. Değeri `cts` ise, `Nothing`hiçbir işlem zaten etkindir. Değer `Nothing`değilse, zaten çalışan işlem iptal edilir.

    ```vb
    ' *** If a download process is already underway, cancel it.
    If cts IsNot Nothing Then
        cts.Cancel()
    End If
    ```

3. `cts` Geçerli işlemi temsil eden farklı bir değerayarlayın.

    ```vb
    ' *** Now set cts to cancel the current process if the button is chosen again.
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()
    cts = newCTS
    ```

4. `StartButton_Click`Sonunda, geçerli işlem tamamlandı, bu yüzden `cts` geri değerini `Nothing`ayarlayın.

    ```vb
    ' *** When the process completes, signal that another process can proceed.
    If cts Is newCTS Then
        cts = Nothing
    End If
    ```

Aşağıdaki kod' daki tüm `StartButton_Click`değişiklikleri gösterir. Eklemeler yıldız işaretleri ile işaretlenir.

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

In `AccessTheWebAsync`, aşağıdaki değişiklikleri yapın.

- 'den `StartButton_Click`iptal belirteci kabul etmek için bir parametre ekleyin.

- Bir <xref:System.Threading.CancellationToken> <xref:System.Net.Http.HttpClient.GetAsync%2A> bağımsız `GetAsync` değişkenkabul ettiği için web sitelerini indirmek için yöntemi kullanın.

- İndirilen her web sitesinin sonuçlarını görüntülemek için aramadan `DisplayResults` önce, geçerli işlemin iptal edilmediğini kontrol edin. `ct`

 Aşağıdaki kod, yıldız işaretleriyle işaretlenmiş bu değişiklikleri gösterir.

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

Bu uygulama çalışırken **Başlat** düğmesini birkaç kez seçerseniz, aşağıdaki çıktıya benzeyen sonuçlar üretmelidir:

```console
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

Kısmi listeleri ortadan kaldırmak `StartButton_Click` için, kullanıcı işlemi her yeniden başlattığında metin kutusunu temizlemek için ilk kod satırının yorumunu kaldırın.

### <a name="run-multiple-operations-and-queue-the-output"></a><a name="BKMK_RunMultipleOperations"></a>Birden Çok İşlem çalıştırın ve Çıktıyı Sıraya

Bu üçüncü örnek, uygulamanın **kullanıcının Başlat** düğmesini her seçtiğinde başka bir eşzamanlı işlem başlatması ve tüm işlemlerin tamamlanması için çalıştırılması açısından en karmaşık örnektir. İstenen tüm işlemler listedeki web sitelerini eşit olarak indirir, ancak işlemlerden elde edilen çıktı sırayla sunulur. Diğer bir deyişle, [Reentrancy'yi Tanıma'daki](#BKMK_RecognizingReentrancy) çıktının gösterdiği gibi, gerçek indirme etkinliği birbiriyle bağlantılıdır, ancak her grubun sonuç listesi ayrı olarak sunulur.

İşlemler, görüntüleme <xref:System.Threading.Tasks.Task> `pendingWork`işlemi için bir kapı bekçisi olarak hizmet veren genel bir , paylaşır.

[Uygulamayı Oluşturma'da](#BKMK_BuildingTheApp)değişiklikleri koda yapıştırarak bu örneği çalıştırabilir veya örneği indirmek ve ardından QueueResults projesini çalıştırmak için [Uygulamayı İndirme](#BKMK_DownloadingTheApp) yönergelerini izleyebilirsiniz.

Kullanıcı **Başlat** düğmesini yalnızca bir kez seçerse aşağıdaki çıktı sonucu gösterir. A harf etiketi, sonucun **Başlat** düğmesinin ilk kez seçildiği nden geldiğini gösterir. Sayılar, indirme hedefleri listesindeKI URL'lerin sırasını gösterir.

```console
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

Kullanıcı **Başlat** düğmesini üç kez seçerse, uygulama aşağıdaki satırları andıran çıktı üretir. Pound işaretiyle başlayan bilgi satırları (#) uygulamanın ilerlemesini izler.

```console
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

B ve C grupları A grubu bitmeden önce başlar, ancak her grubun çıktısı ayrı ayrı görüntülenir. A grubu için tüm çıktı önce görünür, ardından B grubu için tüm çıktı ve ardından C grubu için tüm çıktı çıkar. Uygulama her zaman grupları sırayla görüntüler ve her grup için URL'lerin URL'leri listesinde görünmesi sırasına göre her zaman web siteleri hakkındaki bilgileri görüntüler.

Ancak, indirmelerin gerçekte gerçekleşme sırası tahmin edemezsiniz. Birden çok grup başlatıldıktan sonra, oluşturdukları indirme görevlerinin tümü etkin olur. A-1'in B-1'den önce indirileceğini varsayamaz ve A-1'in A-2'den önce indirileceğini varsayamazsınız.

#### <a name="global-definitions"></a>Küresel Tanımlar

Örnek kod, tüm yöntemlerden görülebilen aşağıdaki iki genel bildirim içerir.

```vb
Class MainWindow    ' Class MainPage in Windows Store app.

    ' ***Declare the following variables where all methods can access them.
    Private pendingWork As Task = Nothing
    Private group As Char = ChrW(AscW("A") - 1)
```

Değişken, `Task` `pendingWork`görüntü işlemini denetler ve herhangi bir grubun başka bir grubun görüntüleme işlemini kesintiye uğratmasını önler. Karakter değişkeni, `group`sonuçların beklenen sırada göründüğünü doğrulamak için farklı gruplardan çıktı etiketler.

#### <a name="the-click-event-handler"></a>Tıklayın Olay Handleyici

Olay işleyicisi, `StartButton_Click`kullanıcı **Başlat** düğmesini her seçtiğinde grup harfini de martılar. Daha sonra işleyici indirme işlemini çalıştırmak için çağırır. `AccessTheWebAsync`

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

#### <a name="the-accessthewebasync-method"></a>AccessThewebasync Yöntemi

Bu örnek `AccessTheWebAsync` iki yönteme bölünür. İlk yöntem, `AccessTheWebAsync`bir grup için tüm indirme görevlerini `pendingWork` başlatır ve görüntüleme işlemini denetlemek için ayarlar. Yöntem, bir Dil Tümleşik Sorgusu <xref:System.Linq.Enumerable.ToArray%2A> (LINQ sorgusu) kullanır ve tüm indirme görevlerini aynı anda başlatmak için kullanır.

`AccessTheWebAsync`sonra `FinishOneGroupAsync` her indirme tamamlanmasını beklemek ve uzunluğunu görüntülemek için çağırır.

`FinishOneGroupAsync``pendingWork` 'de `AccessTheWebAsync`atanan bir görev döndürür. Bu değer, görev tamamlanmadan önce başka bir işlemtarafından kesintiye uğramayı önler.

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

#### <a name="the-finishonegroupasync-method"></a>FinishOneGroupAsync Yöntemi

Bu yöntem, bir gruptaki indirme görevleri arasında geçiş yapmakta, her birini bekler, indirilen web sitesinin uzunluğunu görüntüler ve uzunluğu toplama ekler.

Yönteme girmenin zaten görüntü sürecinde olan veya zaten bekleyen bir işlemi etkilemediğinden emin olmak için `FinishOneGroupAsync` kullanılan `pendingWork` ilk deyim. Böyle bir işlem devam ediyorsa, giren işlem sırasını beklemelidir.

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

[Uygulamayı Oluşturma'da](#BKMK_BuildingTheApp)değişiklikleri koda yapıştırarak bu örneği çalıştırabilir veya örneği indirmek için [Uygulamayı İndirme](#BKMK_DownloadingTheApp) yönergelerini izleyebilir ve ardından QueueResults projesini çalıştırabilirsiniz.

#### <a name="points-of-interest"></a>İlgi Çekici Noktalar

Çıktıdaki pound işaretiyle (#) başlayan bilgi satırları, bu örneğin nasıl çalıştığını açıklığa kavuşturur.

Çıktı aşağıdaki desenleri gösterir.

- Önceki bir grup çıktısını görüntülerken bir grup başlatılabilir, ancak önceki grubun çıktısının görüntülenmesi kesintiye uğramaz.

  ```console
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

- Görev, `pendingWork` `Nothing` yalnızca ilk `FinishOneGroupAsync` olarak başlayan A grubu için başlangıçtadır. A Grubu, 'ye ulaştığında `FinishOneGroupAsync`bekleyen bir ifadeyi henüz tamamlamadı. Bu nedenle, denetim döndürülmedi `AccessTheWebAsync`ve ilk `pendingWork` atama gerçekleşmedi.

- Aşağıdaki iki satır her zaman çıkışta birlikte görünür. Kod, bir grubun çalışmasını başlatma `StartButton_Click` ile grup için bir görev atamak arasında hiçbir zaman kesintiye `pendingWork`uğramaz.

  ```console
  #Starting group B.
  #Task assigned for group B. Download tasks are active.
  ```

  Bir grup `StartButton_Click`girdikten sonra, işlem girene `FinishOneGroupAsync`kadar bekleme ifadesini tamamlamaz. Bu nedenle, kodun bu kesimi sırasında başka hiçbir işlem denetim elde edemez.

## <a name="reviewing-and-running-the-example-app"></a><a name="BKMD_SettingUpTheExample"></a>Örnek Uygulamayı İnceleme ve Çalıştırma

Örnek uygulamayı daha iyi anlamak için uygulamayı indirebilir, kendiniz oluşturabilir veya uygulamayı uygulamadan bu konunun sonundaki kodu gözden geçirebilirsiniz.

> [!NOTE]
> Örneği Windows Presentation Foundation (WPF) masaüstü uygulaması olarak çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınıza yüklü olması gerekir.

### <a name="downloading-the-app"></a><a name="BKMK_DownloadingTheApp"></a>Uygulamayı İndirme

1. Sıkıştırılmış dosyayı [Async Samples: Reentrancy in .NET Desktop Apps'tan](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)indirin.

2. İndirdiğiniz dosyayı sıkıştırın ve Visual Studio'yu başlatın.

3. Menü çubuğunda **Dosya**, **Aç**, **Proje/Çözüm'ü**seçin.

4. Sıkıştırılmış örnek kodu tutan klasöre gidin ve ardından çözüm (.sln) dosyasını açın.

5. **Çözüm Gezgini'nde,** çalıştırmak istediğiniz proje için kısayol menüsünü açın ve ardından **StartUpProject olarak ayarla'yı**seçin.

6. Projeyi oluşturmak ve çalıştırmak için CTRL+F5 tuşlarını seçin.

### <a name="building-the-app"></a><a name="BKMK_BuildingTheApp"></a>Uygulamayı Oluşturma

Aşağıdaki bölümde, örneği WPF uygulaması olarak oluşturmak için kod sağlanır.

##### <a name="to-build-a-wpf-app"></a>WPF uygulaması oluşturmak için

1. Visual Studio’yu çalıştırın.

2. Menü çubuğunda **Dosya**, **Yeni**, **Proje'yi**seçin.

     **Yeni Proje** iletişim kutusu açılır.

3. Yüklü **Şablonlar** bölmesinde Visual **Basic'i**genişletin ve **ardından Windows'u**genişletin.

4. Proje türleri listesinde **WPF Uygulaması'nı**seçin.

5. Projeyi `WebsiteDownloadWPF`adlandırın, 4,6 veya daha yüksek .NET Framework sürümünü seçin ve ardından **Tamam** düğmesini tıklatın.

     Yeni proje Çözüm **Gezgini'nde**görünür.

6. Visual Studio Code Editor'da **MainWindow.xaml** sekmesini seçin.

     Sekme görünmüyorsa, **Solution Explorer'da**MainWindow.xaml için kısayol menüsünü açın ve ardından **Kodu Görüntüle'yi**seçin.

7. MainWindow.xaml'ın **XAML** görünümünde kodu aşağıdaki kodla değiştirin.

    ```xaml
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

     MainWindow.xaml'ın **Tasarım** görünümünde metin kutusu ve düğme içeren basit bir pencere görüntülenir.

8. **Çözüm Gezgini'nde,** **Başvurular'a** sağ tıklayın ve **Referans Ekle'yi**seçin.

     Zaten seçilmemişse, için <xref:System.Net.Http>bir başvuru ekleyin.

9. **Çözüm Gezgini'nde**MainWindow.xaml.vb için kısayol menüsünü açın ve ardından **Kodu Görüntüle'yi**seçin.

10. MainWindow.xaml.vb'de kodu aşağıdaki kodla değiştirin.

    ```vb
    ' Add the following Imports statements, and add a reference for System.Net.Http.
    Imports System.Net.Http
    Imports System.Threading

    Class MainWindow

        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)
            System.Net.ServicePointManager.SecurityProtocol = System.Net.ServicePointManager.SecurityProtocol Or System.Net.SecurityProtocolType.Tls12

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

11. Programı çalıştırmak için CTRL+F5 tuşlarını seçin ve ardından **Başlat** düğmesini birkaç kez seçin.

12. [Başlat Düğmesini Devre Dışı Devre](#BKMK_DisableTheStartButton)Dışı, [İşlemi İptal Et ve Yeniden Başlat'](#BKMK_CancelAndRestart)tan değişiklikler yapın veya birden çok işlemi çalıştırın ve yeniden başlatma işlemini işlemek için [Çıktıyı](#BKMK_RunMultipleOperations) Sıralayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Walkthrough: Async ve Await (Visual Basic) kullanarak Web'e erişim](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async ve Await ile Asynchronous Programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
