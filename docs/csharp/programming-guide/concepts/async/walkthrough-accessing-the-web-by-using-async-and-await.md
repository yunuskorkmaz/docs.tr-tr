---
title: "Walkthrough: Async kullanarak Web'e erişim ve bekleme (C#)"
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: 42b09dab26fd514e184163eaf41aff117d3a463f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74281792"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a><span data-ttu-id="8d32a-102">Walkthrough: Async kullanarak Web'e erişim ve bekleme (C#)</span><span class="sxs-lookup"><span data-stu-id="8d32a-102">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>

<span data-ttu-id="8d32a-103">Async/await özelliklerini kullanarak daha kolay ve sezgisel bir şekilde asynchronous programları yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d32a-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="8d32a-104">Senkron koda benzeyen bir senkron kod yazabilir ve derleyicinin asynchronous kodunun genellikle gerektirdiği zor geri arama işlevlerini ve devamlarını işlemesine izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d32a-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>

<span data-ttu-id="8d32a-105">Async özelliği hakkında daha fazla bilgi [için, async ile Asynchronous Programming'e bakın ve (C#) bekleyin.](./index.md)</span><span class="sxs-lookup"><span data-stu-id="8d32a-105">For more information about the Async feature, see [Asynchronous Programming with async and await (C#)](./index.md).</span></span>

<span data-ttu-id="8d32a-106">Bu gözden geçirme, web siteleri listesindeki bayt sayısını özetleyen eşzamanlı bir Windows Presentation Foundation (WPF) uygulamasıyla başlar.</span><span class="sxs-lookup"><span data-stu-id="8d32a-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="8d32a-107">İzthrough daha sonra yeni özellikleri kullanarak uygulamayı asynchronous çözüme dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="8d32a-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>

<span data-ttu-id="8d32a-108">Uygulamaları kendiniz oluşturmak istemiyorsanız, [Async Örnek: Web Walkthrough (C# ve Visual Basic) erişim](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d32a-108">If you don't want to build the applications yourself, you can download [Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

> [!NOTE]
> <span data-ttu-id="8d32a-109">Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınıza yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-109">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="create-a-wpf-application"></a><span data-ttu-id="8d32a-110">WPF uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="8d32a-110">Create a WPF application</span></span>

1. <span data-ttu-id="8d32a-111">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8d32a-111">Start Visual Studio.</span></span>

2. <span data-ttu-id="8d32a-112">Menü çubuğunda**Yeni** > **Proje** **yi seçin.** > </span><span class="sxs-lookup"><span data-stu-id="8d32a-112">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="8d32a-113">**Yeni Proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="8d32a-113">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="8d32a-114">Yüklü **Şablonlar** bölmesinde Visual C#'ı seçin ve ardından proje türleri listesinden **WPF Uygulamasını** seçin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-114">In the **Installed Templates** pane, choose Visual C#, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="8d32a-115">**Ad** metin kutusuna `AsyncExampleWPF`girin ve **ardından Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-115">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>

     <span data-ttu-id="8d32a-116">Yeni proje Çözüm **Gezgini'nde**görünür.</span><span class="sxs-lookup"><span data-stu-id="8d32a-116">The new project appears in **Solution Explorer**.</span></span>

## <a name="design-a-simple-wpf-mainwindow"></a><span data-ttu-id="8d32a-117">Basit bir WPF MainWindow tasarla</span><span class="sxs-lookup"><span data-stu-id="8d32a-117">Design a simple WPF MainWindow</span></span>

1. <span data-ttu-id="8d32a-118">Visual Studio Code Editor'da **MainWindow.xaml** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-118">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

2. <span data-ttu-id="8d32a-119">Araç **Kutusu** penceresi görünmüyorsa, **Görünüm** menüsünü açın ve ardından **Araç Kutusu'nu**seçin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-119">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>

3. <span data-ttu-id="8d32a-120">**MainWindow** penceresine **düğme** denetimi ve **TextBox** denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-120">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>

4. <span data-ttu-id="8d32a-121">**TextBox** denetimini vurgulayın ve **Özellikler** penceresinde aşağıdaki değerleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="8d32a-121">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="8d32a-122">**Ad** özelliğini `resultsTextBox`' ' ye ayarlama</span><span class="sxs-lookup"><span data-stu-id="8d32a-122">Set the **Name** property to `resultsTextBox`.</span></span>

    - <span data-ttu-id="8d32a-123">**Yükseklik** özelliğini 250 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8d32a-123">Set the **Height** property to 250.</span></span>

    - <span data-ttu-id="8d32a-124">**Genişlik** özelliğini 500 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8d32a-124">Set the **Width** property to 500.</span></span>

    - <span data-ttu-id="8d32a-125">**Metin** sekmesinde, Lucida Console veya Global Monospace gibi tek boşluklu bir yazı tipi belirtin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-125">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>

5. <span data-ttu-id="8d32a-126">**Düğme** denetimini vurgulayın ve **Özellikler** penceresinde aşağıdaki değerleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="8d32a-126">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="8d32a-127">**Ad** özelliğini `startButton`' ' ye ayarlama</span><span class="sxs-lookup"><span data-stu-id="8d32a-127">Set the **Name** property to `startButton`.</span></span>

    - <span data-ttu-id="8d32a-128">**İçerik** özelliğinin değerini **Düğme'den** **Başlangıç**ekranına değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-128">Change the value of the **Content** property from **Button** to **Start**.</span></span>

6. <span data-ttu-id="8d32a-129">Metin kutusunu ve düğmeyi, her ikisi de **Ana Pencere** penceresinde görünecek şekilde konumlandırın.</span><span class="sxs-lookup"><span data-stu-id="8d32a-129">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>

     <span data-ttu-id="8d32a-130">WPF XAML Tasarımcısı hakkında daha fazla bilgi için Bkz. [XAML Designer kullanarak bir kullanıcı arabirimi oluşturma.](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio)</span><span class="sxs-lookup"><span data-stu-id="8d32a-130">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>

## <a name="add-a-reference"></a><span data-ttu-id="8d32a-131">Referans ekleme</span><span class="sxs-lookup"><span data-stu-id="8d32a-131">Add a reference</span></span>

1. <span data-ttu-id="8d32a-132">**Çözüm Gezgini'nde**projenizin adını vurgulayın.</span><span class="sxs-lookup"><span data-stu-id="8d32a-132">In **Solution Explorer**, highlight your project's name.</span></span>

2. <span data-ttu-id="8d32a-133">Menü çubuğunda, **Project** > **Add Reference'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-133">On the menu bar, choose **Project** > **Add Reference**.</span></span>

     <span data-ttu-id="8d32a-134">**Başvuru Yöneticisi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-134">The **Reference Manager** dialog box appears.</span></span>

3. <span data-ttu-id="8d32a-135">İletişim kutusunun üst kısmında, projenizin .NET Framework 4.5 veya daha yüksek hedeflediğini doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="8d32a-135">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>

4. <span data-ttu-id="8d32a-136">**Derlemeler** kategorisinde, henüz seçilmemişse **Çerçeve'yi** seçin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-136">In the **Assemblies** category, choose **Framework** if it isn’t already chosen.</span></span>

5. <span data-ttu-id="8d32a-137">Adlar listesinde **System.Net.Http** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-137">In the list of names, select the **System.Net.Http** check box.</span></span>

6. <span data-ttu-id="8d32a-138">İletişim kutusunu kapatmak için **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-138">Choose the **OK** button to close the dialog box.</span></span>

## <a name="add-necessary-using-directives"></a><span data-ttu-id="8d32a-139">Yönergeleri kullanarak gerekli ekleme</span><span class="sxs-lookup"><span data-stu-id="8d32a-139">Add necessary using directives</span></span>

1. <span data-ttu-id="8d32a-140">**Çözüm Gezgini'nde,** MainWindow.xaml.cs için kısayol menüsünü açın ve ardından **Kodu Görüntüle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-140">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

2. <span data-ttu-id="8d32a-141">Zaten mevcut `using` değillerse kod dosyasının en üstüne aşağıdaki yönergeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-141">Add the following `using` directives at the top of the code file if they’re not already present.</span></span>

    ```csharp
    using System.Net.Http;
    using System.Net;
    using System.IO;
    ```

## <a name="create-a-synchronous-app"></a><span data-ttu-id="8d32a-142">Eşzamanlı bir uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="8d32a-142">Create a synchronous app</span></span>

1. <span data-ttu-id="8d32a-143">Tasarım penceresinde, MainWindow.xaml, MainWindow.xaml.cs olay **Start** işleyicisi `startButton_Click` oluşturmak için Başlat düğmesini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="8d32a-143">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>

2. <span data-ttu-id="8d32a-144">MainWindow.xaml.cs, aşağıdaki kodu gövdeye `startButton_Click`kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="8d32a-144">In MainWindow.xaml.cs, copy the following code into the body of `startButton_Click`:</span></span>

    ```csharp
    resultsTextBox.Clear();
    SumPageSizes();
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";
    ```

    <span data-ttu-id="8d32a-145">Kod, `SumPageSizes`uygulamayı yönlendiren yöntemi çağırır ve denetim `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="8d32a-145">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>

3. <span data-ttu-id="8d32a-146">Senkron çözümün kodu aşağıdaki dört yöntemi içerir:</span><span class="sxs-lookup"><span data-stu-id="8d32a-146">The code for the synchronous solution contains the following four methods:</span></span>

    - <span data-ttu-id="8d32a-147">`SumPageSizes`, web sayfası URL'lerinin bir `SetUpURLList` listesini alır `GetURLContents` `DisplayResults` ve daha sonra aramaları ve her URL işlemek için.</span><span class="sxs-lookup"><span data-stu-id="8d32a-147">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>

    - <span data-ttu-id="8d32a-148">`SetUpURLList`, web adreslerinin listesini yapar ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="8d32a-148">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>

    - <span data-ttu-id="8d32a-149">`GetURLContents`, her web sitesinin içeriğini indirir ve bir bayt dizisi olarak içeriğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8d32a-149">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>

    - <span data-ttu-id="8d32a-150">`DisplayResults`, her URL için bayt dizisindebayt sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8d32a-150">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>

    <span data-ttu-id="8d32a-151">Aşağıdaki dört yöntemi kopyalayın ve MainWindow.xaml.cs `startButton_Click` olay işleyicisinin altına yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="8d32a-151">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.cs:</span></span>

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

## <a name="test-the-synchronous-solution"></a><span data-ttu-id="8d32a-152">Senkron çözümü test edin</span><span class="sxs-lookup"><span data-stu-id="8d32a-152">Test the synchronous solution</span></span>

<span data-ttu-id="8d32a-153">Programı çalıştırmak için **F5** tuşunu seçin ve ardından **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-153">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

<span data-ttu-id="8d32a-154">Aşağıdaki listeye benzeyen çıktı görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="8d32a-154">Output that resembles the following list should appear:</span></span>

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

<span data-ttu-id="8d32a-155">Sayımların görüntülenmesinin birkaç saniye sürdüğünü unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8d32a-155">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="8d32a-156">Bu süre zarfında, istenen kaynakların karşıdan yüklenmesini beklerken UI iş parçacığı engellenir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-156">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="8d32a-157">Sonuç olarak, **Başlat** düğmesini seçtikten sonra ekran penceresini taşıyamaz, en üst düzeye çıkaramaz, simge durumuna indiremez ve hatta kapatamazsınız.</span><span class="sxs-lookup"><span data-stu-id="8d32a-157">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="8d32a-158">Bu çabalar, bayt sayıları görünmeye başlayana kadar başarısız dır.</span><span class="sxs-lookup"><span data-stu-id="8d32a-158">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="8d32a-159">Bir web sitesi yanıt vermiyorsa, hangi sitenin başarısız olduğuna dair bir belirti yoktur.</span><span class="sxs-lookup"><span data-stu-id="8d32a-159">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="8d32a-160">Beklemeyi bırakıp programı kapatmak bile zordur.</span><span class="sxs-lookup"><span data-stu-id="8d32a-160">It is difficult even to stop waiting and close the program.</span></span>

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a><span data-ttu-id="8d32a-161">GetURLContents'i eşzamanlı bir yönteme dönüştürme</span><span class="sxs-lookup"><span data-stu-id="8d32a-161">Convert GetURLContents to an asynchronous method</span></span>

1. <span data-ttu-id="8d32a-162">Senkron çözümü bir asynchronous çözüme dönüştürmek için, başlbaşlamak için en <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebRequest.GetResponse%2A> iyi yer, <xref:System.IO.Stream.CopyTo%2A> `GetURLContents` çünkü yönteme ve <xref:System.IO.Stream> yönteme yapılan çağrılar uygulamanın web'e eriştiği yerdir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-162">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="8d32a-163">.NET Framework, her iki yöntemin eşzamanlı sürümlerini sağlayarak dönüşümü kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="8d32a-163">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>

     <span data-ttu-id="8d32a-164">Kullanılan `GetURLContents`yöntemler hakkında daha fazla bilgi <xref:System.Net.WebRequest>için bkz.</span><span class="sxs-lookup"><span data-stu-id="8d32a-164">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8d32a-165">Bu izbindeki adımları izlediğiniz de, birkaç derleyici hatası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-165">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="8d32a-166">Bunları yok sayabilir ve izliğe devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d32a-166">You can ignore them and continue with the walkthrough.</span></span>

     <span data-ttu-id="8d32a-167">Üçüncü satırda `GetURLContents` çağrılan yöntemi asynchronous, görev tabanlı `GetResponse` <xref:System.Net.WebRequest.GetResponseAsync%2A> yönteme değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-167">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>

    ```csharp
    using (WebResponse response = webReq.GetResponseAsync())
    ```

2. <span data-ttu-id="8d32a-168">`GetResponseAsync`bir <xref:System.Threading.Tasks.Task%601>' yi döndürür.</span><span class="sxs-lookup"><span data-stu-id="8d32a-168">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="8d32a-169">Bu durumda, *görev iade değişkeni*, , `TResult`türü <xref:System.Net.WebResponse>vardır.</span><span class="sxs-lookup"><span data-stu-id="8d32a-169">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="8d32a-170">Görev, istenen veriler karşıdan `WebResponse` yüklendikten ve görev tamamlanmak üzere çalıştırıldıktan sonra gerçek bir nesne oluşturma sözüdür.</span><span class="sxs-lookup"><span data-stu-id="8d32a-170">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>

     <span data-ttu-id="8d32a-171">Görevden `WebResponse` değeri almak için, `GetResponseAsync`aşağıdaki kodun gösterdiği gibi çağrıya bir [bekleyen](../../../language-reference/operators/await.md) işleci uygulayın.</span><span class="sxs-lookup"><span data-stu-id="8d32a-171">To retrieve the `WebResponse` value from the task, apply an [await](../../../language-reference/operators/await.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>

    ```csharp
    using (WebResponse response = await webReq.GetResponseAsync())
    ```

     <span data-ttu-id="8d32a-172">İşleç, `await` `GetURLContents`beklenen görev tamamlanana kadar geçerli yöntemin yürütülmesini askıya adatır.</span><span class="sxs-lookup"><span data-stu-id="8d32a-172">The `await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="8d32a-173">Bu arada, denetim geçerli yöntemin arayan döndürür.</span><span class="sxs-lookup"><span data-stu-id="8d32a-173">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="8d32a-174">Bu örnekte, geçerli `GetURLContents`yöntem ve arayan `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="8d32a-174">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="8d32a-175">Görev tamamlandığında, vaat edilen `WebResponse` nesne beklenen görevin değeri olarak üretilir ve `response`değişkene atanır.</span><span class="sxs-lookup"><span data-stu-id="8d32a-175">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>

     <span data-ttu-id="8d32a-176">Önceki deyim, ne olduğunu açıklığa kavuşturmak için aşağıdaki iki ifadeye ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-176">The previous statement can be separated into the following two statements to clarify what happens.</span></span>

    ```csharp
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();
    //using (WebResponse response = await responseTask)
    ```

     <span data-ttu-id="8d32a-177">Arama bir `webReq.GetResponseAsync` `Task(Of WebResponse)` veya `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="8d32a-177">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="8d32a-178">Daha sonra `WebResponse` değeri almak için göreve bir bekleme işleci uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8d32a-178">Then an await operator is applied to the task to retrieve the `WebResponse` value.</span></span>

     <span data-ttu-id="8d32a-179">Async yönteminizin görevi tamamlamasına bağlı olmayan bir çalışması varsa, yöntem bu iki deyim arasında, async yöntemine yapılan çağrıdan `await` sonra ve işleç uygulanmadan önce bu çalışmaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-179">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the `await` operator is applied.</span></span> <span data-ttu-id="8d32a-180">Örneğin, [async ve await (C#) kullanarak paralel olarak birden çok web isteği nasıl yapılır](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) ve [Task.WhenAll (C#) kullanarak async walkthrough genişletmek için nasıl](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8d32a-180">For examples, see [How to make multiple web requests in parallel by using async and await (C#)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

3. <span data-ttu-id="8d32a-181">Önceki adımda `await` işleci eklediğiniz için derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="8d32a-181">Because you added the `await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="8d32a-182">İşleç yalnızca [async](../../../language-reference/keywords/async.md) değiştirici ile işaretlenmiş yöntemlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-182">The operator can be used only in methods that are marked with the [async](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="8d32a-183">Çağrıyı bir çağrıyla değiştirmek için `CopyTo` dönüşüm adımlarını yinelerken hatayı `CopyToAsync`yoksay.</span><span class="sxs-lookup"><span data-stu-id="8d32a-183">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>

    - <span data-ttu-id="8d32a-184">'ye çağrılan yöntemin adını <xref:System.IO.Stream.CopyToAsync%2A>değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-184">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>

    - <span data-ttu-id="8d32a-185">Veya `CopyTo` `CopyToAsync` yöntem bağımsız değişkenine `content`bayt kopyalar ve anlamlı bir değer döndürmez.</span><span class="sxs-lookup"><span data-stu-id="8d32a-185">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="8d32a-186">Senkron sürümde, çağrı bir `CopyTo` değer döndürmeyen basit bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-186">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="8d32a-187">Asynchronous sürümü, `CopyToAsync`bir <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="8d32a-187">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="8d32a-188">Görev "Görev(void)" gibi işlevgörür ve yöntemin beklenen olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d32a-188">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="8d32a-189">Aşağıdaki `Await` `await` kodun gösterdiği `CopyToAsync`gibi, çağrıya uygulayın veya çağrıya uygulayın.</span><span class="sxs-lookup"><span data-stu-id="8d32a-189">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>

        ```csharp
        await responseStream.CopyToAsync(content);
        ```

         <span data-ttu-id="8d32a-190">Önceki deyim, aşağıdaki iki kod satırını kısaltır.</span><span class="sxs-lookup"><span data-stu-id="8d32a-190">The previous statement abbreviates the following two lines of code.</span></span>

        ```csharp
        // CopyToAsync returns a Task, not a Task<T>.
        //Task copyTask = responseStream.CopyToAsync(content);

        // When copyTask is completed, content contains a copy of
        // responseStream.
        //await copyTask;
        ```

4. <span data-ttu-id="8d32a-191">Yapılması gereken tek `GetURLContents` şey yöntem imzasını ayarlamaktır.</span><span class="sxs-lookup"><span data-stu-id="8d32a-191">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="8d32a-192">İşleç'i `await` yalnızca [async](../../../language-reference/keywords/async.md) değiştirici ile işaretlenmiş yöntemlerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d32a-192">You can use the `await` operator only in methods that are marked with the [async](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="8d32a-193">Aşağıdaki kodun gösterdiği gibi, yöntemi *bir async yöntemi*olarak işaretlemek için değiştirici ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-193">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>

    ```csharp
    private async byte[] GetURLContents(string url)
    ```

5. <span data-ttu-id="8d32a-194">Bir async yönteminin dönüş türü <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>yalnızca `void` , veya C# olabilir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-194">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or `void` in C#.</span></span> <span data-ttu-id="8d32a-195">Genellikle, bir dönüş `void` türü yalnızca gerekli olduğu bir `void` async olay işleyicisi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8d32a-195">Typically, a return type of `void` is used only in an async event handler, where `void` is required.</span></span> <span data-ttu-id="8d32a-196">Diğer durumlarda, tamamlanan `Task(T)` yöntemde T türü bir değer döndüren bir [iade](../../../language-reference/keywords/return.md) deyimi varsa ve tamamlanan yöntem anlamlı bir değer döndürmüyorsa kullanırsınız. `Task`</span><span class="sxs-lookup"><span data-stu-id="8d32a-196">In other cases, you use `Task(T)` if the completed method has a [return](../../../language-reference/keywords/return.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span> <span data-ttu-id="8d32a-197">`Task` İade türünü "Görev(boşluk)" anlamında düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d32a-197">You can think of the `Task` return type as meaning "Task(void)."</span></span>

     <span data-ttu-id="8d32a-198">Daha fazla bilgi için [Bkz. Async İade Türleri (C#)](./async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="8d32a-198">For more information, see [Async Return Types (C#)](./async-return-types.md).</span></span>

     <span data-ttu-id="8d32a-199">Yöntemin `GetURLContents` bir iade deyimi vardır ve deyim bir bayt dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8d32a-199">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="8d32a-200">Bu nedenle, async sürümünün dönüş türü, T'nin bir bayt dizisi olduğu Görev(T) türüdür.</span><span class="sxs-lookup"><span data-stu-id="8d32a-200">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="8d32a-201">Yöntem imzasında aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="8d32a-201">Make the following changes in the method signature:</span></span>

    - <span data-ttu-id="8d32a-202">İade türünü `Task<byte[]>`' le değiştirin</span><span class="sxs-lookup"><span data-stu-id="8d32a-202">Change the return type to `Task<byte[]>`.</span></span>

    - <span data-ttu-id="8d32a-203">Kural olarak, eşişme yöntemleri "Async" ile biten adlar `GetURLContentsAsync`vardır, bu nedenle yöntemi yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="8d32a-203">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>

     <span data-ttu-id="8d32a-204">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-204">The following code shows these changes.</span></span>

    ```csharp
    private async Task<byte[]> GetURLContentsAsync(string url)
    ```

     <span data-ttu-id="8d32a-205">Bu birkaç değişiklikle, `GetURLContents` eşzamanlı bir yönteme dönüştürme tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="8d32a-205">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a><span data-ttu-id="8d32a-206">SumPageSizes'ı eşzamanlı bir yönteme dönüştürme</span><span class="sxs-lookup"><span data-stu-id="8d32a-206">Convert SumPageSizes to an asynchronous method</span></span>

1. <span data-ttu-id="8d32a-207">Önceki `SumPageSizes`yordamdan gelen adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-207">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="8d32a-208">İlk olarak, aramayı `GetURLContents` eşzamanlı çağrıya çevirin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-208">First, change the call to `GetURLContents` to an asynchronous call.</span></span>

    - <span data-ttu-id="8d32a-209">Daha önce `GetURLContents` `GetURLContentsAsync`yapmadıysanız, "bu yöntemden" olarak çağrılan yöntemin adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-209">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>

    - <span data-ttu-id="8d32a-210">Bayt dizi `GetURLContentsAsync` değerini elde etmek için dönen göreve uygulayın. `await`</span><span class="sxs-lookup"><span data-stu-id="8d32a-210">Apply `await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>

     <span data-ttu-id="8d32a-211">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-211">The following code shows these changes.</span></span>

    ```csharp
    byte[] urlContents = await GetURLContentsAsync(url);
    ```

     <span data-ttu-id="8d32a-212">Önceki atama, aşağıdaki iki kod satırını kısaltır.</span><span class="sxs-lookup"><span data-stu-id="8d32a-212">The previous assignment abbreviates the following two lines of code.</span></span>

    ```csharp
    // GetURLContentsAsync returns a Task<T>. At completion, the task
    // produces a byte array.
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //byte[] urlContents = await getContentsTask;
    ```

2. <span data-ttu-id="8d32a-213">Yöntemin imzasında aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="8d32a-213">Make the following changes in the method's signature:</span></span>

    - <span data-ttu-id="8d32a-214">Yöntemi `async` değiştirici ile işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-214">Mark the method with the `async` modifier.</span></span>

    - <span data-ttu-id="8d32a-215">Yöntem adına "Async" ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-215">Add "Async" to the method name.</span></span>

    - <span data-ttu-id="8d32a-216">T. için bir değer `SumPageSizesAsync` döndürmediği için bu sefer görev iade değişkeni yoktur, T, bu sefer (Yöntemin deyimi yoktur.) `return` Ancak, yöntem beklenilebilir bir dönmek `Task` gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-216">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="8d32a-217">Bu nedenle, yöntemin dönüş `void` türünü `Task`' den ' e değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-217">Therefore, change the return type of the method from `void` to `Task`.</span></span>

    <span data-ttu-id="8d32a-218">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-218">The following code shows these changes.</span></span>

    ```csharp
    private async Task SumPageSizesAsync()
    ```

     <span data-ttu-id="8d32a-219">`SumPageSizes` Dönüştürme `SumPageSizesAsync` tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="8d32a-219">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a><span data-ttu-id="8d32a-220">startButton_Click bir eşzamanlı yönteme dönüştürme</span><span class="sxs-lookup"><span data-stu-id="8d32a-220">Convert startButton_Click to an asynchronous method</span></span>

1. <span data-ttu-id="8d32a-221">Olay işleyicisinde, çağrılan yöntemin `SumPageSizes` adını `SumPageSizesAsync`, henüz yapmadıysanız değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-221">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>

2. <span data-ttu-id="8d32a-222">Bir `SumPageSizesAsync` async yöntemi olduğundan, sonucu beklemek için olay işleyicisi kodu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-222">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>

     <span data-ttu-id="8d32a-223">Çağrıyı `SumPageSizesAsync` yansıtmak için `CopyToAsync` `GetURLContentsAsync`çağrı.</span><span class="sxs-lookup"><span data-stu-id="8d32a-223">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="8d32a-224">Arama bir `Task`döndürür, bir `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="8d32a-224">The call returns a `Task`, not a `Task(T)`.</span></span>

     <span data-ttu-id="8d32a-225">Önceki yordamlarda olduğu gibi, bir veya iki deyim kullanarak aramayı dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d32a-225">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="8d32a-226">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-226">The following code shows these changes.</span></span>

    ```csharp
    // One-step async call.
    await SumPageSizesAsync();

    // Two-step async call.
    //Task sumTask = SumPageSizesAsync();
    //await sumTask;
    ```

3. <span data-ttu-id="8d32a-227">İşleme yanlışlıkla yeniden girmesini önlemek için **Başlat** düğmesini `startButton_Click` devre dışı katmak için en üstteki ifadeyi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-227">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>

    ```csharp
    // Disable the button until the operation is complete.
    startButton.IsEnabled = false;
    ```

     <span data-ttu-id="8d32a-228">Olay işleyicisinin sonundaki düğmeyi yeniden etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d32a-228">You can reenable the button at the end of the event handler.</span></span>

    ```csharp
    // Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = true;
    ```

     <span data-ttu-id="8d32a-229">Reentrancy hakkında daha fazla bilgi için, [Async Apps (C#) içinde Reentrancy Işleme](./handling-reentrancy-in-async-apps.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8d32a-229">For more information about reentrancy, see [Handling Reentrancy in Async Apps (C#)](./handling-reentrancy-in-async-apps.md).</span></span>

4. <span data-ttu-id="8d32a-230">Son olarak, `async` olay işleyicisi bekliyor `SumPagSizesAsync`böylece bildirime değiştirici ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-230">Finally, add the `async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>

    ```csharp
    private async void startButton_Click(object sender, RoutedEventArgs e)
    ```

     <span data-ttu-id="8d32a-231">Genellikle, olay işleyicilerinin adları değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="8d32a-231">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="8d32a-232">Olay işleyicileri döndürmesi `Task` `void`gerektiğinden, iade türü değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="8d32a-232">The return type isn’t changed to `Task` because event handlers must return `void`.</span></span>

     <span data-ttu-id="8d32a-233">Projenin senkron işlemden asynchronous işleme ye dönüştürülmesi tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="8d32a-233">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>

## <a name="test-the-asynchronous-solution"></a><span data-ttu-id="8d32a-234">Asynchronous çözeltisini test edin</span><span class="sxs-lookup"><span data-stu-id="8d32a-234">Test the asynchronous solution</span></span>

1. <span data-ttu-id="8d32a-235">Programı çalıştırmak için **F5** tuşunu seçin ve ardından **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-235">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

2. <span data-ttu-id="8d32a-236">Senkron çözeltinin çıktısını andıran çıktı görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-236">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="8d32a-237">Ancak, aşağıdaki farklılıklara dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-237">However, notice the following differences.</span></span>

    - <span data-ttu-id="8d32a-238">İşlem tamamlandıktan sonra tüm sonuçlar aynı anda oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="8d32a-238">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="8d32a-239">Örneğin, her iki program `startButton_Click` da metin kutusunu temizleyen bir satır içerir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-239">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="8d32a-240">Amaç, bir sonuç kümesi ortaya çıktıktan sonra ikinci kez **Başlat** düğmesini seçerseniz, çalıştırmalar arasındaki metin kutusunu temizlemektir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-240">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="8d32a-241">Senkron sürümde, metin kutusu, karşıdan yüklemeler tamamlandığında ve Kullanıcı Arabirimi iş parçacığı başka işler yapmakta özgür olduğunda, sayımlar ikinci kez görünmeden hemen önce temizlenir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-241">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="8d32a-242">Eşzamanlı sürümde, **başlat** düğmesini seçtikten hemen sonra metin kutusu temizlenir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-242">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>

    - <span data-ttu-id="8d32a-243">En önemlisi, UI iş parçacığı indirme sırasında engellenmez.</span><span class="sxs-lookup"><span data-stu-id="8d32a-243">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="8d32a-244">Web kaynakları karşıdan yüklenirken, sayılırken ve görüntülenirken pencereyi taşıyabilir veya yeniden boyutlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d32a-244">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="8d32a-245">Web sitelerinden biri yavaşsa veya yanıt vermiyorsa, **Kapat** düğmesini (sağ üst köşedeki kırmızı alandaki x) seçerek işlemi iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d32a-245">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>

## <a name="replace-method-geturlcontentsasync-with-a-net-framework-method"></a><span data-ttu-id="8d32a-246">GetURLContentsAsync yöntemini bir .NET Framework yöntemiyle değiştirin</span><span class="sxs-lookup"><span data-stu-id="8d32a-246">Replace method GetURLContentsAsync with a .NET Framework method</span></span>

1. <span data-ttu-id="8d32a-247">.NET Framework 4.5, kullanabileceğiniz birçok async yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d32a-247">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="8d32a-248">Bunlardan biri, <xref:System.Net.Http.HttpClient> yöntem <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, bu walkthrough için gereken sadece ne yapar.</span><span class="sxs-lookup"><span data-stu-id="8d32a-248">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="8d32a-249">Daha önceki bir yordamda oluşturduğunuz `GetURLContentsAsync` yöntem yerine kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d32a-249">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>

     <span data-ttu-id="8d32a-250">İlk adım yöntemde `HttpClient` `SumPageSizesAsync`bir nesne oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="8d32a-250">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="8d32a-251">Yöntemin başında aşağıdaki bildirimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-251">Add the following declaration at the start of the method.</span></span>

    ```csharp
    // Declare an HttpClient object and increase the buffer size. The
    // default buffer size is 65,536.
    HttpClient client =
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };
    ```

2. <span data-ttu-id="8d32a-252">Yönteme `SumPageSizesAsync,` `GetURLContentsAsync` yapılan çağrıyı `HttpClient` yönteme yapılan bir çağrıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-252">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>

    ```csharp
    byte[] urlContents = await client.GetByteArrayAsync(url);
    ```

3. <span data-ttu-id="8d32a-253">Yazdığınız `GetURLContentsAsync` yöntemi kaldırın veya yorum yapın.</span><span class="sxs-lookup"><span data-stu-id="8d32a-253">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>

4. <span data-ttu-id="8d32a-254">Programı çalıştırmak için **F5** tuşunu seçin ve ardından **Başlat** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-254">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="8d32a-255">Projenin bu sürümünün davranışı, "Asynchronous çözümünü sınamak için" yordamının açıkladığı davranışla eşleşmelidir, ancak sizden daha az çaba göstermelidir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-255">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>

## <a name="example-code"></a><span data-ttu-id="8d32a-256">Örnek kod</span><span class="sxs-lookup"><span data-stu-id="8d32a-256">Example code</span></span>

<span data-ttu-id="8d32a-257">Aşağıdaki kod, yazdığınız eşzamanlı `GetURLContentsAsync` yöntemi kullanarak eşzamanlı bir çözümden eşzamanlı bir çözüme dönüştürmenin tam örneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-257">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="8d32a-258">Orijinal, eşzamanlı çözüme güçlü bir şekilde benzediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="8d32a-258">Notice that it strongly resembles the original, synchronous solution.</span></span>

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

<span data-ttu-id="8d32a-259">Aşağıdaki kod, `GetByteArrayAsync`yöntemi kullanan çözümün tam `HttpClient` örneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="8d32a-259">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8d32a-260">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d32a-260">See also</span></span>

- <span data-ttu-id="8d32a-261">[Async Örnek: Web Walkthrough (C # ve Visual Basic) erişim](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hh300224(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="8d32a-261">[Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hh300224(v=vs.110))</span></span>
- [<span data-ttu-id="8d32a-262">async</span><span class="sxs-lookup"><span data-stu-id="8d32a-262">async</span></span>](../../../language-reference/keywords/async.md)
- [<span data-ttu-id="8d32a-263">await</span><span class="sxs-lookup"><span data-stu-id="8d32a-263">await</span></span>](../../../language-reference/operators/await.md)
- [<span data-ttu-id="8d32a-264">Async ve await ile Asynchronous Programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="8d32a-264">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="8d32a-265">Async İade Türleri (C#)</span><span class="sxs-lookup"><span data-stu-id="8d32a-265">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="8d32a-266">Görev Tabanlı Eşzamanlı Programlama (TAP)</span><span class="sxs-lookup"><span data-stu-id="8d32a-266">Task-based Asynchronous Programming (TAP)</span></span>](https://www.microsoft.com/download/details.aspx?id=19957)
- [<span data-ttu-id="8d32a-267">Task.WhenAll (C#) kullanarak async walkthrough nasıl genişletilir</span><span class="sxs-lookup"><span data-stu-id="8d32a-267">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [<span data-ttu-id="8d32a-268">Async ve await (C#) kullanarak paralel olarak birden fazla web istekleri yapmak için nasıl</span><span class="sxs-lookup"><span data-stu-id="8d32a-268">How to make multiple web requests in parallel by using async and await (C#)</span></span>](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
