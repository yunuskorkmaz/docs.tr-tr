---
title: "İzlenecek yol: Async ve Await Kullanarak Web'e Erişme"
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: 41ededd4d4335b78b8d7a33e8fe387c7d632cbee
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400751"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a><span data-ttu-id="10054-102">İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10054-102">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>

<span data-ttu-id="10054-103">Zaman uyumsuz programları, zaman uyumsuz/await özelliklerini kullanarak daha kolay ve daha canlı bir şekilde yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10054-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="10054-104">Zaman uyumlu kod gibi görünen zaman uyumsuz kod yazabilir ve derleyicinin zaman uyumsuz kodun genellikle sahip olduğu zor geri çağırma işlevlerini ve devamlılığını işlemesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10054-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>

<span data-ttu-id="10054-105">Async özelliği hakkında daha fazla bilgi için bkz. zaman uyumsuz [programlama, Async ve await (Visual Basic)](index.md).</span><span class="sxs-lookup"><span data-stu-id="10054-105">For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](index.md).</span></span>

<span data-ttu-id="10054-106">Bu izlenecek yol, bir Web sitesi listesindeki bayt sayısını toplayan bir zaman uyumlu Windows Presentation Foundation (WPF) uygulamasıyla başlar.</span><span class="sxs-lookup"><span data-stu-id="10054-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="10054-107">İzlenecek yol, yeni özellikleri kullanarak uygulamayı zaman uyumsuz bir çözüme dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="10054-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>

<span data-ttu-id="10054-108">Uygulamaları kendiniz derlemek istemiyorsanız, [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)"zaman uyumsuz örnek: Web izlenecek yol (C# ve Visual Basic)" erişimini indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10054-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

<span data-ttu-id="10054-109">Bu kılavuzda, aşağıdaki görevleri tamamlayadınız:</span><span class="sxs-lookup"><span data-stu-id="10054-109">In this walkthrough, you complete the following tasks:</span></span>

