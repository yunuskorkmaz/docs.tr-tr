---
title: Zaman uyumsuz bir görev veya görevleri (C#) listesini iptal etme
ms.date: 07/20/2015
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 2aadfccd8b38922b72dfc21daf27f610adffc922
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741354"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a><span data-ttu-id="b3d9c-102">Zaman uyumsuz bir görev veya görevleri (C#) listesini iptal etme</span><span class="sxs-lookup"><span data-stu-id="b3d9c-102">Cancel an Async Task or a List of Tasks (C#)</span></span>
<span data-ttu-id="b3d9c-103">Zaman uyumsuz bir uygulamanın bitmesini beklemek istemiyorsanız, iptal etmek için kullanabileceğiniz bir düğme ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="b3d9c-104">Bu konudaki örnekleri izleyerek, Web sitelerinin bir listesiyle ya da bir Web sitesinin içeriklerini indiren bir uygulama için bir iptal düğmesi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>  
  
 <span data-ttu-id="b3d9c-105">Kullanıcı arabirimini örneklerde, [Fine-Tuning Async uygulamanızda (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) açıklar.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-105">The examples use the UI that [Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) describes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3d9c-106">Yeni bilgisayarınızda yüklü veya örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <a name="BKMK_CancelaTask"></a> <span data-ttu-id="b3d9c-107">Bir görevi iptal etme</span><span class="sxs-lookup"><span data-stu-id="b3d9c-107">Cancel a Task</span></span>  
 <span data-ttu-id="b3d9c-108">İlk örnek ilişkilendirir **iptal** tek bir yükleme göreviyle düğmesi.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="b3d9c-109">Uygulama içeriği karşıdan yüklerken düğmeyi seçerseniz, karşıdan yükleme iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="b3d9c-110">Örneği indirme</span><span class="sxs-lookup"><span data-stu-id="b3d9c-110">Downloading the Example</span></span>  
 <span data-ttu-id="b3d9c-111">Tüm Windows Presentation Foundation (WPF) projeden indirebileceğiniz [zaman uyumsuz örneği: ince uygulamanıza](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) ve sonra aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="b3d9c-112">İndirdiğiniz dosyanın sıkıştırmasını açın ve sonra Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="b3d9c-113">Menü çubuğunda, **dosya**, **açık**, **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="b3d9c-114">İçinde **Proje Aç** iletişim kutusunda, açtığınız örnek kodu barındıran klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="b3d9c-115">İçinde **Çözüm Gezgini**, kısayol menüsünü açın **CancelATask** proje ve ardından **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="b3d9c-116">Projeyi çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="b3d9c-117">Projeyi hata ayıklama olmadan çalıştırmak için Ctrl + F5 tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="b3d9c-118">Projeyi indirmek istemiyorsanız, bu konunun sonunda MainWindow.xaml.cs dosyalarını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-118">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="b3d9c-119">Örneği oluşturma</span><span class="sxs-lookup"><span data-stu-id="b3d9c-119">Building the Example</span></span>  
 <span data-ttu-id="b3d9c-120">Aşağıdaki değişiklikleri ekleyin bir **iptal** bir Web sitesi yükleyen bir uygulamaya düğmesi.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-120">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="b3d9c-121">İndirme veya örnek oluşturmak istemiyorsanız, bu konunun sonundaki "Tam örnekler" bölümünde yer alan son ürünü gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-121">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="b3d9c-122">Yıldız işaretleri, koddaki değişiklikleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-122">Asterisks mark the changes in the code.</span></span>  
  
 <span data-ttu-id="b3d9c-123">Örneği oluşturmak için kendinize, adım adım "Örneği indirme" bölümündeki yönergeleri izleyin, ancak seçin **başlangıç projesi** olarak **başlangıç projesi** yerine **CancelATask** .</span><span class="sxs-lookup"><span data-stu-id="b3d9c-123">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>  
  
 <span data-ttu-id="b3d9c-124">Ardından bu projenin MainWindow.xaml.cs dosyasına aşağıdaki değişiklikleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-124">Then add the following changes to the MainWindow.xaml.cs file of that project.</span></span>  
  
1.  <span data-ttu-id="b3d9c-125">Bildirme bir `CancellationTokenSource` değişken `cts`, kendisine erişen tüm yöntemler için kapsam dahilinde olan.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-125">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>  
  
    ```csharp  
    public partial class MainWindow : Window  
    {  
        // ***Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
    ```  
  
2.  <span data-ttu-id="b3d9c-126">İçin aşağıdaki olay işleyicisini ekleyelim **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-126">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="b3d9c-127">Olay işleyicisi kullanır <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> yöntemi bildirmek için `cts` kullanıcı iptal isteğinde bulunduğunda.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-127">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>  
  
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
  
3.  <span data-ttu-id="b3d9c-128">Aşağıdaki değişiklikler olay işleyicisi yapma **Başlat** düğme `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-128">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>  
  
    -   <span data-ttu-id="b3d9c-129">Örneği `CancellationTokenSource`, `cts`.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-129">Instantiate the `CancellationTokenSource`, `cts`.</span></span>  
  
        ```csharp  
        // ***Instantiate the CancellationTokenSource.  
        cts = new CancellationTokenSource();  
        ```  
  
    -   <span data-ttu-id="b3d9c-130">Çağrısında `AccessTheWebAsync`, belirtilen bir Web sitesinin içeriklerini karşıdan yükler, gönderme <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> özelliği `cts` bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-130">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="b3d9c-131">`Token` Özelliği, iptal istenirse iletiyi yayar.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-131">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="b3d9c-132">Kullanıcı karşıdan yükleme işlemini iptal etmeyi seçerse ileti görüntüleyen bir catch bloğu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-132">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="b3d9c-133">Aşağıdaki kod değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-133">The following code shows the changes.</span></span>  
  
        ```csharp  
        try  
        {  
            // ***Send a token to carry the message if cancellation is requested.  
            int contentLength = await AccessTheWebAsync(cts.Token);  
            resultsTextBox.Text +=  
                String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
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
  
4.  <span data-ttu-id="b3d9c-134">İçinde `AccessTheWebAsync`, kullanın <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> aşırı yükünü `GetAsync` yönteminde <xref:System.Net.Http.HttpClient> bir Web sitesinin içeriklerini karşıdan yüklemek için türü.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-134">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="b3d9c-135">Geçirmek `ct`, <xref:System.Threading.CancellationToken> parametresinin `AccessTheWebAsync`, ikinci bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-135">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="b3d9c-136">Kullanıcı seçerse belirteç iletiyi taşır **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-136">The token carries the message if the user chooses the **Cancel** button.</span></span>  
  
     <span data-ttu-id="b3d9c-137">Aşağıdaki kod değişiklikleri göstermektedir `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-137">The following code shows the changes in `AccessTheWebAsync`.</span></span>  
  
    ```csharp  
    // ***Provide a parameter for the CancellationToken.  
    async Task<int> AccessTheWebAsync(CancellationToken ct)  
    {  
        HttpClient client = new HttpClient();  
  
        resultsTextBox.Text +=  
            String.Format("\r\nReady to download.\r\n");  
  
        // You might need to slow things down to have a chance to cancel.  
        await Task.Delay(250);  
  
        // GetAsync returns a Task<HttpResponseMessage>.   
        // ***The ct argument carries the message if the Cancel button is chosen.  
        HttpResponseMessage response = await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct);  
  
        // Retrieve the website contents from the HttpResponseMessage.  
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
        // The result of the method is the length of the downloaded website.  
        return urlContents.Length;  
    }  
    ```  
  
5.  <span data-ttu-id="b3d9c-138">Programı iptal etmezseniz, aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-138">If you don’t cancel the program, it produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Length of the downloaded string: 158125.  
    ```  
  
     <span data-ttu-id="b3d9c-139">Seçerseniz **iptal** düğmesi önce program içeriği karşıdan, program şu çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-139">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Download canceled.  
    ```  
  
##  <a name="BKMK_CancelaListofTasks"></a> <span data-ttu-id="b3d9c-140">Görev listesini iptal etme</span><span class="sxs-lookup"><span data-stu-id="b3d9c-140">Cancel a List of Tasks</span></span>  
 <span data-ttu-id="b3d9c-141">Aynı ilişkilendirerek birçok görevi iptal etmek için önceki örneği genişletebilirsiniz `CancellationTokenSource` her görev örneği.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-141">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="b3d9c-142">Seçerseniz **iptal** düğmesi, henüz tamamlanmamış tüm görevleri iptal.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-142">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="b3d9c-143">Örneği indirme</span><span class="sxs-lookup"><span data-stu-id="b3d9c-143">Downloading the Example</span></span>  
 <span data-ttu-id="b3d9c-144">Tüm Windows Presentation Foundation (WPF) projeden indirebileceğiniz [zaman uyumsuz örneği: ince uygulamanıza](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) ve sonra aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-144">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="b3d9c-145">İndirdiğiniz dosyanın sıkıştırmasını açın ve sonra Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-145">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="b3d9c-146">Menü çubuğunda, **dosya**, **açık**, **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-146">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="b3d9c-147">İçinde **Proje Aç** iletişim kutusunda, açtığınız örnek kodu barındıran klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-147">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="b3d9c-148">İçinde **Çözüm Gezgini**, kısayol menüsünü açın **CancelAListOfTasks** proje ve ardından **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-148">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="b3d9c-149">Projeyi çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-149">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="b3d9c-150">Projeyi hata ayıklama olmadan çalıştırmak için Ctrl + F5 tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-150">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="b3d9c-151">Projeyi indirmek istemiyorsanız, bu konunun sonunda MainWindow.xaml.cs dosyalarını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-151">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="b3d9c-152">Örneği oluşturma</span><span class="sxs-lookup"><span data-stu-id="b3d9c-152">Building the Example</span></span>  
 <span data-ttu-id="b3d9c-153">Örneği genişletmek için kendiniz adım adım "Örneği indirme" bölümündeki yönergeleri izleyin, ancak seçin **CancelATask** olarak **başlangıç projesi**.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-153">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="b3d9c-154">Aşağıdaki değişiklikleri bu projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-154">Add the following changes to that project.</span></span> <span data-ttu-id="b3d9c-155">Yıldız işaretleri, programdaki değişiklikleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-155">Asterisks mark the changes in the program.</span></span>  
  
1.  <span data-ttu-id="b3d9c-156">Web adresleri listesi oluşturmak için bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-156">Add a method to create a list of web addresses.</span></span>  
  
    ```csharp  
    // ***Add a method that creates a list of web addresses.  
    private List<string> SetUpURLList()  
    {  
        List<string> urls = new List<string>   
        {   
            "http://msdn.microsoft.com",  
            "http://msdn.microsoft.com/library/hh290138.aspx",  
            "http://msdn.microsoft.com/library/hh290140.aspx",  
            "http://msdn.microsoft.com/library/dd470362.aspx",  
            "http://msdn.microsoft.com/library/aa578028.aspx",  
            "http://msdn.microsoft.com/library/ms404677.aspx",  
            "http://msdn.microsoft.com/library/ff730837.aspx"  
        };  
        return urls;  
    }  
    ```  
  
2.  <span data-ttu-id="b3d9c-157">Yöntem çağrısı `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-157">Call the method in `AccessTheWebAsync`.</span></span>  
  
    ```csharp  
    // ***Call SetUpURLList to make a list of web addresses.  
    List<string> urlList = SetUpURLList();  
    ```  
  
3.  <span data-ttu-id="b3d9c-158">İçine şu döngüyü ekleyin `AccessTheWebAsync` listesindeki her bir web adresini işlemek için.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-158">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>  
  
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
            String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
    }  
    ```  
  
4.  <span data-ttu-id="b3d9c-159">Çünkü `AccessTheWebAsync` görüntüler uzunlukları, yöntemin herhangi bir şey getirmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-159">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="b3d9c-160">Return ifadesini kaldırın ve yöntemin dönüş türünü değiştirmek <xref:System.Threading.Tasks.Task> yerine <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-160">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
    ```csharp  
    async Task AccessTheWebAsync(CancellationToken ct)  
    ```  
  
     <span data-ttu-id="b3d9c-161">İçinden yöntemi çağırın `startButton_Click` ifade yerine bir deyim kullanarak.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-161">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>  
  
    ```csharp  
    await AccessTheWebAsync(cts.Token);  
    ```  
  
5.  <span data-ttu-id="b3d9c-162">Programı iptal etmezseniz, aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-162">If you don’t cancel the program, it produces the following output.</span></span>  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Length of the downloaded string: 158124.  
  
    Length of the downloaded string: 204890.  
  
    Length of the downloaded string: 175488.  
  
    Length of the downloaded string: 145790.  
  
    Downloads complete.  
    ```  
  
     <span data-ttu-id="b3d9c-163">Seçerseniz **iptal** indirmeleri tam düğmesini, çıktı iptalden önce tamamlanan karşıdan yüklemelerin uzunluklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-163">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Downloads canceled.  
    ```  
  
##  <a name="BKMK_CompleteExamples"></a> <span data-ttu-id="b3d9c-164">Tam örnekler</span><span class="sxs-lookup"><span data-stu-id="b3d9c-164">Complete Examples</span></span>  
 <span data-ttu-id="b3d9c-165">Aşağıdaki bölümlerde her önceki örnek kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-165">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="b3d9c-166">İçin bir başvuru eklemeniz gerektiğini unutmayın <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-166">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="b3d9c-167">İçinden projeleri karşıdan yükleyebileceğiniz [zaman uyumsuz örneği: ince uygulamanıza](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="b3d9c-167">You can download the projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
### <a name="cancel-a-task-example"></a><span data-ttu-id="b3d9c-168">Bir görevi iptal etme örneği</span><span class="sxs-lookup"><span data-stu-id="b3d9c-168">Cancel a Task Example</span></span>  
 <span data-ttu-id="b3d9c-169">Aşağıdaki kod, tek bir görevi iptal eden örnek için tam MainWindow.xaml.cs dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-169">The following code is the complete MainWindow.xaml.cs file for the example that cancels a single task.</span></span>  
  
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
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
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
  
            resultsTextBox.Text +=  
                String.Format("\r\nReady to download.\r\n");  
  
            // You might need to slow things down to have a chance to cancel.  
            await Task.Delay(250);  
  
            // GetAsync returns a Task<HttpResponseMessage>.   
            // ***The ct argument carries the message if the Cancel button is chosen.  
            HttpResponseMessage response = await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct);  
  
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
  
### <a name="cancel-a-list-of-tasks-example"></a><span data-ttu-id="b3d9c-170">Örnek Görevler listesini iptal etme</span><span class="sxs-lookup"><span data-stu-id="b3d9c-170">Cancel a List of Tasks Example</span></span>  
 <span data-ttu-id="b3d9c-171">Aşağıdaki kod, bir Görevler listesini iptal eden örnek için tam MainWindow.xaml.cs dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-171">The following code is the complete MainWindow.xaml.cs file for the example that cancels a list of tasks.</span></span>  
  
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
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
            }  
        }  
  
        // ***Add a method that creates a list of web addresses.  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
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
  
## <a name="see-also"></a><span data-ttu-id="b3d9c-172">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-172">See Also</span></span>

- <xref:System.Threading.CancellationTokenSource>  
- <xref:System.Threading.CancellationToken>  
- [<span data-ttu-id="b3d9c-173">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="b3d9c-173">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
- [<span data-ttu-id="b3d9c-174">(C#) Async uygulamanızda hassas ayar yapma</span><span class="sxs-lookup"><span data-stu-id="b3d9c-174">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
- [<span data-ttu-id="b3d9c-175">Zaman uyumsuz örneği: Uygulamanıza ince</span><span class="sxs-lookup"><span data-stu-id="b3d9c-175">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
