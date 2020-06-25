---
title: Grup RadioButton denetimlerini küme olarak çalışacak şekilde grupla
description: Windows Forms RadioButton denetimlerini diğer kümelerden bağımsız olarak çalışacak şekilde nasıl grupleyeceğinizi öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: 9f6795330922e739cca1f2b5c11bb2ec68bb4e84
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325928"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a><span data-ttu-id="f8efa-103">Nasıl yapılır: Windows Forms RadioButton Denetimlerini Küme İşlevi Görecek Şekilde Gruplama</span><span class="sxs-lookup"><span data-stu-id="f8efa-103">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>
<span data-ttu-id="f8efa-104">Windows Forms <xref:System.Windows.Forms.RadioButton> denetimleri, kullanıcılara iki veya daha fazla ayar arasında seçim yapmak üzere tasarlanmıştır. Bu, bir yordama veya nesneye yalnızca bir tane atanabilir.</span><span class="sxs-lookup"><span data-stu-id="f8efa-104">Windows Forms <xref:System.Windows.Forms.RadioButton> controls are designed to give users a choice among two or more settings, of which only one can be assigned to a procedure or object.</span></span> <span data-ttu-id="f8efa-105">Örneğin, bir Grup denetim, bir <xref:System.Windows.Forms.RadioButton> sipariş için paket taşıyıcılar seçimi gösterebilir, ancak yalnızca bir tane taşıyıcılar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f8efa-105">For example, a group of <xref:System.Windows.Forms.RadioButton> controls may display a choice of package carriers for an order, but only one of the carriers will be used.</span></span> <span data-ttu-id="f8efa-106">Bu nedenle <xref:System.Windows.Forms.RadioButton> , bir işlevsel grubun parçası olsa bile tek seferde yalnızca bir tane seçilebilir.</span><span class="sxs-lookup"><span data-stu-id="f8efa-106">Therefore only one <xref:System.Windows.Forms.RadioButton> at a time can be selected, even if it is a part of a functional group.</span></span>  
  
 <span data-ttu-id="f8efa-107">Radyo düğmelerini <xref:System.Windows.Forms.Panel> Denetim, denetim veya form gibi bir kapsayıcının içine çizerek gruplandırabilirsiniz <xref:System.Windows.Forms.GroupBox> .</span><span class="sxs-lookup"><span data-stu-id="f8efa-107">You group radio buttons by drawing them inside a container such as a <xref:System.Windows.Forms.Panel> control, a <xref:System.Windows.Forms.GroupBox> control, or a form.</span></span> <span data-ttu-id="f8efa-108">Doğrudan bir forma eklenen tüm radyo düğmeleri tek bir grup haline gelir.</span><span class="sxs-lookup"><span data-stu-id="f8efa-108">All radio buttons that are added directly to a form become one group.</span></span> <span data-ttu-id="f8efa-109">Ayrı gruplar eklemek için bunları panellerin veya grup kutularının içine yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8efa-109">To add separate groups, you must place them inside panels or group boxes.</span></span> <span data-ttu-id="f8efa-110">Paneller veya Grup kutuları hakkında daha fazla bilgi için bkz. [panel denetimine genel bakış](panel-control-overview-windows-forms.md) veya [GroupBox denetimine genel bakış](groupbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f8efa-110">For more information about panels or group boxes, see [Panel Control Overview](panel-control-overview-windows-forms.md) or [GroupBox Control Overview](groupbox-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a><span data-ttu-id="f8efa-111">RadioButton denetimlerini diğer kümelerden bağımsız olarak çalışacak şekilde gruplandırmak için</span><span class="sxs-lookup"><span data-stu-id="f8efa-111">To group RadioButton controls as a set to function independently of other sets</span></span>  
  
1. <span data-ttu-id="f8efa-112"><xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> **Araç kutusundaki** **Windows Forms** sekmesinden bir veya denetimini form üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="f8efa-112">Drag a <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab on the **Toolbox** onto the form.</span></span>  
  
2. <span data-ttu-id="f8efa-113"><xref:System.Windows.Forms.RadioButton>Veya denetiminde denetimler çizin <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> .</span><span class="sxs-lookup"><span data-stu-id="f8efa-113">Draw <xref:System.Windows.Forms.RadioButton> controls on the <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8efa-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8efa-114">See also</span></span>

- <xref:System.Windows.Forms.RadioButton>
- [<span data-ttu-id="f8efa-115">RadioButton Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f8efa-115">RadioButton Control Overview</span></span>](radiobutton-control-overview-windows-forms.md)
- [<span data-ttu-id="f8efa-116">Panel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f8efa-116">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="f8efa-117">GroupBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f8efa-117">GroupBox Control Overview</span></span>](groupbox-control-overview-windows-forms.md)
- [<span data-ttu-id="f8efa-118">CheckBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f8efa-118">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="f8efa-119">RadioButton Denetimi</span><span class="sxs-lookup"><span data-stu-id="f8efa-119">RadioButton Control</span></span>](radiobutton-control-windows-forms.md)
