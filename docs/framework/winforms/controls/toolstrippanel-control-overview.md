---
title: "ToolStripPanel Denetimine Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolStripPanel
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms], about ToolStripPanel control
ms.assetid: ce54a60c-5eba-4b4c-bd77-cf0748a666cc
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bed2f4cbdc2f7d2e2647e39163959aaf42ae8bab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="toolstrippanel-control-overview"></a><span data-ttu-id="55e44-102">ToolStripPanel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="55e44-102">ToolStripPanel Control Overview</span></span>
<span data-ttu-id="55e44-103">A <xref:System.Windows.Forms.ToolStripPanel> konumlandırma ve radye için tek bir alan sağlar <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, ve <xref:System.Windows.Forms.StatusStrip> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="55e44-103">A <xref:System.Windows.Forms.ToolStripPanel> provides a single area for positioning and rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="55e44-104">Birden çok <xref:System.Windows.Forms.ToolStrip> bağlı olarak denetimleri yığın dikey veya yatay olarak <xref:System.Windows.Forms.ToolStripPanelRow.Orientation%2A> , <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="55e44-104">Multiple <xref:System.Windows.Forms.ToolStrip> controls stack vertically or horizontally depending on the <xref:System.Windows.Forms.ToolStripPanelRow.Orientation%2A> of the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>  
  
### <a name="important-toolstrippanel-members"></a><span data-ttu-id="55e44-105">Önemli ToolStripPanel üyeleri</span><span class="sxs-lookup"><span data-stu-id="55e44-105">Important ToolStripPanel Members</span></span>  
  
|<span data-ttu-id="55e44-106">Ad</span><span class="sxs-lookup"><span data-stu-id="55e44-106">Name</span></span>|<span data-ttu-id="55e44-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55e44-107">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripPanel.Orientation%2A>|<span data-ttu-id="55e44-108">Yatay veya dikey yönünü belirten bir değeri alır veya ayarlar <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="55e44-108">Gets or sets a value indicating the horizontal or vertical orientation of the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.Renderer%2A>|<span data-ttu-id="55e44-109">Alır veya ayarlar bir <xref:System.Windows.Forms.ToolStripRenderer> görünümünü özelleştirmek için kullanılan bir <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="55e44-109">Gets or sets a <xref:System.Windows.Forms.ToolStripRenderer> used to customize the appearance of a <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.RenderMode%2A>|<span data-ttu-id="55e44-110">Alır veya ayarlar uygulanacak boyama stilleri <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="55e44-110">Gets or sets the painting styles to be applied to the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.RowMargin%2A>|<span data-ttu-id="55e44-111">Alır veya piksel cinsinden arasındaki boşluğu ayarlar <xref:System.Windows.Forms.ToolStripPanelRow> ve <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="55e44-111">Gets or sets the spacing, in pixels, between the <xref:System.Windows.Forms.ToolStripPanelRow> and the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.Rows%2A>|<span data-ttu-id="55e44-112">Alır <xref:System.Windows.Forms.ToolStripPanelRow> bu <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="55e44-112">Gets the <xref:System.Windows.Forms.ToolStripPanelRow> in this <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.Join%2A>|<span data-ttu-id="55e44-113">Ekler bir <xref:System.Windows.Forms.ToolStrip> için bir <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="55e44-113">Adds a <xref:System.Windows.Forms.ToolStrip> to a <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55e44-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55e44-114">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 <xref:System.Windows.Forms.ToolStripContentPanel>  
 [<span data-ttu-id="55e44-115">ToolStrip örnek</span><span class="sxs-lookup"><span data-stu-id="55e44-115">ToolStrip Sample</span></span>](http://msdn.microsoft.com/en-us/b7352439-184a-4a3a-b2ad-07465d3af9ed)
