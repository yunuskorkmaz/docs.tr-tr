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
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a><span data-ttu-id="47ef5-102">Async Apps 'da Reentrancy Işleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47ef5-102">Handling Reentrancy in Async Apps (Visual Basic)</span></span>

<span data-ttu-id="47ef5-103">Uygulamanıza eşzamanlı kod eklediğinizde, yeniden işlem tamamlanmadan önce yeniden girmeyi ifade eden yeniden canlandırmayı düşünmelisiniz ve muhtemelen önlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="47ef5-104">Yeniden canlandırma olasılıklarını tanımlamaz ve işlemezseniz, beklenmeyen sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>

> [!NOTE]
> <span data-ttu-id="47ef5-105">Örneği çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınıza yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-105">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

> [!NOTE]
> <span data-ttu-id="47ef5-106">Aktarım Katmanı Güvenliği (TLS) sürüm 1.2 artık uygulama geliştirmenizde kullanılacak minimum sürümdür.</span><span class="sxs-lookup"><span data-stu-id="47ef5-106">Transport Layer Security (TLS) version 1.2 is now the minimum version to use in your app development.</span></span> <span data-ttu-id="47ef5-107">Uygulamanız 4,7'den önce bir .NET Framework sürümünü hedefliyorsa, .NET Framework ile birlikte [Taşıma Katmanı Güvenliği (TLS) en iyi uygulamaları](../../../../framework/network-programming/tls.md)için aşağıdaki makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="47ef5-107">If your app targets a .NET Framework version earlier than 4.7, refer to the following article for [Transport Layer Security (TLS) best practices with the .NET Framework](../../../../framework/network-programming/tls.md).</span></span>

## <a name="recognizing-reentrancy"></a><a name="BKMK_RecognizingReentrancy"></a><span data-ttu-id="47ef5-108">Reentrancy Tanıma</span><span class="sxs-lookup"><span data-stu-id="47ef5-108">Recognizing Reentrancy</span></span>

<span data-ttu-id="47ef5-109">Bu konudaki örnekte, kullanıcılar bir dizi web sitesi indiren ve indirilen toplam bayt sayısını hesaplayan bir eşzamanlı uygulama başlatmak için bir **Başlat** düğmesi seçer.</span><span class="sxs-lookup"><span data-stu-id="47ef5-109">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="47ef5-110">Örneğin eşzamanlı sürümü, ilk kez kullanıcının düğmeyi kaç kez seçtiğine bakılmaksızın aynı şekilde yanıt verir, çünkü ilk kez kullanıcı işi, uygulama çalışan bitene kadar bu olayları yok sayar.</span><span class="sxs-lookup"><span data-stu-id="47ef5-110">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="47ef5-111">Ancak, bir eşzamanlı uygulamada, Kullanıcı Birsonucu iş parçacığı yanıt vermeye devam eder ve tamamlanmadan önce eşzamanlı işlemi yeniden girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47ef5-111">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>

<span data-ttu-id="47ef5-112">Aşağıdaki örnekte, kullanıcı **Başlat** düğmesini yalnızca bir kez seçerse beklenen çıktı yı gösterir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-112">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="47ef5-113">İndirilen web sitelerinin listesi, her sitenin boyutu, baytlar halinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-113">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="47ef5-114">Sonunda toplam bayt sayısı görünür.</span><span class="sxs-lookup"><span data-stu-id="47ef5-114">The total number of bytes appears at the end.</span></span>

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

<span data-ttu-id="47ef5-115">Ancak, kullanıcı düğmeyi birden çok kez seçerse, olay işleyicisi tekrar tekrar çağrılır ve indirme işlemi her seferinde yeniden girilir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-115">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="47ef5-116">Sonuç olarak, aynı anda birkaç eşzamanlı işlem yürütülür, çıktı sonuçları birbirine bırakır ve toplam bayt sayısı kafa karıştırıcıdır.</span><span class="sxs-lookup"><span data-stu-id="47ef5-116">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>

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

