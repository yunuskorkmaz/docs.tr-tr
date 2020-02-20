---
title: Zaman Uyumsuz Uygulamalarda Yeniden Girişi İşleme
ms.date: 07/20/2015
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
ms.openlocfilehash: 44c2cdbadd02aef6b2bbb32bde8bcb9b19f8360d
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452584"
---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a>Zaman uyumsuz uygulamalarda yeniden girişi işleme (Visual Basic)

Uygulamanıza zaman uyumsuz kod eklediğinizde, işlem tamamlanmadan önce zaman uyumsuz bir işlemi yeniden girmeye işaret eden yeniden giriş yapmayı göz önünde bulundurmalı ve muhtemelen engellemeniz gerekir. Yeniden giriş için olanaklar tanımlamazsanız ve işleyemezseniz, bu durum beklenmedik sonuçlara neden olabilir.

> [!NOTE]
> Örneği çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.

> [!NOTE]
> Aktarım Katmanı Güvenliği (TLS) sürüm 1,2 artık uygulama geliştirmede kullanılacak en düşük sürümdür. Uygulamanız 4,7 sürümünden önceki bir .NET Framework sürümünü hedefliyorsa [.NET Framework Aktarım Katmanı Güvenliği (TLS) en iyi uygulamaları](../../../../framework/network-programming/tls.md)için aşağıdaki makaleye bakın.

## <a name="BKMK_RecognizingReentrancy"></a>Yeniden giriş tanıma

Bu konudaki örnekte, kullanıcılar bir dizi Web sitesini indiren ve indirilen toplam bayt sayısını hesaplayan bir zaman uyumsuz uygulamayı başlatmak için bir **Başlat** düğmesi seçer. Örneğin zaman uyumlu bir sürümü, bir kullanıcının düğmeyi kaç kez seçtiğinden bağımsız olarak aynı şekilde yanıt verir, çünkü ilk kez sonra, uygulama çalışmaya bitene kadar UI iş parçacığı bu olayları yoksayar. Ancak zaman uyumsuz bir uygulamada, UI iş parçacığı yanıt vermeye devam eder ve tamamlanmadan önce zaman uyumsuz işlemi yeniden girebilirsiniz.

Aşağıdaki örnek, Kullanıcı **Başlat** düğmesini yalnızca bir kez seçerse beklenen çıktıyı gösterir. İndirilen Web sitelerinin listesi, her sitenin bayt cinsinden boyutu ile görüntülenir. Toplam bayt sayısı sonda görüntülenir.

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

Ancak Kullanıcı düğmeyi birden çok kez seçerse, olay işleyicisi sürekli olarak çağrılır ve yükleme işlemi her seferinde yeniden girilir. Sonuç olarak, birkaç zaman uyumsuz işlem aynı anda çalışır, çıkış sonuçları birbirine bırakır ve toplam bayt sayısı kafa karıştırıcı olur.

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

