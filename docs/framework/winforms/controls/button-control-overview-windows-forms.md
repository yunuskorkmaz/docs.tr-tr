---
title: "Düğme Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e04b99c9d85ae92ad4d013abc01c5b16914fe1c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="button-control-overview-windows-forms"></a><span data-ttu-id="db03a-102">Düğme Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="db03a-102">Button Control Overview (Windows Forms)</span></span>
<span data-ttu-id="db03a-103">Windows Forms <xref:System.Windows.Forms.Button> denetimi sağlar kullanıcıya bir eylemi gerçekleştirmek için tıklatın.</span><span class="sxs-lookup"><span data-stu-id="db03a-103">The Windows Forms <xref:System.Windows.Forms.Button> control allows the user to click it to perform an action.</span></span> <span data-ttu-id="db03a-104">Düğme tıklatıldığında, düğmeye gibi durur ve yayımlandı.</span><span class="sxs-lookup"><span data-stu-id="db03a-104">When the button is clicked, it looks as if it is being pushed in and released.</span></span> <span data-ttu-id="db03a-105">Kullanıcı bir düğmesine tıkladığında <xref:System.Windows.Forms.Control.Click> olay işleyicisi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="db03a-105">Whenever the user clicks a button, the <xref:System.Windows.Forms.Control.Click> event handler is invoked.</span></span> <span data-ttu-id="db03a-106">Kodda yerleştirin <xref:System.Windows.Forms.Control.Click> seçtiğiniz herhangi bir eylemi gerçekleştirmek için olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="db03a-106">You place code in the <xref:System.Windows.Forms.Control.Click> event handler to perform any action you choose.</span></span>  
  
 <span data-ttu-id="db03a-107">Düğmeyi görüntülenen metni yer <xref:System.Windows.Forms.Control.Text%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="db03a-107">The text displayed on the button is contained in the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="db03a-108">Düğmenin genişliği metninizi aşarsa, bir sonraki satıra kaydırılır.</span><span class="sxs-lookup"><span data-stu-id="db03a-108">If your text exceeds the width of the button, it will wrap to the next line.</span></span> <span data-ttu-id="db03a-109">Ancak, genel yüksekliğini denetimi sağlayamazsa kırpılır.</span><span class="sxs-lookup"><span data-stu-id="db03a-109">However, it will be clipped if the control cannot accommodate its overall height.</span></span> <span data-ttu-id="db03a-110">Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms denetimi tarafından görüntülenen metni ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span><span class="sxs-lookup"><span data-stu-id="db03a-110">For more information, see [How to: Set the Text Displayed by a Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span></span> <span data-ttu-id="db03a-111"><xref:System.Windows.Forms.Control.Text%2A> Özelliği "Denetim erişim anahtarı ile ALT tuşuna basarak tıklayın" bir kullanıcıya izin veren bir erişim anahtarı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="db03a-111">The <xref:System.Windows.Forms.Control.Text%2A> property can contain an access key, which allows a user to "click" the control by pressing the ALT key with the access key.</span></span> <span data-ttu-id="db03a-112">Ayrıntılar için bkz [nasıl yapılır: oluşturmak erişim anahtarları için Windows Forms denetimleri](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="db03a-112">For details, see [How to: Create Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span></span> <span data-ttu-id="db03a-113">Metnin görünümünü tarafından denetlenen <xref:System.Windows.Forms.Control.Font%2A> özelliği ve <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="db03a-113">The appearance of the text is controlled by the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> property.</span></span>  
  
 <span data-ttu-id="db03a-114"><xref:System.Windows.Forms.Button> Denetim ayrıca kullanarak görüntüleri görüntüleme <xref:System.Windows.Forms.ButtonBase.Image%2A> ve <xref:System.Windows.Forms.ButtonBase.ImageList%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="db03a-114">The <xref:System.Windows.Forms.Button> control can also display images using the <xref:System.Windows.Forms.ButtonBase.Image%2A> and <xref:System.Windows.Forms.ButtonBase.ImageList%2A> properties.</span></span> <span data-ttu-id="db03a-115">Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms denetimi tarafından görüntülenen resmi ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).</span><span class="sxs-lookup"><span data-stu-id="db03a-115">For more information, see [How to: Set the Image Displayed by a Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db03a-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="db03a-116">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="db03a-117">Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="db03a-117">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="db03a-118">Windows Forms Düğme Kontrolü Seçme Yolları</span><span class="sxs-lookup"><span data-stu-id="db03a-118">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="db03a-119">Nasıl yapılır: Tasarımcı Kullanarak Bir Windows Forms Düğmesini Kabul Et Düğmesi Olarak Belirtme</span><span class="sxs-lookup"><span data-stu-id="db03a-119">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)  
 [<span data-ttu-id="db03a-120">Nasıl yapılır: Tasarımcı Kullanarak Bir Windows Forms Düğmesini İptal Düğmesi Olarak Belirtme</span><span class="sxs-lookup"><span data-stu-id="db03a-120">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [<span data-ttu-id="db03a-121">Düğme Kontrolü</span><span class="sxs-lookup"><span data-stu-id="db03a-121">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