<span data-ttu-id="47ef5-117">Bu konunun sonuna kaydırarak bu çıktıyı üreten kodu gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47ef5-117">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="47ef5-118">Çözümü yerel bilgisayarınıza indirip ardından WebsiteDownload projesini çalıştırarak veya kendi projenizi oluşturmak için bu konunun sonundaki kodu kullanarak kodu deneyebilirsiniz Daha fazla bilgi ve talimatlar için [Örnek Uygulamayı Gözden Geçirme ve Çalıştırma](#BKMD_SettingUpTheExample)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="47ef5-118">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project For more information and instructions, see [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span>

## <a name="handling-reentrancy"></a><a name="BKMK_HandlingReentrancy"></a><span data-ttu-id="47ef5-119">Reentrancy işleme</span><span class="sxs-lookup"><span data-stu-id="47ef5-119">Handling Reentrancy</span></span>

<span data-ttu-id="47ef5-120">Uygulamanızın ne yapmasını istediğinize bağlı olarak, yeniden canlandırma işlemlerini çeşitli şekillerde işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47ef5-120">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="47ef5-121">Bu konu aşağıdaki örnekleri sunar:</span><span class="sxs-lookup"><span data-stu-id="47ef5-121">This topic presents the following examples:</span></span>

- [<span data-ttu-id="47ef5-122">Başlat Düğmesini Devre Dışı</span><span class="sxs-lookup"><span data-stu-id="47ef5-122">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)

  <span data-ttu-id="47ef5-123">İşlem çalışırken **Başlat** düğmesini devre dışı kalarak kullanıcı nın sözünü kesemeyecek şekilde devre dışı edin.</span><span class="sxs-lookup"><span data-stu-id="47ef5-123">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>

- [<span data-ttu-id="47ef5-124">İşlemi İptal Etme ve Yeniden Başlatma</span><span class="sxs-lookup"><span data-stu-id="47ef5-124">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)

  <span data-ttu-id="47ef5-125">Kullanıcı **Başlat** düğmesini yeniden seçtiğinde çalışmaya devam eden tüm işlemleri iptal edin ve en son istenen işlemin devam etmesine izin verin.</span><span class="sxs-lookup"><span data-stu-id="47ef5-125">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>

- [<span data-ttu-id="47ef5-126">Birden Çok İşlem çalıştırın ve Çıktıyı Sıraya</span><span class="sxs-lookup"><span data-stu-id="47ef5-126">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)

  <span data-ttu-id="47ef5-127">İstenen tüm işlemlerin eşzamanlı olarak çalışmasına izin verin, ancak her işlemden elde edilen sonuçların birlikte ve sırayla görünmesi için çıktının görüntülenmesini koordine edin.</span><span class="sxs-lookup"><span data-stu-id="47ef5-127">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>

### <a name="disable-the-start-button"></a><a name="BKMK_DisableTheStartButton"></a><span data-ttu-id="47ef5-128">Başlat Düğmesini Devre Dışı</span><span class="sxs-lookup"><span data-stu-id="47ef5-128">Disable the Start Button</span></span>

<span data-ttu-id="47ef5-129">Olay işleyicisinin üst kısmındaki düğmeyi devre dışı bırakarak işlem çalışırken Başlat düğmesini engelleyebilirsiniz. **Start** `StartButton_Click`</span><span class="sxs-lookup"><span data-stu-id="47ef5-129">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="47ef5-130">Daha sonra, işlem bittiğinde düğmeyi bir `Finally` blok içinden yeniden etkinleştirebilirsiniz, böylece kullanıcılar uygulamayı yeniden çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-130">You can then reenable the button from within a  `Finally` block when the operation finishes so that users can run the app again.</span></span>

<span data-ttu-id="47ef5-131">Aşağıdaki kod, yıldız işaretleriyle işaretlenmiş bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-131">The following code shows these changes, which are marked with asterisks.</span></span> <span data-ttu-id="47ef5-132">Bu konunun sonunda koda değişiklikleri ekleyebilirsiniz veya bitmiş uygulamayı [Async Samples: Reentrancy in .NET Desktop Apps'tan](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47ef5-132">You can add the changes to the code at the end of this topic, or you can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="47ef5-133">Proje adı DisableStartButton'dur.</span><span class="sxs-lookup"><span data-stu-id="47ef5-133">The project name is DisableStartButton.</span></span>

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

