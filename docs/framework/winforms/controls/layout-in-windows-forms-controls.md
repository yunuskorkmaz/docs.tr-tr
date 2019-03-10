---
title: Windows Forms Denetimlerindeki Düzenler
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms]
- sizing [Windows Forms], automatic [Windows Forms]
- Margin property [Windows Forms]
- Padding property [Windows Forms]
ms.assetid: 99400e3a-720e-4f56-b68f-89df911a251c
ms.openlocfilehash: d1a3954c8eda87bdda9fa17df1bd2b3858c43619
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711336"
---
# <a name="layout-in-windows-forms-controls"></a><span data-ttu-id="3d67a-102">Windows Forms Denetimlerindeki Düzenler</span><span class="sxs-lookup"><span data-stu-id="3d67a-102">Layout in Windows Forms Controls</span></span>

<span data-ttu-id="3d67a-103">Formunuzdaki denetimleri kesin yerleşimini birçok uygulama için yüksek öncelik taşır.</span><span class="sxs-lookup"><span data-stu-id="3d67a-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="3d67a-104"><xref:System.Windows.Forms?displayProperty=nameWithType> Ad alanı, bunu gerçekleştirmek için çok sayıda düzen araçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="3d67a-104">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace gives you many layout tools to accomplish this.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="3d67a-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3d67a-105">In This Section</span></span>

<span data-ttu-id="3d67a-106">[AutoSize özelliğine genel bakış](autosize-property-overview.md)\\</span><span class="sxs-lookup"><span data-stu-id="3d67a-106">[AutoSize Property Overview](autosize-property-overview.md)\\</span></span>
<span data-ttu-id="3d67a-107">Açıklar <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği ve düzeninde rolü.</span><span class="sxs-lookup"><span data-stu-id="3d67a-107">Describes the <xref:System.Windows.Forms.Control.AutoSize%2A> property and its role in layout.</span></span>

<span data-ttu-id="3d67a-108">[Kenar boşluğu bırakma ve Windows formlarında denetimleri doldurma](margin-and-padding-in-windows-forms-controls.md)\\</span><span class="sxs-lookup"><span data-stu-id="3d67a-108">[Margin and Padding in Windows Forms Controls](margin-and-padding-in-windows-forms-controls.md)\\</span></span>
<span data-ttu-id="3d67a-109">Açıklar <xref:System.Windows.Forms.Control.Margin%2A> ve <xref:System.Windows.Forms.Control.Padding%2A> özellikleri ve rolleri düzeni.</span><span class="sxs-lookup"><span data-stu-id="3d67a-109">Describes the <xref:System.Windows.Forms.Control.Margin%2A> and <xref:System.Windows.Forms.Control.Padding%2A> properties and their roles in layout.</span></span>

<span data-ttu-id="3d67a-110">[Nasıl yapılır: Bir denetimi formların kenarlarına hizalama](how-to-align-a-control-to-the-edges-of-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="3d67a-110">[How to: Align a Control to the Edges of Forms](how-to-align-a-control-to-the-edges-of-forms.md)\\</span></span>
<span data-ttu-id="3d67a-111">Nasıl kullanılacağını gösteren <xref:System.Windows.Forms.Control.Dock%2A> denetiminiz kapladığı form köşesine hizalamak için özellik.</span><span class="sxs-lookup"><span data-stu-id="3d67a-111">Demonstrates how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>

<span data-ttu-id="3d67a-112">[Nasıl yapılır: Bir Windows Forms çevresinde kenarlık oluşturma doldurma kullanarak denetleme](how-to-create-a-border-around-a-windows-forms-control-using-padding.md)\\</span><span class="sxs-lookup"><span data-stu-id="3d67a-112">[How to: Create a Border Around a Windows Forms Control Using Padding](how-to-create-a-border-around-a-windows-forms-control-using-padding.md)\\</span></span>
<span data-ttu-id="3d67a-113">Nasıl kullanılacağını gösteren <xref:System.Windows.Forms.Control.Padding%2A> denetim anahat özelliği.</span><span class="sxs-lookup"><span data-stu-id="3d67a-113">Demonstrates how to use the <xref:System.Windows.Forms.Control.Padding%2A> property to outline a control.</span></span>

<span data-ttu-id="3d67a-114">[Nasıl yapılır: Özel yerleşim altyapısı uygulama](how-to-implement-a-custom-layout-engine.md)\\</span><span class="sxs-lookup"><span data-stu-id="3d67a-114">[How to: Implement a Custom Layout Engine](how-to-implement-a-custom-layout-engine.md)\\</span></span>
<span data-ttu-id="3d67a-115">Nasıl uygulanacağını gösterir bir <xref:System.Windows.Forms.Layout.LayoutEngine> Windows Forms denetimlerini düzenleme için.</span><span class="sxs-lookup"><span data-stu-id="3d67a-115">Demonstrates how to implement a <xref:System.Windows.Forms.Layout.LayoutEngine> for arranging Windows Forms controls.</span></span>

## <a name="reference"></a><span data-ttu-id="3d67a-116">Başvuru</span><span class="sxs-lookup"><span data-stu-id="3d67a-116">Reference</span></span>

<xref:System.Windows.Forms.TableLayoutPanel>\
<span data-ttu-id="3d67a-117">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="3d67a-117">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

<xref:System.Windows.Forms.FlowLayoutPanel>\
<span data-ttu-id="3d67a-118">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.FlowLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="3d67a-118">Provides reference documentation for the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d67a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d67a-119">See also</span></span>

- [<span data-ttu-id="3d67a-120">Nasıl yapılır: Sabitleme ve FlowLayoutPanel denetiminde alt denetimleri yerleştirme</span><span class="sxs-lookup"><span data-stu-id="3d67a-120">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="3d67a-121">Nasıl yapılır: Sabitleme ve TableLayoutPanel denetiminde alt denetimleri yerleştirme</span><span class="sxs-lookup"><span data-stu-id="3d67a-121">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="3d67a-122">Nasıl yapılır: Yerelleştirmeye iyi cevap veren bir Windows Forms düzeni tasarlama</span><span class="sxs-lookup"><span data-stu-id="3d67a-122">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [<span data-ttu-id="3d67a-123">TableLayoutPanel Denetiminde AutoSize Davranışı</span><span class="sxs-lookup"><span data-stu-id="3d67a-123">AutoSize Behavior in the TableLayoutPanel Control</span></span>](autosize-behavior-in-the-tablelayoutpanel-control.md)
