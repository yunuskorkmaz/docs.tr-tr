---
title: Zaman uyumsuz bir görevi veya görev listesini iptal etme (Visual Basic)
ms.date: 07/20/2015
ms.assetid: a9ee1b71-5bec-4736-a1e9-448042dd7215
ms.openlocfilehash: 2b2fa7447c046f70c840791e7fe9bd874ff3795f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630949"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-visual-basic"></a><span data-ttu-id="185aa-102">Zaman uyumsuz bir görevi veya görev listesini iptal etme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="185aa-102">Cancel an Async Task or a List of Tasks (Visual Basic)</span></span>

<span data-ttu-id="185aa-103">Bir zaman uyumsuz uygulamayı, bitmesini beklemek istemiyorsanız iptal etmek için kullanabileceğiniz bir düğme ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="185aa-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="185aa-104">Bu konudaki örnekleri izleyerek, bir Web sitesinin veya Web sitesi listesinin içeriğini yükleyen bir uygulamaya iptal düğmesi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="185aa-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>

<span data-ttu-id="185aa-105">Örnekler, [zaman uyumsuz uygulamanızı (Visual Basic) ayrıntılı olarak ayarlamaya](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) yönelik kullanıcı arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="185aa-105">The examples use the UI that [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) describes.</span></span>

> [!NOTE]
> <span data-ttu-id="185aa-106">Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="185aa-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="BKMK_CancelaTask"></a><span data-ttu-id="185aa-107">Bir görevi iptal etme</span><span class="sxs-lookup"><span data-stu-id="185aa-107">Cancel a Task</span></span>

<span data-ttu-id="185aa-108">İlk örnek, **iptal** düğmesini tek bir indirme göreviyle ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="185aa-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="185aa-109">Uygulama içerik indirirken düğmeyi seçerseniz, indirme iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="185aa-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>

### <a name="downloading-the-example"></a><span data-ttu-id="185aa-110">Örnek indiriliyor</span><span class="sxs-lookup"><span data-stu-id="185aa-110">Downloading the Example</span></span>

<span data-ttu-id="185aa-111">Tüm Windows Presentation Foundation (WPF) projesini [zaman uyumsuz örnekten indirebilirsiniz: Uygulamanızı](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) hassas ayarlamalar yapın ve ardından aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="185aa-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="185aa-112">İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="185aa-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="185aa-113">Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="185aa-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="185aa-114">**Proje Aç** iletişim kutusunda, açtığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningVB için çözüm (. sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="185aa-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>

4. <span data-ttu-id="185aa-115">**Çözüm Gezgini**' de,,,, Iptal eden **görev** projesi için kısayol menüsünü açın ve ardından **Başlangıç projesi olarak ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="185aa-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="185aa-116">Projeyi çalıştırmak için F5 tuşunu seçin.</span><span class="sxs-lookup"><span data-stu-id="185aa-116">Choose the F5 key to run the project.</span></span>

     <span data-ttu-id="185aa-117">Projeyi hata ayıklamadan çalıştırmak için CTRL + F5 tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="185aa-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>

 <span data-ttu-id="185aa-118">Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow. xaml. vb dosyalarını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="185aa-118">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>

### <a name="building-the-example"></a><span data-ttu-id="185aa-119">Örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="185aa-119">Building the Example</span></span>

<span data-ttu-id="185aa-120">Aşağıdaki değişiklikler bir Web sitesini indiren uygulamaya bir **iptal** düğmesi ekler.</span><span class="sxs-lookup"><span data-stu-id="185aa-120">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="185aa-121">Örneği indirmek veya derlemek istemiyorsanız, bu konunun sonundaki "tüm örnekler" bölümünde son ürünü gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="185aa-121">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="185aa-122">Yıldız işaretleri koddaki değişiklikleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="185aa-122">Asterisks mark the changes in the code.</span></span>

