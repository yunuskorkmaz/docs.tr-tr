---
title: "İzlenecek yol: async kullanarak Web'e erişme ve await (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: get-started-article
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 85edc87bc8c5183f85618351034c0b043472b530
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a><span data-ttu-id="f7d11-102">İzlenecek yol: async kullanarak Web'e erişme ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="f7d11-102">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>
<span data-ttu-id="f7d11-103">Zaman uyumsuz ve bekleme özelliklerini kullanarak zaman uyumsuz programlar daha kolay ve sezgisel yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7d11-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="f7d11-104">Zaman uyumlu kod gibi görünüyor zaman uyumsuz kod yazın ve daha zor geri arama işlevleri ve zaman uyumsuz kod genellikle kapsar devamlılıklar işlemek derleyici sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7d11-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>  
  
 <span data-ttu-id="f7d11-105">Async özelliği hakkında daha fazla bilgi için bkz: [zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="f7d11-105">For more information about the Async feature, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="f7d11-106">Bu kılavuzda Web sitelerinin bir listesiyle bayt sayısını toplar zaman uyumlu bir Windows Presentation Foundation (WPF) uygulama başlar.</span><span class="sxs-lookup"><span data-stu-id="f7d11-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="f7d11-107">İzlenecek yol sonra yeni özellikleri kullanarak zaman uyumsuz çözümünü uygulamaya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f7d11-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>  
  
 <span data-ttu-id="f7d11-108">Uygulamaları kendiniz yapılandırmak istemiyorsanız, indirebilirsiniz "zaman uyumsuz örnek: Web gözden geçirme (C# ve Visual Basic) erişme" den [Geliştirici kod örnekleri](http://go.microsoft.com/fwlink/?LinkId=255191).</span><span class="sxs-lookup"><span data-stu-id="f7d11-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191).</span></span>  
  
 <span data-ttu-id="f7d11-109">Bu kılavuzda, aşağıdaki görevleri tamamlayın:</span><span class="sxs-lookup"><span data-stu-id="f7d11-109">In this walkthrough, you complete the following tasks:</span></span>  
  
-   [<span data-ttu-id="f7d11-110">Bir WPF uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f7d11-110">To create a WPF application</span></span>](#CreateWPFApp)  
  
-   [<span data-ttu-id="f7d11-111">Basit bir WPF MainWindow tasarlamak için</span><span class="sxs-lookup"><span data-stu-id="f7d11-111">To design a simple WPF MainWindow</span></span>](#MainWindow)  
  
-   [<span data-ttu-id="f7d11-112">Bir başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="f7d11-112">To add a reference</span></span>](#AddRef)  
  
-   [<span data-ttu-id="f7d11-113">Eklemek için gerekli yönergeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="f7d11-113">To add necessary using directives</span></span>](#usingDir)  
  
-   [<span data-ttu-id="f7d11-114">Zaman uyumlu bir uygulama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f7d11-114">To create a synchronous application</span></span>](#synchronous)  
  
-   [<span data-ttu-id="f7d11-115">Zaman uyumlu çözümü test etmek için</span><span class="sxs-lookup"><span data-stu-id="f7d11-115">To test the synchronous solution</span></span>](#testSynch)  
  
-   [<span data-ttu-id="f7d11-116">Zaman uyumsuz bir yöntem GetURLContents dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="f7d11-116">To convert GetURLContents to an asynchronous method</span></span>](#GetURLContents)  
  
-   [<span data-ttu-id="f7d11-117">Zaman uyumsuz bir yöntem SumPageSizes dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="f7d11-117">To convert SumPageSizes to an asynchronous method</span></span>](#SumPageSizes)  
  
-   [<span data-ttu-id="f7d11-118">Zaman uyumsuz bir yöntem startButton_Click dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="f7d11-118">To convert startButton_Click to an asynchronous method</span></span>](#startButton)  
  
-   [<span data-ttu-id="f7d11-119">Zaman uyumsuz çözümü test etmek için</span><span class="sxs-lookup"><span data-stu-id="f7d11-119">To test the asynchronous solution</span></span>](#testAsynch)  
  
-   [<span data-ttu-id="f7d11-120">.NET Framework yöntemiyle yöntemi GetURLContentsAsync değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="f7d11-120">To replace method GetURLContentsAsync with a .NET Framework method</span></span>](#GetURLContentsAsync)  
  
-   [<span data-ttu-id="f7d11-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7d11-121">Example</span></span>](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a><span data-ttu-id="f7d11-122">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="f7d11-122">Prerequisites</span></span>  
 <span data-ttu-id="f7d11-123">Visual Studio 2012 veya sonraki sürümünü bilgisayarınızda yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7d11-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="f7d11-124">Daha fazla bilgi için bkz: [Microsoft Web sitesi](http://go.microsoft.com/fwlink/?LinkId=235233).</span><span class="sxs-lookup"><span data-stu-id="f7d11-124">For more information, see the [Microsoft website](http://go.microsoft.com/fwlink/?LinkId=235233).</span></span>  
  
###  <a name="CreateWPFApp"></a><span data-ttu-id="f7d11-125">Bir WPF uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f7d11-125">To create a WPF application</span></span>  
  
1.  <span data-ttu-id="f7d11-126">Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="f7d11-126">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="f7d11-127">Menü çubuğunda seçin **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="f7d11-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="f7d11-128">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="f7d11-128">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="f7d11-129">İçinde **yüklü şablonlar** bölmesinde, Visual C# ' ı seçin ve ardından **WPF uygulaması** proje türleri listesinden.</span><span class="sxs-lookup"><span data-stu-id="f7d11-129">In the **Installed Templates** pane, choose Visual C#, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="f7d11-130">İçinde **adı** metin kutusuna `AsyncExampleWPF`ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="f7d11-131">Yeni Proje görünür **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="f7d11-131">The new project appears in **Solution Explorer**.</span></span>  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <a name="MainWindow"></a><span data-ttu-id="f7d11-132">Basit bir WPF MainWindow tasarlamak için</span><span class="sxs-lookup"><span data-stu-id="f7d11-132">To design a simple WPF MainWindow</span></span>  
  
1.  <span data-ttu-id="f7d11-133">Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
2.  <span data-ttu-id="f7d11-134">Varsa **araç** pencere görünür, açık olmayan **Görünüm** menüsünde ve ardından **araç**.</span><span class="sxs-lookup"><span data-stu-id="f7d11-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="f7d11-135">Ekleme bir **düğmesini** denetim ve **TextBox** denetimini **MainWindow** penceresi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>  
  
4.  <span data-ttu-id="f7d11-136">Vurgula **TextBox** denetim hem de **özellikleri** penceresinde, aşağıdaki değerleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="f7d11-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="f7d11-137">Ayarlama **adı** özelliğine `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="f7d11-137">Set the **Name** property to `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="f7d11-138">Ayarlama **yükseklik** 250 özelliğine.</span><span class="sxs-lookup"><span data-stu-id="f7d11-138">Set the **Height** property to 250.</span></span>  
  
    -   <span data-ttu-id="f7d11-139">Ayarlama **genişliği** 500 özelliği.</span><span class="sxs-lookup"><span data-stu-id="f7d11-139">Set the **Width** property to 500.</span></span>  
  
    -   <span data-ttu-id="f7d11-140">Üzerinde **metin** sekmesinde, Lucida Console veya genel tek aralıklı gibi aralıklı bir yazı tipi belirtin.</span><span class="sxs-lookup"><span data-stu-id="f7d11-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>  
  
5.  <span data-ttu-id="f7d11-141">Vurgula **düğmesini** denetim hem de **özellikleri** penceresinde, aşağıdaki değerleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="f7d11-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="f7d11-142">Ayarlama **adı** özelliğine `startButton`.</span><span class="sxs-lookup"><span data-stu-id="f7d11-142">Set the **Name** property to `startButton`.</span></span>  
  
    -   <span data-ttu-id="f7d11-143">Değerini değiştirme **içerik** özelliğinden **düğmesini** için **Başlat**.</span><span class="sxs-lookup"><span data-stu-id="f7d11-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>  
  
6.  <span data-ttu-id="f7d11-144">Her ikisi de görünmesini sağlayacak şekilde, metin kutusu ve düğmesi konum **MainWindow** penceresi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>  
  
     <span data-ttu-id="f7d11-145">WPF XAML Tasarımcısı hakkında daha fazla bilgi için bkz: [XAML Tasarımcısını kullanarak bir kullanıcı Arabirimi oluşturma](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="f7d11-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>  
  
##  <a name="BKMK_AddReference"></a>   
###  <a name="AddRef"></a><span data-ttu-id="f7d11-146">Bir başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="f7d11-146">To add a reference</span></span>  
  
1.  <span data-ttu-id="f7d11-147">İçinde **Çözüm Gezgini**, projenizin adını vurgulayın.</span><span class="sxs-lookup"><span data-stu-id="f7d11-147">In **Solution Explorer**, highlight your project's name.</span></span>  
  
2.  <span data-ttu-id="f7d11-148">Menü çubuğunda seçin **proje**, **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="f7d11-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="f7d11-149">**Başvuru Yöneticisi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f7d11-149">The **Reference Manager** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="f7d11-150">İletişim kutusunun üstündeki projeniz .NET Framework 4.5 veya üstünü hedefleyen olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="f7d11-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>  
  
4.  <span data-ttu-id="f7d11-151">İçinde **derlemeleri** alanı seçin **Framework** tercih değil.</span><span class="sxs-lookup"><span data-stu-id="f7d11-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
5.  <span data-ttu-id="f7d11-152">Adları listesinden seçin **System.Net.Http** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="f7d11-152">In the list of names, select the **System.Net.Http** check box.</span></span>  
  
6.  <span data-ttu-id="f7d11-153">Seçin **Tamam** düğmesi iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="f7d11-153">Choose the **OK** button to close the dialog box.</span></span>  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <a name="usingDir"></a><span data-ttu-id="f7d11-154">Eklemek için gerekli yönergeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="f7d11-154">To add necessary using directives</span></span>  
  
1.  <span data-ttu-id="f7d11-155">İçinde **Çözüm Gezgini**MainWindow.xaml.cs için kısayol menüsünü açın ve ardından **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="f7d11-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="f7d11-156">Aşağıdakileri ekleyin `using` zaten mevcut değillerse kod dosyasının üst yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="f7d11-156">Add the following `using` directives at the top of the code file if they’re not already present.</span></span>  
  
    ```csharp  
    using System.Net.Http;  
    using System.Net;  
    using System.IO;  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <a name="synchronous"></a><span data-ttu-id="f7d11-157">Zaman uyumlu bir uygulama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f7d11-157">To create a synchronous application</span></span>  
  
1.  <span data-ttu-id="f7d11-158">Tasarım penceresinde MainWindow.xaml, çift **Başlat** oluşturmak için düğmesini `startButton_Click` MainWindow.xaml.cs olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2.  <span data-ttu-id="f7d11-159">MainWindow.xaml.cs içinde gövdesine aşağıdaki kodu kopyalayın `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="f7d11-159">In MainWindow.xaml.cs, copy the following code into the body of `startButton_Click`:</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    SumPageSizes();  
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";  
    ```  
  
     <span data-ttu-id="f7d11-160">Kod uygulama sürücüleri yöntemini çağırır `SumPageSizes`ve denetim döndüğünde bir ileti görüntüler `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="f7d11-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>  
  
3.  <span data-ttu-id="f7d11-161">Zaman uyumlu çözüm için kod aşağıdaki dört yöntemi içerir:</span><span class="sxs-lookup"><span data-stu-id="f7d11-161">The code for the synchronous solution contains the following four methods:</span></span>  
  
    -   <span data-ttu-id="f7d11-162">`SumPageSizes`, Web sayfası URL'lerden listesini alır `SetUpURLList` ve çağırır `GetURLContents` ve `DisplayResults` her URL işleyemedi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>  
  
    -   <span data-ttu-id="f7d11-163">`SetUpURLList`, hangi yapar ve web adresleri listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7d11-163">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>  
  
    -   <span data-ttu-id="f7d11-164">`GetURLContents`, her Web sitesi içeriğini indirir ve içeriği bir bayt dizisi olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7d11-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>  
  
    -   <span data-ttu-id="f7d11-165">`DisplayResults`, görüntüleyen bayt sayısı bayt dizisi, her URL için.</span><span class="sxs-lookup"><span data-stu-id="f7d11-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>  
  
     <span data-ttu-id="f7d11-166">Aşağıdaki dört yöntemi kopyalayın ve yapıştırın altında `startButton_Click` MainWindow.xaml.cs olay işleyicisi:</span><span class="sxs-lookup"><span data-stu-id="f7d11-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.cs:</span></span>  
  
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
###  <a name="testSynch"></a><span data-ttu-id="f7d11-167">Zaman uyumlu çözümü test etmek için</span><span class="sxs-lookup"><span data-stu-id="f7d11-167">To test the synchronous solution</span></span>  
  
1.  <span data-ttu-id="f7d11-168">Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="f7d11-169">Aşağıdaki listede benzer bir çıktı görüntülenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7d11-169">Output that resembles the following list should appear.</span></span>  
  
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
  
     <span data-ttu-id="f7d11-170">Sayıları görüntülemek için birkaç saniye sürer dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f7d11-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="f7d11-171">İstenen kaynaklar indirmek beklerken bu süre içinde kullanıcı Arabirimi iş parçacığı engellendi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="f7d11-172">Sonuç olarak, taşıyamazsınız, en üst düzeye çıkarmak, simge durumuna küçült veya seçtiğiniz sonra bile görüntü penceresini kapatın **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="f7d11-173">Görüntülenecek bayt sayıları başlatana kadar bu çaba başarısız.</span><span class="sxs-lookup"><span data-stu-id="f7d11-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="f7d11-174">Bir Web sitesi yanıt vermiyor gösterge olmadan başarısız hangi sitenin varsa.</span><span class="sxs-lookup"><span data-stu-id="f7d11-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="f7d11-175">Hatta bekleme durdurmak ve program kapatmak zordur.</span><span class="sxs-lookup"><span data-stu-id="f7d11-175">It is difficult even to stop waiting and close the program.</span></span>  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <a name="GetURLContents"></a><span data-ttu-id="f7d11-176">Zaman uyumsuz bir yöntem GetURLContents dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="f7d11-176">To convert GetURLContents to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="f7d11-177">Zaman uyumsuz bir çözüme zaman uyumlu çözüm dönüştürmek için başlatmak için en iyi yerdir bulunduğu `GetURLContents` çünkü çağrıları <xref:System.Net.HttpWebRequest> yöntemi <xref:System.Net.HttpWebRequest.GetResponse%2A> ve <xref:System.IO.Stream> yöntemi <xref:System.IO.Stream.CopyTo%2A> burada web uygulama erişen olan .</span><span class="sxs-lookup"><span data-stu-id="f7d11-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="f7d11-178">.NET Framework dönüştürme her iki yöntem zaman uyumsuz sürümlerini sağlayarak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="f7d11-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>  
  
     <span data-ttu-id="f7d11-179">Kullanılan yöntemleri hakkında daha fazla bilgi için `GetURLContents`, bkz: <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="f7d11-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f7d11-180">Bu izlenecek adımları izlediğiniz gibi birkaç derleyici hataları görünür.</span><span class="sxs-lookup"><span data-stu-id="f7d11-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="f7d11-181">Bunları yoksay ve kılavuz ile devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7d11-181">You can ignore them and continue with the walkthrough.</span></span>  
  
     <span data-ttu-id="f7d11-182">Üçüncü satırında adlı yöntemini değiştirme `GetURLContents` gelen `GetResponse` için zaman uyumsuz, görev tabanlı <xref:System.Net.WebRequest.GetResponseAsync%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>  
  
    ```csharp  
    using (WebResponse response = webReq.GetResponseAsync())  
    ```  
  
2.  <span data-ttu-id="f7d11-183">`GetResponseAsync`döndüren bir <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="f7d11-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="f7d11-184">Bu durumda, *görev dönüş değişkeni*, `TResult`, türüne sahip <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="f7d11-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="f7d11-185">Gerçek bir üretmek için promise görevdir `WebResponse` istenen veri indirilir ve görevin tamamlanması çalıştıktan sonra nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>  
  
     <span data-ttu-id="f7d11-186">Alınacak `WebResponse` görevden değer, geçerli bir [await](../../../../csharp/language-reference/keywords/await.md) çağrısına işleci `GetResponseAsync`, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-186">To retrieve the `WebResponse` value from the task, apply an [await](../../../../csharp/language-reference/keywords/await.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>  
  
    ```csharp  
    using (WebResponse response = await webReq.GetResponseAsync())  
    ```  
  
     <span data-ttu-id="f7d11-187">`await` İşleci geçerli yönteminin yürütülmesi askıya `GetURLContents`, awaited görevi tamamlanana kadar.</span><span class="sxs-lookup"><span data-stu-id="f7d11-187">The `await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="f7d11-188">Bu arada, denetim geçerli yöntemi çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7d11-188">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="f7d11-189">Bu örnekte, geçerli bir yöntemdir `GetURLContents`, ve çağrıyı yapan `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="f7d11-189">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="f7d11-190">Görev tamamlandığında taahhüt `WebResponse` nesne awaited görev değeri olarak üretilen ve değişkenine atanan `response`.</span><span class="sxs-lookup"><span data-stu-id="f7d11-190">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>  
  
     <span data-ttu-id="f7d11-191">Önceki deyimi ne olacağını açıklamak için aşağıdaki iki deyime ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7d11-191">The previous statement can be separated into the following two statements to clarify what happens.</span></span>  
  
    ```csharp  
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();  
    //using (WebResponse response = await responseTask)  
    ```  
  
     <span data-ttu-id="f7d11-192">Çağrı `webReq.GetResponseAsync` döndüren bir `Task(Of WebResponse)` veya `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="f7d11-192">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="f7d11-193">Görevi almak için bir bekleme işleç uygulanan sonra `WebResponse` değeri.</span><span class="sxs-lookup"><span data-stu-id="f7d11-193">Then an await operator is applied to the task to retrieve the `WebResponse` value.</span></span>  
  
     <span data-ttu-id="f7d11-194">Zaman uyumsuz yöntem görev tamamlanma bağımlı değil yapmak için iş varsa, yöntemi zaman uyumsuz yöntem ve önce çağrısından sonra bu iki ifade arasındaki, iş ile devam edebilirsiniz `await` işleci uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f7d11-194">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the `await` operator is applied.</span></span> <span data-ttu-id="f7d11-195">Örnekler için bkz [nasıl yapılır: zaman uyumsuz kullanarak birden çok Web isteğini paralel hale ve await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) ve [nasıl yapılır: Task.WhenAll kullanarak (C#) tarafından izlenecek zaman uyumsuz genişletmek](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="f7d11-195">For examples, see [How to: Make Multiple Web Requests in Parallel by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
3.  <span data-ttu-id="f7d11-196">Eklediğiniz çünkü `await` işleci önceki adımda, bir derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="f7d11-196">Because you added the `await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="f7d11-197">İşleç ile işaretlenmiş yöntemleri kullanılabilir [zaman uyumsuz](../../../../csharp/language-reference/keywords/async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-197">The operator can be used only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="f7d11-198">Çağrı değiştirmek için dönüştürme adımları yineleyin sırada hatayı yok sayıp `CopyTo` çağrısıyla `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="f7d11-198">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>  
  
    -   <span data-ttu-id="f7d11-199">İçin çağrılan yöntemin adını değiştirmek <xref:System.IO.Stream.CopyToAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="f7d11-199">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>  
  
    -   <span data-ttu-id="f7d11-200">`CopyTo` Veya `CopyToAsync` yöntemi için bağımsız değişkeni, bayt kopyalar `content`ve anlamlı bir değer döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="f7d11-200">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="f7d11-201">Zaman uyumlu sürümünde, çağrısı `CopyTo` bir değer döndürmüyor basit bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="f7d11-201">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="f7d11-202">Zaman uyumsuz sürümü `CopyToAsync`, döndüren bir <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="f7d11-202">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="f7d11-203">Görev "Task(void)" gibi çalışır ve yöntem beklemenin sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7d11-203">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="f7d11-204">Uygulama `Await` veya `await` çağrısına `CopyToAsync`, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-204">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>  
  
        ```csharp  
        await responseStream.CopyToAsync(content);  
        ```  
  
         <span data-ttu-id="f7d11-205">Önceki deyimi aşağıdaki iki kod satırı kısaltmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7d11-205">The previous statement abbreviates the following two lines of code.</span></span>  
  
        ```csharp  
        // CopyToAsync returns a Task, not a Task<T>.  
        //Task copyTask = responseStream.CopyToAsync(content);  
  
        // When copyTask is completed, content contains a copy of  
        // responseStream.  
        //await copyTask;  
        ```  
  
4.  <span data-ttu-id="f7d11-206">Tüm bu tamamlandı olarak kalır `GetURLContents` yöntem imzası ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="f7d11-206">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="f7d11-207">Kullanabileceğiniz `await` ile işaretlenmiş yöntemleri işlecinde [zaman uyumsuz](../../../../csharp/language-reference/keywords/async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-207">You can use the `await` operator only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="f7d11-208">Yöntemi olarak işaretlemek için değiştiricisi eklemek bir *async yöntemi*, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-208">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>  
  
    ```csharp  
    private async byte[] GetURLContents(string url)  
    ```  
  
5.  <span data-ttu-id="f7d11-209">Bir zaman uyumsuz yöntemin dönüş türünü yalnızca olabilir <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, veya `void` C#.</span><span class="sxs-lookup"><span data-stu-id="f7d11-209">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or `void` in C#.</span></span> <span data-ttu-id="f7d11-210">Genellikle, dönüş türü `void` yalnızca bir zaman uyumsuz olay işleyicisi, kullanılan nerede `void` gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f7d11-210">Typically, a return type of `void` is used only in an async event handler, where `void` is required.</span></span> <span data-ttu-id="f7d11-211">Diğer durumlarda, kullandığınız `Task(T)` tamamlanmış yöntemi varsa bir [dönmek](../../../../csharp/language-reference/keywords/return.md) T değeri döndüren ifadesi yazın ve kullandığınız `Task` tamamlanmış yöntemi anlamlı bir değere döndürmezse.</span><span class="sxs-lookup"><span data-stu-id="f7d11-211">In other cases, you use `Task(T)` if the completed method has a [return](../../../../csharp/language-reference/keywords/return.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span> <span data-ttu-id="f7d11-212">Düşünebilirsiniz `Task` dönüş türü olarak "Task(void)." anlamına gelir</span><span class="sxs-lookup"><span data-stu-id="f7d11-212">You can think of the `Task` return type as meaning "Task(void)."</span></span>  
  
     <span data-ttu-id="f7d11-213">Daha fazla bilgi için bkz: [zaman uyumsuz dönüş türleri (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="f7d11-213">For more information, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
     <span data-ttu-id="f7d11-214">Yöntem `GetURLContents` bir dönüş ifadesi içeriyor ve deyim bir bayt dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7d11-214">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="f7d11-215">Bu nedenle, zaman uyumsuz sürümü dönüş türü T bir bayt dizisi olduğu Task(T) ' dir.</span><span class="sxs-lookup"><span data-stu-id="f7d11-215">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="f7d11-216">Yöntem imzası aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="f7d11-216">Make the following changes in the method signature:</span></span>  
  
    -   <span data-ttu-id="f7d11-217">Dönüş türünü değiştir `Task<byte[]>`.</span><span class="sxs-lookup"><span data-stu-id="f7d11-217">Change the return type to `Task<byte[]>`.</span></span>  
  
    -   <span data-ttu-id="f7d11-218">Kurala göre zaman uyumsuz yöntemleri "Zaman uyumsuz," bitiş adlara sahip şekilde yöntemi yeniden adlandırma `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="f7d11-218">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>  
  
     <span data-ttu-id="f7d11-219">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7d11-219">The following code shows these changes.</span></span>  
  
    ```csharp  
    private async Task<byte[]> GetURLContentsAsync(string url)  
    ```  
  
     <span data-ttu-id="f7d11-220">Dönüştürme işlemi birkaç bu değişikliklerle `GetURLContents` zaman uyumsuz bir yöntem tamamlandığında.</span><span class="sxs-lookup"><span data-stu-id="f7d11-220">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <a name="SumPageSizes"></a><span data-ttu-id="f7d11-221">Zaman uyumsuz bir yöntem SumPageSizes dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="f7d11-221">To convert SumPageSizes to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="f7d11-222">İçin önceki yordamdaki adımları yineleyin `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="f7d11-222">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="f7d11-223">İlk olarak, araması olarak değiştirmelerine `GetURLContents` zaman uyumsuz bir çağrı için.</span><span class="sxs-lookup"><span data-stu-id="f7d11-223">First, change the call to `GetURLContents` to an asynchronous call.</span></span>  
  
    -   <span data-ttu-id="f7d11-224">Yönteminden çağrılan yöntemin adını değiştirmek `GetURLContents` için `GetURLContentsAsync`, zaten yapmadıysanız.</span><span class="sxs-lookup"><span data-stu-id="f7d11-224">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>  
  
    -   <span data-ttu-id="f7d11-225">Uygulama `await` göreve, `GetURLContentsAsync` bayt edinme döndürür dizi değeri.</span><span class="sxs-lookup"><span data-stu-id="f7d11-225">Apply `await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>  
  
     <span data-ttu-id="f7d11-226">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7d11-226">The following code shows these changes.</span></span>  
  
    ```csharp  
    byte[] urlContents = await GetURLContentsAsync(url);  
    ```  
  
     <span data-ttu-id="f7d11-227">Önceki atama kod aşağıdaki iki satırı kısaltmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7d11-227">The previous assignment abbreviates the following two lines of code.</span></span>  
  
    ```csharp  
    // GetURLContentsAsync returns a Task<T>. At completion, the task  
    // produces a byte array.  
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
    //byte[] urlContents = await getContentsTask;  
    ```  
  
2.  <span data-ttu-id="f7d11-228">Yöntemin imzada aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="f7d11-228">Make the following changes in the method's signature:</span></span>  
  
    -   <span data-ttu-id="f7d11-229">Yöntemiyle işaretlemek `async` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-229">Mark the method with the `async` modifier.</span></span>  
  
    -   <span data-ttu-id="f7d11-230">"Zaman uyumsuz" yöntem adını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f7d11-230">Add "Async" to the method name.</span></span>  
  
    -   <span data-ttu-id="f7d11-231">T, hiçbir görev dönüş değişkeni bu süresi yoktur çünkü `SumPageSizesAsync` T. için bir değer döndürmüyor (Yöntem sahip olmayan `return` deyimi.) Ancak, yöntem döndürmelidir bir `Task` bildirdiğimize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7d11-231">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="f7d11-232">Bu nedenle, yöntemden dönüş türünü değiştirme `void` için `Task`.</span><span class="sxs-lookup"><span data-stu-id="f7d11-232">Therefore, change the return type of the method from `void` to `Task`.</span></span>  
  
     <span data-ttu-id="f7d11-233">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7d11-233">The following code shows these changes.</span></span>  
  
    ```csharp  
    private async Task SumPageSizesAsync()  
    ```  
  
     <span data-ttu-id="f7d11-234">Dönüştürülmesi `SumPageSizes` için `SumPageSizesAsync` tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="f7d11-234">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <a name="startButton"></a><span data-ttu-id="f7d11-235">Zaman uyumsuz bir yöntem startButton_Click dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="f7d11-235">To convert startButton_Click to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="f7d11-236">Olay işleyicisinin çağrılan yöntemin adını değiştirmek `SumPageSizes` için `SumPageSizesAsync`, zaten yapmadıysanız.</span><span class="sxs-lookup"><span data-stu-id="f7d11-236">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>  
  
2.  <span data-ttu-id="f7d11-237">Çünkü `SumPageSizesAsync` bir zaman uyumsuz yöntem sonucu beklemek için olay işleyicisini kodda değişiklik.</span><span class="sxs-lookup"><span data-stu-id="f7d11-237">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>  
  
     <span data-ttu-id="f7d11-238">Çağrı `SumPageSizesAsync` çağrısı yansıtan `CopyToAsync` içinde `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="f7d11-238">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="f7d11-239">Çağrı döndürür bir `Task`değil bir `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="f7d11-239">The call returns a `Task`, not a `Task(T)`.</span></span>  
  
     <span data-ttu-id="f7d11-240">Önceki yordamları olduğu gibi bir deyim veya iki deyimleri kullanarak çağrı dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7d11-240">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="f7d11-241">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7d11-241">The following code shows these changes.</span></span>  
  
    ```csharp  
    // One-step async call.  
    await SumPageSizesAsync();  
  
    // Two-step async call.  
    //Task sumTask = SumPageSizesAsync();  
    //await sumTask;  
    ```  
  
3.  <span data-ttu-id="f7d11-242">Yanlışlıkla işlemi yeniden girme önlemek için aşağıdaki en üstünde deyimine `startButton_Click` devre dışı bırakmak için **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-242">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>  
  
    ```csharp  
    // Disable the button until the operation is complete.  
    startButton.IsEnabled = false;  
    ```  
  
     <span data-ttu-id="f7d11-243">Olay işleyicisinin sonunda düğmesini yeniden etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7d11-243">You can reenable the button at the end of the event handler.</span></span>  
  
    ```csharp  
    // Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = true;  
    ```  
  
     <span data-ttu-id="f7d11-244">Yeniden giriş hakkında daha fazla bilgi için bkz: [zaman uyumsuz uygulamalarda (C#) yeniden girişi işleme](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="f7d11-244">For more information about reentrancy, see [Handling Reentrancy in Async Apps (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>  
  
4.  <span data-ttu-id="f7d11-245">Son olarak, ekleme `async` bildirimine değiştiricisi böylece olay işleyicisi await `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="f7d11-245">Finally, add the `async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>  
  
    ```csharp  
    private async void startButton_Click(object sender, RoutedEventArgs e)  
    ```  
  
     <span data-ttu-id="f7d11-246">Olay işleyicileri adları genellikle değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="f7d11-246">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="f7d11-247">Dönüş türü için değiştirilmez `Task` olay işleyicileri dönüştürüldüğünden `void`.</span><span class="sxs-lookup"><span data-stu-id="f7d11-247">The return type isn’t changed to `Task` because event handlers must return `void`.</span></span>  
  
     <span data-ttu-id="f7d11-248">Proje dönüştürme için zaman uyumsuz zaman uyumlu işleme işlemi tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="f7d11-248">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <a name="testAsynch"></a><span data-ttu-id="f7d11-249">Zaman uyumsuz çözümü test etmek için</span><span class="sxs-lookup"><span data-stu-id="f7d11-249">To test the asynchronous solution</span></span>  
  
1.  <span data-ttu-id="f7d11-250">Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-250">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
2.  <span data-ttu-id="f7d11-251">Zaman uyumlu çözüm çıktısını benzer bir çıktı görüntülenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7d11-251">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="f7d11-252">Ancak, aşağıdaki farkları dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f7d11-252">However, notice the following differences.</span></span>  
  
    -   <span data-ttu-id="f7d11-253">Sonuçları tüm işleme işlemi tamamlandıktan sonra aynı anda oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="f7d11-253">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="f7d11-254">Örneğin, her iki programı bir satır içeren `startButton_Click` metin kutusu temizler.</span><span class="sxs-lookup"><span data-stu-id="f7d11-254">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="f7d11-255">Seçerseniz çalıştırmaları arasında metin kutusu temizlemek için amacı olan **Başlat** bir sonuç kümesi göründükten sonra ikinci bir kez düğmesi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-255">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="f7d11-256">Yalnızca sayıları zaman indirmeleri tamamlandı ve diğer iş yapmak kullanıcı Arabirimi iş parçacığı ücretsizdir ikinci kez görünmesi zaman uyumlu bir sürümde metin kutusu işaretli değildir.</span><span class="sxs-lookup"><span data-stu-id="f7d11-256">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="f7d11-257">Seçtiğiniz hemen sonra metin kutusuna zaman uyumsuz bir sürümde temizler **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-257">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>  
  
    -   <span data-ttu-id="f7d11-258">En önemlisi, kullanıcı Arabirimi iş parçacığı yüklemeleri sırasında engellenmiş değil.</span><span class="sxs-lookup"><span data-stu-id="f7d11-258">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="f7d11-259">Taşıma veya web kaynakları karşıdan yüklenirken pencereyi yeniden boyutlandırmak sayılan ve görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f7d11-259">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="f7d11-260">Web sitelerinden birini yavaş veya yanıt vermiyor işlemi seçerek iptal edebilir **Kapat** düğmesi (sağ üst köşesinde kırmızı alanında x).</span><span class="sxs-lookup"><span data-stu-id="f7d11-260">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <a name="GetURLContentsAsync"></a><span data-ttu-id="f7d11-261">.NET Framework yöntemiyle yöntemi GetURLContentsAsync değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="f7d11-261">To replace method GetURLContentsAsync with a .NET Framework method</span></span>  
  
1.  <span data-ttu-id="f7d11-262">.NET Framework 4.5 kullanabileceğiniz birçok zaman uyumsuz yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7d11-262">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="f7d11-263">Bunlardan biri <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, bu kılavuz için gerekenler yalnızca yapar.</span><span class="sxs-lookup"><span data-stu-id="f7d11-263">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="f7d11-264">Bunun yerine kullanabileceğiniz `GetURLContentsAsync` bir önceki yordamda oluşturduğunuz yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-264">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>  
  
     <span data-ttu-id="f7d11-265">İlk adım oluşturmaktır bir `HttpClient` yöntemi nesnesinde `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="f7d11-265">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="f7d11-266">Aşağıdaki bildirimi yöntemi başlangıcında ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f7d11-266">Add the following declaration at the start of the method.</span></span>  
  
    ```csharp  
    // Declare an HttpClient object and increase the buffer size. The  
    // default buffer size is 65,536.  
    HttpClient client =  
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
    ```  
  
2.  <span data-ttu-id="f7d11-267">İçinde `SumPageSizesAsync,` çağrısı değiştirin, `GetURLContentsAsync` çağrısıyla yöntemi `HttpClient` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-267">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>  
  
    ```csharp  
    byte[] urlContents = await client.GetByteArrayAsync(url);  
    ```  
  
3.  <span data-ttu-id="f7d11-268">Kaldırın veya çıkışı açıklama `GetURLContentsAsync` yazdığınız yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-268">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>  
  
4.  <span data-ttu-id="f7d11-269">Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-269">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="f7d11-270">Bu projenin sürümü davranışını "zaman uyumsuz çözümü test etmek için" yordamı açıklanan davranışı eşleşen ancak sizden daha az çaba ile bile gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7d11-270">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>  
  
##  <a name="BKMK_CompleteCodeExamples"></a><span data-ttu-id="f7d11-271">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7d11-271">Example</span></span>  
 <span data-ttu-id="f7d11-272">Aşağıdaki kod dönüştürme eş zamanlı işlemini zaman uyumsuz bir çözüm için tam örnek içeriyor zaman uyumsuz kullanarak `GetURLContentsAsync` yazdığınız yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f7d11-272">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="f7d11-273">Bunu kesinlikle özgün, zaman uyumlu çözüm benzer dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f7d11-273">Notice that it strongly resembles the original, synchronous solution.</span></span>  
  
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
  
 <span data-ttu-id="f7d11-274">Aşağıdaki kodu kullanan çözüm tam örneği içerir `HttpClient` yöntemi, `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="f7d11-274">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f7d11-275">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f7d11-275">See Also</span></span>  
 [<span data-ttu-id="f7d11-276">Zaman uyumsuz örnek: Web gözden geçirme (C# ve Visual Basic) erişme</span><span class="sxs-lookup"><span data-stu-id="f7d11-276">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](http://go.microsoft.com/fwlink/?LinkId=255191)  
 [<span data-ttu-id="f7d11-277">zaman uyumsuz</span><span class="sxs-lookup"><span data-stu-id="f7d11-277">async</span></span>](../../../../csharp/language-reference/keywords/async.md)  
 [<span data-ttu-id="f7d11-278">await</span><span class="sxs-lookup"><span data-stu-id="f7d11-278">await</span></span>](../../../../csharp/language-reference/keywords/await.md)  
 [<span data-ttu-id="f7d11-279">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="f7d11-279">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="f7d11-280">Zaman uyumsuz dönüş türleri (C#)</span><span class="sxs-lookup"><span data-stu-id="f7d11-280">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="f7d11-281">Görev tabanlı zaman uyumsuz programlama (TAP)</span><span class="sxs-lookup"><span data-stu-id="f7d11-281">Task-based Asynchronous Programming (TAP)</span></span>](http://go.microsoft.com/fwlink/?LinkId=204847)  
 [<span data-ttu-id="f7d11-282">Nasıl yapılır: Task.WhenAll (C#) kullanarak tarafından izlenecek zaman uyumsuz genişletme</span><span class="sxs-lookup"><span data-stu-id="f7d11-282">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)  
 [<span data-ttu-id="f7d11-283">Nasıl yapılır: birden çok Web isteğini paralel olarak zaman uyumsuz kullanarak ve olun await (C#)</span><span class="sxs-lookup"><span data-stu-id="f7d11-283">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
