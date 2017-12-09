---
title: "İzlenecek yol: Visual Studio'da (C#) Microsoft Office derlemelerinden tür bilgilerini katıştırma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 3320e866-01f1-4b7f-8932-049a7b2d2a9b
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 45ec4521da08a9a1f4bdc3b433d3f8d765960526
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-c"></a><span data-ttu-id="1797e-102">İzlenecek yol: Visual Studio'da (C#) Microsoft Office derlemelerinden tür bilgilerini katıştırma</span><span class="sxs-lookup"><span data-stu-id="1797e-102">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (C#)</span></span>
<span data-ttu-id="1797e-103">COM nesneleri başvuruda bulunan bir uygulamada tür bilgilerini katıştırma, birincil birlikte çalışma derlemesi (PIA) gereksinimini ortadan kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1797e-103">If you embed type information in an application that references COM objects, you can eliminate the need for a primary interop assembly (PIA).</span></span> <span data-ttu-id="1797e-104">Ayrıca, katıştırılmış tür bilgisi sürüm bağımsızlığı, uygulamanız için elde etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1797e-104">Additionally, the embedded type information enables you to achieve version independence for your application.</span></span> <span data-ttu-id="1797e-105">Diğer bir deyişle, programınız belirli PIA her sürüm için gerek kalmadan COM kitaplığı birden fazla sürümünü türlerinden kullanacak şekilde yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="1797e-105">That is, your program can be written to use types from multiple versions of a COM library without requiring a specific PIA for each version.</span></span> <span data-ttu-id="1797e-106">Bu, Microsoft Office kitaplıklarından nesneleri kullanan uygulamalar için ortak bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="1797e-106">This is a common scenario for applications that use objects from Microsoft Office libraries.</span></span> <span data-ttu-id="1797e-107">Tür bilgilerini katıştırma farklı sürümlerini Microsoft Office programı veya Microsoft Office her sürümü PIA yeniden dağıtmak zorunda kalmadan farklı bilgisayarlarda çalışmak için bir programın aynı yapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1797e-107">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers without the need to redeploy either the program or the PIA for each version of Microsoft Office.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a><span data-ttu-id="1797e-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="1797e-108">Prerequisites</span></span>  
 <span data-ttu-id="1797e-109">Bu kılavuz aşağıdakileri gerektirir:</span><span class="sxs-lookup"><span data-stu-id="1797e-109">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="1797e-110">Visual Studio ve Microsoft Excel yüklü bir bilgisayar.</span><span class="sxs-lookup"><span data-stu-id="1797e-110">A computer on which Visual Studio and Microsoft Excel are installed.</span></span>  
  
-   <span data-ttu-id="1797e-111">.NET Framework 4 veya sonraki sürümünü ve Excel farklı bir sürümü yüklü ikinci bir bilgisayar.</span><span class="sxs-lookup"><span data-stu-id="1797e-111">A second computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
##  <a name="BKMK_createapp"></a><span data-ttu-id="1797e-112">Microsoft Office birden çok sürümü ile çalışan bir uygulama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1797e-112">To create an application that works with multiple versions of Microsoft Office</span></span>  
  
1.  <span data-ttu-id="1797e-113">Excel yüklü olmadığı bir bilgisayara Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="1797e-113">Start Visual Studio on a computer on which Excel is installed.</span></span>  
  
2.  <span data-ttu-id="1797e-114">Üzerinde **dosya** menüsünde seçin **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="1797e-114">On the **File** menu, choose **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="1797e-115">İçinde **yeni proje** iletişim kutusunda **proje türleri** bölmesinde olduğundan emin olun **Windows** seçilir.</span><span class="sxs-lookup"><span data-stu-id="1797e-115">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="1797e-116">Seçin **konsol uygulaması** içinde **şablonları** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="1797e-116">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="1797e-117">İçinde **adı** kutusuna `CreateExcelWorkbook`ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1797e-117">In the **Name** box, enter `CreateExcelWorkbook`, and then choose the **OK** button.</span></span> <span data-ttu-id="1797e-118">Yeni Proje oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1797e-118">The new project is created.</span></span>  
  
