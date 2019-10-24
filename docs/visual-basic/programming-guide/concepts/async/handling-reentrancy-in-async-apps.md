---
title: Zaman uyumsuz uygulamalarda yeniden girişi işleme (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
ms.openlocfilehash: 466ff3ba4cdb627143b3ffc988ae4a16348e6ca6
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775532"
---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a><span data-ttu-id="0625d-102">Zaman uyumsuz uygulamalarda yeniden girişi işleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0625d-102">Handling Reentrancy in Async Apps (Visual Basic)</span></span>

<span data-ttu-id="0625d-103">Uygulamanıza zaman uyumsuz kod eklediğinizde, işlem tamamlanmadan önce zaman uyumsuz bir işlemi yeniden girmeye işaret eden yeniden giriş yapmayı göz önünde bulundurmalı ve muhtemelen engellemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0625d-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="0625d-104">Yeniden giriş için olanaklar tanımlamazsanız ve işleyemezseniz, bu durum beklenmedik sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="0625d-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>

> [!NOTE]
> <span data-ttu-id="0625d-105">Örneği çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0625d-105">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

> [!NOTE]
> <span data-ttu-id="0625d-106">Aktarım Katmanı Güvenliği (TLS) sürüm 1,2 artık uygulama geliştirmede kullanılacak en düşük sürümdür.</span><span class="sxs-lookup"><span data-stu-id="0625d-106">Transport Layer Security (TLS) version 1.2 is now the minimum version to use in your app development.</span></span> <span data-ttu-id="0625d-107">Uygulamanız 4,7 sürümünden önceki bir .NET Framework sürümünü hedefliyorsa, lütfen [.NET Framework Aktarım Katmanı Güvenliği (TLS) en iyi uygulamaları](../../../../framework/network-programming/tls.md) için aşağıdaki makaleye bakın</span><span class="sxs-lookup"><span data-stu-id="0625d-107">If your app targets a .NET framework version earlier than 4.7, please refer to the following article for [Transport Layer Security (TLS) best practices with the .NET Framework](../../../../framework/network-programming/tls.md)</span></span> 

## <a name="BKMK_RecognizingReentrancy"></a><span data-ttu-id="0625d-108">Yeniden giriş tanıma</span><span class="sxs-lookup"><span data-stu-id="0625d-108">Recognizing Reentrancy</span></span>

<span data-ttu-id="0625d-109">Bu konudaki örnekte, kullanıcılar bir dizi Web sitesini indiren ve indirilen toplam bayt sayısını hesaplayan bir zaman uyumsuz uygulamayı başlatmak için bir **Başlat** düğmesi seçer.</span><span class="sxs-lookup"><span data-stu-id="0625d-109">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="0625d-110">Örneğin zaman uyumlu bir sürümü, bir kullanıcının düğmeyi kaç kez seçtiğinden bağımsız olarak aynı şekilde yanıt verir, çünkü ilk kez sonra, uygulama çalışmaya bitene kadar UI iş parçacığı bu olayları yoksayar.</span><span class="sxs-lookup"><span data-stu-id="0625d-110">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="0625d-111">Ancak zaman uyumsuz bir uygulamada, UI iş parçacığı yanıt vermeye devam eder ve tamamlanmadan önce zaman uyumsuz işlemi yeniden girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0625d-111">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>

<span data-ttu-id="0625d-112">Aşağıdaki örnek, Kullanıcı **Başlat** düğmesini yalnızca bir kez seçerse beklenen çıktıyı gösterir.</span><span class="sxs-lookup"><span data-stu-id="0625d-112">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="0625d-113">İndirilen Web sitelerinin listesi, her sitenin bayt cinsinden boyutu ile görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0625d-113">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="0625d-114">Toplam bayt sayısı sonda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0625d-114">The total number of bytes appears at the end.</span></span>

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

<span data-ttu-id="0625d-115">Ancak Kullanıcı düğmeyi birden çok kez seçerse, olay işleyicisi sürekli olarak çağrılır ve yükleme işlemi her seferinde yeniden girilir.</span><span class="sxs-lookup"><span data-stu-id="0625d-115">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="0625d-116">Sonuç olarak, birkaç zaman uyumsuz işlem aynı anda çalışır, çıkış sonuçları birbirine bırakır ve toplam bayt sayısı kafa karıştırıcı olur.</span><span class="sxs-lookup"><span data-stu-id="0625d-116">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>

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

<span data-ttu-id="0625d-117">Bu çıkışın sonuna kadar kayarak bu çıktıyı üreten kodu gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0625d-117">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="0625d-118">Çözümü yerel bilgisayarınıza indirerek ve ardından WebsiteDownload projesini çalıştırarak veya daha fazla bilgi ve yönergeler Için kendi projenizi oluşturmak üzere bu konunun sonundaki kodu kullanarak kodu deneyebilirsiniz. bkz. [İnceleme ve Örnek uygulamayı çalıştırma](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="0625d-118">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project For more information and instructions, see [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span>

## <a name="BKMK_HandlingReentrancy"></a><span data-ttu-id="0625d-119">Yeniden giriş işleme</span><span class="sxs-lookup"><span data-stu-id="0625d-119">Handling Reentrancy</span></span>

<span data-ttu-id="0625d-120">Uygulamanızın ne yaptığını istediğinize bağlı olarak çeşitli yollarla yeniden giriş gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0625d-120">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="0625d-121">Bu konu aşağıdaki örnekleri sunmaktadır:</span><span class="sxs-lookup"><span data-stu-id="0625d-121">This topic presents the following examples:</span></span>

- [<span data-ttu-id="0625d-122">Başlat düğmesini devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="0625d-122">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)

  <span data-ttu-id="0625d-123">İşlem çalışırken kullanıcının kesintiye uğramaması için **Başlat** düğmesini devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="0625d-123">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>

- [<span data-ttu-id="0625d-124">Işlemi iptal edin ve yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="0625d-124">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)

  <span data-ttu-id="0625d-125">Kullanıcı **Başlat** düğmesini yeniden seçtiğinde çalışmaya devam eden tüm işlemleri iptal edin ve son istenen işlemin devam etmesine izin verin.</span><span class="sxs-lookup"><span data-stu-id="0625d-125">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>

- [<span data-ttu-id="0625d-126">Birden çok Işlemi çalıştırma ve çıktıyı sıraya alma</span><span class="sxs-lookup"><span data-stu-id="0625d-126">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)

  <span data-ttu-id="0625d-127">Tüm istenen işlemlerin zaman uyumsuz olarak çalışmasına izin verin, ancak her bir işlemin sonuçlarının bir arada ve sırayla görünmesi için çıktının görüntülenmesini koordine edin.</span><span class="sxs-lookup"><span data-stu-id="0625d-127">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>

### <a name="BKMK_DisableTheStartButton"></a><span data-ttu-id="0625d-128">Başlat düğmesini devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="0625d-128">Disable the Start Button</span></span>

<span data-ttu-id="0625d-129">`StartButton_Click` olay işleyicisinin en üstündeki düğmeyi devre dışı bırakarak, bir işlem çalışırken **Başlat** düğmesini engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0625d-129">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="0625d-130">Böylece, kullanıcılar uygulamayı yeniden çalıştırabilmeleri için işlem bittiğinde düğmeyi bir `Finally` bloğu içinden yeniden etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0625d-130">You can then reenable the button from within a  `Finally` block when the operation finishes so that users can run the app again.</span></span>

<span data-ttu-id="0625d-131">Aşağıdaki kod, yıldız işaretiyle işaretlenen bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="0625d-131">The following code shows these changes, which are marked with asterisks.</span></span> <span data-ttu-id="0625d-132">Bu konunun sonundaki koda değişiklikleri ekleyebilir veya tamamlanmış uygulamayı [zaman uyumsuz örneklerden indirebilirsiniz: .net masaüstü uygulamalarında yeniden giriş](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0625d-132">You can add the changes to the code at the end of this topic, or you can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="0625d-133">Proje adı DisableStartButton ' dir.</span><span class="sxs-lookup"><span data-stu-id="0625d-133">The project name is DisableStartButton.</span></span>

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

<span data-ttu-id="0625d-134">Değişikliklerin bir sonucu olarak, `AccessTheWebAsync` Web sitelerini indirirken işlem yeniden girilemez.</span><span class="sxs-lookup"><span data-stu-id="0625d-134">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>

### <a name="BKMK_CancelAndRestart"></a><span data-ttu-id="0625d-135">Işlemi iptal edin ve yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="0625d-135">Cancel and Restart the Operation</span></span>

<span data-ttu-id="0625d-136">**Başlat** düğmesini devre dışı bırakmak yerine düğmeyi etkin tutabilirsiniz, ancak kullanıcı bu düğmeyi yeniden seçerse, zaten çalışmakta olan işlemi iptal edin ve en son başlatılan işlemin devam etmesine izin verin.</span><span class="sxs-lookup"><span data-stu-id="0625d-136">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>

<span data-ttu-id="0625d-137">İptal hakkında daha fazla bilgi için bkz. [zaman uyumsuz uygulamanızda Ince ayar yapma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="0625d-137">For more information about cancellation, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>

<span data-ttu-id="0625d-138">Bu senaryoyu ayarlamak için, [Örnek uygulamayı gözden geçirmek ve çalıştırmak](#BKMD_SettingUpTheExample)için belirtilen temel kodda aşağıdaki değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="0625d-138">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="0625d-139">Ayrıca, tamamlanmış uygulamayı [zaman uyumsuz örneklerden indirebilirsiniz: .net masaüstü uygulamalarında yeniden giriş](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0625d-139">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="0625d-140">Bu projenin adı, yeniden başlatma.</span><span class="sxs-lookup"><span data-stu-id="0625d-140">The name of this project is CancelAndRestart.</span></span>

1. <span data-ttu-id="0625d-141">Tüm yöntemler için kapsam içindeki bir <xref:System.Threading.CancellationTokenSource> değişken `cts` bildirin.</span><span class="sxs-lookup"><span data-stu-id="0625d-141">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>

    ```vb
    Class MainWindow // Or Class MainPage

        ' *** Declare a System.Threading.CancellationTokenSource.
        Dim cts As CancellationTokenSource
    ```

2. <span data-ttu-id="0625d-142">`StartButton_Click`, bir işlemin zaten devam edilip edilmeyeceğini saptayın.</span><span class="sxs-lookup"><span data-stu-id="0625d-142">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="0625d-143">`cts` değeri `Nothing`ise, hiçbir işlem zaten etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="0625d-143">If the value of `cts` is `Nothing`, no operation is already active.</span></span> <span data-ttu-id="0625d-144">Değer `Nothing`değilse, zaten çalışmakta olan işlem iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="0625d-144">If the value isn't `Nothing`, the operation that is already running is canceled.</span></span>

    ```vb
    ' *** If a download process is already underway, cancel it.
    If cts IsNot Nothing Then
        cts.Cancel()
    End If
    ```

3. <span data-ttu-id="0625d-145">@No__t_0 geçerli işlemi temsil eden farklı bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0625d-145">Set `cts` to a different value that represents the current process.</span></span>

    ```vb
    ' *** Now set cts to cancel the current process if the button is chosen again.
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()
    cts = newCTS
    ```

4. <span data-ttu-id="0625d-146">`StartButton_Click`sonunda geçerli işlem tamamlanmıştır, bu nedenle `cts` değerini `Nothing`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0625d-146">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to `Nothing`.</span></span>

    ```vb
    ' *** When the process completes, signal that another process can proceed.
    If cts Is newCTS Then
        cts = Nothing
    End If
    ```

<span data-ttu-id="0625d-147">Aşağıdaki kod `StartButton_Click`tüm değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="0625d-147">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="0625d-148">Ekler yıldız işaretiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="0625d-148">The additions are marked with asterisks.</span></span>

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

<span data-ttu-id="0625d-149">@No__t_0, aşağıdaki değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="0625d-149">In `AccessTheWebAsync`, make the following changes.</span></span>

- <span data-ttu-id="0625d-150">`StartButton_Click`iptal belirtecini kabul etmek için bir parametre ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0625d-150">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>

- <span data-ttu-id="0625d-151">`GetAsync` bir <xref:System.Threading.CancellationToken> bağımsız değişkenini kabul ettiğinden Web sitelerini indirmek için <xref:System.Net.Http.HttpClient.GetAsync%2A> yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="0625d-151">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>

- <span data-ttu-id="0625d-152">İndirilen her Web sitesinin sonuçlarını göstermek için `DisplayResults` çağrılmadan önce, geçerli işlemin iptal edildiğini doğrulamak için `ct` denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0625d-152">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>

 <span data-ttu-id="0625d-153">Aşağıdaki kod, yıldız işaretiyle işaretlenen bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="0625d-153">The following code shows these changes, which are marked with asterisks.</span></span>

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

<span data-ttu-id="0625d-154">Bu uygulama çalışırken **Başlat** düğmesini birkaç kez seçerseniz, aşağıdaki çıktıya benzeyen sonuçlar üretmelidir:</span><span class="sxs-lookup"><span data-stu-id="0625d-154">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output:</span></span>

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

<span data-ttu-id="0625d-155">Kısmi listeleri ortadan kaldırmak için, kullanıcının işlemi her yeniden başlattığı her seferinde metin kutusunu temizlemek üzere `StartButton_Click` içindeki ilk kod satırının açıklamasını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="0625d-155">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>

### <a name="BKMK_RunMultipleOperations"></a><span data-ttu-id="0625d-156">Birden çok Işlemi çalıştırma ve çıktıyı sıraya alma</span><span class="sxs-lookup"><span data-stu-id="0625d-156">Run Multiple Operations and Queue the Output</span></span>

<span data-ttu-id="0625d-157">Bu üçüncü örnek, Kullanıcı **Başlat** düğmesini her seçtiğinde uygulamanın başka bir zaman uyumsuz işlem başlatması ve tüm işlemlerin tamamlamada çalışması için en karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="0625d-157">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="0625d-158">Tüm istenen işlemler, listeden zaman uyumsuz olarak Web sitelerini indirir, ancak işlemlerden alınan çıkış sıralı olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="0625d-158">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="0625d-159">Diğer bir deyişle, gerçek indirme etkinliği araya eklemeli, bu da bir yandan [yeniden](#BKMK_RecognizingReentrancy) giriş, ancak her grup için sonuçların listesi ayrı olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="0625d-159">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](#BKMK_RecognizingReentrancy) shows, but the list of results for each group is presented separately.</span></span>

<span data-ttu-id="0625d-160">İşlemler, görüntüleme işlemi için bir ağ geçidi denetleyicisi görevi gören küresel bir <xref:System.Threading.Tasks.Task> `pendingWork` paylaşır.</span><span class="sxs-lookup"><span data-stu-id="0625d-160">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>

<span data-ttu-id="0625d-161">Değişiklikleri [uygulamayı oluşturma](#BKMK_BuildingTheApp)bölümünde koda yapıştırarak bu örneği çalıştırabilir veya örneği Indirmek Için [uygulamayı indirme](#BKMK_DownloadingTheApp) bölümündeki yönergeleri izleyerek örneği indirip queueresults projesini çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0625d-161">You can run this example by pasting the changes into the code in [Building the App](#BKMK_BuildingTheApp), or you can follow the instructions in [Downloading the App](#BKMK_DownloadingTheApp) to download the sample and then run the QueueResults project.</span></span>

<span data-ttu-id="0625d-162">Aşağıdaki çıktıda, Kullanıcı **Başlat** düğmesini yalnızca bir kez seçerse sonuç gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0625d-162">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="0625d-163">Harf etiketi,, sonucun **Başlangıç** düğmesinin seçildiği ilk sefer olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0625d-163">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="0625d-164">Sayılar, indirme hedefleri listesindeki URL 'lerin sırasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0625d-164">The numbers show the order of the URLs in the list of download targets.</span></span>

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

<span data-ttu-id="0625d-165">Kullanıcı **Başlat** düğmesini üç kez seçerse, uygulama aşağıdaki satırlara benzer bir çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="0625d-165">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="0625d-166">Numara işareti (#) ile başlayan bilgi satırları, uygulamanın ilerlemesini izler.</span><span class="sxs-lookup"><span data-stu-id="0625d-166">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>

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

<span data-ttu-id="0625d-167">Grup A tamamlanmadan önce B ve C grupları başlar, ancak her grubun çıktısı ayrı olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="0625d-167">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="0625d-168">Önce Grup A 'nın tüm çıktıları, ardından Grup B için tüm çıktılar ve sonra Grup C için tüm çıktılar görüntülenir. Uygulama her zaman grupları sırayla görüntüler ve her grup için her zaman tek tek Web siteleri hakkındaki bilgileri URL 'Ler listesinde görünecek şekilde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0625d-168">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>

<span data-ttu-id="0625d-169">Ancak, indirmelerin gerçekten gerçekleştiği sırayı tahmin edemezseniz.</span><span class="sxs-lookup"><span data-stu-id="0625d-169">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="0625d-170">Birden çok grup başlatıldıktan sonra, oluşturdukları yükleme görevlerinin hepsi etkindir.</span><span class="sxs-lookup"><span data-stu-id="0625d-170">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="0625d-171">-1 ' in B-1 ' den önce indirileceğini varsaymazsınız ve-1 ' in-2 ' den önce indirildiğini varsaymazsınız.</span><span class="sxs-lookup"><span data-stu-id="0625d-171">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>

#### <a name="global-definitions"></a><span data-ttu-id="0625d-172">Genel tanımlar</span><span class="sxs-lookup"><span data-stu-id="0625d-172">Global Definitions</span></span>

<span data-ttu-id="0625d-173">Örnek kod, tüm metotlardan görülebilen aşağıdaki iki genel bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="0625d-173">The sample code contains the following two global declarations that are visible from all methods.</span></span>

```vb
Class MainWindow    ' Class MainPage in Windows Store app.

    ' ***Declare the following variables where all methods can access them.
    Private pendingWork As Task = Nothing
    Private group As Char = ChrW(AscW("A") - 1)
```

<span data-ttu-id="0625d-174">@No__t_0 değişkeni, `pendingWork`, görüntüleme sürecini fazla görür ve herhangi bir grubun başka bir grubun görüntüleme işlemini kesintiye uğramasını önler.</span><span class="sxs-lookup"><span data-stu-id="0625d-174">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="0625d-175">@No__t_0 karakter değişkeni, sonuçların beklenen sırada göründüğünü doğrulamak için farklı gruplardan çıktıyı Etiketler.</span><span class="sxs-lookup"><span data-stu-id="0625d-175">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>

#### <a name="the-click-event-handler"></a><span data-ttu-id="0625d-176">Click olay Işleyicisi</span><span class="sxs-lookup"><span data-stu-id="0625d-176">The Click Event Handler</span></span>

<span data-ttu-id="0625d-177">`StartButton_Click`olay işleyicisi, Kullanıcı **Başlat** düğmesini her seçtiğinde grup harfini artırır.</span><span class="sxs-lookup"><span data-stu-id="0625d-177">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="0625d-178">Ardından işleyici, indirme işlemini çalıştırmak için `AccessTheWebAsync` çağırır.</span><span class="sxs-lookup"><span data-stu-id="0625d-178">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>

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

#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="0625d-179">AccessTheWebAsync yöntemi</span><span class="sxs-lookup"><span data-stu-id="0625d-179">The AccessTheWebAsync Method</span></span>

<span data-ttu-id="0625d-180">Bu örnek `AccessTheWebAsync` iki yönteme ayırır.</span><span class="sxs-lookup"><span data-stu-id="0625d-180">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="0625d-181">İlk yöntem `AccessTheWebAsync`, bir grup için tüm indirme görevlerini başlatır ve görüntüleme işlemini denetlemek için `pendingWork` ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0625d-181">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="0625d-182">Yöntemi, aynı anda tüm indirme görevlerini başlatmak için bir dil tümleşik sorgu (LINQ sorgusu) ve <xref:System.Linq.Enumerable.ToArray%2A> kullanır.</span><span class="sxs-lookup"><span data-stu-id="0625d-182">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>

<span data-ttu-id="0625d-183">`AccessTheWebAsync`, her indirmenin tamamlanmasını beklemek için `FinishOneGroupAsync` çağırır ve uzunluğunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0625d-183">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>

<span data-ttu-id="0625d-184">`FinishOneGroupAsync`, `AccessTheWebAsync` `pendingWork` atanan bir görevi döndürür.</span><span class="sxs-lookup"><span data-stu-id="0625d-184">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="0625d-185">Bu değer, görev tamamlanmadan önce başka bir işlem kesintiye uğramasını önler.</span><span class="sxs-lookup"><span data-stu-id="0625d-185">That value prevents interruption by another operation before the task is complete.</span></span>

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

#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="0625d-186">FinishOneGroupAsync yöntemi</span><span class="sxs-lookup"><span data-stu-id="0625d-186">The FinishOneGroupAsync Method</span></span>

<span data-ttu-id="0625d-187">Bu yöntem bir gruptaki indirme görevleri boyunca geçiş yapar, her birini bekliyor, indirilen Web sitesinin uzunluğunu görüntülüyor ve uzunluğu toplamına ekliyor.</span><span class="sxs-lookup"><span data-stu-id="0625d-187">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>

<span data-ttu-id="0625d-188">@No__t_0 ilk ifade, yöntemi girerken, zaten görüntüleme işleminde olan veya zaten bekleyen bir işlemi etkilemediğinden emin olmak için `pendingWork` kullanır.</span><span class="sxs-lookup"><span data-stu-id="0625d-188">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="0625d-189">Bu tür bir işlem devam ediyorsa, giriş işleminin tamamlanmasını beklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0625d-189">If such an operation is in progress, the entering operation must wait its turn.</span></span>

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

<span data-ttu-id="0625d-190">Bu örneği, [uygulamayı oluştururken](#BKMK_BuildingTheApp)koda değişiklikleri yapıştırarak çalıştırabilir veya örneği Indirmek Için [uygulamayı indirme](#BKMK_DownloadingTheApp) bölümündeki yönergeleri izleyerek örneği indirip queueresults projesini çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0625d-190">You can run this example by pasting the changes into the code in [Building the App](#BKMK_BuildingTheApp), or you can follow the instructions in [Downloading the App](#BKMK_DownloadingTheApp) to download the sample, and then run the QueueResults project.</span></span>

#### <a name="points-of-interest"></a><span data-ttu-id="0625d-191">Ilgi çekici noktaları</span><span class="sxs-lookup"><span data-stu-id="0625d-191">Points of Interest</span></span>

<span data-ttu-id="0625d-192">Çıktıda diyez işareti (#) ile başlayan bilgi satırları bu örneğin nasıl çalıştığını açıklığa kavuşturacak.</span><span class="sxs-lookup"><span data-stu-id="0625d-192">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>

<span data-ttu-id="0625d-193">Çıktıda aşağıdaki desenler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0625d-193">The output shows the following patterns.</span></span>

- <span data-ttu-id="0625d-194">Bir grup, önceki bir grup çıktısını görüntülerken başlatılabilir, ancak önceki grubun çıktısının görüntülenmediği kesintiye uğramaz.</span><span class="sxs-lookup"><span data-stu-id="0625d-194">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>

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

- <span data-ttu-id="0625d-195">`pendingWork` görevi, yalnızca ilk başlatılan A grubu için `FinishOneGroupAsync` başlangıcında `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="0625d-195">The `pendingWork` task is `Nothing` at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="0625d-196">A grubu `FinishOneGroupAsync` ulaştığında bir await ifadesi henüz tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="0625d-196">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="0625d-197">Bu nedenle, denetim `AccessTheWebAsync` döndürülmemiştir ve `pendingWork` ilk atama gerçekleşmemiştir.</span><span class="sxs-lookup"><span data-stu-id="0625d-197">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>

- <span data-ttu-id="0625d-198">Aşağıdaki iki satır, her zaman çıktıda birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0625d-198">The following two lines always appear together in the output.</span></span> <span data-ttu-id="0625d-199">Kod, `StartButton_Click` bir grubun işlemini başlatma ve grup için bir görevin `pendingWork`atama arasında hiçbir şekilde kesintiye uğramaz.</span><span class="sxs-lookup"><span data-stu-id="0625d-199">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>

  ```console
  #Starting group B.
  #Task assigned for group B. Download tasks are active.
  ```

  <span data-ttu-id="0625d-200">Bir grup `StartButton_Click`girdikten sonra, işlem `FinishOneGroupAsync`girene kadar bir await ifadesi tamamlanmaz.</span><span class="sxs-lookup"><span data-stu-id="0625d-200">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="0625d-201">Bu nedenle, başka hiçbir işlem bu kod segmenti sırasında denetim elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="0625d-201">Therefore, no other operation can gain control during that segment of code.</span></span>

## <a name="BKMD_SettingUpTheExample"></a><span data-ttu-id="0625d-202">Örnek uygulamayı inceleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="0625d-202">Reviewing and Running the Example App</span></span>

<span data-ttu-id="0625d-203">Örnek uygulamayı daha iyi anlamak için indirebilir, kendiniz derleyebilir veya uygulamayı uygulamadan bu konunun sonundaki kodu inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0625d-203">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>

> [!NOTE]
> <span data-ttu-id="0625d-204">Örneği bir Windows Presentation Foundation (WPF) masaüstü uygulaması olarak çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0625d-204">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="BKMK_DownloadingTheApp"></a><span data-ttu-id="0625d-205">Uygulama indiriliyor</span><span class="sxs-lookup"><span data-stu-id="0625d-205">Downloading the App</span></span>

1. <span data-ttu-id="0625d-206">[Zaman uyumsuz örneklerden sıkıştırılmış dosyayı indirin: .net masaüstü uygulamalarında yeniden giriş](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="0625d-206">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span>

2. <span data-ttu-id="0625d-207">İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="0625d-207">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

3. <span data-ttu-id="0625d-208">Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="0625d-208">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

4. <span data-ttu-id="0625d-209">Sıkıştırması açılmış örnek kodun bulunduğu klasöre gidin ve çözüm (. sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="0625d-209">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>

5. <span data-ttu-id="0625d-210">**Çözüm Gezgini**' de, çalıştırmak istediğiniz projenin kısayol menüsünü açın ve ardından **StartupProject olarak ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="0625d-210">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>

6. <span data-ttu-id="0625d-211">Projeyi derlemek ve çalıştırmak için CTRL + F5 tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="0625d-211">Choose the CTRL+F5 keys to build and run the project.</span></span>

### <a name="BKMK_BuildingTheApp"></a><span data-ttu-id="0625d-212">Uygulamayı oluşturma</span><span class="sxs-lookup"><span data-stu-id="0625d-212">Building the App</span></span>

<span data-ttu-id="0625d-213">Aşağıdaki bölümde, örneği WPF uygulaması olarak derlemek için kod sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0625d-213">The following section provides the code to build the example as a WPF app.</span></span>

##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="0625d-214">WPF uygulaması derlemek için</span><span class="sxs-lookup"><span data-stu-id="0625d-214">To build a WPF app</span></span>

1. <span data-ttu-id="0625d-215">Visual Studio 'Yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="0625d-215">Start Visual Studio.</span></span>

2. <span data-ttu-id="0625d-216">Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0625d-216">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="0625d-217">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="0625d-217">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="0625d-218">**Yüklü şablonlar** bölmesinde, **Visual Basic**öğesini genişletin ve ardından **Windows**' u genişletin.</span><span class="sxs-lookup"><span data-stu-id="0625d-218">In the **Installed Templates** pane, expand **Visual Basic**, and then expand **Windows**.</span></span>

4. <span data-ttu-id="0625d-219">Proje türleri listesinde **WPF uygulaması**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="0625d-219">In the list of project types, choose **WPF Application**.</span></span>

5. <span data-ttu-id="0625d-220">Projeyi `WebsiteDownloadWPF` olarak adlandırın, .NET Framework 4,6 veya üzeri bir sürüm seçin ve **Tamam** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0625d-220">Name the project `WebsiteDownloadWPF`, choose .NET Framework version of 4.6 or higher and then click the **OK** button.</span></span>

     <span data-ttu-id="0625d-221">Yeni proje **Çözüm Gezgini**görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0625d-221">The new project appears in **Solution Explorer**.</span></span>

6. <span data-ttu-id="0625d-222">Visual Studio Code düzenleyicisinde **MainWindow. xaml** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0625d-222">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="0625d-223">Sekme görünür değilse, **Çözüm Gezgini**' de MainWindow. xaml için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0625d-223">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

7. <span data-ttu-id="0625d-224">MainWindow. xaml ' nin **xaml** görünümünde, kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0625d-224">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

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

     <span data-ttu-id="0625d-225">Bir metin kutusu ve bir düğme içeren basit bir pencere, MainWindow. xaml **Tasarım** görünümünde görünür.</span><span class="sxs-lookup"><span data-stu-id="0625d-225">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

8. <span data-ttu-id="0625d-226">**Çözüm Gezgini**, **Başvurular** ' a sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0625d-226">In **Solution Explorer**, right-click on **References** and select **Add Reference**.</span></span>

     <span data-ttu-id="0625d-227">Zaten seçili değilse <xref:System.Net.Http> için bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0625d-227">Add a reference for <xref:System.Net.Http>, if it is not selected already.</span></span>

9. <span data-ttu-id="0625d-228">**Çözüm Gezgini**, MainWindow. xaml. vb için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0625d-228">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

10. <span data-ttu-id="0625d-229">MainWindow. xaml. vb dosyasında, kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0625d-229">In MainWindow.xaml.vb , replace the code with the following code.</span></span>

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

11. <span data-ttu-id="0625d-230">Programı çalıştırmak için CTRL + F5 tuşlarını seçin ve sonra **Başlat** düğmesini birkaç kez seçin.</span><span class="sxs-lookup"><span data-stu-id="0625d-230">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>

12. <span data-ttu-id="0625d-231">[Başlat düğmesini devre dışı bırak](#BKMK_DisableTheStartButton)' dan değişiklikleri yapın, [işlemi Iptal edin ve yeniden başlatın](#BKMK_CancelAndRestart)ya da [birden çok işlem çalıştırın ve çıktıyı kuyruğa](#BKMK_RunMultipleOperations) alarak yeniden giriş işlemini idare edin.</span><span class="sxs-lookup"><span data-stu-id="0625d-231">Make the changes from [Disable the Start Button](#BKMK_DisableTheStartButton), [Cancel and Restart the Operation](#BKMK_CancelAndRestart), or [Run Multiple Operations and Queue the Output](#BKMK_RunMultipleOperations) to handle the reentrancy.</span></span>

## <a name="see-also"></a><span data-ttu-id="0625d-232">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0625d-232">See also</span></span>

- [<span data-ttu-id="0625d-233">İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0625d-233">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="0625d-234">Async ve await ile zaman uyumsuz programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0625d-234">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
