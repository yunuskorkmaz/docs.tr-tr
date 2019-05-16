---
title: PrintDialog bileşenini görüntüleme
ms.date: 03/30/2017
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
ms.openlocfilehash: de0acc655bbcf0cfc017d594545fae56cc27f981
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637450"
---
# <a name="how-to-display-the-printdialog-component"></a><span data-ttu-id="6cc30-102">PrintDialog bileşenini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="6cc30-102">How to display the PrintDialog component</span></span>

<span data-ttu-id="6cc30-103"><xref:System.Windows.Forms.PrintDialog> Kullanıcılarınızın birçoğu ile tanıdık gelecektir standart Windows yazdırma iletişim kutusunda bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="6cc30-103">The <xref:System.Windows.Forms.PrintDialog> component is the standard Windows print dialog box that many of your users will be familiar with.</span></span> <span data-ttu-id="6cc30-104">Kullanıcılarınızın rahat hemen olacağından, kullanabilmeniz için faydalı olacaktır <xref:System.Windows.Forms.PrintDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="6cc30-104">Because your users will be immediately comfortable with it, it would be beneficial for you to use the <xref:System.Windows.Forms.PrintDialog> component.</span></span>

## <a name="to-display-the-printdialog-component"></a><span data-ttu-id="6cc30-105">PrintDialog bileşenini görüntüleme için</span><span class="sxs-lookup"><span data-stu-id="6cc30-105">To display the PrintDialog component</span></span>

- <span data-ttu-id="6cc30-106">Çağrı <xref:System.Windows.Forms.Form.ShowDialog%2A> uygulamanızın kodundaki yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6cc30-106">Call the <xref:System.Windows.Forms.Form.ShowDialog%2A> method from within the code of your application.</span></span>

     <span data-ttu-id="6cc30-107">Bileşen gösterilen sonra kullanıcılar, yazdırma işinin özelliklerini ayarlama etkileşim.</span><span class="sxs-lookup"><span data-stu-id="6cc30-107">Once the component is shown, users will interact with it, setting the properties of the print job.</span></span> <span data-ttu-id="6cc30-108">Bunlar kaydedilir <xref:System.Drawing.Printing.PrinterSettings> sınıfı (ve <xref:System.Drawing.Printing.PageSettings> kullanıcı erişirse, sınıf [PageSetupDialog bileşeni](pagesetupdialog-component-windows-forms.md) aracılığıyla <xref:System.Windows.Forms.PrintDialog> bileşeni), yazdırma işi ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="6cc30-108">These are saved in the  <xref:System.Drawing.Printing.PrinterSettings> class (and the <xref:System.Drawing.Printing.PageSettings> class, if the user accesses the [PageSetupDialog Component](pagesetupdialog-component-windows-forms.md) through the <xref:System.Windows.Forms.PrintDialog> component) associated with that print job.</span></span> <span data-ttu-id="6cc30-109">Daha sonra yazdırma işinin özelliklerini belirlemek için ayarladıkları çağrıları özelliklerine de yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6cc30-109">You can then make calls to the properties they set to determine the specifics of the print job.</span></span>

## <a name="see-also"></a><span data-ttu-id="6cc30-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6cc30-110">See also</span></span>

- [<span data-ttu-id="6cc30-111">Nasıl yapılır: Standart Windows Forms yazdırma işleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="6cc30-111">How to: Create Standard Windows Forms Print Jobs</span></span>](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [<span data-ttu-id="6cc30-112">Nasıl yapılır: Kullanıcı girişi bir printdialog'dan çalışma zamanında yakalama</span><span class="sxs-lookup"><span data-stu-id="6cc30-112">How to: Capture User Input from a PrintDialog at Run Time</span></span>](../advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)
- [<span data-ttu-id="6cc30-113">PrintPreviewDialog Denetimi</span><span class="sxs-lookup"><span data-stu-id="6cc30-113">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="6cc30-114">PrintDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="6cc30-114">PrintDialog Component</span></span>](printdialog-component-windows-forms.md)
- [<span data-ttu-id="6cc30-115">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="6cc30-115">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="6cc30-116">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="6cc30-116">Windows Forms Controls</span></span>](index.md)
