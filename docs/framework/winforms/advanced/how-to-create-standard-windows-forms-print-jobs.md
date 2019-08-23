---
title: 'Nasıl yapılır: Standart Windows Forms Yazdırma İşleri Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms]
- printing [Windows Forms], creating print jobs
- printing [Visual Basic], in Windows applications
ms.assetid: 03342b90-9cfe-40b2-838b-b479a13c5dea
ms.openlocfilehash: 44673e6b26f088e71813aaac26c4b9a03429597a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938236"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a><span data-ttu-id="e7b40-102">Nasıl yapılır: Standart Windows Forms Yazdırma İşleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7b40-102">How to: Create Standard Windows Forms Print Jobs</span></span>
<span data-ttu-id="e7b40-103">Windows Forms ' de yazdırma temeli <xref:System.Drawing.Printing.PrintDocument> bileşeni, özellikle <xref:System.Drawing.Printing.PrintDocument.PrintPage> de olaydır.</span><span class="sxs-lookup"><span data-stu-id="e7b40-103">The foundation of printing in Windows Forms is the <xref:System.Drawing.Printing.PrintDocument> component—more specifically, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span> <span data-ttu-id="e7b40-104"><xref:System.Drawing.Printing.PrintDocument.PrintPage> Olayı işlemek için kod yazarak neyin yazdırılacağını ve nasıl yazdırılacağını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7b40-104">By writing code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event, you can specify what to print and how to print it.</span></span>  
  
### <a name="to-create-a-print-job"></a><span data-ttu-id="e7b40-105">Bir yazdırma işi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e7b40-105">To create a print job</span></span>  
  
1. <span data-ttu-id="e7b40-106">Formunuza bir <xref:System.Drawing.Printing.PrintDocument> bileşen ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e7b40-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="e7b40-107"><xref:System.Drawing.Printing.PrintDocument.PrintPage> Olayı işlemek için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="e7b40-107">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     <span data-ttu-id="e7b40-108">Kendi yazdırma mantığınızı kodlarınızın olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7b40-108">You will have to code your own printing logic.</span></span> <span data-ttu-id="e7b40-109">Ayrıca, yazdırılacak malzemeleri belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7b40-109">Additionally, you will have to specify the material to be printed.</span></span>  
  
     <span data-ttu-id="e7b40-110">Aşağıdaki kod örneğinde, yazdırılacak malzeme olarak davranacak şekilde <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisinde kırmızı dikdörtgen şeklindeki bir örnek grafik oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e7b40-110">In the following code example, a sample graphic in the shape of a red rectangle is created in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler to act as material to be printed.</span></span>  
  
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
  
     <span data-ttu-id="e7b40-111">(Görsel C# ve görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="e7b40-111">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
     <span data-ttu-id="e7b40-112">Ayrıca, her sayfanın yazdırıldığı şekilde azallanan <xref:System.Drawing.Printing.PrintDocument.BeginPrint> toplam <xref:System.Drawing.Printing.PrintDocument.EndPrint> sayfa sayısını temsil eden bir tamsayı de dahil olmak üzere, ve olayları için kod yazmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7b40-112">You may also want to write code for the <xref:System.Drawing.Printing.PrintDocument.BeginPrint> and <xref:System.Drawing.Printing.PrintDocument.EndPrint> events, perhaps including an integer representing the total number of pages to print that is decremented as each page prints.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e7b40-113">Kullanıcılarınıza temiz ve verimli <xref:System.Windows.Forms.PrintDialog> bir kullanıcı arabirimi (UI) sağlamak için formunuza bir bileşen ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7b40-113">You can add a <xref:System.Windows.Forms.PrintDialog> component to your form to provide a clean and efficient user interface (UI) to your users.</span></span> <span data-ttu-id="e7b40-114"><xref:System.Windows.Forms.PrintDialog> Bileşenin özelliğinin ayarlanması, formunuz üzerinde çalıştığınız yazdırma belgesiyle ilgili özellikleri ayarlamanıza olanak sağlar. <xref:System.Windows.Forms.PrintDialog.Document%2A></span><span class="sxs-lookup"><span data-stu-id="e7b40-114">Setting the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> component enables you to set properties related to the print document you are working with on your form.</span></span> <span data-ttu-id="e7b40-115"><xref:System.Windows.Forms.PrintDialog> Bileşen hakkında daha fazla bilgi için bkz. [PrintDialog bileşeni](../controls/printdialog-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e7b40-115">For more information about the <xref:System.Windows.Forms.PrintDialog> component, see [PrintDialog Component](../controls/printdialog-component-windows-forms.md).</span></span>  
  
     <span data-ttu-id="e7b40-116">Program aracılığıyla yazdırma işi oluşturma da dahil olmak üzere Windows Forms Yazdırma işlerinin özellikleri hakkında daha fazla bilgi için bkz <xref:System.Drawing.Printing.PrintPageEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="e7b40-116">For more information about the specifics of Windows Forms print jobs, including how to create a print job programmatically, see <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7b40-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7b40-117">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="e7b40-118">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="e7b40-118">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
