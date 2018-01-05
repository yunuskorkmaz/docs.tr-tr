---
title: "Windows Forms Düğme Denetimi Seçmenin Yolları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b6fa31b89b8fbe50077933cf04aa3c17db86438
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ways-to-select-a-windows-forms-button-control"></a><span data-ttu-id="f5f4a-102">Windows Forms Düğme Denetimi Seçmenin Yolları</span><span class="sxs-lookup"><span data-stu-id="f5f4a-102">Ways to Select a Windows Forms Button Control</span></span>
<span data-ttu-id="f5f4a-103">Bir Windows Forms düğme, aşağıdaki yollarla seçilebilir:</span><span class="sxs-lookup"><span data-stu-id="f5f4a-103">A Windows Forms button can be selected in the following ways:</span></span>  
  
-   <span data-ttu-id="f5f4a-104">Fare düğmesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f5f4a-104">Use a mouse to click the button.</span></span>  
  
-   <span data-ttu-id="f5f4a-105">Düğmenin çağırma <xref:System.Windows.Forms.Control.Click> kodundaki olay.</span><span class="sxs-lookup"><span data-stu-id="f5f4a-105">Invoke the button's <xref:System.Windows.Forms.Control.Click> event in code.</span></span>  
  
-   <span data-ttu-id="f5f4a-106">Odağı Taşı düğmesi için SEKME tuşuna basarak ve ardından Ara çubuğu veya ENTER tuşuna basarak düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f5f4a-106">Move the focus to the button by pressing the TAB key, and then choose the button by pressing the SPACEBAR or ENTER.</span></span>  
  
-   <span data-ttu-id="f5f4a-107">Erişim anahtarı (ALT + altı çizili harfi) düğmesine basın.</span><span class="sxs-lookup"><span data-stu-id="f5f4a-107">Press the access key (ALT + the underlined letter) for the button.</span></span> <span data-ttu-id="f5f4a-108">Erişim anahtarları hakkında daha fazla bilgi için bkz: [nasıl yapılır: oluşturmak erişim anahtarları için Windows Forms denetimleri](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="f5f4a-108">For more information about access keys, see [How to: Create Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
-   <span data-ttu-id="f5f4a-109">Düğme biçiminde "kabul" düğmesine ise, başka bir denetim odağı olsa bile ENTER tuşuna basarak düğmesini seçer — diğer denetleyen başka bir düğme, çok satırlı metin kutusu veya enter tuşuna yakalar özel bir denetim ise dışındaki.</span><span class="sxs-lookup"><span data-stu-id="f5f4a-109">If the button is the "accept" button of the form, pressing ENTER chooses the button, even if another control has the focus — except if that other control is another button, a multi-line text box, or a custom control that traps the enter key.</span></span>  
  
-   <span data-ttu-id="f5f4a-110">Düğme "İptal" düğmesini biçiminde ise, başka bir denetim odağı olsa bile ESC tuşuna basarak düğmesini seçer.</span><span class="sxs-lookup"><span data-stu-id="f5f4a-110">If the button is the "cancel" button of the form, pressing ESC chooses the button, even if another control has the focus.</span></span>  
  
-   <span data-ttu-id="f5f4a-111">Çağrı <xref:System.Windows.Forms.Button.PerformClick%2A> yöntemi program aracılığıyla düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f5f4a-111">Call the <xref:System.Windows.Forms.Button.PerformClick%2A> method to select the button programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5f4a-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f5f4a-112">See Also</span></span>  
 [<span data-ttu-id="f5f4a-113">Düğme Kontrolüne Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f5f4a-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="f5f4a-114">Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="f5f4a-114">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="f5f4a-115">Düğme Kontrolü</span><span class="sxs-lookup"><span data-stu-id="f5f4a-115">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
