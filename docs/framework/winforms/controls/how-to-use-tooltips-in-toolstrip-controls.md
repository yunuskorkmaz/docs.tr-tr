---
title: 'Nasıl yapılır: ToolStrip Denetiminde ToolTips Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: ffaf859fafc87131de525f7bf2f52db421a208c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785755"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a><span data-ttu-id="86ca8-102">Nasıl yapılır: ToolStrip Denetiminde ToolTips Kullanma</span><span class="sxs-lookup"><span data-stu-id="86ca8-102">How to: Use ToolTips in ToolStrip Controls</span></span>
<span data-ttu-id="86ca8-103">Görüntüleyebileceğiniz bir <xref:System.Windows.Forms.ToolTip> için <xref:System.Windows.Forms.ToolStrip> denetimin ayarlayarak denetimi <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="86ca8-103">You can display a <xref:System.Windows.Forms.ToolTip> for the <xref:System.Windows.Forms.ToolStrip> control you want by setting the control's <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property to `true`.</span></span>  
  
### <a name="to-display-a-tooltip"></a><span data-ttu-id="86ca8-104">Bir araç ipucunu görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="86ca8-104">To display a ToolTip</span></span>  
  
- <span data-ttu-id="86ca8-105">Ayarlama <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> denetimin özellik `true`.</span><span class="sxs-lookup"><span data-stu-id="86ca8-105">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the control to `true`.</span></span>  
  
     <span data-ttu-id="86ca8-106">Varsayılan değer olan <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> olduğu `true`, varsayılan değeri <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> ve <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> olduğu `false`.</span><span class="sxs-lookup"><span data-stu-id="86ca8-106">The default value of <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `true`, and the default value of <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `false`.</span></span>  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a><span data-ttu-id="86ca8-107">Tooltıptext özelliği bir ToolStripButton için araç ipucu metni kullanmak için</span><span class="sxs-lookup"><span data-stu-id="86ca8-107">To use the ToolTipText property for the ToolTip text of a ToolStripButton</span></span>  
  
1. <span data-ttu-id="86ca8-108">Ayarlama <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> özelliği düğmenin `true`.</span><span class="sxs-lookup"><span data-stu-id="86ca8-108">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the button to `true`.</span></span>  
  
2. <span data-ttu-id="86ca8-109">Ayarlama <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> özelliği düğmenin `false`.</span><span class="sxs-lookup"><span data-stu-id="86ca8-109">Set the <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> property of the button to `false`.</span></span>  
  
     <span data-ttu-id="86ca8-110">`AutoToolTip` Özelliği `true` için varsayılan olarak <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, ve <xref:System.Windows.Forms.ToolStripSplitButton>.</span><span class="sxs-lookup"><span data-stu-id="86ca8-110">The `AutoToolTip` property is `true` by default for <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, and <xref:System.Windows.Forms.ToolStripSplitButton>.</span></span>  
  
     <span data-ttu-id="86ca8-111">A <xref:System.Windows.Forms.ToolStripButton> kullanır, `Text` özelliği <xref:System.Windows.Forms.ToolTip> varsayılan metin.</span><span class="sxs-lookup"><span data-stu-id="86ca8-111">A <xref:System.Windows.Forms.ToolStripButton> uses its `Text` property for the <xref:System.Windows.Forms.ToolTip> text by default.</span></span> <span data-ttu-id="86ca8-112">Özel metin görüntülemek için bu yordamı kullanın. bir <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="86ca8-112">Use this procedure to display custom text in a <xref:System.Windows.Forms.ToolStripButton><xref:System.Windows.Forms.ToolTip>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86ca8-113">Ayarlarsanız <xref:System.Windows.Forms.ToolStripItemDisplayStyle> için <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> veya <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>metin düğmesinde görüntülenir, ancak araç ipucu görünmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="86ca8-113">If you set <xref:System.Windows.Forms.ToolStripItemDisplayStyle> to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, no text will appear on the button, but the tool tip still appears.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86ca8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86ca8-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [<span data-ttu-id="86ca8-115">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="86ca8-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
