---
title: Windows Forms Yazdırma Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
ms.openlocfilehash: 4ea04d0b6bb8ffa7182d5166ebd66b809adeed34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528560"
---
# <a name="windows-forms-print-support"></a><span data-ttu-id="90489-102">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="90489-102">Windows Forms Print Support</span></span>
<span data-ttu-id="90489-103">Windows Forms'ta baskı oluşur öncelikle kullanarak [PrintDocument bileşeni](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) yazdırmak, kullanıcının etkinleştirmek için bileşen ve [PrintPreviewDialog denetimi](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md) denetimi [PrintDialog Bileşen](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) ve [PageSetupDialog bileşeni](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) bileşenleri Windows işletim sistemine alışmanızı kullanıcılar için tanıdık bir grafik arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="90489-103">Printing in Windows Forms consists primarily of using the [PrintDocument Component](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) component to enable the user to print, and the [PrintPreviewDialog Control](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md) control, [PrintDialog Component](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) and [PageSetupDialog Component](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) components to provide a familiar graphical interface to users accustomed to the Windows operating system.</span></span>  
  
 <span data-ttu-id="90489-104">Genellikle, yeni bir örneğini oluşturmak <xref:System.Drawing.Printing.PrintDocument> bileşeni ne kullanarak yazdırma açıklayın özelliklerini ayarlama <xref:System.Drawing.Printing.PrinterSettings> ve <xref:System.Drawing.Printing.PageSettings> sınıfları ve çağrı <xref:System.Drawing.Printing.PrintDocument.Print%2A> gerçekten belgeyi yazdırmayı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="90489-104">Typically, you create a new instance of the <xref:System.Drawing.Printing.PrintDocument> component, set the properties that describe what to print using the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to actually print the document.</span></span>  
  
 <span data-ttu-id="90489-105">Windows tabanlı bir uygulama yazıcıdan süresince <xref:System.Drawing.Printing.PrintDocument> bileşeni iptal edilmesi uyarı kullanıcıların yazdırma oluştuğunu olgu ve yazdırma işinin izin vermek için bir iptal Yazdır iletişim kutusu gösterilir.</span><span class="sxs-lookup"><span data-stu-id="90489-105">During the course of printing from a Windows-based application, the <xref:System.Drawing.Printing.PrintDocument> component will show an abort print dialog box to alert users to the fact that printing is occurring and to allow the print job to be canceled.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90489-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="90489-106">In This Section</span></span>  
 [<span data-ttu-id="90489-107">Nasıl yapılır: Standart Windows Forms Yazdırma İşleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="90489-107">How to: Create Standard Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 <span data-ttu-id="90489-108">Nasıl kullanılacağı açıklanmaktadır <xref:System.Drawing.Printing.PrintDocument> bir Windows formundan yazdırmak için bileşen.</span><span class="sxs-lookup"><span data-stu-id="90489-108">Explains how to use the <xref:System.Drawing.Printing.PrintDocument> component to print from a Windows Form.</span></span>  
  
 [<span data-ttu-id="90489-109">Nasıl yapılır: Bir PrintDialog'dan Çalışma Zamanında Kullanıcı Girdisi Yakalama</span><span class="sxs-lookup"><span data-stu-id="90489-109">How to: Capture User Input from a PrintDialog at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 <span data-ttu-id="90489-110">Program aracılığıyla kullanarak seçilen yazdırma seçeneklerinin nasıl değiştirileceği açıklanmaktadır <xref:System.Windows.Forms.PrintDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="90489-110">Explains how to modify selected print options programmatically using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="90489-111">Nasıl yapılır: Windows Forms'ta Bir Kullanıcının Bilgisayarına Bağlanan Yazıcıları Seçme</span><span class="sxs-lookup"><span data-stu-id="90489-111">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 <span data-ttu-id="90489-112">Kullanarak yazdırmak için yazıcı değiştirme açıklar <xref:System.Windows.Forms.PrintDialog> çalışma zamanında bileşen.</span><span class="sxs-lookup"><span data-stu-id="90489-112">Describes changing the printer to print to using the <xref:System.Windows.Forms.PrintDialog> component at run time.</span></span>  
  
 [<span data-ttu-id="90489-113">Nasıl yapılır: Windows Forms'ta Grafik Yazdırma</span><span class="sxs-lookup"><span data-stu-id="90489-113">How to: Print Graphics in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)  
 <span data-ttu-id="90489-114">Yazıcı gönderen grafik açıklar.</span><span class="sxs-lookup"><span data-stu-id="90489-114">Describes sending graphics to the printer.</span></span>  
  
 [<span data-ttu-id="90489-115">Nasıl yapılır: Windows Forms'ta Çok Sayfalı Metin Dosyası Yazdırma</span><span class="sxs-lookup"><span data-stu-id="90489-115">How to: Print a Multi-Page Text File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 <span data-ttu-id="90489-116">Gönderen metin yazıcı açıklar.</span><span class="sxs-lookup"><span data-stu-id="90489-116">Describes sending text to the printer.</span></span>  
  
 [<span data-ttu-id="90489-117">Nasıl yapılır: Windows Forms Yazdırma İşlerini Tamamlama</span><span class="sxs-lookup"><span data-stu-id="90489-117">How to: Complete Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-complete-windows-forms-print-jobs.md)  
 <span data-ttu-id="90489-118">Yazdırma işi tamamlandığında kullanıcılara uyarı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="90489-118">Explains how to alert users to the completion of a print job.</span></span>  
  
 [<span data-ttu-id="90489-119">Nasıl yapılır: Bir Windows Formunu Yazdırma</span><span class="sxs-lookup"><span data-stu-id="90489-119">How to: Print a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-windows-form.md)  
 <span data-ttu-id="90489-120">Geçerli formun bir kopyasını yazdırmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="90489-120">Shows how to print a copy of the current form.</span></span>  
  
 [<span data-ttu-id="90489-121">Nasıl yapılır: Windows Forms'ta Baskı Önizlemeyi Kullanarak Yazdırma</span><span class="sxs-lookup"><span data-stu-id="90489-121">How to: Print in Windows Forms Using Print Preview</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md)  
 <span data-ttu-id="90489-122">Nasıl kullanılacağını gösteren bir <xref:System.Windows.Forms.PrintPreviewDialog> belge yazdırma için.</span><span class="sxs-lookup"><span data-stu-id="90489-122">Shows how to use a <xref:System.Windows.Forms.PrintPreviewDialog> for printing a document.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="90489-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="90489-123">Related Sections</span></span>  
 [<span data-ttu-id="90489-124">PrintDocument Bileşeni</span><span class="sxs-lookup"><span data-stu-id="90489-124">PrintDocument Component</span></span>](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 <span data-ttu-id="90489-125">Kullanımını açıklar <xref:System.Drawing.Printing.PrintDocument> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="90489-125">Explains usage of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 [<span data-ttu-id="90489-126">PrintDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="90489-126">PrintDialog Component</span></span>](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 <span data-ttu-id="90489-127">Kullanımını açıklar <xref:System.Windows.Forms.PrintDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="90489-127">Explains usage of the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="90489-128">PrintPreviewDialog Denetimi</span><span class="sxs-lookup"><span data-stu-id="90489-128">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 <span data-ttu-id="90489-129">Kullanımını açıklar <xref:System.Windows.Forms.PrintPreviewDialog> denetim.</span><span class="sxs-lookup"><span data-stu-id="90489-129">Explains usage of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
 [<span data-ttu-id="90489-130">PageSetupDialog bileşeni</span><span class="sxs-lookup"><span data-stu-id="90489-130">PageSetupDialog Component</span></span>](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)  
 <span data-ttu-id="90489-131">Kullanımını açıklar <xref:System.Windows.Forms.PageSetupDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="90489-131">Explains usage of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="90489-132">Sınıflarda açıklar <xref:System.Drawing.Printing> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="90489-132">Describes the classes in the <xref:System.Drawing.Printing> namespace.</span></span>