<span data-ttu-id="185aa-123">Örneği kendiniz oluşturmak için, "örneği Indirme" bölümündeki yönergeleri izleyin, ancak **Başlangıç projesi** olarak, **1. aşama**yerine **startercode** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="185aa-123">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>

<span data-ttu-id="185aa-124">Ardından, bu projenin MainWindow. xaml. vb dosyasına aşağıdaki değişiklikleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="185aa-124">Then add the following changes to the MainWindow.xaml.vb file of that project.</span></span>

1. <span data-ttu-id="185aa-125">Kendisine erişen `CancellationTokenSource` tüm yöntemler `cts`için kapsam içinde olan bir değişken bildirin.</span><span class="sxs-lookup"><span data-stu-id="185aa-125">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>

    ```vb
    Class MainWindow

        ' ***Declare a System.Threading.CancellationTokenSource.
        Dim cts As CancellationTokenSource
    ```

2. <span data-ttu-id="185aa-126">**İptal** düğmesi için aşağıdaki olay işleyicisini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="185aa-126">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="185aa-127">Olay işleyicisi, Kullanıcı iptali <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> istediğinde bildirimde `cts` bulunan yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="185aa-127">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>

    ```vb
    ' ***Add an event handler for the Cancel button.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub
    ```

3. <span data-ttu-id="185aa-128">**Başlat** düğmesi `startButton_Click`için olay işleyicisinde aşağıdaki değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="185aa-128">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>

    - <span data-ttu-id="185aa-129">`CancellationTokenSource` ,`cts`İçin örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="185aa-129">Instantiate the `CancellationTokenSource`, `cts`.</span></span>

      ```vb
      ' ***Instantiate the CancellationTokenSource.
      cts = New CancellationTokenSource()
      ```

    - <span data-ttu-id="185aa-130">Belirtilen bir Web sitesinin `AccessTheWebAsync`içeriğini yükleyen çağrısında, <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> özelliğini `cts` bağımsız değişken olarak gönderin.</span><span class="sxs-lookup"><span data-stu-id="185aa-130">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="185aa-131">Özelliği `Token` , iptal isteniyorsa iletiyi yayar.</span><span class="sxs-lookup"><span data-stu-id="185aa-131">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="185aa-132">Kullanıcı indirme işlemini iptal etmeyi seçerse bir ileti görüntüleyen bir catch bloğu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="185aa-132">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="185aa-133">Aşağıdaki kod değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="185aa-133">The following code shows the changes.</span></span>

      ```vb
      Try
          ' ***Send a token to carry the message if cancellation is requested.
          Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)

          resultsTextBox.Text &=
              String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)

          ' *** If cancellation is requested, an OperationCanceledException results.
      Catch ex As OperationCanceledException
          resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

      Catch ex As Exception
          resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf
      End Try
      ```

4. <span data-ttu-id="185aa-134">İçinde `AccessTheWebAsync`, bir Web <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> sitesinin içeriğini indirmek `GetAsync` için <xref:System.Net.Http.HttpClient> türünde yönteminin aşırı yüklemesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="185aa-134">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="185aa-135">İkinci bağımsız değişken olarak `ct`, `AccessTheWebAsync`parametresini geçirin. <xref:System.Threading.CancellationToken></span><span class="sxs-lookup"><span data-stu-id="185aa-135">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="185aa-136">Kullanıcı **iptal** düğmesini seçerse, belirteç iletiyi taşır.</span><span class="sxs-lookup"><span data-stu-id="185aa-136">The token carries the message if the user chooses the **Cancel** button.</span></span>

    <span data-ttu-id="185aa-137">Aşağıdaki kod, içindeki `AccessTheWebAsync`değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="185aa-137">The following code shows the changes in `AccessTheWebAsync`.</span></span>

    ```vb
    ' ***Provide a parameter for the CancellationToken.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)

        Dim client As HttpClient = New HttpClient()

        resultsTextBox.Text &=
            String.Format(vbCrLf & "Ready to download." & vbCrLf)

        ' You might need to slow things down to have a chance to cancel.
        Await Task.Delay(250)

        ' GetAsync returns a Task(Of HttpResponseMessage).
        ' ***The ct argument carries the message if the Cancel button is chosen.
        Dim response As HttpResponseMessage = Await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ' The result of the method is the length of the downloaded website.
        Return urlContents.Length
    End Function
    ```

