---
title: Bölümlendirici Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Splitter
helpviewer_keywords:
- Splitter control [Windows Forms], about Splitter control
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
ms.openlocfilehash: 2e3e46c9d4cf118bb846e5d9efefeb0d57fea567
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703206"
---
# <a name="splitter-control-overview-windows-forms"></a><span data-ttu-id="e4763-102">Bölümlendirici Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e4763-102">Splitter Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="e4763-103">Ancak <xref:System.Windows.Forms.SplitContainer> değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.Splitter> önceki sürümlerinde, denetimin <xref:System.Windows.Forms.Splitter> seçerseniz geriye dönük uyumluluk ve gelecekte kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="e4763-103">Although <xref:System.Windows.Forms.SplitContainer> replaces and adds functionality to the <xref:System.Windows.Forms.Splitter> control of previous versions, <xref:System.Windows.Forms.Splitter> is retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="e4763-104">Windows Forms <xref:System.Windows.Forms.Splitter> denetimleri yerleşik denetimlerin çalışma zamanında yeniden boyutlandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e4763-104">Windows Forms <xref:System.Windows.Forms.Splitter> controls are used to resize docked controls at run time.</span></span> <span data-ttu-id="e4763-105"><xref:System.Windows.Forms.Splitter> Değişen uzunlukları, veri bölmeleri içeren genişlikleri değişen bir bilgilerinin farklı zamanlarda, Windows Gezgini gibi sunmak için veri denetimleri ile formlarında genellikle Denetim kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e4763-105">The <xref:System.Windows.Forms.Splitter> control is often used on forms with controls that have varying lengths of data to present, like Windows Explorer, whose data panes contain information of varying widths at different times.</span></span>  
  
## <a name="working-with-the-splitter-control"></a><span data-ttu-id="e4763-106">Bölümlendirici denetimi ile çalışma</span><span class="sxs-lookup"><span data-stu-id="e4763-106">Working with the Splitter Control</span></span>  
 <span data-ttu-id="e4763-107">Bölümlendirici denetimi tarafından yeniden boyutlandırılabilir bir denetimin yerleştirilmemiş uç cihazlarında fare işaretçisi kullanıcı işaret ettiğinde, işaretçi denetimi boyutlandırılabileceğini belirtmekte görünümünü değiştirir.</span><span class="sxs-lookup"><span data-stu-id="e4763-107">When the user points the mouse pointer at the undocked edge of a control that can be resized by a splitter control, the pointer changes its appearance to indicate that the control can be resized.</span></span> <span data-ttu-id="e4763-108">Bölümlendirici denetimi ile kullanıcı hemen önce bu yerleşik denetimi yeniden boyutlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4763-108">With the splitter control, the user can resize the docked control that is immediately before it.</span></span> <span data-ttu-id="e4763-109">Bu nedenle, bir yerleşik denetimin çalışma zamanında yeniden boyutlandırmak kullanıcının etkinleştirmek için bir kapsayıcının bir kenara boyutlandırılmaya denetim noktası ve ardından bu kapsayıcı aynı tarafına Bölümlendirici denetimi dock.</span><span class="sxs-lookup"><span data-stu-id="e4763-109">Therefore, to enable the user to resize a docked control at run time, dock the control to be resized to an edge of a container, and then dock a splitter control to the same side of that container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4763-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4763-110">See also</span></span>
- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="e4763-111">Nasıl yapılır: Windows Forms'da denetimleri yerleştirme</span><span class="sxs-lookup"><span data-stu-id="e4763-111">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="e4763-112">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="e4763-112">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
