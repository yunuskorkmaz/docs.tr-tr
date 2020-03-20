---
title: 'Nasıl Yapılır: PageSetupDialog Bileşenini Kullanarak Sayfa Özelliklerini Belirleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- page properties
- page setup
- PageSetupDialog component
ms.assetid: 6dae05bc-c0fd-4357-bb93-841a1631d98f
ms.openlocfilehash: 8a015c199193dfd9c43bec53cc93cbf9dc201413
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142049"
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a><span data-ttu-id="70177-102">Nasıl Yapılır: PageSetupDialog Bileşenini Kullanarak Sayfa Özelliklerini Belirleme</span><span class="sxs-lookup"><span data-stu-id="70177-102">How to: Determine Page Properties Using the PageSetupDialog Component</span></span>
<span data-ttu-id="70177-103">[PageSetupDialog](pagesetupdialog-component-windows-forms.md) bileşeni, bir belge için kullanıcıya düzen, kağıt boyutu ve diğer sayfa düzeni seçeneklerini sunar.</span><span class="sxs-lookup"><span data-stu-id="70177-103">The [PageSetupDialog](pagesetupdialog-component-windows-forms.md) component presents layout, paper size, and other page layout choices to the user for a document.</span></span>  
  
 <span data-ttu-id="70177-104"><xref:System.Drawing.Printing.PrintDocument> Sınıfın bir örneğini belirtmeniz gerekir, bu yazdırılacak belgedir.</span><span class="sxs-lookup"><span data-stu-id="70177-104">You need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class—this is the document to be printed.</span></span> <span data-ttu-id="70177-105">Ayrıca, bileşenin kullanıcıya sunulan sayfa biçimlendirme seçeneklerini kısmen nasıl <xref:System.Windows.Forms.PageSetupDialog> belirlediği nden, kullanıcıların bilgisayarında yerel olarak veya ağ üzerinden bir yazıcı yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="70177-105">Additionally, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PageSetupDialog> component determines the page formatting choices presented to the user.</span></span>  
  
 <span data-ttu-id="70177-106"><xref:System.Windows.Forms.PageSetupDialog> Bileşenle çalışmanın önemli bir yönü de <xref:System.Drawing.Printing.PageSettings> sınıfla nasıl etkileşimde olduğudur.</span><span class="sxs-lookup"><span data-stu-id="70177-106">An important aspect of working with the <xref:System.Windows.Forms.PageSetupDialog> component is how it interacts with the <xref:System.Drawing.Printing.PageSettings> class.</span></span> <span data-ttu-id="70177-107">Sınıf, <xref:System.Drawing.Printing.PageSettings> kağıt yönlendirmesi, sayfanın boyutu ve kenar boşlukları gibi sayfanın yazdırılma biçimini değiştiren ayarları belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="70177-107">The <xref:System.Drawing.Printing.PageSettings> class is used to specify settings that modify the way a page will be printed, such as paper orientation, the size of the page, and the margins.</span></span> <span data-ttu-id="70177-108">Bu ayarların her biri <xref:System.Drawing.Printing.PageSettings> sınıfın bir özelliği olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="70177-108">Each of these settings is represented as a property of the <xref:System.Drawing.Printing.PageSettings> class.</span></span> <span data-ttu-id="70177-109">Sınıf, <xref:System.Windows.Forms.PageSetupDialog> belgeyle ilişkili (ve özellik <xref:System.Drawing.Printing.PageSettings> <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> olarak temsil edilen) sınıfın belirli bir örneği için bu özellik değerlerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="70177-109">The <xref:System.Windows.Forms.PageSetupDialog> class modifies these property values for a given instance of the <xref:System.Drawing.Printing.PageSettings> class that is associated with the document (and is represented as a <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> property).</span></span>  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a><span data-ttu-id="70177-110">PageSetupDialog bileşenini kullanarak sayfa özelliklerini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="70177-110">To set page properties using the PageSetupDialog component</span></span>  
  
1. <span data-ttu-id="70177-111">İletişim <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> kutusunu görüntülemek için kullanımı belirten <xref:System.Drawing.Printing.PrintDocument> yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="70177-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="70177-112">Aşağıdaki örnekte, <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olay işleyicisi bileşenin bir örneğini <xref:System.Windows.Forms.PageSetupDialog> açar.</span><span class="sxs-lookup"><span data-stu-id="70177-112">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span> <span data-ttu-id="70177-113">Özellikte <xref:System.Windows.Forms.PageSetupDialog.Document%2A> varolan bir belge belirtilir <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> ve özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="70177-113">An existing document is specified in the <xref:System.Windows.Forms.PageSetupDialog.Document%2A> property, and its <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> property is set to `false`.</span></span>  
  
     <span data-ttu-id="70177-114">Örnek, formunuzun bir <xref:System.Windows.Forms.Button> denetimi, <xref:System.Drawing.Printing.PrintDocument> adında `myDocument`bir <xref:System.Windows.Forms.PageSetupDialog> bileşeni ve bir bileşeni olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="70177-114">The example assumes your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       'You will have to specify your own print document.  
       PageSetupDialog1.Document = myDocument  
       ' Sets the print document's color setting to false,  
       ' so that the page will not be printed in color.  
       PageSetupDialog1.Document.DefaultPageSettings.Color = False  
       PageSetupDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       pageSetupDialog1.Document = myDocument;  
       // Sets the print document's color setting to false,  
       // so that the page will not be printed in color.  
       pageSetupDialog1.Document.DefaultPageSettings.Color = false;  
       pageSetupDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void button1_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          pageSetupDialog1->Document = myDocument;  
          // Sets the print document's color setting to false,  
          // so that the page will not be printed in color.  
          pageSetupDialog1->Document->DefaultPageSettings->Color = false;  
          pageSetupDialog1->ShowDialog();  
       }  
    ```  
  
     <span data-ttu-id="70177-115">(Görsel C# ve Görsel C++) Olay işleyicisini kaydetmek için aşağıdaki kodu formun oluşturucusuna yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="70177-115">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="70177-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70177-116">See also</span></span>

- <xref:System.Windows.Forms.PageSetupDialog>
- [<span data-ttu-id="70177-117">Nasıl yapılır: Standart Windows Forms Yazdırma İşleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="70177-117">How to: Create Standard Windows Forms Print Jobs</span></span>](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [<span data-ttu-id="70177-118">PageSetupDialog bileşeni</span><span class="sxs-lookup"><span data-stu-id="70177-118">PageSetupDialog Component</span></span>](pagesetupdialog-component-windows-forms.md)
