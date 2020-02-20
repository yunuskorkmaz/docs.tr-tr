---
title: Zaman uyumsuz uygulamalarda yeniden girişi işleme (C#)
ms.date: 07/20/2015
ms.assetid: 47c5075e-c448-45ce-9155-ed4e7e98c677
ms.openlocfilehash: 67fbbd294ffe6219b58065f974543b2dd483a92c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451869"
---
# <a name="handling-reentrancy-in-async-apps-c"></a><span data-ttu-id="4ad1f-102">Zaman uyumsuz uygulamalarda yeniden girişi işleme (C#)</span><span class="sxs-lookup"><span data-stu-id="4ad1f-102">Handling Reentrancy in Async Apps (C#)</span></span>

<span data-ttu-id="4ad1f-103">Uygulamanıza zaman uyumsuz kod eklediğinizde, işlem tamamlanmadan önce zaman uyumsuz bir işlemi yeniden girmeye işaret eden yeniden giriş yapmayı göz önünde bulundurmalı ve muhtemelen engellemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="4ad1f-104">Yeniden giriş için olanaklar tanımlamazsanız ve işleyemezseniz, bu durum beklenmedik sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>

<span data-ttu-id="4ad1f-105">**Bu konuda**</span><span class="sxs-lookup"><span data-stu-id="4ad1f-105">**In this topic**</span></span>

- [<span data-ttu-id="4ad1f-106">Yeniden giriş tanıma</span><span class="sxs-lookup"><span data-stu-id="4ad1f-106">Recognizing Reentrancy</span></span>](#BKMK_RecognizingReentrancy)

- [<span data-ttu-id="4ad1f-107">Yeniden giriş işleme</span><span class="sxs-lookup"><span data-stu-id="4ad1f-107">Handling Reentrancy</span></span>](#BKMK_HandlingReentrancy)

  - [<span data-ttu-id="4ad1f-108">Başlat düğmesini devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="4ad1f-108">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)

  - [<span data-ttu-id="4ad1f-109">Işlemi iptal edin ve yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="4ad1f-109">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)

  - [<span data-ttu-id="4ad1f-110">Birden çok Işlemi çalıştırma ve çıktıyı sıraya alma</span><span class="sxs-lookup"><span data-stu-id="4ad1f-110">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)

- [<span data-ttu-id="4ad1f-111">Örnek uygulamayı inceleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="4ad1f-111">Reviewing and Running the Example App</span></span>](#BKMD_SettingUpTheExample)

> [!NOTE]
> <span data-ttu-id="4ad1f-112">Örneği çalıştırmak için bilgisayarınızda Visual Studio 2012 veya sonraki bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-112">To run the example, you must have Visual Studio 2012 or newer and .NET Framework 4.5 or newer installed on your computer.</span></span>

> [!NOTE]
> <span data-ttu-id="4ad1f-113">Aktarım Katmanı Güvenliği (TLS) sürüm 1,2 artık uygulama geliştirmede kullanılacak en düşük sürümdür.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-113">Transport Layer Security (TLS) version 1.2 is now the minimum version to use in your app development.</span></span> <span data-ttu-id="4ad1f-114">Uygulamanız 4,7 sürümünden önceki bir .NET Framework sürümünü hedefliyorsa [.NET Framework Aktarım Katmanı Güvenliği (TLS) en iyi uygulamaları](../../../../framework/network-programming/tls.md)için aşağıdaki makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-114">If your app targets a .NET Framework version earlier than 4.7, refer to the following article for [Transport Layer Security (TLS) best practices with the .NET Framework](../../../../framework/network-programming/tls.md).</span></span>

## <a name="BKMK_RecognizingReentrancy"></a><span data-ttu-id="4ad1f-115">Yeniden giriş tanıma</span><span class="sxs-lookup"><span data-stu-id="4ad1f-115">Recognizing Reentrancy</span></span>

<span data-ttu-id="4ad1f-116">Bu konudaki örnekte, kullanıcılar bir dizi Web sitesini indiren ve indirilen toplam bayt sayısını hesaplayan bir zaman uyumsuz uygulamayı başlatmak için bir **Başlat** düğmesi seçer.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-116">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="4ad1f-117">Örneğin zaman uyumlu bir sürümü, bir kullanıcının düğmeyi kaç kez seçtiğinden bağımsız olarak aynı şekilde yanıt verir, çünkü ilk kez sonra, uygulama çalışmaya bitene kadar UI iş parçacığı bu olayları yoksayar.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-117">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="4ad1f-118">Ancak zaman uyumsuz bir uygulamada, UI iş parçacığı yanıt vermeye devam eder ve tamamlanmadan önce zaman uyumsuz işlemi yeniden girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-118">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>

<span data-ttu-id="4ad1f-119">Aşağıdaki örnek, Kullanıcı **Başlat** düğmesini yalnızca bir kez seçerse beklenen çıktıyı gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-119">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="4ad1f-120">İndirilen Web sitelerinin listesi, her sitenin bayt cinsinden boyutu ile görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-120">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="4ad1f-121">Toplam bayt sayısı sonda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-121">The total number of bytes appears at the end.</span></span>

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

<span data-ttu-id="4ad1f-122">Ancak Kullanıcı düğmeyi birden çok kez seçerse, olay işleyicisi sürekli olarak çağrılır ve yükleme işlemi her seferinde yeniden girilir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-122">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="4ad1f-123">Sonuç olarak, birkaç zaman uyumsuz işlem aynı anda çalışır, çıkış sonuçları birbirine bırakır ve toplam bayt sayısı kafa karıştırıcı olur.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-123">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>

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

<span data-ttu-id="4ad1f-124">Bu çıkışın sonuna kadar kayarak bu çıktıyı üreten kodu gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-124">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="4ad1f-125">Çözümü yerel bilgisayarınıza indirerek ve ardından WebsiteDownload projesini çalıştırarak veya kendi projenizi oluşturmak için bu konunun sonundaki kodu kullanarak kodu deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-125">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project.</span></span> <span data-ttu-id="4ad1f-126">Daha fazla bilgi ve yönergeler için bkz. [Örnek uygulamayı inceleme ve çalıştırma](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="4ad1f-126">For more information and instructions, see [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span>

## <a name="BKMK_HandlingReentrancy"></a><span data-ttu-id="4ad1f-127">Yeniden giriş işleme</span><span class="sxs-lookup"><span data-stu-id="4ad1f-127">Handling Reentrancy</span></span>

<span data-ttu-id="4ad1f-128">Uygulamanızın ne yaptığını istediğinize bağlı olarak çeşitli yollarla yeniden giriş gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-128">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="4ad1f-129">Bu konu aşağıdaki örnekleri sunmaktadır:</span><span class="sxs-lookup"><span data-stu-id="4ad1f-129">This topic presents the following examples:</span></span>

- [<span data-ttu-id="4ad1f-130">Başlat düğmesini devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="4ad1f-130">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)

  <span data-ttu-id="4ad1f-131">İşlem çalışırken kullanıcının kesintiye uğramaması için **Başlat** düğmesini devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-131">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>

- [<span data-ttu-id="4ad1f-132">Işlemi iptal edin ve yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="4ad1f-132">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)

  <span data-ttu-id="4ad1f-133">Kullanıcı **Başlat** düğmesini yeniden seçtiğinde çalışmaya devam eden tüm işlemleri iptal edin ve son istenen işlemin devam etmesine izin verin.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-133">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>

- [<span data-ttu-id="4ad1f-134">Birden çok Işlemi çalıştırma ve çıktıyı sıraya alma</span><span class="sxs-lookup"><span data-stu-id="4ad1f-134">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)

  <span data-ttu-id="4ad1f-135">Tüm istenen işlemlerin zaman uyumsuz olarak çalışmasına izin verin, ancak her bir işlemin sonuçlarının bir arada ve sırayla görünmesi için çıktının görüntülenmesini koordine edin.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-135">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>

### <a name="BKMK_DisableTheStartButton"></a><span data-ttu-id="4ad1f-136">Başlat düğmesini devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="4ad1f-136">Disable the Start Button</span></span>

<span data-ttu-id="4ad1f-137">`StartButton_Click` olay işleyicisinin en üstündeki düğmeyi devre dışı bırakarak, bir işlem çalışırken **Başlat** düğmesini engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-137">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="4ad1f-138">Böylece, kullanıcılar uygulamayı yeniden çalıştırabilmeleri için işlem bittiğinde düğmeyi bir `finally` bloğu içinden yeniden etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-138">You can then reenable the button from within a  `finally` block when the operation finishes so that users can run the app again.</span></span>

<span data-ttu-id="4ad1f-139">Bu senaryoyu ayarlamak için, [Örnek uygulamayı gözden geçirmek ve çalıştırmak](#BKMD_SettingUpTheExample)için belirtilen temel kodda aşağıdaki değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-139">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="4ad1f-140">Ayrıca, tamamlanmış uygulamayı [zaman uyumsuz örneklerden indirebilirsiniz: .net masaüstü uygulamalarında yeniden giriş](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-140">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="4ad1f-141">Projenin adı DisableStartButton olur.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-141">The name of the project is DisableStartButton.</span></span>

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

<span data-ttu-id="4ad1f-142">Değişikliklerin bir sonucu olarak, `AccessTheWebAsync` Web sitelerini indirirken işlem yeniden girilemez.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-142">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>

### <a name="BKMK_CancelAndRestart"></a><span data-ttu-id="4ad1f-143">Işlemi iptal edin ve yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="4ad1f-143">Cancel and Restart the Operation</span></span>

<span data-ttu-id="4ad1f-144">**Başlat** düğmesini devre dışı bırakmak yerine düğmeyi etkin tutabilirsiniz, ancak kullanıcı bu düğmeyi yeniden seçerse, zaten çalışmakta olan işlemi iptal edin ve en son başlatılan işlemin devam etmesine izin verin.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-144">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>

<span data-ttu-id="4ad1f-145">İptal hakkında daha fazla bilgi için bkz. [zaman uyumsuz uygulamanızda Ince ayar yapmaC#()](./fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="4ad1f-145">For more information about cancellation, see [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md).</span></span>

<span data-ttu-id="4ad1f-146">Bu senaryoyu ayarlamak için, [Örnek uygulamayı gözden geçirmek ve çalıştırmak](#BKMD_SettingUpTheExample)için belirtilen temel kodda aşağıdaki değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-146">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="4ad1f-147">Ayrıca, tamamlanmış uygulamayı [zaman uyumsuz örneklerden indirebilirsiniz: .net masaüstü uygulamalarında yeniden giriş](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-147">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="4ad1f-148">Projenin adı, geçersiz bir şekilde başlatılır.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-148">The name of the project is CancelAndRestart.</span></span>

1. <span data-ttu-id="4ad1f-149">Tüm yöntemler için kapsam içindeki bir <xref:System.Threading.CancellationTokenSource> değişken `cts`bildirin.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-149">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>

    ```csharp
    public partial class MainWindow : Window   // Or class MainPage
    {
        // *** Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. <span data-ttu-id="4ad1f-150">`StartButton_Click`, bir işlemin zaten devam edilip edilmeyeceğini saptayın.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-150">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="4ad1f-151">`cts` değeri null ise, zaten etkin bir işlem yoktur.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-151">If the value of `cts` is null, no operation is already active.</span></span> <span data-ttu-id="4ad1f-152">Değer null değilse, zaten çalışmakta olan işlem iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-152">If the value isn't null, the operation that is already running is canceled.</span></span>

    ```csharp
    // *** If a download process is already underway, cancel it.
    if (cts != null)
    {
        cts.Cancel();
    }
    ```

3. <span data-ttu-id="4ad1f-153">`cts` geçerli işlemi temsil eden farklı bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-153">Set `cts` to a different value that represents the current process.</span></span>

    ```csharp
    // *** Now set cts to a new value that you can use to cancel the current process
    // if the button is chosen again.
    CancellationTokenSource newCTS = new CancellationTokenSource();
    cts = newCTS;
    ```

4. <span data-ttu-id="4ad1f-154">`StartButton_Click`sonunda geçerli işlem tamamlanmıştır, `cts` değerini null olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-154">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to null.</span></span>

    ```csharp
    // *** When the process is complete, signal that another process can begin.
    if (cts == newCTS)
        cts = null;
    ```

<span data-ttu-id="4ad1f-155">Aşağıdaki kod `StartButton_Click`tüm değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-155">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="4ad1f-156">Ekler yıldız işaretiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-156">The additions are marked with asterisks.</span></span>

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

<span data-ttu-id="4ad1f-157">`AccessTheWebAsync`, aşağıdaki değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-157">In `AccessTheWebAsync`, make the following changes.</span></span>

- <span data-ttu-id="4ad1f-158">`StartButton_Click`iptal belirtecini kabul etmek için bir parametre ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-158">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>

- <span data-ttu-id="4ad1f-159">`GetAsync` bir <xref:System.Threading.CancellationToken> bağımsız değişkenini kabul ettiğinden Web sitelerini indirmek için <xref:System.Net.Http.HttpClient.GetAsync%2A> yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-159">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>

- <span data-ttu-id="4ad1f-160">İndirilen her Web sitesinin sonuçlarını göstermek için `DisplayResults` çağrılmadan önce, geçerli işlemin iptal edildiğini doğrulamak için `ct` denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-160">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>

<span data-ttu-id="4ad1f-161">Aşağıdaki kod, yıldız işaretiyle işaretlenen bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-161">The following code shows these changes, which are marked with asterisks.</span></span>

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

<span data-ttu-id="4ad1f-162">Bu uygulama çalışırken **Başlat** düğmesini birkaç kez seçerseniz, aşağıdaki çıktıya benzeyen sonuçlar üretmelidir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-162">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>

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

<span data-ttu-id="4ad1f-163">Kısmi listeleri ortadan kaldırmak için, kullanıcının işlemi her yeniden başlattığı her seferinde metin kutusunu temizlemek üzere `StartButton_Click` içindeki ilk kod satırının açıklamasını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-163">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>

### <a name="BKMK_RunMultipleOperations"></a><span data-ttu-id="4ad1f-164">Birden çok Işlemi çalıştırma ve çıktıyı sıraya alma</span><span class="sxs-lookup"><span data-stu-id="4ad1f-164">Run Multiple Operations and Queue the Output</span></span>

<span data-ttu-id="4ad1f-165">Bu üçüncü örnek, Kullanıcı **Başlat** düğmesini her seçtiğinde uygulamanın başka bir zaman uyumsuz işlem başlatması ve tüm işlemlerin tamamlamada çalışması için en karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-165">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="4ad1f-166">Tüm istenen işlemler, listeden zaman uyumsuz olarak Web sitelerini indirir, ancak işlemlerden alınan çıkış sıralı olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-166">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="4ad1f-167">Diğer bir deyişle, gerçek indirme etkinliği araya eklemeli, bu da bir yandan [yeniden](#BKMK_RecognizingReentrancy) giriş, ancak her grup için sonuçların listesi ayrı olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-167">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](#BKMK_RecognizingReentrancy) shows, but the list of results for each group is presented separately.</span></span>

<span data-ttu-id="4ad1f-168">İşlemler, görüntüleme işlemi için bir ağ geçidi denetleyicisi görevi gören küresel bir <xref:System.Threading.Tasks.Task>`pendingWork`paylaşır.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-168">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>

<span data-ttu-id="4ad1f-169">Bu senaryoyu ayarlamak için, [Örnek uygulamayı gözden geçirmek ve çalıştırmak](#BKMD_SettingUpTheExample)için belirtilen temel kodda aşağıdaki değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-169">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="4ad1f-170">Ayrıca, tamamlanmış uygulamayı [zaman uyumsuz örneklerden indirebilirsiniz: .net masaüstü uygulamalarında yeniden giriş](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-170">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="4ad1f-171">Projenin adı örneği indirip queueresults.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-171">The name of the project is QueueResults.</span></span>

<span data-ttu-id="4ad1f-172">Aşağıdaki çıktıda, Kullanıcı **Başlat** düğmesini yalnızca bir kez seçerse sonuç gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-172">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="4ad1f-173">Harf etiketi,, sonucun **Başlangıç** düğmesinin seçildiği ilk sefer olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-173">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="4ad1f-174">Sayılar, indirme hedefleri listesindeki URL 'lerin sırasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-174">The numbers show the order of the URLs in the list of download targets.</span></span>

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

<span data-ttu-id="4ad1f-175">Kullanıcı **Başlat** düğmesini üç kez seçerse, uygulama aşağıdaki satırlara benzer bir çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-175">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="4ad1f-176">Numara işareti (#) ile başlayan bilgi satırları, uygulamanın ilerlemesini izler.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-176">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>

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

<span data-ttu-id="4ad1f-177">Grup A tamamlanmadan önce B ve C grupları başlar, ancak her grubun çıktısı ayrı olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-177">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="4ad1f-178">Önce Grup A 'nın tüm çıktıları, ardından Grup B için tüm çıktılar ve sonra Grup C için tüm çıktılar görüntülenir. Uygulama her zaman grupları sırayla görüntüler ve her grup için her zaman tek tek Web siteleri hakkındaki bilgileri URL 'Ler listesinde görünecek şekilde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-178">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>

<span data-ttu-id="4ad1f-179">Ancak, indirmelerin gerçekten gerçekleştiği sırayı tahmin edemezseniz.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-179">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="4ad1f-180">Birden çok grup başlatıldıktan sonra, oluşturdukları yükleme görevlerinin hepsi etkindir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-180">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="4ad1f-181">-1 ' in B-1 ' den önce indirileceğini varsaymazsınız ve-1 ' in-2 ' den önce indirildiğini varsaymazsınız.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-181">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>

#### <a name="global-definitions"></a><span data-ttu-id="4ad1f-182">Genel tanımlar</span><span class="sxs-lookup"><span data-stu-id="4ad1f-182">Global Definitions</span></span>

<span data-ttu-id="4ad1f-183">Örnek kod, tüm metotlardan görülebilen aşağıdaki iki genel bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-183">The sample code contains the following two global declarations that are visible from all methods.</span></span>

```csharp
public partial class MainWindow : Window  // Class MainPage in Windows Store app.
{
    // ***Declare the following variables where all methods can access them.
    private Task pendingWork = null;
    private char group = (char)('A' - 1);
```

<span data-ttu-id="4ad1f-184">`Task` değişkeni, `pendingWork`, görüntüleme sürecini fazla görür ve herhangi bir grubun başka bir grubun görüntüleme işlemini kesintiye uğramasını önler.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-184">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="4ad1f-185">`group`karakter değişkeni, sonuçların beklenen sırada göründüğünü doğrulamak için farklı gruplardan çıktıyı Etiketler.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-185">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>

#### <a name="the-click-event-handler"></a><span data-ttu-id="4ad1f-186">Click olay Işleyicisi</span><span class="sxs-lookup"><span data-stu-id="4ad1f-186">The Click Event Handler</span></span>

<span data-ttu-id="4ad1f-187">`StartButton_Click`olay işleyicisi, Kullanıcı **Başlat** düğmesini her seçtiğinde grup harfini artırır.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-187">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="4ad1f-188">Ardından işleyici, indirme işlemini çalıştırmak için `AccessTheWebAsync` çağırır.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-188">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>

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

#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="4ad1f-189">AccessTheWebAsync yöntemi</span><span class="sxs-lookup"><span data-stu-id="4ad1f-189">The AccessTheWebAsync Method</span></span>

<span data-ttu-id="4ad1f-190">Bu örnek `AccessTheWebAsync` iki yönteme ayırır.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-190">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="4ad1f-191">İlk yöntem `AccessTheWebAsync`, bir grup için tüm indirme görevlerini başlatır ve görüntüleme işlemini denetlemek için `pendingWork` ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-191">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="4ad1f-192">Yöntemi, aynı anda tüm indirme görevlerini başlatmak için bir dil tümleşik sorgu (LINQ sorgusu) ve <xref:System.Linq.Enumerable.ToArray%2A> kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-192">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>

<span data-ttu-id="4ad1f-193">`AccessTheWebAsync`, her indirmenin tamamlanmasını beklemek için `FinishOneGroupAsync` çağırır ve uzunluğunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-193">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>

<span data-ttu-id="4ad1f-194">`FinishOneGroupAsync`, `AccessTheWebAsync``pendingWork` atanan bir görevi döndürür.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-194">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="4ad1f-195">Bu değer, görev tamamlanmadan önce başka bir işlem kesintiye uğramasını önler.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-195">That value prevents interruption by another operation before the task is complete.</span></span>

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

#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="4ad1f-196">FinishOneGroupAsync yöntemi</span><span class="sxs-lookup"><span data-stu-id="4ad1f-196">The FinishOneGroupAsync Method</span></span>

<span data-ttu-id="4ad1f-197">Bu yöntem bir gruptaki indirme görevleri boyunca geçiş yapar, her birini bekliyor, indirilen Web sitesinin uzunluğunu görüntülüyor ve uzunluğu toplamına ekliyor.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-197">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>

<span data-ttu-id="4ad1f-198">`FinishOneGroupAsync` ilk ifade, yöntemi girerken, zaten görüntüleme işleminde olan veya zaten bekleyen bir işlemi etkilemediğinden emin olmak için `pendingWork` kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-198">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="4ad1f-199">Bu tür bir işlem devam ediyorsa, giriş işleminin tamamlanmasını beklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-199">If such an operation is in progress, the entering operation must wait its turn.</span></span>

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

#### <a name="points-of-interest"></a><span data-ttu-id="4ad1f-200">Ilgi çekici noktaları</span><span class="sxs-lookup"><span data-stu-id="4ad1f-200">Points of Interest</span></span>

<span data-ttu-id="4ad1f-201">Çıktıda diyez işareti (#) ile başlayan bilgi satırları bu örneğin nasıl çalıştığını açıklığa kavuşturacak.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-201">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>

<span data-ttu-id="4ad1f-202">Çıktıda aşağıdaki desenler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-202">The output shows the following patterns.</span></span>

- <span data-ttu-id="4ad1f-203">Bir grup, önceki bir grup çıktısını görüntülerken başlatılabilir, ancak önceki grubun çıktısının görüntülenmediği kesintiye uğramaz.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-203">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>

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

- <span data-ttu-id="4ad1f-204">`pendingWork` görevi, yalnızca ilk başlatılan A grubu için `FinishOneGroupAsync` başlangıcında boştur.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-204">The `pendingWork` task is null  at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="4ad1f-205">A grubu `FinishOneGroupAsync`ulaştığında bir await ifadesi henüz tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-205">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="4ad1f-206">Bu nedenle, denetim `AccessTheWebAsync`döndürülmemiştir ve `pendingWork` ilk atama gerçekleşmemiştir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-206">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>

- <span data-ttu-id="4ad1f-207">Aşağıdaki iki satır, her zaman çıktıda birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-207">The following two lines always appear together in the output.</span></span> <span data-ttu-id="4ad1f-208">Kod, `StartButton_Click` bir grubun işlemini başlatma ve grup için bir görevin `pendingWork`atama arasında hiçbir şekilde kesintiye uğramaz.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-208">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>

    ```output
    #Starting group B.
    #Task assigned for group B. Download tasks are active.
    ```

    <span data-ttu-id="4ad1f-209">Bir grup `StartButton_Click`girdikten sonra, işlem `FinishOneGroupAsync`girene kadar bir await ifadesi tamamlanmaz.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-209">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="4ad1f-210">Bu nedenle, başka hiçbir işlem bu kod segmenti sırasında denetim elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-210">Therefore, no other operation can gain control during that segment of code.</span></span>

## <a name="BKMD_SettingUpTheExample"></a><span data-ttu-id="4ad1f-211">Örnek uygulamayı inceleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="4ad1f-211">Reviewing and Running the Example App</span></span>

<span data-ttu-id="4ad1f-212">Örnek uygulamayı daha iyi anlamak için indirebilir, kendiniz derleyebilir veya uygulamayı uygulamadan bu konunun sonundaki kodu inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-212">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>

> [!NOTE]
> <span data-ttu-id="4ad1f-213">Örneği bir Windows Presentation Foundation (WPF) masaüstü uygulaması olarak çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-213">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="BKMK_DownloadingTheApp"></a><span data-ttu-id="4ad1f-214">Uygulama indiriliyor</span><span class="sxs-lookup"><span data-stu-id="4ad1f-214">Downloading the App</span></span>

1. <span data-ttu-id="4ad1f-215">[Zaman uyumsuz örneklerden sıkıştırılmış dosyayı indirin: .net masaüstü uygulamalarında yeniden giriş](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="4ad1f-215">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span>

2. <span data-ttu-id="4ad1f-216">İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-216">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

3. <span data-ttu-id="4ad1f-217">Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-217">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

4. <span data-ttu-id="4ad1f-218">Sıkıştırması açılmış örnek kodun bulunduğu klasöre gidin ve çözüm (. sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-218">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>

5. <span data-ttu-id="4ad1f-219">**Çözüm Gezgini**' de, çalıştırmak istediğiniz projenin kısayol menüsünü açın ve ardından **StartupProject olarak ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-219">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>

6. <span data-ttu-id="4ad1f-220">Projeyi derlemek ve çalıştırmak için CTRL + F5 tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-220">Choose the CTRL+F5 keys to build and run the project.</span></span>

### <a name="BKMK_BuildingTheApp"></a><span data-ttu-id="4ad1f-221">Uygulamayı oluşturma</span><span class="sxs-lookup"><span data-stu-id="4ad1f-221">Building the App</span></span>

<span data-ttu-id="4ad1f-222">Aşağıdaki bölümde, örneği WPF uygulaması olarak derlemek için kod sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-222">The following section provides the code to build the example as a WPF app.</span></span>

##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="4ad1f-223">WPF uygulaması derlemek için</span><span class="sxs-lookup"><span data-stu-id="4ad1f-223">To build a WPF app</span></span>

1. <span data-ttu-id="4ad1f-224">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-224">Start Visual Studio.</span></span>

2. <span data-ttu-id="4ad1f-225">Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-225">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="4ad1f-226">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-226">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="4ad1f-227">**Yüklü şablonlar** bölmesinde, **görsel C#** ' i genişletin ve ardından **Windows**' u genişletin.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-227">In the **Installed Templates** pane, expand **Visual C#**, and then expand **Windows**.</span></span>

4. <span data-ttu-id="4ad1f-228">Proje türleri listesinde **WPF uygulaması**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-228">In the list of project types, choose **WPF Application**.</span></span>

5. <span data-ttu-id="4ad1f-229">Projeyi `WebsiteDownloadWPF`olarak adlandırın, .NET Framework 4,6 veya üzeri bir sürüm seçin ve **Tamam** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-229">Name the project `WebsiteDownloadWPF`, choose .NET Framework version of 4.6 or higher and then click the **OK** button.</span></span>

     <span data-ttu-id="4ad1f-230">Yeni proje **Çözüm Gezgini**görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-230">The new project appears in **Solution Explorer**.</span></span>

6. <span data-ttu-id="4ad1f-231">Visual Studio Code düzenleyicisinde **MainWindow. xaml** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-231">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="4ad1f-232">Sekme görünür değilse, **Çözüm Gezgini**' de MainWindow. xaml için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-232">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

7. <span data-ttu-id="4ad1f-233">MainWindow. xaml ' nin **xaml** görünümünde, kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-233">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

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

     <span data-ttu-id="4ad1f-234">Bir metin kutusu ve bir düğme içeren basit bir pencere, MainWindow. xaml **Tasarım** görünümünde görünür.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-234">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

8. <span data-ttu-id="4ad1f-235">**Çözüm Gezgini**, **Başvurular** ' a sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-235">In **Solution Explorer**, right-click on **References** and select **Add Reference**.</span></span>

     <span data-ttu-id="4ad1f-236">Zaten seçili değilse <xref:System.Net.Http>için bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-236">Add a reference for <xref:System.Net.Http>, if it is not selected already.</span></span>

9. <span data-ttu-id="4ad1f-237">**Çözüm Gezgini**' de, MainWindow.xaml.cs için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-237">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

10. <span data-ttu-id="4ad1f-238">MainWindow.xaml.cs ' de, kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-238">In MainWindow.xaml.cs, replace the code with the following code.</span></span>

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

11. <span data-ttu-id="4ad1f-239">Programı çalıştırmak için CTRL + F5 tuşlarını seçin ve sonra **Başlat** düğmesini birkaç kez seçin.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-239">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>

12. <span data-ttu-id="4ad1f-240">[Başlat düğmesini devre dışı bırak](#BKMK_DisableTheStartButton)' dan değişiklikleri yapın, [işlemi Iptal edin ve yeniden başlatın](#BKMK_CancelAndRestart)ya da [birden çok işlem çalıştırın ve çıktıyı kuyruğa](#BKMK_RunMultipleOperations) alarak yeniden giriş işlemini idare edin.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-240">Make the changes from [Disable the Start Button](#BKMK_DisableTheStartButton), [Cancel and Restart the Operation](#BKMK_CancelAndRestart), or [Run Multiple Operations and Queue the Output](#BKMK_RunMultipleOperations) to handle the reentrancy.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ad1f-241">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ad1f-241">See also</span></span>

- [<span data-ttu-id="4ad1f-242">İzlenecek yol: Async ve await (C#) kullanarak Web 'e erişme</span><span class="sxs-lookup"><span data-stu-id="4ad1f-242">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="4ad1f-243">Async ve await (C#) ile zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="4ad1f-243">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
