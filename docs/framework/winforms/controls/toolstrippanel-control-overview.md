---
title: ToolStripPanel Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- ToolStripPanel
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms], about ToolStripPanel control
ms.assetid: ce54a60c-5eba-4b4c-bd77-cf0748a666cc
ms.openlocfilehash: 104ccfd0370eff48312372a2391031575b53b3bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660235"
---
# <a name="toolstrippanel-control-overview"></a><span data-ttu-id="d50a9-102">ToolStripPanel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d50a9-102">ToolStripPanel Control Overview</span></span>
<span data-ttu-id="d50a9-103">A <xref:System.Windows.Forms.ToolStripPanel> konumlandırma ve radye için tek bir alan sağlar <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, ve <xref:System.Windows.Forms.StatusStrip> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="d50a9-103">A <xref:System.Windows.Forms.ToolStripPanel> provides a single area for positioning and rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="d50a9-104">Birden çok <xref:System.Windows.Forms.ToolStrip> bağlı denetimleri yığın yatay veya dikey olarak <xref:System.Windows.Forms.ToolStripPanelRow.Orientation%2A> , <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="d50a9-104">Multiple <xref:System.Windows.Forms.ToolStrip> controls stack vertically or horizontally depending on the <xref:System.Windows.Forms.ToolStripPanelRow.Orientation%2A> of the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>  
  
### <a name="important-toolstrippanel-members"></a><span data-ttu-id="d50a9-105">Önemli ToolStripPanel üyeleri</span><span class="sxs-lookup"><span data-stu-id="d50a9-105">Important ToolStripPanel Members</span></span>  
  
|<span data-ttu-id="d50a9-106">Ad</span><span class="sxs-lookup"><span data-stu-id="d50a9-106">Name</span></span>|<span data-ttu-id="d50a9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d50a9-107">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripPanel.Orientation%2A>|<span data-ttu-id="d50a9-108">Yatay veya dikey yönünü belirten bir değeri alır veya ayarlar <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="d50a9-108">Gets or sets a value indicating the horizontal or vertical orientation of the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.Renderer%2A>|<span data-ttu-id="d50a9-109">Alır veya ayarlar bir <xref:System.Windows.Forms.ToolStripRenderer> görünümünü özelleştirmek için kullanılan bir <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="d50a9-109">Gets or sets a <xref:System.Windows.Forms.ToolStripRenderer> used to customize the appearance of a <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.RenderMode%2A>|<span data-ttu-id="d50a9-110">Alır veya ayarlar uygulanmaya boyama stilleri <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="d50a9-110">Gets or sets the painting styles to be applied to the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.RowMargin%2A>|<span data-ttu-id="d50a9-111">Alır veya aralığı arasındaki piksel cinsinden ayarlar <xref:System.Windows.Forms.ToolStripPanelRow> ve <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="d50a9-111">Gets or sets the spacing, in pixels, between the <xref:System.Windows.Forms.ToolStripPanelRow> and the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.Rows%2A>|<span data-ttu-id="d50a9-112">Alır <xref:System.Windows.Forms.ToolStripPanelRow> bu <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="d50a9-112">Gets the <xref:System.Windows.Forms.ToolStripPanelRow> in this <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.Join%2A>|<span data-ttu-id="d50a9-113">Ekler bir <xref:System.Windows.Forms.ToolStrip> için bir <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="d50a9-113">Adds a <xref:System.Windows.Forms.ToolStrip> to a <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d50a9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d50a9-114">See also</span></span>
- <xref:System.Windows.Forms.ToolStripContainer>
- <xref:System.Windows.Forms.ToolStripContentPanel>
- [<span data-ttu-id="d50a9-115">ToolStrip örnek</span><span class="sxs-lookup"><span data-stu-id="d50a9-115">ToolStrip Sample</span></span>](https://msdn.microsoft.com/library/b7352439-184a-4a3a-b2ad-07465d3af9ed)
