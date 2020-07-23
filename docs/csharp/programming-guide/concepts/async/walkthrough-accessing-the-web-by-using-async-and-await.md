---
title: "İzlenecek yol: Async ve await kullanarak Web 'e erişme (C#)"
description: Bu izlenecek yol, zaman uyumsuz ve await özelliklerini kullanan bir zaman uyumlu uygulamayı C# dilinde zaman uyumsuz bir çözüme dönüştürür.
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: d643793bfcdeaaeff56dd252c510d197a45442f9
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925117"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a><span data-ttu-id="b6ae3-103">İzlenecek yol: Async ve await kullanarak Web 'e erişme (C#)</span><span class="sxs-lookup"><span data-stu-id="b6ae3-103">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>

<span data-ttu-id="b6ae3-104">Zaman uyumsuz programları, zaman uyumsuz/await özelliklerini kullanarak daha kolay ve daha canlı bir şekilde yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-104">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="b6ae3-105">Zaman uyumlu kod gibi görünen zaman uyumsuz kod yazabilir ve derleyicinin zaman uyumsuz kodun genellikle sahip olduğu zor geri çağırma işlevlerini ve devamlılığını işlemesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-105">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>

<span data-ttu-id="b6ae3-106">Zaman uyumsuz özellik hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama (C#)](./index.md).</span><span class="sxs-lookup"><span data-stu-id="b6ae3-106">For more information about the Async feature, see [Asynchronous Programming with async and await (C#)](./index.md).</span></span>

<span data-ttu-id="b6ae3-107">Bu izlenecek yol, bir Web sitesi listesindeki bayt sayısını toplayan bir zaman uyumlu Windows Presentation Foundation (WPF) uygulamasıyla başlar.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-107">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="b6ae3-108">İzlenecek yol, yeni özellikleri kullanarak uygulamayı zaman uyumsuz bir çözüme dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-108">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>

<span data-ttu-id="b6ae3-109">Uygulamaları kendiniz derlemek istemiyorsanız, [zaman uyumsuz örneği indirebilirsiniz: Web 'e (C# ve Visual Basic) erişme](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="b6ae3-109">If you don't want to build the applications yourself, you can download [Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

> [!NOTE]
> <span data-ttu-id="b6ae3-110">Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="create-a-wpf-application"></a><span data-ttu-id="b6ae3-111">WPF uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="b6ae3-111">Create a WPF application</span></span>

1. <span data-ttu-id="b6ae3-112">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-112">Start Visual Studio.</span></span>

2. <span data-ttu-id="b6ae3-113">Menü çubuğunda **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-113">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="b6ae3-114">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-114">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="b6ae3-115">**Yüklü şablonlar** bölmesinde, Visual C# ' ı seçin ve ardından Proje türleri listesinden **WPF uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-115">In the **Installed Templates** pane, choose Visual C#, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="b6ae3-116">**Ad** metin kutusuna girin `AsyncExampleWPF` ve sonra **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-116">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>

     <span data-ttu-id="b6ae3-117">Yeni proje **Çözüm Gezgini**görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-117">The new project appears in **Solution Explorer**.</span></span>

## <a name="design-a-simple-wpf-mainwindow"></a><span data-ttu-id="b6ae3-118">Basit bir WPF MainWindow tasarımı</span><span class="sxs-lookup"><span data-stu-id="b6ae3-118">Design a simple WPF MainWindow</span></span>

1. <span data-ttu-id="b6ae3-119">Visual Studio Code düzenleyicisinde **MainWindow. xaml** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-119">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

2. <span data-ttu-id="b6ae3-120">**Araç kutusu** penceresi görünür değilse, **Görünüm** menüsünü açın ve ardından **araç kutusu**' nu seçin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-120">If the **Toolbox** window isn't visible, open the **View** menu, and then choose **Toolbox**.</span></span>

3. <span data-ttu-id="b6ae3-121">**MainWindow** penceresine bir **Button** denetimi ve **TextBox** denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-121">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>

4. <span data-ttu-id="b6ae3-122">**TextBox** denetimini vurgulayın ve **Özellikler** penceresinde aşağıdaki değerleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="b6ae3-122">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="b6ae3-123">**Name** özelliğini olarak ayarlayın `resultsTextBox` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-123">Set the **Name** property to `resultsTextBox`.</span></span>

    - <span data-ttu-id="b6ae3-124">**Height** özelliğini 250 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-124">Set the **Height** property to 250.</span></span>

    - <span data-ttu-id="b6ae3-125">**Width** özelliğini 500 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-125">Set the **Width** property to 500.</span></span>

    - <span data-ttu-id="b6ae3-126">**Metin** sekmesinde, Lucida Console veya Global tek boşluk gibi tek boşluklu bir yazı tipi belirtin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-126">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>

5. <span data-ttu-id="b6ae3-127">**Düğme** denetimini vurgulayın ve **Özellikler** penceresinde aşağıdaki değerleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="b6ae3-127">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="b6ae3-128">**Name** özelliğini olarak ayarlayın `startButton` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-128">Set the **Name** property to `startButton`.</span></span>

    - <span data-ttu-id="b6ae3-129">**İçerik** özelliğinin değerini **düğmeden** **başla**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-129">Change the value of the **Content** property from **Button** to **Start**.</span></span>

6. <span data-ttu-id="b6ae3-130">Metin kutusunu ve düğmeyi her ikisinin de **MainWindow** penceresinde görünmesi için konumlandırın.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-130">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>

     <span data-ttu-id="b6ae3-131">WPF XAML Tasarımcısı hakkında daha fazla bilgi için, bkz. [XAML Tasarımcısı kullanarak Kullanıcı arabirimi oluşturma](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="b6ae3-131">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>

## <a name="add-a-reference"></a><span data-ttu-id="b6ae3-132">Başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="b6ae3-132">Add a reference</span></span>

1. <span data-ttu-id="b6ae3-133">**Çözüm Gezgini**, projenizin adını vurgulayın.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-133">In **Solution Explorer**, highlight your project's name.</span></span>

2. <span data-ttu-id="b6ae3-134">Menü çubuğunda **Proje**  >  **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-134">On the menu bar, choose **Project** > **Add Reference**.</span></span>

     <span data-ttu-id="b6ae3-135">**Başvuru Yöneticisi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-135">The **Reference Manager** dialog box appears.</span></span>

3. <span data-ttu-id="b6ae3-136">İletişim kutusunun üst kısmında, projenizin .NET Framework 4,5 veya üstünü hedeflediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-136">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>

4. <span data-ttu-id="b6ae3-137">**Derlemeler** kategorisinde, zaten seçili değilse **Framework** ' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-137">In the **Assemblies** category, choose **Framework** if it isn't already chosen.</span></span>

5. <span data-ttu-id="b6ae3-138">Ad listesinde, **System .net. http** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-138">In the list of names, select the **System.Net.Http** check box.</span></span>

6. <span data-ttu-id="b6ae3-139">İletişim kutusunu kapatmak için **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-139">Choose the **OK** button to close the dialog box.</span></span>

## <a name="add-necessary-using-directives"></a><span data-ttu-id="b6ae3-140">Gerekli yönergeleri kullanarak ekleme</span><span class="sxs-lookup"><span data-stu-id="b6ae3-140">Add necessary using directives</span></span>

1. <span data-ttu-id="b6ae3-141">**Çözüm Gezgini**' de, MainWindow.xaml.cs için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-141">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

2. <span data-ttu-id="b6ae3-142">`using`Zaten mevcut değilse, kod dosyasının en üstüne aşağıdaki yönergeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-142">Add the following `using` directives at the top of the code file if they're not already present.</span></span>

    ```csharp
    using System.Net.Http;
    using System.Net;
    using System.IO;
    ```

## <a name="create-a-synchronous-app"></a><span data-ttu-id="b6ae3-143">Zaman uyumlu uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="b6ae3-143">Create a synchronous app</span></span>

1. <span data-ttu-id="b6ae3-144">Tasarım penceresinde, MainWindow. xaml, **Start** `startButton_Click` MainWindow.xaml.cs içinde olay Işleyicisini oluşturmak için Başlat düğmesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-144">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>

2. <span data-ttu-id="b6ae3-145">MainWindow.xaml.cs içinde aşağıdaki kodu ' ın gövdesine kopyalayın `startButton_Click` :</span><span class="sxs-lookup"><span data-stu-id="b6ae3-145">In MainWindow.xaml.cs, copy the following code into the body of `startButton_Click`:</span></span>

    ```csharp
    resultsTextBox.Clear();
    SumPageSizes();
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";
    ```

    <span data-ttu-id="b6ae3-146">Kod, uygulamayı yönlendiren yöntemini çağırır `SumPageSizes` ve denetim ' e döndüğünde bir ileti görüntüler `startButton_Click` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-146">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>

3. <span data-ttu-id="b6ae3-147">Zaman uyumlu çözüm kodu aşağıdaki dört yöntemi içerir:</span><span class="sxs-lookup"><span data-stu-id="b6ae3-147">The code for the synchronous solution contains the following four methods:</span></span>

    - <span data-ttu-id="b6ae3-148">`SumPageSizes`, ' den Web sayfası URL 'Lerinin bir listesini alır ve `SetUpURLList` ardından `GetURLContents` `DisplayResults` her URL 'yi çağırır ve işler.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-148">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>

    - <span data-ttu-id="b6ae3-149">`SetUpURLList`, bir Web adresleri listesi oluşturur ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-149">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>

    - <span data-ttu-id="b6ae3-150">`GetURLContents`, her bir Web sitesinin içeriğini indirir ve bir bayt dizisi olarak içeriğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-150">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>

    - <span data-ttu-id="b6ae3-151">`DisplayResults`, her bir URL için bayt dizisindeki bayt sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-151">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>

    <span data-ttu-id="b6ae3-152">Aşağıdaki dört yöntemi kopyalayın ve sonra `startButton_Click` MainWindow.xaml.cs içindeki olay işleyicisinin altına yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="b6ae3-152">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.cs:</span></span>

    ```csharp
    private void SumPageSizes()
    {
        // Make a list of web addresses.
        List<string> urlList = SetUpURLList();

        var total = 0;
        foreach (var url in urlList)
        {
            // GetURLContents returns the contents of url as a byte array.
            byte[] urlContents = GetURLContents(url);

            DisplayResults(url, urlContents);

            // Update the total.
            total += urlContents.Length;
        }

        // Display the total count for all of the web addresses.
        resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
    }

    private List<string> SetUpURLList()
    {
        var urls = new List<string>
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
        };
        return urls;
    }

    private byte[] GetURLContents(string url)
    {
        // The downloaded resource ends up in the variable named content.
        var content = new MemoryStream();

        // Initialize an HttpWebRequest for the current URL.
        var webReq = (HttpWebRequest)WebRequest.Create(url);

        // Send the request to the Internet resource and wait for
        // the response.
        // Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.
        using (WebResponse response = webReq.GetResponse())
        {
            // Get the data stream that is associated with the specified URL.
            using (Stream responseStream = response.GetResponseStream())
            {
                // Read the bytes in responseStream and copy them to content.
                responseStream.CopyTo(content);
            }
        }

        // Return the result as a byte array.
        return content.ToArray();
    }

    private void DisplayResults(string url, byte[] content)
    {
        // Display the length of each website. The string format
        // is designed to be used with a monospaced font, such as
        // Lucida Console or Global Monospace.
        var bytes = content.Length;
        // Strip off the "https://".
        var displayURL = url.Replace("https://", "");
        resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
    }
    ```

## <a name="test-the-synchronous-solution"></a><span data-ttu-id="b6ae3-153">Zaman uyumlu çözümü test etme</span><span class="sxs-lookup"><span data-stu-id="b6ae3-153">Test the synchronous solution</span></span>

<span data-ttu-id="b6ae3-154">Programı çalıştırmak için **F5** tuşunu seçin ve sonra **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-154">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

<span data-ttu-id="b6ae3-155">Aşağıdaki listeye benzer bir çıktı görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="b6ae3-155">Output that resembles the following list should appear:</span></span>

```text
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

<span data-ttu-id="b6ae3-156">Sayıları görüntülemenin birkaç saniye sürdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-156">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="b6ae3-157">Bu süre boyunca, Kullanıcı arabirimi iş parçacığı istenen kaynakların indirilmesini beklerken engellenir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-157">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="b6ae3-158">Sonuç olarak, **Başlat** düğmesini seçtikten sonra görüntü penceresini taşıyamaz, ekranı kaplamaz, simge durumuna küçültebilir ya da kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-158">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="b6ae3-159">Bu çalışmalar, bayt sayıları görünene kadar başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-159">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="b6ae3-160">Bir Web sitesi yanıt vermiyorsa, hangi sitenin başarısız olduğunun belirtii olmaz.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-160">If a website isn't responding, you have no indication of which site failed.</span></span> <span data-ttu-id="b6ae3-161">Beklemeyi durdurup programı kapatmanız zordur.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-161">It is difficult even to stop waiting and close the program.</span></span>

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a><span data-ttu-id="b6ae3-162">GetURLContents öğesini zaman uyumsuz bir metoda Dönüştür</span><span class="sxs-lookup"><span data-stu-id="b6ae3-162">Convert GetURLContents to an asynchronous method</span></span>

1. <span data-ttu-id="b6ae3-163">Zaman uyumlu çözümü zaman uyumsuz bir çözüme dönüştürmek için, `GetURLContents` <xref:System.Net.HttpWebRequest> yönteme <xref:System.Net.HttpWebRequest.GetResponse%2A> ve yöntemine yapılan çağrılar <xref:System.IO.Stream> <xref:System.IO.Stream.CopyTo%2A> uygulamanın Web 'e eriştiği yerdir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-163">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="b6ae3-164">.NET Framework, her iki yöntemin de zaman uyumsuz sürümlerini sağlayarak dönüştürmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-164">.NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>

     <span data-ttu-id="b6ae3-165">İçinde kullanılan yöntemler hakkında daha fazla bilgi için `GetURLContents` bkz <xref:System.Net.WebRequest> ..</span><span class="sxs-lookup"><span data-stu-id="b6ae3-165">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b6ae3-166">Bu izlenecek yolda bulunan adımları izleyerek bazı derleyici hataları görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-166">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="b6ae3-167">Bunları yoksayabilir ve İzlenecek yol ile devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-167">You can ignore them and continue with the walkthrough.</span></span>

     <span data-ttu-id="b6ae3-168">' In üçüncü satırında çağrılan yöntemi, `GetURLContents` `GetResponse` zaman uyumsuz, görev tabanlı <xref:System.Net.WebRequest.GetResponseAsync%2A> metoda değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-168">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>

    ```csharp
    using (WebResponse response = webReq.GetResponseAsync())
    ```

2. <span data-ttu-id="b6ae3-169">`GetResponseAsync`döndürür <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-169">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="b6ae3-170">Bu durumda, *görev dönüş değişkeni*, `TResult` türündedir <xref:System.Net.WebResponse> .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-170">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="b6ae3-171">Görev, `WebResponse` istenen veriler indirildikten ve görevin tamamlanmasını çalıştırdıktan sonra gerçek bir nesne oluşturmak için bir taahhüddir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-171">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>

     <span data-ttu-id="b6ae3-172">`WebResponse`Görevden değeri almak için, aşağıdaki kodda gösterildiği gibi çağrısına bir [await](../../../language-reference/operators/await.md) işleci uygulayın `GetResponseAsync` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-172">To retrieve the `WebResponse` value from the task, apply an [await](../../../language-reference/operators/await.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>

    ```csharp
    using (WebResponse response = await webReq.GetResponseAsync())
    ```

     <span data-ttu-id="b6ae3-173">`await`İşleç, beklenen görev tamamlanana kadar geçerli yöntemin yürütülmesini askıya alır `GetURLContents` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-173">The `await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="b6ae3-174">Bu arada, Denetim geçerli yöntemi çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-174">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="b6ae3-175">Bu örnekte, geçerli yöntem `GetURLContents` ve arayan ' dır `SumPageSizes` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-175">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="b6ae3-176">Görev tamamlandığında, taahhüt edilen `WebResponse` nesne, beklenen görevin değeri olarak üretilir ve değişkenine atanır `response` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-176">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>

     <span data-ttu-id="b6ae3-177">Önceki deyim, ne olacağını açıklamak için aşağıdaki iki ifadeye ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-177">The previous statement can be separated into the following two statements to clarify what happens.</span></span>

    ```csharp
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();
    //using (WebResponse response = await responseTask)
    ```

     <span data-ttu-id="b6ae3-178">Çağrısı `webReq.GetResponseAsync` bir `Task(Of WebResponse)` veya döndürür `Task<WebResponse>` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-178">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="b6ae3-179">Sonra değeri almak için göreve bir Await işleci uygulanır `WebResponse` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-179">Then an await operator is applied to the task to retrieve the `WebResponse` value.</span></span>

     <span data-ttu-id="b6ae3-180">Zaman uyumsuz yönteminiz görevin tamamlanmasına bağlı değilse, bu iki deyim arasında, zaman uyumsuz metoda yapılan çağrıdan sonra ve işleç uygulanmadan önce, yöntemi bu iş ile devam edebilir `await` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-180">If your async method has work to do that doesn't depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the `await` operator is applied.</span></span> <span data-ttu-id="b6ae3-181">Örnekler için bkz. [Async ve await (c#) kullanarak birden çok web isteğini paralel hale getirme](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) ve [Task. WhenAll (c#) kullanarak zaman uyumsuz izlenecek yolu genişletme](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="b6ae3-181">For examples, see [How to make multiple web requests in parallel by using async and await (C#)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

3. <span data-ttu-id="b6ae3-182">`await`Önceki adımda işleci eklediğiniz için bir derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-182">Because you added the `await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="b6ae3-183">İşleci yalnızca [zaman uyumsuz](../../../language-reference/keywords/async.md) değiştiriciyle işaretlenen yöntemlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-183">The operator can be used only in methods that are marked with the [async](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="b6ae3-184">Çağrısını ' a ' çağrısı ile değiştirmek için dönüştürme adımlarını tekrarlarken hatayı yoksayın `CopyTo` `CopyToAsync` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-184">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>

    - <span data-ttu-id="b6ae3-185">Olarak çağrılan metodun adını değiştirin <xref:System.IO.Stream.CopyToAsync%2A> .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-185">Change the name of the method that's called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>

    - <span data-ttu-id="b6ae3-186">`CopyTo`Ya da `CopyToAsync` yöntemi, bayt bağımsız değişkenine bayt kopyalar, `content` ve anlamlı bir değer döndürmez.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-186">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn't return a meaningful value.</span></span> <span data-ttu-id="b6ae3-187">Zaman uyumlu sürümde, çağrısı `CopyTo` bir değer döndürmeyen basit bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-187">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="b6ae3-188">Zaman uyumsuz sürüm, `CopyToAsync` bir döndürür <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-188">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="b6ae3-189">Görev, "Task (void)" gibi çalışır ve yöntemin beklenmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-189">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="b6ae3-190">`Await` `await` `CopyToAsync` Aşağıdaki kodda gösterildiği gibi, çağrısına yönelik veya çağrısı yapın.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-190">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>

        ```csharp
        await responseStream.CopyToAsync(content);
        ```

         <span data-ttu-id="b6ae3-191">Önceki ifade aşağıdaki iki kod satırını abbreviates.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-191">The previous statement abbreviates the following two lines of code.</span></span>

        ```csharp
        // CopyToAsync returns a Task, not a Task<T>.
        //Task copyTask = responseStream.CopyToAsync(content);

        // When copyTask is completed, content contains a copy of
        // responseStream.
        //await copyTask;
        ```

4. <span data-ttu-id="b6ae3-192">Tüm bunlar ' de yapılacak şekilde, `GetURLContents` yöntem imzasını ayarlamasıdır.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-192">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="b6ae3-193">`await`İşlecini yalnızca [zaman uyumsuz](../../../language-reference/keywords/async.md) değiştiriciyle işaretlenen yöntemlerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-193">You can use the `await` operator only in methods that are marked with the [async](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="b6ae3-194">Aşağıdaki kodun gösterdiği gibi, yöntemi *zaman uyumsuz bir yöntem*olarak işaretlemek için değiştirici ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-194">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>

    ```csharp
    private async byte[] GetURLContents(string url)
    ```

5. <span data-ttu-id="b6ae3-195">Zaman uyumsuz bir yöntemin dönüş türü yalnızca <xref:System.Threading.Tasks.Task> , <xref:System.Threading.Tasks.Task%601> veya `void` C# olabilir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-195">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or `void` in C#.</span></span> <span data-ttu-id="b6ae3-196">Genellikle, bir dönüş türü `void` yalnızca zaman uyumsuz olay işleyicide kullanılır, burada `void` gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-196">Typically, a return type of `void` is used only in an async event handler, where `void` is required.</span></span> <span data-ttu-id="b6ae3-197">Diğer durumlarda, `Task(T)` Tamamlanan yöntemin T türünde bir değer döndüren bir [Return](../../../language-reference/keywords/return.md) ifadesine sahip olması ve `Task` Tamamlanan yöntemin anlamlı bir değer döndürmemesi durumunda kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-197">In other cases, you use `Task(T)` if the completed method has a [return](../../../language-reference/keywords/return.md) statement that returns a value of type T, and you use `Task` if the completed method doesn't return a meaningful value.</span></span> <span data-ttu-id="b6ae3-198">`Task`Dönüş türünü anlamı "görev (void)" olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-198">You can think of the `Task` return type as meaning "Task(void)."</span></span>

     <span data-ttu-id="b6ae3-199">Daha fazla bilgi için bkz. [Async Return Types (C#)](./async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="b6ae3-199">For more information, see [Async Return Types (C#)](./async-return-types.md).</span></span>

     <span data-ttu-id="b6ae3-200">Yöntem `GetURLContents` bir return ifadesine sahiptir ve ifade bir bayt dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-200">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="b6ae3-201">Bu nedenle, zaman uyumsuz sürümün dönüş türü görev (T), burada T bir bayt dizisidir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-201">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="b6ae3-202">Yöntem imzasında aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="b6ae3-202">Make the following changes in the method signature:</span></span>

    - <span data-ttu-id="b6ae3-203">Dönüş türünü olarak değiştirin `Task<byte[]>` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-203">Change the return type to `Task<byte[]>`.</span></span>

    - <span data-ttu-id="b6ae3-204">Kurala göre, zaman uyumsuz metotların "Async" ile biten adları vardır. bu nedenle, yöntemi yeniden adlandırın `GetURLContentsAsync` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-204">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>

     <span data-ttu-id="b6ae3-205">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-205">The following code shows these changes.</span></span>

    ```csharp
    private async Task<byte[]> GetURLContentsAsync(string url)
    ```

     <span data-ttu-id="b6ae3-206">Bu az değişiklikle, `GetURLContents` zaman uyumsuz bir metoda dönüştürme işlemi tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-206">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a><span data-ttu-id="b6ae3-207">Sumpageslikleri zaman uyumsuz bir metoda Dönüştür</span><span class="sxs-lookup"><span data-stu-id="b6ae3-207">Convert SumPageSizes to an asynchronous method</span></span>

1. <span data-ttu-id="b6ae3-208">İçin önceki yordamdaki adımları tekrarlayın `SumPageSizes` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-208">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="b6ae3-209">İlk olarak, çağrısını `GetURLContents` zaman uyumsuz bir çağrıya değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-209">First, change the call to `GetURLContents` to an asynchronous call.</span></span>

    - <span data-ttu-id="b6ae3-210">`GetURLContents` `GetURLContentsAsync` Daha önce yapmadıysanız, ' dan ' a çağrılan metodun adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-210">Change the name of the method that's called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>

    - <span data-ttu-id="b6ae3-211">`await` `GetURLContentsAsync` Bayt dizi değerini almak için döndüren göreve uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-211">Apply `await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>

     <span data-ttu-id="b6ae3-212">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-212">The following code shows these changes.</span></span>

    ```csharp
    byte[] urlContents = await GetURLContentsAsync(url);
    ```

     <span data-ttu-id="b6ae3-213">Önceki atama, aşağıdaki iki kod satırını abbreviates.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-213">The previous assignment abbreviates the following two lines of code.</span></span>

    ```csharp
    // GetURLContentsAsync returns a Task<T>. At completion, the task
    // produces a byte array.
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //byte[] urlContents = await getContentsTask;
    ```

2. <span data-ttu-id="b6ae3-214">Yöntemin imzasında aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="b6ae3-214">Make the following changes in the method's signature:</span></span>

    - <span data-ttu-id="b6ae3-215">Yöntemi `async` değiştiriciyle işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-215">Mark the method with the `async` modifier.</span></span>

    - <span data-ttu-id="b6ae3-216">Yöntem adına "Async" ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-216">Add "Async" to the method name.</span></span>

    - <span data-ttu-id="b6ae3-217">Bir görev dönüş değişkeni yok, T, bu kez `SumPageSizesAsync` t için bir değer döndürmüyor. (yöntemin hiçbir yöntemi yoktur `return` .) Ancak, yöntemi bir `Task` olarak bir olarak döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-217">There is no task return variable, T, this time because `SumPageSizesAsync` doesn't return a value for T. (The method has no `return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="b6ae3-218">Bu nedenle, yönteminin dönüş türünü ' den ' `void` e değiştirin `Task` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-218">Therefore, change the return type of the method from `void` to `Task`.</span></span>

    <span data-ttu-id="b6ae3-219">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-219">The following code shows these changes.</span></span>

    ```csharp
    private async Task SumPageSizesAsync()
    ```

     <span data-ttu-id="b6ae3-220">' A dönüştürme `SumPageSizes` `SumPageSizesAsync` işlemi tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-220">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a><span data-ttu-id="b6ae3-221">StartButton_Click zaman uyumsuz bir metoda Dönüştür</span><span class="sxs-lookup"><span data-stu-id="b6ae3-221">Convert startButton_Click to an asynchronous method</span></span>

1. <span data-ttu-id="b6ae3-222">Daha önce yapmadıysanız, olay işleyicisinde, çağrılan yöntemin adını `SumPageSizes` olarak olarak değiştirin `SumPageSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-222">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven't already done so.</span></span>

2. <span data-ttu-id="b6ae3-223">`SumPageSizesAsync`Zaman uyumsuz bir yöntem olduğundan, olay işleyicisindeki kodu, sonucu bekleme olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-223">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>

     <span data-ttu-id="b6ae3-224">`SumPageSizesAsync`İçindeki çağrısını yansıtan çağrı `CopyToAsync` `GetURLContentsAsync` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-224">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="b6ae3-225">Çağrı `Task` a değil, döndürür `Task(T)` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-225">The call returns a `Task`, not a `Task(T)`.</span></span>

     <span data-ttu-id="b6ae3-226">Önceki yordamlarda olduğu gibi, çağrıyı tek bir deyim veya iki deyim kullanarak dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-226">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="b6ae3-227">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-227">The following code shows these changes.</span></span>

    ```csharp
    // One-step async call.
    await SumPageSizesAsync();

    // Two-step async call.
    //Task sumTask = SumPageSizesAsync();
    //await sumTask;
    ```

3. <span data-ttu-id="b6ae3-228">İşlemi yanlışlıkla yeniden girmeye engel olmak için, `startButton_Click` **Başlangıç** düğmesini devre dışı bırakmak için aşağıdaki ifadeyi ' ın üst kısmına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-228">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>

    ```csharp
    // Disable the button until the operation is complete.
    startButton.IsEnabled = false;
    ```

     <span data-ttu-id="b6ae3-229">Olay işleyicisinin sonundaki düğmeyi yeniden etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-229">You can reenable the button at the end of the event handler.</span></span>

    ```csharp
    // Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = true;
    ```

     <span data-ttu-id="b6ae3-230">Yeniden giriş hakkında daha fazla bilgi için bkz. [zaman uyumsuz uygulamalarda yeniden girişi işleme (C#)](./handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="b6ae3-230">For more information about reentrancy, see [Handling Reentrancy in Async Apps (C#)](./handling-reentrancy-in-async-apps.md).</span></span>

4. <span data-ttu-id="b6ae3-231">Son olarak, `async` olay işleyicisinin beklebilmesi için değiştiricisini bildirime ekleyin `SumPagSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-231">Finally, add the `async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>

    ```csharp
    private async void startButton_Click(object sender, RoutedEventArgs e)
    ```

     <span data-ttu-id="b6ae3-232">Genellikle, olay işleyicilerinin adları değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-232">Typically, the names of event handlers aren't changed.</span></span> <span data-ttu-id="b6ae3-233">Olay işleyicilerinin dönmesi gereken için dönüş türü olarak değiştirilmez `Task` `void` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-233">The return type isn't changed to `Task` because event handlers must return `void`.</span></span>

     <span data-ttu-id="b6ae3-234">Projenin zaman uyumlu olarak zaman uyumsuz işlemeye dönüştürülmesi işlemi tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-234">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>

## <a name="test-the-asynchronous-solution"></a><span data-ttu-id="b6ae3-235">Zaman uyumsuz çözümü test etme</span><span class="sxs-lookup"><span data-stu-id="b6ae3-235">Test the asynchronous solution</span></span>

1. <span data-ttu-id="b6ae3-236">Programı çalıştırmak için **F5** tuşunu seçin ve sonra **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-236">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

2. <span data-ttu-id="b6ae3-237">Zaman uyumlu çözümün çıktısına benzeyen çıkış görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-237">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="b6ae3-238">Ancak, aşağıdaki farklılıklara dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-238">However, notice the following differences.</span></span>

    - <span data-ttu-id="b6ae3-239">İşlem tamamlandıktan sonra sonuçların hepsi aynı anda gerçekleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-239">The results don't all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="b6ae3-240">Örneğin, her iki program içinde `startButton_Click` metin kutusunu temizleyen bir satır içerir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-240">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="b6ae3-241">Tek bir sonuç kümesi görüntülendikten sonra **Başlat** düğmesini ikinci bir kez seçerseniz, çalıştırmalar arasındaki metin kutusunu temizlemek amaç.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-241">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="b6ae3-242">Zaman uyumlu sürümde, metin kutusu yalnızca sayımlar ikinci kez görüntülenmeden önce temizlenir, İndirmeler tamamlandığında ve Kullanıcı arabirimi iş parçacığı başka iş yapmak için ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-242">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="b6ae3-243">Zaman uyumsuz sürümde, **Başlat** düğmesini seçtikten sonra metin kutusu hemen temizlenir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-243">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>

    - <span data-ttu-id="b6ae3-244">En önemlisi, indirme sırasında UI iş parçacığı engellenmiyor.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-244">Most importantly, the UI thread isn't blocked during the downloads.</span></span> <span data-ttu-id="b6ae3-245">Web kaynakları indirilirken, sayıldıkça ve görüntülenirken pencereyi taşıyabilir veya yeniden boyutlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-245">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="b6ae3-246">Web sitelerinden biri yavaşsa veya yanıt vermiyorsa, **Kapat** düğmesini (sağ üst köşedeki kırmızı alanda bulunan x) seçerek işlemi iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-246">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>

## <a name="replace-method-geturlcontentsasync-with-a-net-method"></a><span data-ttu-id="b6ae3-247">GetURLContentsAsync yöntemini bir .NET yöntemiyle Değiştir</span><span class="sxs-lookup"><span data-stu-id="b6ae3-247">Replace method GetURLContentsAsync with a .NET method</span></span>

1. <span data-ttu-id="b6ae3-248">.NET Framework 4,5 ve sonraki sürümler, kullanabileceğiniz birçok zaman uyumsuz yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-248">.NET Framework 4.5 and later versions provide many async methods that you can use.</span></span> <span data-ttu-id="b6ae3-249">Bunlardan biri, <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29> Bu izlenecek yol için yalnızca ihtiyacınız olanları yapar.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-249">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="b6ae3-250">`GetURLContentsAsync`Daha önceki bir yordamda oluşturduğunuz yöntemi yerine kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-250">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>

     <span data-ttu-id="b6ae3-251">İlk adım, yönteminde bir nesne oluşturmaktır `HttpClient` `SumPageSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-251">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="b6ae3-252">Yönteminin başlangıcında aşağıdaki bildirimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-252">Add the following declaration at the start of the method.</span></span>

    ```csharp
    // Declare an HttpClient object and increase the buffer size. The
    // default buffer size is 65,536.
    HttpClient client =
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };
    ```

2. <span data-ttu-id="b6ae3-253">İçinde, yöntemine yapılan çağrıyı yöntemine `SumPageSizesAsync,` `GetURLContentsAsync` bir çağrı ile değiştirin `HttpClient` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-253">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>

    ```csharp
    byte[] urlContents = await client.GetByteArrayAsync(url);
    ```

3. <span data-ttu-id="b6ae3-254">Yazdığınız yöntemi kaldırın veya not edin `GetURLContentsAsync` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-254">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>

4. <span data-ttu-id="b6ae3-255">Programı çalıştırmak için **F5** tuşunu seçin ve sonra **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-255">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="b6ae3-256">Projenin bu sürümünün davranışı, "zaman uyumsuz çözümü test etmek Için" yordamının açıklandığı, ancak sizin de daha az çaba gösteren davranışla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-256">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>

## <a name="example-code"></a><span data-ttu-id="b6ae3-257">Örnek kod</span><span class="sxs-lookup"><span data-stu-id="b6ae3-257">Example code</span></span>

<span data-ttu-id="b6ae3-258">Aşağıdaki kod, yazdığınız zaman uyumsuz yöntemi kullanarak zaman uyumsuz bir çözüme dönüştürme işleminin tam örneğini içerir `GetURLContentsAsync` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-258">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="b6ae3-259">Özgün, zaman uyumlu çözüme kesinlikle benzediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-259">Notice that it strongly resembles the original, synchronous solution.</span></span>

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
using System.IO;
using System.Net;

namespace AsyncExampleWPF
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // Disable the button until the operation is complete.
            startButton.IsEnabled = false;

            resultsTextBox.Clear();

            // One-step async call.
            await SumPageSizesAsync();

            // Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";

            // Reenable the button in case you want to run the operation again.
            startButton.IsEnabled = true;
        }

        private async Task SumPageSizesAsync()
        {
            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            var total = 0;

            foreach (var url in urlList)
            {
                byte[] urlContents = await GetURLContentsAsync(url);

                // The previous line abbreviates the following two assignment statements.

                // GetURLContentsAsync returns a Task<T>. At completion, the task
                // produces a byte array.
                //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
                //byte[] urlContents = await getContentsTask;

                DisplayResults(url, urlContents);

                // Update the total.
                total += urlContents.Length;
            }
            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
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
            };
            return urls;
        }

        private async Task<byte[]> GetURLContentsAsync(string url)
        {
            // The downloaded resource ends up in the variable named content.
            var content = new MemoryStream();

            // Initialize an HttpWebRequest for the current URL.
            var webReq = (HttpWebRequest)WebRequest.Create(url);

            // Send the request to the Internet resource and wait for
            // the response.
            using (WebResponse response = await webReq.GetResponseAsync())

            // The previous statement abbreviates the following two statements.

            //Task<WebResponse> responseTask = webReq.GetResponseAsync();
            //using (WebResponse response = await responseTask)
            {
                // Get the data stream that is associated with the specified url.
                using (Stream responseStream = response.GetResponseStream())
                {
                    // Read the bytes in responseStream and copy them to content.
                    await responseStream.CopyToAsync(content);

                    // The previous statement abbreviates the following two statements.

                    // CopyToAsync returns a Task, not a Task<T>.
                    //Task copyTask = responseStream.CopyToAsync(content);

                    // When copyTask is completed, content contains a copy of
                    // responseStream.
                    //await copyTask;
                }
            }
            // Return the result as a byte array.
            return content.ToArray();
        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each website. The string format
            // is designed to be used with a monospaced font, such as
            // Lucida Console or Global Monospace.
            var bytes = content.Length;
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

<span data-ttu-id="b6ae3-260">Aşağıdaki kod, yöntemini kullanan çözümün tam örneğini içerir `HttpClient` `GetByteArrayAsync` .</span><span class="sxs-lookup"><span data-stu-id="b6ae3-260">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>

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
using System.IO;
using System.Net;

namespace AsyncExampleWPF
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            resultsTextBox.Clear();

            // Disable the button until the operation is complete.
            startButton.IsEnabled = false;

            // One-step async call.
            await SumPageSizesAsync();

            //// Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";

            // Reenable the button in case you want to run the operation again.
            startButton.IsEnabled = true;
        }

        private async Task SumPageSizesAsync()
        {
            // Declare an HttpClient object and increase the buffer size. The
            // default buffer size is 65,536.
            HttpClient client =
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            var total = 0;

            foreach (var url in urlList)
            {
                // GetByteArrayAsync returns a task. At completion, the task
                // produces a byte array.
                byte[] urlContents = await client.GetByteArrayAsync(url);

                // The following two lines can replace the previous assignment statement.
                //Task<byte[]> getContentsTask = client.GetByteArrayAsync(url);
                //byte[] urlContents = await getContentsTask;

                DisplayResults(url, urlContents);

                // Update the total.
                total += urlContents.Length;
            }

            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
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
            };
            return urls;
        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each website. The string format
            // is designed to be used with a monospaced font, such as
            // Lucida Console or Global Monospace.
            var bytes = content.Length;
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="b6ae3-261">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6ae3-261">See also</span></span>

- <span data-ttu-id="b6ae3-262">[Zaman uyumsuz örnek: Web 'e yönelik Izlenecek yol (C# ve Visual Basic)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hh300224(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="b6ae3-262">[Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hh300224(v=vs.110))</span></span>
- [<span data-ttu-id="b6ae3-263">async</span><span class="sxs-lookup"><span data-stu-id="b6ae3-263">async</span></span>](../../../language-reference/keywords/async.md)
- [<span data-ttu-id="b6ae3-264">await</span><span class="sxs-lookup"><span data-stu-id="b6ae3-264">await</span></span>](../../../language-reference/operators/await.md)
- [<span data-ttu-id="b6ae3-265">Async ve await ile zaman uyumsuz programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="b6ae3-265">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="b6ae3-266">Zaman uyumsuz dönüş türleri (C#)</span><span class="sxs-lookup"><span data-stu-id="b6ae3-266">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="b6ae3-267">Görev tabanlı zaman uyumsuz programlama (TAP)</span><span class="sxs-lookup"><span data-stu-id="b6ae3-267">Task-based Asynchronous Programming (TAP)</span></span>](https://www.microsoft.com/download/details.aspx?id=19957)
- [<span data-ttu-id="b6ae3-268">Task. WhenAll kullanarak zaman uyumsuz izlenecek yolu genişletme (C#)</span><span class="sxs-lookup"><span data-stu-id="b6ae3-268">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [<span data-ttu-id="b6ae3-269">Async ve await kullanarak birden çok web isteğini paralel hale getirme (C#)</span><span class="sxs-lookup"><span data-stu-id="b6ae3-269">How to make multiple web requests in parallel by using async and await (C#)</span></span>](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