> [!div class="checklist"]
>
> - [<span data-ttu-id="10054-110">WPF uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="10054-110">Create a WPF application</span></span>](#create-a-wpf-application)
> - [<span data-ttu-id="10054-111">Basit bir WPF MainWindow tasarımı</span><span class="sxs-lookup"><span data-stu-id="10054-111">Design a simple WPF MainWindow</span></span>](#design-a-simple-wpf-mainwindow)
> - [<span data-ttu-id="10054-112">Başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="10054-112">Add a reference</span></span>](#add-a-reference)
> - [<span data-ttu-id="10054-113">Gerekli Imports deyimlerini Ekle</span><span class="sxs-lookup"><span data-stu-id="10054-113">Add necessary Imports statements</span></span>](#add-necessary-imports-statements)
> - [<span data-ttu-id="10054-114">Zaman uyumlu uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="10054-114">Create a synchronous application</span></span>](#create-a-synchronous-application)
> - [<span data-ttu-id="10054-115">Zaman uyumlu çözümü test etme</span><span class="sxs-lookup"><span data-stu-id="10054-115">Test the synchronous solution</span></span>](#test-the-synchronous-solution)
> - [<span data-ttu-id="10054-116">GetURLContents öğesini zaman uyumsuz bir metoda Dönüştür</span><span class="sxs-lookup"><span data-stu-id="10054-116">Convert GetURLContents to an asynchronous method</span></span>](#convert-geturlcontents-to-an-asynchronous-method)
> - [<span data-ttu-id="10054-117">Sumpageslikleri zaman uyumsuz bir metoda Dönüştür</span><span class="sxs-lookup"><span data-stu-id="10054-117">Convert SumPageSizes to an asynchronous method</span></span>](#convert-sumpagesizes-to-an-asynchronous-method)
> - [<span data-ttu-id="10054-118">StartButton_Click zaman uyumsuz bir metoda Dönüştür</span><span class="sxs-lookup"><span data-stu-id="10054-118">Convert startButton_Click to an asynchronous method</span></span>](#convert-startbutton_click-to-an-asynchronous-method)
> - [<span data-ttu-id="10054-119">Zaman uyumsuz çözümü test etme</span><span class="sxs-lookup"><span data-stu-id="10054-119">Test the asynchronous solution</span></span>](#test-the-asynchronous-solution)
> - [<span data-ttu-id="10054-120">GetURLContentsAsync yöntemini bir .NET Framework yöntemiyle değiştirin</span><span class="sxs-lookup"><span data-stu-id="10054-120">Replace the GetURLContentsAsync method with a .NET Framework method</span></span>](#replace-the-geturlcontentsasync-method-with-a-net-framework-method)

<span data-ttu-id="10054-121">Tüm zaman uyumsuz örnek için [örnek](#example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="10054-121">See the [Example](#example) section for the complete asynchronous example.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="10054-122">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="10054-122">Prerequisites</span></span>

<span data-ttu-id="10054-123">Bilgisayarınızda Visual Studio 2012 veya üzeri yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="10054-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="10054-124">Daha fazla bilgi için bkz. Visual Studio [İndirmeleri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) sayfası.</span><span class="sxs-lookup"><span data-stu-id="10054-124">For more information, see the Visual Studio [Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) page.</span></span>

## <a name="create-a-wpf-application"></a><span data-ttu-id="10054-125">WPF uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="10054-125">Create a WPF application</span></span>

1. <span data-ttu-id="10054-126">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="10054-126">Start Visual Studio.</span></span>

2. <span data-ttu-id="10054-127">Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="10054-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>

    <span data-ttu-id="10054-128">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="10054-128">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="10054-129">**Yüklü şablonlar** bölmesinde Visual Basic öğesini seçin ve ardından Proje türleri listesinden **WPF uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="10054-129">In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="10054-130">**Ad** metin kutusuna girin `AsyncExampleWPF` ve sonra **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="10054-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>

    <span data-ttu-id="10054-131">Yeni proje **Çözüm Gezgini**görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="10054-131">The new project appears in **Solution Explorer**.</span></span>

## <a name="design-a-simple-wpf-mainwindow"></a><span data-ttu-id="10054-132">Basit bir WPF MainWindow tasarımı</span><span class="sxs-lookup"><span data-stu-id="10054-132">Design a simple WPF MainWindow</span></span>

1. <span data-ttu-id="10054-133">Visual Studio Code düzenleyicisinde **MainWindow. xaml** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="10054-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

2. <span data-ttu-id="10054-134">**Araç kutusu** penceresi görünür değilse, **Görünüm** menüsünü açın ve ardından **araç kutusu**' nu seçin.</span><span class="sxs-lookup"><span data-stu-id="10054-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>

3. <span data-ttu-id="10054-135">**MainWindow** penceresine bir **Button** denetimi ve **TextBox** denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="10054-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>

4. <span data-ttu-id="10054-136">**TextBox** denetimini vurgulayın ve **Özellikler** penceresinde aşağıdaki değerleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="10054-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="10054-137">**Name** özelliğini olarak ayarlayın `resultsTextBox` .</span><span class="sxs-lookup"><span data-stu-id="10054-137">Set the **Name** property to `resultsTextBox`.</span></span>

    - <span data-ttu-id="10054-138">**Height** özelliğini 250 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="10054-138">Set the **Height** property to 250.</span></span>

    - <span data-ttu-id="10054-139">**Width** özelliğini 500 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="10054-139">Set the **Width** property to 500.</span></span>

    - <span data-ttu-id="10054-140">**Metin** sekmesinde, Lucida Console veya Global tek boşluk gibi tek boşluklu bir yazı tipi belirtin.</span><span class="sxs-lookup"><span data-stu-id="10054-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>

5. <span data-ttu-id="10054-141">**Düğme** denetimini vurgulayın ve **Özellikler** penceresinde aşağıdaki değerleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="10054-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="10054-142">**Name** özelliğini olarak ayarlayın `startButton` .</span><span class="sxs-lookup"><span data-stu-id="10054-142">Set the **Name** property to `startButton`.</span></span>

    - <span data-ttu-id="10054-143">**İçerik** özelliğinin değerini **düğmeden** **başla**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="10054-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>

6. <span data-ttu-id="10054-144">Metin kutusunu ve düğmeyi her ikisinin de **MainWindow** penceresinde görünmesi için konumlandırın.</span><span class="sxs-lookup"><span data-stu-id="10054-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>

    <span data-ttu-id="10054-145">WPF XAML Tasarımcısı hakkında daha fazla bilgi için, bkz. [XAML Tasarımcısı kullanarak Kullanıcı arabirimi oluşturma](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="10054-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>

## <a name="add-a-reference"></a><span data-ttu-id="10054-146">Başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="10054-146">Add a reference</span></span>

1. <span data-ttu-id="10054-147">**Çözüm Gezgini**, projenizin adını vurgulayın.</span><span class="sxs-lookup"><span data-stu-id="10054-147">In **Solution Explorer**, highlight your project's name.</span></span>

2. <span data-ttu-id="10054-148">Menü çubuğunda **Proje**, **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="10054-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>

    <span data-ttu-id="10054-149">**Başvuru Yöneticisi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="10054-149">The **Reference Manager** dialog box appears.</span></span>

3. <span data-ttu-id="10054-150">İletişim kutusunun üst kısmında, projenizin .NET Framework 4,5 veya üstünü hedeflediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="10054-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>

4. <span data-ttu-id="10054-151">**Derlemeler** alanında, zaten seçili değilse **Framework** ' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="10054-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>

5. <span data-ttu-id="10054-152">Ad listesinde, **System .net. http** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="10054-152">In the list of names, select the **System.Net.Http** check box.</span></span>

6. <span data-ttu-id="10054-153">İletişim kutusunu kapatmak için **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="10054-153">Choose the **OK** button to close the dialog box.</span></span>

## <a name="add-necessary-imports-statements"></a><span data-ttu-id="10054-154">Gerekli Imports deyimlerini Ekle</span><span class="sxs-lookup"><span data-stu-id="10054-154">Add necessary Imports statements</span></span>

1. <span data-ttu-id="10054-155">**Çözüm Gezgini**, MainWindow. xaml. vb için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="10054-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

2. <span data-ttu-id="10054-156">`Imports`Zaten mevcut değilse, kod dosyasının en üstüne aşağıdaki deyimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="10054-156">Add the following `Imports` statements at the top of the code file if they’re not already present.</span></span>

    ```vb
    Imports System.Net.Http
    Imports System.Net
    Imports System.IO
    ```

## <a name="create-a-synchronous-application"></a><span data-ttu-id="10054-157">Zaman uyumlu uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="10054-157">Create a synchronous application</span></span>

1. <span data-ttu-id="10054-158">MainWindow. xaml tasarım penceresinde, **Start** `startButton_Click` MainWindow. xaml. vb ' de olay Işleyicisini oluşturmak için Başlat düğmesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="10054-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

2. <span data-ttu-id="10054-159">MainWindow. xaml. vb dosyasında aşağıdaki kodu ' ın gövdesine kopyalayın `startButton_Click` :</span><span class="sxs-lookup"><span data-stu-id="10054-159">In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:</span></span>

    ```vb
    resultsTextBox.Clear()
    SumPageSizes()
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."
    ```

    <span data-ttu-id="10054-160">Kod, uygulamayı yönlendiren yöntemini çağırır `SumPageSizes` ve denetim ' e döndüğünde bir ileti görüntüler `startButton_Click` .</span><span class="sxs-lookup"><span data-stu-id="10054-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>

3. <span data-ttu-id="10054-161">Zaman uyumlu çözüm kodu aşağıdaki dört yöntemi içerir:</span><span class="sxs-lookup"><span data-stu-id="10054-161">The code for the synchronous solution contains the following four methods:</span></span>

    - <span data-ttu-id="10054-162">`SumPageSizes`, ' den Web sayfası URL 'Lerinin bir listesini alır ve `SetUpURLList` ardından `GetURLContents` `DisplayResults` her URL 'yi çağırır ve işler.</span><span class="sxs-lookup"><span data-stu-id="10054-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>

    - <span data-ttu-id="10054-163">`SetUpURLList`, bir Web adresleri listesi oluşturur ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="10054-163">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>

    - <span data-ttu-id="10054-164">`GetURLContents`, her bir Web sitesinin içeriğini indirir ve bir bayt dizisi olarak içeriğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="10054-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>

    - <span data-ttu-id="10054-165">`DisplayResults`, her bir URL için bayt dizisindeki bayt sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="10054-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>

    <span data-ttu-id="10054-166">Aşağıdaki dört yöntemi kopyalayın ve ardından bunları `startButton_Click` MainWindow. xaml. vb içindeki olay işleyicisinin altına yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="10054-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:</span></span>

    ```vb
    Private Sub SumPageSizes()

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetURLContents returns the contents of url as a byte array.
            Dim urlContents As Byte() = GetURLContents(url)

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "Total bytes returned:  {0}" & vbCrLf, total)
    End Sub

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Function GetURLContents(url As String) As Byte()

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        ' Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.
        Using response As WebResponse = webReq.GetResponse()
            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                responseStream.CopyTo(content)
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
    ```

## <a name="test-the-synchronous-solution"></a><span data-ttu-id="10054-167">Zaman uyumlu çözümü test etme</span><span class="sxs-lookup"><span data-stu-id="10054-167">Test the synchronous solution</span></span>

1. <span data-ttu-id="10054-168">Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="10054-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="10054-169">Aşağıdaki listeye benzer bir çıktı görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="10054-169">Output that resembles the following list should appear:</span></span>

    ```console
    msdn.microsoft.com/library/windows/apps/br211380.aspx        383832
    msdn.microsoft.com                                            33964
    msdn.microsoft.com/library/hh290136.aspx               225793
    msdn.microsoft.com/library/ee256749.aspx               143577
    msdn.microsoft.com/library/hh290138.aspx               237372
    msdn.microsoft.com/library/hh290140.aspx               128279
    msdn.microsoft.com/library/dd470362.aspx               157649
    msdn.microsoft.com/library/aa578028.aspx               204457
    msdn.microsoft.com/library/ms404677.aspx               176405
    msdn.microsoft.com/library/ff730837.aspx               143474

    Total bytes returned:  1834802

    Control returned to startButton_Click.
    ```

    <span data-ttu-id="10054-170">Sayıları görüntülemenin birkaç saniye sürdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="10054-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="10054-171">Bu süre boyunca, Kullanıcı arabirimi iş parçacığı istenen kaynakların indirilmesini beklerken engellenir.</span><span class="sxs-lookup"><span data-stu-id="10054-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="10054-172">Sonuç olarak, **Başlat** düğmesini seçtikten sonra görüntü penceresini taşıyamaz, ekranı kaplamaz, simge durumuna küçültebilir ya da kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10054-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="10054-173">Bu çalışmalar, bayt sayıları görünene kadar başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="10054-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="10054-174">Bir Web sitesi yanıt vermiyorsa, hangi sitenin başarısız olduğunun belirtii olmaz.</span><span class="sxs-lookup"><span data-stu-id="10054-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="10054-175">Beklemeyi durdurup programı kapatmanız zordur.</span><span class="sxs-lookup"><span data-stu-id="10054-175">It is difficult even to stop waiting and close the program.</span></span>

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a><span data-ttu-id="10054-176">GetURLContents öğesini zaman uyumsuz bir metoda Dönüştür</span><span class="sxs-lookup"><span data-stu-id="10054-176">Convert GetURLContents to an asynchronous method</span></span>

1. <span data-ttu-id="10054-177">Zaman uyumlu çözümü zaman uyumsuz bir çözüme dönüştürmek için, `GetURLContents` <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> yönteme ve yöntemine yapılan çağrılar <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> uygulamanın Web 'e eriştiği yerdir.</span><span class="sxs-lookup"><span data-stu-id="10054-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> method and to the <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> method are where the application accesses the web.</span></span> <span data-ttu-id="10054-178">.NET Framework, her iki yöntemin de zaman uyumsuz sürümlerini sağlayarak dönüştürmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="10054-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>

    <span data-ttu-id="10054-179">İçinde kullanılan yöntemler hakkında daha fazla bilgi için `GetURLContents` bkz <xref:System.Net.WebRequest> ..</span><span class="sxs-lookup"><span data-stu-id="10054-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="10054-180">Bu izlenecek yolda bulunan adımları izleyerek bazı derleyici hataları görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="10054-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="10054-181">Bunları yoksayabilir ve İzlenecek yol ile devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10054-181">You can ignore them and continue with the walkthrough.</span></span>

    <span data-ttu-id="10054-182">' In üçüncü satırında çağrılan yöntemi, `GetURLContents` `GetResponse` zaman uyumsuz, görev tabanlı <xref:System.Net.WebRequest.GetResponseAsync%2A> metoda değiştirin.</span><span class="sxs-lookup"><span data-stu-id="10054-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>

    ```vb
    Using response As WebResponse = webReq.GetResponseAsync()
    ```

2. <span data-ttu-id="10054-183">`GetResponseAsync`döndürür <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="10054-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="10054-184">Bu durumda, *görev dönüş değişkeni*, `TResult` türündedir <xref:System.Net.WebResponse> .</span><span class="sxs-lookup"><span data-stu-id="10054-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="10054-185">Görev, `WebResponse` istenen veriler indirildikten ve görevin tamamlanmasını çalıştırdıktan sonra gerçek bir nesne oluşturmak için bir taahhüddir.</span><span class="sxs-lookup"><span data-stu-id="10054-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>

    <span data-ttu-id="10054-186">`WebResponse`Görevden değeri almak için, aşağıdaki kodda gösterildiği gibi çağrısına bir [await](../../../language-reference/operators/await-operator.md) işleci uygulayın `GetResponseAsync` .</span><span class="sxs-lookup"><span data-stu-id="10054-186">To retrieve the `WebResponse` value from the task, apply an [Await](../../../language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>

    ```vb
    Using response As WebResponse = Await webReq.GetResponseAsync()
    ```

    <span data-ttu-id="10054-187">`Await`İşleç, beklenen görev tamamlanana kadar geçerli yöntemin yürütülmesini askıya alır `GetURLContents` .</span><span class="sxs-lookup"><span data-stu-id="10054-187">The `Await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="10054-188">Bu arada, Denetim geçerli yöntemi çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="10054-188">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="10054-189">Bu örnekte, geçerli yöntem `GetURLContents` ve arayan ' dır `SumPageSizes` .</span><span class="sxs-lookup"><span data-stu-id="10054-189">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="10054-190">Görev tamamlandığında, taahhüt edilen `WebResponse` nesne, beklenen görevin değeri olarak üretilir ve değişkenine atanır `response` .</span><span class="sxs-lookup"><span data-stu-id="10054-190">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>

    <span data-ttu-id="10054-191">Önceki deyim, ne olacağını açıklamak için aşağıdaki iki ifadeye ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="10054-191">The previous statement can be separated into the following two statements to clarify what happens.</span></span>

    ```vb
    Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
    Using response As WebResponse = Await responseTask
    ```

    <span data-ttu-id="10054-192">Çağrısı `webReq.GetResponseAsync` bir `Task(Of WebResponse)` veya döndürür `Task<WebResponse>` .</span><span class="sxs-lookup"><span data-stu-id="10054-192">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="10054-193">Sonra `Await` değeri almak için göreve bir işleç uygulanır `WebResponse` .</span><span class="sxs-lookup"><span data-stu-id="10054-193">Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.</span></span>

    <span data-ttu-id="10054-194">Zaman uyumsuz yönteminizin, görevin tamamlanmasına bağlı olmaması durumunda, zaman uyumsuz metoda yapılan çağrıdan sonra ve Await işleci uygulanmadan önce bu iki deyim arasında bu işe devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="10054-194">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied.</span></span> <span data-ttu-id="10054-195">Örnekler için bkz. [nasıl yapılır: Async ve await kullanarak birden çok Web Isteğini paralel hale getirme (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) ve [nasıl yapılır: Task. whenall (Visual Basic) kullanarak zaman uyumsuz izlenecek yolu genişletme](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="10054-195">For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

3. <span data-ttu-id="10054-196">`Await`Önceki adımda işleci eklediğiniz için bir derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="10054-196">Because you added the `Await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="10054-197">İşleci yalnızca [zaman uyumsuz](../../../language-reference/modifiers/async.md) değiştiriciyle işaretlenen yöntemlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="10054-197">The operator can be used only in methods that are marked with the [Async](../../../language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="10054-198">Çağrısını ' a ' çağrısı ile değiştirmek için dönüştürme adımlarını tekrarlarken hatayı yoksayın `CopyTo` `CopyToAsync` .</span><span class="sxs-lookup"><span data-stu-id="10054-198">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>

    - <span data-ttu-id="10054-199">Olarak çağrılan metodun adını değiştirin <xref:System.IO.Stream.CopyToAsync%2A> .</span><span class="sxs-lookup"><span data-stu-id="10054-199">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>

    - <span data-ttu-id="10054-200">`CopyTo`Ya da `CopyToAsync` yöntemi, bayt bağımsız değişkenine bayt kopyalar, `content` ve anlamlı bir değer döndürmez.</span><span class="sxs-lookup"><span data-stu-id="10054-200">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="10054-201">Zaman uyumlu sürümde, çağrısı `CopyTo` bir değer döndürmeyen basit bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="10054-201">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="10054-202">Zaman uyumsuz sürüm, `CopyToAsync` bir döndürür <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="10054-202">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="10054-203">Görev, "Task (void)" gibi çalışır ve yöntemin beklenmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="10054-203">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="10054-204">`Await` `await` `CopyToAsync` Aşağıdaki kodda gösterildiği gibi, çağrısına yönelik veya çağrısı yapın.</span><span class="sxs-lookup"><span data-stu-id="10054-204">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>

        ```vb
        Await responseStream.CopyToAsync(content)
        ```

         <span data-ttu-id="10054-205">Önceki ifade aşağıdaki iki kod satırını abbreviates.</span><span class="sxs-lookup"><span data-stu-id="10054-205">The previous statement abbreviates the following two lines of code.</span></span>

        ```vb
        ' CopyToAsync returns a Task, not a Task<T>.
        Dim copyTask As Task = responseStream.CopyToAsync(content)

        ' When copyTask is completed, content contains a copy of
        ' responseStream.
        Await copyTask
        ```

4. <span data-ttu-id="10054-206">Tüm bunlar ' de yapılacak şekilde, `GetURLContents` yöntem imzasını ayarlamasıdır.</span><span class="sxs-lookup"><span data-stu-id="10054-206">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="10054-207">`Await`İşlecini yalnızca [zaman uyumsuz](../../../language-reference/modifiers/async.md) değiştiriciyle işaretlenen yöntemlerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10054-207">You can use the `Await` operator only in methods that are marked with the [Async](../../../language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="10054-208">Aşağıdaki kodun gösterdiği gibi, yöntemi *zaman uyumsuz bir yöntem*olarak işaretlemek için değiştirici ekleyin.</span><span class="sxs-lookup"><span data-stu-id="10054-208">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>

    ```vb
    Private Async Function GetURLContents(url As String) As Byte()
    ```

5. <span data-ttu-id="10054-209">Zaman uyumsuz bir yöntemin dönüş türü yalnızca <xref:System.Threading.Tasks.Task> , olabilir <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="10054-209">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="10054-210">Visual Basic, yöntemi `Function` bir veya döndüren bir `Task` `Task(Of T)` , ya da yönteminin bir olması gerekir `Sub` .</span><span class="sxs-lookup"><span data-stu-id="10054-210">In Visual Basic, the method must be a `Function` that returns a `Task` or a `Task(Of T)`, or the method must be a `Sub`.</span></span> <span data-ttu-id="10054-211">Genellikle, bir `Sub` Yöntem yalnızca zaman uyumsuz olay işleyicide kullanılır, burada `Sub` gereklidir.</span><span class="sxs-lookup"><span data-stu-id="10054-211">Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required.</span></span> <span data-ttu-id="10054-212">Diğer durumlarda, `Task(T)` Tamamlanan yöntemin T türünde bir değer döndüren bir [Return](../../../language-reference/statements/return-statement.md) ifadesine sahip olması ve `Task` Tamamlanan yöntemin anlamlı bir değer döndürmemesi durumunda kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="10054-212">In other cases, you use `Task(T)` if the completed method has a [Return](../../../language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span>

    <span data-ttu-id="10054-213">Daha fazla bilgi için bkz. [Async Return Types (Visual Basic)](async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="10054-213">For more information, see [Async Return Types (Visual Basic)](async-return-types.md).</span></span>

    <span data-ttu-id="10054-214">Yöntem `GetURLContents` bir return ifadesine sahiptir ve ifade bir bayt dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="10054-214">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="10054-215">Bu nedenle, zaman uyumsuz sürümün dönüş türü görev (T), burada T bir bayt dizisidir.</span><span class="sxs-lookup"><span data-stu-id="10054-215">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="10054-216">Yöntem imzasında aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="10054-216">Make the following changes in the method signature:</span></span>

    - <span data-ttu-id="10054-217">Dönüş türünü olarak değiştirin `Task(Of Byte())` .</span><span class="sxs-lookup"><span data-stu-id="10054-217">Change the return type to `Task(Of Byte())`.</span></span>

    - <span data-ttu-id="10054-218">Kurala göre, zaman uyumsuz metotların "Async" ile biten adları vardır. bu nedenle, yöntemi yeniden adlandırın `GetURLContentsAsync` .</span><span class="sxs-lookup"><span data-stu-id="10054-218">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>

    <span data-ttu-id="10054-219">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="10054-219">The following code shows these changes.</span></span>

    ```vb
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())
    ```

    <span data-ttu-id="10054-220">Bu az değişiklikle, `GetURLContents` zaman uyumsuz bir metoda dönüştürme işlemi tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="10054-220">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a><span data-ttu-id="10054-221">Sumpageslikleri zaman uyumsuz bir metoda Dönüştür</span><span class="sxs-lookup"><span data-stu-id="10054-221">Convert SumPageSizes to an asynchronous method</span></span>

1. <span data-ttu-id="10054-222">İçin önceki yordamdaki adımları tekrarlayın `SumPageSizes` .</span><span class="sxs-lookup"><span data-stu-id="10054-222">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="10054-223">İlk olarak, çağrısını `GetURLContents` zaman uyumsuz bir çağrıya değiştirin.</span><span class="sxs-lookup"><span data-stu-id="10054-223">First, change the call to `GetURLContents` to an asynchronous call.</span></span>

    - <span data-ttu-id="10054-224">`GetURLContents` `GetURLContentsAsync` Daha önce yapmadıysanız, ' dan ' a çağrılan metodun adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="10054-224">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>

    - <span data-ttu-id="10054-225">`Await` `GetURLContentsAsync` Bayt dizi değerini almak için döndüren göreve uygulanır.</span><span class="sxs-lookup"><span data-stu-id="10054-225">Apply `Await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>

    <span data-ttu-id="10054-226">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="10054-226">The following code shows these changes.</span></span>

    ```vb
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)
    ```

    <span data-ttu-id="10054-227">Önceki atama, aşağıdaki iki kod satırını abbreviates.</span><span class="sxs-lookup"><span data-stu-id="10054-227">The previous assignment abbreviates the following two lines of code.</span></span>

    ```vb
    ' GetURLContentsAsync returns a task. At completion, the task
    ' produces a byte array.
    Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
    Dim urlContents As Byte() = Await getContentsTask
    ```

2. <span data-ttu-id="10054-228">Yöntemin imzasında aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="10054-228">Make the following changes in the method's signature:</span></span>

    - <span data-ttu-id="10054-229">Yöntemi `Async` değiştiriciyle işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="10054-229">Mark the method with the `Async` modifier.</span></span>

    - <span data-ttu-id="10054-230">Yöntem adına "Async" ekleyin.</span><span class="sxs-lookup"><span data-stu-id="10054-230">Add "Async" to the method name.</span></span>

    - <span data-ttu-id="10054-231">Bir görev dönüş değişkeni yok, T, bu kez `SumPageSizesAsync` t için bir değer döndürmüyor. (yöntemin hiçbir yöntemi yoktur `Return` .) Ancak, yöntemi bir `Task` olarak bir olarak döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="10054-231">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="10054-232">Bu nedenle, yöntem türünü olarak değiştirin `Sub` `Function` .</span><span class="sxs-lookup"><span data-stu-id="10054-232">Therefore, change the method type from `Sub` to `Function`.</span></span> <span data-ttu-id="10054-233">İşlevin dönüş türü `Task` .</span><span class="sxs-lookup"><span data-stu-id="10054-233">The return type of the function is `Task`.</span></span>

    <span data-ttu-id="10054-234">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="10054-234">The following code shows these changes.</span></span>

    ```vb
    Private Async Function SumPageSizesAsync() As Task
    ```

    <span data-ttu-id="10054-235">' A dönüştürme `SumPageSizes` `SumPageSizesAsync` işlemi tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="10054-235">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a><span data-ttu-id="10054-236">StartButton_Click zaman uyumsuz bir metoda Dönüştür</span><span class="sxs-lookup"><span data-stu-id="10054-236">Convert startButton_Click to an asynchronous method</span></span>

1. <span data-ttu-id="10054-237">Daha önce yapmadıysanız, olay işleyicisinde, çağrılan yöntemin adını `SumPageSizes` olarak olarak değiştirin `SumPageSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="10054-237">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>

2. <span data-ttu-id="10054-238">`SumPageSizesAsync`Zaman uyumsuz bir yöntem olduğundan, olay işleyicisindeki kodu, sonucu bekleme olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="10054-238">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>

    <span data-ttu-id="10054-239">`SumPageSizesAsync`İçindeki çağrısını yansıtan çağrı `CopyToAsync` `GetURLContentsAsync` .</span><span class="sxs-lookup"><span data-stu-id="10054-239">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="10054-240">Çağrı `Task` a değil, döndürür `Task(T)` .</span><span class="sxs-lookup"><span data-stu-id="10054-240">The call returns a `Task`, not a `Task(T)`.</span></span>

    <span data-ttu-id="10054-241">Önceki yordamlarda olduğu gibi, çağrıyı tek bir deyim veya iki deyim kullanarak dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10054-241">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="10054-242">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="10054-242">The following code shows these changes.</span></span>

    ```vb
    ' One-step async call.
    Await SumPageSizesAsync()

    ' Two-step async call.
    Dim sumTask As Task = SumPageSizesAsync()
    Await sumTask
    ```

3. <span data-ttu-id="10054-243">İşlemi yanlışlıkla yeniden girmeye engel olmak için, `startButton_Click` **Başlangıç** düğmesini devre dışı bırakmak için aşağıdaki ifadeyi ' ın üst kısmına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="10054-243">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>

    ```vb
    ' Disable the button until the operation is complete.
    startButton.IsEnabled = False
    ```

    <span data-ttu-id="10054-244">Olay işleyicisinin sonundaki düğmeyi yeniden etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10054-244">You can reenable the button at the end of the event handler.</span></span>

    ```vb
    ' Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = True
    ```

    <span data-ttu-id="10054-245">Yeniden giriş hakkında daha fazla bilgi için bkz. [zaman uyumsuz uygulamalarda yeniden girişi işleme (Visual Basic)](handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="10054-245">For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](handling-reentrancy-in-async-apps.md).</span></span>

4. <span data-ttu-id="10054-246">Son olarak, `Async` olay işleyicisinin beklebilmesi için değiştiricisini bildirime ekleyin `SumPagSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="10054-246">Finally, add the `Async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>

    ```vb
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
    ```

    <span data-ttu-id="10054-247">Genellikle, olay işleyicilerinin adları değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="10054-247">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="10054-248">`Task`Olay işleyicilerinin Visual Basic yordamlar olması gerektiğinden, dönüş türü olarak değiştirilmez `Sub` .</span><span class="sxs-lookup"><span data-stu-id="10054-248">The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.</span></span>

    <span data-ttu-id="10054-249">Projenin zaman uyumlu olarak zaman uyumsuz işlemeye dönüştürülmesi işlemi tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="10054-249">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>

## <a name="test-the-asynchronous-solution"></a><span data-ttu-id="10054-250">Zaman uyumsuz çözümü test etme</span><span class="sxs-lookup"><span data-stu-id="10054-250">Test the asynchronous solution</span></span>

1. <span data-ttu-id="10054-251">Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="10054-251">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

2. <span data-ttu-id="10054-252">Zaman uyumlu çözümün çıktısına benzeyen çıkış görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="10054-252">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="10054-253">Ancak, aşağıdaki farklılıklara dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="10054-253">However, notice the following differences.</span></span>

    - <span data-ttu-id="10054-254">İşlem tamamlandıktan sonra sonuçların hepsi aynı anda gerçekleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="10054-254">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="10054-255">Örneğin, her iki program içinde `startButton_Click` metin kutusunu temizleyen bir satır içerir.</span><span class="sxs-lookup"><span data-stu-id="10054-255">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="10054-256">Tek bir sonuç kümesi görüntülendikten sonra **Başlat** düğmesini ikinci bir kez seçerseniz, çalıştırmalar arasındaki metin kutusunu temizlemek amaç.</span><span class="sxs-lookup"><span data-stu-id="10054-256">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="10054-257">Zaman uyumlu sürümde, metin kutusu yalnızca sayımlar ikinci kez görüntülenmeden önce temizlenir, İndirmeler tamamlandığında ve Kullanıcı arabirimi iş parçacığı başka iş yapmak için ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="10054-257">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="10054-258">Zaman uyumsuz sürümde, **Başlat** düğmesini seçtikten sonra metin kutusu hemen temizlenir.</span><span class="sxs-lookup"><span data-stu-id="10054-258">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>

    - <span data-ttu-id="10054-259">En önemlisi, indirme sırasında UI iş parçacığı engellenmiyor.</span><span class="sxs-lookup"><span data-stu-id="10054-259">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="10054-260">Web kaynakları indirilirken, sayıldıkça ve görüntülenirken pencereyi taşıyabilir veya yeniden boyutlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10054-260">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="10054-261">Web sitelerinden biri yavaşsa veya yanıt vermiyorsa, **Kapat** düğmesini (sağ üst köşedeki kırmızı alanda bulunan x) seçerek işlemi iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10054-261">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>

## <a name="replace-the-geturlcontentsasync-method-with-a-net-framework-method"></a><span data-ttu-id="10054-262">GetURLContentsAsync yöntemini bir .NET Framework yöntemiyle değiştirin</span><span class="sxs-lookup"><span data-stu-id="10054-262">Replace the GetURLContentsAsync method with a .NET Framework method</span></span>

1. <span data-ttu-id="10054-263">.NET Framework kullanabileceğiniz birçok zaman uyumsuz yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="10054-263">The .NET Framework provides many async methods that you can use.</span></span> <span data-ttu-id="10054-264">Bunlardan biri, <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> yöntemi Bu izlenecek yol için yalnızca ihtiyacınız olanları yapar.</span><span class="sxs-lookup"><span data-stu-id="10054-264">One of them, the <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> method, does just what you need for this walkthrough.</span></span> <span data-ttu-id="10054-265">`GetURLContentsAsync`Daha önceki bir yordamda oluşturduğunuz yöntemi yerine kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10054-265">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>

    <span data-ttu-id="10054-266">İlk adım <xref:System.Net.Http.HttpClient> yönteminde bir nesne oluşturmaktır `SumPageSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="10054-266">The first step is to create an <xref:System.Net.Http.HttpClient> object in the `SumPageSizesAsync` method.</span></span> <span data-ttu-id="10054-267">Yönteminin başlangıcında aşağıdaki bildirimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="10054-267">Add the following declaration at the start of the method.</span></span>

    ```vb
    ' Declare an HttpClient object and increase the buffer size. The
    ' default buffer size is 65,536.
    Dim client As HttpClient =
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}
    ```

2. <span data-ttu-id="10054-268">İçinde, yöntemine yapılan çağrıyı yöntemine `SumPageSizesAsync,` `GetURLContentsAsync` bir çağrı ile değiştirin `HttpClient` .</span><span class="sxs-lookup"><span data-stu-id="10054-268">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>

    ```vb
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ```

3. <span data-ttu-id="10054-269">Yazdığınız yöntemi kaldırın veya not edin `GetURLContentsAsync` .</span><span class="sxs-lookup"><span data-stu-id="10054-269">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>

4. <span data-ttu-id="10054-270">Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="10054-270">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="10054-271">Projenin bu sürümünün davranışı, "zaman uyumsuz çözümü test etmek Için" yordamının açıklandığı, ancak sizin de daha az çaba gösteren davranışla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="10054-271">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>

## <a name="example"></a><span data-ttu-id="10054-272">Örnek</span><span class="sxs-lookup"><span data-stu-id="10054-272">Example</span></span>

<span data-ttu-id="10054-273">Aşağıda, zaman uyumsuz yöntemi kullanan dönüştürülmüş zaman uyumsuz çözümün tam örneği verilmiştir `GetURLContentsAsync` .</span><span class="sxs-lookup"><span data-stu-id="10054-273">The following is the full example of the converted asynchronous solution that uses the asynchronous `GetURLContentsAsync` method.</span></span> <span data-ttu-id="10054-274">Özgün, zaman uyumlu çözüme kesinlikle benzediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="10054-274">Notice that it strongly resembles the original, synchronous solution.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        resultsTextBox.Clear()

        '' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            Dim urlContents As Byte() = Await GetURLContentsAsync(url)

            ' The previous line abbreviates the following two assignment statements.

            '//<snippet21>
            ' GetURLContentsAsync returns a task. At completion, the task
            ' produces a byte array.
            'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        Using response As WebResponse = Await webReq.GetResponseAsync()

            ' The previous statement abbreviates the following two statements.

            'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
            'Using response As WebResponse = Await responseTask

            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                Await responseStream.CopyToAsync(content)

                ' The previous statement abbreviates the following two statements.

                ' CopyToAsync returns a Task, not a Task<T>.
                'Dim copyTask As Task = responseStream.CopyToAsync(content)

                ' When copyTask is completed, content contains a copy of
                ' responseStream.
                'Await copyTask
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

<span data-ttu-id="10054-275">Aşağıdaki kod, yöntemini kullanan çözümün tam örneğini içerir `HttpClient` `GetByteArrayAsync` .</span><span class="sxs-lookup"><span data-stu-id="10054-275">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        ' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Declare an HttpClient object and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetByteArrayAsync returns a task. At completion, the task
            ' produces a byte array.
            Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

            ' The following two lines can replace the previous assignment statement.
            'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

## <a name="see-also"></a><span data-ttu-id="10054-276">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10054-276">See also</span></span>

- [<span data-ttu-id="10054-277">Zaman uyumsuz örnek: Web 'e yönelik Izlenecek yol (C# ve Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10054-277">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [<span data-ttu-id="10054-278">Await Işleci</span><span class="sxs-lookup"><span data-stu-id="10054-278">Await Operator</span></span>](../../../language-reference/operators/await-operator.md)
- [<span data-ttu-id="10054-279">Eş</span><span class="sxs-lookup"><span data-stu-id="10054-279">Async</span></span>](../../../language-reference/modifiers/async.md)
- [<span data-ttu-id="10054-280">Async ve await ile zaman uyumsuz programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10054-280">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="10054-281">Zaman uyumsuz dönüş türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10054-281">Async Return Types (Visual Basic)</span></span>](async-return-types.md)
- [<span data-ttu-id="10054-282">Görev tabanlı zaman uyumsuz programlama (TAP)</span><span class="sxs-lookup"><span data-stu-id="10054-282">Task-based Asynchronous Programming (TAP)</span></span>](https://www.microsoft.com/download/details.aspx?id=19957)
- [<span data-ttu-id="10054-283">Nasıl yapılır: Task. WhenAll kullanarak zaman uyumsuz Izlenecek yolu genişletme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10054-283">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [<span data-ttu-id="10054-284">Nasıl yapılır: Async ve await kullanarak birden çok Web Isteğini paralel hale getirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10054-284">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
