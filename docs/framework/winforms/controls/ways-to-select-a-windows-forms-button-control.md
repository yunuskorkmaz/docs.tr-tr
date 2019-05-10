---
title: Windows Forms Düğme Denetimi Seçmenin Yolları
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: e511b0d7bcac725ed477678ab4c865f5337e658d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584953"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a><span data-ttu-id="8d481-102">Windows Forms Düğme Denetimi Seçmenin Yolları</span><span class="sxs-lookup"><span data-stu-id="8d481-102">Ways to Select a Windows Forms Button Control</span></span>
<span data-ttu-id="8d481-103">Aşağıdaki yollarla bir Windows Forms düğmesini seçilebilir:</span><span class="sxs-lookup"><span data-stu-id="8d481-103">A Windows Forms button can be selected in the following ways:</span></span>  
  
- <span data-ttu-id="8d481-104">Fare düğmesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8d481-104">Use a mouse to click the button.</span></span>  
  
- <span data-ttu-id="8d481-105">Düğmenin çağırma <xref:System.Windows.Forms.Control.Click> kodundaki olay.</span><span class="sxs-lookup"><span data-stu-id="8d481-105">Invoke the button's <xref:System.Windows.Forms.Control.Click> event in code.</span></span>  
  
- <span data-ttu-id="8d481-106">Sekme tuşuna basarak düğmeyi odağı Taşı ve ardından bir boşluk veya ENTER tuşuna basarak düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="8d481-106">Move the focus to the button by pressing the TAB key, and then choose the button by pressing the SPACEBAR or ENTER.</span></span>  
  
- <span data-ttu-id="8d481-107">Erişim anahtarı (ALT + altı çizili harfi) düğmesine basın.</span><span class="sxs-lookup"><span data-stu-id="8d481-107">Press the access key (ALT + the underlined letter) for the button.</span></span> <span data-ttu-id="8d481-108">Erişim anahtarları hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms denetimleri için erişim tuşları oluşturma](how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="8d481-108">For more information about access keys, see [How to: Create Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
- <span data-ttu-id="8d481-109">Düğmeyi formun "kabul" düğmesine, başka bir denetim odağa sahip olsa bile ENTER tuşuna basarak düğmesini seçer — diğer denetleyen başka bir düğme, çok satırlı metin kutusu veya enter tuşuna yakalar özel bir denetim varsa hariç.</span><span class="sxs-lookup"><span data-stu-id="8d481-109">If the button is the "accept" button of the form, pressing ENTER chooses the button, even if another control has the focus — except if that other control is another button, a multi-line text box, or a custom control that traps the enter key.</span></span>  
  
- <span data-ttu-id="8d481-110">Düğmeyi formun "İptal" düğmesine, başka bir denetim odağa sahip olsa bile ESC tuşuna basarak düğmesini seçer.</span><span class="sxs-lookup"><span data-stu-id="8d481-110">If the button is the "cancel" button of the form, pressing ESC chooses the button, even if another control has the focus.</span></span>  
  
- <span data-ttu-id="8d481-111">Çağrı <xref:System.Windows.Forms.Button.PerformClick%2A> düğmeyi programlı olarak seçmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8d481-111">Call the <xref:System.Windows.Forms.Button.PerformClick%2A> method to select the button programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d481-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d481-112">See also</span></span>

- [<span data-ttu-id="8d481-113">Düğme Kontrolüne Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8d481-113">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="8d481-114">Nasıl yapılır: Windows Forms düğme tıklamalarına yanıt verme</span><span class="sxs-lookup"><span data-stu-id="8d481-114">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="8d481-115">Düğme Kontrolü</span><span class="sxs-lookup"><span data-stu-id="8d481-115">Button Control</span></span>](button-control-windows-forms.md)
