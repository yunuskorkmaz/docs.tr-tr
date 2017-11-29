---
title: "Windows Forms'ta İletişim Kutuları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dialog boxes [Windows Forms], Windows Forms
- Windows Forms dialog boxes
- dialogs [Windows Forms], using in Windows Forms
ms.assetid: d43d022b-451b-490d-9386-dc79d98fbf8a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1660bf08f10a7d4e0db4b7ae8d58fd631986974c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="dialog-boxes-in-windows-forms"></a><span data-ttu-id="1a43a-102">Windows Forms'ta İletişim Kutuları</span><span class="sxs-lookup"><span data-stu-id="1a43a-102">Dialog Boxes in Windows Forms</span></span>
<span data-ttu-id="1a43a-103">İletişim kutuları, kullanıcıyla etkileşim ve bilgi almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1a43a-103">Dialog boxes are used to interact with the user and retrieve information.</span></span> <span data-ttu-id="1a43a-104">Basitçe bir formla iletişim kutusudur kendi <xref:System.Windows.Forms.FormBorderStyle> ayarlanan numaralandırma özelliği `FixedDialog`.</span><span class="sxs-lookup"><span data-stu-id="1a43a-104">In simple terms, a dialog box is a form with its <xref:System.Windows.Forms.FormBorderStyle> enumeration property set to `FixedDialog`.</span></span> <span data-ttu-id="1a43a-105">Windows Forms Tasarımcısı'nda kullanarak kendi özel iletişim kutuları oluşturabileceğiniz [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1a43a-105">You can construct your own custom dialog boxes by using the Windows Forms Designer in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="1a43a-106">Denetimleri gibi ekleme `Label`, `Textbox`, ve `Button` iletişim kutuları, özel gereksinimlerinizi karşılamak için özelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="1a43a-106">Add controls such as `Label`, `Textbox`, and `Button` to customize dialog boxes to your specific needs.</span></span> <span data-ttu-id="1a43a-107">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] De önceden tanımlanmış iletişim kutuları gibi içerir **Dosya Aç** ve kendi uygulamalarınıza uyarlayabilirsiniz ileti kutuları.</span><span class="sxs-lookup"><span data-stu-id="1a43a-107">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] also includes predefined dialog boxes, such as **File Open** and message boxes, which you can adapt for your own applications.</span></span> <span data-ttu-id="1a43a-108">Daha fazla bilgi için bkz: [iletişim kutusu denetimleri ve bileşenleri](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="1a43a-108">For more information, see [Dialog-Box Controls and Components](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1a43a-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1a43a-109">In This Section</span></span>  
 [<span data-ttu-id="1a43a-110">Nasıl yapılır: Windows Forms için iletişim kutularını görüntüleme</span><span class="sxs-lookup"><span data-stu-id="1a43a-110">How to: Display Dialog Boxes for Windows Forms</span></span>](../../../docs/framework/winforms/how-to-display-dialog-boxes-for-windows-forms.md)  
 <span data-ttu-id="1a43a-111">İletişim kutuları gösteren için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a43a-111">Gives directions for showing dialog boxes.</span></span>  
  
-   <span data-ttu-id="1a43a-112">[Nasıl yapılır: Al iletişim kutusu bilgileri seçmeli olarak birden çok özelliklerini kullanma](http://msdn.microsoft.com/library/56taefba\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="1a43a-112">[How to: Retrieve Dialog Box Information Selectively Using Multiple Properties](http://msdn.microsoft.com/library/56taefba\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="1a43a-113">[Nasıl yapılır: bir iletişim kutusunun üst formundan bilgisi alma](http://msdn.microsoft.com/library/k70t19bb\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="1a43a-113">[How to: Retrieve Information from the Parent Form of a Dialog Box](http://msdn.microsoft.com/library/k70t19bb\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="1a43a-114">[İletişim kutuları için kullanıcı girişi](http://msdn.microsoft.com/library/1s9ws53w\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="1a43a-114">[User Input to Dialog Boxes](http://msdn.microsoft.com/library/1s9ws53w\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="1a43a-115">[Nasıl yapılır: iletişim kutuları için sonucu almasını](http://msdn.microsoft.com/library/40x40td1\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="1a43a-115">[How to: Retrieve the Result for Dialog Boxes](http://msdn.microsoft.com/library/40x40td1\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="1a43a-116">[İzlenecek yol: Topluca nesneleri kullanarak iletişim kutusu bilgileri alınıyor](http://msdn.microsoft.com/library/cakx2hdw\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="1a43a-116">[Walkthrough: Retrieving Dialog Box Information Collectively Using Objects](http://msdn.microsoft.com/library/cakx2hdw\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="1a43a-117">[Nasıl yapılır: iletişim kutularını kapatın ve kullanıcı girişi koru](http://msdn.microsoft.com/library/65ad5907\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="1a43a-117">[How to: Close Dialog Boxes and Retain User Input](http://msdn.microsoft.com/library/65ad5907\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="1a43a-118">[Nasıl yapılır: tasarım zamanında iletişim kutuları oluşturma](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="1a43a-118">[How to: Create Dialog Boxes at Design Time](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="1a43a-119">[Nasıl yapılır: ileti kutusu görüntüleme](http://msdn.microsoft.com/library/3tt9e94f\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="1a43a-119">[How to: Display Message Boxes](http://msdn.microsoft.com/library/3tt9e94f\(v=vs.110\))</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1a43a-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="1a43a-120">Related Sections</span></span>  
 [<span data-ttu-id="1a43a-121">İletişim kutusu denetimleri ve bileşenleri</span><span class="sxs-lookup"><span data-stu-id="1a43a-121">Dialog-Box Controls and Components</span></span>](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 <span data-ttu-id="1a43a-122">Önceden tanımlanmış iletişim kutusu denetimleri listeler.</span><span class="sxs-lookup"><span data-stu-id="1a43a-122">Lists the predefined dialog box controls.</span></span>  
  
 [<span data-ttu-id="1a43a-123">Windows formlarının görünüşünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="1a43a-123">Changing the Appearance of Windows Forms</span></span>](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)  
 <span data-ttu-id="1a43a-124">Windows Forms uygulamalarının görünümünü değiştirmek nasıl açıklayan konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="1a43a-124">Contains links to topics that describe how to change the appearance of Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="1a43a-125">TabControl denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="1a43a-125">TabControl Control Overview</span></span>](../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 <span data-ttu-id="1a43a-126">Sekme denetimi nasıl iletişim kutusuna dahil açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1a43a-126">Explains how you incorporate the tab control into a dialog box.</span></span>