Bu çıkışın sonuna kadar kayarak bu çıktıyı üreten kodu gözden geçirebilirsiniz. Çözümü yerel bilgisayarınıza indirerek ve ardından WebsiteDownload projesini çalıştırarak veya bu konunun sonundaki kodu kullanarak, daha fazla bilgi ve yönergeler Için, bkz. [Örnek uygulamayı inceleme ve çalıştırma](#BKMD_SettingUpTheExample).

## <a name="BKMK_HandlingReentrancy"></a>Yeniden giriş işleme

Uygulamanızın ne yaptığını istediğinize bağlı olarak çeşitli yollarla yeniden giriş gerçekleştirebilirsiniz. Bu konu aşağıdaki örnekleri sunmaktadır:

- [Başlat düğmesini devre dışı bırak](#BKMK_DisableTheStartButton)

  İşlem çalışırken kullanıcının kesintiye uğramaması için **Başlat** düğmesini devre dışı bırakın.

- [Işlemi iptal edin ve yeniden başlatın](#BKMK_CancelAndRestart)

  Kullanıcı **Başlat** düğmesini yeniden seçtiğinde çalışmaya devam eden tüm işlemleri iptal edin ve son istenen işlemin devam etmesine izin verin.

- [Birden çok Işlemi çalıştırma ve çıktıyı sıraya alma](#BKMK_RunMultipleOperations)

  Tüm istenen işlemlerin zaman uyumsuz olarak çalışmasına izin verin, ancak her bir işlemin sonuçlarının bir arada ve sırayla görünmesi için çıktının görüntülenmesini koordine edin.

### <a name="BKMK_DisableTheStartButton"></a>Başlat düğmesini devre dışı bırak

`StartButton_Click` olay işleyicisinin en üstündeki düğmeyi devre dışı bırakarak, bir işlem çalışırken **Başlat** düğmesini engelleyebilirsiniz. Böylece, kullanıcılar uygulamayı yeniden çalıştırabilmeleri için işlem bittiğinde düğmeyi bir `Finally` bloğu içinden yeniden etkinleştirebilirsiniz.

Aşağıdaki kod, yıldız işaretiyle işaretlenen bu değişiklikleri gösterir. Bu konunun sonundaki koda değişiklikleri ekleyebilir veya tamamlanmış uygulamayı [zaman uyumsuz örneklerden indirebilirsiniz: .net masaüstü uygulamalarında yeniden giriş](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)yapabilirsiniz. Proje adı DisableStartButton ' dir.

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

Değişikliklerin bir sonucu olarak, `AccessTheWebAsync` Web sitelerini indirirken işlem yeniden girilemez.

### <a name="BKMK_CancelAndRestart"></a>Işlemi iptal edin ve yeniden başlatın

**Başlat** düğmesini devre dışı bırakmak yerine düğmeyi etkin tutabilirsiniz, ancak kullanıcı bu düğmeyi yeniden seçerse, zaten çalışmakta olan işlemi iptal edin ve en son başlatılan işlemin devam etmesine izin verin.

İptal hakkında daha fazla bilgi için bkz. [zaman uyumsuz uygulamanızda Ince ayar yapma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).

Bu senaryoyu ayarlamak için, [Örnek uygulamayı gözden geçirmek ve çalıştırmak](#BKMD_SettingUpTheExample)için belirtilen temel kodda aşağıdaki değişiklikleri yapın. Ayrıca, tamamlanmış uygulamayı [zaman uyumsuz örneklerden indirebilirsiniz: .net masaüstü uygulamalarında yeniden giriş](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)yapabilirsiniz. Bu projenin adı, yeniden başlatma.

1. Tüm yöntemler için kapsam içindeki bir <xref:System.Threading.CancellationTokenSource> değişken `cts`bildirin.

    ```vb
    Class MainWindow // Or Class MainPage

        ' *** Declare a System.Threading.CancellationTokenSource.
        Dim cts As CancellationTokenSource
    ```

2. `StartButton_Click`, bir işlemin zaten devam edilip edilmeyeceğini saptayın. `cts` değeri `Nothing`ise, hiçbir işlem zaten etkin değildir. Değer `Nothing`değilse, zaten çalışmakta olan işlem iptal edilir.

    ```vb
    ' *** If a download process is already underway, cancel it.
    If cts IsNot Nothing Then
        cts.Cancel()
    End If
    ```

3. `cts` geçerli işlemi temsil eden farklı bir değere ayarlayın.

    ```vb
    ' *** Now set cts to cancel the current process if the button is chosen again.
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()
    cts = newCTS
    ```

4. `StartButton_Click`sonunda geçerli işlem tamamlanmıştır, bu nedenle `cts` değerini `Nothing`olarak ayarlayın.

    ```vb
    ' *** When the process completes, signal that another process can proceed.
    If cts Is newCTS Then
        cts = Nothing
    End If
    ```

Aşağıdaki kod `StartButton_Click`tüm değişiklikleri gösterir. Ekler yıldız işaretiyle işaretlenir.

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

`AccessTheWebAsync`, aşağıdaki değişiklikleri yapın.

- `StartButton_Click`iptal belirtecini kabul etmek için bir parametre ekleyin.

- `GetAsync` bir <xref:System.Threading.CancellationToken> bağımsız değişkenini kabul ettiğinden Web sitelerini indirmek için <xref:System.Net.Http.HttpClient.GetAsync%2A> yöntemi kullanın.

- İndirilen her Web sitesinin sonuçlarını göstermek için `DisplayResults` çağrılmadan önce, geçerli işlemin iptal edildiğini doğrulamak için `ct` denetleyin.

 Aşağıdaki kod, yıldız işaretiyle işaretlenen bu değişiklikleri gösterir.

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

Kısmi listeleri ortadan kaldırmak için, kullanıcının işlemi her yeniden başlattığı her seferinde metin kutusunu temizlemek üzere `StartButton_Click` içindeki ilk kod satırının açıklamasını kaldırın.

### <a name="BKMK_RunMultipleOperations"></a>Birden çok Işlemi çalıştırma ve çıktıyı sıraya alma

Bu üçüncü örnek, Kullanıcı **Başlat** düğmesini her seçtiğinde uygulamanın başka bir zaman uyumsuz işlem başlatması ve tüm işlemlerin tamamlamada çalışması için en karmaşıktır. Tüm istenen işlemler, listeden zaman uyumsuz olarak Web sitelerini indirir, ancak işlemlerden alınan çıkış sıralı olarak sunulur. Diğer bir deyişle, gerçek indirme etkinliği araya eklemeli, bu da bir yandan [yeniden](#BKMK_RecognizingReentrancy) giriş, ancak her grup için sonuçların listesi ayrı olarak sunulur.

İşlemler, görüntüleme işlemi için bir ağ geçidi denetleyicisi görevi gören küresel bir <xref:System.Threading.Tasks.Task>`pendingWork`paylaşır.

Değişiklikleri [uygulamayı oluşturma](#BKMK_BuildingTheApp)bölümünde koda yapıştırarak bu örneği çalıştırabilir veya örneği Indirmek Için [uygulamayı indirme](#BKMK_DownloadingTheApp) bölümündeki yönergeleri izleyerek örneği indirip queueresults projesini çalıştırabilirsiniz.

Aşağıdaki çıktıda, Kullanıcı **Başlat** düğmesini yalnızca bir kez seçerse sonuç gösterilmektedir. Harf etiketi,, sonucun **Başlangıç** düğmesinin seçildiği ilk sefer olduğunu gösterir. Sayılar, indirme hedefleri listesindeki URL 'lerin sırasını gösterir.

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

Kullanıcı **Başlat** düğmesini üç kez seçerse, uygulama aşağıdaki satırlara benzer bir çıktı üretir. Numara işareti (#) ile başlayan bilgi satırları, uygulamanın ilerlemesini izler.

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

Grup A tamamlanmadan önce B ve C grupları başlar, ancak her grubun çıktısı ayrı olarak görünür. Önce Grup A 'nın tüm çıktıları, ardından Grup B için tüm çıktılar ve sonra Grup C için tüm çıktılar görüntülenir. Uygulama her zaman grupları sırayla görüntüler ve her grup için her zaman tek tek Web siteleri hakkındaki bilgileri URL 'Ler listesinde görünecek şekilde görüntüler.

Ancak, indirmelerin gerçekten gerçekleştiği sırayı tahmin edemezseniz. Birden çok grup başlatıldıktan sonra, oluşturdukları yükleme görevlerinin hepsi etkindir. -1 ' in B-1 ' den önce indirileceğini varsaymazsınız ve-1 ' in-2 ' den önce indirildiğini varsaymazsınız.

#### <a name="global-definitions"></a>Genel tanımlar

Örnek kod, tüm metotlardan görülebilen aşağıdaki iki genel bildirimi içerir.

```vb
Class MainWindow    ' Class MainPage in Windows Store app.

    ' ***Declare the following variables where all methods can access them.
    Private pendingWork As Task = Nothing
    Private group As Char = ChrW(AscW("A") - 1)
```

`Task` değişkeni, `pendingWork`, görüntüleme sürecini fazla görür ve herhangi bir grubun başka bir grubun görüntüleme işlemini kesintiye uğramasını önler. `group`karakter değişkeni, sonuçların beklenen sırada göründüğünü doğrulamak için farklı gruplardan çıktıyı Etiketler.

#### <a name="the-click-event-handler"></a>Click olay Işleyicisi

`StartButton_Click`olay işleyicisi, Kullanıcı **Başlat** düğmesini her seçtiğinde grup harfini artırır. Ardından işleyici, indirme işlemini çalıştırmak için `AccessTheWebAsync` çağırır.

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

Bu örnek `AccessTheWebAsync` iki yönteme ayırır. İlk yöntem `AccessTheWebAsync`, bir grup için tüm indirme görevlerini başlatır ve görüntüleme işlemini denetlemek için `pendingWork` ayarlar. Yöntemi, aynı anda tüm indirme görevlerini başlatmak için bir dil tümleşik sorgu (LINQ sorgusu) ve <xref:System.Linq.Enumerable.ToArray%2A> kullanır.

`AccessTheWebAsync`, her indirmenin tamamlanmasını beklemek için `FinishOneGroupAsync` çağırır ve uzunluğunu görüntüler.

`FinishOneGroupAsync`, `AccessTheWebAsync``pendingWork` atanan bir görevi döndürür. Bu değer, görev tamamlanmadan önce başka bir işlem kesintiye uğramasını önler.

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

Bu yöntem bir gruptaki indirme görevleri boyunca geçiş yapar, her birini bekliyor, indirilen Web sitesinin uzunluğunu görüntülüyor ve uzunluğu toplamına ekliyor.

`FinishOneGroupAsync` ilk ifade, yöntemi girerken, zaten görüntüleme işleminde olan veya zaten bekleyen bir işlemi etkilemediğinden emin olmak için `pendingWork` kullanır. Bu tür bir işlem devam ediyorsa, giriş işleminin tamamlanmasını beklemesi gerekir.

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

Bu örneği, [uygulamayı oluştururken](#BKMK_BuildingTheApp)koda değişiklikleri yapıştırarak çalıştırabilir veya örneği Indirmek Için [uygulamayı indirme](#BKMK_DownloadingTheApp) bölümündeki yönergeleri izleyerek örneği indirip queueresults projesini çalıştırabilirsiniz.

#### <a name="points-of-interest"></a>Ilgi çekici noktaları

Çıktıda diyez işareti (#) ile başlayan bilgi satırları bu örneğin nasıl çalıştığını açıklığa kavuşturacak.

Çıktıda aşağıdaki desenler gösterilmektedir.

- Bir grup, önceki bir grup çıktısını görüntülerken başlatılabilir, ancak önceki grubun çıktısının görüntülenmediği kesintiye uğramaz.

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

- `pendingWork` görevi, yalnızca ilk başlatılan A grubu için `FinishOneGroupAsync` başlangıcında `Nothing`. A grubu `FinishOneGroupAsync`ulaştığında bir await ifadesi henüz tamamlanmadı. Bu nedenle, denetim `AccessTheWebAsync`döndürülmemiştir ve `pendingWork` ilk atama gerçekleşmemiştir.

- Aşağıdaki iki satır, her zaman çıktıda birlikte görüntülenir. Kod, `StartButton_Click` bir grubun işlemini başlatma ve grup için bir görevin `pendingWork`atama arasında hiçbir şekilde kesintiye uğramaz.

  ```console
  #Starting group B.
  #Task assigned for group B. Download tasks are active.
  ```

  Bir grup `StartButton_Click`girdikten sonra, işlem `FinishOneGroupAsync`girene kadar bir await ifadesi tamamlanmaz. Bu nedenle, başka hiçbir işlem bu kod segmenti sırasında denetim elde edebilir.

## <a name="BKMD_SettingUpTheExample"></a>Örnek uygulamayı inceleme ve çalıştırma

Örnek uygulamayı daha iyi anlamak için indirebilir, kendiniz derleyebilir veya uygulamayı uygulamadan bu konunun sonundaki kodu inceleyebilirsiniz.

> [!NOTE]
> Örneği bir Windows Presentation Foundation (WPF) masaüstü uygulaması olarak çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.

### <a name="BKMK_DownloadingTheApp"></a>Uygulama indiriliyor

1. [Zaman uyumsuz örneklerden sıkıştırılmış dosyayı indirin: .net masaüstü uygulamalarında yeniden giriş](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).

2. İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.

3. Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin.

4. Sıkıştırması açılmış örnek kodun bulunduğu klasöre gidin ve çözüm (. sln) dosyasını açın.

5. **Çözüm Gezgini**' de, çalıştırmak istediğiniz projenin kısayol menüsünü açın ve ardından **StartupProject olarak ayarla**' yı seçin.

6. Projeyi derlemek ve çalıştırmak için CTRL + F5 tuşlarını seçin.

### <a name="BKMK_BuildingTheApp"></a>Uygulamayı oluşturma

Aşağıdaki bölümde, örneği WPF uygulaması olarak derlemek için kod sağlanmaktadır.

##### <a name="to-build-a-wpf-app"></a>WPF uygulaması derlemek için

1. Visual Studio’yu çalıştırın.

2. Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.

     **Yeni proje** iletişim kutusu açılır.

3. **Yüklü şablonlar** bölmesinde, **Visual Basic**öğesini genişletin ve ardından **Windows**' u genişletin.

4. Proje türleri listesinde **WPF uygulaması**' nı seçin.

5. Projeyi `WebsiteDownloadWPF`olarak adlandırın, .NET Framework 4,6 veya üzeri bir sürüm seçin ve **Tamam** düğmesine tıklayın.

     Yeni proje **Çözüm Gezgini**görüntülenir.

6. Visual Studio Code düzenleyicisinde **MainWindow. xaml** sekmesini seçin.

     Sekme görünür değilse, **Çözüm Gezgini**' de MainWindow. xaml için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

7. MainWindow. xaml ' nin **xaml** görünümünde, kodu aşağıdaki kodla değiştirin.

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

     Bir metin kutusu ve bir düğme içeren basit bir pencere, MainWindow. xaml **Tasarım** görünümünde görünür.

8. **Çözüm Gezgini**, **Başvurular** ' a sağ tıklayın ve **Başvuru Ekle**' yi seçin.

     Zaten seçili değilse <xref:System.Net.Http>için bir başvuru ekleyin.

9. **Çözüm Gezgini**, MainWindow. xaml. vb için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

10. MainWindow. xaml. vb dosyasında, kodu aşağıdaki kodla değiştirin.

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

11. Programı çalıştırmak için CTRL + F5 tuşlarını seçin ve sonra **Başlat** düğmesini birkaç kez seçin.

12. [Başlat düğmesini devre dışı bırak](#BKMK_DisableTheStartButton)' dan değişiklikleri yapın, [işlemi Iptal edin ve yeniden başlatın](#BKMK_CancelAndRestart)ya da [birden çok işlem çalıştırın ve çıktıyı kuyruğa](#BKMK_RunMultipleOperations) alarak yeniden giriş işlemini idare edin.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async ve await ile zaman uyumsuz programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
