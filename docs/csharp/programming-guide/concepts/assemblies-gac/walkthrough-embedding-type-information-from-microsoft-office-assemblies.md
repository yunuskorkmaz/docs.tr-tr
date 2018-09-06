---
title: "İzlenecek yol: Visual Studio'da (C#) Microsoft Office derlemelerinden tür bilgilerini katıştırma"
ms.date: 07/20/2015
ms.assetid: 3320e866-01f1-4b7f-8932-049a7b2d2a9b
ms.openlocfilehash: 381173eedc209930e011dfa7f1711167f16d5ef6
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43890720"
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-c"></a>İzlenecek yol: Visual Studio'da (C#) Microsoft Office derlemelerinden tür bilgilerini katıştırma
Tür bilgilerini COM nesnelerine başvuran bir uygulamaya eklerseniz, birincil birlikte çalışma derlemesi (PIA) gereksinimini ortadan kaldırabilir. Ek olarak, gömülü tür bilgileri, uygulamanız için sürüm bağımsızlığı elde etmenizi sağlar. Diğer bir deyişle, programınız her sürüm için belirli bir PIA'ya gerek kalmadan bir COM kitaplığının birden çok sürümünden türler kullanmak üzere yazılabilir. Bu, Microsoft Office kitaplıklarından nesne kullanan uygulamalar için yaygın bir senaryodur. Tür bilgilerini katıştırma farklı Microsoft Office sürümleri program ya da her sürümü Microsoft Office PIA'yı tekrar dağıtma gereği olmaksızın farklı bilgisayarlarda çalışmak için bir programı'nın aynı derlemesini etkinleştirir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yol aşağıdakileri gerektirir:  
  
-   Visual Studio ve Microsoft Excel yüklü olan bir bilgisayar.  
  
-   .NET Framework 4 veya daha yüksek ve farklı bir Excel sürümünün yüklü olan ikinci bir bilgisayar.  
  
##  <a name="BKMK_createapp"></a> Birden çok Microsoft Office sürümü ile çalışan bir uygulama oluşturmak için  
  
1.  Excel yüklü olduğu bir bilgisayarda Visual Studio'yu başlatın.  
  
2.  Üzerinde **dosya** menüsünde seçin **yeni**, **proje**.  
  
3.  İçinde **yeni proje** iletişim kutusundaki **proje türleri** bölmesinde emin olun **Windows** seçilir. Seçin **konsol uygulaması** içinde **şablonları** bölmesi. İçinde **adı** kutusuna `CreateExcelWorkbook`ve ardından **Tamam** düğmesi. Yeni Proje oluşturulur.  
  
4.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **başvuruları** klasörünü ve ardından **Başvuru Ekle**.  
  
5.  Üzerinde **.NET** sekmesini, en son sürümünü `Microsoft.Office.Interop.Excel`. Örneğin, **Microsoft.Office.Interop.Excel 14.0.0.0**. Seçin **Tamam** düğmesi.  
  
6.  Başvuruları listesinde **CreateExcelWorkbook** başvurusunu seçin, proje `Microsoft.Office.Interop.Excel` önceki adımda eklediğiniz. İçinde **özellikleri** penceresinde emin `Embed Interop Types` özelliği `True`.  
  
    > [!NOTE]
    >  Bu izlenecek yolda oluşturulan uygulama, katıştırılmış birlikte çalışma türünden bilgiler nedeniyle farklı Microsoft Office sürümleri ile çalışır. Varsa `Embed Interop Types` özelliği `False`, her uygulamanın birlikte çalışacağı Microsoft Office sürümü için bir PIA eklemelisiniz.  
  
7.  Açık **Program.cs** dosya. Dosyasındaki kodu aşağıdaki kodla değiştirin:  
  
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
  
8.  Projeyi kaydedin.  
  
9. Derleme ve projeyi çalıştırmak için CTRL + F5 tuşlarına basın. Örnek kodda belirtilen konumda bir Excel çalışma kitabının oluşturulduğunu doğrulayın: C:\SampleFolder\SampleWorkbook.xls.  
  
##  <a name="BKMK_publishapp"></a> Uygulamayı farklı bir Microsoft Office sürümü yüklü olan bir bilgisayarda yayınlamak için  
  
1.  Bu kılavuzda Visual Studio tarafından oluşturulan projeyi açın.  
  
2.  Üzerinde **derleme** menüsünde seçin **CreateExcelWorkbook Yayınla**. Uygulamanın yüklenebilir bir sürümünü oluşturmak için yayınlama Sihirbazı'nın adımları izleyin. Daha fazla bilgi için [Yayımlama Sihirbazı (Visual Studio'da Office Geliştirme)](/visualstudio/vsto/publish-wizard-office-development-in-visual-studio).  
  
3.  Uygulama, .NET Framework 4 veya daha yüksek ve farklı bir Excel sürümünün yüklü bir bilgisayara yükleyin.  
  
4.  Yükleme tamamlandığında yüklenen programı çalıştırın.  
  
5.  Örnek kodda belirtilen konumda bir Excel çalışma kitabının oluşturulduğunu doğrulayın: C:\SampleFolder\SampleWorkbook.xls.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [İzlenecek yol: Visual Studio'da (C#) yönetilen derlemelerden türler katıştırma](../../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
- [/ Link (C# Derleyici Seçenekleri)](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)
