---
title: "Nasıl yapılır: Windows Forms'da Bir Kullanıcının Bilgisayarına Bağlanan Yazıcıları Seçme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
ms.openlocfilehash: efd65ff6417b1a63a7f87917c4d9a95dedc464ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318812"
---
# <a name="how-to-choose-the-printers-attached-to-a-users-computer-in-windows-forms"></a><span data-ttu-id="f0a83-102">Nasıl yapılır: Windows Forms'da Bir Kullanıcının Bilgisayarına Bağlanan Yazıcıları Seçme</span><span class="sxs-lookup"><span data-stu-id="f0a83-102">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>
<span data-ttu-id="f0a83-103">Genellikle, kullanıcıların bir yazıcı yazdırmak için varsayılan yazıcı dışında seçmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="f0a83-103">Often, users want to choose a printer other than the default printer to print to.</span></span> <span data-ttu-id="f0a83-104">Kullanıcıların bunları kullanarak yüklü arasından seçim yapmasını sağlayabilirsiniz <xref:System.Windows.Forms.PrintDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="f0a83-104">You can enable users to choose a printer from among those currently installed by using the <xref:System.Windows.Forms.PrintDialog> component.</span></span> <span data-ttu-id="f0a83-105">Aracılığıyla <xref:System.Windows.Forms.PrintDialog> bileşeni <xref:System.Windows.Forms.DialogResult> , <xref:System.Windows.Forms.PrintDialog> bileşen yakalanır ve yazıcı seçmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f0a83-105">Through the <xref:System.Windows.Forms.PrintDialog> component, the <xref:System.Windows.Forms.DialogResult> of the <xref:System.Windows.Forms.PrintDialog> component is captured and used to select the printer.</span></span>  
  
 <span data-ttu-id="f0a83-106">Aşağıdaki yordamda, bir metin dosyası varsayılan yazıcıda yazdırılmak üzere seçilir.</span><span class="sxs-lookup"><span data-stu-id="f0a83-106">In the following procedure, a text file is selected to be printed to the default printer.</span></span> <span data-ttu-id="f0a83-107"><xref:System.Windows.Forms.PrintDialog> Sınıfının örneği sonra.</span><span class="sxs-lookup"><span data-stu-id="f0a83-107">The <xref:System.Windows.Forms.PrintDialog> class is then instantiated.</span></span>  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a><span data-ttu-id="f0a83-108">Bir yazıcı seçin ve ardından dosya yazdırmak için</span><span class="sxs-lookup"><span data-stu-id="f0a83-108">To choose a printer and then print a file</span></span>  
  
1. <span data-ttu-id="f0a83-109">Kullanarak kullanılacak yazıcı seçin <xref:System.Windows.Forms.PrintDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="f0a83-109">Select the printer to be used using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
     <span data-ttu-id="f0a83-110">Aşağıdaki kod örneğinde, işlenen iki olaylar vardır.</span><span class="sxs-lookup"><span data-stu-id="f0a83-110">In the following code example, there are two events being handled.</span></span> <span data-ttu-id="f0a83-111">İlk bir <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olay <xref:System.Windows.Forms.PrintDialog> sınıfı örneği ve kullanıcı tarafından seçilen yazıcı yakalanan <xref:System.Windows.Forms.DialogResult> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f0a83-111">In the first, a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event, the <xref:System.Windows.Forms.PrintDialog> class is instantiated and the printer selected by the user is captured in the <xref:System.Windows.Forms.DialogResult> property.</span></span>  
  
     <span data-ttu-id="f0a83-112">İkinci olay <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayı <xref:System.Drawing.Printing.PrintDocument> bileşeni, örnek bir belge belirtilen yazıcıya yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="f0a83-112">In the second event, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event of the <xref:System.Drawing.Printing.PrintDocument> component, a sample document is printed to the printer specified.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim PrintDialog1 As New PrintDialog()  
       PrintDialog1.Document = PrintDocument1  
       Dim result As DialogResult = PrintDialog1.ShowDialog()  
  
       If (result = DialogResult.OK) Then  
         PrintDocument1.Print()  
       End If   
  
    End Sub  
  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))          
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       PrintDialog printDialog1 = new PrintDialog();  
       printDialog1.Document = printDocument1;  
       DialogResult result = printDialog1.ShowDialog();  
       if (result == DialogResult.OK)  
       {  
          printDocument1.Print();  
       }  
    }  
  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          PrintDialog ^ printDialog1 = gcnew PrintDialog();  
          printDialog1->Document = printDocument1;  
          System::Windows::Forms::DialogResult result =   
             printDialog1->ShowDialog();  
          if (result == DialogResult::OK)  
          {  
             printDocument1->Print();  
          }  
       }  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     <span data-ttu-id="f0a83-113">(Visual C# ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="f0a83-113">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f0a83-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0a83-114">See also</span></span>

- [<span data-ttu-id="f0a83-115">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="f0a83-115">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
