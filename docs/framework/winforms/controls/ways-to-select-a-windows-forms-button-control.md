---
title: Düğme denetimi seçme yolları
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: 145166d182f1ec51068ab3e0c23c12b471b69231
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740009"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a><span data-ttu-id="f49bf-102">Windows Forms Düğme Denetimi Seçmenin Yolları</span><span class="sxs-lookup"><span data-stu-id="f49bf-102">Ways to Select a Windows Forms Button Control</span></span>
<span data-ttu-id="f49bf-103">Windows Forms bir düğme aşağıdaki yollarla seçilebilir:</span><span class="sxs-lookup"><span data-stu-id="f49bf-103">A Windows Forms button can be selected in the following ways:</span></span>  
  
- <span data-ttu-id="f49bf-104">Düğmeye tıklayarak fare kullanın.</span><span class="sxs-lookup"><span data-stu-id="f49bf-104">Use a mouse to click the button.</span></span>  
  
- <span data-ttu-id="f49bf-105">Koddaki <xref:System.Windows.Forms.Control.Click> olayını çağırın.</span><span class="sxs-lookup"><span data-stu-id="f49bf-105">Invoke the button's <xref:System.Windows.Forms.Control.Click> event in code.</span></span>  
  
- <span data-ttu-id="f49bf-106">Sekme tuşuna basarak odağı düğmeye taşıyın ve ardından ara çubuğuna veya ENTER tuşuna basarak düğmeyi seçin.</span><span class="sxs-lookup"><span data-stu-id="f49bf-106">Move the focus to the button by pressing the TAB key, and then choose the button by pressing the SPACEBAR or ENTER.</span></span>  
  
- <span data-ttu-id="f49bf-107">Düğme için erişim tuşuna (ALT + altı çizili harfe) basın.</span><span class="sxs-lookup"><span data-stu-id="f49bf-107">Press the access key (ALT + the underlined letter) for the button.</span></span> <span data-ttu-id="f49bf-108">Erişim anahtarları hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms denetimleri Için erişim tuşları oluşturma](how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="f49bf-108">For more information about access keys, see [How to: Create Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
- <span data-ttu-id="f49bf-109">Düğme, formun "kabul etme" düğmesidir, başka bir denetim odağa sahip olsa bile ENTER tuşuna basmak, diğer denetimin başka bir düğme, çok satırlı bir metin kutusu ya da Enter tuşunu yakaladığı özel bir denetim olması dışında, düğmeyi seçer.</span><span class="sxs-lookup"><span data-stu-id="f49bf-109">If the button is the "accept" button of the form, pressing ENTER chooses the button, even if another control has the focus — except if that other control is another button, a multi-line text box, or a custom control that traps the enter key.</span></span>  
  
- <span data-ttu-id="f49bf-110">Düğme, formun "iptal" düğmesidir, başka bir denetim odağa sahip olsa bile ESC tuşuna basmak düğmeyi seçer.</span><span class="sxs-lookup"><span data-stu-id="f49bf-110">If the button is the "cancel" button of the form, pressing ESC chooses the button, even if another control has the focus.</span></span>  
  
- <span data-ttu-id="f49bf-111">Düğmeyi program aracılığıyla seçmek için <xref:System.Windows.Forms.Button.PerformClick%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="f49bf-111">Call the <xref:System.Windows.Forms.Button.PerformClick%2A> method to select the button programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f49bf-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f49bf-112">See also</span></span>

- [<span data-ttu-id="f49bf-113">Düğme Kontrolüne Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f49bf-113">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="f49bf-114">Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="f49bf-114">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="f49bf-115">Düğme Kontrolü</span><span class="sxs-lookup"><span data-stu-id="f49bf-115">Button Control</span></span>](button-control-windows-forms.md)
