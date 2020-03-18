---
title: Async Apps'ta Reentrancy'yi Işleme (C#)
ms.date: 07/20/2015
ms.assetid: 47c5075e-c448-45ce-9155-ed4e7e98c677
ms.openlocfilehash: 67fbbd294ffe6219b58065f974543b2dd483a92c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451869"
---
# <a name="handling-reentrancy-in-async-apps-c"></a><span data-ttu-id="358d9-102">Async Apps'ta Reentrancy'yi Işleme (C#)</span><span class="sxs-lookup"><span data-stu-id="358d9-102">Handling Reentrancy in Async Apps (C#)</span></span>

<span data-ttu-id="358d9-103">Uygulamanıza eşzamanlı kod eklediğinizde, yeniden işlem tamamlanmadan önce yeniden girmeyi ifade eden yeniden canlandırmayı düşünmelisiniz ve muhtemelen önlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="358d9-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="358d9-104">Yeniden canlandırma olasılıklarını tanımlamaz ve işlemezseniz, beklenmeyen sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="358d9-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>

<span data-ttu-id="358d9-105">**Bu konuda**</span><span class="sxs-lookup"><span data-stu-id="358d9-105">**In this topic**</span></span>

- [<span data-ttu-id="358d9-106">Reentrancy Tanıma</span><span class="sxs-lookup"><span data-stu-id="358d9-106">Recognizing Reentrancy</span></span>](#BKMK_RecognizingReentrancy)

- [<span data-ttu-id="358d9-107">Reentrancy işleme</span><span class="sxs-lookup"><span data-stu-id="358d9-107">Handling Reentrancy</span></span>](#BKMK_HandlingReentrancy)

  - [<span data-ttu-id="358d9-108">Başlat Düğmesini Devre Dışı</span><span class="sxs-lookup"><span data-stu-id="358d9-108">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)

  - [<span data-ttu-id="358d9-109">İşlemi İptal Etme ve Yeniden Başlatma</span><span class="sxs-lookup"><span data-stu-id="358d9-109">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)

  - [<span data-ttu-id="358d9-110">Birden Çok İşlem çalıştırın ve Çıktıyı Sıraya</span><span class="sxs-lookup"><span data-stu-id="358d9-110">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)

- [<span data-ttu-id="358d9-111">Örnek Uygulamayı İnceleme ve Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="358d9-111">Reviewing and Running the Example App</span></span>](#BKMD_SettingUpTheExample)

> [!NOTE]
> <span data-ttu-id="358d9-112">Örneği çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınıza yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="358d9-112">To run the example, you must have Visual Studio 2012 or newer and .NET Framework 4.5 or newer installed on your computer.</span></span>

> [!NOTE]
> <span data-ttu-id="358d9-113">Aktarım Katmanı Güvenliği (TLS) sürüm 1.2 artık uygulama geliştirmenizde kullanılacak minimum sürümdür.</span><span class="sxs-lookup"><span data-stu-id="358d9-113">Transport Layer Security (TLS) version 1.2 is now the minimum version to use in your app development.</span></span> <span data-ttu-id="358d9-114">Uygulamanız 4,7'den önce bir .NET Framework sürümünü hedefliyorsa, .NET Framework ile birlikte [Taşıma Katmanı Güvenliği (TLS) en iyi uygulamaları](../../../../framework/network-programming/tls.md)için aşağıdaki makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="358d9-114">If your app targets a .NET Framework version earlier than 4.7, refer to the following article for [Transport Layer Security (TLS) best practices with the .NET Framework](../../../../framework/network-programming/tls.md).</span></span>

## <a name="BKMK_RecognizingReentrancy"></a><span data-ttu-id="358d9-115">Reentrancy Tanıma</span><span class="sxs-lookup"><span data-stu-id="358d9-115">Recognizing Reentrancy</span></span>

<span data-ttu-id="358d9-116">Bu konudaki örnekte, kullanıcılar bir dizi web sitesi indiren ve indirilen toplam bayt sayısını hesaplayan bir eşzamanlı uygulama başlatmak için bir **Başlat** düğmesi seçer.</span><span class="sxs-lookup"><span data-stu-id="358d9-116">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="358d9-117">Örneğin eşzamanlı sürümü, ilk kez kullanıcının düğmeyi kaç kez seçtiğine bakılmaksızın aynı şekilde yanıt verir, çünkü ilk kez kullanıcı işi, uygulama çalışan bitene kadar bu olayları yok sayar.</span><span class="sxs-lookup"><span data-stu-id="358d9-117">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="358d9-118">Ancak, bir eşzamanlı uygulamada, Kullanıcı Birsonucu iş parçacığı yanıt vermeye devam eder ve tamamlanmadan önce eşzamanlı işlemi yeniden girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="358d9-118">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>

<span data-ttu-id="358d9-119">Aşağıdaki örnekte, kullanıcı **Başlat** düğmesini yalnızca bir kez seçerse beklenen çıktı yı gösterir.</span><span class="sxs-lookup"><span data-stu-id="358d9-119">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="358d9-120">İndirilen web sitelerinin listesi, her sitenin boyutu, baytlar halinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="358d9-120">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="358d9-121">Sonunda toplam bayt sayısı görünür.</span><span class="sxs-lookup"><span data-stu-id="358d9-121">The total number of bytes appears at the end.</span></span>

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

<span data-ttu-id="358d9-122">Ancak, kullanıcı düğmeyi birden çok kez seçerse, olay işleyicisi tekrar tekrar çağrılır ve indirme işlemi her seferinde yeniden girilir.</span><span class="sxs-lookup"><span data-stu-id="358d9-122">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="358d9-123">Sonuç olarak, aynı anda birkaç eşzamanlı işlem yürütülür, çıktı sonuçları birbirine bırakır ve toplam bayt sayısı kafa karıştırıcıdır.</span><span class="sxs-lookup"><span data-stu-id="358d9-123">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>

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

<span data-ttu-id="358d9-124">Bu konunun sonuna kaydırarak bu çıktıyı üreten kodu gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="358d9-124">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="358d9-125">Çözümü yerel bilgisayarınıza indirip websitedownload projesini çalıştırarak veya kendi projenizi oluşturmak için bu konunun sonundaki kodu kullanarak kodu deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="358d9-125">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project.</span></span> <span data-ttu-id="358d9-126">Daha fazla bilgi ve yönerge için [Örnek Uygulamayı İnceleme ve Çalıştırma'ya](#BKMD_SettingUpTheExample)bakın.</span><span class="sxs-lookup"><span data-stu-id="358d9-126">For more information and instructions, see [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span>

## <a name="BKMK_HandlingReentrancy"></a><span data-ttu-id="358d9-127">Reentrancy işleme</span><span class="sxs-lookup"><span data-stu-id="358d9-127">Handling Reentrancy</span></span>

<span data-ttu-id="358d9-128">Uygulamanızın ne yapmasını istediğinize bağlı olarak, yeniden canlandırma işlemlerini çeşitli şekillerde işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="358d9-128">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="358d9-129">Bu konu aşağıdaki örnekleri sunar:</span><span class="sxs-lookup"><span data-stu-id="358d9-129">This topic presents the following examples:</span></span>

- [<span data-ttu-id="358d9-130">Başlat Düğmesini Devre Dışı</span><span class="sxs-lookup"><span data-stu-id="358d9-130">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)

  <span data-ttu-id="358d9-131">İşlem çalışırken **Başlat** düğmesini devre dışı kalarak kullanıcı nın sözünü kesemeyecek şekilde devre dışı edin.</span><span class="sxs-lookup"><span data-stu-id="358d9-131">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>

- [<span data-ttu-id="358d9-132">İşlemi İptal Etme ve Yeniden Başlatma</span><span class="sxs-lookup"><span data-stu-id="358d9-132">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)

  <span data-ttu-id="358d9-133">Kullanıcı **Başlat** düğmesini yeniden seçtiğinde çalışmaya devam eden tüm işlemleri iptal edin ve en son istenen işlemin devam etmesine izin verin.</span><span class="sxs-lookup"><span data-stu-id="358d9-133">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>

- [<span data-ttu-id="358d9-134">Birden Çok İşlem çalıştırın ve Çıktıyı Sıraya</span><span class="sxs-lookup"><span data-stu-id="358d9-134">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)

  <span data-ttu-id="358d9-135">İstenen tüm işlemlerin eşzamanlı olarak çalışmasına izin verin, ancak her işlemden elde edilen sonuçların birlikte ve sırayla görünmesi için çıktının görüntülenmesini koordine edin.</span><span class="sxs-lookup"><span data-stu-id="358d9-135">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>

### <a name="BKMK_DisableTheStartButton"></a><span data-ttu-id="358d9-136">Başlat Düğmesini Devre Dışı</span><span class="sxs-lookup"><span data-stu-id="358d9-136">Disable the Start Button</span></span>

<span data-ttu-id="358d9-137">Olay işleyicisinin üst kısmındaki düğmeyi devre dışı bırakarak işlem çalışırken Başlat düğmesini engelleyebilirsiniz. **Start** `StartButton_Click`</span><span class="sxs-lookup"><span data-stu-id="358d9-137">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="358d9-138">Daha sonra, işlem bittiğinde düğmeyi bir `finally` blok içinden yeniden etkinleştirebilirsiniz, böylece kullanıcılar uygulamayı yeniden çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="358d9-138">You can then reenable the button from within a  `finally` block when the operation finishes so that users can run the app again.</span></span>

<span data-ttu-id="358d9-139">Bu senaryoyu ayarlamak için, Örnek Uygulamayı Gözden Geçirme [ve Çalıştırma'da](#BKMD_SettingUpTheExample)sağlanan temel kodda aşağıdaki değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="358d9-139">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="358d9-140">Ayrıca bitmiş uygulamayı [Async Samples: Reentrancy in .NET Desktop Apps'tan](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="358d9-140">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="358d9-141">Projenin adı DisableStartButton'dur.</span><span class="sxs-lookup"><span data-stu-id="358d9-141">The name of the project is DisableStartButton.</span></span>

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

<span data-ttu-id="358d9-142">Değişikliklerin bir sonucu olarak, düğme web sitelerini indirirken `AccessTheWebAsync` yanıt vermez, bu nedenle işlem yeniden girilemez.</span><span class="sxs-lookup"><span data-stu-id="358d9-142">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>

### <a name="BKMK_CancelAndRestart"></a><span data-ttu-id="358d9-143">İşlemi İptal Etme ve Yeniden Başlatma</span><span class="sxs-lookup"><span data-stu-id="358d9-143">Cancel and Restart the Operation</span></span>

<span data-ttu-id="358d9-144">**Başlat** düğmesini devre dışı bırakmak yerine düğmeyi etkin tutabilirsiniz, ancak kullanıcı bu düğmeyi tekrar seçerse, zaten çalışan işlemi iptal edin ve en son başlatılan işlemin devam etmesine izin verin.</span><span class="sxs-lookup"><span data-stu-id="358d9-144">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>

<span data-ttu-id="358d9-145">İptal hakkında daha fazla bilgi için [Async Uygulamanızı (C#) İnce Ayarla'ya](./fine-tuning-your-async-application.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="358d9-145">For more information about cancellation, see [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md).</span></span>

<span data-ttu-id="358d9-146">Bu senaryoyu ayarlamak için, Örnek Uygulamayı Gözden Geçirme [ve Çalıştırma'da](#BKMD_SettingUpTheExample)sağlanan temel kodda aşağıdaki değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="358d9-146">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="358d9-147">Ayrıca bitmiş uygulamayı [Async Samples: Reentrancy in .NET Desktop Apps'tan](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="358d9-147">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="358d9-148">Projenin adı CancelAndRestart'tır.</span><span class="sxs-lookup"><span data-stu-id="358d9-148">The name of the project is CancelAndRestart.</span></span>

1. <span data-ttu-id="358d9-149">Tüm <xref:System.Threading.CancellationTokenSource> yöntemler `cts`için kapsamda olan bir değişken bildirin.</span><span class="sxs-lookup"><span data-stu-id="358d9-149">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>

    ```csharp
    public partial class MainWindow : Window   // Or class MainPage
    {
        // *** Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. <span data-ttu-id="358d9-150">In `StartButton_Click`, bir işlemin devam edip etmediğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="358d9-150">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="358d9-151">Değeri null `cts` ise, hiçbir işlem zaten etkin.</span><span class="sxs-lookup"><span data-stu-id="358d9-151">If the value of `cts` is null, no operation is already active.</span></span> <span data-ttu-id="358d9-152">Değer null değilse, zaten çalışan işlem iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="358d9-152">If the value isn't null, the operation that is already running is canceled.</span></span>

    ```csharp
    // *** If a download process is already underway, cancel it.
    if (cts != null)
    {
        cts.Cancel();
    }
    ```

3. <span data-ttu-id="358d9-153">`cts` Geçerli işlemi temsil eden farklı bir değerayarlayın.</span><span class="sxs-lookup"><span data-stu-id="358d9-153">Set `cts` to a different value that represents the current process.</span></span>

    ```csharp
    // *** Now set cts to a new value that you can use to cancel the current process
    // if the button is chosen again.
    CancellationTokenSource newCTS = new CancellationTokenSource();
    cts = newCTS;
    ```

4. <span data-ttu-id="358d9-154">`StartButton_Click`Sonunda, geçerli işlem tamamlandı, bu nedenle `cts` geri null değerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="358d9-154">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to null.</span></span>

    ```csharp
    // *** When the process is complete, signal that another process can begin.
    if (cts == newCTS)
        cts = null;
    ```

<span data-ttu-id="358d9-155">Aşağıdaki kod' daki tüm `StartButton_Click`değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="358d9-155">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="358d9-156">Eklemeler yıldız işaretleri ile işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="358d9-156">The additions are marked with asterisks.</span></span>

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

<span data-ttu-id="358d9-157">In `AccessTheWebAsync`, aşağıdaki değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="358d9-157">In `AccessTheWebAsync`, make the following changes.</span></span>

- <span data-ttu-id="358d9-158">'den `StartButton_Click`iptal belirteci kabul etmek için bir parametre ekleyin.</span><span class="sxs-lookup"><span data-stu-id="358d9-158">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>

- <span data-ttu-id="358d9-159">Bir <xref:System.Threading.CancellationToken> <xref:System.Net.Http.HttpClient.GetAsync%2A> bağımsız `GetAsync` değişkenkabul ettiği için web sitelerini indirmek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="358d9-159">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>

- <span data-ttu-id="358d9-160">İndirilen her web sitesinin sonuçlarını görüntülemek için aramadan `DisplayResults` önce, geçerli işlemin iptal edilmediğini kontrol edin. `ct`</span><span class="sxs-lookup"><span data-stu-id="358d9-160">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>

<span data-ttu-id="358d9-161">Aşağıdaki kod, yıldız işaretleriyle işaretlenmiş bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="358d9-161">The following code shows these changes, which are marked with asterisks.</span></span>

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

<span data-ttu-id="358d9-162">Bu uygulama çalışırken **Başlat** düğmesini birkaç kez seçerseniz, aşağıdaki çıktıya benzeyen sonuçlar üretmelidir.</span><span class="sxs-lookup"><span data-stu-id="358d9-162">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>

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

<span data-ttu-id="358d9-163">Kısmi listeleri ortadan kaldırmak `StartButton_Click` için, kullanıcı işlemi her yeniden başlattığında metin kutusunu temizlemek için ilk kod satırının yorumunu kaldırın.</span><span class="sxs-lookup"><span data-stu-id="358d9-163">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>

### <a name="BKMK_RunMultipleOperations"></a><span data-ttu-id="358d9-164">Birden Çok İşlem çalıştırın ve Çıktıyı Sıraya</span><span class="sxs-lookup"><span data-stu-id="358d9-164">Run Multiple Operations and Queue the Output</span></span>

<span data-ttu-id="358d9-165">Bu üçüncü örnek, uygulamanın **kullanıcının Başlat** düğmesini her seçtiğinde başka bir eşzamanlı işlem başlatması ve tüm işlemlerin tamamlanması için çalıştırılması açısından en karmaşık örnektir.</span><span class="sxs-lookup"><span data-stu-id="358d9-165">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="358d9-166">İstenen tüm işlemler listedeki web sitelerini eşit olarak indirir, ancak işlemlerden elde edilen çıktı sırayla sunulur.</span><span class="sxs-lookup"><span data-stu-id="358d9-166">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="358d9-167">Diğer bir deyişle, [Reentrancy'yi Tanıma'daki](#BKMK_RecognizingReentrancy) çıktının gösterdiği gibi, gerçek indirme etkinliği birbiriyle bağlantılıdır, ancak her grubun sonuç listesi ayrı olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="358d9-167">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](#BKMK_RecognizingReentrancy) shows, but the list of results for each group is presented separately.</span></span>

<span data-ttu-id="358d9-168">İşlemler, görüntüleme <xref:System.Threading.Tasks.Task> `pendingWork`işlemi için bir kapı bekçisi olarak hizmet veren genel bir , paylaşır.</span><span class="sxs-lookup"><span data-stu-id="358d9-168">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>

<span data-ttu-id="358d9-169">Bu senaryoyu ayarlamak için, Örnek Uygulamayı Gözden Geçirme [ve Çalıştırma'da](#BKMD_SettingUpTheExample)sağlanan temel kodda aşağıdaki değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="358d9-169">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="358d9-170">Ayrıca bitmiş uygulamayı [Async Samples: Reentrancy in .NET Desktop Apps'tan](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="358d9-170">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="358d9-171">Projenin adı QueueResults'dir.</span><span class="sxs-lookup"><span data-stu-id="358d9-171">The name of the project is QueueResults.</span></span>

<span data-ttu-id="358d9-172">Kullanıcı **Başlat** düğmesini yalnızca bir kez seçerse aşağıdaki çıktı sonucu gösterir.</span><span class="sxs-lookup"><span data-stu-id="358d9-172">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="358d9-173">A harf etiketi, sonucun **Başlat** düğmesinin ilk kez seçildiği nden geldiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="358d9-173">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="358d9-174">Sayılar, indirme hedefleri listesindeKI URL'lerin sırasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="358d9-174">The numbers show the order of the URLs in the list of download targets.</span></span>

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

<span data-ttu-id="358d9-175">Kullanıcı **Başlat** düğmesini üç kez seçerse, uygulama aşağıdaki satırları andıran çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="358d9-175">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="358d9-176">Pound işaretiyle başlayan bilgi satırları (#) uygulamanın ilerlemesini izler.</span><span class="sxs-lookup"><span data-stu-id="358d9-176">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>

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

<span data-ttu-id="358d9-177">B ve C grupları A grubu bitmeden önce başlar, ancak her grubun çıktısı ayrı ayrı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="358d9-177">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="358d9-178">A grubu için tüm çıktı önce görünür, ardından B grubu için tüm çıktı ve ardından C grubu için tüm çıktı çıkar. Uygulama her zaman grupları sırayla görüntüler ve her grup için URL'lerin URL'leri listesinde görünmesi sırasına göre her zaman web siteleri hakkındaki bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="358d9-178">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>

<span data-ttu-id="358d9-179">Ancak, indirmelerin gerçekte gerçekleşme sırası tahmin edemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="358d9-179">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="358d9-180">Birden çok grup başlatıldıktan sonra, oluşturdukları indirme görevlerinin tümü etkin olur.</span><span class="sxs-lookup"><span data-stu-id="358d9-180">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="358d9-181">A-1'in B-1'den önce indirileceğini varsayamaz ve A-1'in A-2'den önce indirileceğini varsayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="358d9-181">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>

#### <a name="global-definitions"></a><span data-ttu-id="358d9-182">Küresel Tanımlar</span><span class="sxs-lookup"><span data-stu-id="358d9-182">Global Definitions</span></span>

<span data-ttu-id="358d9-183">Örnek kod, tüm yöntemlerden görülebilen aşağıdaki iki genel bildirim içerir.</span><span class="sxs-lookup"><span data-stu-id="358d9-183">The sample code contains the following two global declarations that are visible from all methods.</span></span>

```csharp
public partial class MainWindow : Window  // Class MainPage in Windows Store app.
{
    // ***Declare the following variables where all methods can access them.
    private Task pendingWork = null;
    private char group = (char)('A' - 1);
```

<span data-ttu-id="358d9-184">Değişken, `Task` `pendingWork`görüntü işlemini denetler ve herhangi bir grubun başka bir grubun görüntüleme işlemini kesintiye uğratmasını önler.</span><span class="sxs-lookup"><span data-stu-id="358d9-184">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="358d9-185">Karakter değişkeni, `group`sonuçların beklenen sırada göründüğünü doğrulamak için farklı gruplardan çıktı etiketler.</span><span class="sxs-lookup"><span data-stu-id="358d9-185">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>

#### <a name="the-click-event-handler"></a><span data-ttu-id="358d9-186">Tıklayın Olay Handleyici</span><span class="sxs-lookup"><span data-stu-id="358d9-186">The Click Event Handler</span></span>

<span data-ttu-id="358d9-187">Olay işleyicisi, `StartButton_Click`kullanıcı **Başlat** düğmesini her seçtiğinde grup harfini de martılar.</span><span class="sxs-lookup"><span data-stu-id="358d9-187">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="358d9-188">Daha sonra işleyici indirme işlemini çalıştırmak için çağırır. `AccessTheWebAsync`</span><span class="sxs-lookup"><span data-stu-id="358d9-188">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>

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

#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="358d9-189">AccessThewebasync Yöntemi</span><span class="sxs-lookup"><span data-stu-id="358d9-189">The AccessTheWebAsync Method</span></span>

<span data-ttu-id="358d9-190">Bu örnek `AccessTheWebAsync` iki yönteme bölünür.</span><span class="sxs-lookup"><span data-stu-id="358d9-190">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="358d9-191">İlk yöntem, `AccessTheWebAsync`bir grup için tüm indirme görevlerini `pendingWork` başlatır ve görüntüleme işlemini denetlemek için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="358d9-191">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="358d9-192">Yöntem, bir Dil Tümleşik Sorgusu <xref:System.Linq.Enumerable.ToArray%2A> (LINQ sorgusu) kullanır ve tüm indirme görevlerini aynı anda başlatmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="358d9-192">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>

<span data-ttu-id="358d9-193">`AccessTheWebAsync`sonra `FinishOneGroupAsync` her indirme tamamlanmasını beklemek ve uzunluğunu görüntülemek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="358d9-193">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>

<span data-ttu-id="358d9-194">`FinishOneGroupAsync``pendingWork` 'de `AccessTheWebAsync`atanan bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="358d9-194">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="358d9-195">Bu değer, görev tamamlanmadan önce başka bir işlemtarafından kesintiye uğramayı önler.</span><span class="sxs-lookup"><span data-stu-id="358d9-195">That value prevents interruption by another operation before the task is complete.</span></span>

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

#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="358d9-196">FinishOneGroupAsync Yöntemi</span><span class="sxs-lookup"><span data-stu-id="358d9-196">The FinishOneGroupAsync Method</span></span>

<span data-ttu-id="358d9-197">Bu yöntem, bir gruptaki indirme görevleri arasında geçiş yapmakta, her birini bekler, indirilen web sitesinin uzunluğunu görüntüler ve uzunluğu toplama ekler.</span><span class="sxs-lookup"><span data-stu-id="358d9-197">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>

<span data-ttu-id="358d9-198">Yönteme girmenin zaten görüntü sürecinde olan veya zaten bekleyen bir işlemi etkilemediğinden emin olmak için `FinishOneGroupAsync` kullanılan `pendingWork` ilk deyim.</span><span class="sxs-lookup"><span data-stu-id="358d9-198">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="358d9-199">Böyle bir işlem devam ediyorsa, giren işlem sırasını beklemelidir.</span><span class="sxs-lookup"><span data-stu-id="358d9-199">If such an operation is in progress, the entering operation must wait its turn.</span></span>

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

#### <a name="points-of-interest"></a><span data-ttu-id="358d9-200">İlgi Çekici Noktalar</span><span class="sxs-lookup"><span data-stu-id="358d9-200">Points of Interest</span></span>

<span data-ttu-id="358d9-201">Çıktıdaki pound işaretiyle (#) başlayan bilgi satırları, bu örneğin nasıl çalıştığını açıklığa kavuşturur.</span><span class="sxs-lookup"><span data-stu-id="358d9-201">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>

<span data-ttu-id="358d9-202">Çıktı aşağıdaki desenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="358d9-202">The output shows the following patterns.</span></span>

- <span data-ttu-id="358d9-203">Önceki bir grup çıktısını görüntülerken bir grup başlatılabilir, ancak önceki grubun çıktısının görüntülenmesi kesintiye uğramaz.</span><span class="sxs-lookup"><span data-stu-id="358d9-203">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>

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

- <span data-ttu-id="358d9-204">Görev, `pendingWork` `FinishOneGroupAsync` yalnızca ilk olarak başlayan A grubu için başlangıçta geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="358d9-204">The `pendingWork` task is null  at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="358d9-205">A Grubu, 'ye ulaştığında `FinishOneGroupAsync`bekleyen bir ifadeyi henüz tamamlamadı.</span><span class="sxs-lookup"><span data-stu-id="358d9-205">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="358d9-206">Bu nedenle, denetim döndürülmedi `AccessTheWebAsync`ve ilk `pendingWork` atama gerçekleşmedi.</span><span class="sxs-lookup"><span data-stu-id="358d9-206">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>

- <span data-ttu-id="358d9-207">Aşağıdaki iki satır her zaman çıkışta birlikte görünür.</span><span class="sxs-lookup"><span data-stu-id="358d9-207">The following two lines always appear together in the output.</span></span> <span data-ttu-id="358d9-208">Kod, bir grubun çalışmasını başlatma `StartButton_Click` ile grup için bir görev atamak arasında hiçbir zaman kesintiye `pendingWork`uğramaz.</span><span class="sxs-lookup"><span data-stu-id="358d9-208">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>

    ```output
    #Starting group B.
    #Task assigned for group B. Download tasks are active.
    ```

    <span data-ttu-id="358d9-209">Bir grup `StartButton_Click`girdikten sonra, işlem girene `FinishOneGroupAsync`kadar bekleme ifadesini tamamlamaz.</span><span class="sxs-lookup"><span data-stu-id="358d9-209">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="358d9-210">Bu nedenle, kodun bu kesimi sırasında başka hiçbir işlem denetim elde edemez.</span><span class="sxs-lookup"><span data-stu-id="358d9-210">Therefore, no other operation can gain control during that segment of code.</span></span>

## <a name="BKMD_SettingUpTheExample"></a><span data-ttu-id="358d9-211">Örnek Uygulamayı İnceleme ve Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="358d9-211">Reviewing and Running the Example App</span></span>

<span data-ttu-id="358d9-212">Örnek uygulamayı daha iyi anlamak için uygulamayı indirebilir, kendiniz oluşturabilir veya uygulamayı uygulamadan bu konunun sonundaki kodu gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="358d9-212">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>

> [!NOTE]
> <span data-ttu-id="358d9-213">Örneği Windows Presentation Foundation (WPF) masaüstü uygulaması olarak çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınıza yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="358d9-213">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="BKMK_DownloadingTheApp"></a><span data-ttu-id="358d9-214">Uygulamayı İndirme</span><span class="sxs-lookup"><span data-stu-id="358d9-214">Downloading the App</span></span>

1. <span data-ttu-id="358d9-215">Sıkıştırılmış dosyayı [Async Samples: Reentrancy in .NET Desktop Apps'tan](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)indirin.</span><span class="sxs-lookup"><span data-stu-id="358d9-215">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span>

2. <span data-ttu-id="358d9-216">İndirdiğiniz dosyayı sıkıştırın ve Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="358d9-216">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

3. <span data-ttu-id="358d9-217">Menü çubuğunda **Dosya**, **Aç**, **Proje/Çözüm'ü**seçin.</span><span class="sxs-lookup"><span data-stu-id="358d9-217">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

4. <span data-ttu-id="358d9-218">Sıkıştırılmış örnek kodu tutan klasöre gidin ve ardından çözüm (.sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="358d9-218">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>

5. <span data-ttu-id="358d9-219">**Çözüm Gezgini'nde,** çalıştırmak istediğiniz proje için kısayol menüsünü açın ve ardından **StartUpProject olarak ayarla'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="358d9-219">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>

6. <span data-ttu-id="358d9-220">Projeyi oluşturmak ve çalıştırmak için CTRL+F5 tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="358d9-220">Choose the CTRL+F5 keys to build and run the project.</span></span>

### <a name="BKMK_BuildingTheApp"></a><span data-ttu-id="358d9-221">Uygulamayı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="358d9-221">Building the App</span></span>

<span data-ttu-id="358d9-222">Aşağıdaki bölümde, örneği WPF uygulaması olarak oluşturmak için kod sağlanır.</span><span class="sxs-lookup"><span data-stu-id="358d9-222">The following section provides the code to build the example as a WPF app.</span></span>

##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="358d9-223">WPF uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="358d9-223">To build a WPF app</span></span>

1. <span data-ttu-id="358d9-224">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="358d9-224">Start Visual Studio.</span></span>

2. <span data-ttu-id="358d9-225">Menü çubuğunda **Dosya**, **Yeni**, **Proje'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="358d9-225">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="358d9-226">**Yeni Proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="358d9-226">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="358d9-227">Yüklü **Şablonlar** bölmesinde Visual **C# 'yi**genişletin ve **ardından Windows'u**genişletin.</span><span class="sxs-lookup"><span data-stu-id="358d9-227">In the **Installed Templates** pane, expand **Visual C#**, and then expand **Windows**.</span></span>

4. <span data-ttu-id="358d9-228">Proje türleri listesinde **WPF Uygulaması'nı**seçin.</span><span class="sxs-lookup"><span data-stu-id="358d9-228">In the list of project types, choose **WPF Application**.</span></span>

5. <span data-ttu-id="358d9-229">Projeyi `WebsiteDownloadWPF`adlandırın, 4,6 veya daha yüksek .NET Framework sürümünü seçin ve ardından **Tamam** düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="358d9-229">Name the project `WebsiteDownloadWPF`, choose .NET Framework version of 4.6 or higher and then click the **OK** button.</span></span>

     <span data-ttu-id="358d9-230">Yeni proje Çözüm **Gezgini'nde**görünür.</span><span class="sxs-lookup"><span data-stu-id="358d9-230">The new project appears in **Solution Explorer**.</span></span>

6. <span data-ttu-id="358d9-231">Visual Studio Code Editor'da **MainWindow.xaml** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="358d9-231">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="358d9-232">Sekme görünmüyorsa, **Solution Explorer'da**MainWindow.xaml için kısayol menüsünü açın ve ardından **Kodu Görüntüle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="358d9-232">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

7. <span data-ttu-id="358d9-233">MainWindow.xaml'ın **XAML** görünümünde kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="358d9-233">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

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

     <span data-ttu-id="358d9-234">MainWindow.xaml'ın **Tasarım** görünümünde metin kutusu ve düğme içeren basit bir pencere görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="358d9-234">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

8. <span data-ttu-id="358d9-235">**Çözüm Gezgini'nde,** **Başvurular'a** sağ tıklayın ve **Referans Ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="358d9-235">In **Solution Explorer**, right-click on **References** and select **Add Reference**.</span></span>

     <span data-ttu-id="358d9-236">Zaten seçilmemişse, için <xref:System.Net.Http>bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="358d9-236">Add a reference for <xref:System.Net.Http>, if it is not selected already.</span></span>

9. <span data-ttu-id="358d9-237">**Çözüm Gezgini'nde,** MainWindow.xaml.cs için kısayol menüsünü açın ve ardından **Kodu Görüntüle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="358d9-237">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

10. <span data-ttu-id="358d9-238">MainWindow.xaml.cs kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="358d9-238">In MainWindow.xaml.cs, replace the code with the following code.</span></span>

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

11. <span data-ttu-id="358d9-239">Programı çalıştırmak için CTRL+F5 tuşlarını seçin ve ardından **Başlat** düğmesini birkaç kez seçin.</span><span class="sxs-lookup"><span data-stu-id="358d9-239">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>

12. <span data-ttu-id="358d9-240">[Başlat Düğmesini Devre Dışı Devre](#BKMK_DisableTheStartButton)Dışı, [İşlemi İptal Et ve Yeniden Başlat'](#BKMK_CancelAndRestart)tan değişiklikler yapın veya birden çok işlemi çalıştırın ve yeniden başlatma işlemini işlemek için [Çıktıyı](#BKMK_RunMultipleOperations) Sıralayın.</span><span class="sxs-lookup"><span data-stu-id="358d9-240">Make the changes from [Disable the Start Button](#BKMK_DisableTheStartButton), [Cancel and Restart the Operation](#BKMK_CancelAndRestart), or [Run Multiple Operations and Queue the Output](#BKMK_RunMultipleOperations) to handle the reentrancy.</span></span>

## <a name="see-also"></a><span data-ttu-id="358d9-241">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="358d9-241">See also</span></span>

- [<span data-ttu-id="358d9-242">Walkthrough: Async kullanarak Web'e erişim ve bekleme (C#)</span><span class="sxs-lookup"><span data-stu-id="358d9-242">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="358d9-243">Async ve await ile Asynchronous Programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="358d9-243">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
