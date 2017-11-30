---
title: "İzlenecek yol: Visual Studio'da (Visual Basic) Microsoft Office derlemelerinden tür bilgilerini katıştırma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26b44286-5066-4ad4-8e6a-c24902be347c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 26e6fee5147e8477c64f7eaf0dc2aeb928c13e15
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-visual-basic"></a><span data-ttu-id="6fbaf-102">İzlenecek yol: Visual Studio'da (Visual Basic) Microsoft Office derlemelerinden tür bilgilerini katıştırma</span><span class="sxs-lookup"><span data-stu-id="6fbaf-102">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="6fbaf-103">COM nesneleri başvuruda bulunan bir uygulamada tür bilgilerini katıştırma, birincil birlikte çalışma derlemesi (PIA) gereksinimini ortadan kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-103">If you embed type information in an application that references COM objects, you can eliminate the need for a primary interop assembly (PIA).</span></span> <span data-ttu-id="6fbaf-104">Ayrıca, katıştırılmış tür bilgisi sürüm bağımsızlığı, uygulamanız için elde etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-104">Additionally, the embedded type information enables you to achieve version independence for your application.</span></span> <span data-ttu-id="6fbaf-105">Diğer bir deyişle, programınız belirli PIA her sürüm için gerek kalmadan COM kitaplığı birden fazla sürümünü türlerinden kullanacak şekilde yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-105">That is, your program can be written to use types from multiple versions of a COM library without requiring a specific PIA for each version.</span></span> <span data-ttu-id="6fbaf-106">Bu, Microsoft Office kitaplıklarından nesneleri kullanan uygulamalar için ortak bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-106">This is a common scenario for applications that use objects from Microsoft Office libraries.</span></span> <span data-ttu-id="6fbaf-107">Tür bilgilerini katıştırma farklı sürümlerini Microsoft Office programı veya Microsoft Office her sürümü PIA yeniden dağıtmak zorunda kalmadan farklı bilgisayarlarda çalışmak için bir programın aynı yapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-107">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers without the need to redeploy either the program or the PIA for each version of Microsoft Office.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a><span data-ttu-id="6fbaf-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="6fbaf-108">Prerequisites</span></span>  
 <span data-ttu-id="6fbaf-109">Bu kılavuz aşağıdakileri gerektirir:</span><span class="sxs-lookup"><span data-stu-id="6fbaf-109">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="6fbaf-110">Visual Studio ve Microsoft Excel yüklü bir bilgisayar.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-110">A computer on which Visual Studio and Microsoft Excel are installed.</span></span>  
  
-   <span data-ttu-id="6fbaf-111">.NET Framework 4 veya sonraki sürümünü ve Excel farklı bir sürümü yüklü ikinci bir bilgisayar.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-111">A second computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
##  <span data-ttu-id="6fbaf-112"><a name="BKMK_createapp"></a>Microsoft Office birden çok sürümü ile çalışan bir uygulama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6fbaf-112"><a name="BKMK_createapp"></a> To create an application that works with multiple versions of Microsoft Office</span></span>  
  
1.  <span data-ttu-id="6fbaf-113">Excel yüklü olmadığı bir bilgisayara Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-113">Start Visual Studio on a computer on which Excel is installed.</span></span>  
  
2.  <span data-ttu-id="6fbaf-114">Üzerinde **dosya** menüsünde seçin **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-114">On the **File** menu, choose **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="6fbaf-115">İçinde **yeni proje** iletişim kutusunda **proje türleri** bölmesinde olduğundan emin olun **Windows** seçilir.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-115">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="6fbaf-116">Seçin **konsol uygulaması** içinde **şablonları** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-116">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="6fbaf-117">İçinde **adı** kutusuna `CreateExcelWorkbook`ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-117">In the **Name** box, enter `CreateExcelWorkbook`, and then choose the **OK** button.</span></span> <span data-ttu-id="6fbaf-118">Yeni Proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-118">The new project is created.</span></span>  
  
4.  <span data-ttu-id="6fbaf-119">CreateExcelWorkbook proje için kısayol menüsünü açın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-119">Open the shortcut menu for the CreateExcelWorkbook project and then choose **Properties**.</span></span> <span data-ttu-id="6fbaf-120">Seçin **başvuruları** sekmesi. Seçin **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-120">Choose the **References** tab. Choose the **Add** button.</span></span>  
  
5.  <span data-ttu-id="6fbaf-121">Üzerinde **.NET** sekmesinde, en son sürümünü seçin `Microsoft.Office.Interop.Excel`.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-121">On the **.NET** tab, choose the most recent version of `Microsoft.Office.Interop.Excel`.</span></span> <span data-ttu-id="6fbaf-122">Örneğin, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-122">For example, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span></span> <span data-ttu-id="6fbaf-123">Seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-123">Choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="6fbaf-124">Başvuruları listesinde **CreateExcelWorkbook** projesi, başvurusunu seçin `Microsoft.Office.Interop.Excel` , önceki adımda eklediğiniz.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-124">In the list of references for the **CreateExcelWorkbook** project, select the reference for `Microsoft.Office.Interop.Excel` that you added in the previous step.</span></span> <span data-ttu-id="6fbaf-125">İçinde **özellikleri** penceresinde olduğundan emin olun `Embed Interop Types` özelliği ayarlanmış `True`.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-125">In the **Properties** window, make sure that the `Embed Interop Types` property is set to `True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6fbaf-126">Bu kılavuzda oluşturulan uygulama nedeniyle katıştırılmış birlikte çalışma türü bilgileri Microsoft Office'in farklı sürümlerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-126">The application created in this walkthrough runs with different versions of Microsoft Office because of the embedded interop type information.</span></span> <span data-ttu-id="6fbaf-127">Varsa `Embed Interop Types` özelliği ayarlanmış `False`, her sürümü ile uygulamanın çalıştırılacağı Microsoft Office PIA eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-127">If the `Embed Interop Types` property is set to `False`, you must include a PIA for each version of Microsoft Office that the application will run with.</span></span>  
  
