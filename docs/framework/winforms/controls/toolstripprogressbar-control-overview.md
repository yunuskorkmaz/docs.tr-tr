---
title: ToolStripProgressBar Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- ToolStripProgressBar
helpviewer_keywords:
- toolbars [Windows Forms], progress bars
- progress controls [Windows Forms]
- ToolStripProgressBar control [Windows Forms], about ToolStripProgressBar control
ms.assetid: ec3ab522-5fe4-4b4d-a551-bc19e84f4774
ms.openlocfilehash: 0ce2347be055cc1840341747f202125cbbf678c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537758"
---
# <a name="toolstripprogressbar-control-overview"></a><span data-ttu-id="4fa3c-102">ToolStripProgressBar Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4fa3c-102">ToolStripProgressBar Control Overview</span></span>
<span data-ttu-id="4fa3c-103"><xref:System.Windows.Forms.ToolStripProgressBar> Radye ve tüm işleme işlevlerini birleştiren <xref:System.Windows.Forms.ToolStrip> normal işlem izleme işlevselliğini denetimleriyle.</span><span class="sxs-lookup"><span data-stu-id="4fa3c-103">The <xref:System.Windows.Forms.ToolStripProgressBar> combines the rafting and rendering functionality of all <xref:System.Windows.Forms.ToolStrip> controls with its typical process-tracking functionality.</span></span> <span data-ttu-id="4fa3c-104">A <xref:System.Windows.Forms.ToolStripProgressBar> en genellikle tarafından barındırılan <xref:System.Windows.Forms.StatusStrip>, sık tarafından küçük bir <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="4fa3c-104">A <xref:System.Windows.Forms.ToolStripProgressBar> is most usually hosted by <xref:System.Windows.Forms.StatusStrip>, and less frequently by a <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="4fa3c-105">Ancak <xref:System.Windows.Forms.ToolStripProgressBar> değiştirir ve önceki sürümlerde, denetim için işlevsellik ekler <xref:System.Windows.Forms.ToolStripProgressBar> geriye dönük uyumluluk ve gelecekte kullanım için isterseniz korunur.</span><span class="sxs-lookup"><span data-stu-id="4fa3c-105">Although <xref:System.Windows.Forms.ToolStripProgressBar> replaces and adds functionality to the control in previous versions, <xref:System.Windows.Forms.ToolStripProgressBar> is retained for both backward compatibility and future use if desired.</span></span>  
  
### <a name="important-toolstripprogressbar-members"></a><span data-ttu-id="4fa3c-106">Önemli ToolStripProgressBar üyeleri</span><span class="sxs-lookup"><span data-stu-id="4fa3c-106">Important ToolStripProgressBar Members</span></span>  
  
|<span data-ttu-id="4fa3c-107">Ad</span><span class="sxs-lookup"><span data-stu-id="4fa3c-107">Name</span></span>|<span data-ttu-id="4fa3c-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4fa3c-108">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripProgressBar.MarqueeAnimationSpeed%2A>|<span data-ttu-id="4fa3c-109">Her arasındaki gecikme temsil eden bir değeri alır veya ayarlar <xref:System.Windows.Forms.ProgressBarStyle.Marquee> güncelleştirme, milisaniye cinsinden görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4fa3c-109">Gets or sets a value representing the delay between each <xref:System.Windows.Forms.ProgressBarStyle.Marquee> display update, in milliseconds.</span></span>|  
|<xref:System.Windows.Forms.ProgressBar.Maximum%2A>|<span data-ttu-id="4fa3c-110">Alır veya ayarlar bu için tanımlanan aralığın üst sınırının <xref:System.Windows.Forms.ToolStripProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="4fa3c-110">Gets or sets the upper bound of the range that is defined for this <xref:System.Windows.Forms.ToolStripProgressBar>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.Minimum%2A>|<span data-ttu-id="4fa3c-111">Alır veya ayarlar bu için tanımlanan aralığının alt sınırı <xref:System.Windows.Forms.ToolStripProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="4fa3c-111">Gets or sets the lower bound of the range that is defined for this <xref:System.Windows.Forms.ToolStripProgressBar>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.Style%2A>|<span data-ttu-id="4fa3c-112">Alır veya stilini ayarlar <xref:System.Windows.Forms.ToolStripProgressBar> bir işlemin ilerlemesini görüntülemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="4fa3c-112">Gets or sets the style that the <xref:System.Windows.Forms.ToolStripProgressBar> uses to display the progress of an operation.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.Value%2A>|<span data-ttu-id="4fa3c-113">Geçerli değeri alır veya ayarlar <xref:System.Windows.Forms.ToolStripProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="4fa3c-113">Gets or sets the current value of the <xref:System.Windows.Forms.ToolStripProgressBar>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.PerformStep%2A>|<span data-ttu-id="4fa3c-114">İlerleme çubuğu geçerli konumunu miktarı ilerler <xref:System.Windows.Forms.ToolStripProgressBar.Step%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4fa3c-114">Advances the current position of the progress bar by the amount of the <xref:System.Windows.Forms.ToolStripProgressBar.Step%2A> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4fa3c-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4fa3c-115">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripProgressBar>
