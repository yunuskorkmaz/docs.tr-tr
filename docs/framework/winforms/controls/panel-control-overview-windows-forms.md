---
title: "Panel Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8855c88a0ec60cd0d44d73046e44c9614347d90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="panel-control-overview-windows-forms"></a><span data-ttu-id="68d36-102">Panel Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="68d36-102">Panel Control Overview (Windows Forms)</span></span>
<span data-ttu-id="68d36-103">Windows Forms <xref:System.Windows.Forms.Panel> denetimleri, diğer denetimler için tanımlanabilen bir gruplandırma sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="68d36-103">Windows Forms <xref:System.Windows.Forms.Panel> controls are used to provide an identifiable grouping for other controls.</span></span> <span data-ttu-id="68d36-104">Genellikle, işlev tarafından bir form ayırabilir için panelleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="68d36-104">Typically, you use panels to subdivide a form by function.</span></span> <span data-ttu-id="68d36-105">Örneğin, kullanmak için hangi ertesi gün taşıyıcı gibi posta seçeneklerini belirtir. bir sipariş formu olabilir.</span><span class="sxs-lookup"><span data-stu-id="68d36-105">For example, you may have an order form that specifies mailing options such as which overnight carrier to use.</span></span> <span data-ttu-id="68d36-106">Paneldeki tüm seçeneklerin gruplandırma kullanıcı mantıksal bir görsel ipucu verir.</span><span class="sxs-lookup"><span data-stu-id="68d36-106">Grouping all options in a panel gives the user a logical visual cue.</span></span> <span data-ttu-id="68d36-107">Tüm denetimler kolayca taşınabileceği tasarım sırasında zaman — taşıdığınızda <xref:System.Windows.Forms.Panel> denetlemek, tüm çok kapsanan denetimlerinden taşıyın.</span><span class="sxs-lookup"><span data-stu-id="68d36-107">At design time all the controls can be moved easily — when you move the <xref:System.Windows.Forms.Panel> control, all its contained controls move, too.</span></span> <span data-ttu-id="68d36-108">Masası'nda gruplanmış denetimleri aracılığıyla erişilebilir kendi <xref:System.Windows.Forms.Control.Controls%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="68d36-108">The controls grouped in a panel can be accessed through its <xref:System.Windows.Forms.Control.Controls%2A> property.</span></span> <span data-ttu-id="68d36-109">Bu özellik bir koleksiyonunu döndürür <xref:System.Windows.Forms.Control> genellikle bir denetim cast gerekir böylece örnekleri alınan belirli türünü bu şekilde.</span><span class="sxs-lookup"><span data-stu-id="68d36-109">This property returns a collection of <xref:System.Windows.Forms.Control> instances, so you will typically need to cast a control retrieved this way to its specific type.</span></span>  
  
## <a name="panel-versus-groupbox"></a><span data-ttu-id="68d36-110">GroupBox karşı paneli</span><span class="sxs-lookup"><span data-stu-id="68d36-110">Panel Versus GroupBox</span></span>  
 <span data-ttu-id="68d36-111"><xref:System.Windows.Forms.Panel> Denetim benzer <xref:System.Windows.Forms.GroupBox> kontrol; ancak, yalnızca <xref:System.Windows.Forms.Panel> denetim kaydırma çubukları sahip olabilir ve yalnızca <xref:System.Windows.Forms.GroupBox> denetimi, bir resim yazısı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="68d36-111">The <xref:System.Windows.Forms.Panel> control is similar to the <xref:System.Windows.Forms.GroupBox> control; however, only the <xref:System.Windows.Forms.Panel> control can have scroll bars, and only the <xref:System.Windows.Forms.GroupBox> control displays a caption.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="68d36-112">Anahtar Özellikler</span><span class="sxs-lookup"><span data-stu-id="68d36-112">Key Properties</span></span>  
 <span data-ttu-id="68d36-113">Kaydırma çubukları görüntülenecek ayarlamak <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="68d36-113">To display scroll bars, set the <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> property to `true`.</span></span> <span data-ttu-id="68d36-114">Ayarlayarak paneli görünümünü özelleştirebilirsiniz <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, ve <xref:System.Windows.Forms.Panel.BorderStyle%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="68d36-114">You can also customize the appearance of the panel by setting the <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, and <xref:System.Windows.Forms.Panel.BorderStyle%2A> properties.</span></span> <span data-ttu-id="68d36-115">Daha fazla bilgi için <xref:System.Windows.Forms.Control.BackColor%2A> ve <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliklerini görmek [nasıl yapılır: bir panelin arka planını ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md).</span><span class="sxs-lookup"><span data-stu-id="68d36-115">For more information on the <xref:System.Windows.Forms.Control.BackColor%2A> and <xref:System.Windows.Forms.Control.BackgroundImage%2A> properties, see [How to: Set the Background of a Panel](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md).</span></span> <span data-ttu-id="68d36-116"><xref:System.Windows.Forms.Panel.BorderStyle%2A> Özelliği belirler paneli ile görünür hiçbir kenarlık ana hatlarıyla varsa (<xref:System.Windows.Forms.BorderStyle.None>), düz bir satır (<xref:System.Windows.Forms.BorderStyle.FixedSingle>), ya da gölgeli bir satır (<xref:System.Windows.Forms.BorderStyle.Fixed3D>).</span><span class="sxs-lookup"><span data-stu-id="68d36-116">The <xref:System.Windows.Forms.Panel.BorderStyle%2A> property determines if the panel is outlined with no visible border (<xref:System.Windows.Forms.BorderStyle.None>), a plain line (<xref:System.Windows.Forms.BorderStyle.FixedSingle>), or a shadowed line (<xref:System.Windows.Forms.BorderStyle.Fixed3D>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68d36-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68d36-117">See Also</span></span>  
 <xref:System.Windows.Forms.Panel>  
 [<span data-ttu-id="68d36-118">GroupBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="68d36-118">GroupBox Control</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)  
 [<span data-ttu-id="68d36-119">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Panel Denetimi ile Denetimleri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="68d36-119">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)  
 [<span data-ttu-id="68d36-120">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Panelinin Arka Planını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="68d36-120">How to: Set the Background of a Windows Forms Panel Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
