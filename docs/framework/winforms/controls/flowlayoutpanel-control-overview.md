---
title: FlowLayoutPanel Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- FlowLayoutPanel
helpviewer_keywords:
- forms [Windows Forms], dynamic layout
- layout [Windows Forms], dynamic
- Windows Forms, dynamic layout
- FlowLayoutPanel control [Windows Forms], about FlowLayoutPanel control
ms.assetid: 3883e024-f5a0-456d-9c27-b4dfa1cc9045
ms.openlocfilehash: 58d95c2238687b4822155916177172a34c3abb87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526731"
---
# <a name="flowlayoutpanel-control-overview"></a><span data-ttu-id="480d0-102">FlowLayoutPanel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="480d0-102">FlowLayoutPanel Control Overview</span></span>
<span data-ttu-id="480d0-103"><xref:System.Windows.Forms.FlowLayoutPanel> Denetimi içeriğini yatay veya dikey akış yönü düzenler.</span><span class="sxs-lookup"><span data-stu-id="480d0-103">The <xref:System.Windows.Forms.FlowLayoutPanel> control arranges its contents in a horizontal or vertical flow direction.</span></span> <span data-ttu-id="480d0-104">Denetimin içeriği sonraki bir satır veya sonraki bir sütuna kayabilir.</span><span class="sxs-lookup"><span data-stu-id="480d0-104">You can wrap the control's contents from one row to the next, or from one column to the next.</span></span> <span data-ttu-id="480d0-105">Alternatif olarak, içeriği kaydırma yerine bölebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="480d0-105">Alternately, you can clip instead of wrap its contents.</span></span>  
  
 <span data-ttu-id="480d0-106">Akış yönü değeri ayarlayarak belirleyebilirsiniz <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="480d0-106">You can specify the flow direction by setting the value of the <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> property.</span></span> <span data-ttu-id="480d0-107"><xref:System.Windows.Forms.FlowLayoutPanel> Denetim doğru sağdan sola (RTL) düzenleri akış yönünü tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="480d0-107">The <xref:System.Windows.Forms.FlowLayoutPanel> control correctly reverses its flow direction in Right-to-Left (RTL) layouts.</span></span> <span data-ttu-id="480d0-108">Ayrıca belirtebilirsiniz olup olmadığını <xref:System.Windows.Forms.FlowLayoutPanel> denetimin içeriği Sarmalanan veya değerini ayarlayarak kırpılmış <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="480d0-108">You can also specify whether the <xref:System.Windows.Forms.FlowLayoutPanel> control's contents are wrapped or clipped by setting the value of the <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> property.</span></span>  
  
 <span data-ttu-id="480d0-109"><xref:System.Windows.Forms.FlowLayoutPanel> Ayarladığınızda boyutları içeriğine otomatik olarak kontrol <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="480d0-109">The <xref:System.Windows.Forms.FlowLayoutPanel> control automatically sizes to its contents when you set the <xref:System.Windows.Forms.Control.AutoSize%2A> property to `true`.</span></span> <span data-ttu-id="480d0-110">Ayrıca sağlayan bir **FlowBreak** alt denetimlerinden özelliğine.</span><span class="sxs-lookup"><span data-stu-id="480d0-110">It also provides a **FlowBreak** property to its child controls.</span></span> <span data-ttu-id="480d0-111">FlowBreak özelliğinin değerini ayarlama `true` neden <xref:System.Windows.Forms.FlowLayoutPanel> denetim geçerli akış yönü ve bir sonraki satır veya sütun kaydırılır denetimlerinde düzenlemeyi durdur.</span><span class="sxs-lookup"><span data-stu-id="480d0-111">Setting the value of the FlowBreak property to `true` causes the <xref:System.Windows.Forms.FlowLayoutPanel> control to stop laying out controls in the current flow direction and wrap to the next row or column.</span></span>  
  
 <span data-ttu-id="480d0-112">Herhangi bir Windows Forms denetimini bir alt olabilir <xref:System.Windows.Forms.FlowLayoutPanel> diğer örnekleri dahil olmak üzere Denetim <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="480d0-112">Any Windows Forms control can be a child of the <xref:System.Windows.Forms.FlowLayoutPanel> control, including other instances of <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="480d0-113">Bu özellik ile çalışma zamanında, formun boyutlarını uyum Gelişmiş düzenleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="480d0-113">With this capability, you can construct sophisticated layouts that adapt to your form's dimensions at run time.</span></span>  
  
 <span data-ttu-id="480d0-114">Ayrıca bkz. [izlenecek yol: Windows Forms FlowLayoutPanel kullanarak düzenleme denetimleri](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="480d0-114">Also see [Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="480d0-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="480d0-115">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="480d0-116">FlowLayoutPanel Denetimi</span><span class="sxs-lookup"><span data-stu-id="480d0-116">FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-windows-forms.md)
