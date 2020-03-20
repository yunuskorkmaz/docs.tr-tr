---
title: Standart Yazdırma İşleri Oluşturma
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
ms.openlocfilehash: d9607de7c74132e0d7dce605b16d62c79b7dbccb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182575"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a><span data-ttu-id="446d4-102">Nasıl yapılır: Standart Windows Forms Yazdırma İşleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="446d4-102">How to: Create Standard Windows Forms Print Jobs</span></span>
<span data-ttu-id="446d4-103">Windows Formlarında yazdırmanın <xref:System.Drawing.Printing.PrintDocument> temeli, daha spesifik <xref:System.Drawing.Printing.PrintDocument.PrintPage> olarak olayın bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="446d4-103">The foundation of printing in Windows Forms is the <xref:System.Drawing.Printing.PrintDocument> component—more specifically, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span> <span data-ttu-id="446d4-104"><xref:System.Drawing.Printing.PrintDocument.PrintPage> Olayı işlemek için kod yazarak, neyi yazdırabileceğinizi ve nasıl yazdırılacağınızı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="446d4-104">By writing code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event, you can specify what to print and how to print it.</span></span>  
  
### <a name="to-create-a-print-job"></a><span data-ttu-id="446d4-105">Yazdırma işi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="446d4-105">To create a print job</span></span>  
  
1. <span data-ttu-id="446d4-106">Formunuza <xref:System.Drawing.Printing.PrintDocument> bir bileşen ekleyin.</span><span class="sxs-lookup"><span data-stu-id="446d4-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="446d4-107"><xref:System.Drawing.Printing.PrintDocument.PrintPage> Olayı işlemek için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="446d4-107">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     <span data-ttu-id="446d4-108">Kendi yazdırma mantığınızı kodlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="446d4-108">You will have to code your own printing logic.</span></span> <span data-ttu-id="446d4-109">Ayrıca, yazdırılacak malzemeyi belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="446d4-109">Additionally, you will have to specify the material to be printed.</span></span>  
  
     <span data-ttu-id="446d4-110">Aşağıdaki kod örneğinde, yazdırılacak malzeme olarak hareket etmek üzere <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisi kırmızı dikdörtgen şeklinde bir örnek grafik oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="446d4-110">In the following code example, a sample graphic in the shape of a red rectangle is created in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler to act as material to be printed.</span></span>  
  
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
  
     <span data-ttu-id="446d4-111">(Görsel C# ve Görsel C++) Olay işleyicisini kaydetmek için aşağıdaki kodu formun oluşturucusuna yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="446d4-111">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
     <span data-ttu-id="446d4-112">Ayrıca, her sayfa yazdırıldıkça yazdırılacak toplam sayfa sayısını temsil eden bir tamsayı da dahil olmak üzere, olaylar <xref:System.Drawing.Printing.PrintDocument.BeginPrint> ve <xref:System.Drawing.Printing.PrintDocument.EndPrint> olaylar için kod yazmak da isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="446d4-112">You may also want to write code for the <xref:System.Drawing.Printing.PrintDocument.BeginPrint> and <xref:System.Drawing.Printing.PrintDocument.EndPrint> events, perhaps including an integer representing the total number of pages to print that is decremented as each page prints.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="446d4-113">Kullanıcılarınıza temiz <xref:System.Windows.Forms.PrintDialog> ve verimli bir kullanıcı arabirimi (UI) sağlamak için formunuza bir bileşen ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="446d4-113">You can add a <xref:System.Windows.Forms.PrintDialog> component to your form to provide a clean and efficient user interface (UI) to your users.</span></span> <span data-ttu-id="446d4-114">Bileşenin <xref:System.Windows.Forms.PrintDialog.Document%2A> özelliğini <xref:System.Windows.Forms.PrintDialog> ayarlamak, formunuzda birlikte çalıştığınız yazdırma belgesiyle ilgili özellikleri ayarlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="446d4-114">Setting the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> component enables you to set properties related to the print document you are working with on your form.</span></span> <span data-ttu-id="446d4-115">Bileşen hakkında daha <xref:System.Windows.Forms.PrintDialog> fazla bilgi için [PrintDialog Bileşeni'ne](../controls/printdialog-component-windows-forms.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="446d4-115">For more information about the <xref:System.Windows.Forms.PrintDialog> component, see [PrintDialog Component](../controls/printdialog-component-windows-forms.md).</span></span>  
  
     <span data-ttu-id="446d4-116">Windows Forms yazdırma işlerinin özellikleri hakkında daha fazla bilgi için, programlı bir <xref:System.Drawing.Printing.PrintPageEventArgs>yazdırma işi oluşturma da dahil olmak üzere bkz.</span><span class="sxs-lookup"><span data-stu-id="446d4-116">For more information about the specifics of Windows Forms print jobs, including how to create a print job programmatically, see <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="446d4-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="446d4-117">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="446d4-118">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="446d4-118">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
