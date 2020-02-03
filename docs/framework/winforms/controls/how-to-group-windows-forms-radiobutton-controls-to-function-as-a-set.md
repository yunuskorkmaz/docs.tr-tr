---
title: Grup RadioButton denetimlerini küme olarak çalışacak şekilde grupla
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: c4b37c84bf0f93837b91c743c7681d39fd83a659
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732943"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a><span data-ttu-id="47d0c-102">Nasıl yapılır: Windows Forms RadioButton Denetimlerini Küme İşlevi Görecek Şekilde Gruplama</span><span class="sxs-lookup"><span data-stu-id="47d0c-102">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>
<span data-ttu-id="47d0c-103">Windows Forms <xref:System.Windows.Forms.RadioButton> denetimleri, kullanıcılara iki veya daha fazla ayar arasında seçim yapmak için tasarlanmıştır. Bu, yalnızca bir yordama veya nesneye atanabilir.</span><span class="sxs-lookup"><span data-stu-id="47d0c-103">Windows Forms <xref:System.Windows.Forms.RadioButton> controls are designed to give users a choice among two or more settings, of which only one can be assigned to a procedure or object.</span></span> <span data-ttu-id="47d0c-104">Örneğin, bir <xref:System.Windows.Forms.RadioButton> denetimleri grubu, bir sipariş için paket taşıyıcılar seçimi gösterebilir, ancak yalnızca bir tane taşıyıcılar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="47d0c-104">For example, a group of <xref:System.Windows.Forms.RadioButton> controls may display a choice of package carriers for an order, but only one of the carriers will be used.</span></span> <span data-ttu-id="47d0c-105">Bu nedenle, bir işlevsel grubun parçası olsa bile tek seferde yalnızca bir <xref:System.Windows.Forms.RadioButton> seçilebilir.</span><span class="sxs-lookup"><span data-stu-id="47d0c-105">Therefore only one <xref:System.Windows.Forms.RadioButton> at a time can be selected, even if it is a part of a functional group.</span></span>  
  
 <span data-ttu-id="47d0c-106">Radyo düğmelerini, <xref:System.Windows.Forms.Panel> denetimi, <xref:System.Windows.Forms.GroupBox> denetimi veya form gibi bir kapsayıcının içine çizerek gruplandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47d0c-106">You group radio buttons by drawing them inside a container such as a <xref:System.Windows.Forms.Panel> control, a <xref:System.Windows.Forms.GroupBox> control, or a form.</span></span> <span data-ttu-id="47d0c-107">Doğrudan bir forma eklenen tüm radyo düğmeleri tek bir grup haline gelir.</span><span class="sxs-lookup"><span data-stu-id="47d0c-107">All radio buttons that are added directly to a form become one group.</span></span> <span data-ttu-id="47d0c-108">Ayrı gruplar eklemek için bunları panellerin veya grup kutularının içine yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="47d0c-108">To add separate groups, you must place them inside panels or group boxes.</span></span> <span data-ttu-id="47d0c-109">Paneller veya Grup kutuları hakkında daha fazla bilgi için bkz. [panel denetimine genel bakış](panel-control-overview-windows-forms.md) veya [GroupBox denetimine genel bakış](groupbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="47d0c-109">For more information about panels or group boxes, see [Panel Control Overview](panel-control-overview-windows-forms.md) or [GroupBox Control Overview](groupbox-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a><span data-ttu-id="47d0c-110">RadioButton denetimlerini diğer kümelerden bağımsız olarak çalışacak şekilde gruplandırmak için</span><span class="sxs-lookup"><span data-stu-id="47d0c-110">To group RadioButton controls as a set to function independently of other sets</span></span>  
  
1. <span data-ttu-id="47d0c-111">**Araç kutusundaki** **Windows Forms** sekmesinden bir <xref:System.Windows.Forms.GroupBox> veya <xref:System.Windows.Forms.Panel> denetimini form üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="47d0c-111">Drag a <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab on the **Toolbox** onto the form.</span></span>  
  
2. <span data-ttu-id="47d0c-112"><xref:System.Windows.Forms.GroupBox> veya <xref:System.Windows.Forms.Panel> denetiminde <xref:System.Windows.Forms.RadioButton> denetimleri çizin.</span><span class="sxs-lookup"><span data-stu-id="47d0c-112">Draw <xref:System.Windows.Forms.RadioButton> controls on the <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47d0c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47d0c-113">See also</span></span>

- <xref:System.Windows.Forms.RadioButton>
- [<span data-ttu-id="47d0c-114">RadioButton Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="47d0c-114">RadioButton Control Overview</span></span>](radiobutton-control-overview-windows-forms.md)
- [<span data-ttu-id="47d0c-115">Panel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="47d0c-115">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="47d0c-116">GroupBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="47d0c-116">GroupBox Control Overview</span></span>](groupbox-control-overview-windows-forms.md)
- [<span data-ttu-id="47d0c-117">CheckBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="47d0c-117">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="47d0c-118">RadioButton Denetimi</span><span class="sxs-lookup"><span data-stu-id="47d0c-118">RadioButton Control</span></span>](radiobutton-control-windows-forms.md)
