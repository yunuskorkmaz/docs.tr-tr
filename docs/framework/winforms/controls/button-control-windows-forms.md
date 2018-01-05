---
title: "Düğme Denetimi (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- buttons
- Button control [Windows Forms]
ms.assetid: d38bc40c-8040-4f19-9e88-2c665b0ab80b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 085ef918b2828dc754f5b91e0ad61262ce7d8c60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="button-control-windows-forms"></a><span data-ttu-id="273e9-102">Düğme Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="273e9-102">Button Control (Windows Forms)</span></span>
<span data-ttu-id="273e9-103">Windows Forms `Button` denetimi sağlar kullanıcıya bir eylemi gerçekleştirmek için tıklatın.</span><span class="sxs-lookup"><span data-stu-id="273e9-103">The Windows Forms `Button` control allows the user to click it to perform an action.</span></span> <span data-ttu-id="273e9-104">`Button` Denetim metin ve görüntüler görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="273e9-104">The `Button` control can display both text and images.</span></span> <span data-ttu-id="273e9-105">Düğme tıklatıldığında, düğmeye gibi durur ve yayımlandı.</span><span class="sxs-lookup"><span data-stu-id="273e9-105">When the button is clicked, it looks as if it is being pushed in and released.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="273e9-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="273e9-106">In This Section</span></span>  
 [<span data-ttu-id="273e9-107">Düğme Kontrolüne Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="273e9-107">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 <span data-ttu-id="273e9-108">Bu denetimi nedir ve anahtar özellikleri ve özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="273e9-108">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="273e9-109">Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="273e9-109">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 <span data-ttu-id="273e9-110">Bir Windows formunda bir düğme en temel kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="273e9-110">Explains the most basic use of a button on a Windows Form.</span></span>  
  
 [<span data-ttu-id="273e9-111">Nasıl yapılır: Bir Windows Forms Düğmesini Kabul Et Düğmesi Olarak Belirtme</span><span class="sxs-lookup"><span data-stu-id="273e9-111">How to: Designate a Windows Forms Button as the Accept Button</span></span>](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-accept-button.md)  
 <span data-ttu-id="273e9-112">Atama açıklar bir `Button` kabul et düğmesi olarak da bilinen varsayılan düğme olarak denetim.</span><span class="sxs-lookup"><span data-stu-id="273e9-112">Explains how to designate a `Button` control to be the accept button, also known as the default button.</span></span>  
  
 [<span data-ttu-id="273e9-113">Nasıl yapılır: Bir Windows Forms Düğmesini İptal Düğmesi Olarak Belirtme</span><span class="sxs-lookup"><span data-stu-id="273e9-113">How to: Designate a Windows Forms Button as the Cancel Button</span></span>](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-cancel-button.md)  
 <span data-ttu-id="273e9-114">Atama açıklar bir `Button` her kullanıcı ESC tuşuna bastığında tıklandığında iptal düğmesi olarak denetim.</span><span class="sxs-lookup"><span data-stu-id="273e9-114">Explains how to designate a `Button` control to be the cancel button, which is clicked whenever the user presses the ESC key.</span></span>  
  
 [<span data-ttu-id="273e9-115">Windows Forms Düğme Kontrolü Seçme Yolları</span><span class="sxs-lookup"><span data-stu-id="273e9-115">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 <span data-ttu-id="273e9-116">Bir düğme seçme yöntemlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="273e9-116">Lists methods of selecting a button.</span></span>  
  
 <span data-ttu-id="273e9-117">Ayrıca bkz. [nasıl yapılır: Tasarımcı kabul düğmesini kullanarak bir Windows Formları düğmesi atama](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md) ve [nasıl yapılır: Windows Forms düğmesini iptal düğmesi kullanılarak Tasarımcı belirtme](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="273e9-117">Also see [How to: Designate a Windows Forms Button as the Accept Button Using the Designer](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md) and [How to: Designate a Windows Forms Button as the Cancel Button Using the Designer](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="273e9-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="273e9-118">Reference</span></span>  
 <span data-ttu-id="273e9-119"><xref:System.Windows.Forms.Button>sınıfı</span><span class="sxs-lookup"><span data-stu-id="273e9-119"><xref:System.Windows.Forms.Button> class</span></span>  
 <span data-ttu-id="273e9-120">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="273e9-120">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="273e9-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="273e9-121">Related Sections</span></span>  
 [<span data-ttu-id="273e9-122">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="273e9-122">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="273e9-123">Windows Forms denetimleri, tam bir listesi ile bunların kullanılması hakkında bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="273e9-123">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 <span data-ttu-id="273e9-124">Ayrıca bkz. [iletişim kutuları için kullanıcı girişi](http://msdn.microsoft.com/en-us/63ad8645-6842-45e8-b215-73f778e29a55) ve [nasıl yapılır: Kapat iletişim kutuları ve kullanıcı girişi korumak](http://msdn.microsoft.com/en-us/9e118fad-3bf4-4f70-a3de-a0cda2b0229d).</span><span class="sxs-lookup"><span data-stu-id="273e9-124">Also see [User Input to Dialog Boxes](http://msdn.microsoft.com/en-us/63ad8645-6842-45e8-b215-73f778e29a55) and [How to: Close Dialog Boxes and Retain User Input](http://msdn.microsoft.com/en-us/9e118fad-3bf4-4f70-a3de-a0cda2b0229d).</span></span>
