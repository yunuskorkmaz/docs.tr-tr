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
ms.openlocfilehash: cfdc8d21b3ddad19fd38eef9cb1c506920da9de6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64609892"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a><span data-ttu-id="a696d-102">Nasıl yapılır: Windows Forms Uygulamalarında Baskı Önizlemede Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a696d-102">How to: Display Print Preview in Windows Forms Applications</span></span>
<span data-ttu-id="a696d-103">Kullanabileceğiniz <xref:System.Windows.Forms.PrintPreviewDialog> yazdırılması için önce bir belge genellikle görüntüleme olanağı denetimi.</span><span class="sxs-lookup"><span data-stu-id="a696d-103">You can use the <xref:System.Windows.Forms.PrintPreviewDialog> control to enable users to display a document, often before it is to be printed.</span></span>  
  
 <span data-ttu-id="a696d-104">Bunu yapmak için örneği belirtmeniz gerekir <xref:System.Drawing.Printing.PrintDocument> sınıfı; yazdırılması için belgeyi budur.</span><span class="sxs-lookup"><span data-stu-id="a696d-104">To do this, you need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class; this is the document to be printed.</span></span> <span data-ttu-id="a696d-105">Baskı Önizleme ile kullanma hakkında daha fazla bilgi için <xref:System.Drawing.Printing.PrintDocument> bileşeni Bkz [nasıl yapılır: Windows Forms'ta baskı önizlemeyi kullanarak yazdırma](../advanced/how-to-print-in-windows-forms-using-print-preview.md).</span><span class="sxs-lookup"><span data-stu-id="a696d-105">For more information about using print preview with the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print in Windows Forms Using Print Preview](../advanced/how-to-print-in-windows-forms-using-print-preview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a696d-106">Kullanılacak <xref:System.Windows.Forms.PrintPreviewDialog> denetimi şu kısmen olduğundan çalışma zamanında, kullanıcıların kendi bilgisayarlarında yerel olarak veya bir ağ üzerinden yüklü bir yazıcının olmalıdır nasıl <xref:System.Windows.Forms.PrintPreviewDialog> bileşeni, bir belge yazdırıldığında nasıl görüneceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="a696d-106">To use the <xref:System.Windows.Forms.PrintPreviewDialog> control at run time, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PrintPreviewDialog> component determines how a document will look when printed.</span></span>  
  
 <span data-ttu-id="a696d-107"><xref:System.Windows.Forms.PrintPreviewDialog> Denetim kullandığı <xref:System.Drawing.Printing.PrinterSettings> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a696d-107">The <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span> <span data-ttu-id="a696d-108">Ayrıca, <xref:System.Windows.Forms.PrintPreviewDialog> denetim kullandığı <xref:System.Drawing.Printing.PageSettings> sınıfı gibi <xref:System.Windows.Forms.PrintPreviewDialog> bileşen yok.</span><span class="sxs-lookup"><span data-stu-id="a696d-108">Additionally, the <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PageSettings> class, just as the <xref:System.Windows.Forms.PrintPreviewDialog> component does.</span></span> <span data-ttu-id="a696d-109">Belirtilen Belgeyi Yazdır <xref:System.Windows.Forms.PrintPreviewDialog> denetimin <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> özelliği hem örneklere başvurur <xref:System.Drawing.Printing.PrinterSettings> ve <xref:System.Drawing.Printing.PageSettings> sınıfları ve bu Önizleme penceresinde belgeyi işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a696d-109">The print document specified in the <xref:System.Windows.Forms.PrintPreviewDialog> control's <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> property refers to instances of both the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and these are used to render the document in the preview window.</span></span>  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a><span data-ttu-id="a696d-110">PrintPreviewDialog denetimi kullanan sayfaları görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="a696d-110">To view pages using the PrintPreviewDialog control</span></span>  
  
- <span data-ttu-id="a696d-111">Kullanma <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> iletişim kutusunu görüntülemek için yöntemi belirtme <xref:System.Drawing.Printing.PrintDocument> kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="a696d-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="a696d-112">Aşağıdaki kod örneğinde, <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olay işleyicisi örneği açılır <xref:System.Windows.Forms.PrintPreviewDialog> denetimi.</span><span class="sxs-lookup"><span data-stu-id="a696d-112">In the following code example, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="a696d-113">Belgeyi Yazdır belirtilen <xref:System.Windows.Forms.PrintDialog.Document%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a696d-113">The print document is specified in the <xref:System.Windows.Forms.PrintDialog.Document%2A> property.</span></span> <span data-ttu-id="a696d-114">Aşağıdaki örnekte, yazdırma belgesi belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="a696d-114">In the example below, no print document is specified.</span></span>  
  
     <span data-ttu-id="a696d-115">Örnek formunuza olmasını gerektirir bir <xref:System.Windows.Forms.Button> denetimi, bir <xref:System.Drawing.Printing.PrintDocument> bileşeninizin `myDocument`ve <xref:System.Windows.Forms.PrintPreviewDialog> denetimi.</span><span class="sxs-lookup"><span data-stu-id="a696d-115">The example requires that your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
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
  
     <span data-ttu-id="a696d-116">(Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="a696d-116">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a696d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a696d-117">See also</span></span>

- [<span data-ttu-id="a696d-118">PrintDocument Bileşeni</span><span class="sxs-lookup"><span data-stu-id="a696d-118">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
- [<span data-ttu-id="a696d-119">PrintPreviewDialog Denetimi</span><span class="sxs-lookup"><span data-stu-id="a696d-119">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="a696d-120">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="a696d-120">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="a696d-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a696d-121">Windows Forms</span></span>](../index.md)
