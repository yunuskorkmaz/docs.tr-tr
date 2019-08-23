---
title: 'Nasıl yapılır: Windows Forms Uygulamalarında Baskı Önizlemede Görüntüleme'
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
ms.openlocfilehash: 8252906de9a574f49617609a4cb08a1e8aa6a992
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929003"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a><span data-ttu-id="a0927-102">Nasıl yapılır: Windows Forms Uygulamalarında Baskı Önizlemede Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a0927-102">How to: Display Print Preview in Windows Forms Applications</span></span>
<span data-ttu-id="a0927-103">Kullanıcıların, genellikle yazdırılmadan <xref:System.Windows.Forms.PrintPreviewDialog> önce bir belgeyi görüntülemesini sağlamak için denetimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0927-103">You can use the <xref:System.Windows.Forms.PrintPreviewDialog> control to enable users to display a document, often before it is to be printed.</span></span>  
  
 <span data-ttu-id="a0927-104">Bunu yapmak için, <xref:System.Drawing.Printing.PrintDocument> sınıfının bir örneğini belirtmeniz gerekir; bu, yazdırılacak belgedir.</span><span class="sxs-lookup"><span data-stu-id="a0927-104">To do this, you need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class; this is the document to be printed.</span></span> <span data-ttu-id="a0927-105"><xref:System.Drawing.Printing.PrintDocument> Bileşen ile baskı önizlemeyi kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Baskı önizlemeyi](../advanced/how-to-print-in-windows-forms-using-print-preview.md)kullanarak Windows Forms yazdır.</span><span class="sxs-lookup"><span data-stu-id="a0927-105">For more information about using print preview with the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print in Windows Forms Using Print Preview](../advanced/how-to-print-in-windows-forms-using-print-preview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a0927-106">Çalışma zamanında <xref:System.Windows.Forms.PrintPreviewDialog> denetimi kullanmak için, kullanıcıların bir belgenin yazdırıldığında nasıl görüneceğine ilişkin bir yazıcı, yerel olarak veya bir ağ <xref:System.Windows.Forms.PrintPreviewDialog> aracılığıyla bilgisayarında yüklü bir yazıcıya sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0927-106">To use the <xref:System.Windows.Forms.PrintPreviewDialog> control at run time, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PrintPreviewDialog> component determines how a document will look when printed.</span></span>  
  
 <span data-ttu-id="a0927-107"><xref:System.Windows.Forms.PrintPreviewDialog> Denetim ,<xref:System.Drawing.Printing.PrinterSettings> sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="a0927-107">The <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span> <span data-ttu-id="a0927-108">Ayrıca, <xref:System.Windows.Forms.PrintPreviewDialog> denetim, <xref:System.Windows.Forms.PrintPreviewDialog> bileşeni olduğu <xref:System.Drawing.Printing.PageSettings> gibi sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="a0927-108">Additionally, the <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PageSettings> class, just as the <xref:System.Windows.Forms.PrintPreviewDialog> component does.</span></span> <span data-ttu-id="a0927-109">Denetimin özelliğinde belirtilen <xref:System.Drawing.Printing.PrinterSettings> <xref:System.Drawing.Printing.PageSettings> yazdırma belgesi hem hem de sınıflarının örneklerine başvurur ve bunlar belgeyi önizleme penceresinde işlemek için kullanılır. <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> <xref:System.Windows.Forms.PrintPreviewDialog></span><span class="sxs-lookup"><span data-stu-id="a0927-109">The print document specified in the <xref:System.Windows.Forms.PrintPreviewDialog> control's <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> property refers to instances of both the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and these are used to render the document in the preview window.</span></span>  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a><span data-ttu-id="a0927-110">Printönizleme Iletişim kutusu denetimini kullanarak sayfaları görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="a0927-110">To view pages using the PrintPreviewDialog control</span></span>  
  
- <span data-ttu-id="a0927-111">Kullanılacak öğesini<xref:System.Drawing.Printing.PrintDocument> belirterek iletişim kutusunu göstermek için <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0927-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="a0927-112">Aşağıdaki kod örneğinde, <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Click> denetimin olay işleyicisi <xref:System.Windows.Forms.PrintPreviewDialog> denetimin bir örneğini açar.</span><span class="sxs-lookup"><span data-stu-id="a0927-112">In the following code example, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="a0927-113">Yazdırma belgesi, <xref:System.Windows.Forms.PrintDialog.Document%2A> özelliğinde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a0927-113">The print document is specified in the <xref:System.Windows.Forms.PrintDialog.Document%2A> property.</span></span> <span data-ttu-id="a0927-114">Aşağıdaki örnekte, bir yazdırma belgesi belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="a0927-114">In the example below, no print document is specified.</span></span>  
  
     <span data-ttu-id="a0927-115">Örnekte formunuzun bir <xref:System.Windows.Forms.Button> denetimi, `myDocument`adlı bir <xref:System.Drawing.Printing.PrintDocument> bileşen ve bir <xref:System.Windows.Forms.PrintPreviewDialog> denetim olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0927-115">The example requires that your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
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
  
     <span data-ttu-id="a0927-116">(Görsel C#, görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="a0927-116">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a0927-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0927-117">See also</span></span>

- [<span data-ttu-id="a0927-118">PrintDocument Bileşeni</span><span class="sxs-lookup"><span data-stu-id="a0927-118">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
- [<span data-ttu-id="a0927-119">PrintPreviewDialog Denetimi</span><span class="sxs-lookup"><span data-stu-id="a0927-119">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="a0927-120">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="a0927-120">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="a0927-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a0927-121">Windows Forms</span></span>](../index.md)
