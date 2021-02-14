---
description: "Daha fazla bilgi edinin: Izlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)"
title: "İzlenecek yol: Async ve Await Kullanarak Web'e Erişme"
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: 08488d4909e4fbc40cc11213eb293c2693fdec71
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474167"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a><span data-ttu-id="6e6e2-103">İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e6e2-103">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>

<span data-ttu-id="6e6e2-104">Zaman uyumsuz programları, zaman uyumsuz/await özelliklerini kullanarak daha kolay ve daha canlı bir şekilde yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-104">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="6e6e2-105">Zaman uyumlu kod gibi görünen zaman uyumsuz kod yazabilir ve derleyicinin zaman uyumsuz kodun genellikle sahip olduğu zor geri çağırma işlevlerini ve devamlılığını işlemesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-105">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>

<span data-ttu-id="6e6e2-106">Async özelliği hakkında daha fazla bilgi için bkz. zaman uyumsuz [programlama, Async ve await (Visual Basic)](index.md).</span><span class="sxs-lookup"><span data-stu-id="6e6e2-106">For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](index.md).</span></span>

<span data-ttu-id="6e6e2-107">Bu izlenecek yol, bir Web sitesi listesindeki bayt sayısını toplayan bir zaman uyumlu Windows Presentation Foundation (WPF) uygulamasıyla başlar.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-107">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="6e6e2-108">İzlenecek yol, yeni özellikleri kullanarak uygulamayı zaman uyumsuz bir çözüme dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-108">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>

<span data-ttu-id="6e6e2-109">Uygulamaları kendiniz derlemek istemiyorsanız, [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)"zaman uyumsuz örnek: Web izlenecek yol (C# ve Visual Basic)" erişimini indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-109">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

<span data-ttu-id="6e6e2-110">Bu kılavuzda, aşağıdaki görevleri tamamlayadınız:</span><span class="sxs-lookup"><span data-stu-id="6e6e2-110">In this walkthrough, you complete the following tasks:</span></span>

