---
title: "Nasıl yapılır: Bir PrintDialog'dan Çalışma Zamanında Kullanıcı Girdisi Yakalama"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print options [Windows Forms], changing at run time
- printing [Windows Forms], options
- print options
- run time [Windows Forms], changing print options
ms.assetid: 438501d8-9a70-4fb3-aae6-e46579aba0c6
ms.openlocfilehash: 554c3c43f8ac4d41ddfc8651472d0b7fbed960bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522882"
---
# <a name="how-to-capture-user-input-from-a-printdialog-at-run-time"></a><span data-ttu-id="c71cd-102">Nasıl yapılır: Bir PrintDialog'dan Çalışma Zamanında Kullanıcı Girdisi Yakalama</span><span class="sxs-lookup"><span data-stu-id="c71cd-102">How to: Capture User Input from a PrintDialog at Run Time</span></span>
<span data-ttu-id="c71cd-103">Tasarım zamanında yazdırma ilgili seçenekleri ayarlayın, ancak bazı durumlarda çalışma zamanında, kullanıcı tarafından yapılan seçimler nedeniyle büyük olasılıkla bu seçeneklerini değiştirmek isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="c71cd-103">While you can set options related to printing at design time, you will sometimes want to change these options at run time, most likely because of choices made by the user.</span></span> <span data-ttu-id="c71cd-104">Kullanarak bir belge yazdırma için kullanıcı girişi yakalama <xref:System.Windows.Forms.PrintDialog> ve <xref:System.Drawing.Printing.PrintDocument> bileşenleri.</span><span class="sxs-lookup"><span data-stu-id="c71cd-104">You can capture user input for printing a document using the <xref:System.Windows.Forms.PrintDialog> and the <xref:System.Drawing.Printing.PrintDocument> components.</span></span>  
  
### <a name="to-change-print-options-programmatically"></a><span data-ttu-id="c71cd-105">Program aracılığıyla yazdırma seçeneklerini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="c71cd-105">To change print options programmatically</span></span>  
  
1.  <span data-ttu-id="c71cd-106">Ekleme bir <xref:System.Windows.Forms.PrintDialog> ve <xref:System.Drawing.Printing.PrintDocument> formunuza bileşen.</span><span class="sxs-lookup"><span data-stu-id="c71cd-106">Add a <xref:System.Windows.Forms.PrintDialog> and a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2.  <span data-ttu-id="c71cd-107">Ayarlama <xref:System.Windows.Forms.PrintDialog.Document%2A> özelliği <xref:System.Windows.Forms.PrintDialog> için <xref:System.Drawing.Printing.PrintDocument> forma eklenir.</span><span class="sxs-lookup"><span data-stu-id="c71cd-107">Set the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> to the <xref:System.Drawing.Printing.PrintDocument> added to the form.</span></span>  
  
    ```vb  
    PrintDialog1.Document = PrintDocument1  
    ```  
  
    ```csharp  
    printDialog1.Document = PrintDocument1;  
    ```  
  
    ```cpp  
    printDialog1->Document = PrintDocument1;  
    ```  
  
3.  <span data-ttu-id="c71cd-108">Görüntü <xref:System.Windows.Forms.PrintDialog> kullanarak bileşen <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c71cd-108">Display the <xref:System.Windows.Forms.PrintDialog> component by using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
    ```vb  
    PrintDialog1.ShowDialog()  
    ```  
  
    ```csharp  
    printDialog1.ShowDialog();  
    ```  
  
    ```cpp  
    printDialog1->ShowDialog();  
    ```  
  
4.  <span data-ttu-id="c71cd-109">Kullanıcının yazdırma seçenekleri iletişim kutusundan kopyalanacak <xref:System.Drawing.Printing.PrinterSettings> özelliği <xref:System.Drawing.Printing.PrintDocument> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="c71cd-109">The user's printing choices from the dialog will be copied to the <xref:System.Drawing.Printing.PrinterSettings> property of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c71cd-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c71cd-110">See Also</span></span>  
 [<span data-ttu-id="c71cd-111">Nasıl yapılır: Windows Forms'ta Çok Sayfalı Metin Dosyası Yazdırma</span><span class="sxs-lookup"><span data-stu-id="c71cd-111">How to: Print a Multi-Page Text File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 [<span data-ttu-id="c71cd-112">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="c71cd-112">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
