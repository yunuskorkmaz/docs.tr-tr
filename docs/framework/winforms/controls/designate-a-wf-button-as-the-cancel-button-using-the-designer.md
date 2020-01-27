---
title: Tasarımcı kullanarak bir düğmeyi Iptal düğmesi olarak belirleme
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: 95d1139b6e339055f944ad0b0967a6d91283d49e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746056"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a><span data-ttu-id="e4a69-102">Nasıl yapılır: Tasarımcı Kullanarak İptal Düğmesi olarak bir Windows Formları Düğmesi Atama</span><span class="sxs-lookup"><span data-stu-id="e4a69-102">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>
<span data-ttu-id="e4a69-103">Herhangi bir Windows formunda, bir <xref:System.Windows.Forms.Button> denetimini iptal düğmesi olacak şekilde belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4a69-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="e4a69-104">Kullanıcı, form üzerindeki diğer denetimin odağa sahip olduğu bağımsız olarak ESC tuşuna bastığında bir iptal düğmesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e4a69-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="e4a69-105">Bu tür bir düğme, genellikle kullanıcının herhangi bir eylemde bulunmadan bir işlemden hızlı bir şekilde çıkmasına olanak tanımak üzere programlanır.</span><span class="sxs-lookup"><span data-stu-id="e4a69-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>

## <a name="to-designate-the-cancel-button"></a><span data-ttu-id="e4a69-106">İptal düğmesini belirlemek için</span><span class="sxs-lookup"><span data-stu-id="e4a69-106">To designate the cancel button</span></span>

1. <span data-ttu-id="e4a69-107">Düğmenin bulunduğu formu seçin.</span><span class="sxs-lookup"><span data-stu-id="e4a69-107">Select the form on which the button resides.</span></span>

2. <span data-ttu-id="e4a69-108">**Özellikler** penceresinde, formun <xref:System.Windows.Forms.Form.CancelButton%2A> özelliğini <xref:System.Windows.Forms.Button> denetimin adı olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e4a69-108">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4a69-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4a69-109">See also</span></span>

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [<span data-ttu-id="e4a69-110">Düğme Kontrolüne Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e4a69-110">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="e4a69-111">Windows Forms Düğme Kontrolü Seçme Yolları</span><span class="sxs-lookup"><span data-stu-id="e4a69-111">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="e4a69-112">Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="e4a69-112">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="e4a69-113">Nasıl yapılır: Tasarımcı Kullanarak Bir Windows Forms Düğmesini Kabul Et Düğmesi Olarak Belirtme</span><span class="sxs-lookup"><span data-stu-id="e4a69-113">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [<span data-ttu-id="e4a69-114">Düğme Kontrolü</span><span class="sxs-lookup"><span data-stu-id="e4a69-114">Button Control</span></span>](button-control-windows-forms.md)
