---
title: Bir Async Görevi veya Görev Listesini İptal Etme (C#)
ms.date: 07/20/2015
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 93526f772f79e993767fd8f29087b6caf4e29468
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595724"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a><span data-ttu-id="28b1b-102">Eşitleme görevini veya görev listesini iptal etme (C#)</span><span class="sxs-lookup"><span data-stu-id="28b1b-102">Cancel an async task or a list of tasks (C#)</span></span>

<span data-ttu-id="28b1b-103">Tamamlanmasını beklemek istemiyorsanız, bir async uygulamasını iptal etmek için kullanabileceğiniz bir düğme ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28b1b-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="28b1b-104">Bu konudaki örnekleri izleyerek, bir web sitesinin veya web sitelerinin listesini indiren bir uygulamaya iptal düğmesi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28b1b-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>

<span data-ttu-id="28b1b-105">Örnekler, [Async Uygulamanızı (C#) İnce Ayarlanın](./fine-tuning-your-async-application.md) açıklandığı Kullanıcı Birikintisi'ni kullanır.</span><span class="sxs-lookup"><span data-stu-id="28b1b-105">The examples use the UI that [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md) describes.</span></span>

> [!NOTE]
> <span data-ttu-id="28b1b-106">Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınıza yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="28b1b-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="cancel-a-task"></a><span data-ttu-id="28b1b-107">Görevi iptal etme</span><span class="sxs-lookup"><span data-stu-id="28b1b-107">Cancel a task</span></span>

<span data-ttu-id="28b1b-108">İlk örnek, **İptal** düğmesini tek bir indirme göreviyle ilişkilendirer.</span><span class="sxs-lookup"><span data-stu-id="28b1b-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="28b1b-109">Uygulama içerik indirirken düğmeyi seçerseniz, indirme iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="28b1b-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>

### <a name="download-the-example"></a><span data-ttu-id="28b1b-110">Örneği indirin</span><span class="sxs-lookup"><span data-stu-id="28b1b-110">Download the example</span></span>

<span data-ttu-id="28b1b-111">Windows Presentation Foundation (WPF) projesinin tamamını [Async Sample: Fine Tuning Application'dan](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) indirebilir ve ardından aşağıdaki adımları izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28b1b-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="28b1b-112">İndirdiğiniz dosyayı sıkıştırın ve Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="28b1b-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="28b1b-113">Menü çubuğunda **Dosya** > **Aç** > **Projesi/Çözümü'nü**seçin.</span><span class="sxs-lookup"><span data-stu-id="28b1b-113">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="28b1b-114">**Projeyi Aç** iletişim kutusunda, sıkıştırdığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="28b1b-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="28b1b-115">**Solution**Explorer'da, **CancelATask** projesinin kısayol menüsünü açın ve ardından **StartUp Project olarak ayarla'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="28b1b-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="28b1b-116">Projeyi çalıştırmak için **F5** tuşunu seçin (veya projeyi hata ayıklamadan çalıştırmak için **Ctrl**+**F5** tuşuna basın).</span><span class="sxs-lookup"><span data-stu-id="28b1b-116">Choose the **F5** key to run the project (or, press **Ctrl**+**F5** to run the project without debugging it).</span></span>

> [!TIP]
> <span data-ttu-id="28b1b-117">Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyalarını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28b1b-117">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>

### <a name="build-the-example"></a><span data-ttu-id="28b1b-118">Örneği derleme</span><span class="sxs-lookup"><span data-stu-id="28b1b-118">Build the example</span></span>
 <span data-ttu-id="28b1b-119">Aşağıdaki değişiklikler, bir web sitesini indiren bir uygulamaya **İptal** düğmesi ekler.</span><span class="sxs-lookup"><span data-stu-id="28b1b-119">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="28b1b-120">Örneği indirmek veya oluşturmak istemiyorsanız, bu konunun sonundaki "Örnekleri Tamamla" bölümündeki son ürünü inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28b1b-120">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="28b1b-121">Yıldız işaretleri koddaki değişiklikleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="28b1b-121">Asterisks mark the changes in the code.</span></span>

 <span data-ttu-id="28b1b-122">Örneği adım adım oluşturmak için, "Örneği İndirme" bölümündeki yönergeleri izleyin, ancak **CancelATask**yerine **Başlangıç Projesi** olarak **Başlangıç Kodu'nu** seçin.</span><span class="sxs-lookup"><span data-stu-id="28b1b-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>

 <span data-ttu-id="28b1b-123">Ardından, bu projenin MainWindow.xaml.cs dosyasına aşağıdaki değişiklikleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="28b1b-123">Then add the following changes to the MainWindow.xaml.cs file of that project.</span></span>

1. <span data-ttu-id="28b1b-124">Bir `CancellationTokenSource` değişken `cts`bildirin, bu ona erişen tüm yöntemler için kapsamdadır.</span><span class="sxs-lookup"><span data-stu-id="28b1b-124">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>

    ```csharp
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. <span data-ttu-id="28b1b-125">**İptal** düğmesi için aşağıdaki olay işleyicisini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="28b1b-125">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="28b1b-126">Olay işleyicisi, kullanıcı `cts` iptal istediğinde durumu bildirmek için <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="28b1b-126">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>

    ```csharp
    // ***Add an event handler for the Cancel button.
    private void cancelButton_Click(object sender, RoutedEventArgs e)
    {
        if (cts != null)
        {
            cts.Cancel();
        }
    }
    ```

3. <span data-ttu-id="28b1b-127">**Başlat** düğmesi için olay işleyicisinde aşağıdaki `startButton_Click`değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="28b1b-127">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>

    - <span data-ttu-id="28b1b-128">Instantiate `CancellationTokenSource`, `cts`.</span><span class="sxs-lookup"><span data-stu-id="28b1b-128">Instantiate the `CancellationTokenSource`, `cts`.</span></span>

        ```csharp
        // ***Instantiate the CancellationTokenSource.
        cts = new CancellationTokenSource();
        ```

    - <span data-ttu-id="28b1b-129">Belirli bir `AccessTheWebAsync`web sitesinin içeriğini indiren çağrıda, <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> bir `cts` argüman olarak özelliğini gönderin.</span><span class="sxs-lookup"><span data-stu-id="28b1b-129">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="28b1b-130">İptal `Token` istenirse özellik iletiyi yayır.</span><span class="sxs-lookup"><span data-stu-id="28b1b-130">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="28b1b-131">Kullanıcı indirme işlemini iptal etmeyi seçerse ileti görüntüleyen bir catch bloğu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="28b1b-131">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="28b1b-132">Aşağıdaki kod değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="28b1b-132">The following code shows the changes.</span></span>

        ```csharp
        try
        {
            // ***Send a token to carry the message if cancellation is requested.
            int contentLength = await AccessTheWebAsync(cts.Token);
            resultsTextBox.Text += $"\r\nLength of the downloaded string: {contentLength}.\r\n";
        }
        // *** If cancellation is requested, an OperationCanceledException results.
        catch (OperationCanceledException)
        {
            resultsTextBox.Text += "\r\nDownload canceled.\r\n";
        }
        catch (Exception)
        {
            resultsTextBox.Text += "\r\nDownload failed.\r\n";
        }
        ```

4. <span data-ttu-id="28b1b-133">`AccessTheWebAsync`In, bir <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> web sitesinin `GetAsync` içeriğini <xref:System.Net.Http.HttpClient> indirmek için türünde yöntemin aşırı yüklenmesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="28b1b-133">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="28b1b-134">Pass `ct`, <xref:System.Threading.CancellationToken> parametresi `AccessTheWebAsync`, ikinci bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="28b1b-134">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="28b1b-135">Kullanıcı **İptal** düğmesini seçerse belirteç iletiyi taşır.</span><span class="sxs-lookup"><span data-stu-id="28b1b-135">The token carries the message if the user chooses the **Cancel** button.</span></span>

     <span data-ttu-id="28b1b-136">Aşağıdaki kod' daki `AccessTheWebAsync`değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="28b1b-136">The following code shows the changes in `AccessTheWebAsync`.</span></span>

    ```csharp
    // ***Provide a parameter for the CancellationToken.
    async Task<int> AccessTheWebAsync(CancellationToken ct)
    {
        HttpClient client = new HttpClient();

        resultsTextBox.Text += "\r\nReady to download.\r\n";

        // You might need to slow things down to have a chance to cancel.
        await Task.Delay(250);

        // GetAsync returns a Task<HttpResponseMessage>.
        // ***The ct argument carries the message if the Cancel button is chosen.
        HttpResponseMessage response = await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct);

        // Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        // The result of the method is the length of the downloaded website.
        return urlContents.Length;
    }
    ```

5. <span data-ttu-id="28b1b-137">Programı iptal etmezseniz, aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="28b1b-137">If you don’t cancel the program, it produces the following output.</span></span>

    ```text
    Ready to download.
    Length of the downloaded string: 158125.
    ```

     <span data-ttu-id="28b1b-138">Program içeriği indirmeyi tamamlamadan önce **İptal** düğmesini seçerseniz, program aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="28b1b-138">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>

    ```text
    Ready to download.
    Download canceled.
    ```

## <a name="cancel-a-list-of-tasks"></a><span data-ttu-id="28b1b-139">Görev listesini iptal etme</span><span class="sxs-lookup"><span data-stu-id="28b1b-139">Cancel a list of tasks</span></span>

<span data-ttu-id="28b1b-140">Önceki örneği, her görevle aynı `CancellationTokenSource` örneği ilişkilendirerek birçok görevi iptal etmek için genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28b1b-140">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="28b1b-141">**İptal** düğmesini seçerseniz, henüz tamamlanmamış tüm görevleri iptal emiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="28b1b-141">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>

### <a name="download-the-example"></a><span data-ttu-id="28b1b-142">Örneği indirin</span><span class="sxs-lookup"><span data-stu-id="28b1b-142">Download the example</span></span>

<span data-ttu-id="28b1b-143">Windows Presentation Foundation (WPF) projesinin tamamını [Async Sample: Fine Tuning Application'dan](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) indirebilir ve ardından aşağıdaki adımları izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28b1b-143">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="28b1b-144">İndirdiğiniz dosyayı sıkıştırın ve Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="28b1b-144">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="28b1b-145">Menü çubuğunda **Dosya** > **Aç** > **Projesi/Çözümü'nü**seçin.</span><span class="sxs-lookup"><span data-stu-id="28b1b-145">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="28b1b-146">**Projeyi Aç** iletişim kutusunda, sıkıştırdığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="28b1b-146">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="28b1b-147">**Solution**Explorer'da, **CancelAListOfTasks** projesinin kısayol menüsünü açın ve ardından **StartUp Project olarak ayarla'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="28b1b-147">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="28b1b-148">Projeyi çalıştırmak için **F5** tuşunu seçin.</span><span class="sxs-lookup"><span data-stu-id="28b1b-148">Choose the **F5** key to run the project.</span></span>

     <span data-ttu-id="28b1b-149">Projeyi hata ayıklamadan çalıştırmak için **Ctrl**+**F5** tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="28b1b-149">Choose the **Ctrl**+**F5** keys to run the project without debugging it.</span></span>

<span data-ttu-id="28b1b-150">Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyalarını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28b1b-150">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>

### <a name="build-the-example"></a><span data-ttu-id="28b1b-151">Örneği derleme</span><span class="sxs-lookup"><span data-stu-id="28b1b-151">Build the example</span></span>

<span data-ttu-id="28b1b-152">Örneği adım adım genişletmek için, "Örneği İndirme" bölümündeki yönergeleri izleyin, ancak **StartUp Project**olarak **CancelATask'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="28b1b-152">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="28b1b-153">Bu projeye aşağıdaki değişiklikleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="28b1b-153">Add the following changes to that project.</span></span> <span data-ttu-id="28b1b-154">Yıldız işaretleri programdaki değişiklikleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="28b1b-154">Asterisks mark the changes in the program.</span></span>

1. <span data-ttu-id="28b1b-155">Web adreslerinin listesini oluşturmak için bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="28b1b-155">Add a method to create a list of web addresses.</span></span>

    ```csharp
    // ***Add a method that creates a list of web addresses.
    private List<string> SetUpURLList()
    {
        List<string> urls = new List<string>
        {
            "https://msdn.microsoft.com",
            "https://msdn.microsoft.com/library/hh290138.aspx",
            "https://msdn.microsoft.com/library/hh290140.aspx",
            "https://msdn.microsoft.com/library/dd470362.aspx",
            "https://msdn.microsoft.com/library/aa578028.aspx",
            "https://msdn.microsoft.com/library/ms404677.aspx",
            "https://msdn.microsoft.com/library/ff730837.aspx"
        };
        return urls;
    }
    ```

2. <span data-ttu-id="28b1b-156">Yöntemi ' `AccessTheWebAsync`de çağırın.</span><span class="sxs-lookup"><span data-stu-id="28b1b-156">Call the method in `AccessTheWebAsync`.</span></span>

    ```csharp
    // ***Call SetUpURLList to make a list of web addresses.
    List<string> urlList = SetUpURLList();
    ```

3. <span data-ttu-id="28b1b-157">Listedeki her `AccessTheWebAsync` web adresini işlemek için aşağıdaki döngüyü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="28b1b-157">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>

    ```csharp
    // ***Add a loop to process the list of web addresses.
    foreach (var url in urlList)
    {
        // GetAsync returns a Task<HttpResponseMessage>.
        // Argument ct carries the message if the Cancel button is chosen.
        // ***Note that the Cancel button can cancel all remaining downloads.
        HttpResponseMessage response = await client.GetAsync(url, ct);

        // Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        resultsTextBox.Text +=
            $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
    }
    ```

4. <span data-ttu-id="28b1b-158">Uzunlukları `AccessTheWebAsync` görüntülediği için, yöntemin hiçbir şeyi döndürmesine gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="28b1b-158">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="28b1b-159">İade deyimini kaldırın ve yöntemin dönüş <xref:System.Threading.Tasks.Task> türünü <xref:System.Threading.Tasks.Task%601>yerine değiştirin.</span><span class="sxs-lookup"><span data-stu-id="28b1b-159">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>

    ```csharp
    async Task AccessTheWebAsync(CancellationToken ct)
    ```

     <span data-ttu-id="28b1b-160">İfade yerine `startButton_Click` deyim kullanarak yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="28b1b-160">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>

    ```csharp
    await AccessTheWebAsync(cts.Token);
    ```

5. <span data-ttu-id="28b1b-161">Programı iptal etmezseniz, aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="28b1b-161">If you don’t cancel the program, it produces the following output.</span></span>

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Length of the downloaded string: 158124.

    Length of the downloaded string: 204890.

    Length of the downloaded string: 175488.

    Length of the downloaded string: 145790.

    Downloads complete.
    ```

     <span data-ttu-id="28b1b-162">İndirmeler tamamlanmadan önce **İptal** düğmesini seçerseniz, çıktı iptalden önce tamamlanan indirmelerin uzunluklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="28b1b-162">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="complete-examples"></a><span data-ttu-id="28b1b-163">Tam örnekler</span><span class="sxs-lookup"><span data-stu-id="28b1b-163">Complete examples</span></span>

<span data-ttu-id="28b1b-164">Aşağıdaki bölümler, önceki örneklerin her biri için kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="28b1b-164">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="28b1b-165">Için bir başvuru eklemeniz <xref:System.Net.Http>gerektiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="28b1b-165">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="28b1b-166">Projeleri [Async Sample: Fine Tuning Your Application'dan](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28b1b-166">You can download the projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

### <a name="example---cancel-a-task"></a><span data-ttu-id="28b1b-167">Örnek - Görevi iptal etme</span><span class="sxs-lookup"><span data-stu-id="28b1b-167">Example - Cancel a task</span></span>

<span data-ttu-id="28b1b-168">Aşağıdaki kod, tek bir görevi iptal eden örnek için dosya MainWindow.xaml.csnın tamamıdır.</span><span class="sxs-lookup"><span data-stu-id="28b1b-168">The following code is the complete MainWindow.xaml.cs file for the example that cancels a single task.</span></span>

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

// Add a using directive and a reference for System.Net.Http.
using System.Net.Http;

// Add the following using directive for System.Threading.

using System.Threading;
namespace CancelATask
{
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;

        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // ***Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            resultsTextBox.Clear();

            try
            {
                // ***Send a token to carry the message if cancellation is requested.
                int contentLength = await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {contentLength}.\r\n";
            }
            // *** If cancellation is requested, an OperationCanceledException results.
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownload canceled.\r\n";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownload failed.\r\n";
            }

            // ***Set the CancellationTokenSource to null when the download is complete.
            cts = null;
        }

        // ***Add an event handler for the Cancel button.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        // ***Provide a parameter for the CancellationToken.
        async Task<int> AccessTheWebAsync(CancellationToken ct)
        {
            HttpClient client = new HttpClient();

            resultsTextBox.Text += "\r\nReady to download.\r\n";

            // You might need to slow things down to have a chance to cancel.
            await Task.Delay(250);

            // GetAsync returns a Task<HttpResponseMessage>.
            // ***The ct argument carries the message if the Cancel button is chosen.
            HttpResponseMessage response = await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct);

            // Retrieve the website contents from the HttpResponseMessage.
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

            // The result of the method is the length of the downloaded website.
            return urlContents.Length;
        }
    }

    // Output for a successful download:

    // Ready to download.

    // Length of the downloaded string: 158125.

    // Or, if you cancel:

    // Ready to download.

    // Download canceled.
}
```

### <a name="example---cancel-a-list-of-tasks"></a><span data-ttu-id="28b1b-169">Örnek - Görev listesini iptal etme</span><span class="sxs-lookup"><span data-stu-id="28b1b-169">Example - Cancel a list of tasks</span></span>

<span data-ttu-id="28b1b-170">Aşağıdaki kod, görev listesini iptal eden örnek için MainWindow.xaml.cs dosyanın tamamıdır.</span><span class="sxs-lookup"><span data-stu-id="28b1b-170">The following code is the complete MainWindow.xaml.cs file for the example that cancels a list of tasks.</span></span>

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

// Add a using directive and a reference for System.Net.Http.
using System.Net.Http;

// Add the following using directive for System.Threading.
using System.Threading;

namespace CancelAListOfTasks
{
    public partial class MainWindow : Window
    {
        // Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;

        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            resultsTextBox.Clear();

            try
            {
                await AccessTheWebAsync(cts.Token);
                // ***Small change in the display lines.
                resultsTextBox.Text += "\r\nDownloads complete.";
            }
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownloads canceled.";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownloads failed.";
            }

            // Set the CancellationTokenSource to null when the download is complete.
            cts = null;
        }

        // Add an event handler for the Cancel button.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        // Provide a parameter for the CancellationToken.
        // ***Change the return type to Task because the method has no return statement.
        async Task AccessTheWebAsync(CancellationToken ct)
        {
            // Declare an HttpClient object.
            HttpClient client = new HttpClient();

            // ***Call SetUpURLList to make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // ***Add a loop to process the list of web addresses.
            foreach (var url in urlList)
            {
                // GetAsync returns a Task<HttpResponseMessage>.
                // Argument ct carries the message if the Cancel button is chosen.
                // ***Note that the Cancel button can cancel all remaining downloads.
                HttpResponseMessage response = await client.GetAsync(url, ct);

                // Retrieve the website contents from the HttpResponseMessage.
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            }
        }

        // ***Add a method that creates a list of web addresses.
        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }
    }

    // Output if you do not choose to cancel:

    //Length of the downloaded string: 35939.

    //Length of the downloaded string: 237682.

    //Length of the downloaded string: 128607.

    //Length of the downloaded string: 158124.

    //Length of the downloaded string: 204890.

    //Length of the downloaded string: 175488.

    //Length of the downloaded string: 145790.

    //Downloads complete.

    // Sample output if you choose to cancel:

    //Length of the downloaded string: 35939.

    //Length of the downloaded string: 237682.

    //Length of the downloaded string: 128607.

    //Downloads canceled.
}
```

## <a name="see-also"></a><span data-ttu-id="28b1b-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28b1b-171">See also</span></span>

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [<span data-ttu-id="28b1b-172">Async ve await ile Asynchronous Programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="28b1b-172">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="28b1b-173">Async Uygulamanızda İnce Ayar (C#)</span><span class="sxs-lookup"><span data-stu-id="28b1b-173">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="28b1b-174">Async Örnek: Uygulamanızı İyi Ayar</span><span class="sxs-lookup"><span data-stu-id="28b1b-174">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