7.  <span data-ttu-id="6fbaf-128">Module1.vb dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-128">Open the Module1.vb file.</span></span> <span data-ttu-id="6fbaf-129">Dosyasındaki kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="6fbaf-129">Replace the code in the file with the following code:</span></span>  
  
    ```vb  
    Imports Excel = Microsoft.Office.Interop.Excel  
  
    Module Module1  
  
        Sub Main()  
            Dim values = {4, 6, 18, 2, 1, 76, 0, 3, 11}  
  
            CreateWorkbook(values, "C:\SampleFolder\SampleWorkbook.xls")  
        End Sub  
  
        Sub CreateWorkbook(ByVal values As Integer(), ByVal filePath As String)  
            Dim excelApp As Excel.Application = Nothing  
            Dim wkbk As Excel.Workbook  
            Dim sheet As Excel.Worksheet  
  
            Try  
                ' Start Excel and create a workbook and worksheet.  
                excelApp = New Excel.Application  
                wkbk = excelApp.Workbooks.Add()  
                sheet = CType(wkbk.Sheets.Add(), Excel.Worksheet)  
                sheet.Name = "Sample Worksheet"  
  
                ' Write a column of values.  
                ' In the For loop, both the row index and array index start at 1.  
                ' Therefore the value of 4 at array index 0 is not included.  
                For i = 1 To values.Length - 1  
                    sheet.Cells(i, 1) = values(i)  
                Next  
  
                ' Suppress any alerts and save the file. Create the directory   
                ' if it does not exist. Overwrite the file if it exists.  
                excelApp.DisplayAlerts = False  
                Dim folderPath = My.Computer.FileSystem.GetParentPath(filePath)  
                If Not My.Computer.FileSystem.DirectoryExists(folderPath) Then  
                    My.Computer.FileSystem.CreateDirectory(folderPath)  
                End If  
                wkbk.SaveAs(filePath)  
        Catch  
  
            Finally  
                sheet = Nothing  
                wkbk = Nothing  
  
                ' Close Excel.  
                excelApp.Quit()  
                excelApp = Nothing  
            End Try  
  
        End Sub  
    End Module  
    ```  
  
8.  <span data-ttu-id="6fbaf-130">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-130">Save the project.</span></span>  
  
9. <span data-ttu-id="6fbaf-131">Projesini derlemeyi ve çalıştırmayı için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-131">Press CTRL+F5 to build and run the project.</span></span> <span data-ttu-id="6fbaf-132">Bir Excel çalışma kitabı örnek kodda belirtilen konumda oluşturulduğunu doğrulayın: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-132">Verify that an Excel workbook has been created at the location specified in the example code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
##  <span data-ttu-id="6fbaf-133"><a name="BKMK_publishapp"></a>Microsoft Office'in farklı bir sürümü yüklü olduğu bir bilgisayar için uygulama yayımlamak için</span><span class="sxs-lookup"><span data-stu-id="6fbaf-133"><a name="BKMK_publishapp"></a> To publish the application to a computer on which a different version of Microsoft Office is installed</span></span>  
  
1.  <span data-ttu-id="6fbaf-134">Bu kılavuzda Visual Studio tarafından oluşturulan projeyi açın.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-134">Open the project created by this walkthrough in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="6fbaf-135">Üzerinde **yapı** menüsünde seçin **yayımlama CreateExcelWorkbook**.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-135">On the **Build** menu, choose **Publish CreateExcelWorkbook**.</span></span> <span data-ttu-id="6fbaf-136">Uygulama, yüklenebilir bir sürümünü oluşturmak için Yayımlama Sihirbazı'nın adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-136">Follow the steps of the Publish Wizard to create an installable version of the application.</span></span> <span data-ttu-id="6fbaf-137">Daha fazla bilgi için bkz: [Yayımlama Sihirbazı (Visual Studio'da Office Geliştirme)](https://msdn.microsoft.com/library/bb625071).</span><span class="sxs-lookup"><span data-stu-id="6fbaf-137">For more information, see [Publish Wizard (Office Development in Visual Studio)](https://msdn.microsoft.com/library/bb625071).</span></span>  
  
3.  <span data-ttu-id="6fbaf-138">Uygulama, .NET Framework 4 veya sonraki sürümünü ve Excel farklı bir sürümü yüklü bir bilgisayara yükleyin.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-138">Install the application on a computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
4.  <span data-ttu-id="6fbaf-139">Yükleme tamamlandığında, yüklenen bir program çalıştır.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-139">When the installation is finished, run the installed program.</span></span>  
  
5.  <span data-ttu-id="6fbaf-140">Bir Excel çalışma kitabı örnek kodda belirtilen konumda oluşturulduğunu doğrulayın: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-140">Verify that an Excel workbook has been created at the location specified in the sample code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fbaf-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6fbaf-141">See Also</span></span>  
 [<span data-ttu-id="6fbaf-142">İzlenecek yol: Visual Studio'da (Visual Basic) yönetilen derlemelerden türler katıştırma</span><span class="sxs-lookup"><span data-stu-id="6fbaf-142">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)  
 [<span data-ttu-id="6fbaf-143">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fbaf-143">/link (Visual Basic)</span></span>](../../../../visual-basic/reference/command-line-compiler/link.md)