> [!div class="checklist"]
>
> - [<span data-ttu-id="6e6e2-111">WPF uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="6e6e2-111">Create a WPF application</span></span>](#create-a-wpf-application)
> - [<span data-ttu-id="6e6e2-112">Basit bir WPF MainWindow tasarımı</span><span class="sxs-lookup"><span data-stu-id="6e6e2-112">Design a simple WPF MainWindow</span></span>](#design-a-simple-wpf-mainwindow)
> - [<span data-ttu-id="6e6e2-113">Başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="6e6e2-113">Add a reference</span></span>](#add-a-reference)
> - [<span data-ttu-id="6e6e2-114">Gerekli Imports deyimlerini Ekle</span><span class="sxs-lookup"><span data-stu-id="6e6e2-114">Add necessary Imports statements</span></span>](#add-necessary-imports-statements)
> - [<span data-ttu-id="6e6e2-115">Zaman uyumlu uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="6e6e2-115">Create a synchronous application</span></span>](#create-a-synchronous-application)
> - [<span data-ttu-id="6e6e2-116">Zaman uyumlu çözümü test etme</span><span class="sxs-lookup"><span data-stu-id="6e6e2-116">Test the synchronous solution</span></span>](#test-the-synchronous-solution)
> - [<span data-ttu-id="6e6e2-117">GetURLContents öğesini zaman uyumsuz bir metoda Dönüştür</span><span class="sxs-lookup"><span data-stu-id="6e6e2-117">Convert GetURLContents to an asynchronous method</span></span>](#convert-geturlcontents-to-an-asynchronous-method)
> - [<span data-ttu-id="6e6e2-118">Sumpageslikleri zaman uyumsuz bir metoda Dönüştür</span><span class="sxs-lookup"><span data-stu-id="6e6e2-118">Convert SumPageSizes to an asynchronous method</span></span>](#convert-sumpagesizes-to-an-asynchronous-method)
> - [<span data-ttu-id="6e6e2-119">StartButton_Click zaman uyumsuz bir metoda Dönüştür</span><span class="sxs-lookup"><span data-stu-id="6e6e2-119">Convert startButton_Click to an asynchronous method</span></span>](#convert-startbutton_click-to-an-asynchronous-method)
> - [<span data-ttu-id="6e6e2-120">Zaman uyumsuz çözümü test etme</span><span class="sxs-lookup"><span data-stu-id="6e6e2-120">Test the asynchronous solution</span></span>](#test-the-asynchronous-solution)
> - [<span data-ttu-id="6e6e2-121">GetURLContentsAsync yöntemini bir .NET Framework yöntemiyle değiştirin</span><span class="sxs-lookup"><span data-stu-id="6e6e2-121">Replace the GetURLContentsAsync method with a .NET Framework method</span></span>](#replace-the-geturlcontentsasync-method-with-a-net-framework-method)

<span data-ttu-id="6e6e2-122">Tüm zaman uyumsuz örnek için [örnek](#example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-122">See the [Example](#example) section for the complete asynchronous example.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6e6e2-123">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="6e6e2-123">Prerequisites</span></span>

<span data-ttu-id="6e6e2-124">Bilgisayarınızda Visual Studio 2012 veya üzeri yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-124">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="6e6e2-125">Daha fazla bilgi için bkz. Visual Studio [İndirmeleri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) sayfası.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-125">For more information, see the Visual Studio [Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) page.</span></span>

## <a name="create-a-wpf-application"></a><span data-ttu-id="6e6e2-126">WPF uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="6e6e2-126">Create a WPF application</span></span>

1. <span data-ttu-id="6e6e2-127">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-127">Start Visual Studio.</span></span>

2. <span data-ttu-id="6e6e2-128">Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-128">On the menu bar, choose **File**, **New**, **Project**.</span></span>

    <span data-ttu-id="6e6e2-129">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-129">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="6e6e2-130">**Yüklü şablonlar** bölmesinde Visual Basic öğesini seçin ve ardından Proje türleri listesinden **WPF uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-130">In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="6e6e2-131">**Ad** metin kutusuna girin `AsyncExampleWPF` ve sonra **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-131">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>

    <span data-ttu-id="6e6e2-132">Yeni proje **Çözüm Gezgini** görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-132">The new project appears in **Solution Explorer**.</span></span>

## <a name="design-a-simple-wpf-mainwindow"></a><span data-ttu-id="6e6e2-133">Basit bir WPF MainWindow tasarımı</span><span class="sxs-lookup"><span data-stu-id="6e6e2-133">Design a simple WPF MainWindow</span></span>

1. <span data-ttu-id="6e6e2-134">Visual Studio Code düzenleyicisinde **MainWindow. xaml** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-134">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

2. <span data-ttu-id="6e6e2-135">**Araç kutusu** penceresi görünür değilse, **Görünüm** menüsünü açın ve ardından **araç kutusu**' nu seçin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-135">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>

3. <span data-ttu-id="6e6e2-136">**MainWindow** penceresine bir **Button** denetimi ve **TextBox** denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-136">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>

4. <span data-ttu-id="6e6e2-137">**TextBox** denetimini vurgulayın ve **Özellikler** penceresinde aşağıdaki değerleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="6e6e2-137">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="6e6e2-138">**Name** özelliğini olarak ayarlayın `resultsTextBox` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-138">Set the **Name** property to `resultsTextBox`.</span></span>

    - <span data-ttu-id="6e6e2-139">**Height** özelliğini 250 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-139">Set the **Height** property to 250.</span></span>

    - <span data-ttu-id="6e6e2-140">**Width** özelliğini 500 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-140">Set the **Width** property to 500.</span></span>

    - <span data-ttu-id="6e6e2-141">**Metin** sekmesinde, Lucida Console veya Global tek boşluk gibi tek boşluklu bir yazı tipi belirtin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-141">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>

5. <span data-ttu-id="6e6e2-142">**Düğme** denetimini vurgulayın ve **Özellikler** penceresinde aşağıdaki değerleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="6e6e2-142">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="6e6e2-143">**Name** özelliğini olarak ayarlayın `startButton` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-143">Set the **Name** property to `startButton`.</span></span>

    - <span data-ttu-id="6e6e2-144">**İçerik** özelliğinin değerini **düğmeden** **başla** olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-144">Change the value of the **Content** property from **Button** to **Start**.</span></span>

6. <span data-ttu-id="6e6e2-145">Metin kutusunu ve düğmeyi her ikisinin de **MainWindow** penceresinde görünmesi için konumlandırın.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-145">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>

    <span data-ttu-id="6e6e2-146">WPF XAML Tasarımcısı hakkında daha fazla bilgi için, bkz. [XAML Tasarımcısı kullanarak Kullanıcı arabirimi oluşturma](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="6e6e2-146">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>

## <a name="add-a-reference"></a><span data-ttu-id="6e6e2-147">Başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="6e6e2-147">Add a reference</span></span>

1. <span data-ttu-id="6e6e2-148">**Çözüm Gezgini**, projenizin adını vurgulayın.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-148">In **Solution Explorer**, highlight your project's name.</span></span>

2. <span data-ttu-id="6e6e2-149">Menü çubuğunda **Proje**, **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-149">On the menu bar, choose **Project**, **Add Reference**.</span></span>

    <span data-ttu-id="6e6e2-150">**Başvuru Yöneticisi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-150">The **Reference Manager** dialog box appears.</span></span>

3. <span data-ttu-id="6e6e2-151">İletişim kutusunun üst kısmında, projenizin .NET Framework 4,5 veya üstünü hedeflediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-151">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>

4. <span data-ttu-id="6e6e2-152">**Derlemeler** alanında, zaten seçili değilse **Framework** ' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-152">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>

5. <span data-ttu-id="6e6e2-153">Ad listesinde, **System .net. http** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-153">In the list of names, select the **System.Net.Http** check box.</span></span>

6. <span data-ttu-id="6e6e2-154">İletişim kutusunu kapatmak için **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-154">Choose the **OK** button to close the dialog box.</span></span>

## <a name="add-necessary-imports-statements"></a><span data-ttu-id="6e6e2-155">Gerekli Imports deyimlerini Ekle</span><span class="sxs-lookup"><span data-stu-id="6e6e2-155">Add necessary Imports statements</span></span>

1. <span data-ttu-id="6e6e2-156">**Çözüm Gezgini**, MainWindow. xaml. vb için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-156">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

2. <span data-ttu-id="6e6e2-157">`Imports`Zaten mevcut değilse, kod dosyasının en üstüne aşağıdaki deyimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-157">Add the following `Imports` statements at the top of the code file if they’re not already present.</span></span>

    ```vb
    Imports System.Net.Http
    Imports System.Net
    Imports System.IO
    ```

## <a name="create-a-synchronous-application"></a><span data-ttu-id="6e6e2-158">Zaman uyumlu uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="6e6e2-158">Create a synchronous application</span></span>

1. <span data-ttu-id="6e6e2-159">MainWindow. xaml tasarım penceresinde,  `startButton_Click` MainWindow. xaml. vb ' de olay Işleyicisini oluşturmak için Başlat düğmesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-159">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

2. <span data-ttu-id="6e6e2-160">MainWindow. xaml. vb dosyasında aşağıdaki kodu ' ın gövdesine kopyalayın `startButton_Click` :</span><span class="sxs-lookup"><span data-stu-id="6e6e2-160">In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:</span></span>

    ```vb
    resultsTextBox.Clear()
    SumPageSizes()
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."
    ```

    <span data-ttu-id="6e6e2-161">Kod, uygulamayı yönlendiren yöntemini çağırır `SumPageSizes` ve denetim ' e döndüğünde bir ileti görüntüler `startButton_Click` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-161">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>

3. <span data-ttu-id="6e6e2-162">Zaman uyumlu çözüm kodu aşağıdaki dört yöntemi içerir:</span><span class="sxs-lookup"><span data-stu-id="6e6e2-162">The code for the synchronous solution contains the following four methods:</span></span>

    - <span data-ttu-id="6e6e2-163">`SumPageSizes`, ' den Web sayfası URL 'Lerinin bir listesini alır ve `SetUpURLList` ardından `GetURLContents` `DisplayResults` her URL 'yi çağırır ve işler.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-163">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>

    - <span data-ttu-id="6e6e2-164">`SetUpURLList`, bir Web adresleri listesi oluşturur ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-164">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>

    - <span data-ttu-id="6e6e2-165">`GetURLContents`, her bir Web sitesinin içeriğini indirir ve bir bayt dizisi olarak içeriğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-165">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>

    - <span data-ttu-id="6e6e2-166">`DisplayResults`, her bir URL için bayt dizisindeki bayt sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-166">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>

    <span data-ttu-id="6e6e2-167">Aşağıdaki dört yöntemi kopyalayın ve ardından bunları `startButton_Click` MainWindow. xaml. vb içindeki olay işleyicisinin altına yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="6e6e2-167">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:</span></span>

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

## <a name="test-the-synchronous-solution"></a><span data-ttu-id="6e6e2-168">Zaman uyumlu çözümü test etme</span><span class="sxs-lookup"><span data-stu-id="6e6e2-168">Test the synchronous solution</span></span>

1. <span data-ttu-id="6e6e2-169">Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-169">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="6e6e2-170">Aşağıdaki listeye benzer bir çıktı görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="6e6e2-170">Output that resembles the following list should appear:</span></span>

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

    <span data-ttu-id="6e6e2-171">Sayıları görüntülemenin birkaç saniye sürdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-171">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="6e6e2-172">Bu süre boyunca, Kullanıcı arabirimi iş parçacığı istenen kaynakların indirilmesini beklerken engellenir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-172">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="6e6e2-173">Sonuç olarak,  **Başlat** düğmesini seçtikten sonra görüntü penceresini taşıyamaz, ekranı kaplamaz, simge durumuna küçültebilir ya da kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-173">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="6e6e2-174">Bu çalışmalar, bayt sayıları görünene kadar başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-174">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="6e6e2-175">Bir Web sitesi yanıt vermiyorsa, hangi sitenin başarısız olduğunun belirtii olmaz.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-175">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="6e6e2-176">Beklemeyi durdurup programı kapatmanız zordur.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-176">It is difficult even to stop waiting and close the program.</span></span>

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a><span data-ttu-id="6e6e2-177">GetURLContents öğesini zaman uyumsuz bir metoda Dönüştür</span><span class="sxs-lookup"><span data-stu-id="6e6e2-177">Convert GetURLContents to an asynchronous method</span></span>

1. <span data-ttu-id="6e6e2-178">Zaman uyumlu çözümü zaman uyumsuz bir çözüme dönüştürmek için, `GetURLContents` <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> yönteme ve yöntemine yapılan çağrılar <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> uygulamanın Web 'e eriştiği yerdir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-178">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> method and to the <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> method are where the application accesses the web.</span></span> <span data-ttu-id="6e6e2-179">.NET Framework, her iki yöntemin de zaman uyumsuz sürümlerini sağlayarak dönüştürmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-179">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>

    <span data-ttu-id="6e6e2-180">İçinde kullanılan yöntemler hakkında daha fazla bilgi için `GetURLContents` bkz <xref:System.Net.WebRequest> ..</span><span class="sxs-lookup"><span data-stu-id="6e6e2-180">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6e6e2-181">Bu izlenecek yolda bulunan adımları izleyerek bazı derleyici hataları görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-181">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="6e6e2-182">Bunları yoksayabilir ve İzlenecek yol ile devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-182">You can ignore them and continue with the walkthrough.</span></span>

    <span data-ttu-id="6e6e2-183">' In üçüncü satırında çağrılan yöntemi, `GetURLContents` `GetResponse` zaman uyumsuz, görev tabanlı <xref:System.Net.WebRequest.GetResponseAsync%2A> metoda değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-183">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>

    ```vb
    Using response As WebResponse = webReq.GetResponseAsync()
    ```

2. <span data-ttu-id="6e6e2-184">`GetResponseAsync` döndürür <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-184">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="6e6e2-185">Bu durumda, *görev dönüş değişkeni*, `TResult` türündedir <xref:System.Net.WebResponse> .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-185">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="6e6e2-186">Görev, `WebResponse` istenen veriler indirildikten ve görevin tamamlanmasını çalıştırdıktan sonra gerçek bir nesne oluşturmak için bir taahhüddir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-186">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>

    <span data-ttu-id="6e6e2-187">`WebResponse`Görevden değeri almak için, aşağıdaki kodda gösterildiği gibi çağrısına bir [await](../../../language-reference/operators/await-operator.md) işleci uygulayın `GetResponseAsync` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-187">To retrieve the `WebResponse` value from the task, apply an [Await](../../../language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>

    ```vb
    Using response As WebResponse = Await webReq.GetResponseAsync()
    ```

    <span data-ttu-id="6e6e2-188">`Await`İşleç, beklenen görev tamamlanana kadar geçerli yöntemin yürütülmesini askıya alır `GetURLContents` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-188">The `Await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="6e6e2-189">Bu arada, Denetim geçerli yöntemi çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-189">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="6e6e2-190">Bu örnekte, geçerli yöntem `GetURLContents` ve arayan ' dır `SumPageSizes` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-190">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="6e6e2-191">Görev tamamlandığında, taahhüt edilen `WebResponse` nesne, beklenen görevin değeri olarak üretilir ve değişkenine atanır `response` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-191">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>

    <span data-ttu-id="6e6e2-192">Önceki deyim, ne olacağını açıklamak için aşağıdaki iki ifadeye ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-192">The previous statement can be separated into the following two statements to clarify what happens.</span></span>

    ```vb
    Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
    Using response As WebResponse = Await responseTask
    ```

    <span data-ttu-id="6e6e2-193">Çağrısı `webReq.GetResponseAsync` bir `Task(Of WebResponse)` veya döndürür `Task<WebResponse>` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-193">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="6e6e2-194">Sonra `Await` değeri almak için göreve bir işleç uygulanır `WebResponse` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-194">Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.</span></span>

    <span data-ttu-id="6e6e2-195">Zaman uyumsuz yönteminizin, görevin tamamlanmasına bağlı olmaması durumunda, zaman uyumsuz metoda yapılan çağrıdan sonra ve Await işleci uygulanmadan önce bu iki deyim arasında bu işe devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-195">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied.</span></span> <span data-ttu-id="6e6e2-196">Örnekler için bkz. [nasıl yapılır: Async ve await kullanarak birden çok Web Isteğini paralel hale getirme (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) ve [nasıl yapılır: Task. whenall (Visual Basic) kullanarak zaman uyumsuz izlenecek yolu genişletme](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="6e6e2-196">For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

3. <span data-ttu-id="6e6e2-197">`Await`Önceki adımda işleci eklediğiniz için bir derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-197">Because you added the `Await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="6e6e2-198">İşleci yalnızca [zaman uyumsuz](../../../language-reference/modifiers/async.md) değiştiriciyle işaretlenen yöntemlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-198">The operator can be used only in methods that are marked with the [Async](../../../language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="6e6e2-199">Çağrısını ' a ' çağrısı ile değiştirmek için dönüştürme adımlarını tekrarlarken hatayı yoksayın `CopyTo` `CopyToAsync` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-199">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>

    - <span data-ttu-id="6e6e2-200">Olarak çağrılan metodun adını değiştirin <xref:System.IO.Stream.CopyToAsync%2A> .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-200">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>

    - <span data-ttu-id="6e6e2-201">`CopyTo`Ya da `CopyToAsync` yöntemi, bayt bağımsız değişkenine bayt kopyalar, `content` ve anlamlı bir değer döndürmez.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-201">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="6e6e2-202">Zaman uyumlu sürümde, çağrısı `CopyTo` bir değer döndürmeyen basit bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-202">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="6e6e2-203">Zaman uyumsuz sürüm, `CopyToAsync` bir döndürür <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-203">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="6e6e2-204">Görev, "Task (void)" gibi çalışır ve yöntemin beklenmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-204">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="6e6e2-205">`Await` `await` `CopyToAsync` Aşağıdaki kodda gösterildiği gibi, çağrısına yönelik veya çağrısı yapın.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-205">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>

        ```vb
        Await responseStream.CopyToAsync(content)
        ```

         <span data-ttu-id="6e6e2-206">Önceki ifade aşağıdaki iki kod satırını abbreviates.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-206">The previous statement abbreviates the following two lines of code.</span></span>

        ```vb
        ' CopyToAsync returns a Task, not a Task<T>.
        Dim copyTask As Task = responseStream.CopyToAsync(content)

        ' When copyTask is completed, content contains a copy of
        ' responseStream.
        Await copyTask
        ```

4. <span data-ttu-id="6e6e2-207">Tüm bunlar ' de yapılacak şekilde, `GetURLContents` yöntem imzasını ayarlamasıdır.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-207">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="6e6e2-208">`Await`İşlecini yalnızca [zaman uyumsuz](../../../language-reference/modifiers/async.md) değiştiriciyle işaretlenen yöntemlerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-208">You can use the `Await` operator only in methods that are marked with the [Async](../../../language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="6e6e2-209">Aşağıdaki kodun gösterdiği gibi, yöntemi *zaman uyumsuz bir yöntem* olarak işaretlemek için değiştirici ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-209">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>

    ```vb
    Private Async Function GetURLContents(url As String) As Byte()
    ```

5. <span data-ttu-id="6e6e2-210">Zaman uyumsuz bir yöntemin dönüş türü yalnızca <xref:System.Threading.Tasks.Task> , olabilir <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-210">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="6e6e2-211">Visual Basic, yöntemi `Function` bir veya döndüren bir `Task` `Task(Of T)` , ya da yönteminin bir olması gerekir `Sub` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-211">In Visual Basic, the method must be a `Function` that returns a `Task` or a `Task(Of T)`, or the method must be a `Sub`.</span></span> <span data-ttu-id="6e6e2-212">Genellikle, bir `Sub` Yöntem yalnızca zaman uyumsuz olay işleyicide kullanılır, burada `Sub` gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-212">Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required.</span></span> <span data-ttu-id="6e6e2-213">Diğer durumlarda, `Task(T)` Tamamlanan yöntemin T türünde bir değer döndüren bir [Return](../../../language-reference/statements/return-statement.md) ifadesine sahip olması ve `Task` Tamamlanan yöntemin anlamlı bir değer döndürmemesi durumunda kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-213">In other cases, you use `Task(T)` if the completed method has a [Return](../../../language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span>

    <span data-ttu-id="6e6e2-214">Daha fazla bilgi için bkz. [Async Return Types (Visual Basic)](async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="6e6e2-214">For more information, see [Async Return Types (Visual Basic)](async-return-types.md).</span></span>

    <span data-ttu-id="6e6e2-215">Yöntem `GetURLContents` bir return ifadesine sahiptir ve ifade bir bayt dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-215">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="6e6e2-216">Bu nedenle, zaman uyumsuz sürümün dönüş türü görev (T), burada T bir bayt dizisidir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-216">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="6e6e2-217">Yöntem imzasında aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="6e6e2-217">Make the following changes in the method signature:</span></span>

    - <span data-ttu-id="6e6e2-218">Dönüş türünü olarak değiştirin `Task(Of Byte())` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-218">Change the return type to `Task(Of Byte())`.</span></span>

    - <span data-ttu-id="6e6e2-219">Kurala göre, zaman uyumsuz metotların "Async" ile biten adları vardır. bu nedenle, yöntemi yeniden adlandırın `GetURLContentsAsync` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-219">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>

    <span data-ttu-id="6e6e2-220">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-220">The following code shows these changes.</span></span>

    ```vb
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())
    ```

    <span data-ttu-id="6e6e2-221">Bu az değişiklikle, `GetURLContents` zaman uyumsuz bir metoda dönüştürme işlemi tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-221">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a><span data-ttu-id="6e6e2-222">Sumpageslikleri zaman uyumsuz bir metoda Dönüştür</span><span class="sxs-lookup"><span data-stu-id="6e6e2-222">Convert SumPageSizes to an asynchronous method</span></span>

1. <span data-ttu-id="6e6e2-223">İçin önceki yordamdaki adımları tekrarlayın `SumPageSizes` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-223">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="6e6e2-224">İlk olarak, çağrısını `GetURLContents` zaman uyumsuz bir çağrıya değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-224">First, change the call to `GetURLContents` to an asynchronous call.</span></span>

    - <span data-ttu-id="6e6e2-225">`GetURLContents` `GetURLContentsAsync` Daha önce yapmadıysanız, ' dan ' a çağrılan metodun adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-225">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>

    - <span data-ttu-id="6e6e2-226">`Await` `GetURLContentsAsync` Bayt dizi değerini almak için döndüren göreve uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-226">Apply `Await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>

    <span data-ttu-id="6e6e2-227">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-227">The following code shows these changes.</span></span>

    ```vb
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)
    ```

    <span data-ttu-id="6e6e2-228">Önceki atama, aşağıdaki iki kod satırını abbreviates.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-228">The previous assignment abbreviates the following two lines of code.</span></span>

    ```vb
    ' GetURLContentsAsync returns a task. At completion, the task
    ' produces a byte array.
    Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
    Dim urlContents As Byte() = Await getContentsTask
    ```

2. <span data-ttu-id="6e6e2-229">Yöntemin imzasında aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="6e6e2-229">Make the following changes in the method's signature:</span></span>

    - <span data-ttu-id="6e6e2-230">Yöntemi `Async` değiştiriciyle işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-230">Mark the method with the `Async` modifier.</span></span>

    - <span data-ttu-id="6e6e2-231">Yöntem adına "Async" ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-231">Add "Async" to the method name.</span></span>

    - <span data-ttu-id="6e6e2-232">Bir görev dönüş değişkeni yok, T, bu kez `SumPageSizesAsync` t için bir değer döndürmüyor. (yöntemin hiçbir yöntemi yoktur `Return` .) Ancak, yöntemi bir `Task` olarak bir olarak döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-232">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="6e6e2-233">Bu nedenle, yöntem türünü olarak değiştirin `Sub` `Function` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-233">Therefore, change the method type from `Sub` to `Function`.</span></span> <span data-ttu-id="6e6e2-234">İşlevin dönüş türü `Task` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-234">The return type of the function is `Task`.</span></span>

    <span data-ttu-id="6e6e2-235">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-235">The following code shows these changes.</span></span>

    ```vb
    Private Async Function SumPageSizesAsync() As Task
    ```

    <span data-ttu-id="6e6e2-236">' A dönüştürme `SumPageSizes` `SumPageSizesAsync` işlemi tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-236">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a><span data-ttu-id="6e6e2-237">StartButton_Click zaman uyumsuz bir metoda Dönüştür</span><span class="sxs-lookup"><span data-stu-id="6e6e2-237">Convert startButton_Click to an asynchronous method</span></span>

1. <span data-ttu-id="6e6e2-238">Daha önce yapmadıysanız, olay işleyicisinde, çağrılan yöntemin adını `SumPageSizes` olarak olarak değiştirin `SumPageSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-238">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>

2. <span data-ttu-id="6e6e2-239">`SumPageSizesAsync`Zaman uyumsuz bir yöntem olduğundan, olay işleyicisindeki kodu, sonucu bekleme olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-239">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>

    <span data-ttu-id="6e6e2-240">`SumPageSizesAsync`İçindeki çağrısını yansıtan çağrı `CopyToAsync` `GetURLContentsAsync` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-240">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="6e6e2-241">Çağrı `Task` a değil, döndürür `Task(T)` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-241">The call returns a `Task`, not a `Task(T)`.</span></span>

    <span data-ttu-id="6e6e2-242">Önceki yordamlarda olduğu gibi, çağrıyı tek bir deyim veya iki deyim kullanarak dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-242">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="6e6e2-243">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-243">The following code shows these changes.</span></span>

    ```vb
    ' One-step async call.
    Await SumPageSizesAsync()

    ' Two-step async call.
    Dim sumTask As Task = SumPageSizesAsync()
    Await sumTask
    ```

3. <span data-ttu-id="6e6e2-244">İşlemi yanlışlıkla yeniden girmeye engel olmak için, `startButton_Click` **Başlangıç** düğmesini devre dışı bırakmak için aşağıdaki ifadeyi ' ın üst kısmına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-244">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>

    ```vb
    ' Disable the button until the operation is complete.
    startButton.IsEnabled = False
    ```

    <span data-ttu-id="6e6e2-245">Olay işleyicisinin sonundaki düğmeyi yeniden etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-245">You can reenable the button at the end of the event handler.</span></span>

    ```vb
    ' Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = True
    ```

    <span data-ttu-id="6e6e2-246">Yeniden giriş hakkında daha fazla bilgi için bkz. [zaman uyumsuz uygulamalarda yeniden girişi işleme (Visual Basic)](handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="6e6e2-246">For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](handling-reentrancy-in-async-apps.md).</span></span>

4. <span data-ttu-id="6e6e2-247">Son olarak, `Async` olay işleyicisinin beklebilmesi için değiştiricisini bildirime ekleyin `SumPagSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-247">Finally, add the `Async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>

    ```vb
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
    ```

    <span data-ttu-id="6e6e2-248">Genellikle, olay işleyicilerinin adları değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-248">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="6e6e2-249">`Task`Olay işleyicilerinin Visual Basic yordamlar olması gerektiğinden, dönüş türü olarak değiştirilmez `Sub` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-249">The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.</span></span>

    <span data-ttu-id="6e6e2-250">Projenin zaman uyumlu olarak zaman uyumsuz işlemeye dönüştürülmesi işlemi tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-250">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>

## <a name="test-the-asynchronous-solution"></a><span data-ttu-id="6e6e2-251">Zaman uyumsuz çözümü test etme</span><span class="sxs-lookup"><span data-stu-id="6e6e2-251">Test the asynchronous solution</span></span>

1. <span data-ttu-id="6e6e2-252">Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-252">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

2. <span data-ttu-id="6e6e2-253">Zaman uyumlu çözümün çıktısına benzeyen çıkış görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-253">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="6e6e2-254">Ancak, aşağıdaki farklılıklara dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-254">However, notice the following differences.</span></span>

    - <span data-ttu-id="6e6e2-255">İşlem tamamlandıktan sonra sonuçların hepsi aynı anda gerçekleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-255">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="6e6e2-256">Örneğin, her iki program içinde `startButton_Click` metin kutusunu temizleyen bir satır içerir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-256">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="6e6e2-257">Tek bir sonuç kümesi görüntülendikten sonra **Başlat** düğmesini ikinci bir kez seçerseniz, çalıştırmalar arasındaki metin kutusunu temizlemek amaç.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-257">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="6e6e2-258">Zaman uyumlu sürümde, metin kutusu yalnızca sayımlar ikinci kez görüntülenmeden önce temizlenir, İndirmeler tamamlandığında ve Kullanıcı arabirimi iş parçacığı başka iş yapmak için ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-258">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="6e6e2-259">Zaman uyumsuz sürümde, **Başlat** düğmesini seçtikten sonra metin kutusu hemen temizlenir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-259">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>

    - <span data-ttu-id="6e6e2-260">En önemlisi, indirme sırasında UI iş parçacığı engellenmiyor.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-260">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="6e6e2-261">Web kaynakları indirilirken, sayıldıkça ve görüntülenirken pencereyi taşıyabilir veya yeniden boyutlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-261">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="6e6e2-262">Web sitelerinden biri yavaşsa veya yanıt vermiyorsa, **Kapat** düğmesini (sağ üst köşedeki kırmızı alanda bulunan x) seçerek işlemi iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-262">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>

## <a name="replace-the-geturlcontentsasync-method-with-a-net-framework-method"></a><span data-ttu-id="6e6e2-263">GetURLContentsAsync yöntemini bir .NET Framework yöntemiyle değiştirin</span><span class="sxs-lookup"><span data-stu-id="6e6e2-263">Replace the GetURLContentsAsync method with a .NET Framework method</span></span>

1. <span data-ttu-id="6e6e2-264">.NET Framework kullanabileceğiniz birçok zaman uyumsuz yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-264">The .NET Framework provides many async methods that you can use.</span></span> <span data-ttu-id="6e6e2-265">Bunlardan biri, <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> yöntemi Bu izlenecek yol için yalnızca ihtiyacınız olanları yapar.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-265">One of them, the <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> method, does just what you need for this walkthrough.</span></span> <span data-ttu-id="6e6e2-266">`GetURLContentsAsync`Daha önceki bir yordamda oluşturduğunuz yöntemi yerine kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-266">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>

    <span data-ttu-id="6e6e2-267">İlk adım <xref:System.Net.Http.HttpClient> yönteminde bir nesne oluşturmaktır `SumPageSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-267">The first step is to create an <xref:System.Net.Http.HttpClient> object in the `SumPageSizesAsync` method.</span></span> <span data-ttu-id="6e6e2-268">Yönteminin başlangıcında aşağıdaki bildirimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-268">Add the following declaration at the start of the method.</span></span>

    ```vb
    ' Declare an HttpClient object and increase the buffer size. The
    ' default buffer size is 65,536.
    Dim client As HttpClient =
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}
    ```

2. <span data-ttu-id="6e6e2-269">İçinde, yöntemine yapılan çağrıyı yöntemine `SumPageSizesAsync,` `GetURLContentsAsync` bir çağrı ile değiştirin `HttpClient` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-269">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>

    ```vb
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ```

3. <span data-ttu-id="6e6e2-270">Yazdığınız yöntemi kaldırın veya not edin `GetURLContentsAsync` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-270">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>

4. <span data-ttu-id="6e6e2-271">Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-271">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="6e6e2-272">Projenin bu sürümünün davranışı, "zaman uyumsuz çözümü test etmek Için" yordamının açıklandığı, ancak sizin de daha az çaba gösteren davranışla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-272">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>

## <a name="example"></a><span data-ttu-id="6e6e2-273">Örnek</span><span class="sxs-lookup"><span data-stu-id="6e6e2-273">Example</span></span>

<span data-ttu-id="6e6e2-274">Aşağıda, zaman uyumsuz yöntemi kullanan dönüştürülmüş zaman uyumsuz çözümün tam örneği verilmiştir `GetURLContentsAsync` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-274">The following is the full example of the converted asynchronous solution that uses the asynchronous `GetURLContentsAsync` method.</span></span> <span data-ttu-id="6e6e2-275">Özgün, zaman uyumlu çözüme kesinlikle benzediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-275">Notice that it strongly resembles the original, synchronous solution.</span></span>

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

<span data-ttu-id="6e6e2-276">Aşağıdaki kod, yöntemini kullanan çözümün tam örneğini içerir `HttpClient` `GetByteArrayAsync` .</span><span class="sxs-lookup"><span data-stu-id="6e6e2-276">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6e6e2-277">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e6e2-277">See also</span></span>

- [<span data-ttu-id="6e6e2-278">Zaman uyumsuz örnek: Web 'e yönelik Izlenecek yol (C# ve Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e6e2-278">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [<span data-ttu-id="6e6e2-279">Await Işleci</span><span class="sxs-lookup"><span data-stu-id="6e6e2-279">Await Operator</span></span>](../../../language-reference/operators/await-operator.md)
- [<span data-ttu-id="6e6e2-280">Eş</span><span class="sxs-lookup"><span data-stu-id="6e6e2-280">Async</span></span>](../../../language-reference/modifiers/async.md)
- [<span data-ttu-id="6e6e2-281">Async ve await ile zaman uyumsuz programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e6e2-281">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="6e6e2-282">Zaman uyumsuz dönüş türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e6e2-282">Async Return Types (Visual Basic)</span></span>](async-return-types.md)
- [<span data-ttu-id="6e6e2-283">Görev tabanlı zaman uyumsuz programlama (TAP)</span><span class="sxs-lookup"><span data-stu-id="6e6e2-283">Task-based Asynchronous Programming (TAP)</span></span>](https://www.microsoft.com/download/details.aspx?id=19957)
- [<span data-ttu-id="6e6e2-284">Nasıl yapılır: Task. WhenAll kullanarak zaman uyumsuz Izlenecek yolu genişletme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e6e2-284">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [<span data-ttu-id="6e6e2-285">Nasıl yapılır: Async ve await kullanarak birden çok Web Isteğini paralel hale getirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e6e2-285">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
