---
title: 'Nasıl yapılır: PrintDialog Bileşenini Görüntüleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
ms.openlocfilehash: d8765187522f8becf24b519434b7c170c1c755b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532193"
---
# <a name="how-to-display-the-printdialog-component"></a><span data-ttu-id="489fe-102">Nasıl yapılır: PrintDialog Bileşenini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="489fe-102">How to: Display the PrintDialog Component</span></span>
<span data-ttu-id="489fe-103"><xref:System.Windows.Forms.PrintDialog> Birçok kullanıcılarınızın aşina olacaktır standart Windows yazdırma iletişim kutusu bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="489fe-103">The <xref:System.Windows.Forms.PrintDialog> component is the standard Windows print dialog box that many of your users will be familiar with.</span></span> <span data-ttu-id="489fe-104">Kullanıcılarınızın rahat hemen olacağından kullanabilmeniz için faydalı olacaktır <xref:System.Windows.Forms.PrintDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="489fe-104">Because your users will be immediately comfortable with it, it would be beneficial for you to use the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
### <a name="to-display-the-printdialog-component"></a><span data-ttu-id="489fe-105">PrintDialog bileşeni görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="489fe-105">To display the PrintDialog component</span></span>  
  
-   <span data-ttu-id="489fe-106">Çağrı <xref:System.Windows.Forms.Form.ShowDialog%2A> uygulamanızın kodundaki yönteminden.</span><span class="sxs-lookup"><span data-stu-id="489fe-106">Call the <xref:System.Windows.Forms.Form.ShowDialog%2A> method from within the code of your application.</span></span>  
  
     <span data-ttu-id="489fe-107">Bileşen gösterilen sonra kullanıcılar ile yazdırma işinin özelliklerini ayarlama etkileşim.</span><span class="sxs-lookup"><span data-stu-id="489fe-107">Once the component is shown, users will interact with it, setting the properties of the print job.</span></span> <span data-ttu-id="489fe-108">Bunlar kaydedilir <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` sınıfı (ve <xref:System.Drawing.Printing.PageSettings> kullanıcı erişirse, sınıf [PageSetupDialog bileşeni](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) aracılığıyla <xref:System.Windows.Forms.PrintDialog> bileşeni), yazdırma işi ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="489fe-108">These are saved in the <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` class (and the <xref:System.Drawing.Printing.PageSettings> class, if the user accesses the [PageSetupDialog Component](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) through the <xref:System.Windows.Forms.PrintDialog> component) associated with that print job.</span></span> <span data-ttu-id="489fe-109">Yazdırma işinin özelliklerini belirlemek ayarlayın çağrıları özellikleri daha sonra yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="489fe-109">You can then make calls to the properties they set to determine the specifics of the print job.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="489fe-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="489fe-110">See Also</span></span>  
 [<span data-ttu-id="489fe-111">Nasıl yapılır: Standart Windows Forms Yazdırma İşleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="489fe-111">How to: Create Standard Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [<span data-ttu-id="489fe-112">Nasıl yapılır: Bir PrintDialog'dan Çalışma Zamanında Kullanıcı Girdisi Yakalama</span><span class="sxs-lookup"><span data-stu-id="489fe-112">How to: Capture User Input from a PrintDialog at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 [<span data-ttu-id="489fe-113">PrintPreviewDialog Denetimi</span><span class="sxs-lookup"><span data-stu-id="489fe-113">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [<span data-ttu-id="489fe-114">PrintDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="489fe-114">PrintDialog Component</span></span>](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 [<span data-ttu-id="489fe-115">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="489fe-115">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [<span data-ttu-id="489fe-116">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="489fe-116">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)
