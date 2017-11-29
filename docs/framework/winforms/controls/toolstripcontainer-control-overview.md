---
title: "ToolStripContainer Denetimine Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolStripContainer
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], about ToolStripContainer control
ms.assetid: c7d63bff-64e2-4a63-bd89-d31bc96dacb8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4abc783961177a55cdb81cefd21ed2d7aefb0620
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="toolstripcontainer-control-overview"></a><span data-ttu-id="d349c-102">ToolStripContainer Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d349c-102">ToolStripContainer Control Overview</span></span>
<span data-ttu-id="d349c-103">A <xref:System.Windows.Forms.ToolStripContainer> sol, sağ, üst ve alt kenarı konumlandırma ve radye panoları sahip <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, ve <xref:System.Windows.Forms.StatusStrip> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="d349c-103">A <xref:System.Windows.Forms.ToolStripContainer> has panels on its left, right, top, and bottom sides for positioning and rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="d349c-104">Birden çok <xref:System.Windows.Forms.ToolStrip> denetimleri yığın dikey bunları sola veya sağa moduna geçirirseniz <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="d349c-104">Multiple <xref:System.Windows.Forms.ToolStrip> controls stack vertically if you put them in the left or right <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="d349c-105">Bunları üstüne veya altına yerleştirin varsa bunlar yatay yığın <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="d349c-105">They stack horizontally if you put them in the top or bottom <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="d349c-106">Orta kullanabilirsiniz <xref:System.Windows.Forms.ToolStripContentPanel> , <xref:System.Windows.Forms.ToolStripContainer> geleneksel denetimleri form üzerinde konumlandırmak için.</span><span class="sxs-lookup"><span data-stu-id="d349c-106">You can use the central <xref:System.Windows.Forms.ToolStripContentPanel> of the <xref:System.Windows.Forms.ToolStripContainer> to position traditional controls on the form.</span></span>  
  
 <span data-ttu-id="d349c-107">Tüm <xref:System.Windows.Forms.ToolStripContainer> denetimleri tasarım zamanında doğrudan seçilebilir ve silinebilir.</span><span class="sxs-lookup"><span data-stu-id="d349c-107">Any or all <xref:System.Windows.Forms.ToolStripContainer> controls are directly selectable at design time and can be deleted.</span></span> <span data-ttu-id="d349c-108">Her panelini bir <xref:System.Windows.Forms.ToolStripContainer> genişletilebilir ve daraltılabilir ve içerdiği denetimleriyle göre yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="d349c-108">Each panel of a <xref:System.Windows.Forms.ToolStripContainer> is expandable and collapsible, and resizes with the controls that it contains.</span></span>  
  
### <a name="important-toolstripcontainer-members"></a><span data-ttu-id="d349c-109">Önemli ToolStripContainer üyeleri</span><span class="sxs-lookup"><span data-stu-id="d349c-109">Important ToolStripContainer Members</span></span>  
  
|<span data-ttu-id="d349c-110">Ad</span><span class="sxs-lookup"><span data-stu-id="d349c-110">Name</span></span>|<span data-ttu-id="d349c-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d349c-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanel%2A>|<span data-ttu-id="d349c-112">Alt panelini alır <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="d349c-112">Gets the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanelVisible%2A>|<span data-ttu-id="d349c-113">Belirten değeri alır veya ayarlar olup olmadığını alt panelini <xref:System.Windows.Forms.ToolStripContainer> görünür.</span><span class="sxs-lookup"><span data-stu-id="d349c-113">Gets or sets a value indicating whether the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanel%2A>|<span data-ttu-id="d349c-114">Sol bölmesi, alır <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="d349c-114">Gets the left panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanelVisible%2A>|<span data-ttu-id="d349c-115">Belirten değeri alır veya ayarlar olup olmadığını, Sol paneldeki <xref:System.Windows.Forms.ToolStripContainer> görünür.</span><span class="sxs-lookup"><span data-stu-id="d349c-115">Gets or sets a value indicating whether the left panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanel%2A>|<span data-ttu-id="d349c-116">Sağ bölmesinde alır <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="d349c-116">Gets the right panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanelVisible%2A>|<span data-ttu-id="d349c-117">Belirten değeri alır veya ayarlar olup olmadığını sağ bölmesinde <xref:System.Windows.Forms.ToolStripContainer> görünür.</span><span class="sxs-lookup"><span data-stu-id="d349c-117">Gets or sets a value indicating whether the right panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A>|<span data-ttu-id="d349c-118">Üst panelinin alır <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="d349c-118">Gets the top panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanelVisible%2A>|<span data-ttu-id="d349c-119">Belirten değeri alır veya ayarlar olup olmadığını üst panelinin <xref:System.Windows.Forms.ToolStripContainer> görünür.</span><span class="sxs-lookup"><span data-stu-id="d349c-119">Gets or sets a value indicating whether the top panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d349c-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d349c-120">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 <xref:System.Windows.Forms.ToolStripContentPanel>