5. <span data-ttu-id="185aa-138">Programı iptal ederseniz, aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="185aa-138">If you don’t cancel the program, it produces the following output.</span></span>

    ```
    Ready to download.
    Length of the downloaded string: 158125.
    ```

    <span data-ttu-id="185aa-139">Program içeriği indirmeyi bitirmeden **iptal** düğmesini seçerseniz, program aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="185aa-139">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>

    ```
    Ready to download.
    Download canceled.
    ```

## <a name="BKMK_CancelaListofTasks"></a><span data-ttu-id="185aa-140">Görev listesini iptal etme</span><span class="sxs-lookup"><span data-stu-id="185aa-140">Cancel a List of Tasks</span></span>

<span data-ttu-id="185aa-141">Aynı `CancellationTokenSource` örneği her görevle ilişkilendirerek, daha fazla görevi iptal etmek için önceki örneği genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="185aa-141">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="185aa-142">**İptal** düğmesini seçerseniz, henüz tamamlanmamış tüm görevleri iptal edersiniz.</span><span class="sxs-lookup"><span data-stu-id="185aa-142">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>

### <a name="downloading-the-example"></a><span data-ttu-id="185aa-143">Örnek indiriliyor</span><span class="sxs-lookup"><span data-stu-id="185aa-143">Downloading the Example</span></span>

<span data-ttu-id="185aa-144">Tüm Windows Presentation Foundation (WPF) projesini [zaman uyumsuz örnekten indirebilirsiniz: Uygulamanızı](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) hassas ayarlamalar yapın ve ardından aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="185aa-144">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="185aa-145">İndirdiğiniz dosyayı sıkıştırmasını açın ve ardından Visual Studio 'Yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="185aa-145">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="185aa-146">Menü çubuğunda **Dosya**, **Aç**, **Proje/çözüm**' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="185aa-146">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="185aa-147">**Proje Aç** iletişim kutusunda, açtığınız örnek kodu tutan klasörü açın ve ardından AsyncFineTuningVB için çözüm (. sln) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="185aa-147">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>

4. <span data-ttu-id="185aa-148">**Çözüm Gezgini**' de,,,,,,,, iptal eden bir **Proje projesi için** kısayol menüsünü açın ve **Başlangıç projesi olarak ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="185aa-148">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="185aa-149">Projeyi çalıştırmak için F5 tuşunu seçin.</span><span class="sxs-lookup"><span data-stu-id="185aa-149">Choose the F5 key to run the project.</span></span>

     <span data-ttu-id="185aa-150">Projeyi hata ayıklamadan çalıştırmak için CTRL + F5 tuşlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="185aa-150">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>

 <span data-ttu-id="185aa-151">Projeyi indirmek istemiyorsanız, bu konunun sonundaki MainWindow. xaml. vb dosyalarını gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="185aa-151">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>

### <a name="building-the-example"></a><span data-ttu-id="185aa-152">Örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="185aa-152">Building the Example</span></span>

<span data-ttu-id="185aa-153">Örneği kendiniz genişletmek için, "örneği Indirme" bölümündeki yönergeleri izleyin, ancak **Başlangıç projesi** **olarak iptal** eden ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="185aa-153">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="185aa-154">Aşağıdaki değişiklikleri bu projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="185aa-154">Add the following changes to that project.</span></span> <span data-ttu-id="185aa-155">Yıldız işaretleri programdaki değişiklikleri işaretler.</span><span class="sxs-lookup"><span data-stu-id="185aa-155">Asterisks mark the changes in the program.</span></span>

