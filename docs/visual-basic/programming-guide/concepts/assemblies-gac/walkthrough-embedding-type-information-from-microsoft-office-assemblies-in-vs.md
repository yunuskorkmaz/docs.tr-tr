---
title: "İzlenecek yol: Visual Studio'da (Visual Basic) Microsoft Office derlemelerinden tür bilgilerini katıştırma"
ms.date: 07/20/2015
ms.assetid: 26b44286-5066-4ad4-8e6a-c24902be347c
ms.openlocfilehash: 6a28e95f9c3cfcc2481c8f4f9f83303648df43cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643828"
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-visual-basic"></a>İzlenecek yol: Visual Studio'da (Visual Basic) Microsoft Office derlemelerinden tür bilgilerini katıştırma
COM nesneleri başvuruda bulunan bir uygulamada tür bilgilerini katıştırma, birincil birlikte çalışma derlemesi (PIA) gereksinimini ortadan kaldırabilirsiniz. Ayrıca, katıştırılmış tür bilgisi sürüm bağımsızlığı, uygulamanız için elde etmenizi sağlar. Diğer bir deyişle, programınız belirli PIA her sürüm için gerek kalmadan COM kitaplığı birden fazla sürümünü türlerinden kullanacak şekilde yazılabilir. Bu, Microsoft Office kitaplıklarından nesneleri kullanan uygulamalar için ortak bir senaryodur. Tür bilgilerini katıştırma farklı sürümlerini Microsoft Office programı veya Microsoft Office her sürümü PIA yeniden dağıtmak zorunda kalmadan farklı bilgisayarlarda çalışmak için bir programın aynı yapı sağlar.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuz aşağıdakileri gerektirir:  
  
-   Visual Studio ve Microsoft Excel yüklü bir bilgisayar.  
  
-   .NET Framework 4 veya sonraki sürümünü ve Excel farklı bir sürümü yüklü ikinci bir bilgisayar.  
  
##  <a name="BKMK_createapp"></a> Microsoft Office birden çok sürümü ile çalışan bir uygulama oluşturmak için  
  
1.  Excel yüklü olmadığı bir bilgisayara Visual Studio'yu başlatın.  
  
2.  Üzerinde **dosya** menüsünde seçin **yeni**, **proje**.  
  
3.  İçinde **yeni proje** iletişim kutusunda **proje türleri** bölmesinde olduğundan emin olun **Windows** seçilir. Seçin **konsol uygulaması** içinde **şablonları** bölmesi. İçinde **adı** kutusuna `CreateExcelWorkbook`ve ardından **Tamam** düğmesi. Yeni Proje oluşturulur.  
  
4.  CreateExcelWorkbook proje için kısayol menüsünü açın ve ardından **özellikleri**. Seçin **başvuruları** sekmesi. Seçin **Ekle** düğmesi.  
  
5.  Üzerinde **.NET** sekmesinde, en son sürümünü seçin `Microsoft.Office.Interop.Excel`. Örneğin, **Microsoft.Office.Interop.Excel 14.0.0.0**. Seçin **Tamam** düğmesi.  
  
6.  Başvuruları listesinde **CreateExcelWorkbook** projesi, başvurusunu seçin `Microsoft.Office.Interop.Excel` , önceki adımda eklediğiniz. İçinde **özellikleri** penceresinde olduğundan emin olun `Embed Interop Types` özelliği ayarlanmış `True`.  
  
    > [!NOTE]
    >  Bu kılavuzda oluşturulan uygulama nedeniyle katıştırılmış birlikte çalışma türü bilgileri Microsoft Office'in farklı sürümlerinde çalışır. Varsa `Embed Interop Types` özelliği ayarlanmış `False`, her sürümü ile uygulamanın çalıştırılacağı Microsoft Office PIA eklemeniz gerekir.  
  
7.  Module1.vb dosyasını açın. Dosyasındaki kodu aşağıdaki kodla değiştirin:  
  
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
  
8.  Projeyi kaydedin.  
  
9. Projesini derlemeyi ve çalıştırmayı için CTRL + F5 tuşuna basın. Bir Excel çalışma kitabı örnek kodda belirtilen konumda oluşturulduğunu doğrulayın: C:\SampleFolder\SampleWorkbook.xls.  
  
##  <a name="BKMK_publishapp"></a> Microsoft Office'in farklı bir sürümü yüklü olduğu bir bilgisayar için uygulama yayımlamak için  
  
1.  Bu kılavuzda Visual Studio tarafından oluşturulan projeyi açın.  
  
2.  Üzerinde **yapı** menüsünde seçin **yayımlama CreateExcelWorkbook**. Uygulama, yüklenebilir bir sürümünü oluşturmak için Yayımlama Sihirbazı'nın adımları izleyin. Daha fazla bilgi için bkz: [Yayımlama Sihirbazı (Visual Studio'da Office Geliştirme)](https://msdn.microsoft.com/library/bb625071).  
  
3.  Uygulama, .NET Framework 4 veya sonraki sürümünü ve Excel farklı bir sürümü yüklü bir bilgisayara yükleyin.  
  
4.  Yükleme tamamlandığında, yüklenen bir program çalıştır.  
  
5.  Bir Excel çalışma kitabı örnek kodda belirtilen konumda oluşturulduğunu doğrulayın: C:\SampleFolder\SampleWorkbook.xls.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Visual Studio'da (Visual Basic) yönetilen derlemelerden türler katıştırma](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)  
 [/ Link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)