4.  <span data-ttu-id="1797e-119">İçinde **Çözüm Gezgini**, kısayol menüsünü açın **başvuruları** klasörünü ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="1797e-119">In **Solution Explorer**, open the shortcut menu for the **References** folder and then choose **Add Reference**.</span></span>  
  
5.  <span data-ttu-id="1797e-120">Üzerinde **.NET** sekmesinde, en son sürümünü seçin `Microsoft.Office.Interop.Excel`.</span><span class="sxs-lookup"><span data-stu-id="1797e-120">On the **.NET** tab, choose the most recent version of `Microsoft.Office.Interop.Excel`.</span></span> <span data-ttu-id="1797e-121">Örneğin, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="1797e-121">For example, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span></span> <span data-ttu-id="1797e-122">Seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1797e-122">Choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="1797e-123">Başvuruları listesinde **CreateExcelWorkbook** projesi, başvurusunu seçin `Microsoft.Office.Interop.Excel` , önceki adımda eklediğiniz.</span><span class="sxs-lookup"><span data-stu-id="1797e-123">In the list of references for the **CreateExcelWorkbook** project, select the reference for `Microsoft.Office.Interop.Excel` that you added in the previous step.</span></span> <span data-ttu-id="1797e-124">İçinde **özellikleri** penceresinde olduğundan emin olun `Embed Interop Types` özelliği ayarlanmış `True`.</span><span class="sxs-lookup"><span data-stu-id="1797e-124">In the **Properties** window, make sure that the `Embed Interop Types` property is set to `True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1797e-125">Bu kılavuzda oluşturulan uygulama nedeniyle katıştırılmış birlikte çalışma türü bilgileri Microsoft Office'in farklı sürümlerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="1797e-125">The application created in this walkthrough runs with different versions of Microsoft Office because of the embedded interop type information.</span></span> <span data-ttu-id="1797e-126">Varsa `Embed Interop Types` özelliği ayarlanmış `False`, her sürümü ile uygulamanın çalıştırılacağı Microsoft Office PIA eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1797e-126">If the `Embed Interop Types` property is set to `False`, you must include a PIA for each version of Microsoft Office that the application will run with.</span></span>  
  
