---
title: 'Nasıl yapılır: ToolStrip Denetiminde ToolTips Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: 3f383b6cccba7825637ea65a0e13280b91b406c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939728"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a><span data-ttu-id="f7c8b-102">Nasıl yapılır: ToolStrip Denetiminde ToolTips Kullanma</span><span class="sxs-lookup"><span data-stu-id="f7c8b-102">How to: Use ToolTips in ToolStrip Controls</span></span>
<span data-ttu-id="f7c8b-103"><xref:System.Windows.Forms.ToolTip> <xref:System.Windows.Forms.ToolStrip> Denetimin özelliğiniolarak`true`ayarlayarak istediğiniz denetim için bir görüntüleyebilirsiniz. <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A></span><span class="sxs-lookup"><span data-stu-id="f7c8b-103">You can display a <xref:System.Windows.Forms.ToolTip> for the <xref:System.Windows.Forms.ToolStrip> control you want by setting the control's <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property to `true`.</span></span>  
  
### <a name="to-display-a-tooltip"></a><span data-ttu-id="f7c8b-104">Araç Ipucunu görüntüleme</span><span class="sxs-lookup"><span data-stu-id="f7c8b-104">To display a ToolTip</span></span>  
  
- <span data-ttu-id="f7c8b-105">Denetiminin özelliğini olarak `true`ayarlayın. <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A></span><span class="sxs-lookup"><span data-stu-id="f7c8b-105">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the control to `true`.</span></span>  
  
     <span data-ttu-id="f7c8b-106">Varsayılan değeri <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> `true`, <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> ve varsayılan<xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType>değeridir . `false`</span><span class="sxs-lookup"><span data-stu-id="f7c8b-106">The default value of <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `true`, and the default value of <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `false`.</span></span>  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a><span data-ttu-id="f7c8b-107">ToolStripButton araç Ipucu metni için ToolTipText özelliğini kullanmak için</span><span class="sxs-lookup"><span data-stu-id="f7c8b-107">To use the ToolTipText property for the ToolTip text of a ToolStripButton</span></span>  
  
1. <span data-ttu-id="f7c8b-108">Düğmenin özelliğini olarak `true`ayarlayın. <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A></span><span class="sxs-lookup"><span data-stu-id="f7c8b-108">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the button to `true`.</span></span>  
  
2. <span data-ttu-id="f7c8b-109">Düğmenin özelliğini olarak `false`ayarlayın. <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f7c8b-109">Set the <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> property of the button to `false`.</span></span>  
  
     <span data-ttu-id="f7c8b-110"><xref:System.Windows.Forms.ToolStripButton> `true` Özelliği,,ve<xref:System.Windows.Forms.ToolStripSplitButton>için Varsayılanolarakolur.<xref:System.Windows.Forms.ToolStripDropDownButton> `AutoToolTip`</span><span class="sxs-lookup"><span data-stu-id="f7c8b-110">The `AutoToolTip` property is `true` by default for <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, and <xref:System.Windows.Forms.ToolStripSplitButton>.</span></span>  
  
     <span data-ttu-id="f7c8b-111">, Varsayılan olarak `Text` <xref:System.Windows.Forms.ToolTip> metin için özelliğini kullanır.<xref:System.Windows.Forms.ToolStripButton></span><span class="sxs-lookup"><span data-stu-id="f7c8b-111">A <xref:System.Windows.Forms.ToolStripButton> uses its `Text` property for the <xref:System.Windows.Forms.ToolTip> text by default.</span></span> <span data-ttu-id="f7c8b-112"><xref:System.Windows.Forms.ToolStripButton> İçinde<xref:System.Windows.Forms.ToolTip>özel metin göstermek için bu yordamı kullanın.</span><span class="sxs-lookup"><span data-stu-id="f7c8b-112">Use this procedure to display custom text in a <xref:System.Windows.Forms.ToolStripButton><xref:System.Windows.Forms.ToolTip>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7c8b-113">Veya <xref:System.Windows.Forms.ToolStripItemDisplayStyle> <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> olarak ayarlarsanız,düğmeüzerindehiçbirmetingörünmez,ancakaraçipucugörünmeyedevameder.<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image></span><span class="sxs-lookup"><span data-stu-id="f7c8b-113">If you set <xref:System.Windows.Forms.ToolStripItemDisplayStyle> to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, no text will appear on the button, but the tool tip still appears.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7c8b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7c8b-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [<span data-ttu-id="f7c8b-115">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f7c8b-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
