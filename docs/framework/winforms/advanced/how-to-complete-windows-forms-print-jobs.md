---
title: 'Nasıl yapılır: Tam bir Windows Forms yazdırma işleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: f7504d645ea1fca6f45b17f79eb576919b782263
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572831"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a><span data-ttu-id="8c9a2-102">Nasıl yapılır: Tam bir Windows Forms yazdırma işleri</span><span class="sxs-lookup"><span data-stu-id="8c9a2-102">How to: Complete Windows Forms Print Jobs</span></span>
<span data-ttu-id="8c9a2-103">Genellikle, sözcük işlemciler ve yazdırma gerektiren diğer uygulamaları yazdırma işi tamamlandığını kullanıcılara bir ileti görüntülemek için seçeneği sunacak.</span><span class="sxs-lookup"><span data-stu-id="8c9a2-103">Frequently, word processors and other applications that involve printing will provide the option to display a message to users that a print job is complete.</span></span> <span data-ttu-id="8c9a2-104">Bu işlevsellik, Windows Forms'ta işleyerek sağlayabilir <xref:System.Drawing.Printing.PrintDocument.EndPrint> olayı <xref:System.Drawing.Printing.PrintDocument> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="8c9a2-104">You can provide this functionality in your Windows Forms by handling the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 <span data-ttu-id="8c9a2-105">Aşağıdaki yordam, Windows tabanlı bir uygulama ile oluşturduğunuz gerektirir bir <xref:System.Drawing.Printing.PrintDocument> bileşen üzerindeki, Windows tabanlı bir uygulama yazdırma etkinleştirme standart yoludur.</span><span class="sxs-lookup"><span data-stu-id="8c9a2-105">The following procedure requires that you have created a Windows-based application with a <xref:System.Drawing.Printing.PrintDocument> component on it, which is the standard way of enabling printing from a Windows-based application.</span></span> <span data-ttu-id="8c9a2-106">Kullanarak Windows Forms yazdırma hakkında daha fazla bilgi için <xref:System.Drawing.Printing.PrintDocument> bileşeni Bkz [nasıl yapılır: Standart Windows Forms yazdırma işleri oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="8c9a2-106">For more information about printing from Windows Forms using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Create Standard Windows Forms Print Jobs](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md).</span></span>  
  
### <a name="to-complete-a-print-job"></a><span data-ttu-id="8c9a2-107">Yazdırma işi tamamlamak için</span><span class="sxs-lookup"><span data-stu-id="8c9a2-107">To complete a print job</span></span>  
  
1.  <span data-ttu-id="8c9a2-108">Ayarlama <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> özelliği <xref:System.Drawing.Printing.PrintDocument> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="8c9a2-108">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2.  <span data-ttu-id="8c9a2-109">İşlemek için kod yazma <xref:System.Drawing.Printing.PrintDocument.EndPrint> olay.</span><span class="sxs-lookup"><span data-stu-id="8c9a2-109">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event.</span></span>  
  
     <span data-ttu-id="8c9a2-110">Aşağıdaki kod örneğinde, belgeyi yazdırma tamamlandığını belirten bir ileti kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8c9a2-110">In the following code example, a message box is displayed, indicating that the document has finished printing.</span></span>  
  
    ```vb  
    Private Sub PrintDocument1_EndPrint(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintEventArgs) Handles PrintDocument1.EndPrint  
       MessageBox.Show(PrintDocument1.DocumentName + " has finished printing.")  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_EndPrint(object sender,   
    System.Drawing.Printing.PrintEventArgs e)  
    {  
       MessageBox.Show(printDocument1.DocumentName +   
          " has finished printing.");  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_EndPrint(System::Object ^ sender,  
          System::Drawing::Printing::PrintEventArgs ^ e)  
       {  
          MessageBox::Show(String::Concat(printDocument1->DocumentName,  
             " has finished printing."));  
       }  
    ```  
  
     <span data-ttu-id="8c9a2-111">(Visual C# ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="8c9a2-111">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.EndPrint += new  
       System.Drawing.Printing.PrintEventHandler  
       (this.printDocument1_EndPrint);  
    ```  
  
    ```cpp  
    this->printDocument1->EndPrint += gcnew  
       System::Drawing::Printing::PrintEventHandler  
       (this, &Form1::printDocument1_EndPrint);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8c9a2-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c9a2-112">See also</span></span>
- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="8c9a2-113">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="8c9a2-113">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
