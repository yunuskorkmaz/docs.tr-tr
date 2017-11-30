---
title: "İzlenecek yol: Async kullanarak Web'e erişme ve bekleme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: de1219de72be5ddc022d898c904663bf92ca5ab6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a><span data-ttu-id="4476c-102">İzlenecek yol: Async kullanarak Web'e erişme ve bekleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4476c-102">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>
<span data-ttu-id="4476c-103">Zaman uyumsuz ve bekleme özelliklerini kullanarak zaman uyumsuz programlar daha kolay ve sezgisel yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4476c-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="4476c-104">Zaman uyumlu kod gibi görünüyor zaman uyumsuz kod yazın ve daha zor geri arama işlevleri ve zaman uyumsuz kod genellikle kapsar devamlılıklar işlemek derleyici sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4476c-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>  
  
 <span data-ttu-id="4476c-105">Async özelliği hakkında daha fazla bilgi için bkz: [zaman uyumsuz programlama uyumsuz ve bekleme (Visual Basic) ile](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="4476c-105">For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="4476c-106">Bu kılavuzda Web sitelerinin bir listesiyle bayt sayısını toplar zaman uyumlu bir Windows Presentation Foundation (WPF) uygulama başlar.</span><span class="sxs-lookup"><span data-stu-id="4476c-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="4476c-107">İzlenecek yol sonra yeni özellikleri kullanarak zaman uyumsuz çözümünü uygulamaya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="4476c-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>  
  
 <span data-ttu-id="4476c-108">Uygulamaları kendiniz yapılandırmak istemiyorsanız, indirebilirsiniz "zaman uyumsuz örnek: Web gözden geçirme (C# ve Visual Basic) erişme" den [Geliştirici kod örnekleri](http://go.microsoft.com/fwlink/?LinkId=255191).</span><span class="sxs-lookup"><span data-stu-id="4476c-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191).</span></span>  
  
 <span data-ttu-id="4476c-109">Bu kılavuzda, aşağıdaki görevleri tamamlayın:</span><span class="sxs-lookup"><span data-stu-id="4476c-109">In this walkthrough, you complete the following tasks:</span></span>  
  
-   [<span data-ttu-id="4476c-110">Bir WPF uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4476c-110">To create a WPF application</span></span>](#CreateWPFApp)  
  
-   [<span data-ttu-id="4476c-111">Basit bir WPF MainWindow tasarlamak için</span><span class="sxs-lookup"><span data-stu-id="4476c-111">To design a simple WPF MainWindow</span></span>](#MainWindow)  
  
-   [<span data-ttu-id="4476c-112">Bir başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="4476c-112">To add a reference</span></span>](#AddRef)  
  
-   [<span data-ttu-id="4476c-113">Gerekli içeri aktarmaları deyimleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="4476c-113">To add necessary Imports statements</span></span>](#ImportsState)  
  
-   [<span data-ttu-id="4476c-114">Zaman uyumlu bir uygulama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4476c-114">To create a synchronous application</span></span>](#synchronous)  
  
-   [<span data-ttu-id="4476c-115">Zaman uyumlu çözümü test etmek için</span><span class="sxs-lookup"><span data-stu-id="4476c-115">To test the synchronous solution</span></span>](#testSynch)  
  
-   [<span data-ttu-id="4476c-116">Zaman uyumsuz bir yöntem GetURLContents dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="4476c-116">To convert GetURLContents to an asynchronous method</span></span>](#GetURLContents)  
  
-   [<span data-ttu-id="4476c-117">Zaman uyumsuz bir yöntem SumPageSizes dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="4476c-117">To convert SumPageSizes to an asynchronous method</span></span>](#SumPageSizes)  
  
-   [<span data-ttu-id="4476c-118">Zaman uyumsuz bir yöntem startButton_Click dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="4476c-118">To convert startButton_Click to an asynchronous method</span></span>](#startButton)  
  
-   [<span data-ttu-id="4476c-119">Zaman uyumsuz çözümü test etmek için</span><span class="sxs-lookup"><span data-stu-id="4476c-119">To test the asynchronous solution</span></span>](#testAsynch)  
  
-   [<span data-ttu-id="4476c-120">.NET Framework yöntemiyle yöntemi GetURLContentsAsync değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="4476c-120">To replace method GetURLContentsAsync with a .NET Framework method</span></span>](#GetURLContentsAsync)  
  
-   [<span data-ttu-id="4476c-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="4476c-121">Example</span></span>](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a><span data-ttu-id="4476c-122">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="4476c-122">Prerequisites</span></span>  
 <span data-ttu-id="4476c-123">Visual Studio 2012 veya sonraki sürümünü bilgisayarınızda yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4476c-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="4476c-124">Daha fazla bilgi için bkz: [Microsoft Web sitesi](http://go.microsoft.com/fwlink/?LinkId=235233).</span><span class="sxs-lookup"><span data-stu-id="4476c-124">For more information, see the [Microsoft website](http://go.microsoft.com/fwlink/?LinkId=235233).</span></span>  
  
###  <span data-ttu-id="4476c-125"><a name="CreateWPFApp"></a>Bir WPF uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4476c-125"><a name="CreateWPFApp"></a> To create a WPF application</span></span>  
  
1.  <span data-ttu-id="4476c-126">Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="4476c-126">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="4476c-127">Menü çubuğunda seçin **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="4476c-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="4476c-128">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="4476c-128">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="4476c-129">İçinde **yüklü şablonlar** bölmesinde, Visual Basic seçin ve ardından **WPF uygulaması** proje türleri listesinden.</span><span class="sxs-lookup"><span data-stu-id="4476c-129">In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="4476c-130">İçinde **adı** metin kutusuna `AsyncExampleWPF`ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="4476c-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="4476c-131">Yeni Proje görünür **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="4476c-131">The new project appears in **Solution Explorer**.</span></span>  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <span data-ttu-id="4476c-132"><a name="MainWindow"></a>Basit bir WPF MainWindow tasarlamak için</span><span class="sxs-lookup"><span data-stu-id="4476c-132"><a name="MainWindow"></a> To design a simple WPF MainWindow</span></span>  
  
1.  <span data-ttu-id="4476c-133">Visual Studio Kod Düzenleyicisi'nde seçin **MainWindow.xaml** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="4476c-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
2.  <span data-ttu-id="4476c-134">Varsa **araç** pencere görünür, açık olmayan **Görünüm** menüsünde ve ardından **araç**.</span><span class="sxs-lookup"><span data-stu-id="4476c-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="4476c-135">Ekleme bir **düğmesini** denetim ve **TextBox** denetimini **MainWindow** penceresi.</span><span class="sxs-lookup"><span data-stu-id="4476c-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>  
  
4.  <span data-ttu-id="4476c-136">Vurgula **TextBox** denetim hem de **özellikleri** penceresinde, aşağıdaki değerleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="4476c-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="4476c-137">Ayarlama **adı** özelliğine `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="4476c-137">Set the **Name** property to `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="4476c-138">Ayarlama **yükseklik** 250 özelliğine.</span><span class="sxs-lookup"><span data-stu-id="4476c-138">Set the **Height** property to 250.</span></span>  
  
    -   <span data-ttu-id="4476c-139">Ayarlama **genişliği** 500 özelliği.</span><span class="sxs-lookup"><span data-stu-id="4476c-139">Set the **Width** property to 500.</span></span>  
  
    -   <span data-ttu-id="4476c-140">Üzerinde **metin** sekmesinde, Lucida Console veya genel tek aralıklı gibi aralıklı bir yazı tipi belirtin.</span><span class="sxs-lookup"><span data-stu-id="4476c-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>  
  
5.  <span data-ttu-id="4476c-141">Vurgula **düğmesini** denetim hem de **özellikleri** penceresinde, aşağıdaki değerleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="4476c-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="4476c-142">Ayarlama **adı** özelliğine `startButton`.</span><span class="sxs-lookup"><span data-stu-id="4476c-142">Set the **Name** property to `startButton`.</span></span>  
  
    -   <span data-ttu-id="4476c-143">Değerini değiştirme **içerik** özelliğinden **düğmesini** için **Başlat**.</span><span class="sxs-lookup"><span data-stu-id="4476c-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>  
  
6.  <span data-ttu-id="4476c-144">Her ikisi de görünmesini sağlayacak şekilde, metin kutusu ve düğmesi konum **MainWindow** penceresi.</span><span class="sxs-lookup"><span data-stu-id="4476c-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>  
  
     <span data-ttu-id="4476c-145">WPF XAML Tasarımcısı hakkında daha fazla bilgi için bkz: [XAML Tasarımcısını kullanarak bir kullanıcı Arabirimi oluşturma](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="4476c-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>  
  
##  <a name="BKMK_AddReference"></a>   
###  <span data-ttu-id="4476c-146"><a name="AddRef"></a>Bir başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="4476c-146"><a name="AddRef"></a> To add a reference</span></span>  
  
1.  <span data-ttu-id="4476c-147">İçinde **Çözüm Gezgini**, projenizin adını vurgulayın.</span><span class="sxs-lookup"><span data-stu-id="4476c-147">In **Solution Explorer**, highlight your project's name.</span></span>  
  
2.  <span data-ttu-id="4476c-148">Menü çubuğunda seçin **proje**, **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="4476c-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="4476c-149">**Başvuru Yöneticisi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4476c-149">The **Reference Manager** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="4476c-150">İletişim kutusunun üstündeki projeniz .NET Framework 4.5 veya üstünü hedefleyen olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="4476c-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>  
  
4.  <span data-ttu-id="4476c-151">İçinde **derlemeleri** alanı seçin **Framework** tercih değil.</span><span class="sxs-lookup"><span data-stu-id="4476c-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
5.  <span data-ttu-id="4476c-152">Adları listesinden seçin **System.Net.Http** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="4476c-152">In the list of names, select the **System.Net.Http** check box.</span></span>  
  
6.  <span data-ttu-id="4476c-153">Seçin **Tamam** düğmesi iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="4476c-153">Choose the **OK** button to close the dialog box.</span></span>  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <span data-ttu-id="4476c-154"><a name="ImportsState"></a>Gerekli içeri aktarmaları deyimleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="4476c-154"><a name="ImportsState"></a> To add necessary Imports statements</span></span>  
  
1.  <span data-ttu-id="4476c-155">İçinde **Çözüm Gezgini**MainWindow.xaml.vb için kısayol menüsünü açın ve ardından **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="4476c-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="4476c-156">Aşağıdakileri ekleyin `Imports` zaten mevcut değillerse kod dosyasının deyimlerini.</span><span class="sxs-lookup"><span data-stu-id="4476c-156">Add the following `Imports` statements at the top of the code file if they’re not already present.</span></span>  
  
    ```vb  
    Imports System.Net.Http  
    Imports System.Net  
    Imports System.IO  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <span data-ttu-id="4476c-157"><a name="synchronous"></a>Zaman uyumlu bir uygulama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4476c-157"><a name="synchronous"></a> To create a synchronous application</span></span>  
  
1.  <span data-ttu-id="4476c-158">Tasarım penceresinde MainWindow.xaml, çift **Başlat** oluşturmak için düğmesini `startButton_Click` MainWindow.xaml.vb olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="4476c-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="4476c-159">MainWindow.xaml.vb içinde gövdesine aşağıdaki kodu kopyalayın `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="4476c-159">In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:</span></span>  
  
    ```vb  
    resultsTextBox.Clear()  
    SumPageSizes()  
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."  
    ```  
  
     <span data-ttu-id="4476c-160">Kod uygulama sürücüleri yöntemini çağırır `SumPageSizes`ve denetim döndüğünde bir ileti görüntüler `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="4476c-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>  
  
3.  <span data-ttu-id="4476c-161">Zaman uyumlu çözüm için kod aşağıdaki dört yöntemi içerir:</span><span class="sxs-lookup"><span data-stu-id="4476c-161">The code for the synchronous solution contains the following four methods:</span></span>  
  
    -   <span data-ttu-id="4476c-162">`SumPageSizes`, Web sayfası URL'lerden listesini alır `SetUpURLList` ve çağırır `GetURLContents` ve `DisplayResults` her URL işleyemedi.</span><span class="sxs-lookup"><span data-stu-id="4476c-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>  
  
    -   <span data-ttu-id="4476c-163">`SetUpURLList`, hangi yapar ve web adresleri listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="4476c-163">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>  
  
    -   <span data-ttu-id="4476c-164">`GetURLContents`, her Web sitesi içeriğini indirir ve içeriği bir bayt dizisi olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="4476c-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>  
  
    -   <span data-ttu-id="4476c-165">`DisplayResults`, görüntüleyen bayt sayısı bayt dizisi, her URL için.</span><span class="sxs-lookup"><span data-stu-id="4476c-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>  
  
     <span data-ttu-id="4476c-166">Aşağıdaki dört yöntemi kopyalayın ve yapıştırın altında `startButton_Click` MainWindow.xaml.vb olay işleyicisi:</span><span class="sxs-lookup"><span data-stu-id="4476c-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:</span></span>  
  
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
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
    ```  
  
##  <a name="BKMK_TestSynchSol"></a>   
###  <span data-ttu-id="4476c-167"><a name="testSynch"></a>Zaman uyumlu çözümü test etmek için</span><span class="sxs-lookup"><span data-stu-id="4476c-167"><a name="testSynch"></a> To test the synchronous solution</span></span>  
  
1.  <span data-ttu-id="4476c-168">Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="4476c-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="4476c-169">Aşağıdaki listede benzer bir çıktı görüntülenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4476c-169">Output that resembles the following list should appear.</span></span>  
  
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
  
     <span data-ttu-id="4476c-170">Sayıları görüntülemek için birkaç saniye sürer dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="4476c-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="4476c-171">İstenen kaynaklar indirmek beklerken bu süre içinde kullanıcı Arabirimi iş parçacığı engellendi.</span><span class="sxs-lookup"><span data-stu-id="4476c-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="4476c-172">Sonuç olarak, taşıyamazsınız, en üst düzeye çıkarmak, simge durumuna küçült veya seçtiğiniz sonra bile görüntü penceresini kapatın **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="4476c-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="4476c-173">Görüntülenecek bayt sayıları başlatana kadar bu çaba başarısız.</span><span class="sxs-lookup"><span data-stu-id="4476c-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="4476c-174">Bir Web sitesi yanıt vermiyor gösterge olmadan başarısız hangi sitenin varsa.</span><span class="sxs-lookup"><span data-stu-id="4476c-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="4476c-175">Hatta bekleme durdurmak ve program kapatmak zordur.</span><span class="sxs-lookup"><span data-stu-id="4476c-175">It is difficult even to stop waiting and close the program.</span></span>  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <span data-ttu-id="4476c-176"><a name="GetURLContents"></a>Zaman uyumsuz bir yöntem GetURLContents dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="4476c-176"><a name="GetURLContents"></a> To convert GetURLContents to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="4476c-177">Zaman uyumsuz bir çözüme zaman uyumlu çözüm dönüştürmek için başlatmak için en iyi yerdir bulunduğu `GetURLContents` çünkü çağrıları <xref:System.Net.HttpWebRequest> yöntemi <xref:System.Net.HttpWebRequest.GetResponse%2A> ve <xref:System.IO.Stream> yöntemi <xref:System.IO.Stream.CopyTo%2A> burada web uygulama erişen olan .</span><span class="sxs-lookup"><span data-stu-id="4476c-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="4476c-178">.NET Framework dönüştürme her iki yöntem zaman uyumsuz sürümlerini sağlayarak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="4476c-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>  
  
     <span data-ttu-id="4476c-179">Kullanılan yöntemleri hakkında daha fazla bilgi için `GetURLContents`, bkz: <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="4476c-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4476c-180">Bu izlenecek adımları izlediğiniz gibi birkaç derleyici hataları görünür.</span><span class="sxs-lookup"><span data-stu-id="4476c-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="4476c-181">Bunları yoksay ve kılavuz ile devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4476c-181">You can ignore them and continue with the walkthrough.</span></span>  
  
     <span data-ttu-id="4476c-182">Üçüncü satırında adlı yöntemini değiştirme `GetURLContents` gelen `GetResponse` için zaman uyumsuz, görev tabanlı <xref:System.Net.WebRequest.GetResponseAsync%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4476c-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>  
  
    ```vb  
    Using response As WebResponse = webReq.GetResponseAsync()  
    ```  
  
2.  <span data-ttu-id="4476c-183">`GetResponseAsync`döndüren bir <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="4476c-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="4476c-184">Bu durumda, *görev dönüş değişkeni*, `TResult`, türüne sahip <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="4476c-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="4476c-185">Gerçek bir üretmek için promise görevdir `WebResponse` istenen veri indirilir ve görevin tamamlanması çalıştıktan sonra nesnesi.</span><span class="sxs-lookup"><span data-stu-id="4476c-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>  
  
     <span data-ttu-id="4476c-186">Alınacak `WebResponse` görevden değer, geçerli bir [bekleme](../../../../visual-basic/language-reference/operators/await-operator.md) çağrısına işleci `GetResponseAsync`, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="4476c-186">To retrieve the `WebResponse` value from the task, apply an [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>  
  
    ```vb  
    Using response As WebResponse = Await webReq.GetResponseAsync()  
    ```  
  
     <span data-ttu-id="4476c-187">`Await` İşleci geçerli yönteminin yürütülmesi askıya `GetURLContents`, awaited görevi tamamlanana kadar.</span><span class="sxs-lookup"><span data-stu-id="4476c-187">The `Await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="4476c-188">Bu arada, denetim geçerli yöntemi çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="4476c-188">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="4476c-189">Bu örnekte, geçerli bir yöntemdir `GetURLContents`, ve çağrıyı yapan `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="4476c-189">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="4476c-190">Görev tamamlandığında taahhüt `WebResponse` nesne awaited görev değeri olarak üretilen ve değişkenine atanan `response`.</span><span class="sxs-lookup"><span data-stu-id="4476c-190">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>  
  
     <span data-ttu-id="4476c-191">Önceki deyimi ne olacağını açıklamak için aşağıdaki iki deyime ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="4476c-191">The previous statement can be separated into the following two statements to clarify what happens.</span></span>  
  
    ```vb  
    'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()  
    'Using response As WebResponse = Await responseTask  
    ```  
  
     <span data-ttu-id="4476c-192">Çağrı `webReq.GetResponseAsync` döndüren bir `Task(Of WebResponse)` veya `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="4476c-192">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="4476c-193">Ardından bir `Await` işleci almak için göreve uygulanan `WebResponse` değeri.</span><span class="sxs-lookup"><span data-stu-id="4476c-193">Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.</span></span>  
  
     <span data-ttu-id="4476c-194">Zaman uyumsuz yöntem görev tamamlanma bağımlı değil yapmak için iş varsa, yöntemi zaman uyumsuz yöntem ve bekleme işleci uygulanmadan önce çağrısından sonra bu iki ifade arasındaki, iş devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4476c-194">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied.</span></span> <span data-ttu-id="4476c-195">Örnekler için bkz: [nasıl yapılır: olun birden çok Web isteğini paralel kullanarak zaman uyumsuz ve bekleme (Visual Basic) tarafından](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) ve [nasıl yapılır: Task.WhenAll kullanarak (Visual Basic) tarafından zaman uyumsuz izlenecek yolu genişletme](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="4476c-195">For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
3.  <span data-ttu-id="4476c-196">Eklediğiniz çünkü `Await` işleci önceki adımda, bir derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="4476c-196">Because you added the `Await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="4476c-197">İşleç ile işaretlenmiş yöntemleri kullanılabilir [zaman uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="4476c-197">The operator can be used only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="4476c-198">Çağrı değiştirmek için dönüştürme adımları yineleyin sırada hatayı yok sayıp `CopyTo` çağrısıyla `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="4476c-198">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>  
  
    -   <span data-ttu-id="4476c-199">İçin çağrılan yöntemin adını değiştirmek <xref:System.IO.Stream.CopyToAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="4476c-199">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>  
  
    -   <span data-ttu-id="4476c-200">`CopyTo` Veya `CopyToAsync` yöntemi için bağımsız değişkeni, bayt kopyalar `content`ve anlamlı bir değer döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="4476c-200">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="4476c-201">Zaman uyumlu sürümünde, çağrısı `CopyTo` bir değer döndürmüyor basit bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="4476c-201">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="4476c-202">Zaman uyumsuz sürümü `CopyToAsync`, döndüren bir <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="4476c-202">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="4476c-203">Görev "Task(void)" gibi çalışır ve yöntem beklemenin sağlar.</span><span class="sxs-lookup"><span data-stu-id="4476c-203">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="4476c-204">Uygulama `Await` veya `await` çağrısına `CopyToAsync`, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="4476c-204">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>  
  
        ```vb  
        Await responseStream.CopyToAsync(content)  
        ```  
  
         <span data-ttu-id="4476c-205">Önceki deyimi aşağıdaki iki kod satırı kısaltmasıdır.</span><span class="sxs-lookup"><span data-stu-id="4476c-205">The previous statement abbreviates the following two lines of code.</span></span>  
  
        ```vb  
        ' CopyToAsync returns a Task, not a Task<T>.  
        'Dim copyTask As Task = responseStream.CopyToAsync(content)  
  
        ' When copyTask is completed, content contains a copy of  
        ' responseStream.  
        'Await copyTask  
        ```  
  
4.  <span data-ttu-id="4476c-206">Tüm bu tamamlandı olarak kalır `GetURLContents` yöntem imzası ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="4476c-206">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="4476c-207">Kullanabileceğiniz `Await` ile işaretlenmiş yöntemleri işlecinde [zaman uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="4476c-207">You can use the `Await` operator only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="4476c-208">Yöntemi olarak işaretlemek için değiştiricisi eklemek bir *async yöntemi*, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="4476c-208">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>  
  
    ```vb  
    Private Async Function GetURLContents(url As String) As Byte()  
    ```  
  
5.  <span data-ttu-id="4476c-209">Bir zaman uyumsuz yöntemin dönüş türünü yalnızca olabilir <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="4476c-209">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="4476c-210">Visual Basic'te yöntemi olmalıdır bir `Function` döndüren bir `Task` veya `Task(Of T)`, veya bir yöntem olmalıdır bir `Sub`.</span><span class="sxs-lookup"><span data-stu-id="4476c-210">In Visual Basic, the method must be a `Function` that returns a `Task` or a `Task(Of T)`, or the method must be a `Sub`.</span></span> <span data-ttu-id="4476c-211">Genellikle, bir `Sub` yöntemi yalnızca bir zaman uyumsuz olay işleyicisi, kullanılan nerede `Sub` gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4476c-211">Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required.</span></span> <span data-ttu-id="4476c-212">Diğer durumlarda, kullandığınız `Task(T)` tamamlanmış yöntemi varsa bir [dönmek](../../../../visual-basic/language-reference/statements/return-statement.md) T değeri döndüren ifadesi yazın ve kullandığınız `Task` tamamlanmış yöntemi anlamlı bir değere döndürmezse.</span><span class="sxs-lookup"><span data-stu-id="4476c-212">In other cases, you use `Task(T)` if the completed method has a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span>  
  
     <span data-ttu-id="4476c-213">Daha fazla bilgi için bkz: [zaman uyumsuz dönüş türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="4476c-213">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
     <span data-ttu-id="4476c-214">Yöntem `GetURLContents` bir dönüş ifadesi içeriyor ve deyim bir bayt dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="4476c-214">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="4476c-215">Bu nedenle, zaman uyumsuz sürümü dönüş türü T bir bayt dizisi olduğu Task(T) ' dir.</span><span class="sxs-lookup"><span data-stu-id="4476c-215">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="4476c-216">Yöntem imzası aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="4476c-216">Make the following changes in the method signature:</span></span>  
  
    -   <span data-ttu-id="4476c-217">Dönüş türünü değiştir `Task(Of Byte())`.</span><span class="sxs-lookup"><span data-stu-id="4476c-217">Change the return type to `Task(Of Byte())`.</span></span>  
  
    -   <span data-ttu-id="4476c-218">Kurala göre zaman uyumsuz yöntemleri "Zaman uyumsuz," bitiş adlara sahip şekilde yöntemi yeniden adlandırma `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="4476c-218">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>  
  
     <span data-ttu-id="4476c-219">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="4476c-219">The following code shows these changes.</span></span>  
  
    ```vb  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
    ```  
  
     <span data-ttu-id="4476c-220">Dönüştürme işlemi birkaç bu değişikliklerle `GetURLContents` zaman uyumsuz bir yöntem tamamlandığında.</span><span class="sxs-lookup"><span data-stu-id="4476c-220">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <span data-ttu-id="4476c-221"><a name="SumPageSizes"></a>Zaman uyumsuz bir yöntem SumPageSizes dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="4476c-221"><a name="SumPageSizes"></a> To convert SumPageSizes to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="4476c-222">İçin önceki yordamdaki adımları yineleyin `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="4476c-222">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="4476c-223">İlk olarak, araması olarak değiştirmelerine `GetURLContents` zaman uyumsuz bir çağrı için.</span><span class="sxs-lookup"><span data-stu-id="4476c-223">First, change the call to `GetURLContents` to an asynchronous call.</span></span>  
  
    -   <span data-ttu-id="4476c-224">Yönteminden çağrılan yöntemin adını değiştirmek `GetURLContents` için `GetURLContentsAsync`, zaten yapmadıysanız.</span><span class="sxs-lookup"><span data-stu-id="4476c-224">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>  
  
    -   <span data-ttu-id="4476c-225">Uygulama `Await` göreve, `GetURLContentsAsync` bayt edinme döndürür dizi değeri.</span><span class="sxs-lookup"><span data-stu-id="4476c-225">Apply `Await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>  
  
     <span data-ttu-id="4476c-226">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="4476c-226">The following code shows these changes.</span></span>  
  
    ```vb  
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
    ```  
  
     <span data-ttu-id="4476c-227">Önceki atama kod aşağıdaki iki satırı kısaltmasıdır.</span><span class="sxs-lookup"><span data-stu-id="4476c-227">The previous assignment abbreviates the following two lines of code.</span></span>  
  
    ```vb  
    ' GetURLContentsAsync returns a task. At completion, the task   
    ' produces a byte array.   
    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)   
    'Dim urlContents As Byte() = Await getContentsTask  
    ```  
  
2.  <span data-ttu-id="4476c-228">Yöntemin imzada aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="4476c-228">Make the following changes in the method's signature:</span></span>  
  
    -   <span data-ttu-id="4476c-229">Yöntemiyle işaretlemek `Async` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="4476c-229">Mark the method with the `Async` modifier.</span></span>  
  
    -   <span data-ttu-id="4476c-230">"Zaman uyumsuz" yöntem adını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4476c-230">Add "Async" to the method name.</span></span>  
  
    -   <span data-ttu-id="4476c-231">T, hiçbir görev dönüş değişkeni bu süresi yoktur çünkü `SumPageSizesAsync` T. için bir değer döndürmüyor (Yöntem sahip olmayan `Return` deyimi.) Ancak, yöntem döndürmelidir bir `Task` bildirdiğimize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4476c-231">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="4476c-232">Bu nedenle, yöntemi türünden değiştirme `Sub` için `Function`.</span><span class="sxs-lookup"><span data-stu-id="4476c-232">Therefore, change the method type from `Sub` to `Function`.</span></span> <span data-ttu-id="4476c-233">İşlev dönüş türü `Task`.</span><span class="sxs-lookup"><span data-stu-id="4476c-233">The return type of the function is `Task`.</span></span>  
  
     <span data-ttu-id="4476c-234">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="4476c-234">The following code shows these changes.</span></span>  
  
    ```vb  
    Private Async Function SumPageSizesAsync() As Task  
    ```  
  
     <span data-ttu-id="4476c-235">Dönüştürülmesi `SumPageSizes` için `SumPageSizesAsync` tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="4476c-235">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <span data-ttu-id="4476c-236"><a name="startButton"></a>Zaman uyumsuz bir yöntem startButton_Click dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="4476c-236"><a name="startButton"></a> To convert startButton_Click to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="4476c-237">Olay işleyicisinin çağrılan yöntemin adını değiştirmek `SumPageSizes` için `SumPageSizesAsync`, zaten yapmadıysanız.</span><span class="sxs-lookup"><span data-stu-id="4476c-237">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>  
  
2.  <span data-ttu-id="4476c-238">Çünkü `SumPageSizesAsync` bir zaman uyumsuz yöntem sonucu beklemek için olay işleyicisini kodda değişiklik.</span><span class="sxs-lookup"><span data-stu-id="4476c-238">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>  
  
     <span data-ttu-id="4476c-239">Çağrı `SumPageSizesAsync` çağrısı yansıtan `CopyToAsync` içinde `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="4476c-239">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="4476c-240">Çağrı döndürür bir `Task`değil bir `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="4476c-240">The call returns a `Task`, not a `Task(T)`.</span></span>  
  
     <span data-ttu-id="4476c-241">Önceki yordamları olduğu gibi bir deyim veya iki deyimleri kullanarak çağrı dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4476c-241">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="4476c-242">Aşağıdaki kod bu değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="4476c-242">The following code shows these changes.</span></span>  
  
    ```vb  
    '' One-step async call.  
    Await SumPageSizesAsync()  
  
    ' Two-step async call.  
    'Dim sumTask As Task = SumPageSizesAsync()  
    'Await sumTask  
    ```  
  
3.  <span data-ttu-id="4476c-243">Yanlışlıkla işlemi yeniden girme önlemek için aşağıdaki en üstünde deyimine `startButton_Click` devre dışı bırakmak için **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="4476c-243">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>  
  
    ```vb  
    ' Disable the button until the operation is complete.  
    startButton.IsEnabled = False  
    ```  
  
     <span data-ttu-id="4476c-244">Olay işleyicisinin sonunda düğmesini yeniden etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4476c-244">You can reenable the button at the end of the event handler.</span></span>  
  
    ```vb  
    ' Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = True  
    ```  
  
     <span data-ttu-id="4476c-245">Yeniden giriş hakkında daha fazla bilgi için bkz: [(Visual Basic) zaman uyumsuz uygulamalarda yeniden girişi işleme](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="4476c-245">For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>  
  
4.  <span data-ttu-id="4476c-246">Son olarak, ekleme `Async` bildirimine değiştiricisi böylece olay işleyicisi await `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="4476c-246">Finally, add the `Async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>  
  
    ```vb  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
    ```  
  
     <span data-ttu-id="4476c-247">Olay işleyicileri adları genellikle değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="4476c-247">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="4476c-248">Dönüş türü için değiştirilmez `Task` olay işleyicileri olması gerektiğinden `Sub` Visual Basic'de yordamlar.</span><span class="sxs-lookup"><span data-stu-id="4476c-248">The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.</span></span>  
  
     <span data-ttu-id="4476c-249">Proje dönüştürme için zaman uyumsuz zaman uyumlu işleme işlemi tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="4476c-249">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <span data-ttu-id="4476c-250"><a name="testAsynch"></a>Zaman uyumsuz çözümü test etmek için</span><span class="sxs-lookup"><span data-stu-id="4476c-250"><a name="testAsynch"></a> To test the asynchronous solution</span></span>  
  
1.  <span data-ttu-id="4476c-251">Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="4476c-251">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
2.  <span data-ttu-id="4476c-252">Zaman uyumlu çözüm çıktısını benzer bir çıktı görüntülenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4476c-252">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="4476c-253">Ancak, aşağıdaki farkları dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="4476c-253">However, notice the following differences.</span></span>  
  
    -   <span data-ttu-id="4476c-254">Sonuçları tüm işleme işlemi tamamlandıktan sonra aynı anda oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="4476c-254">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="4476c-255">Örneğin, her iki programı bir satır içeren `startButton_Click` metin kutusu temizler.</span><span class="sxs-lookup"><span data-stu-id="4476c-255">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="4476c-256">Seçerseniz çalıştırmaları arasında metin kutusu temizlemek için amacı olan **Başlat** bir sonuç kümesi göründükten sonra ikinci bir kez düğmesi.</span><span class="sxs-lookup"><span data-stu-id="4476c-256">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="4476c-257">Yalnızca sayıları zaman indirmeleri tamamlandı ve diğer iş yapmak kullanıcı Arabirimi iş parçacığı ücretsizdir ikinci kez görünmesi zaman uyumlu bir sürümde metin kutusu işaretli değildir.</span><span class="sxs-lookup"><span data-stu-id="4476c-257">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="4476c-258">Seçtiğiniz hemen sonra metin kutusuna zaman uyumsuz bir sürümde temizler **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="4476c-258">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>  
  
    -   <span data-ttu-id="4476c-259">En önemlisi, kullanıcı Arabirimi iş parçacığı yüklemeleri sırasında engellenmiş değil.</span><span class="sxs-lookup"><span data-stu-id="4476c-259">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="4476c-260">Taşıma veya web kaynakları karşıdan yüklenirken pencereyi yeniden boyutlandırmak sayılan ve görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4476c-260">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="4476c-261">Web sitelerinden birini yavaş veya yanıt vermiyor işlemi seçerek iptal edebilir **Kapat** düğmesi (sağ üst köşesinde kırmızı alanında x).</span><span class="sxs-lookup"><span data-stu-id="4476c-261">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <span data-ttu-id="4476c-262"><a name="GetURLContentsAsync"></a>.NET Framework yöntemiyle yöntemi GetURLContentsAsync değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="4476c-262"><a name="GetURLContentsAsync"></a> To replace method GetURLContentsAsync with a .NET Framework method</span></span>  
  
1.  <span data-ttu-id="4476c-263">.NET Framework 4.5 kullanabileceğiniz birçok zaman uyumsuz yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4476c-263">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="4476c-264">Bunlardan biri <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, bu kılavuz için gerekenler yalnızca yapar.</span><span class="sxs-lookup"><span data-stu-id="4476c-264">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="4476c-265">Bunun yerine kullanabileceğiniz `GetURLContentsAsync` bir önceki yordamda oluşturduğunuz yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4476c-265">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>  
  
     <span data-ttu-id="4476c-266">İlk adım oluşturmaktır bir `HttpClient` yöntemi nesnesinde `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="4476c-266">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="4476c-267">Aşağıdaki bildirimi yöntemi başlangıcında ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4476c-267">Add the following declaration at the start of the method.</span></span>  
  
    ```vb  
    ' Declare an HttpClient object and increase the buffer size. The  
    ' default buffer size is 65,536.  
    Dim client As HttpClient =  
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
    ```  
  
2.  <span data-ttu-id="4476c-268">İçinde `SumPageSizesAsync,` çağrısı değiştirin, `GetURLContentsAsync` çağrısıyla yöntemi `HttpClient` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4476c-268">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>  
  
    ```vb  
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ```  
  
3.  <span data-ttu-id="4476c-269">Kaldırın veya çıkışı açıklama `GetURLContentsAsync` yazdığınız yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4476c-269">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>  
  
4.  <span data-ttu-id="4476c-270">Programını çalıştırın ve ardından için F5 tuşuna seçin **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="4476c-270">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="4476c-271">Bu projenin sürümü davranışını "zaman uyumsuz çözümü test etmek için" yordamı açıklanan davranışı eşleşen ancak sizden daha az çaba ile bile gerekir.</span><span class="sxs-lookup"><span data-stu-id="4476c-271">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>  
  
##  <span data-ttu-id="4476c-272"><a name="BKMK_CompleteCodeExamples"></a>Örnek</span><span class="sxs-lookup"><span data-stu-id="4476c-272"><a name="BKMK_CompleteCodeExamples"></a> Example</span></span>  
 <span data-ttu-id="4476c-273">Aşağıdaki kod dönüştürme eş zamanlı işlemini zaman uyumsuz bir çözüm için tam örnek içeriyor zaman uyumsuz kullanarak `GetURLContentsAsync` yazdığınız yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4476c-273">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="4476c-274">Bunu kesinlikle özgün, zaman uyumlu çözüm benzer dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="4476c-274">Notice that it strongly resembles the original, synchronous solution.</span></span>  
  
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
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
 <span data-ttu-id="4476c-275">Aşağıdaki kodu kullanan çözüm tam örneği içerir `HttpClient` yöntemi, `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="4476c-275">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>  
  
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
  
        '' Two-step async call.  
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
            }  
        Return urls  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="4476c-276">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4476c-276">See Also</span></span>  
 [<span data-ttu-id="4476c-277">Zaman uyumsuz örnek: Web gözden geçirme (C# ve Visual Basic) erişme</span><span class="sxs-lookup"><span data-stu-id="4476c-277">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](http://go.microsoft.com/fwlink/?LinkId=255191)  
 [<span data-ttu-id="4476c-278">Await işleci</span><span class="sxs-lookup"><span data-stu-id="4476c-278">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)  
 [<span data-ttu-id="4476c-279">Zaman uyumsuz</span><span class="sxs-lookup"><span data-stu-id="4476c-279">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)  
 [<span data-ttu-id="4476c-280">Zaman uyumsuz programlama ile Async ve Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4476c-280">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="4476c-281">Zaman uyumsuz dönüş türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4476c-281">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="4476c-282">Görev tabanlı zaman uyumsuz programlama (TAP)</span><span class="sxs-lookup"><span data-stu-id="4476c-282">Task-based Asynchronous Programming (TAP)</span></span>](http://go.microsoft.com/fwlink/?LinkId=204847)  
 [<span data-ttu-id="4476c-283">Nasıl yapılır: Task.WhenAll (Visual Basic) kullanarak zaman uyumsuz izlenecek yolu genişletme</span><span class="sxs-lookup"><span data-stu-id="4476c-283">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)  
 [<span data-ttu-id="4476c-284">Nasıl yapılır: Async kullanarak birden çok Web isteğini paralel hale ve Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4476c-284">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
