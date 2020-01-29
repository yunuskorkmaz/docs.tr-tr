---
title: Yazdırma desteği
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
ms.openlocfilehash: d6e8f60db7afe2f1b04eaae6fe71aa93e5c22cae
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732498"
---
# <a name="windows-forms-print-support"></a><span data-ttu-id="ac4b8-102">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="ac4b8-102">Windows Forms Print Support</span></span>
<span data-ttu-id="ac4b8-103">Windows Forms Yazdırma, öncelikle kullanıcının yazdırmasını sağlamak için [PrintDocument bileşen](../controls/printdocument-component-windows-forms.md) bileşenini ve [Printönizleme iletişim kutusu denetim](../controls/printpreviewdialog-control-windows-forms.md) denetimi, [PrintDialog bileşeni](../controls/printdialog-component-windows-forms.md) ve [PageSetupDialog bileşen](../controls/pagesetupdialog-component-windows-forms.md) bileşenlerini kullanarak Windows işletim sistemine alışkın kullanıcılara tanıdık bir grafik arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac4b8-103">Printing in Windows Forms consists primarily of using the [PrintDocument Component](../controls/printdocument-component-windows-forms.md) component to enable the user to print, and the [PrintPreviewDialog Control](../controls/printpreviewdialog-control-windows-forms.md) control, [PrintDialog Component](../controls/printdialog-component-windows-forms.md) and [PageSetupDialog Component](../controls/pagesetupdialog-component-windows-forms.md) components to provide a familiar graphical interface to users accustomed to the Windows operating system.</span></span>  
  
 <span data-ttu-id="ac4b8-104">Genellikle <xref:System.Drawing.Printing.PrintDocument> bileşenin yeni bir örneğini oluşturur, <xref:System.Drawing.Printing.PrinterSettings> ve <xref:System.Drawing.Printing.PageSettings> sınıfları kullanarak neyin yazdırılacağını tanımlayan özellikleri ayarlar ve belgeyi gerçekten yazdırmak için <xref:System.Drawing.Printing.PrintDocument.Print%2A> yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac4b8-104">Typically, you create a new instance of the <xref:System.Drawing.Printing.PrintDocument> component, set the properties that describe what to print using the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to actually print the document.</span></span>  
  
 <span data-ttu-id="ac4b8-105">Windows tabanlı bir uygulamadan yazdırma işlemi sırasında, <xref:System.Drawing.Printing.PrintDocument> bileşeni, kullanıcıların yazdırmanın meydana geldiğini ve yazdırma işinin iptal edilmesine izin vermek için bir yazdırmayı iptal et iletişim kutusunu gösterecektir.</span><span class="sxs-lookup"><span data-stu-id="ac4b8-105">During the course of printing from a Windows-based application, the <xref:System.Drawing.Printing.PrintDocument> component will show an abort print dialog box to alert users to the fact that printing is occurring and to allow the print job to be canceled.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac4b8-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ac4b8-106">In This Section</span></span>  
 [<span data-ttu-id="ac4b8-107">Nasıl yapılır: Standart Windows Forms Yazdırma İşleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ac4b8-107">How to: Create Standard Windows Forms Print Jobs</span></span>](how-to-create-standard-windows-forms-print-jobs.md)  
 <span data-ttu-id="ac4b8-108"><xref:System.Drawing.Printing.PrintDocument> bileşeninin bir Windows formdan yazdırılması için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac4b8-108">Explains how to use the <xref:System.Drawing.Printing.PrintDocument> component to print from a Windows Form.</span></span>  
  
 [<span data-ttu-id="ac4b8-109">Nasıl yapılır: Bir PrintDialog'dan Çalışma Zamanında Kullanıcı Girdisi Yakalama</span><span class="sxs-lookup"><span data-stu-id="ac4b8-109">How to: Capture User Input from a PrintDialog at Run Time</span></span>](how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 <span data-ttu-id="ac4b8-110">Seçilen yazdırma seçeneklerinin <xref:System.Windows.Forms.PrintDialog> bileşeni kullanılarak programlı bir şekilde nasıl değiştirileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ac4b8-110">Explains how to modify selected print options programmatically using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="ac4b8-111">Nasıl yapılır: Windows Forms'ta Bir Kullanıcının Bilgisayarına Bağlanan Yazıcıları Seçme</span><span class="sxs-lookup"><span data-stu-id="ac4b8-111">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>](how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 <span data-ttu-id="ac4b8-112">Çalışma zamanında <xref:System.Windows.Forms.PrintDialog> bileşeni kullanılarak yazdırılacak yazıcının değiştirilmesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac4b8-112">Describes changing the printer to print to using the <xref:System.Windows.Forms.PrintDialog> component at run time.</span></span>  
  
 [<span data-ttu-id="ac4b8-113">Nasıl yapılır: Windows Forms'ta Grafik Yazdırma</span><span class="sxs-lookup"><span data-stu-id="ac4b8-113">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)  
 <span data-ttu-id="ac4b8-114">Yazıcıya grafik gönderilmesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac4b8-114">Describes sending graphics to the printer.</span></span>  
  
 [<span data-ttu-id="ac4b8-115">Nasıl yapılır: Windows Forms'ta Çok Sayfalı Metin Dosyası Yazdırma</span><span class="sxs-lookup"><span data-stu-id="ac4b8-115">How to: Print a Multi-Page Text File in Windows Forms</span></span>](how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 <span data-ttu-id="ac4b8-116">Yazıcıya metin gönderilmesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac4b8-116">Describes sending text to the printer.</span></span>  
  
 [<span data-ttu-id="ac4b8-117">Nasıl yapılır: Windows Forms Yazdırma İşlerini Tamamlama</span><span class="sxs-lookup"><span data-stu-id="ac4b8-117">How to: Complete Windows Forms Print Jobs</span></span>](how-to-complete-windows-forms-print-jobs.md)  
 <span data-ttu-id="ac4b8-118">Kullanıcılara bir yazdırma işinin tamamlanmasına yönelik nasıl uyarı verileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac4b8-118">Explains how to alert users to the completion of a print job.</span></span>  
  
 [<span data-ttu-id="ac4b8-119">Nasıl yapılır: Bir Windows Formunu Yazdırma</span><span class="sxs-lookup"><span data-stu-id="ac4b8-119">How to: Print a Windows Form</span></span>](how-to-print-a-windows-form.md)  
 <span data-ttu-id="ac4b8-120">Geçerli formun bir kopyasının nasıl yazdırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac4b8-120">Shows how to print a copy of the current form.</span></span>  
  
 [<span data-ttu-id="ac4b8-121">Nasıl yapılır: Windows Forms'ta Baskı Önizlemeyi Kullanarak Yazdırma</span><span class="sxs-lookup"><span data-stu-id="ac4b8-121">How to: Print in Windows Forms Using Print Preview</span></span>](how-to-print-in-windows-forms-using-print-preview.md)  
 <span data-ttu-id="ac4b8-122">Belge yazdırmak için <xref:System.Windows.Forms.PrintPreviewDialog> nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac4b8-122">Shows how to use a <xref:System.Windows.Forms.PrintPreviewDialog> for printing a document.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ac4b8-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ac4b8-123">Related Sections</span></span>  
 [<span data-ttu-id="ac4b8-124">PrintDocument Bileşeni</span><span class="sxs-lookup"><span data-stu-id="ac4b8-124">PrintDocument Component</span></span>](../controls/printdocument-component-windows-forms.md)  
 <span data-ttu-id="ac4b8-125"><xref:System.Drawing.Printing.PrintDocument> bileşeninin kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac4b8-125">Explains usage of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 [<span data-ttu-id="ac4b8-126">PrintDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="ac4b8-126">PrintDialog Component</span></span>](../controls/printdialog-component-windows-forms.md)  
 <span data-ttu-id="ac4b8-127"><xref:System.Windows.Forms.PrintDialog> bileşeninin kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac4b8-127">Explains usage of the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="ac4b8-128">PrintPreviewDialog Denetimi</span><span class="sxs-lookup"><span data-stu-id="ac4b8-128">PrintPreviewDialog Control</span></span>](../controls/printpreviewdialog-control-windows-forms.md)  
 <span data-ttu-id="ac4b8-129"><xref:System.Windows.Forms.PrintPreviewDialog> denetiminin kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac4b8-129">Explains usage of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
 [<span data-ttu-id="ac4b8-130">PageSetupDialog bileşeni</span><span class="sxs-lookup"><span data-stu-id="ac4b8-130">PageSetupDialog Component</span></span>](../controls/pagesetupdialog-component-windows-forms.md)  
 <span data-ttu-id="ac4b8-131"><xref:System.Windows.Forms.PageSetupDialog> bileşeninin kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac4b8-131">Explains usage of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="ac4b8-132"><xref:System.Drawing.Printing> ad alanındaki sınıfları açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac4b8-132">Describes the classes in the <xref:System.Drawing.Printing> namespace.</span></span>
