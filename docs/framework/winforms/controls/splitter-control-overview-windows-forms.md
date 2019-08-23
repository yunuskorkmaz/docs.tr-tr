---
title: Bölümlendirici Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Splitter
helpviewer_keywords:
- Splitter control [Windows Forms], about Splitter control
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
ms.openlocfilehash: 934efd707f2a52da5ba604139c8e4510aad4606b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964454"
---
# <a name="splitter-control-overview-windows-forms"></a><span data-ttu-id="bef8d-102">Bölümlendirici Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="bef8d-102">Splitter Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="bef8d-103">, Ve önceki sürümlerin <xref:System.Windows.Forms.Splitter> denetimine işlevsellik ekler ve bu, <xref:System.Windows.Forms.Splitter> isterseniz hem geriye dönük uyumluluk hem de gelecekte kullanılmak üzere korunur. <xref:System.Windows.Forms.SplitContainer></span><span class="sxs-lookup"><span data-stu-id="bef8d-103">Although <xref:System.Windows.Forms.SplitContainer> replaces and adds functionality to the <xref:System.Windows.Forms.Splitter> control of previous versions, <xref:System.Windows.Forms.Splitter> is retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="bef8d-104">Windows Forms <xref:System.Windows.Forms.Splitter> denetimleri çalışma zamanında yerleşik denetimleri yeniden boyutlandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bef8d-104">Windows Forms <xref:System.Windows.Forms.Splitter> controls are used to resize docked controls at run time.</span></span> <span data-ttu-id="bef8d-105"><xref:System.Windows.Forms.Splitter> Denetim genellikle, veri bölmeleri farklı zamanlarda değişen genişlikler bilgisi içeren Windows Gezgini gibi, mevcut uzunluklara sahip denetimlerle birlikte formlarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bef8d-105">The <xref:System.Windows.Forms.Splitter> control is often used on forms with controls that have varying lengths of data to present, like Windows Explorer, whose data panes contain information of varying widths at different times.</span></span>  
  
## <a name="working-with-the-splitter-control"></a><span data-ttu-id="bef8d-106">Splitter denetimiyle çalışma</span><span class="sxs-lookup"><span data-stu-id="bef8d-106">Working with the Splitter Control</span></span>  
 <span data-ttu-id="bef8d-107">Kullanıcı, bir denetimin bir Splitter denetimi tarafından yeniden boyutlandırılabileceği bir denetimin yerleştirilmemiş kenarında fare işaretçisini işaret ediyorsa, işaretçiyi denetimin yeniden boyutlandırılabileceğini belirtmek için görünümünü değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bef8d-107">When the user points the mouse pointer at the undocked edge of a control that can be resized by a splitter control, the pointer changes its appearance to indicate that the control can be resized.</span></span> <span data-ttu-id="bef8d-108">Bölümlendirici denetimi ile, Kullanıcı hemen öncesindeki yerleşik denetimi yeniden boyutlandırabilir.</span><span class="sxs-lookup"><span data-stu-id="bef8d-108">With the splitter control, the user can resize the docked control that is immediately before it.</span></span> <span data-ttu-id="bef8d-109">Bu nedenle, kullanıcının çalışma zamanında yerleşik bir denetimi yeniden boyutlandırmasını etkinleştirmek için, denetimin bir kenarına yeniden boyutlandırılması için denetimi yerleştirin ve ardından Bu kapsayıcının aynı tarafına bir Splitter denetimi yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="bef8d-109">Therefore, to enable the user to resize a docked control at run time, dock the control to be resized to an edge of a container, and then dock a splitter control to the same side of that container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bef8d-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bef8d-110">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="bef8d-111">Nasıl yapılır: Windows Forms denetimleri yerleştirme</span><span class="sxs-lookup"><span data-stu-id="bef8d-111">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="bef8d-112">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="bef8d-112">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
