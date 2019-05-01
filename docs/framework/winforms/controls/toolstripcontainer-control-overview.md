---
title: ToolStripContainer Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- ToolStripContainer
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], about ToolStripContainer control
ms.assetid: c7d63bff-64e2-4a63-bd89-d31bc96dacb8
ms.openlocfilehash: c279316c2a372a1498707b27ec8658813306304b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009480"
---
# <a name="toolstripcontainer-control-overview"></a><span data-ttu-id="35010-102">ToolStripContainer Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="35010-102">ToolStripContainer Control Overview</span></span>
<span data-ttu-id="35010-103">A <xref:System.Windows.Forms.ToolStripContainer> sol, sağ, üst ve alt kenarı konumlandırma ve radye panelleri sahip <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, ve <xref:System.Windows.Forms.StatusStrip> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="35010-103">A <xref:System.Windows.Forms.ToolStripContainer> has panels on its left, right, top, and bottom sides for positioning and rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="35010-104">Birden çok <xref:System.Windows.Forms.ToolStrip> denetimleri yığın dikey olarak bunları sola veya sağa yerleştirdiğinizde <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="35010-104">Multiple <xref:System.Windows.Forms.ToolStrip> controls stack vertically if you put them in the left or right <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="35010-105">Bunları üstüne veya altına yerleştirebilirsiniz varsa bunlar yatay olarak yerleşir <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="35010-105">They stack horizontally if you put them in the top or bottom <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="35010-106">Orta kullanabileceğiniz <xref:System.Windows.Forms.ToolStripContentPanel> , <xref:System.Windows.Forms.ToolStripContainer> geleneksel denetimleri form üzerinde yerleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="35010-106">You can use the central <xref:System.Windows.Forms.ToolStripContentPanel> of the <xref:System.Windows.Forms.ToolStripContainer> to position traditional controls on the form.</span></span>  
  
 <span data-ttu-id="35010-107">Tüm <xref:System.Windows.Forms.ToolStripContainer> denetimleri tasarım zamanında doğrudan seçilebilir ve silinebilir.</span><span class="sxs-lookup"><span data-stu-id="35010-107">Any or all <xref:System.Windows.Forms.ToolStripContainer> controls are directly selectable at design time and can be deleted.</span></span> <span data-ttu-id="35010-108">Her panelinin bir <xref:System.Windows.Forms.ToolStripContainer> genişletilebilen ve daraltılabilen ve içerdiği denetimlerle yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="35010-108">Each panel of a <xref:System.Windows.Forms.ToolStripContainer> is expandable and collapsible, and resizes with the controls that it contains.</span></span>  
  
### <a name="important-toolstripcontainer-members"></a><span data-ttu-id="35010-109">Önemli ToolStripContainer üyeleri</span><span class="sxs-lookup"><span data-stu-id="35010-109">Important ToolStripContainer Members</span></span>  
  
|<span data-ttu-id="35010-110">Ad</span><span class="sxs-lookup"><span data-stu-id="35010-110">Name</span></span>|<span data-ttu-id="35010-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35010-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanel%2A>|<span data-ttu-id="35010-112">Alt paneli, alır <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="35010-112">Gets the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanelVisible%2A>|<span data-ttu-id="35010-113">Belirten bir değeri alır veya ayarlar olup olmadığını alt panelini <xref:System.Windows.Forms.ToolStripContainer> görülebilir.</span><span class="sxs-lookup"><span data-stu-id="35010-113">Gets or sets a value indicating whether the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanel%2A>|<span data-ttu-id="35010-114">Sol bölmesinde alır <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="35010-114">Gets the left panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanelVisible%2A>|<span data-ttu-id="35010-115">Belirten bir değeri alır veya ayarlar olmadığını sol bölmesinde <xref:System.Windows.Forms.ToolStripContainer> görülebilir.</span><span class="sxs-lookup"><span data-stu-id="35010-115">Gets or sets a value indicating whether the left panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanel%2A>|<span data-ttu-id="35010-116">Sağ bölmesinde alır <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="35010-116">Gets the right panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanelVisible%2A>|<span data-ttu-id="35010-117">Belirten bir değeri alır veya ayarlar olup olmadığını doğru panelini <xref:System.Windows.Forms.ToolStripContainer> görülebilir.</span><span class="sxs-lookup"><span data-stu-id="35010-117">Gets or sets a value indicating whether the right panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A>|<span data-ttu-id="35010-118">Üst panelde, alır <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="35010-118">Gets the top panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanelVisible%2A>|<span data-ttu-id="35010-119">Belirten bir değeri alır veya ayarlar olup olmadığını, üst panelde <xref:System.Windows.Forms.ToolStripContainer> görülebilir.</span><span class="sxs-lookup"><span data-stu-id="35010-119">Gets or sets a value indicating whether the top panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="35010-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35010-120">See also</span></span>

- <xref:System.Windows.Forms.ToolStripContainer>
- <xref:System.Windows.Forms.ToolStripContentPanel>
