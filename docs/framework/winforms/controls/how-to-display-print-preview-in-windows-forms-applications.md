---
title: Windows Forms uygulamalarında baskı önizlemeyi görüntüleme
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print preview [Windows Forms], displaying
- printing [Windows Forms], print preview
- examples [Windows Forms], print preview
ms.assetid: e394134c-0886-4517-bd8d-edc4a3749eb5
ms.openlocfilehash: ac02339ad86e491cd047dcd4b0c8841374b3bb2e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745575"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a><span data-ttu-id="2932d-102">Nasıl yapılır: Windows Forms Uygulamalarında Baskı Önizlemede Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="2932d-102">How to: Display Print Preview in Windows Forms Applications</span></span>
<span data-ttu-id="2932d-103">Kullanıcıların, genellikle yazdırılmadan önce bir belgeyi görüntülemesini sağlamak için <xref:System.Windows.Forms.PrintPreviewDialog> denetimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2932d-103">You can use the <xref:System.Windows.Forms.PrintPreviewDialog> control to enable users to display a document, often before it is to be printed.</span></span>  
  
 <span data-ttu-id="2932d-104">Bunu yapmak için <xref:System.Drawing.Printing.PrintDocument> sınıfının bir örneğini belirtmeniz gerekir; Bu, yazdırılacak belgedir.</span><span class="sxs-lookup"><span data-stu-id="2932d-104">To do this, you need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class; this is the document to be printed.</span></span> <span data-ttu-id="2932d-105"><xref:System.Drawing.Printing.PrintDocument> bileşeniyle baskı önizlemeyi kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: baskı önizlemeyi kullanarak Windows Forms Yazdırma](../advanced/how-to-print-in-windows-forms-using-print-preview.md).</span><span class="sxs-lookup"><span data-stu-id="2932d-105">For more information about using print preview with the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print in Windows Forms Using Print Preview](../advanced/how-to-print-in-windows-forms-using-print-preview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2932d-106">Çalışma zamanında <xref:System.Windows.Forms.PrintPreviewDialog> denetimini kullanmak için, kullanıcıların, bir belgenin yazdırıldığında nasıl görüneceğine ilişkin bir, <xref:System.Windows.Forms.PrintPreviewDialog> bileşeninin bir yazıcı üzerinden yerel olarak ya da bir ağ üzerinden yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2932d-106">To use the <xref:System.Windows.Forms.PrintPreviewDialog> control at run time, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PrintPreviewDialog> component determines how a document will look when printed.</span></span>  
  
 <span data-ttu-id="2932d-107"><xref:System.Windows.Forms.PrintPreviewDialog> denetim <xref:System.Drawing.Printing.PrinterSettings> sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="2932d-107">The <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span> <span data-ttu-id="2932d-108">Ayrıca, <xref:System.Windows.Forms.PrintPreviewDialog> bileşeni gibi <xref:System.Windows.Forms.PrintPreviewDialog> denetimi <xref:System.Drawing.Printing.PageSettings> sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="2932d-108">Additionally, the <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PageSettings> class, just as the <xref:System.Windows.Forms.PrintPreviewDialog> component does.</span></span> <span data-ttu-id="2932d-109"><xref:System.Windows.Forms.PrintPreviewDialog> denetiminin <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> özelliğinde belirtilen yazdırma belgesi hem <xref:System.Drawing.Printing.PrinterSettings> hem de <xref:System.Drawing.Printing.PageSettings> sınıflarının örneklerine başvurur ve bunlar belgeyi önizleme penceresinde işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2932d-109">The print document specified in the <xref:System.Windows.Forms.PrintPreviewDialog> control's <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> property refers to instances of both the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and these are used to render the document in the preview window.</span></span>  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a><span data-ttu-id="2932d-110">Printönizleme Iletişim kutusu denetimini kullanarak sayfaları görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="2932d-110">To view pages using the PrintPreviewDialog control</span></span>  
  
- <span data-ttu-id="2932d-111">Kullanılacak <xref:System.Drawing.Printing.PrintDocument> belirterek iletişim kutusunu göstermek için <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2932d-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="2932d-112">Aşağıdaki kod örneğinde, <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.Control.Click> olay işleyicisi <xref:System.Windows.Forms.PrintPreviewDialog> denetiminin bir örneğini açar.</span><span class="sxs-lookup"><span data-stu-id="2932d-112">In the following code example, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="2932d-113">Yazdırma belgesi <xref:System.Windows.Forms.PrintDialog.Document%2A> özelliğinde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2932d-113">The print document is specified in the <xref:System.Windows.Forms.PrintDialog.Document%2A> property.</span></span> <span data-ttu-id="2932d-114">Aşağıdaki örnekte, bir yazdırma belgesi belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="2932d-114">In the example below, no print document is specified.</span></span>  
  
     <span data-ttu-id="2932d-115">Örnekte formunuzun <xref:System.Windows.Forms.Button> denetimi, `myDocument`adlı bir <xref:System.Drawing.Printing.PrintDocument> bileşeni ve <xref:System.Windows.Forms.PrintPreviewDialog> denetimi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2932d-115">The example requires that your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       ' You will have to specify your own print document.  
       PrintPreviewDialog1.Document = myDocument  
       PrintPreviewDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       printPreviewDialog1.Document = myDocument;  
       printPreviewDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          printPreviewDialog1->Document = myDocument;  
          printPreviewDialog1->ShowDialog();  
       }  
    ```  
  
     <span data-ttu-id="2932d-116">(Görsel C#, görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="2932d-116">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2932d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2932d-117">See also</span></span>

- [<span data-ttu-id="2932d-118">PrintDocument Bileşeni</span><span class="sxs-lookup"><span data-stu-id="2932d-118">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
- [<span data-ttu-id="2932d-119">PrintPreviewDialog Denetimi</span><span class="sxs-lookup"><span data-stu-id="2932d-119">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="2932d-120">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="2932d-120">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="2932d-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2932d-121">Windows Forms</span></span>](../index.md)
