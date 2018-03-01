---
title: "LinkLabel Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 73bbd04b9ef5d2d0c5457dafb794435b3a4db380
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="linklabel-control-overview-windows-forms"></a><span data-ttu-id="bb1de-102">LinkLabel Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="bb1de-102">LinkLabel Control Overview (Windows Forms)</span></span>
<span data-ttu-id="bb1de-103">Windows Forms <xref:System.Windows.Forms.LinkLabel> denetimi Web stili bağlantılar için Windows Forms uygulamaları eklemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb1de-103">The Windows Forms <xref:System.Windows.Forms.LinkLabel> control allows you to add Web-style links to Windows Forms applications.</span></span> <span data-ttu-id="bb1de-104">Kullanabileceğiniz <xref:System.Windows.Forms.LinkLabel> denetimi için kullanabileceğiniz her şeyi <xref:System.Windows.Forms.Label> için kontrol; dosya, klasör veya Web sayfası bağlantısı olarak metnin bir bölümünü de ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bb1de-104">You can use the <xref:System.Windows.Forms.LinkLabel> control for everything that you can use the <xref:System.Windows.Forms.Label> control for; you also can set part of the text as a link to a file, folder, or Web page.</span></span>  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a><span data-ttu-id="bb1de-105">LinkLabel denetimi ile yapabilecekleriniz</span><span class="sxs-lookup"><span data-stu-id="bb1de-105">What You Can Do with the LinkLabel Control</span></span>  
 <span data-ttu-id="bb1de-106">Tüm özellikleri, yöntemleri ve olayları yanı sıra <xref:System.Windows.Forms.Label> denetimi <xref:System.Windows.Forms.LinkLabel> denetim özelliklerini bağlar ve bağlantı renkleri vardır.</span><span class="sxs-lookup"><span data-stu-id="bb1de-106">In addition to all the properties, methods, and events of the <xref:System.Windows.Forms.Label> control, the <xref:System.Windows.Forms.LinkLabel> control has properties for hyperlinks and link colors.</span></span> <span data-ttu-id="bb1de-107"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Özelliği bağlantıyı etkinleştirir metni alanını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bb1de-107">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property sets the area of the text that activates the link.</span></span> <span data-ttu-id="bb1de-108"><xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, Ve <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> özellikleri bağlantı renklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bb1de-108">The <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, and <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> properties set the colors of the link.</span></span> <span data-ttu-id="bb1de-109"><xref:System.Windows.Forms.LinkLabel.LinkClicked> Olay bağlantı metnini seçildiğinde ne olacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="bb1de-109">The <xref:System.Windows.Forms.LinkLabel.LinkClicked> event determines what happens when the link text is selected.</span></span>  
  
 <span data-ttu-id="bb1de-110">En basit kullanımını <xref:System.Windows.Forms.LinkLabel> denetimidir tek bağlantıyı kullanarak görüntülemek için <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> özelliği, ancak aynı zamanda görüntüleyebilir kullanarak birden çok köprü <xref:System.Windows.Forms.LinkLabel.Links%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="bb1de-110">The simplest use of the <xref:System.Windows.Forms.LinkLabel> control is to display a single link using the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property, but you can also display multiple hyperlinks using the <xref:System.Windows.Forms.LinkLabel.Links%2A> property.</span></span> <span data-ttu-id="bb1de-111"><xref:System.Windows.Forms.LinkLabel.Links%2A> Özelliği, bağlantılar koleksiyonu erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb1de-111">The <xref:System.Windows.Forms.LinkLabel.Links%2A> property enables you to access a collection of links.</span></span> <span data-ttu-id="bb1de-112">Ayrıca verileri belirtebilirsiniz <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> her bir özelliğinin <xref:System.Windows.Forms.LinkLabel.Link> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="bb1de-112">You can also specify data in the <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> property of each individual <xref:System.Windows.Forms.LinkLabel.Link> object.</span></span> <span data-ttu-id="bb1de-113">Değeri <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> özelliği, görüntülenecek bir dosyanın konumunu veya bir Web sitesi adresini depolamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bb1de-113">The value of the <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> property can be used to store the location of a file to display or the address of a Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb1de-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bb1de-114">See Also</span></span>  
 <xref:System.Windows.Forms.LinkLabel>  
 [<span data-ttu-id="bb1de-115">Etiket Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bb1de-115">Label Control Overview</span></span>](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [<span data-ttu-id="bb1de-116">Nasıl yapılır: Windows Forms LinkLabel Denetimi ile Bir Nesneye veya Web Sayfasına Bağlama</span><span class="sxs-lookup"><span data-stu-id="bb1de-116">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)  
 [<span data-ttu-id="bb1de-117">Nasıl yapılır: Windows Forms LinkLabel Denetiminin Görünüşünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="bb1de-117">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
