---
title: "Zaman uyumsuz görevi veya görev (C#) listesini iptal etme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 78becece40b4b527869c593f8a1fe1eeba1f1f51
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a><span data-ttu-id="5065b-102">Zaman uyumsuz görevi veya görev (C#) listesini iptal etme</span><span class="sxs-lookup"><span data-stu-id="5065b-102">Cancel an Async Task or a List of Tasks (C#)</span></span>
<span data-ttu-id="5065b-103">Zaman uyumsuz uygulama tamamlanmasını beklemek istemiyorsanız, iptal etmek için kullanabileceğiniz bir düğme ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5065b-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="5065b-104">Bu konudaki örnekler izleyerek bir Web sitesi içeriğini ya da Web sitelerinin bir listesini indirir bir uygulamaya iptal düğmesi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5065b-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>  
  
 <span data-ttu-id="5065b-105">Kullanıcı arabirimini örneklerde, [Fine-Tuning zaman uyumsuz uygulamanız (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) açıklar.</span><span class="sxs-lookup"><span data-stu-id="5065b-105">The examples use the UI that [Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) describes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5065b-106">Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 olmalıdır veya daha yeni bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="5065b-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <a name="BKMK_CancelaTask"></a><span data-ttu-id="5065b-107">Bir görevi iptal etme</span><span class="sxs-lookup"><span data-stu-id="5065b-107">Cancel a Task</span></span>  
 <span data-ttu-id="5065b-108">İlk örnek ilişkilendirir **iptal** tek indirme görev düğme.</span><span class="sxs-lookup"><span data-stu-id="5065b-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="5065b-109">Uygulama içeriği indirirken düğmesini seçerseniz, indirme iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="5065b-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="5065b-110">Örnek indirme</span><span class="sxs-lookup"><span data-stu-id="5065b-110">Downloading the Example</span></span>  
 <span data-ttu-id="5065b-111">Tam Windows Presentation Foundation (WPF) projeden indirebilirsiniz [zaman uyumsuz örnek: ince ayar uygulamanız](http://go.microsoft.com/fwlink/?LinkId=255046) ve ardından aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="5065b-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="5065b-112">İndirdiğiniz dosyanın sıkıştırmasını ve Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="5065b-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="5065b-113">Menü çubuğunda seçin **dosya**, **açık**, **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="5065b-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="5065b-114">İçinde **Proje Aç** iletişim kutusunda, sıkıştırması örnek kod tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="5065b-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="5065b-115">İçinde **Çözüm Gezgini**, kısayol menüsünü açın **CancelATask** proje ve ardından **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="5065b-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="5065b-116">Projeyi çalıştırmak için F5 tuşuna seçin.</span><span class="sxs-lookup"><span data-stu-id="5065b-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="5065b-117">Hata ayıklama olmadan projeyi çalıştırmak için Ctrl + F5 anahtarları'i seçin.</span><span class="sxs-lookup"><span data-stu-id="5065b-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="5065b-118">Projenizi indirin istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyalarını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5065b-118">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="5065b-119">Örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="5065b-119">Building the Example</span></span>  
 <span data-ttu-id="5065b-120">Aşağıdaki değişiklikleri eklemek bir **iptal** düğmesi uygulamaya bir Web sitesi yükler.</span><span class="sxs-lookup"><span data-stu-id="5065b-120">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="5065b-121">İndirme veya örnek oluşturmak istemiyorsanız, bu konunun sonunda "Tam örnekler" bölümündeki son ürün gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5065b-121">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="5065b-122">Kod değişiklikleri yıldızlar işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="5065b-122">Asterisks mark the changes in the code.</span></span>  
  
 <span data-ttu-id="5065b-123">Örnek oluşturmak için kendiniz, adım adım "örnek indirme" bölümündeki yönergeleri izleyin, ancak seçin **StarterCode** olarak **başlangıç projesi** yerine **CancelATask** .</span><span class="sxs-lookup"><span data-stu-id="5065b-123">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>  
  
 <span data-ttu-id="5065b-124">Ardından aşağıdaki değişiklikleri proje MainWindow.xaml.cs dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5065b-124">Then add the following changes to the MainWindow.xaml.cs file of that project.</span></span>  
  
1.  <span data-ttu-id="5065b-125">Bildirme bir `CancellationTokenSource` değişkeni `cts`, kapsamında erişim tüm yöntemleri için olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="5065b-125">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>  
  
    ```csharp  
    public partial class MainWindow : Window  
    {  
        // ***Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
    ```  
  
2.  <span data-ttu-id="5065b-126">İçin aşağıdaki olay işleyicisi ekleme **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="5065b-126">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="5065b-127">Olay işleyicisi kullanan <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> bildirmek için yöntemi `cts` kullanıcı iptal isteğinde bulunduğunda.</span><span class="sxs-lookup"><span data-stu-id="5065b-127">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>  
  
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
  
3.  <span data-ttu-id="5065b-128">Aşağıdaki değişiklikler olay işleyicisi yapma **Başlat** düğmesini `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="5065b-128">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>  
  
    -   <span data-ttu-id="5065b-129">Örneği `CancellationTokenSource`, `cts`.</span><span class="sxs-lookup"><span data-stu-id="5065b-129">Instantiate the `CancellationTokenSource`, `cts`.</span></span>  
  
        ```csharp  
        // ***Instantiate the CancellationTokenSource.  
        cts = new CancellationTokenSource();  
        ```  
  
    -   <span data-ttu-id="5065b-130">Çağrısında `AccessTheWebAsync`, belirtilen bir Web sitesi içeriğini indirir, gönderme <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> özelliği `cts` bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="5065b-130">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="5065b-131">`Token` Özelliği iptal isteniyorsa ileti yayar.</span><span class="sxs-lookup"><span data-stu-id="5065b-131">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="5065b-132">Kullanıcı yükleme işlemi iptal etmek seçerse, bir ileti görüntüler bir catch bloğu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5065b-132">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="5065b-133">Aşağıdaki kod değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="5065b-133">The following code shows the changes.</span></span>  
  
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
  
4.  <span data-ttu-id="5065b-134">İçinde `AccessTheWebAsync`, kullanın <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> , aşırı `GetAsync` yönteminde <xref:System.Net.Http.HttpClient> bir Web sitesi içeriğini indirmek için türü.</span><span class="sxs-lookup"><span data-stu-id="5065b-134">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="5065b-135">Geçirmek `ct`, <xref:System.Threading.CancellationToken> parametresinin `AccessTheWebAsync`, ikinci bağımsız değişkeni olarak.</span><span class="sxs-lookup"><span data-stu-id="5065b-135">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="5065b-136">Kullanıcı seçerse belirteç ileti taşır **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="5065b-136">The token carries the message if the user chooses the **Cancel** button.</span></span>  
  
     <span data-ttu-id="5065b-137">Aşağıdaki kod değişiklikleri gösterir `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="5065b-137">The following code shows the changes in `AccessTheWebAsync`.</span></span>  
  
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
  
5.  <span data-ttu-id="5065b-138">Program iptal etme, şu çıkışı üretir.</span><span class="sxs-lookup"><span data-stu-id="5065b-138">If you don’t cancel the program, it produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Length of the downloaded string: 158125.  
    ```  
  
     <span data-ttu-id="5065b-139">Seçerseniz **iptal** düğmesi program önce tamamlanır içerik indirme, program şu çıkışı üretir.</span><span class="sxs-lookup"><span data-stu-id="5065b-139">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Download canceled.  
    ```  
  
##  <a name="BKMK_CancelaListofTasks"></a><span data-ttu-id="5065b-140">Görev listesini iptal etme</span><span class="sxs-lookup"><span data-stu-id="5065b-140">Cancel a List of Tasks</span></span>  
 <span data-ttu-id="5065b-141">Aynı ilişkilendirerek birçok görevleri iptal etmek için önceki örnekte genişletebilirsiniz `CancellationTokenSource` her görev örneği.</span><span class="sxs-lookup"><span data-stu-id="5065b-141">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="5065b-142">Seçerseniz **iptal** düğmesi, henüz tam olmayan tüm görevler iptal.</span><span class="sxs-lookup"><span data-stu-id="5065b-142">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="5065b-143">Örnek indirme</span><span class="sxs-lookup"><span data-stu-id="5065b-143">Downloading the Example</span></span>  
 <span data-ttu-id="5065b-144">Tam Windows Presentation Foundation (WPF) projeden indirebilirsiniz [zaman uyumsuz örnek: ince ayar uygulamanız](http://go.microsoft.com/fwlink/?LinkId=255046) ve ardından aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="5065b-144">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="5065b-145">İndirdiğiniz dosyanın sıkıştırmasını ve Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="5065b-145">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="5065b-146">Menü çubuğunda seçin **dosya**, **açık**, **proje/çözüm**.</span><span class="sxs-lookup"><span data-stu-id="5065b-146">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="5065b-147">İçinde **Proje Aç** iletişim kutusunda, sıkıştırması örnek kod tutan klasörü açın ve ardından AsyncFineTuningCS için çözüm (.sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="5065b-147">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="5065b-148">İçinde **Çözüm Gezgini**, kısayol menüsünü açın **CancelAListOfTasks** proje ve ardından **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="5065b-148">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="5065b-149">Projeyi çalıştırmak için F5 tuşuna seçin.</span><span class="sxs-lookup"><span data-stu-id="5065b-149">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="5065b-150">Hata ayıklama olmadan projeyi çalıştırmak için Ctrl + F5 anahtarları'i seçin.</span><span class="sxs-lookup"><span data-stu-id="5065b-150">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="5065b-151">Projenizi indirin istemiyorsanız, bu konunun sonundaki MainWindow.xaml.cs dosyalarını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5065b-151">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="5065b-152">Örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="5065b-152">Building the Example</span></span>  
 <span data-ttu-id="5065b-153">Örneği genişletmek için kendiniz, adım adım "örnek indirme" bölümündeki yönergeleri izleyin, ancak seçin **CancelATask** olarak **başlangıç projesi**.</span><span class="sxs-lookup"><span data-stu-id="5065b-153">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="5065b-154">Aşağıdaki değişiklikler bu projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5065b-154">Add the following changes to that project.</span></span> <span data-ttu-id="5065b-155">Yıldız işareti program değişiklikleri işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="5065b-155">Asterisks mark the changes in the program.</span></span>  
  
1.  <span data-ttu-id="5065b-156">Web adresleri listesi oluşturmak için bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5065b-156">Add a method to create a list of web addresses.</span></span>  
  
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
  
2.  <span data-ttu-id="5065b-157">Yöntem çağrısı `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="5065b-157">Call the method in `AccessTheWebAsync`.</span></span>  
  
    ```csharp  
    // ***Call SetUpURLList to make a list of web addresses.  
    List<string> urlList = SetUpURLList();  
    ```  
  
3.  <span data-ttu-id="5065b-158">Aşağıdaki döngüde eklemek `AccessTheWebAsync` listede her web adresini işleyemedi.</span><span class="sxs-lookup"><span data-stu-id="5065b-158">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>  
  
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
  
4.  <span data-ttu-id="5065b-159">Çünkü `AccessTheWebAsync` değil yöntemi uzunlukları gereken her şeyi geri dönmek için görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5065b-159">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="5065b-160">Return deyimi kaldırın ve yöntemin dönüş türünü değiştir <xref:System.Threading.Tasks.Task> yerine <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="5065b-160">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
    ```csharp  
    async Task AccessTheWebAsync(CancellationToken ct)  
    ```  
  
     <span data-ttu-id="5065b-161">Yöntemi çağırın `startButton_Click` yerine bir ifadenin bir deyimi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="5065b-161">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>  
  
    ```csharp  
    await AccessTheWebAsync(cts.Token);  
    ```  
  
5.  <span data-ttu-id="5065b-162">Program iptal etme, şu çıkışı üretir.</span><span class="sxs-lookup"><span data-stu-id="5065b-162">If you don’t cancel the program, it produces the following output.</span></span>  
  
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
  
     <span data-ttu-id="5065b-163">Seçerseniz **iptal** indirmeleri tam önce düğmesi, çıktı içerir önce iptal tamamlandı indirmeleri uzunlukları.</span><span class="sxs-lookup"><span data-stu-id="5065b-163">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Downloads canceled.  
    ```  
  
##  <a name="BKMK_CompleteExamples"></a><span data-ttu-id="5065b-164">Tam örnekleri</span><span class="sxs-lookup"><span data-stu-id="5065b-164">Complete Examples</span></span>  
 <span data-ttu-id="5065b-165">Aşağıdaki bölümler her önceki örnekler için kod içerir.</span><span class="sxs-lookup"><span data-stu-id="5065b-165">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="5065b-166">İçin bir başvuru eklemeniz gerekir fark <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="5065b-166">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="5065b-167">Projelerden indirebilirsiniz [zaman uyumsuz örnek: ince ayar uygulamanız](http://go.microsoft.com/fwlink/?LinkId=255046).</span><span class="sxs-lookup"><span data-stu-id="5065b-167">You can download the projects from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
### <a name="cancel-a-task-example"></a><span data-ttu-id="5065b-168">Bir görev örneği iptal et</span><span class="sxs-lookup"><span data-stu-id="5065b-168">Cancel a Task Example</span></span>  
 <span data-ttu-id="5065b-169">Aşağıdaki kod, tek bir görevi iptal eder örneğin tam MainWindow.xaml.cs dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="5065b-169">The following code is the complete MainWindow.xaml.cs file for the example that cancels a single task.</span></span>  
  
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
  
### <a name="cancel-a-list-of-tasks-example"></a><span data-ttu-id="5065b-170">Görevler örneği listesini iptal etme</span><span class="sxs-lookup"><span data-stu-id="5065b-170">Cancel a List of Tasks Example</span></span>  
 <span data-ttu-id="5065b-171">Aşağıdaki kod, görev listesini iptal eder örneğin tam MainWindow.xaml.cs dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="5065b-171">The following code is the complete MainWindow.xaml.cs file for the example that cancels a list of tasks.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5065b-172">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5065b-172">See Also</span></span>  
 <xref:System.Threading.CancellationTokenSource>  
 <xref:System.Threading.CancellationToken>  
 [<span data-ttu-id="5065b-173">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="5065b-173">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="5065b-174">(C#) Async uygulamanızda hassas ayar yapma</span><span class="sxs-lookup"><span data-stu-id="5065b-174">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="5065b-175">Zaman uyumsuz örnek: İnce uygulamanızı ayarlama</span><span class="sxs-lookup"><span data-stu-id="5065b-175">Async Sample: Fine Tuning Your Application</span></span>](http://go.microsoft.com/fwlink/?LinkId=255046)
