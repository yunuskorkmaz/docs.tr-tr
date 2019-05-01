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
ms.openlocfilehash: 8e008f2cb4b2f32cdba676e68d9fd790530e2b06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011859"
---
# <a name="windows-forms-print-support"></a><span data-ttu-id="e0e54-102">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="e0e54-102">Windows Forms Print Support</span></span>
<span data-ttu-id="e0e54-103">Windows Forms'ta baskı oluşur öncelikle kullanarak [PrintDocument bileşeni](../controls/printdocument-component-windows-forms.md) yazdırmak, kullanıcının etkinleştirmek için bileşen ve [PrintPreviewDialog denetimi](../controls/printpreviewdialog-control-windows-forms.md) denetimi [PrintDialog Bileşen](../controls/printdialog-component-windows-forms.md) ve [PageSetupDialog bileşeni](../controls/pagesetupdialog-component-windows-forms.md) alışmanızı sağlamak için Windows işletim sistemi kullanıcılara tanıdık bir grafik arabirim sağlamak için bileşenler.</span><span class="sxs-lookup"><span data-stu-id="e0e54-103">Printing in Windows Forms consists primarily of using the [PrintDocument Component](../controls/printdocument-component-windows-forms.md) component to enable the user to print, and the [PrintPreviewDialog Control](../controls/printpreviewdialog-control-windows-forms.md) control, [PrintDialog Component](../controls/printdialog-component-windows-forms.md) and [PageSetupDialog Component](../controls/pagesetupdialog-component-windows-forms.md) components to provide a familiar graphical interface to users accustomed to the Windows operating system.</span></span>  
  
 <span data-ttu-id="e0e54-104">Genellikle, yeni bir örneğini oluşturduğunuz <xref:System.Drawing.Printing.PrintDocument> bileşeni kullanarak yazdırma gerekenler açıklayan özellikleri ayarlamak <xref:System.Drawing.Printing.PrinterSettings> ve <xref:System.Drawing.Printing.PageSettings> sınıfları ve çağrı <xref:System.Drawing.Printing.PrintDocument.Print%2A> gerçekten belge yazdırma için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e0e54-104">Typically, you create a new instance of the <xref:System.Drawing.Printing.PrintDocument> component, set the properties that describe what to print using the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to actually print the document.</span></span>  
  
 <span data-ttu-id="e0e54-105">Windows tabanlı bir uygulama yazdırma süresince <xref:System.Drawing.Printing.PrintDocument> bileşeni iptal uyarı kullanıcıların yazdırma oluştuğunu olgu ve yazdırma işinin izin vermek için bir iptal Yazdır iletişim kutusunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0e54-105">During the course of printing from a Windows-based application, the <xref:System.Drawing.Printing.PrintDocument> component will show an abort print dialog box to alert users to the fact that printing is occurring and to allow the print job to be canceled.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e0e54-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e0e54-106">In This Section</span></span>  
 [<span data-ttu-id="e0e54-107">Nasıl yapılır: Standart Windows Forms yazdırma işleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="e0e54-107">How to: Create Standard Windows Forms Print Jobs</span></span>](how-to-create-standard-windows-forms-print-jobs.md)  
 <span data-ttu-id="e0e54-108">Nasıl kullanılacağını açıklar <xref:System.Drawing.Printing.PrintDocument> bir Windows formdan yazdırmak için bileşen.</span><span class="sxs-lookup"><span data-stu-id="e0e54-108">Explains how to use the <xref:System.Drawing.Printing.PrintDocument> component to print from a Windows Form.</span></span>  
  
 [<span data-ttu-id="e0e54-109">Nasıl yapılır: Kullanıcı girişi bir printdialog'dan çalışma zamanında yakalama</span><span class="sxs-lookup"><span data-stu-id="e0e54-109">How to: Capture User Input from a PrintDialog at Run Time</span></span>](how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 <span data-ttu-id="e0e54-110">Program aracılığıyla kullanarak seçilen yazdırma seçeneklerinin nasıl değiştirileceği açıklanmaktadır <xref:System.Windows.Forms.PrintDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="e0e54-110">Explains how to modify selected print options programmatically using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="e0e54-111">Nasıl yapılır: Windows Forms'ta bir kullanıcının bilgisayarına bağlanan yazıcıları seçme</span><span class="sxs-lookup"><span data-stu-id="e0e54-111">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>](how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 <span data-ttu-id="e0e54-112">Yazıcıyı kullanarak yazdırılacak değiştirmeyi açıklar <xref:System.Windows.Forms.PrintDialog> çalışma zamanında bileşeni.</span><span class="sxs-lookup"><span data-stu-id="e0e54-112">Describes changing the printer to print to using the <xref:System.Windows.Forms.PrintDialog> component at run time.</span></span>  
  
 [<span data-ttu-id="e0e54-113">Nasıl yapılır: Windows Forms'ta grafik yazdırma</span><span class="sxs-lookup"><span data-stu-id="e0e54-113">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)  
 <span data-ttu-id="e0e54-114">Gönderen grafik yazıcıya açıklar.</span><span class="sxs-lookup"><span data-stu-id="e0e54-114">Describes sending graphics to the printer.</span></span>  
  
 [<span data-ttu-id="e0e54-115">Nasıl yapılır: Windows Forms'ta çok sayfalı metin dosyası yazdırma</span><span class="sxs-lookup"><span data-stu-id="e0e54-115">How to: Print a Multi-Page Text File in Windows Forms</span></span>](how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 <span data-ttu-id="e0e54-116">Gönderen metin yazıcı açıklar.</span><span class="sxs-lookup"><span data-stu-id="e0e54-116">Describes sending text to the printer.</span></span>  
  
 [<span data-ttu-id="e0e54-117">Nasıl yapılır: Tam bir Windows Forms yazdırma işleri</span><span class="sxs-lookup"><span data-stu-id="e0e54-117">How to: Complete Windows Forms Print Jobs</span></span>](how-to-complete-windows-forms-print-jobs.md)  
 <span data-ttu-id="e0e54-118">Kullanıcılar bir yazdırma işinin tamamlanması için uyarı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e0e54-118">Explains how to alert users to the completion of a print job.</span></span>  
  
 [<span data-ttu-id="e0e54-119">Nasıl yapılır: Bir Windows formunu yazdırma</span><span class="sxs-lookup"><span data-stu-id="e0e54-119">How to: Print a Windows Form</span></span>](how-to-print-a-windows-form.md)  
 <span data-ttu-id="e0e54-120">Formun geçerli bir kopyasını yazdırmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e0e54-120">Shows how to print a copy of the current form.</span></span>  
  
 [<span data-ttu-id="e0e54-121">Nasıl yapılır: Windows Forms'ta baskı önizlemeyi kullanarak yazdırma</span><span class="sxs-lookup"><span data-stu-id="e0e54-121">How to: Print in Windows Forms Using Print Preview</span></span>](how-to-print-in-windows-forms-using-print-preview.md)  
 <span data-ttu-id="e0e54-122">Nasıl kullanılacağını gösteren bir <xref:System.Windows.Forms.PrintPreviewDialog> belge yazdırma için.</span><span class="sxs-lookup"><span data-stu-id="e0e54-122">Shows how to use a <xref:System.Windows.Forms.PrintPreviewDialog> for printing a document.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e0e54-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e0e54-123">Related Sections</span></span>  
 [<span data-ttu-id="e0e54-124">PrintDocument Bileşeni</span><span class="sxs-lookup"><span data-stu-id="e0e54-124">PrintDocument Component</span></span>](../controls/printdocument-component-windows-forms.md)  
 <span data-ttu-id="e0e54-125">Kullanımını açıklayan <xref:System.Drawing.Printing.PrintDocument> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="e0e54-125">Explains usage of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 [<span data-ttu-id="e0e54-126">PrintDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="e0e54-126">PrintDialog Component</span></span>](../controls/printdialog-component-windows-forms.md)  
 <span data-ttu-id="e0e54-127">Kullanımını açıklayan <xref:System.Windows.Forms.PrintDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="e0e54-127">Explains usage of the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="e0e54-128">PrintPreviewDialog Denetimi</span><span class="sxs-lookup"><span data-stu-id="e0e54-128">PrintPreviewDialog Control</span></span>](../controls/printpreviewdialog-control-windows-forms.md)  
 <span data-ttu-id="e0e54-129">Kullanımını açıklayan <xref:System.Windows.Forms.PrintPreviewDialog> denetimi.</span><span class="sxs-lookup"><span data-stu-id="e0e54-129">Explains usage of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
 [<span data-ttu-id="e0e54-130">PageSetupDialog bileşeni</span><span class="sxs-lookup"><span data-stu-id="e0e54-130">PageSetupDialog Component</span></span>](../controls/pagesetupdialog-component-windows-forms.md)  
 <span data-ttu-id="e0e54-131">Kullanımını açıklayan <xref:System.Windows.Forms.PageSetupDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="e0e54-131">Explains usage of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="e0e54-132">Sınıfları açıklar <xref:System.Drawing.Printing> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e0e54-132">Describes the classes in the <xref:System.Drawing.Printing> namespace.</span></span>
