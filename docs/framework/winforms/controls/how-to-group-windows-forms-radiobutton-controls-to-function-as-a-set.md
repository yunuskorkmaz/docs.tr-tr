---
title: 'Nasıl yapılır: Windows Forms RadioButton Denetimlerini Küme İşlevi Görecek Şekilde Gruplama'
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: cbc6ab410fa2ab9d89255f82863e51aad36f8c18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534509"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a><span data-ttu-id="8697c-102">Nasıl yapılır: Windows Forms RadioButton Denetimlerini Küme İşlevi Görecek Şekilde Gruplama</span><span class="sxs-lookup"><span data-stu-id="8697c-102">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>
<span data-ttu-id="8697c-103">Windows Forms <xref:System.Windows.Forms.RadioButton> denetimleri hangisinin yalnızca biri atanabilir bir yordam veya nesne, iki veya daha fazla ayarları arasından seçim kullanıcılara vermek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8697c-103">Windows Forms <xref:System.Windows.Forms.RadioButton> controls are designed to give users a choice among two or more settings, of which only one can be assigned to a procedure or object.</span></span> <span data-ttu-id="8697c-104">Örneğin, bir grup <xref:System.Windows.Forms.RadioButton> denetimleri, sipariş paket hizmet sağlayıcılar seçimine görüntüleyebilir, ancak yalnızca bir hizmet sağlayıcılar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8697c-104">For example, a group of <xref:System.Windows.Forms.RadioButton> controls may display a choice of package carriers for an order, but only one of the carriers will be used.</span></span> <span data-ttu-id="8697c-105">Bu nedenle yalnızca bir <xref:System.Windows.Forms.RadioButton> işlevsel grubunun bir parçası olsa bile aynı anda seçilebilir.</span><span class="sxs-lookup"><span data-stu-id="8697c-105">Therefore only one <xref:System.Windows.Forms.RadioButton> at a time can be selected, even if it is a part of a functional group.</span></span>  
  
 <span data-ttu-id="8697c-106">İçinde bir kapsayıcı gibi çizerek radyo düğmesi grubunda bir <xref:System.Windows.Forms.Panel> denetimi, bir <xref:System.Windows.Forms.GroupBox> denetim ya da bir formu.</span><span class="sxs-lookup"><span data-stu-id="8697c-106">You group radio buttons by drawing them inside a container such as a <xref:System.Windows.Forms.Panel> control, a <xref:System.Windows.Forms.GroupBox> control, or a form.</span></span> <span data-ttu-id="8697c-107">Doğrudan bir form haline bir gruba eklenen tüm radyo düğmeleri.</span><span class="sxs-lookup"><span data-stu-id="8697c-107">All radio buttons that are added directly to a form become one group.</span></span> <span data-ttu-id="8697c-108">Ayrı grupları eklemek için bunları paneller veya grup kutuları içinde yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8697c-108">To add separate groups, you must place them inside panels or group boxes.</span></span> <span data-ttu-id="8697c-109">Panelleri veya grup kutuları hakkında daha fazla bilgi için bkz: [Panel denetimine genel bakış](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md) veya [GroupBox denetimine genel bakış](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8697c-109">For more information about panels or group boxes, see [Panel Control Overview](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md) or [GroupBox Control Overview](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a><span data-ttu-id="8697c-110">İşlev bağımsız olarak diğer ayarlar için bir küme olarak Grup RadioButton denetimlerini</span><span class="sxs-lookup"><span data-stu-id="8697c-110">To group RadioButton controls as a set to function independently of other sets</span></span>  
  
1.  <span data-ttu-id="8697c-111">Sürükleme bir <xref:System.Windows.Forms.GroupBox> veya <xref:System.Windows.Forms.Panel> gelen denetim **Windows Forms** sekmesi **araç** forma.</span><span class="sxs-lookup"><span data-stu-id="8697c-111">Drag a <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab on the **Toolbox** onto the form.</span></span>  
  
2.  <span data-ttu-id="8697c-112">Çizim <xref:System.Windows.Forms.RadioButton> denetimlerini <xref:System.Windows.Forms.GroupBox> veya <xref:System.Windows.Forms.Panel> denetim.</span><span class="sxs-lookup"><span data-stu-id="8697c-112">Draw <xref:System.Windows.Forms.RadioButton> controls on the <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8697c-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8697c-113">See Also</span></span>  
 <xref:System.Windows.Forms.RadioButton>  
 [<span data-ttu-id="8697c-114">RadioButton Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8697c-114">RadioButton Control Overview</span></span>](../../../../docs/framework/winforms/controls/radiobutton-control-overview-windows-forms.md)  
 [<span data-ttu-id="8697c-115">Panel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8697c-115">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [<span data-ttu-id="8697c-116">GroupBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8697c-116">GroupBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="8697c-117">CheckBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8697c-117">CheckBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="8697c-118">RadioButton Denetimi</span><span class="sxs-lookup"><span data-stu-id="8697c-118">RadioButton Control</span></span>](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)
