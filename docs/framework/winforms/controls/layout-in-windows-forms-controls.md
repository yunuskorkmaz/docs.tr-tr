---
title: "Windows Forms Denetimlerindeki Düzenler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- layout [Windows Forms]
- sizing [Windows Forms], automatic [Windows Forms]
- Margin property [Windows Forms]
- Padding property [Windws Forms]
ms.assetid: 99400e3a-720e-4f56-b68f-89df911a251c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6244b21c2729df3bfe5899a4f4970f4b48030057
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="layout-in-windows-forms-controls"></a><span data-ttu-id="feb2c-102">Windows Forms Denetimlerindeki Düzenler</span><span class="sxs-lookup"><span data-stu-id="feb2c-102">Layout in Windows Forms Controls</span></span>
<span data-ttu-id="feb2c-103">Formunuza denetimler tam yerleşimi, pek çok uygulama yüksek önceliktir.</span><span class="sxs-lookup"><span data-stu-id="feb2c-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="feb2c-104"><xref:System.Windows.Forms?displayProperty=nameWithType> Ad alanı, bunu başarmak için birçok düzeni Araçlar verir.</span><span class="sxs-lookup"><span data-stu-id="feb2c-104">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace gives you many layout tools to accomplish this.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="feb2c-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="feb2c-105">In This Section</span></span>  
 [<span data-ttu-id="feb2c-106">AutoSize özelliğine genel bakış</span><span class="sxs-lookup"><span data-stu-id="feb2c-106">AutoSize Property Overview</span></span>](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 <span data-ttu-id="feb2c-107">Açıklar <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği ve düzeninde rolü.</span><span class="sxs-lookup"><span data-stu-id="feb2c-107">Describes the <xref:System.Windows.Forms.Control.AutoSize%2A> property and its role in layout.</span></span>  
  
 [<span data-ttu-id="feb2c-108">Kenar boşlukları ve Windows Forms denetimleri doldurma</span><span class="sxs-lookup"><span data-stu-id="feb2c-108">Margin and Padding in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/margin-and-padding-in-windows-forms-controls.md)  
 <span data-ttu-id="feb2c-109">Açıklar <xref:System.Windows.Forms.Control.Margin%2A> ve <xref:System.Windows.Forms.Control.Padding%2A> özellikleri ve rolleri düzeni.</span><span class="sxs-lookup"><span data-stu-id="feb2c-109">Describes the <xref:System.Windows.Forms.Control.Margin%2A> and <xref:System.Windows.Forms.Control.Padding%2A> properties and their roles in layout.</span></span>  
  
 [<span data-ttu-id="feb2c-110">Nasıl yapılır: denetimi formların kenarlarına hizalama</span><span class="sxs-lookup"><span data-stu-id="feb2c-110">How to: Align a Control to the Edges of Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md)  
 <span data-ttu-id="feb2c-111">Nasıl kullanılacağı ortaya <xref:System.Windows.Forms.Control.Dock%2A> özelliği denetiminizi nesnenin kapladığı form köşesine hizalar.</span><span class="sxs-lookup"><span data-stu-id="feb2c-111">Demonstrates how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>  
  
 [<span data-ttu-id="feb2c-112">Nasıl yapılır: Windows Forms çevresinde kenarlık oluşturma doldurmayı kullanarak denetleme</span><span class="sxs-lookup"><span data-stu-id="feb2c-112">How to: Create a Border Around a Windows Forms Control Using Padding</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-border-around-a-windows-forms-control-using-padding.md)  
 <span data-ttu-id="feb2c-113">Nasıl kullanılacağı ortaya <xref:System.Windows.Forms.Control.Padding%2A> denetim ana hatlarını belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="feb2c-113">Demonstrates how to use the <xref:System.Windows.Forms.Control.Padding%2A> property to outline a control.</span></span>  
  
 [<span data-ttu-id="feb2c-114">Nasıl yapılır: özel yerleşim altyapısı uygulama</span><span class="sxs-lookup"><span data-stu-id="feb2c-114">How to: Implement a Custom Layout Engine</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-custom-layout-engine.md)  
 <span data-ttu-id="feb2c-115">Nasıl uygulandığını gösteren bir <xref:System.Windows.Forms.Layout.LayoutEngine> Windows Forms denetimlerini düzenleme için.</span><span class="sxs-lookup"><span data-stu-id="feb2c-115">Demonstrates how to implement a <xref:System.Windows.Forms.Layout.LayoutEngine> for arranging Windows Forms controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="feb2c-116">Başvuru</span><span class="sxs-lookup"><span data-stu-id="feb2c-116">Reference</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <span data-ttu-id="feb2c-117">Başvuru belgelerine sağlar <xref:System.Windows.Forms.TableLayoutPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="feb2c-117">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <span data-ttu-id="feb2c-118">Başvuru belgelerine sağlar <xref:System.Windows.Forms.FlowLayoutPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="feb2c-118">Provides reference documentation for the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feb2c-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="feb2c-119">See Also</span></span>  
 [<span data-ttu-id="feb2c-120">Nasıl yapılır: FlowLayoutPanel denetiminde alt denetimleri sabitleme ve yerleştirme</span><span class="sxs-lookup"><span data-stu-id="feb2c-120">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [<span data-ttu-id="feb2c-121">Nasıl yapılır: TableLayoutPanel denetiminde alt denetimleri sabitleme ve yerleştirme</span><span class="sxs-lookup"><span data-stu-id="feb2c-121">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="feb2c-122">Nasıl yapılır: Windows Formları yerelleştirmeye iyi cevap veren düzeni tasarım</span><span class="sxs-lookup"><span data-stu-id="feb2c-122">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [<span data-ttu-id="feb2c-123">TableLayoutPanel denetiminde AutoSize davranışı</span><span class="sxs-lookup"><span data-stu-id="feb2c-123">AutoSize Behavior in the TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/autosize-behavior-in-the-tablelayoutpanel-control.md)