<span data-ttu-id="47ef5-134">Değişikliklerin bir sonucu olarak, düğme web sitelerini indirirken `AccessTheWebAsync` yanıt vermez, bu nedenle işlem yeniden girilemez.</span><span class="sxs-lookup"><span data-stu-id="47ef5-134">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>

### <a name="cancel-and-restart-the-operation"></a><a name="BKMK_CancelAndRestart"></a><span data-ttu-id="47ef5-135">İşlemi İptal Etme ve Yeniden Başlatma</span><span class="sxs-lookup"><span data-stu-id="47ef5-135">Cancel and Restart the Operation</span></span>

<span data-ttu-id="47ef5-136">**Başlat** düğmesini devre dışı bırakmak yerine düğmeyi etkin tutabilirsiniz, ancak kullanıcı bu düğmeyi tekrar seçerse, zaten çalışan işlemi iptal edin ve en son başlatılan işlemin devam etmesine izin verin.</span><span class="sxs-lookup"><span data-stu-id="47ef5-136">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>

<span data-ttu-id="47ef5-137">İptal hakkında daha fazla bilgi için [Async Uygulamanızı (Visual Basic) İnce Ayarla'ya](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="47ef5-137">For more information about cancellation, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>

<span data-ttu-id="47ef5-138">Bu senaryoyu ayarlamak için, Örnek Uygulamayı Gözden Geçirme [ve Çalıştırma'da](#BKMD_SettingUpTheExample)sağlanan temel kodda aşağıdaki değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="47ef5-138">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="47ef5-139">Ayrıca bitmiş uygulamayı [Async Samples: Reentrancy in .NET Desktop Apps'tan](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)da indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47ef5-139">You can also download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="47ef5-140">Bu projenin adı CancelAndRestart olduğunu.</span><span class="sxs-lookup"><span data-stu-id="47ef5-140">The name of this project is CancelAndRestart.</span></span>

1. <span data-ttu-id="47ef5-141">Tüm <xref:System.Threading.CancellationTokenSource> yöntemler `cts`için kapsamda olan bir değişken bildirin.</span><span class="sxs-lookup"><span data-stu-id="47ef5-141">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>

    ```vb
    Class MainWindow // Or Class MainPage

        ' *** Declare a System.Threading.CancellationTokenSource.
        Dim cts As CancellationTokenSource
    ```

2. <span data-ttu-id="47ef5-142">In `StartButton_Click`, bir işlemin devam edip etmediğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="47ef5-142">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="47ef5-143">Değeri `cts` ise, `Nothing`hiçbir işlem zaten etkindir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-143">If the value of `cts` is `Nothing`, no operation is already active.</span></span> <span data-ttu-id="47ef5-144">Değer `Nothing`değilse, zaten çalışan işlem iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-144">If the value isn't `Nothing`, the operation that is already running is canceled.</span></span>

    ```vb
    ' *** If a download process is already underway, cancel it.
    If cts IsNot Nothing Then
        cts.Cancel()
    End If
    ```

3. <span data-ttu-id="47ef5-145">`cts` Geçerli işlemi temsil eden farklı bir değerayarlayın.</span><span class="sxs-lookup"><span data-stu-id="47ef5-145">Set `cts` to a different value that represents the current process.</span></span>

    ```vb
    ' *** Now set cts to cancel the current process if the button is chosen again.
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()
    cts = newCTS
    ```

4. <span data-ttu-id="47ef5-146">`StartButton_Click`Sonunda, geçerli işlem tamamlandı, bu yüzden `cts` geri değerini `Nothing`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="47ef5-146">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to `Nothing`.</span></span>

    ```vb
    ' *** When the process completes, signal that another process can proceed.
    If cts Is newCTS Then
        cts = Nothing
    End If
    ```

<span data-ttu-id="47ef5-147">Aşağıdaki kod' daki tüm `StartButton_Click`değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-147">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="47ef5-148">Eklemeler yıldız işaretleri ile işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-148">The additions are marked with asterisks.</span></span>

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

<span data-ttu-id="47ef5-149">In `AccessTheWebAsync`, aşağıdaki değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="47ef5-149">In `AccessTheWebAsync`, make the following changes.</span></span>

- <span data-ttu-id="47ef5-150">'den `StartButton_Click`iptal belirteci kabul etmek için bir parametre ekleyin.</span><span class="sxs-lookup"><span data-stu-id="47ef5-150">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>

- <span data-ttu-id="47ef5-151">Bir <xref:System.Threading.CancellationToken> <xref:System.Net.Http.HttpClient.GetAsync%2A> bağımsız `GetAsync` değişkenkabul ettiği için web sitelerini indirmek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="47ef5-151">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>

- <span data-ttu-id="47ef5-152">İndirilen her web sitesinin sonuçlarını görüntülemek için aramadan `DisplayResults` önce, geçerli işlemin iptal edilmediğini kontrol edin. `ct`</span><span class="sxs-lookup"><span data-stu-id="47ef5-152">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>

 <span data-ttu-id="47ef5-153">Aşağıdaki kod, yıldız işaretleriyle işaretlenmiş bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-153">The following code shows these changes, which are marked with asterisks.</span></span>

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

<span data-ttu-id="47ef5-154">Bu uygulama çalışırken **Başlat** düğmesini birkaç kez seçerseniz, aşağıdaki çıktıya benzeyen sonuçlar üretmelidir:</span><span class="sxs-lookup"><span data-stu-id="47ef5-154">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output:</span></span>

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

<span data-ttu-id="47ef5-155">Kısmi listeleri ortadan kaldırmak `StartButton_Click` için, kullanıcı işlemi her yeniden başlattığında metin kutusunu temizlemek için ilk kod satırının yorumunu kaldırın.</span><span class="sxs-lookup"><span data-stu-id="47ef5-155">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>

### <a name="run-multiple-operations-and-queue-the-output"></a><a name="BKMK_RunMultipleOperations"></a><span data-ttu-id="47ef5-156">Birden Çok İşlem çalıştırın ve Çıktıyı Sıraya</span><span class="sxs-lookup"><span data-stu-id="47ef5-156">Run Multiple Operations and Queue the Output</span></span>

<span data-ttu-id="47ef5-157">Bu üçüncü örnek, uygulamanın **kullanıcının Başlat** düğmesini her seçtiğinde başka bir eşzamanlı işlem başlatması ve tüm işlemlerin tamamlanması için çalıştırılması açısından en karmaşık örnektir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-157">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="47ef5-158">İstenen tüm işlemler listedeki web sitelerini eşit olarak indirir, ancak işlemlerden elde edilen çıktı sırayla sunulur.</span><span class="sxs-lookup"><span data-stu-id="47ef5-158">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="47ef5-159">Diğer bir deyişle, [Reentrancy'yi Tanıma'daki](#BKMK_RecognizingReentrancy) çıktının gösterdiği gibi, gerçek indirme etkinliği birbiriyle bağlantılıdır, ancak her grubun sonuç listesi ayrı olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="47ef5-159">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](#BKMK_RecognizingReentrancy) shows, but the list of results for each group is presented separately.</span></span>

<span data-ttu-id="47ef5-160">İşlemler, görüntüleme <xref:System.Threading.Tasks.Task> `pendingWork`işlemi için bir kapı bekçisi olarak hizmet veren genel bir , paylaşır.</span><span class="sxs-lookup"><span data-stu-id="47ef5-160">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>

<span data-ttu-id="47ef5-161">[Uygulamayı Oluşturma'da](#BKMK_BuildingTheApp)değişiklikleri koda yapıştırarak bu örneği çalıştırabilir veya örneği indirmek ve ardından QueueResults projesini çalıştırmak için [Uygulamayı İndirme](#BKMK_DownloadingTheApp) yönergelerini izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47ef5-161">You can run this example by pasting the changes into the code in [Building the App](#BKMK_BuildingTheApp), or you can follow the instructions in [Downloading the App](#BKMK_DownloadingTheApp) to download the sample and then run the QueueResults project.</span></span>

<span data-ttu-id="47ef5-162">Kullanıcı **Başlat** düğmesini yalnızca bir kez seçerse aşağıdaki çıktı sonucu gösterir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-162">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="47ef5-163">A harf etiketi, sonucun **Başlat** düğmesinin ilk kez seçildiği nden geldiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-163">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="47ef5-164">Sayılar, indirme hedefleri listesindeKI URL'lerin sırasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-164">The numbers show the order of the URLs in the list of download targets.</span></span>

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

<span data-ttu-id="47ef5-165">Kullanıcı **Başlat** düğmesini üç kez seçerse, uygulama aşağıdaki satırları andıran çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-165">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="47ef5-166">Pound işaretiyle başlayan bilgi satırları (#) uygulamanın ilerlemesini izler.</span><span class="sxs-lookup"><span data-stu-id="47ef5-166">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>

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

<span data-ttu-id="47ef5-167">B ve C grupları A grubu bitmeden önce başlar, ancak her grubun çıktısı ayrı ayrı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-167">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="47ef5-168">A grubu için tüm çıktı önce görünür, ardından B grubu için tüm çıktı ve ardından C grubu için tüm çıktı çıkar. Uygulama her zaman grupları sırayla görüntüler ve her grup için URL'lerin URL'leri listesinde görünmesi sırasına göre her zaman web siteleri hakkındaki bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="47ef5-168">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>

<span data-ttu-id="47ef5-169">Ancak, indirmelerin gerçekte gerçekleşme sırası tahmin edemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="47ef5-169">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="47ef5-170">Birden çok grup başlatıldıktan sonra, oluşturdukları indirme görevlerinin tümü etkin olur.</span><span class="sxs-lookup"><span data-stu-id="47ef5-170">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="47ef5-171">A-1'in B-1'den önce indirileceğini varsayamaz ve A-1'in A-2'den önce indirileceğini varsayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="47ef5-171">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>

#### <a name="global-definitions"></a><span data-ttu-id="47ef5-172">Küresel Tanımlar</span><span class="sxs-lookup"><span data-stu-id="47ef5-172">Global Definitions</span></span>

<span data-ttu-id="47ef5-173">Örnek kod, tüm yöntemlerden görülebilen aşağıdaki iki genel bildirim içerir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-173">The sample code contains the following two global declarations that are visible from all methods.</span></span>

```vb
Class MainWindow    ' Class MainPage in Windows Store app.

    ' ***Declare the following variables where all methods can access them.
    Private pendingWork As Task = Nothing
    Private group As Char = ChrW(AscW("A") - 1)
```

<span data-ttu-id="47ef5-174">Değişken, `Task` `pendingWork`görüntü işlemini denetler ve herhangi bir grubun başka bir grubun görüntüleme işlemini kesintiye uğratmasını önler.</span><span class="sxs-lookup"><span data-stu-id="47ef5-174">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="47ef5-175">Karakter değişkeni, `group`sonuçların beklenen sırada göründüğünü doğrulamak için farklı gruplardan çıktı etiketler.</span><span class="sxs-lookup"><span data-stu-id="47ef5-175">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>

#### <a name="the-click-event-handler"></a><span data-ttu-id="47ef5-176">Tıklayın Olay Handleyici</span><span class="sxs-lookup"><span data-stu-id="47ef5-176">The Click Event Handler</span></span>

<span data-ttu-id="47ef5-177">Olay işleyicisi, `StartButton_Click`kullanıcı **Başlat** düğmesini her seçtiğinde grup harfini de martılar.</span><span class="sxs-lookup"><span data-stu-id="47ef5-177">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="47ef5-178">Daha sonra işleyici indirme işlemini çalıştırmak için çağırır. `AccessTheWebAsync`</span><span class="sxs-lookup"><span data-stu-id="47ef5-178">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>

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

#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="47ef5-179">AccessThewebasync Yöntemi</span><span class="sxs-lookup"><span data-stu-id="47ef5-179">The AccessTheWebAsync Method</span></span>

<span data-ttu-id="47ef5-180">Bu örnek `AccessTheWebAsync` iki yönteme bölünür.</span><span class="sxs-lookup"><span data-stu-id="47ef5-180">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="47ef5-181">İlk yöntem, `AccessTheWebAsync`bir grup için tüm indirme görevlerini `pendingWork` başlatır ve görüntüleme işlemini denetlemek için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="47ef5-181">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="47ef5-182">Yöntem, bir Dil Tümleşik Sorgusu <xref:System.Linq.Enumerable.ToArray%2A> (LINQ sorgusu) kullanır ve tüm indirme görevlerini aynı anda başlatmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="47ef5-182">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>

<span data-ttu-id="47ef5-183">`AccessTheWebAsync`sonra `FinishOneGroupAsync` her indirme tamamlanmasını beklemek ve uzunluğunu görüntülemek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="47ef5-183">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>

<span data-ttu-id="47ef5-184">`FinishOneGroupAsync``pendingWork` 'de `AccessTheWebAsync`atanan bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="47ef5-184">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="47ef5-185">Bu değer, görev tamamlanmadan önce başka bir işlemtarafından kesintiye uğramayı önler.</span><span class="sxs-lookup"><span data-stu-id="47ef5-185">That value prevents interruption by another operation before the task is complete.</span></span>

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

#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="47ef5-186">FinishOneGroupAsync Yöntemi</span><span class="sxs-lookup"><span data-stu-id="47ef5-186">The FinishOneGroupAsync Method</span></span>

<span data-ttu-id="47ef5-187">Bu yöntem, bir gruptaki indirme görevleri arasında geçiş yapmakta, her birini bekler, indirilen web sitesinin uzunluğunu görüntüler ve uzunluğu toplama ekler.</span><span class="sxs-lookup"><span data-stu-id="47ef5-187">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>

<span data-ttu-id="47ef5-188">Yönteme girmenin zaten görüntü sürecinde olan veya zaten bekleyen bir işlemi etkilemediğinden emin olmak için `FinishOneGroupAsync` kullanılan `pendingWork` ilk deyim.</span><span class="sxs-lookup"><span data-stu-id="47ef5-188">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="47ef5-189">Böyle bir işlem devam ediyorsa, giren işlem sırasını beklemelidir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-189">If such an operation is in progress, the entering operation must wait its turn.</span></span>

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

<span data-ttu-id="47ef5-190">[Uygulamayı Oluşturma'da](#BKMK_BuildingTheApp)değişiklikleri koda yapıştırarak bu örneği çalıştırabilir veya örneği indirmek için [Uygulamayı İndirme](#BKMK_DownloadingTheApp) yönergelerini izleyebilir ve ardından QueueResults projesini çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47ef5-190">You can run this example by pasting the changes into the code in [Building the App](#BKMK_BuildingTheApp), or you can follow the instructions in [Downloading the App](#BKMK_DownloadingTheApp) to download the sample, and then run the QueueResults project.</span></span>

#### <a name="points-of-interest"></a><span data-ttu-id="47ef5-191">İlgi Çekici Noktalar</span><span class="sxs-lookup"><span data-stu-id="47ef5-191">Points of Interest</span></span>

<span data-ttu-id="47ef5-192">Çıktıdaki pound işaretiyle (#) başlayan bilgi satırları, bu örneğin nasıl çalıştığını açıklığa kavuşturur.</span><span class="sxs-lookup"><span data-stu-id="47ef5-192">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>

<span data-ttu-id="47ef5-193">Çıktı aşağıdaki desenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-193">The output shows the following patterns.</span></span>

- <span data-ttu-id="47ef5-194">Önceki bir grup çıktısını görüntülerken bir grup başlatılabilir, ancak önceki grubun çıktısının görüntülenmesi kesintiye uğramaz.</span><span class="sxs-lookup"><span data-stu-id="47ef5-194">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>

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

- <span data-ttu-id="47ef5-195">Görev, `pendingWork` `Nothing` yalnızca ilk `FinishOneGroupAsync` olarak başlayan A grubu için başlangıçtadır.</span><span class="sxs-lookup"><span data-stu-id="47ef5-195">The `pendingWork` task is `Nothing` at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="47ef5-196">A Grubu, 'ye ulaştığında `FinishOneGroupAsync`bekleyen bir ifadeyi henüz tamamlamadı.</span><span class="sxs-lookup"><span data-stu-id="47ef5-196">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="47ef5-197">Bu nedenle, denetim döndürülmedi `AccessTheWebAsync`ve ilk `pendingWork` atama gerçekleşmedi.</span><span class="sxs-lookup"><span data-stu-id="47ef5-197">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>

- <span data-ttu-id="47ef5-198">Aşağıdaki iki satır her zaman çıkışta birlikte görünür.</span><span class="sxs-lookup"><span data-stu-id="47ef5-198">The following two lines always appear together in the output.</span></span> <span data-ttu-id="47ef5-199">Kod, bir grubun çalışmasını başlatma `StartButton_Click` ile grup için bir görev atamak arasında hiçbir zaman kesintiye `pendingWork`uğramaz.</span><span class="sxs-lookup"><span data-stu-id="47ef5-199">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>

  ```console
  #Starting group B.
  #Task assigned for group B. Download tasks are active.
  ```

  <span data-ttu-id="47ef5-200">Bir grup `StartButton_Click`girdikten sonra, işlem girene `FinishOneGroupAsync`kadar bekleme ifadesini tamamlamaz.</span><span class="sxs-lookup"><span data-stu-id="47ef5-200">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="47ef5-201">Bu nedenle, kodun bu kesimi sırasında başka hiçbir işlem denetim elde edemez.</span><span class="sxs-lookup"><span data-stu-id="47ef5-201">Therefore, no other operation can gain control during that segment of code.</span></span>

## <a name="reviewing-and-running-the-example-app"></a><a name="BKMD_SettingUpTheExample"></a><span data-ttu-id="47ef5-202">Örnek Uygulamayı İnceleme ve Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="47ef5-202">Reviewing and Running the Example App</span></span>

<span data-ttu-id="47ef5-203">Örnek uygulamayı daha iyi anlamak için uygulamayı indirebilir, kendiniz oluşturabilir veya uygulamayı uygulamadan bu konunun sonundaki kodu gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47ef5-203">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>

> [!NOTE]
> <span data-ttu-id="47ef5-204">Örneği Windows Presentation Foundation (WPF) masaüstü uygulaması olarak çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınıza yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-204">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="downloading-the-app"></a><a name="BKMK_DownloadingTheApp"></a><span data-ttu-id="47ef5-205">Uygulamayı İndirme</span><span class="sxs-lookup"><span data-stu-id="47ef5-205">Downloading the App</span></span>

1. <span data-ttu-id="47ef5-206">Sıkıştırılmış dosyayı [Async Samples: Reentrancy in .NET Desktop Apps'tan](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)indirin.</span><span class="sxs-lookup"><span data-stu-id="47ef5-206">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span>

2. <span data-ttu-id="47ef5-207">İndirdiğiniz dosyayı sıkıştırın ve Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="47ef5-207">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

3. <span data-ttu-id="47ef5-208">Menü çubuğunda **Dosya**, **Aç**, **Proje/Çözüm'ü**seçin.</span><span class="sxs-lookup"><span data-stu-id="47ef5-208">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

4. <span data-ttu-id="47ef5-209">Sıkıştırılmış örnek kodu tutan klasöre gidin ve ardından çözüm (.sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="47ef5-209">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>

5. <span data-ttu-id="47ef5-210">**Çözüm Gezgini'nde,** çalıştırmak istediğiniz proje için kısayol menüsünü açın ve ardından **StartUpProject olarak ayarla'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="47ef5-210">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>

6. <span data-ttu-id="47ef5-211">Projeyi oluşturmak ve çalıştırmak için CTRL+F5 tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="47ef5-211">Choose the CTRL+F5 keys to build and run the project.</span></span>

### <a name="building-the-app"></a><a name="BKMK_BuildingTheApp"></a><span data-ttu-id="47ef5-212">Uygulamayı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="47ef5-212">Building the App</span></span>

<span data-ttu-id="47ef5-213">Aşağıdaki bölümde, örneği WPF uygulaması olarak oluşturmak için kod sağlanır.</span><span class="sxs-lookup"><span data-stu-id="47ef5-213">The following section provides the code to build the example as a WPF app.</span></span>

##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="47ef5-214">WPF uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="47ef5-214">To build a WPF app</span></span>

1. <span data-ttu-id="47ef5-215">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="47ef5-215">Start Visual Studio.</span></span>

2. <span data-ttu-id="47ef5-216">Menü çubuğunda **Dosya**, **Yeni**, **Proje'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="47ef5-216">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="47ef5-217">**Yeni Proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="47ef5-217">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="47ef5-218">Yüklü **Şablonlar** bölmesinde Visual **Basic'i**genişletin ve **ardından Windows'u**genişletin.</span><span class="sxs-lookup"><span data-stu-id="47ef5-218">In the **Installed Templates** pane, expand **Visual Basic**, and then expand **Windows**.</span></span>

4. <span data-ttu-id="47ef5-219">Proje türleri listesinde **WPF Uygulaması'nı**seçin.</span><span class="sxs-lookup"><span data-stu-id="47ef5-219">In the list of project types, choose **WPF Application**.</span></span>

5. <span data-ttu-id="47ef5-220">Projeyi `WebsiteDownloadWPF`adlandırın, 4,6 veya daha yüksek .NET Framework sürümünü seçin ve ardından **Tamam** düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="47ef5-220">Name the project `WebsiteDownloadWPF`, choose .NET Framework version of 4.6 or higher and then click the **OK** button.</span></span>

     <span data-ttu-id="47ef5-221">Yeni proje Çözüm **Gezgini'nde**görünür.</span><span class="sxs-lookup"><span data-stu-id="47ef5-221">The new project appears in **Solution Explorer**.</span></span>

6. <span data-ttu-id="47ef5-222">Visual Studio Code Editor'da **MainWindow.xaml** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="47ef5-222">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="47ef5-223">Sekme görünmüyorsa, **Solution Explorer'da**MainWindow.xaml için kısayol menüsünü açın ve ardından **Kodu Görüntüle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="47ef5-223">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

7. <span data-ttu-id="47ef5-224">MainWindow.xaml'ın **XAML** görünümünde kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="47ef5-224">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

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

     <span data-ttu-id="47ef5-225">MainWindow.xaml'ın **Tasarım** görünümünde metin kutusu ve düğme içeren basit bir pencere görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="47ef5-225">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

8. <span data-ttu-id="47ef5-226">**Çözüm Gezgini'nde,** **Başvurular'a** sağ tıklayın ve **Referans Ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="47ef5-226">In **Solution Explorer**, right-click on **References** and select **Add Reference**.</span></span>

     <span data-ttu-id="47ef5-227">Zaten seçilmemişse, için <xref:System.Net.Http>bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="47ef5-227">Add a reference for <xref:System.Net.Http>, if it is not selected already.</span></span>

9. <span data-ttu-id="47ef5-228">**Çözüm Gezgini'nde**MainWindow.xaml.vb için kısayol menüsünü açın ve ardından **Kodu Görüntüle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="47ef5-228">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

10. <span data-ttu-id="47ef5-229">MainWindow.xaml.vb'de kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="47ef5-229">In MainWindow.xaml.vb , replace the code with the following code.</span></span>

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

11. <span data-ttu-id="47ef5-230">Programı çalıştırmak için CTRL+F5 tuşlarını seçin ve ardından **Başlat** düğmesini birkaç kez seçin.</span><span class="sxs-lookup"><span data-stu-id="47ef5-230">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>

12. <span data-ttu-id="47ef5-231">[Başlat Düğmesini Devre Dışı Devre](#BKMK_DisableTheStartButton)Dışı, [İşlemi İptal Et ve Yeniden Başlat'](#BKMK_CancelAndRestart)tan değişiklikler yapın veya birden çok işlemi çalıştırın ve yeniden başlatma işlemini işlemek için [Çıktıyı](#BKMK_RunMultipleOperations) Sıralayın.</span><span class="sxs-lookup"><span data-stu-id="47ef5-231">Make the changes from [Disable the Start Button](#BKMK_DisableTheStartButton), [Cancel and Restart the Operation](#BKMK_CancelAndRestart), or [Run Multiple Operations and Queue the Output](#BKMK_RunMultipleOperations) to handle the reentrancy.</span></span>

## <a name="see-also"></a><span data-ttu-id="47ef5-232">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47ef5-232">See also</span></span>

- [<span data-ttu-id="47ef5-233">Walkthrough: Async ve Await (Visual Basic) kullanarak Web'e erişim</span><span class="sxs-lookup"><span data-stu-id="47ef5-233">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="47ef5-234">Async ve Await ile Asynchronous Programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47ef5-234">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