7.  <span data-ttu-id="1797e-127">Açık **Program.cs** dosya.</span><span class="sxs-lookup"><span data-stu-id="1797e-127">Open the **Program.cs** file.</span></span> <span data-ttu-id="1797e-128">Dosyasındaki kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="1797e-128">Replace the code in the file with the following code:</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.IO;  
    using Excel = Microsoft.Office.Interop.Excel;  
  
    namespace CreateExcelWorkbook  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                int[] values = {4, 6, 18, 2, 1, 76, 0, 3, 11};  
  
                CreateWorkbook(values, @"C:\SampleFolder\SampleWorkbook.xls");  
            }  
  
            static void CreateWorkbook(int[] values, string filePath)  
            {  
                Excel.Application excelApp = null;  
                Excel.Workbook wkbk;  
                Excel.Worksheet sheet;  
  
                try  
                {  
                        // Start Excel and create a workbook and worksheet.  
                        excelApp = new Excel.Application();  
                        wkbk = excelApp.Workbooks.Add();  
                        sheet = wkbk.Sheets.Add() as Excel.Worksheet;  
                        sheet.Name = "Sample Worksheet";  
  
                        // Write a column of values.  
                        // In the For loop, both the row index and array index start at 1.  
                        // Therefore the value of 4 at array index 0 is not included.  
                        for (int i = 1; i < values.Length; i++)  
                        {  
                            sheet.Cells[i, 1] = values[i];  
                        }  
  
                        // Suppress any alerts and save the file. Create the directory   
                        // if it does not exist. Overwrite the file if it exists.  
                        excelApp.DisplayAlerts = false;  
                        string folderPath = Path.GetDirectoryName(filePath);  
                        if (!Directory.Exists(folderPath))  
                        {  
                            Directory.CreateDirectory(folderPath);  
                        }  
                        wkbk.SaveAs(filePath);  
                }  
                catch  
                {  
                }  
                finally  
                {  
                    sheet = null;  
                    wkbk = null;  
  
                    // Close Excel.  
                    excelApp.Quit();  
                    excelApp = null;  
                }  
            }  
        }  
    }  
    ```  
  
8.  <span data-ttu-id="1797e-129">Projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="1797e-129">Save the project.</span></span>  
  
9. <span data-ttu-id="1797e-130">Projesini derlemeyi ve çalıştırmayı için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1797e-130">Press CTRL+F5 to build and run the project.</span></span> <span data-ttu-id="1797e-131">Bir Excel çalışma kitabı örnek kodda belirtilen konumda oluşturulduğunu doğrulayın: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="1797e-131">Verify that an Excel workbook has been created at the location specified in the example code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
##  <a name="BKMK_publishapp"></a><span data-ttu-id="1797e-132">Microsoft Office'in farklı bir sürümü yüklü olduğu bir bilgisayar için uygulama yayımlamak için</span><span class="sxs-lookup"><span data-stu-id="1797e-132">To publish the application to a computer on which a different version of Microsoft Office is installed</span></span>  
  
1.  <span data-ttu-id="1797e-133">Bu kılavuzda Visual Studio tarafından oluşturulan projeyi açın.</span><span class="sxs-lookup"><span data-stu-id="1797e-133">Open the project created by this walkthrough in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="1797e-134">Üzerinde **yapı** menüsünde seçin **yayımlama CreateExcelWorkbook**.</span><span class="sxs-lookup"><span data-stu-id="1797e-134">On the **Build** menu, choose **Publish CreateExcelWorkbook**.</span></span> <span data-ttu-id="1797e-135">Uygulama, yüklenebilir bir sürümünü oluşturmak için Yayımlama Sihirbazı'nın adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="1797e-135">Follow the steps of the Publish Wizard to create an installable version of the application.</span></span> <span data-ttu-id="1797e-136">Daha fazla bilgi için bkz: [Yayımlama Sihirbazı (Visual Studio'da Office Geliştirme)](https://msdn.microsoft.com/library/bb625071).</span><span class="sxs-lookup"><span data-stu-id="1797e-136">For more information, see [Publish Wizard (Office Development in Visual Studio)](https://msdn.microsoft.com/library/bb625071).</span></span>  
  
3.  <span data-ttu-id="1797e-137">Uygulama, .NET Framework 4 veya sonraki sürümünü ve Excel farklı bir sürümü yüklü bir bilgisayara yükleyin.</span><span class="sxs-lookup"><span data-stu-id="1797e-137">Install the application on a computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
4.  <span data-ttu-id="1797e-138">Yükleme tamamlandığında, yüklenen bir program çalıştır.</span><span class="sxs-lookup"><span data-stu-id="1797e-138">When the installation is finished, run the installed program.</span></span>  
  
5.  <span data-ttu-id="1797e-139">Bir Excel çalışma kitabı örnek kodda belirtilen konumda oluşturulduğunu doğrulayın: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="1797e-139">Verify that an Excel workbook has been created at the location specified in the sample code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1797e-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1797e-140">See Also</span></span>  
 [<span data-ttu-id="1797e-141">İzlenecek yol: Visual Studio'da (C#) yönetilen derlemelerden türler katıştırma</span><span class="sxs-lookup"><span data-stu-id="1797e-141">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
 [<span data-ttu-id="1797e-142">/ Link (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="1797e-142">/link (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)
