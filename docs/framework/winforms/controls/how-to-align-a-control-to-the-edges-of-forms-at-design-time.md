---
title: "Nasıl yapılır: Tasarım Zamanında Denetimi Formların Kenarlarına Hizalama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1232f1f091412017e22f29d529bf7c76b32a4b6d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a><span data-ttu-id="a8a62-102">Nasıl yapılır: Tasarım Zamanında Denetimi Formların Kenarlarına Hizalama</span><span class="sxs-lookup"><span data-stu-id="a8a62-102">How to: Align a Control to the Edges of Forms at Design Time</span></span>
<span data-ttu-id="a8a62-103">Formlarınızı için ayarlayarak hizalar denetiminizi yapabileceğiniz <xref:System.Windows.Forms.Control.Dock%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8a62-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A>.</span></span> <span data-ttu-id="a8a62-104">Bu özellik, Denetim biçiminde bulunduğu belirler.</span><span class="sxs-lookup"><span data-stu-id="a8a62-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="a8a62-105"><xref:System.Windows.Forms.Control.Dock%2A> Özelliği aşağıdaki değerlere ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="a8a62-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>  
  
|<span data-ttu-id="a8a62-106">Ayar</span><span class="sxs-lookup"><span data-stu-id="a8a62-106">Setting</span></span>|<span data-ttu-id="a8a62-107">Denetim etkisi</span><span class="sxs-lookup"><span data-stu-id="a8a62-107">Effect on your control</span></span>|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="a8a62-108">Formun altına noktaları.</span><span class="sxs-lookup"><span data-stu-id="a8a62-108">Docks to the bottom of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="a8a62-109">Formdaki tüm kalan alanı doldurur.</span><span class="sxs-lookup"><span data-stu-id="a8a62-109">Fills all remaining space in the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="a8a62-110">Formun sol tarafına noktaları.</span><span class="sxs-lookup"><span data-stu-id="a8a62-110">Docks to the left side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="a8a62-111">Yoksa her yerden ve onu görünen tarafından belirtilen konumda yerleştirme kendi <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8a62-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A>.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="a8a62-112">Formun sağ tarafındaki noktaları.</span><span class="sxs-lookup"><span data-stu-id="a8a62-112">Docks to the right side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="a8a62-113">Formun üstüne noktaları.</span><span class="sxs-lookup"><span data-stu-id="a8a62-113">Docks to the top of the form.</span></span>|  
  
 <span data-ttu-id="a8a62-114">Bu değerleri kodda de ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a8a62-114">These values can also be set in code.</span></span> <span data-ttu-id="a8a62-115">Daha fazla bilgi için bkz: [nasıl yapılır: biçimlerine kenarları denetimi hizalama](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a8a62-115">For more information, see [How to: Align a Control to the Edges of Forms](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8a62-116">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="a8a62-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a8a62-117">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="a8a62-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a8a62-118">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="a8a62-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-the-dock-property-for-your-control-at-design-time"></a><span data-ttu-id="a8a62-119">Tasarım zamanında denetiminizi Dock özelliğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="a8a62-119">To set the Dock property for your control at design time</span></span>  
  
1.  <span data-ttu-id="a8a62-120">Windows Forms Tasarımcısı'nda, denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="a8a62-120">In the Windows Forms Designer, select your control.</span></span>  
  
2.  <span data-ttu-id="a8a62-121">İçinde **özellikleri** penceresinde, aşağı açılan kutusu sonraki tıklatın <xref:System.Windows.Forms.Control.Dock%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a8a62-121">In the **Properties** window, click the drop-down box next to the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="a8a62-122">Altı olası temsil eden bir grafik arabirim <xref:System.Windows.Forms.Control.Dock%2A> ayarları görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a8a62-122">A graphical interface representing the six possible <xref:System.Windows.Forms.Control.Dock%2A> settings is displayed.</span></span>  
  
3.  <span data-ttu-id="a8a62-123">Uygun ayarı seçin.</span><span class="sxs-lookup"><span data-stu-id="a8a62-123">Choose the appropriate setting.</span></span>  
  
4.  <span data-ttu-id="a8a62-124">Denetim şimdi ayarı tarafından belirlenen şekilde yerleştirme.</span><span class="sxs-lookup"><span data-stu-id="a8a62-124">Your control will now dock in the manner specified by the setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8a62-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8a62-125">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="a8a62-126">Nasıl yapılır: Denetimi Formların Kenarlarına Hizalama</span><span class="sxs-lookup"><span data-stu-id="a8a62-126">How to: Align a Control to the Edges of Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md)  
 [<span data-ttu-id="a8a62-127">İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="a8a62-127">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="a8a62-128">Nasıl yapılır: Windows Forms’da Denetimleri Bağlama</span><span class="sxs-lookup"><span data-stu-id="a8a62-128">How to: Anchor Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [<span data-ttu-id="a8a62-129">Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="a8a62-129">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="a8a62-130">Nasıl yapılır: FlowLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="a8a62-130">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [<span data-ttu-id="a8a62-131">İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="a8a62-131">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="a8a62-132">İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="a8a62-132">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="a8a62-133">Tasarım Zamanında Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="a8a62-133">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
