---
title: "Nasıl yapılır: Standart Windows Forms Yazdırma İşleri Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms]
- printing [Windows Forms], creating print jobs
- printing [Visual Basic], in Windows applications
ms.assetid: 03342b90-9cfe-40b2-838b-b479a13c5dea
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c2b0ce30f76fe7f8cbdc156c4a8ff5abffafae10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a><span data-ttu-id="615fe-102">Nasıl yapılır: Standart Windows Forms Yazdırma İşleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="615fe-102">How to: Create Standard Windows Forms Print Jobs</span></span>
<span data-ttu-id="615fe-103">Windows Forms'ta baskı temelidir <xref:System.Drawing.Printing.PrintDocument> bileşen — daha belirgin olarak <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay.</span><span class="sxs-lookup"><span data-stu-id="615fe-103">The foundation of printing in Windows Forms is the <xref:System.Drawing.Printing.PrintDocument> component—more specifically, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span> <span data-ttu-id="615fe-104">İşlemek için kod yazarak <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay, yazdırma gerekenler ve yazdırmak nasıl belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="615fe-104">By writing code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event, you can specify what to print and how to print it.</span></span>  
  
### <a name="to-create-a-print-job"></a><span data-ttu-id="615fe-105">Bir yazdırma işi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="615fe-105">To create a print job</span></span>  
  
1.  <span data-ttu-id="615fe-106">Ekleme bir <xref:System.Drawing.Printing.PrintDocument> formunuza bileşen.</span><span class="sxs-lookup"><span data-stu-id="615fe-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2.  <span data-ttu-id="615fe-107">İşlemek için kod yazma <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay.</span><span class="sxs-lookup"><span data-stu-id="615fe-107">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     <span data-ttu-id="615fe-108">Yazdırma mantığınızı kod gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="615fe-108">You will have to code your own printing logic.</span></span> <span data-ttu-id="615fe-109">Ayrıca, yazdırılacak malzeme belirtmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="615fe-109">Additionally, you will have to specify the material to be printed.</span></span>  
  
     <span data-ttu-id="615fe-110">Aşağıdaki kod örneğinde bir örnek grafik kırmızı bir dikdörtgen şeklinde oluşturulan <xref:System.Drawing.Printing.PrintDocument.PrintPage> yazdırılması malzeme olarak davranacak şekilde olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="615fe-110">In the following code example, a sample graphic in the shape of a red rectangle is created in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler to act as material to be printed.</span></span>  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     <span data-ttu-id="615fe-111">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="615fe-111">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    ```  
  
    ```cpp  
    printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
     <span data-ttu-id="615fe-112">İçin kod yazma isteyebilirsiniz <xref:System.Drawing.Printing.PrintDocument.BeginPrint> ve <xref:System.Drawing.Printing.PrintDocument.EndPrint> olayları, belki de her bir sayfa yazdırır gibi düşülür yazdırmak için sayfaların toplam sayısını temsil eden bir tamsayı dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="615fe-112">You may also want to write code for the <xref:System.Drawing.Printing.PrintDocument.BeginPrint> and <xref:System.Drawing.Printing.PrintDocument.EndPrint> events, perhaps including an integer representing the total number of pages to print that is decremented as each page prints.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="615fe-113">Ekleyebileceğiniz bir <xref:System.Windows.Forms.PrintDialog> kullanıcılarınıza temiz ve etkili bir kullanıcı arabirimi (UI) sağlamak için formunuza bileşen.</span><span class="sxs-lookup"><span data-stu-id="615fe-113">You can add a <xref:System.Windows.Forms.PrintDialog> component to your form to provide a clean and efficient user interface (UI) to your users.</span></span> <span data-ttu-id="615fe-114">Ayarı <xref:System.Windows.Forms.PrintDialog.Document%2A> özelliği <xref:System.Windows.Forms.PrintDialog> Yazdır ilgili özelliği ayarlamak için belge bileşen etkinleştirir, form üzerinde çalıştığınız.</span><span class="sxs-lookup"><span data-stu-id="615fe-114">Setting the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> component enables you to set properties related to the print document you are working with on your form.</span></span> <span data-ttu-id="615fe-115">Hakkında daha fazla bilgi için <xref:System.Windows.Forms.PrintDialog> bileşeni Bkz [PrintDialog bileşeni](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="615fe-115">For more information about the <xref:System.Windows.Forms.PrintDialog> component, see [PrintDialog Component](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md).</span></span>  
  
     <span data-ttu-id="615fe-116">Daha fazla Windows Forms hakkında bilgi için ayrıntıları yazdırma işlerini bir yazdırma işi programlı olarak oluşturmak nasıl dahil olmak üzere, bkz: <xref:System.Drawing.Printing.PrintPageEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="615fe-116">For more information about the specifics of Windows Forms print jobs, including how to create a print job programmatically, see <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="615fe-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="615fe-117">See Also</span></span>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [<span data-ttu-id="615fe-118">Windows Forms yazdırma desteği</span><span class="sxs-lookup"><span data-stu-id="615fe-118">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
