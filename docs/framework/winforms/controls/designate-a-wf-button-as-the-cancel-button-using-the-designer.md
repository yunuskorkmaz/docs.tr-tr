---
title: "Nasıl yapılır: Tasarımcı Kullanarak İptal Düğmesi olarak bir Windows Formları Düğmesi Atama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 28e1667d086f26759e0129fc62d94ea79c68d880
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a><span data-ttu-id="1da49-102">Nasıl yapılır: Tasarımcı Kullanarak İptal Düğmesi olarak bir Windows Formları Düğmesi Atama</span><span class="sxs-lookup"><span data-stu-id="1da49-102">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>
<span data-ttu-id="1da49-103">Herhangi bir Windows formunda tanımladığınız bir <xref:System.Windows.Forms.Button> iptal düğmesi olarak denetim.</span><span class="sxs-lookup"><span data-stu-id="1da49-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="1da49-104">Her kullanıcının hangi bağımsız olarak formunda diğer denetimi odağa sahip ESC tuşuna bastığında iptal düğmesine tıklandığında.</span><span class="sxs-lookup"><span data-stu-id="1da49-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="1da49-105">Bu tür bir düğme genellikle hızlı bir şekilde bir işlem için herhangi bir eylem kaydetmeden çıkmak kullanıcının etkinleştirmek için programlanmış.</span><span class="sxs-lookup"><span data-stu-id="1da49-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1da49-106">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="1da49-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1da49-107">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="1da49-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1da49-108">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="1da49-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-designate-the-cancel-button"></a><span data-ttu-id="1da49-109">İptal düğmesi atamak için</span><span class="sxs-lookup"><span data-stu-id="1da49-109">To designate the cancel button</span></span>  
  
1.  <span data-ttu-id="1da49-110">Düğme bulunduğu formu seçin.</span><span class="sxs-lookup"><span data-stu-id="1da49-110">Select the form on which the button resides.</span></span>  
  
2.  <span data-ttu-id="1da49-111">İçinde **özellikleri** penceresinde, formun ayarlamak <xref:System.Windows.Forms.Form.CancelButton%2A> özelliğine <xref:System.Windows.Forms.Button> denetimin adı.</span><span class="sxs-lookup"><span data-stu-id="1da49-111">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1da49-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1da49-112">See Also</span></span>  
 <xref:System.Windows.Forms.Form.CancelButton%2A>  
 [<span data-ttu-id="1da49-113">Düğme denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="1da49-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="1da49-114">Windows Forms düğme denetimi seçmenin yolları</span><span class="sxs-lookup"><span data-stu-id="1da49-114">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="1da49-115">Nasıl yapılır: Windows Forms düğme tıklamalarına yanıt verme</span><span class="sxs-lookup"><span data-stu-id="1da49-115">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="1da49-116">Nasıl yapılır: Tasarımcı kullanarak kabul düğmesi olarak bir Windows Formları düğmesi atama</span><span class="sxs-lookup"><span data-stu-id="1da49-116">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)  
 [<span data-ttu-id="1da49-117">Düğme denetimi</span><span class="sxs-lookup"><span data-stu-id="1da49-117">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
