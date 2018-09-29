---
title: "İzlenecek yol: async kullanarak Web'e erişme ve await (C#)"
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: 24ce1e405019ef83ff6bcbb61552d6fc5d911935
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47455755"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a><span data-ttu-id="02440-102">İzlenecek yol: async kullanarak Web'e erişme ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="02440-102">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>

<span data-ttu-id="02440-103">Async ve await özelliklerini kullanarak zaman uyumsuz programları daha kolay ve sezgisel bir şekilde yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02440-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="02440-104">Zaman uyumlu kod gibi görünen zaman uyumsuz kod yazabilir ve zor geri çağırma işlevleri ve zaman uyumsuz kod genellikle kapsar devamlılıklar derleyici olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="02440-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>

<span data-ttu-id="02440-105">Async özelliği hakkında daha fazla bilgi için bkz. [Asynchronous Programming with async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="02440-105">For more information about the Async feature, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="02440-106">Bu izlenecek yol, Web sitelerinin bir listesiyle bayt sayısını toplar. zaman uyumlu bir Windows Presentation Foundation (WPF) uygulaması ile başlar.</span><span class="sxs-lookup"><span data-stu-id="02440-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="02440-107">İzlenecek yol, yeni özellikleri kullanarak zaman uyumsuz bir çözümü uygulamaya ardından dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="02440-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>

<span data-ttu-id="02440-108">Uygulamaları kendiniz yapılandırmak istemiyorsanız, indirebileceğiniz [zaman uyumsuz örneği: izlenecek yol (C# ve Visual Basic) erişme](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="02440-108">If you don't want to build the applications yourself, you can download [Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

> [!NOTE]
> <span data-ttu-id="02440-109">Yeni bilgisayarınızda yüklü veya örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="02440-109">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="create-a-wpf-application"></a><span data-ttu-id="02440-110">WPF uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="02440-110">Create a WPF application</span></span>

1.  <span data-ttu-id="02440-111">Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="02440-111">Start Visual Studio.</span></span>

2.  <span data-ttu-id="02440-112">Menü çubuğunda, **dosya** > **yeni** > **proje**.</span><span class="sxs-lookup"><span data-stu-id="02440-112">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="02440-113">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="02440-113">The **New Project** dialog box opens.</span></span>

3.  <span data-ttu-id="02440-114">İçinde **yüklü şablonlar** bölmesinde, Visual C# ' ı seçin ve ardından **WPF uygulaması** proje türleri listesinden.</span><span class="sxs-lookup"><span data-stu-id="02440-114">In the **Installed Templates** pane, choose Visual C#, and then choose **WPF Application** from the list of project types.</span></span>

4.  <span data-ttu-id="02440-115">İçinde **adı** metin kutusuna `AsyncExampleWPF`ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="02440-115">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>

     <span data-ttu-id="02440-116">Yeni Proje görünür **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="02440-116">The new project appears in **Solution Explorer**.</span></span>

## <a name="design-a-simple-wpf-mainwindow"></a><span data-ttu-id="02440-117">Basit bir WPF MainWindow tasarlama</span><span class="sxs-lookup"><span data-stu-id="02440-117">Design a simple WPF MainWindow</span></span>

1.  <span data-ttu-id="02440-118">Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="02440-118">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

2.  <span data-ttu-id="02440-119">Varsa **araç kutusu** penceresi görünür ve açık değilse **görünümü** menüsünde ve ardından **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="02440-119">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>

3.  <span data-ttu-id="02440-120">Ekleme bir **düğmesi** denetimi ve bir **TextBox** denetimini **MainWindow** penceresi.</span><span class="sxs-lookup"><span data-stu-id="02440-120">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>

4.  <span data-ttu-id="02440-121">Vurgulama **TextBox** denetim hem de **özellikleri** penceresinde aşağıdaki değerleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="02440-121">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>

    -   <span data-ttu-id="02440-122">Ayarlama **adı** özelliğini `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="02440-122">Set the **Name** property to `resultsTextBox`.</span></span>

    -   <span data-ttu-id="02440-123">Ayarlama **yükseklik** 250 özelliği.</span><span class="sxs-lookup"><span data-stu-id="02440-123">Set the **Height** property to 250.</span></span>

    -   <span data-ttu-id="02440-124">Ayarlama **genişliği** 500 özelliği.</span><span class="sxs-lookup"><span data-stu-id="02440-124">Set the **Width** property to 500.</span></span>

    -   <span data-ttu-id="02440-125">Üzerinde **metin** sekmesinde, Lucida konsol veya genel tek aralıklı gibi sabit genişlikli bir yazı tipi belirtin.</span><span class="sxs-lookup"><span data-stu-id="02440-125">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>

5.  <span data-ttu-id="02440-126">Vurgulama **düğmesi** denetim hem de **özellikleri** penceresinde aşağıdaki değerleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="02440-126">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>

    -   <span data-ttu-id="02440-127">Ayarlama **adı** özelliğini `startButton`.</span><span class="sxs-lookup"><span data-stu-id="02440-127">Set the **Name** property to `startButton`.</span></span>

    -   <span data-ttu-id="02440-128">Değiştirin **içerik** özelliğinden **düğmesi** için **Başlat**.</span><span class="sxs-lookup"><span data-stu-id="02440-128">Change the value of the **Content** property from **Button** to **Start**.</span></span>

6.  <span data-ttu-id="02440-129">Metin kutusu ve düğme hem görünmesini sağlayacak şekilde konumlandırın **MainWindow** penceresi.</span><span class="sxs-lookup"><span data-stu-id="02440-129">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>

     <span data-ttu-id="02440-130">WPF XAML Tasarımcısı hakkında daha fazla bilgi için bkz. [XAML Tasarımcısını kullanarak kullanıcı Arabirimi oluşturma](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="02440-130">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>

## <a name="add-a-reference"></a><span data-ttu-id="02440-131">Bir başvuru ekleyin</span><span class="sxs-lookup"><span data-stu-id="02440-131">Add a reference</span></span>

1.  <span data-ttu-id="02440-132">İçinde **Çözüm Gezgini**, projenizin adını vurgulayın.</span><span class="sxs-lookup"><span data-stu-id="02440-132">In **Solution Explorer**, highlight your project's name.</span></span>

2.  <span data-ttu-id="02440-133">Menü çubuğunda, **proje** > **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="02440-133">On the menu bar, choose **Project** > **Add Reference**.</span></span>

     <span data-ttu-id="02440-134">**Başvuru Yöneticisi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="02440-134">The **Reference Manager** dialog box appears.</span></span>

3.  <span data-ttu-id="02440-135">İletişim kutusunun en üstünde, projeniz .NET Framework 4.5 veya üzerini hedeflediğinden doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="02440-135">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>

4.  <span data-ttu-id="02440-136">İçinde **derlemeleri** kategorisi seçin **Framework** tercih değildir.</span><span class="sxs-lookup"><span data-stu-id="02440-136">In the **Assemblies** category, choose **Framework** if it isn’t already chosen.</span></span>

5.  <span data-ttu-id="02440-137">Adları listesinde seçin **System.Net.Http** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="02440-137">In the list of names, select the **System.Net.Http** check box.</span></span>

6.  <span data-ttu-id="02440-138">Seçin **Tamam** iletişim kutusunu kapatmak için düğme.</span><span class="sxs-lookup"><span data-stu-id="02440-138">Choose the **OK** button to close the dialog box.</span></span>

## <a name="add-necessary-using-directives"></a><span data-ttu-id="02440-139">Ekleme yönergeleri kullanarak gerekli</span><span class="sxs-lookup"><span data-stu-id="02440-139">Add necessary using directives</span></span>

1.  <span data-ttu-id="02440-140">İçinde **Çözüm Gezgini**için MainWindow.xaml.cs kısayol menüsünü açın ve ardından **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="02440-140">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

2.  <span data-ttu-id="02440-141">Aşağıdaki `using` zaten mevcut değillerse kod dosyanın üst kısmındaki yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="02440-141">Add the following `using` directives at the top of the code file if they’re not already present.</span></span>

    ```csharp
    using System.Net.Http;
    using System.Net;
    using System.IO;
    ```

## <a name="create-a-synchronous-app"></a><span data-ttu-id="02440-142">Zaman uyumlu bir uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="02440-142">Create a synchronous app</span></span>

1.  <span data-ttu-id="02440-143">Tasarım penceresinde, MainWindow.xaml **Başlat** oluşturmak için düğmeyi `startButton_Click` MainWindow.xaml.cs olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="02440-143">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>

2.  <span data-ttu-id="02440-144">MainWindow.xaml.cs içinde gövdesine aşağıdaki kodu kopyalayın `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="02440-144">In MainWindow.xaml.cs, copy the following code into the body of `startButton_Click`:</span></span>

    ```csharp
    resultsTextBox.Clear();
    SumPageSizes();
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";
    ```

    <span data-ttu-id="02440-145">Kod uygulama sürücüleri yöntemini çağırır `SumPageSizes`ve denetim döndüğünde, bir ileti görüntüler `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="02440-145">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>

3.  <span data-ttu-id="02440-146">Aşağıdaki dört yöntemi zaman uyumlu çözüm için kod içerir:</span><span class="sxs-lookup"><span data-stu-id="02440-146">The code for the synchronous solution contains the following four methods:</span></span>

    -   <span data-ttu-id="02440-147">`SumPageSizes`, Web sayfasını URL'lerin bir listesini alır `SetUpURLList` ve `GetURLContents` ve `DisplayResults` her URL işlenecek.</span><span class="sxs-lookup"><span data-stu-id="02440-147">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>

    -   <span data-ttu-id="02440-148">`SetUpURLList`, yapar ve web adreslerinden oluşan bir liste döndürür.</span><span class="sxs-lookup"><span data-stu-id="02440-148">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>

    -   <span data-ttu-id="02440-149">`GetURLContents`, her bir Web sitesinin içeriklerini karşıdan yükler ve içeriği bir bayt dizisi olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="02440-149">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>

    -   <span data-ttu-id="02440-150">`DisplayResults`, görüntüleyen bayt bayt dizisindeki her URL.</span><span class="sxs-lookup"><span data-stu-id="02440-150">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>

    <span data-ttu-id="02440-151">Aşağıdaki dört yöntemi kopyalayın ve yapıştırın altında `startButton_Click` MainWindow.xaml.cs olay işleyicisinde:</span><span class="sxs-lookup"><span data-stu-id="02440-151">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.cs:</span></span>

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
        resultsTextBox.Text +=
            string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);
    }

    private List<string> SetUpURLList()
    {
        var urls = new List<string>
        {
            "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",
            "http://msdn.microsoft.com",
            "http://msdn.microsoft.com/library/hh290136.aspx",
            "http://msdn.microsoft.com/library/ee256749.aspx",
            "http://msdn.microsoft.com/library/hh290138.aspx",
            "http://msdn.microsoft.com/library/hh290140.aspx",
            "http://msdn.microsoft.com/library/dd470362.aspx",
            "http://msdn.microsoft.com/library/aa578028.aspx",
            "http://msdn.microsoft.com/library/ms404677.aspx",
            "http://msdn.microsoft.com/library/ff730837.aspx"
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
        // Strip off the "http://".
        var displayURL = url.Replace("http://", "");
        resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);
    }
    ```

## <a name="test-the-synchronous-solution"></a><span data-ttu-id="02440-152">Zaman uyumlu çözümü test</span><span class="sxs-lookup"><span data-stu-id="02440-152">Test the synchronous solution</span></span>

<span data-ttu-id="02440-153">Seçin **F5** programı çalıştırmak için anahtar ve ardından **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="02440-153">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

<span data-ttu-id="02440-154">Aşağıdaki listede benzer bir çıktı görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="02440-154">Output that resembles the following list should appear:</span></span>

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

<span data-ttu-id="02440-155">Sayıları görüntülemek için birkaç saniye sürer dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="02440-155">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="02440-156">İstenen kaynaklara indirmek beklediği sırada bu süre boyunca, kullanıcı Arabirimi iş parçacığı engellenir.</span><span class="sxs-lookup"><span data-stu-id="02440-156">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="02440-157">Sonuç olarak, taşıyamazsınız, en üst düzeye çıkarmak, en aza indirmek veya seçtiğiniz sonra bile görüntü penceresini kapatın **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="02440-157">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="02440-158">Görüntülenecek bayt sayısını başlatana kadar bu çalışmaların başarısız.</span><span class="sxs-lookup"><span data-stu-id="02440-158">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="02440-159">Bir Web sitesi yanıt vermediği takdirde başarısız hangi sitenin herhangi bir gösterge sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="02440-159">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="02440-160">Programı kapatmak ve bile beklemek istemiyorsanız zordur.</span><span class="sxs-lookup"><span data-stu-id="02440-160">It is difficult even to stop waiting and close the program.</span></span>

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a><span data-ttu-id="02440-161">Zaman uyumsuz bir yöntem GetURLContents Dönüştür</span><span class="sxs-lookup"><span data-stu-id="02440-161">Convert GetURLContents to an asynchronous method</span></span>

1.  <span data-ttu-id="02440-162">Zaman uyumlu çözüm için zaman uyumsuz bir çözümün dönüştürmek için başlatmak için en iyi yeri yer `GetURLContents` çünkü çağrıları <xref:System.Net.HttpWebRequest> yöntemi <xref:System.Net.HttpWebRequest.GetResponse%2A> ve <xref:System.IO.Stream> yöntemi <xref:System.IO.Stream.CopyTo%2A> uygulamaya web eriştiği olan .</span><span class="sxs-lookup"><span data-stu-id="02440-162">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="02440-163">.NET Framework dönüştürme iki yöntem de zaman uyumsuz sürümlerini sağlanarak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="02440-163">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>

     <span data-ttu-id="02440-164">Kullanılan yöntemleri hakkında daha fazla bilgi için `GetURLContents`, bkz: <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="02440-164">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="02440-165">Bu izlenecek yolda adımları gibi birkaç derleyici hatalar görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="02440-165">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="02440-166">Bunların yoksayılması ve adım adım kılavuza devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02440-166">You can ignore them and continue with the walkthrough.</span></span>

     <span data-ttu-id="02440-167">Üçüncü satırında çağrılan yöntem Değiştir `GetURLContents` gelen `GetResponse` için zaman uyumsuz, görev tabanlı <xref:System.Net.WebRequest.GetResponseAsync%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="02440-167">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>

    ```csharp
    using (WebResponse response = webReq.GetResponseAsync())
    ```

2.  <span data-ttu-id="02440-168">`GetResponseAsync` döndürür bir <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="02440-168">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="02440-169">Bu durumda, *görev dönüş değişkeni*, `TResult`, türünde <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="02440-169">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="02440-170">Görev bir gerçek üretmek için bir vaattir `WebResponse` istenen veri indirildi ve görevin çalıştırılıp tamamlandıktan sonra nesne.</span><span class="sxs-lookup"><span data-stu-id="02440-170">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>

     <span data-ttu-id="02440-171">Alınacak `WebResponse` görevden değer, geçerli bir [await](../../../../csharp/language-reference/keywords/await.md) işleci çağrısına `GetResponseAsync`aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="02440-171">To retrieve the `WebResponse` value from the task, apply an [await](../../../../csharp/language-reference/keywords/await.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>

    ```csharp
    using (WebResponse response = await webReq.GetResponseAsync())
    ```

     <span data-ttu-id="02440-172">`await` İşleci geçerli yöntemin yürütülmesini askıya `GetURLContents`, beklenen görev tamamlanana kadar.</span><span class="sxs-lookup"><span data-stu-id="02440-172">The `await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="02440-173">Bu sırada, denetim geçerli yöntemi çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="02440-173">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="02440-174">Bu örnekte, geçerli bir yöntemdir `GetURLContents`, ve çağıran `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="02440-174">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="02440-175">Görev tamamlandığında, taahhüt `WebResponse` nesne imzalamasına değeri olarak üretilen ve değişkenine atanan `response`.</span><span class="sxs-lookup"><span data-stu-id="02440-175">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>

     <span data-ttu-id="02440-176">Önceki deyim ne olduğunu açıklamak için aşağıdaki iki ifadeye ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="02440-176">The previous statement can be separated into the following two statements to clarify what happens.</span></span>

    ```csharp
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();
    //using (WebResponse response = await responseTask)
    ```

     <span data-ttu-id="02440-177">Çağrı `webReq.GetResponseAsync` döndürür bir `Task(Of WebResponse)` veya `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="02440-177">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="02440-178">Alınacak göreve await işleci uygulanır `WebResponse` değeri.</span><span class="sxs-lookup"><span data-stu-id="02440-178">Then an await operator is applied to the task to retrieve the `WebResponse` value.</span></span>

     <span data-ttu-id="02440-179">Zaman uyumsuz yöntem görev öğesinin tamamlanmasına bağlı olmayan bağımsız yapılacak çalışmaya sahipse yöntem çağrısından önce zaman uyumsuz yöntem ve sonra bu iki deyimden arasında bu çalışmalar ile devam edebilir `await` işleci uygulanır.</span><span class="sxs-lookup"><span data-stu-id="02440-179">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the `await` operator is applied.</span></span> <span data-ttu-id="02440-180">Örnekler için bkz [nasıl yapılır: zaman uyumsuz kullanarak birden çok Web isteğini paralel hale getirme ve await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) ve [nasıl yapılır: zaman uyumsuz izlenecek yolu Task.WhenAll (C#) kullanarak genişletme](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="02440-180">For examples, see [How to: Make Multiple Web Requests in Parallel by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

3.  <span data-ttu-id="02440-181">Eklediğiniz çünkü `await` işleci önceki adımda, bir derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="02440-181">Because you added the `await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="02440-182">İşleci ile işaretlenmiş yöntemler kullanılabilir [zaman uyumsuz](../../../../csharp/language-reference/keywords/async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="02440-182">The operator can be used only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="02440-183">Çağrısını için dönüştürme adımı yineleyin ancak hatasını görmezden Gel `CopyTo` çağrısıyla `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="02440-183">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>

    -   <span data-ttu-id="02440-184">İçin çağrılan yöntemin adını değiştirmek <xref:System.IO.Stream.CopyToAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="02440-184">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>

    -   <span data-ttu-id="02440-185">`CopyTo` Veya `CopyToAsync` yöntemi, bağımsız değişkeni için bayt kopyalar `content`ve anlamlı bir değer döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="02440-185">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="02440-186">Zaman uyumlu sürümü, çağrı `CopyTo` bir değer döndürmüyor basit bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="02440-186">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="02440-187">Zaman uyumsuz sürümü `CopyToAsync`, döndürür bir <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="02440-187">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="02440-188">Görev "Task(void)" gibi çalışır ve beklenmesini yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="02440-188">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="02440-189">Uygulama `Await` veya `await` çağrısına `CopyToAsync`aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="02440-189">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>

        ```csharp
        await responseStream.CopyToAsync(content);
        ```

         <span data-ttu-id="02440-190">Önceki deyim, aşağıdaki iki kod satırlarını kısaltmasıdır.</span><span class="sxs-lookup"><span data-stu-id="02440-190">The previous statement abbreviates the following two lines of code.</span></span>

        ```csharp
        // CopyToAsync returns a Task, not a Task<T>.
        //Task copyTask = responseStream.CopyToAsync(content);

        // When copyTask is completed, content contains a copy of
        // responseStream.
        //await copyTask;
        ```

4.  <span data-ttu-id="02440-191">Tüm bu yapılması kalır `GetURLContents` yöntem imzası ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="02440-191">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="02440-192">Kullanabileceğiniz `await` ile işaretlenmiş yöntemler işlecinde [zaman uyumsuz](../../../../csharp/language-reference/keywords/async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="02440-192">You can use the `await` operator only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="02440-193">Yöntemi olarak işaretlemek için değiştiricisi Ekle bir *zaman uyumsuz yöntem*aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="02440-193">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>

    ```csharp
    private async byte[] GetURLContents(string url)
    ```

5.  <span data-ttu-id="02440-194">Zaman uyumsuz bir yöntemin dönüş türü yalnızca olabilir <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, veya `void` C#.</span><span class="sxs-lookup"><span data-stu-id="02440-194">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or `void` in C#.</span></span> <span data-ttu-id="02440-195">Genellikle, dönüş türü `void` yalnızca zaman uyumsuz olay işleyicisi kullanılan burada `void` gereklidir.</span><span class="sxs-lookup"><span data-stu-id="02440-195">Typically, a return type of `void` is used only in an async event handler, where `void` is required.</span></span> <span data-ttu-id="02440-196">Diğer durumlarda, kullandığınız `Task(T)` tamamlanmış yöntemi varsa bir [dönüş](../../../../csharp/language-reference/keywords/return.md) T değeri döndüren bir ifade yazın ve kullandığınız `Task` tamamlanmış yöntemi anlamlı bir değer döndürmezse.</span><span class="sxs-lookup"><span data-stu-id="02440-196">In other cases, you use `Task(T)` if the completed method has a [return](../../../../csharp/language-reference/keywords/return.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span> <span data-ttu-id="02440-197">Düşünebilirsiniz `Task` dönüş türü olarak "Task(void)." anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="02440-197">You can think of the `Task` return type as meaning "Task(void)."</span></span>

     <span data-ttu-id="02440-198">Daha fazla bilgi için [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="02440-198">For more information, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>

     <span data-ttu-id="02440-199">Yöntemi `GetURLContents` bir dönüş ifadesi ve deyim bir bayt dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="02440-199">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="02440-200">Bu nedenle, zaman uyumsuz sürümü dönüş türünü görev(t), burada T bir bayt dizisi, ' dir.</span><span class="sxs-lookup"><span data-stu-id="02440-200">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="02440-201">Yöntem imzasında aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="02440-201">Make the following changes in the method signature:</span></span>

    -   <span data-ttu-id="02440-202">Geri dönüş için değiştirme `Task<byte[]>`.</span><span class="sxs-lookup"><span data-stu-id="02440-202">Change the return type to `Task<byte[]>`.</span></span>

    -   <span data-ttu-id="02440-203">Kural gereği, zaman uyumsuz yöntemler "Async," biten sahip. Bu nedenle metodu yeniden adlandırmak `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="02440-203">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>

     <span data-ttu-id="02440-204">Aşağıdaki kod, bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="02440-204">The following code shows these changes.</span></span>

    ```csharp
    private async Task<byte[]> GetURLContentsAsync(string url)
    ```

     <span data-ttu-id="02440-205">Bu birkaç değişiklikle dönüştürülmesi `GetURLContents` zaman uyumsuz bir yöntem tamamlandıktan.</span><span class="sxs-lookup"><span data-stu-id="02440-205">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a><span data-ttu-id="02440-206">Zaman uyumsuz bir yöntem SumPageSizes Dönüştür</span><span class="sxs-lookup"><span data-stu-id="02440-206">Convert SumPageSizes to an asynchronous method</span></span>

1.  <span data-ttu-id="02440-207">İçin önceki yordamdaki adımları yineleyin `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="02440-207">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="02440-208">İlk olarak, araması olarak değiştirmelerine `GetURLContents` zaman uyumsuz bir çağrı için.</span><span class="sxs-lookup"><span data-stu-id="02440-208">First, change the call to `GetURLContents` to an asynchronous call.</span></span>

    -   <span data-ttu-id="02440-209">Yönteminden çağrılan yöntemin adını değiştirmek `GetURLContents` için `GetURLContentsAsync`, zaten yapmadıysanız.</span><span class="sxs-lookup"><span data-stu-id="02440-209">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>

    -   <span data-ttu-id="02440-210">Uygulama `await` görev, `GetURLContentsAsync` dizi değeri bayt almak için döndürür.</span><span class="sxs-lookup"><span data-stu-id="02440-210">Apply `await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>

     <span data-ttu-id="02440-211">Aşağıdaki kod, bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="02440-211">The following code shows these changes.</span></span>

    ```csharp
    byte[] urlContents = await GetURLContentsAsync(url);
    ```

     <span data-ttu-id="02440-212">Önceki atama aşağıdaki iki kod satırlarını kısaltmasıdır.</span><span class="sxs-lookup"><span data-stu-id="02440-212">The previous assignment abbreviates the following two lines of code.</span></span>

    ```csharp
    // GetURLContentsAsync returns a Task<T>. At completion, the task
    // produces a byte array.
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //byte[] urlContents = await getContentsTask;
    ```

2.  <span data-ttu-id="02440-213">Yöntemin imzası ' aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="02440-213">Make the following changes in the method's signature:</span></span>

    -   <span data-ttu-id="02440-214">Yöntemi işaretlemek `async` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="02440-214">Mark the method with the `async` modifier.</span></span>

    -   <span data-ttu-id="02440-215">"Async" yöntem adına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="02440-215">Add "Async" to the method name.</span></span>

    -   <span data-ttu-id="02440-216">T, hiçbir görev dönüş değişken bu süresi yoktur çünkü `SumPageSizesAsync` t için bir değer döndürmüyor (Yöntemin sahip olmayan `return` deyimi.) Ancak, yöntem döndürmelidir bir `Task` olması beklenebilir.</span><span class="sxs-lookup"><span data-stu-id="02440-216">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="02440-217">Bu nedenle, metodun dönüş türü değiştirme `void` için `Task`.</span><span class="sxs-lookup"><span data-stu-id="02440-217">Therefore, change the return type of the method from `void` to `Task`.</span></span>

    <span data-ttu-id="02440-218">Aşağıdaki kod, bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="02440-218">The following code shows these changes.</span></span>

    ```csharp
    private async Task SumPageSizesAsync()
    ```

     <span data-ttu-id="02440-219">Dönüştürme `SumPageSizes` için `SumPageSizesAsync` tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="02440-219">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>

## <a name="convert-startbuttonclick-to-an-asynchronous-method"></a><span data-ttu-id="02440-220">Zaman uyumsuz bir yöntem startButton_Click Dönüştür</span><span class="sxs-lookup"><span data-stu-id="02440-220">Convert startButton_Click to an asynchronous method</span></span>

1.  <span data-ttu-id="02440-221">Olay işleyicisi, çağrılan yöntemden adını değiştirmek `SumPageSizes` için `SumPageSizesAsync`, zaten yapmadıysanız.</span><span class="sxs-lookup"><span data-stu-id="02440-221">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>

2.  <span data-ttu-id="02440-222">Çünkü `SumPageSizesAsync` bir zaman uyumsuz yöntem sonucu await için olay işleyicisinde kodu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="02440-222">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>

     <span data-ttu-id="02440-223">Çağrı `SumPageSizesAsync` çağrısı yansıtır `CopyToAsync` içinde `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="02440-223">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="02440-224">Çağrı döndürür bir `Task`değil bir `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="02440-224">The call returns a `Task`, not a `Task(T)`.</span></span>

     <span data-ttu-id="02440-225">Önceki yordamlardan olduğu gibi bir deyim ya da iki ifadeleri kullanarak arama dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02440-225">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="02440-226">Aşağıdaki kod, bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="02440-226">The following code shows these changes.</span></span>

    ```csharp
    // One-step async call.
    await SumPageSizesAsync();

    // Two-step async call.
    //Task sumTask = SumPageSizesAsync();
    //await sumTask;
    ```

3.  <span data-ttu-id="02440-227">İşlem yanlışlıkla yeniden girildi önlemek için üstüne aşağıdaki ifadeyi ekleyin `startButton_Click` devre dışı bırakmak için **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="02440-227">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>

    ```csharp
    // Disable the button until the operation is complete.
    startButton.IsEnabled = false;
    ```

     <span data-ttu-id="02440-228">Olay işleyicisi sonunda düğmeyi yeniden etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02440-228">You can reenable the button at the end of the event handler.</span></span>

    ```csharp
    // Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = true;
    ```

     <span data-ttu-id="02440-229">Yeniden giriş hakkında daha fazla bilgi için bkz: [(C#) zaman uyumsuz uygulamalarda yeniden girişi işleme](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="02440-229">For more information about reentrancy, see [Handling Reentrancy in Async Apps (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>

4.  <span data-ttu-id="02440-230">Son olarak, ekleme `async` değiştiricisi bildirimine olay işleyicisi await, böylece `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="02440-230">Finally, add the `async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>

    ```csharp
    private async void startButton_Click(object sender, RoutedEventArgs e)
    ```

     <span data-ttu-id="02440-231">Olay işleyicileri adları genellikle değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="02440-231">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="02440-232">Dönüş türü için değiştirilmez `Task` olay işleyicileri dönüştürüldüğünden `void`.</span><span class="sxs-lookup"><span data-stu-id="02440-232">The return type isn’t changed to `Task` because event handlers must return `void`.</span></span>

     <span data-ttu-id="02440-233">Proje dönüştürülmesi için zaman uyumsuz zaman uyumlu işlenmesi tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="02440-233">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>

## <a name="test-the-asynchronous-solution"></a><span data-ttu-id="02440-234">Zaman uyumsuz bir çözümü test etme</span><span class="sxs-lookup"><span data-stu-id="02440-234">Test the asynchronous solution</span></span>

1.  <span data-ttu-id="02440-235">Seçin **F5** programı çalıştırmak için anahtar ve ardından **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="02440-235">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

2.  <span data-ttu-id="02440-236">Zaman uyumlu çözümün çıktıya benzer bir çıktı görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="02440-236">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="02440-237">Ancak, aşağıdaki farklar dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="02440-237">However, notice the following differences.</span></span>

    -   <span data-ttu-id="02440-238">Sonuçları işleme tamamlandıktan sonra aynı zamanda, tüm oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="02440-238">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="02440-239">Örneğin, her iki programın bir satır içeren `startButton_Click` , metin kutusuna temizler.</span><span class="sxs-lookup"><span data-stu-id="02440-239">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="02440-240">Seçerseniz çalıştırmaları arasında metin kutusunu temizlemek için hedefi olan **Başlat** bir sonuç kümesini göründükten sonra ikinci bir kez, düğme.</span><span class="sxs-lookup"><span data-stu-id="02440-240">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="02440-241">Yalnızca sayıları ne zaman karşıdan yüklemeler tamamlandı ve diğer işlerini gerçekleştirmek kullanıcı Arabirimi iş parçacığı ücretsizdir ikinci kez görünmesi zaman uyumlu bir sürümde, metin kutusu işaretli değildir.</span><span class="sxs-lookup"><span data-stu-id="02440-241">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="02440-242">Seçtiğiniz hemen sonra metin kutusuna zaman uyumsuz sürümünde temizler **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="02440-242">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>

    -   <span data-ttu-id="02440-243">En önemlisi de UI iş parçacığı yüklemeleri sırasında bloke değildir.</span><span class="sxs-lookup"><span data-stu-id="02440-243">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="02440-244">Geçiş yapabilir veya web kaynakları indirilirken, penceresini yeniden boyutlandırdığınızda sayılan ve görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="02440-244">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="02440-245">Web sitelerinden birini ise yavaş veya yanıt vermiyor, işlem seçerek iptal edebilirsiniz **Kapat** düğmesine (sağ üst köşesinde kırmızı alanında x).</span><span class="sxs-lookup"><span data-stu-id="02440-245">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>

## <a name="replace-method-geturlcontentsasync-with-a-net-framework-method"></a><span data-ttu-id="02440-246">Bir .NET Framework yöntemi ile yöntem GetURLContentsAsync değiştirin</span><span class="sxs-lookup"><span data-stu-id="02440-246">Replace method GetURLContentsAsync with a .NET Framework method</span></span>

1.  <span data-ttu-id="02440-247">.NET Framework 4.5 kullanabileceğiniz pek çok zaman uyumsuz yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="02440-247">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="02440-248">Bunlardan biri <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, yalnızca bu kılavuz için ihtiyacınız olanları yapar.</span><span class="sxs-lookup"><span data-stu-id="02440-248">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="02440-249">Bunu yerine `GetURLContentsAsync` bir önceki yordamda oluşturduğunuz yöntemi.</span><span class="sxs-lookup"><span data-stu-id="02440-249">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>

     <span data-ttu-id="02440-250">İlk adım oluşturmaktır bir `HttpClient` yöntemi nesnesinde `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="02440-250">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="02440-251">Yönteminin başlangıcında aşağıdaki bildirimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="02440-251">Add the following declaration at the start of the method.</span></span>

    ```csharp
    // Declare an HttpClient object and increase the buffer size. The
    // default buffer size is 65,536.
    HttpClient client =
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };
    ```

2.  <span data-ttu-id="02440-252">İçinde `SumPageSizesAsync,` çağrısını, `GetURLContentsAsync` yöntemi çağrısıyla `HttpClient` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="02440-252">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>

    ```csharp
    byte[] urlContents = await client.GetByteArrayAsync(url);
    ```

3.  <span data-ttu-id="02440-253">Kaldırın veya açıklama `GetURLContentsAsync` yazdığınız yöntemi.</span><span class="sxs-lookup"><span data-stu-id="02440-253">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>

4.  <span data-ttu-id="02440-254">Seçin **F5** programı çalıştırmak için anahtar ve ardından **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="02440-254">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="02440-255">Bu sürümü, proje davranışını "zaman uyumsuz bir çözümü test etmek için" yordamı açıklanan davranışı eşleşen ancak sizden daha az çaba ile bile gerekir.</span><span class="sxs-lookup"><span data-stu-id="02440-255">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>

## <a name="example-code"></a><span data-ttu-id="02440-256">Örnek kod</span><span class="sxs-lookup"><span data-stu-id="02440-256">Example code</span></span>

<span data-ttu-id="02440-257">Zaman uyumsuz kullanarak zaman uyumsuz bir çözüm eş zamanlı dönüştürme tam örneği aşağıdaki kodu içeren `GetURLContentsAsync` yazdığınız yöntemi.</span><span class="sxs-lookup"><span data-stu-id="02440-257">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="02440-258">Bunu kesinlikle özgün, zaman uyumlu bir çözüm benzer olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="02440-258">Notice that it strongly resembles the original, synchronous solution.</span></span>

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
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "http://msdn.microsoft.com",
                "http://msdn.microsoft.com/library/hh290136.aspx",
                "http://msdn.microsoft.com/library/ee256749.aspx",
                "http://msdn.microsoft.com/library/hh290138.aspx",
                "http://msdn.microsoft.com/library/hh290140.aspx",
                "http://msdn.microsoft.com/library/dd470362.aspx",
                "http://msdn.microsoft.com/library/aa578028.aspx",
                "http://msdn.microsoft.com/library/ms404677.aspx",
                "http://msdn.microsoft.com/library/ff730837.aspx"
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
            // Strip off the "http://".
            var displayURL = url.Replace("http://", "");
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);
        }
    }
}
```

<span data-ttu-id="02440-259">Aşağıdaki kod tam örneği kullanan bir çözüm içeren `HttpClient` yöntemi `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="02440-259">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>

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
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "http://msdn.microsoft.com",
                "http://msdn.microsoft.com/library/hh290136.aspx",
                "http://msdn.microsoft.com/library/ee256749.aspx",
                "http://msdn.microsoft.com/library/hh290138.aspx",
                "http://msdn.microsoft.com/library/hh290140.aspx",
                "http://msdn.microsoft.com/library/dd470362.aspx",
                "http://msdn.microsoft.com/library/aa578028.aspx",
                "http://msdn.microsoft.com/library/ms404677.aspx",
                "http://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each website. The string format
            // is designed to be used with a monospaced font, such as
            // Lucida Console or Global Monospace.
            var bytes = content.Length;
            // Strip off the "http://".
            var displayURL = url.Replace("http://", "");
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="02440-260">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02440-260">See also</span></span>

- [<span data-ttu-id="02440-261">Zaman uyumsuz örneği: izlenecek yol (C# ve Visual Basic) erişme</span><span class="sxs-lookup"><span data-stu-id="02440-261">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [<span data-ttu-id="02440-262">async</span><span class="sxs-lookup"><span data-stu-id="02440-262">async</span></span>](../../../../csharp/language-reference/keywords/async.md)
- [<span data-ttu-id="02440-263">await</span><span class="sxs-lookup"><span data-stu-id="02440-263">await</span></span>](../../../../csharp/language-reference/keywords/await.md)
- [<span data-ttu-id="02440-264">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="02440-264">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="02440-265">Zaman uyumsuz dönüş türleri (C#)</span><span class="sxs-lookup"><span data-stu-id="02440-265">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)
- [<span data-ttu-id="02440-266">Görev tabanlı zaman uyumsuz desen (TAP)</span><span class="sxs-lookup"><span data-stu-id="02440-266">Task-based Asynchronous Programming (TAP)</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=19957)
- [<span data-ttu-id="02440-267">Nasıl yapılır: zaman uyumsuz izlenecek yolu Task.WhenAll (C#) kullanarak genişletme</span><span class="sxs-lookup"><span data-stu-id="02440-267">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [<span data-ttu-id="02440-268">Nasıl yapılır: birden çok Web isteğini paralel olarak zaman uyumsuz kullanarak ve olun await (C#)</span><span class="sxs-lookup"><span data-stu-id="02440-268">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
