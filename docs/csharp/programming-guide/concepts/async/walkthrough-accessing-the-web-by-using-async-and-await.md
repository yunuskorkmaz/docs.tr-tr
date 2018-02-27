---
title: "İzlenecek yol: async kullanarak Web'e erişme ve await (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: get-started-article
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 533cb4b342e3de3eb3143b001f5a26e36e4d79b9
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2018
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a><span data-ttu-id="1593f-102">İzlenecek yol: async kullanarak Web'e erişme ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="1593f-102">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>
<span data-ttu-id="1593f-103">Zaman uyumsuz ve bekleme özelliklerini kullanarak zaman uyumsuz programlar daha kolay ve sezgisel yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1593f-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="1593f-104">Zaman uyumlu kod gibi görünüyor zaman uyumsuz kod yazın ve daha zor geri arama işlevleri ve zaman uyumsuz kod genellikle kapsar devamlılıklar işlemek derleyici sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1593f-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>  
  
 <span data-ttu-id="1593f-105">Async özelliği hakkında daha fazla bilgi için bkz: [zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="1593f-105">For more information about the Async feature, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="1593f-106">Bu kılavuzda Web sitelerinin bir listesiyle bayt sayısını toplar zaman uyumlu bir Windows Presentation Foundation (WPF) uygulama başlar.</span><span class="sxs-lookup"><span data-stu-id="1593f-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="1593f-107">İzlenecek yol sonra yeni özellikleri kullanarak zaman uyumsuz çözümünü uygulamaya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="1593f-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>  
  
 <span data-ttu-id="1593f-108">Uygulamaları kendiniz yapılandırmak istemiyorsanız, indirebilirsiniz [zaman uyumsuz örnek: Web gözden geçirme (C# ve Visual Basic) erişme](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="1593f-108">If you don't want to build the applications yourself, you can download [Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
  
 <span data-ttu-id="1593f-109">Bu kılavuzda, aşağıdaki görevleri tamamlayın:</span><span class="sxs-lookup"><span data-stu-id="1593f-109">In this walkthrough, you complete the following tasks:</span></span>  
  
-   [<span data-ttu-id="1593f-110">Bir WPF uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1593f-110">To create a WPF application</span></span>](#CreateWPFApp)  
  
-   [<span data-ttu-id="1593f-111">Basit bir WPF MainWindow tasarlamak için</span><span class="sxs-lookup"><span data-stu-id="1593f-111">To design a simple WPF MainWindow</span></span>](#MainWindow)  
  
-   [<span data-ttu-id="1593f-112">Bir başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="1593f-112">To add a reference</span></span>](#AddRef)  
  
-   [<span data-ttu-id="1593f-113">Eklemek için gerekli yönergeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="1593f-113">To add necessary using directives</span></span>](#usingDir)  
  
-   [<span data-ttu-id="1593f-114">Zaman uyumlu bir uygulama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1593f-114">To create a synchronous application</span></span>](#synchronous)  
  
-   [<span data-ttu-id="1593f-115">Zaman uyumlu çözümü test etmek için</span><span class="sxs-lookup"><span data-stu-id="1593f-115">To test the synchronous solution</span></span>](#testSynch)  
  
-   [<span data-ttu-id="1593f-116">Zaman uyumsuz bir yöntem GetURLContents dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="1593f-116">To convert GetURLContents to an asynchronous method</span></span>](#GetURLContents)  
  
-   [<span data-ttu-id="1593f-117">Zaman uyumsuz bir yöntem SumPageSizes dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="1593f-117">To convert SumPageSizes to an asynchronous method</span></span>](#SumPageSizes)  
  
-   [<span data-ttu-id="1593f-118">Zaman uyumsuz bir yöntem startButton_Click dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="1593f-118">To convert startButton_Click to an asynchronous method</span></span>](#startButton)  
  
-   [<span data-ttu-id="1593f-119">Zaman uyumsuz çözümü test etmek için</span><span class="sxs-lookup"><span data-stu-id="1593f-119">To test the asynchronous solution</span></span>](#testAsynch)  
  
-   [<span data-ttu-id="1593f-120">.NET Framework yöntemiyle yöntemi GetURLContentsAsync değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="1593f-120">To replace method GetURLContentsAsync with a .NET Framework method</span></span>](#GetURLContentsAsync)  
  
-   [<span data-ttu-id="1593f-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="1593f-121">Example</span></span>](#BKMK_CompleteCodeExamples)  
  
> [!NOTE]
>  <span data-ttu-id="1593f-122">Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 olmalıdır veya daha yeni bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="1593f-122">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
###  <a name="CreateWPFApp"></a> <span data-ttu-id="1593f-123">Bir WPF uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1593f-123">To create a WPF application</span></span>  
  
1.  <span data-ttu-id="1593f-124">Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="1593f-124">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="1593f-125">Menü çubuğunda seçin **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="1593f-125">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="1593f-126">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="1593f-126">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="1593f-127">İçinde **yüklü şablonlar** bölmesinde, Visual C# ' ı seçin ve ardından **WPF uygulaması** proje türleri listesinden.</span><span class="sxs-lookup"><span data-stu-id="1593f-127">In the **Installed Templates** pane, choose Visual C#, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="1593f-128">İçinde **adı** metin kutusuna `AsyncExampleWPF`ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1593f-128">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="1593f-129">Yeni Proje görünür **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="1593f-129">The new project appears in **Solution Explorer**.</span></span>  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <a name="MainWindow"></a> <span data-ttu-id="1593f-130">Basit bir WPF MainWindow tasarlamak için</span><span class="sxs-lookup"><span data-stu-id="1593f-130">To design a simple WPF MainWindow</span></span>  
  
1.  <span data-ttu-id="1593f-131">Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="1593f-131">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
2.  <span data-ttu-id="1593f-132">Varsa **araç** pencere görünür, açık olmayan **Görünüm** menüsünde ve ardından **araç**.</span><span class="sxs-lookup"><span data-stu-id="1593f-132">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="1593f-133">Ekleme bir **düğmesini** denetim ve **TextBox** denetimini **MainWindow** penceresi.</span><span class="sxs-lookup"><span data-stu-id="1593f-133">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>  
  
4.  <span data-ttu-id="1593f-134">Vurgula **TextBox** denetim hem de **özellikleri** penceresinde, aşağıdaki değerleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="1593f-134">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="1593f-135">Ayarlama **adı** özelliğine `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="1593f-135">Set the **Name** property to `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="1593f-136">Ayarlama **yükseklik** 250 özelliğine.</span><span class="sxs-lookup"><span data-stu-id="1593f-136">Set the **Height** property to 250.</span></span>  
  
    -   <span data-ttu-id="1593f-137">Ayarlama **genişliği** 500 özelliği.</span><span class="sxs-lookup"><span data-stu-id="1593f-137">Set the **Width** property to 500.</span></span>  
  
    -   <span data-ttu-id="1593f-138">Üzerinde **metin** sekmesinde, Lucida Console veya genel tek aralıklı gibi aralıklı bir yazı tipi belirtin.</span><span class="sxs-lookup"><span data-stu-id="1593f-138">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>  
  
5.  <span data-ttu-id="1593f-139">Vurgula **düğmesini** denetim hem de **özellikleri** penceresinde, aşağıdaki değerleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="1593f-139">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="1593f-140">Ayarlama **adı** özelliğine `startButton`.</span><span class="sxs-lookup"><span data-stu-id="1593f-140">Set the **Name** property to `startButton`.</span></span>  
  
    -   <span data-ttu-id="1593f-141">Değerini değiştirme **içerik** özelliğinden **düğmesini** için **Başlat**.</span><span class="sxs-lookup"><span data-stu-id="1593f-141">Change the value of the **Content** property from **Button** to **Start**.</span></span>  
  
6.  <span data-ttu-id="1593f-142">Her ikisi de görünmesini sağlayacak şekilde, metin kutusu ve düğmesi konum **MainWindow** penceresi.</span><span class="sxs-lookup"><span data-stu-id="1593f-142">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>  
  
     <span data-ttu-id="1593f-143">WPF XAML Tasarımcısı hakkında daha fazla bilgi için bkz: [XAML Tasarımcısını kullanarak bir kullanıcı Arabirimi oluşturma](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="1593f-143">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>  
  
##  <a name="BKMK_AddReference"></a>   
###  <a name="AddRef"></a> <span data-ttu-id="1593f-144">Bir başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="1593f-144">To add a reference</span></span>  
  
1.  <span data-ttu-id="1593f-145">İçinde **Çözüm Gezgini**, projenizin adını vurgulayın.</span><span class="sxs-lookup"><span data-stu-id="1593f-145">In **Solution Explorer**, highlight your project's name.</span></span>  
  
2.  <span data-ttu-id="1593f-146">Menü çubuğunda seçin **proje**, **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="1593f-146">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="1593f-147">**Başvuru Yöneticisi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1593f-147">The **Reference Manager** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="1593f-148">İletişim kutusunun üstündeki projeniz .NET Framework 4.5 veya üstünü hedefleyen olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="1593f-148">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>  
  
4.  <span data-ttu-id="1593f-149">İçinde **derlemeleri** alanı seçin **Framework** tercih değil.</span><span class="sxs-lookup"><span data-stu-id="1593f-149">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
5.  <span data-ttu-id="1593f-150">Adları listesinden seçin **System.Net.Http** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="1593f-150">In the list of names, select the **System.Net.Http** check box.</span></span>  
  
6.  <span data-ttu-id="1593f-151">Seçin **Tamam** düğmesi iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="1593f-151">Choose the **OK** button to close the dialog box.</span></span>  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <a name="usingDir"></a> <span data-ttu-id="1593f-152">Eklemek için gerekli yönergeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="1593f-152">To add necessary using directives</span></span>  
  
1.  <span data-ttu-id="1593f-153">İçinde **Çözüm Gezgini**MainWindow.xaml.cs için kısayol menüsünü açın ve ardından **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="1593f-153">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="1593f-154">Aşağıdakileri ekleyin `using` zaten mevcut değillerse kod dosyasının üst yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="1593f-154">Add the following `using` directives at the top of the code file if they’re not already present.</span></span>  
  
    ```csharp  
    using System.Net.Http;  
    using System.Net;  
    using System.IO;  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <a name="synchronous"></a> <span data-ttu-id="1593f-155">Zaman uyumlu bir uygulama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1593f-155">To create a synchronous application</span></span>  
  
1.  <span data-ttu-id="1593f-156">Tasarım penceresinde MainWindow.xaml, çift **Başlat** oluşturmak için düğmesini `startButton_Click` MainWindow.xaml.cs olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="1593f-156">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2.  <span data-ttu-id="1593f-157">MainWindow.xaml.cs içinde gövdesine aşağıdaki kodu kopyalayın `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="1593f-157">In MainWindow.xaml.cs, copy the following code into the body of `startButton_Click`:</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    SumPageSizes();  
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";  
    ```  
  
     <span data-ttu-id="1593f-158">Kod uygulama sürücüleri yöntemini çağırır `SumPageSizes`ve denetim döndüğünde bir ileti görüntüler `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="1593f-158">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>  
  
3.  <span data-ttu-id="1593f-159">Zaman uyumlu çözüm için kod aşağıdaki dört yöntemi içerir:</span><span class="sxs-lookup"><span data-stu-id="1593f-159">The code for the synchronous solution contains the following four methods:</span></span>  
  
    -   <span data-ttu-id="1593f-160">`SumPageSizes`, Web sayfası URL'lerden listesini alır `SetUpURLList` ve çağırır `GetURLContents` ve `DisplayResults` her URL işleyemedi.</span><span class="sxs-lookup"><span data-stu-id="1593f-160">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>  
  
    -   <span data-ttu-id="1593f-161">`SetUpURLList`, hangi yapar ve web adresleri listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="1593f-161">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>  
  
    -   <span data-ttu-id="1593f-162">`GetURLContents`, her Web sitesi içeriğini indirir ve içeriği bir bayt dizisi olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="1593f-162">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>  
  
    -   <span data-ttu-id="1593f-163">`DisplayResults`, görüntüleyen bayt sayısı bayt dizisi, her URL için.</span><span class="sxs-lookup"><span data-stu-id="1593f-163">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>  
  
     <span data-ttu-id="1593f-164">Aşağıdaki dört yöntemi kopyalayın ve yapıştırın altında `startButton_Click` MainWindow.xaml.cs olay işleyicisi:</span><span class="sxs-lookup"><span data-stu-id="1593f-164">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.cs:</span></span>  
  
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
  
##  <a name="BKMK_TestSynchSol"></a>   
###  <a name="testSynch"></a> <span data-ttu-id="1593f-165">Zaman uyumlu çözümü test etmek için</span><span class="sxs-lookup"><span data-stu-id="1593f-165">To test the synchronous solution</span></span>  
  
1.  <span data-ttu-id="1593f-166">Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1593f-166">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="1593f-167">Aşağıdaki listede benzer bir çıktı görüntülenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1593f-167">Output that resembles the following list should appear.</span></span>  
  
    ```  
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
  
     <span data-ttu-id="1593f-168">Sayıları görüntülemek için birkaç saniye sürer dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1593f-168">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="1593f-169">İstenen kaynaklar indirmek beklerken bu süre içinde kullanıcı Arabirimi iş parçacığı engellendi.</span><span class="sxs-lookup"><span data-stu-id="1593f-169">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="1593f-170">Sonuç olarak, taşıyamazsınız, en üst düzeye çıkarmak, simge durumuna küçült veya seçtiğiniz sonra bile görüntü penceresini kapatın **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1593f-170">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="1593f-171">Görüntülenecek bayt sayıları başlatana kadar bu çaba başarısız.</span><span class="sxs-lookup"><span data-stu-id="1593f-171">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="1593f-172">Bir Web sitesi yanıt vermiyor gösterge olmadan başarısız hangi sitenin varsa.</span><span class="sxs-lookup"><span data-stu-id="1593f-172">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="1593f-173">Hatta bekleme durdurmak ve program kapatmak zordur.</span><span class="sxs-lookup"><span data-stu-id="1593f-173">It is difficult even to stop waiting and close the program.</span></span>  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <a name="GetURLContents"></a> <span data-ttu-id="1593f-174">Zaman uyumsuz bir yöntem GetURLContents dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="1593f-174">To convert GetURLContents to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="1593f-175">Zaman uyumsuz bir çözüme zaman uyumlu çözüm dönüştürmek için başlatmak için en iyi yerdir bulunduğu `GetURLContents` çünkü çağrıları <xref:System.Net.HttpWebRequest> yöntemi <xref:System.Net.HttpWebRequest.GetResponse%2A> ve <xref:System.IO.Stream> yöntemi <xref:System.IO.Stream.CopyTo%2A> burada web uygulama erişen olan .</span><span class="sxs-lookup"><span data-stu-id="1593f-175">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="1593f-176">.NET Framework dönüştürme her iki yöntem zaman uyumsuz sürümlerini sağlayarak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="1593f-176">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>  
  
     <span data-ttu-id="1593f-177">Kullanılan yöntemleri hakkında daha fazla bilgi için `GetURLContents`, bkz: <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="1593f-177">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1593f-178">Bu izlenecek adımları izlediğiniz gibi birkaç derleyici hataları görünür.</span><span class="sxs-lookup"><span data-stu-id="1593f-178">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="1593f-179">Bunları yoksay ve kılavuz ile devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1593f-179">You can ignore them and continue with the walkthrough.</span></span>  
  
     <span data-ttu-id="1593f-180">Üçüncü satırında adlı yöntemini değiştirme `GetURLContents` gelen `GetResponse` için zaman uyumsuz, görev tabanlı <xref:System.Net.WebRequest.GetResponseAsync%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1593f-180">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>  
  
    ```csharp  
    using (WebResponse response = webReq.GetResponseAsync())  
    ```  
  
2.  <span data-ttu-id="1593f-181">`GetResponseAsync` döndüren bir <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="1593f-181">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="1593f-182">Bu durumda, *görev dönüş değişkeni*, `TResult`, türüne sahip <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="1593f-182">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="1593f-183">Gerçek bir üretmek için promise görevdir `WebResponse` istenen veri indirilir ve görevin tamamlanması çalıştıktan sonra nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1593f-183">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>  
  
     <span data-ttu-id="1593f-184">Alınacak `WebResponse` görevden değer, geçerli bir [await](../../../../csharp/language-reference/keywords/await.md) çağrısına işleci `GetResponseAsync`, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="1593f-184">To retrieve the `WebResponse` value from the task, apply an [await](../../../../csharp/language-reference/keywords/await.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>  
  
    ```csharp  
    using (WebResponse response = await webReq.GetResponseAsync())  
    ```  
  
     <span data-ttu-id="1593f-185">`await` İşleci geçerli yönteminin yürütülmesi askıya `GetURLContents`, awaited görevi tamamlanana kadar.</span><span class="sxs-lookup"><span data-stu-id="1593f-185">The `await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="1593f-186">Bu arada, denetim geçerli yöntemi çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="1593f-186">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="1593f-187">Bu örnekte, geçerli bir yöntemdir `GetURLContents`, ve çağrıyı yapan `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="1593f-187">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="1593f-188">Görev tamamlandığında taahhüt `WebResponse` nesne awaited görev değeri olarak üretilen ve değişkenine atanan `response`.</span><span class="sxs-lookup"><span data-stu-id="1593f-188">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>  
  
     <span data-ttu-id="1593f-189">Önceki deyimi ne olacağını açıklamak için aşağıdaki iki deyime ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="1593f-189">The previous statement can be separated into the following two statements to clarify what happens.</span></span>  
  
    ```csharp  
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();  
    //using (WebResponse response = await responseTask)  
    ```  
  
     <span data-ttu-id="1593f-190">Çağrı `webReq.GetResponseAsync` döndüren bir `Task(Of WebResponse)` veya `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="1593f-190">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="1593f-191">Görevi almak için bir bekleme işleç uygulanan sonra `WebResponse` değeri.</span><span class="sxs-lookup"><span data-stu-id="1593f-191">Then an await operator is applied to the task to retrieve the `WebResponse` value.</span></span>  
  
     <span data-ttu-id="1593f-192">Zaman uyumsuz yöntem görev tamamlanma bağımlı değil yapmak için iş varsa, yöntemi zaman uyumsuz yöntem ve önce çağrısından sonra bu iki ifade arasındaki, iş ile devam edebilirsiniz `await` işleci uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1593f-192">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the `await` operator is applied.</span></span> <span data-ttu-id="1593f-193">Örnekler için bkz [nasıl yapılır: zaman uyumsuz kullanarak birden çok Web isteğini paralel hale ve await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) ve [nasıl yapılır: Task.WhenAll kullanarak (C#) tarafından izlenecek zaman uyumsuz genişletmek](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="1593f-193">For examples, see [How to: Make Multiple Web Requests in Parallel by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
3.  <span data-ttu-id="1593f-194">Eklediğiniz çünkü `await` işleci önceki adımda, bir derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="1593f-194">Because you added the `await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="1593f-195">İşleç ile işaretlenmiş yöntemleri kullanılabilir [zaman uyumsuz](../../../../csharp/language-reference/keywords/async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="1593f-195">The operator can be used only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="1593f-196">Çağrı değiştirmek için dönüştürme adımları yineleyin sırada hatayı yok sayıp `CopyTo` çağrısıyla `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="1593f-196">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>  
  
    -   <span data-ttu-id="1593f-197">İçin çağrılan yöntemin adını değiştirmek <xref:System.IO.Stream.CopyToAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="1593f-197">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>  
  
    -   <span data-ttu-id="1593f-198">`CopyTo` Veya `CopyToAsync` yöntemi için bağımsız değişkeni, bayt kopyalar `content`ve anlamlı bir değer döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="1593f-198">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="1593f-199">Zaman uyumlu sürümünde, çağrısı `CopyTo` bir değer döndürmüyor basit bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="1593f-199">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="1593f-200">Zaman uyumsuz sürümü `CopyToAsync`, döndüren bir <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="1593f-200">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="1593f-201">Görev "Task(void)" gibi çalışır ve yöntem beklemenin sağlar.</span><span class="sxs-lookup"><span data-stu-id="1593f-201">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="1593f-202">Uygulama `Await` veya `await` çağrısına `CopyToAsync`, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="1593f-202">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>  
  
        ```csharp  
        await responseStream.CopyToAsync(content);  
        ```  
  
         <span data-ttu-id="1593f-203">Önceki deyimi aşağıdaki iki kod satırı kısaltmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1593f-203">The previous statement abbreviates the following two lines of code.</span></span>  
  
        ```csharp  
        // CopyToAsync returns a Task, not a Task<T>.  
        //Task copyTask = responseStream.CopyToAsync(content);  
  
        // When copyTask is completed, content contains a copy of  
        // responseStream.  
        //await copyTask;  
        ```  
  
4.  <span data-ttu-id="1593f-204">Tüm bu tamamlandı olarak kalır `GetURLContents` yöntem imzası ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="1593f-204">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="1593f-205">Kullanabileceğiniz `await` ile işaretlenmiş yöntemleri işlecinde [zaman uyumsuz](../../../../csharp/language-reference/keywords/async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="1593f-205">You can use the `await` operator only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="1593f-206">Yöntemi olarak işaretlemek için değiştiricisi eklemek bir *async yöntemi*, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="1593f-206">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>  
  
    ```csharp  
    private async byte[] GetURLContents(string url)  
    ```  
  
5.  <span data-ttu-id="1593f-207">Bir zaman uyumsuz yöntemin dönüş türünü yalnızca olabilir <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, veya `void` C#.</span><span class="sxs-lookup"><span data-stu-id="1593f-207">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or `void` in C#.</span></span> <span data-ttu-id="1593f-208">Genellikle, dönüş türü `void` yalnızca bir zaman uyumsuz olay işleyicisi, kullanılan nerede `void` gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1593f-208">Typically, a return type of `void` is used only in an async event handler, where `void` is required.</span></span> <span data-ttu-id="1593f-209">Diğer durumlarda, kullandığınız `Task(T)` tamamlanmış yöntemi varsa bir [dönmek](../../../../csharp/language-reference/keywords/return.md) T değeri döndüren ifadesi yazın ve kullandığınız `Task` tamamlanmış yöntemi anlamlı bir değere döndürmezse.</span><span class="sxs-lookup"><span data-stu-id="1593f-209">In other cases, you use `Task(T)` if the completed method has a [return](../../../../csharp/language-reference/keywords/return.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span> <span data-ttu-id="1593f-210">Düşünebilirsiniz `Task` dönüş türü olarak "Task(void)." anlamına gelir</span><span class="sxs-lookup"><span data-stu-id="1593f-210">You can think of the `Task` return type as meaning "Task(void)."</span></span>  
  
     <span data-ttu-id="1593f-211">Daha fazla bilgi için bkz: [zaman uyumsuz dönüş türleri (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="1593f-211">For more information, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
     <span data-ttu-id="1593f-212">Yöntem `GetURLContents` bir dönüş ifadesi içeriyor ve deyim bir bayt dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="1593f-212">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="1593f-213">Bu nedenle, zaman uyumsuz sürümü dönüş türü T bir bayt dizisi olduğu Task(T) ' dir.</span><span class="sxs-lookup"><span data-stu-id="1593f-213">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="1593f-214">Yöntem imzası aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="1593f-214">Make the following changes in the method signature:</span></span>  
  
    -   <span data-ttu-id="1593f-215">Dönüş türünü değiştir `Task<byte[]>`.</span><span class="sxs-lookup"><span data-stu-id="1593f-215">Change the return type to `Task<byte[]>`.</span></span>  
  
    -   <span data-ttu-id="1593f-216">Kurala göre zaman uyumsuz yöntemleri "Zaman uyumsuz," bitiş adlara sahip şekilde yöntemi yeniden adlandırma `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="1593f-216">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>  
  
     <span data-ttu-id="1593f-217">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="1593f-217">The following code shows these changes.</span></span>  
  
    ```csharp  
    private async Task<byte[]> GetURLContentsAsync(string url)  
    ```  
  
     <span data-ttu-id="1593f-218">Dönüştürme işlemi birkaç bu değişikliklerle `GetURLContents` zaman uyumsuz bir yöntem tamamlandığında.</span><span class="sxs-lookup"><span data-stu-id="1593f-218">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <a name="SumPageSizes"></a> <span data-ttu-id="1593f-219">Zaman uyumsuz bir yöntem SumPageSizes dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="1593f-219">To convert SumPageSizes to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="1593f-220">İçin önceki yordamdaki adımları yineleyin `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="1593f-220">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="1593f-221">İlk olarak, araması olarak değiştirmelerine `GetURLContents` zaman uyumsuz bir çağrı için.</span><span class="sxs-lookup"><span data-stu-id="1593f-221">First, change the call to `GetURLContents` to an asynchronous call.</span></span>  
  
    -   <span data-ttu-id="1593f-222">Yönteminden çağrılan yöntemin adını değiştirmek `GetURLContents` için `GetURLContentsAsync`, zaten yapmadıysanız.</span><span class="sxs-lookup"><span data-stu-id="1593f-222">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>  
  
    -   <span data-ttu-id="1593f-223">Uygulama `await` göreve, `GetURLContentsAsync` bayt edinme döndürür dizi değeri.</span><span class="sxs-lookup"><span data-stu-id="1593f-223">Apply `await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>  
  
     <span data-ttu-id="1593f-224">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="1593f-224">The following code shows these changes.</span></span>  
  
    ```csharp  
    byte[] urlContents = await GetURLContentsAsync(url);  
    ```  
  
     <span data-ttu-id="1593f-225">Önceki atama kod aşağıdaki iki satırı kısaltmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1593f-225">The previous assignment abbreviates the following two lines of code.</span></span>  
  
    ```csharp  
    // GetURLContentsAsync returns a Task<T>. At completion, the task  
    // produces a byte array.  
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
    //byte[] urlContents = await getContentsTask;  
    ```  
  
2.  <span data-ttu-id="1593f-226">Yöntemin imzada aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="1593f-226">Make the following changes in the method's signature:</span></span>  
  
    -   <span data-ttu-id="1593f-227">Yöntemiyle işaretlemek `async` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="1593f-227">Mark the method with the `async` modifier.</span></span>  
  
    -   <span data-ttu-id="1593f-228">"Zaman uyumsuz" yöntem adını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1593f-228">Add "Async" to the method name.</span></span>  
  
    -   <span data-ttu-id="1593f-229">T, hiçbir görev dönüş değişkeni bu süresi yoktur çünkü `SumPageSizesAsync` T. için bir değer döndürmüyor (Yöntem sahip olmayan `return` deyimi.) Ancak, yöntem döndürmelidir bir `Task` bildirdiğimize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1593f-229">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="1593f-230">Bu nedenle, yöntemden dönüş türünü değiştirme `void` için `Task`.</span><span class="sxs-lookup"><span data-stu-id="1593f-230">Therefore, change the return type of the method from `void` to `Task`.</span></span>  
  
     <span data-ttu-id="1593f-231">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="1593f-231">The following code shows these changes.</span></span>  
  
    ```csharp  
    private async Task SumPageSizesAsync()  
    ```  
  
     <span data-ttu-id="1593f-232">Dönüştürülmesi `SumPageSizes` için `SumPageSizesAsync` tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="1593f-232">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <a name="startButton"></a> <span data-ttu-id="1593f-233">Zaman uyumsuz bir yöntem startButton_Click dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="1593f-233">To convert startButton_Click to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="1593f-234">Olay işleyicisinin çağrılan yöntemin adını değiştirmek `SumPageSizes` için `SumPageSizesAsync`, zaten yapmadıysanız.</span><span class="sxs-lookup"><span data-stu-id="1593f-234">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>  
  
2.  <span data-ttu-id="1593f-235">Çünkü `SumPageSizesAsync` bir zaman uyumsuz yöntem sonucu beklemek için olay işleyicisini kodda değişiklik.</span><span class="sxs-lookup"><span data-stu-id="1593f-235">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>  
  
     <span data-ttu-id="1593f-236">Çağrı `SumPageSizesAsync` çağrısı yansıtan `CopyToAsync` içinde `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="1593f-236">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="1593f-237">Çağrı döndürür bir `Task`değil bir `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="1593f-237">The call returns a `Task`, not a `Task(T)`.</span></span>  
  
     <span data-ttu-id="1593f-238">Önceki yordamları olduğu gibi bir deyim veya iki deyimleri kullanarak çağrı dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1593f-238">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="1593f-239">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="1593f-239">The following code shows these changes.</span></span>  
  
    ```csharp  
    // One-step async call.  
    await SumPageSizesAsync();  
  
    // Two-step async call.  
    //Task sumTask = SumPageSizesAsync();  
    //await sumTask;  
    ```  
  
3.  <span data-ttu-id="1593f-240">Yanlışlıkla işlemi yeniden girme önlemek için aşağıdaki en üstünde deyimine `startButton_Click` devre dışı bırakmak için **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1593f-240">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>  
  
    ```csharp  
    // Disable the button until the operation is complete.  
    startButton.IsEnabled = false;  
    ```  
  
     <span data-ttu-id="1593f-241">Olay işleyicisinin sonunda düğmesini yeniden etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1593f-241">You can reenable the button at the end of the event handler.</span></span>  
  
    ```csharp  
    // Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = true;  
    ```  
  
     <span data-ttu-id="1593f-242">Yeniden giriş hakkında daha fazla bilgi için bkz: [zaman uyumsuz uygulamalarda (C#) yeniden girişi işleme](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="1593f-242">For more information about reentrancy, see [Handling Reentrancy in Async Apps (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>  
  
4.  <span data-ttu-id="1593f-243">Son olarak, ekleme `async` bildirimine değiştiricisi böylece olay işleyicisi await `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="1593f-243">Finally, add the `async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>  
  
    ```csharp  
    private async void startButton_Click(object sender, RoutedEventArgs e)  
    ```  
  
     <span data-ttu-id="1593f-244">Olay işleyicileri adları genellikle değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="1593f-244">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="1593f-245">Dönüş türü için değiştirilmez `Task` olay işleyicileri dönüştürüldüğünden `void`.</span><span class="sxs-lookup"><span data-stu-id="1593f-245">The return type isn’t changed to `Task` because event handlers must return `void`.</span></span>  
  
     <span data-ttu-id="1593f-246">Proje dönüştürme için zaman uyumsuz zaman uyumlu işleme işlemi tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="1593f-246">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <a name="testAsynch"></a> <span data-ttu-id="1593f-247">Zaman uyumsuz çözümü test etmek için</span><span class="sxs-lookup"><span data-stu-id="1593f-247">To test the asynchronous solution</span></span>  
  
1.  <span data-ttu-id="1593f-248">Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1593f-248">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
2.  <span data-ttu-id="1593f-249">Zaman uyumlu çözüm çıktısını benzer bir çıktı görüntülenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1593f-249">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="1593f-250">Ancak, aşağıdaki farkları dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1593f-250">However, notice the following differences.</span></span>  
  
    -   <span data-ttu-id="1593f-251">Sonuçları tüm işleme işlemi tamamlandıktan sonra aynı anda oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="1593f-251">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="1593f-252">Örneğin, her iki programı bir satır içeren `startButton_Click` metin kutusu temizler.</span><span class="sxs-lookup"><span data-stu-id="1593f-252">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="1593f-253">Seçerseniz çalıştırmaları arasında metin kutusu temizlemek için amacı olan **Başlat** bir sonuç kümesi göründükten sonra ikinci bir kez düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1593f-253">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="1593f-254">Yalnızca sayıları zaman indirmeleri tamamlandı ve diğer iş yapmak kullanıcı Arabirimi iş parçacığı ücretsizdir ikinci kez görünmesi zaman uyumlu bir sürümde metin kutusu işaretli değildir.</span><span class="sxs-lookup"><span data-stu-id="1593f-254">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="1593f-255">Seçtiğiniz hemen sonra metin kutusuna zaman uyumsuz bir sürümde temizler **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1593f-255">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>  
  
    -   <span data-ttu-id="1593f-256">En önemlisi, kullanıcı Arabirimi iş parçacığı yüklemeleri sırasında engellenmiş değil.</span><span class="sxs-lookup"><span data-stu-id="1593f-256">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="1593f-257">Taşıma veya web kaynakları karşıdan yüklenirken pencereyi yeniden boyutlandırmak sayılan ve görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1593f-257">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="1593f-258">Web sitelerinden birini yavaş veya yanıt vermiyor işlemi seçerek iptal edebilir **Kapat** düğmesi (sağ üst köşesinde kırmızı alanında x).</span><span class="sxs-lookup"><span data-stu-id="1593f-258">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <a name="GetURLContentsAsync"></a> <span data-ttu-id="1593f-259">.NET Framework yöntemiyle yöntemi GetURLContentsAsync değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="1593f-259">To replace method GetURLContentsAsync with a .NET Framework method</span></span>  
  
1.  <span data-ttu-id="1593f-260">.NET Framework 4.5 kullanabileceğiniz birçok zaman uyumsuz yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1593f-260">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="1593f-261">Bunlardan biri <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, bu kılavuz için gerekenler yalnızca yapar.</span><span class="sxs-lookup"><span data-stu-id="1593f-261">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="1593f-262">Bunun yerine kullanabileceğiniz `GetURLContentsAsync` bir önceki yordamda oluşturduğunuz yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1593f-262">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>  
  
     <span data-ttu-id="1593f-263">İlk adım oluşturmaktır bir `HttpClient` yöntemi nesnesinde `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="1593f-263">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="1593f-264">Aşağıdaki bildirimi yöntemi başlangıcında ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1593f-264">Add the following declaration at the start of the method.</span></span>  
  
    ```csharp  
    // Declare an HttpClient object and increase the buffer size. The  
    // default buffer size is 65,536.  
    HttpClient client =  
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
    ```  
  
2.  <span data-ttu-id="1593f-265">İçinde `SumPageSizesAsync,` çağrısı değiştirin, `GetURLContentsAsync` çağrısıyla yöntemi `HttpClient` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1593f-265">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>  
  
    ```csharp  
    byte[] urlContents = await client.GetByteArrayAsync(url);  
    ```  
  
3.  <span data-ttu-id="1593f-266">Kaldırın veya çıkışı açıklama `GetURLContentsAsync` yazdığınız yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1593f-266">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>  
  
4.  <span data-ttu-id="1593f-267">Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1593f-267">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="1593f-268">Bu projenin sürümü davranışını "zaman uyumsuz çözümü test etmek için" yordamı açıklanan davranışı eşleşen ancak sizden daha az çaba ile bile gerekir.</span><span class="sxs-lookup"><span data-stu-id="1593f-268">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>  
  
##  <a name="BKMK_CompleteCodeExamples"></a> <span data-ttu-id="1593f-269">Örnek</span><span class="sxs-lookup"><span data-stu-id="1593f-269">Example</span></span>  
 <span data-ttu-id="1593f-270">Aşağıdaki kod dönüştürme eş zamanlı işlemini zaman uyumsuz bir çözüm için tam örnek içeriyor zaman uyumsuz kullanarak `GetURLContentsAsync` yazdığınız yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1593f-270">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="1593f-271">Bunu kesinlikle özgün, zaman uyumlu çözüm benzer dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1593f-271">Notice that it strongly resembles the original, synchronous solution.</span></span>  
  
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
  
 <span data-ttu-id="1593f-272">Aşağıdaki kodu kullanan çözüm tam örneği içerir `HttpClient` yöntemi, `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="1593f-272">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1593f-273">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1593f-273">See Also</span></span>  
 [<span data-ttu-id="1593f-274">Zaman uyumsuz örnek: Web gözden geçirme (C# ve Visual Basic) erişme</span><span class="sxs-lookup"><span data-stu-id="1593f-274">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)  
 [<span data-ttu-id="1593f-275">async</span><span class="sxs-lookup"><span data-stu-id="1593f-275">async</span></span>](../../../../csharp/language-reference/keywords/async.md)  
 [<span data-ttu-id="1593f-276">await</span><span class="sxs-lookup"><span data-stu-id="1593f-276">await</span></span>](../../../../csharp/language-reference/keywords/await.md)  
 [<span data-ttu-id="1593f-277">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="1593f-277">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="1593f-278">Zaman uyumsuz dönüş türleri (C#)</span><span class="sxs-lookup"><span data-stu-id="1593f-278">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="1593f-279">Görev tabanlı zaman uyumsuz programlama (TAP)</span><span class="sxs-lookup"><span data-stu-id="1593f-279">Task-based Asynchronous Programming (TAP)</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=19957)  
 [<span data-ttu-id="1593f-280">Nasıl yapılır: Task.WhenAll (C#) kullanarak tarafından izlenecek zaman uyumsuz genişletme</span><span class="sxs-lookup"><span data-stu-id="1593f-280">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)  
 [<span data-ttu-id="1593f-281">Nasıl yapılır: birden çok Web isteğini paralel olarak zaman uyumsuz kullanarak ve olun await (C#)</span><span class="sxs-lookup"><span data-stu-id="1593f-281">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
