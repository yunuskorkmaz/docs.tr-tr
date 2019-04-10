---
title: 'Nasıl yapılır: PageSetupDialog Bileşenini Kullanarak Sayfa Özelliklerini Belirleme'
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
ms.openlocfilehash: 6eefe7dd69d02712b650d95ddf14394c10792807
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213709"
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a><span data-ttu-id="9051f-102">Nasıl yapılır: PageSetupDialog Bileşenini Kullanarak Sayfa Özelliklerini Belirleme</span><span class="sxs-lookup"><span data-stu-id="9051f-102">How to: Determine Page Properties Using the PageSetupDialog Component</span></span>
<span data-ttu-id="9051f-103">[PageSetupDialog](pagesetupdialog-component-windows-forms.md) kullanıcıya bir belge için bileşen sunar düzen, sayfa boyutunu ve diğer sayfa düzeni seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="9051f-103">The [PageSetupDialog](pagesetupdialog-component-windows-forms.md) component presents layout, paper size, and other page layout choices to the user for a document.</span></span>  
  
 <span data-ttu-id="9051f-104">Örneği belirtmeniz gereken <xref:System.Drawing.Printing.PrintDocument> sınıfı — belgenin yazdırılması budur.</span><span class="sxs-lookup"><span data-stu-id="9051f-104">You need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class—this is the document to be printed.</span></span> <span data-ttu-id="9051f-105">Ayrıca, bu kısmen olduğundan kullanıcıların kendi bilgisayarlarında yerel olarak veya bir ağ üzerinden yüklü bir yazıcının olmalıdır nasıl <xref:System.Windows.Forms.PageSetupDialog> bileşen sayfasının kullanıcıya sunulan seçenekler biçimlendirme belirler.</span><span class="sxs-lookup"><span data-stu-id="9051f-105">Additionally, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PageSetupDialog> component determines the page formatting choices presented to the user.</span></span>  
  
 <span data-ttu-id="9051f-106">İle çalışmanın önemli bir yönüdür <xref:System.Windows.Forms.PageSetupDialog> bileşendir nasıl etkileşimde <xref:System.Drawing.Printing.PageSettings> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9051f-106">An important aspect of working with the <xref:System.Windows.Forms.PageSetupDialog> component is how it interacts with the <xref:System.Drawing.Printing.PageSettings> class.</span></span> <span data-ttu-id="9051f-107"><xref:System.Drawing.Printing.PageSettings> Sınıfı, bir sayfa yazdırılır, sayfa ve kenar boşlukları boyutunu Kağıt yönlendirmesi gibi şekilde ayarlarını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9051f-107">The <xref:System.Drawing.Printing.PageSettings> class is used to specify settings that modify the way a page will be printed, such as paper orientation, the size of the page, and the margins.</span></span> <span data-ttu-id="9051f-108">Bu ayarların her biri bir özelliği olarak temsil edilen <xref:System.Drawing.Printing.PageSettings> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9051f-108">Each of these settings is represented as a property of the <xref:System.Drawing.Printing.PageSettings> class.</span></span> <span data-ttu-id="9051f-109"><xref:System.Windows.Forms.PageSetupDialog> Sınıfı belirli bir örneği için bu özellik değerlerini değiştirir <xref:System.Drawing.Printing.PageSettings> belgeyle ilişkili sınıf (ve olarak temsil edilen bir <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> özelliği).</span><span class="sxs-lookup"><span data-stu-id="9051f-109">The <xref:System.Windows.Forms.PageSetupDialog> class modifies these property values for a given instance of the <xref:System.Drawing.Printing.PageSettings> class that is associated with the document (and is represented as a <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> property).</span></span>  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a><span data-ttu-id="9051f-110">PageSetupDialog bileşenini kullanarak sayfa özelliklerini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="9051f-110">To set page properties using the PageSetupDialog component</span></span>  
  
1.  <span data-ttu-id="9051f-111">Kullanma <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> iletişim kutusunu görüntülemek için yöntemi belirtme <xref:System.Drawing.Printing.PrintDocument> kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="9051f-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="9051f-112">Aşağıdaki örnekte <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olay işleyicisi örneği açılır <xref:System.Windows.Forms.PageSetupDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="9051f-112">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span> <span data-ttu-id="9051f-113">Var olan bir belgeyi belirtilen <xref:System.Windows.Forms.PageSetupDialog.Document%2A> özelliği ve kendi <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="9051f-113">An existing document is specified in the <xref:System.Windows.Forms.PageSetupDialog.Document%2A> property, and its <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> property is set to `false`.</span></span>  
  
     <span data-ttu-id="9051f-114">Formunuza sahip örnek varsayar bir <xref:System.Windows.Forms.Button> denetimi, bir <xref:System.Drawing.Printing.PrintDocument> bileşeninizin `myDocument`ve <xref:System.Windows.Forms.PageSetupDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="9051f-114">The example assumes your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
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
  
     <span data-ttu-id="9051f-115">(Visual C# ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="9051f-115">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew   
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9051f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9051f-116">See also</span></span>

- <xref:System.Windows.Forms.PageSetupDialog>
- [<span data-ttu-id="9051f-117">Nasıl yapılır: Standart Windows Forms Yazdırma İşleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9051f-117">How to: Create Standard Windows Forms Print Jobs</span></span>](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [<span data-ttu-id="9051f-118">PageSetupDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="9051f-118">PageSetupDialog Component</span></span>](pagesetupdialog-component-windows-forms.md)
