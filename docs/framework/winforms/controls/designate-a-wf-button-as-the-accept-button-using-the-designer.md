---
title: Tasarımcıyı kullanarak bir düğmeyi kabul et düğmesi olarak belirleme
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: 27a5de51f8c5b2c84cc205e09ac1a2179c315752
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746070"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a><span data-ttu-id="bce68-102">Nasıl yapılır: Tasarımcı Kullanarak Kabul Düğmesi olarak bir Windows Formları Düğmesi Atama</span><span class="sxs-lookup"><span data-stu-id="bce68-102">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>
<span data-ttu-id="bce68-103">Herhangi bir Windows formunda, bir <xref:System.Windows.Forms.Button> denetimini, varsayılan düğme olarak da bilinen kabul et düğmesi olacak şekilde belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bce68-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="bce68-104">Kullanıcı ENTER tuşuna bastığında, form üzerindeki diğer denetimin odağa sahip olduğu bağımsız olarak varsayılan düğme tıklanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bce68-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="bce68-105">Bunun özel durumları, odağa sahip olan denetimin başka bir düğme olduğu durumdur. Bu durumda, odağa sahip düğme veya çok satırlı bir metin kutusu ya da ENTER tuşunu yakaladığı özel bir denetim olur.</span><span class="sxs-lookup"><span data-stu-id="bce68-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>

## <a name="to-designate-the-accept-button"></a><span data-ttu-id="bce68-106">Kabul et düğmesini belirlemek için</span><span class="sxs-lookup"><span data-stu-id="bce68-106">To designate the accept button</span></span>

1. <span data-ttu-id="bce68-107">Düğmenin bulunduğu formu seçin.</span><span class="sxs-lookup"><span data-stu-id="bce68-107">Select the form on which the button resides.</span></span>

2. <span data-ttu-id="bce68-108">**Özellikler** penceresinde, formun <xref:System.Windows.Forms.Form.AcceptButton%2A> özelliğini <xref:System.Windows.Forms.Button> denetimin adı olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bce68-108">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>

## <a name="see-also"></a><span data-ttu-id="bce68-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bce68-109">See also</span></span>

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [<span data-ttu-id="bce68-110">Düğme Kontrolüne Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bce68-110">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="bce68-111">Windows Forms Düğme Kontrolü Seçme Yolları</span><span class="sxs-lookup"><span data-stu-id="bce68-111">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="bce68-112">Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="bce68-112">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="bce68-113">Nasıl yapılır: Tasarımcı Kullanarak Bir Windows Forms Düğmesini İptal Düğmesi Olarak Belirtme</span><span class="sxs-lookup"><span data-stu-id="bce68-113">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [<span data-ttu-id="bce68-114">Düğme Kontrolü</span><span class="sxs-lookup"><span data-stu-id="bce68-114">Button Control</span></span>](button-control-windows-forms.md)