1. <span data-ttu-id="185aa-156">Web adreslerinin bir listesini oluşturmak için bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="185aa-156">Add a method to create a list of web addresses.</span></span>

    ```vb
    ' ***Add a method that creates a list of web addresses.
    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function
    ```

2. <span data-ttu-id="185aa-157">İçindeki `AccessTheWebAsync`yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="185aa-157">Call the method in `AccessTheWebAsync`.</span></span>

    ```vb
    ' ***Call SetUpURLList to make a list of web addresses.
    Dim urlList As List(Of String) = SetUpURLList()
    ```

3. <span data-ttu-id="185aa-158">Listesindeki her bir Web adresini `AccessTheWebAsync` işlemek için aşağıdaki döngüsünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="185aa-158">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>

    ```vb
    ' ***Add a loop to process the list of web addresses.
    For Each url In urlList
        ' GetAsync returns a Task(Of HttpResponseMessage).
        ' Argument ct carries the message if the Cancel button is chosen.
        ' ***Note that the Cancel button can cancel all remaining downloads.
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        resultsTextBox.Text &=
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)
    Next
    ```

4. <span data-ttu-id="185aa-159">, `AccessTheWebAsync` Uzunlukları gösterdiği için yöntemin herhangi bir şey döndürmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="185aa-159">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="185aa-160">Return ifadesini kaldırın ve yöntemin dönüş türünü <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>yerine olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="185aa-160">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>

    ```vb
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task
    ```

    <span data-ttu-id="185aa-161">Bir ifadesi yerine deyimi `startButton_Click` kullanarak yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="185aa-161">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>

    ```vb
    Await AccessTheWebAsync(cts.Token)
    ```

5. <span data-ttu-id="185aa-162">Programı iptal ederseniz, aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="185aa-162">If you don’t cancel the program, it produces the following output.</span></span>

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

    <span data-ttu-id="185aa-163">İndirmeler tamamlanmadan önce **iptal** düğmesini seçerseniz, çıkış, iptalden önce tamamlanan indirmelerin uzunluklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="185aa-163">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>

    ```
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="BKMK_CompleteExamples"></a><span data-ttu-id="185aa-164">Tüm örnekler</span><span class="sxs-lookup"><span data-stu-id="185aa-164">Complete Examples</span></span>

<span data-ttu-id="185aa-165">Aşağıdaki bölümler, önceki örneklerin her birine ilişkin kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="185aa-165">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="185aa-166">İçin <xref:System.Net.Http>bir başvuru eklemeniz gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="185aa-166">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="185aa-167">Projeleri [zaman uyumsuz örnekten indirebilirsiniz: Uygulamanızı](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)hassas bir şekilde ayarlama.</span><span class="sxs-lookup"><span data-stu-id="185aa-167">You can download the projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

### <a name="cancel-a-task-example"></a><span data-ttu-id="185aa-168">Bir görev örneğini iptal etme</span><span class="sxs-lookup"><span data-stu-id="185aa-168">Cancel a Task Example</span></span>

<span data-ttu-id="185aa-169">Aşağıdaki kod, tek bir görevi iptal eden örnek için tüm MainWindow. xaml. vb dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="185aa-169">The following code is the complete MainWindow.xaml.vb file for the example that cancels a single task.</span></span>

```vb
' Add an Imports directive and a reference for System.Net.Http.
Imports System.Net.Http

' Add the following Imports directive for System.Threading.
Imports System.Threading

Class MainWindow

    ' ***Declare a System.Threading.CancellationTokenSource.
    Dim cts As CancellationTokenSource

    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)
        ' ***Instantiate the CancellationTokenSource.
        cts = New CancellationTokenSource()

        resultsTextBox.Clear()

        Try
            ' ***Send a token to carry the message if cancellation is requested.
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)

            resultsTextBox.Text &=
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)

            ' *** If cancellation is requested, an OperationCanceledException results.
        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf
        End Try

        ' ***Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' ***Add an event handler for the Cancel button.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' ***Provide a parameter for the CancellationToken.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)

        Dim client As HttpClient = New HttpClient()

        resultsTextBox.Text &=
            String.Format(vbCrLf & "Ready to download." & vbCrLf)

        ' You might need to slow things down to have a chance to cancel.
        Await Task.Delay(250)

        ' GetAsync returns a Task(Of HttpResponseMessage).
        ' ***The ct argument carries the message if the Cancel button is chosen.
        Dim response As HttpResponseMessage = Await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ' The result of the method is the length of the downloaded website.
        Return urlContents.Length
    End Function
End Class

' Output for a successful download:

' Ready to download.

' Length of the downloaded string: 158125.

' Or, if you cancel:

' Ready to download.

' Download canceled.
```

### <a name="cancel-a-list-of-tasks-example"></a><span data-ttu-id="185aa-170">Görev listesini iptal etme örneği</span><span class="sxs-lookup"><span data-stu-id="185aa-170">Cancel a List of Tasks Example</span></span>

<span data-ttu-id="185aa-171">Aşağıdaki kod, bir görev listesini iptal eden örnek için tüm MainWindow. xaml. vb dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="185aa-171">The following code is the complete MainWindow.xaml.vb file for the example that cancels a list of tasks.</span></span>

```vb
' Add an Imports directive and a reference for System.Net.Http.
Imports System.Net.Http

' Add the following Imports directive for System.Threading.
Imports System.Threading

Class MainWindow

    ' Declare a System.Threading.CancellationTokenSource.
    Dim cts As CancellationTokenSource

    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)

        ' Instantiate the CancellationTokenSource.
        cts = New CancellationTokenSource()

        resultsTextBox.Clear()

        Try
            ' ***AccessTheWebAsync returns a Task, not a Task(Of Integer).
            Await AccessTheWebAsync(cts.Token)
            '  ***Small change in the display lines.
            resultsTextBox.Text &= vbCrLf & "Downloads complete."

        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf
        End Try

        ' Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' Add an event handler for the Cancel button.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' Provide a parameter for the CancellationToken.
    ' ***Change the return type to Task because the method has no return statement.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task

        Dim client As HttpClient = New HttpClient()

        ' ***Call SetUpURLList to make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' ***Add a loop to process the list of web addresses.
        For Each url In urlList
            ' GetAsync returns a Task(Of HttpResponseMessage).
            ' Argument ct carries the message if the Cancel button is chosen.
            ' ***Note that the Cancel button can cancel all remaining downloads.
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

            ' Retrieve the website contents from the HttpResponseMessage.
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

            resultsTextBox.Text &=
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)
        Next
    End Function

    ' ***Add a method that creates a list of web addresses.
    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

End Class

' Output if you do not choose to cancel:

' Length of the downloaded string: 35939.

' Length of the downloaded string: 237682.

' Length of the downloaded string: 128607.

' Length of the downloaded string: 158124.

' Length of the downloaded string: 204890.

' Length of the downloaded string: 175488.

' Length of the downloaded string: 145790.

' Downloads complete.

'  Sample output if you choose to cancel:

' Length of the downloaded string: 35939.

' Length of the downloaded string: 237682.

' Length of the downloaded string: 128607.

' Downloads canceled.
```

## <a name="see-also"></a><span data-ttu-id="185aa-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="185aa-172">See also</span></span>

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [<span data-ttu-id="185aa-173">Async ve await ile zaman uyumsuz programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="185aa-173">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="185aa-174">Zaman uyumsuz uygulamanızda ince ayar yapma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="185aa-174">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [<span data-ttu-id="185aa-175">Zaman uyumsuz örnek: Uygulamanızda ince ayar yapma</span><span class="sxs-lookup"><span data-stu-id="185aa-175">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
