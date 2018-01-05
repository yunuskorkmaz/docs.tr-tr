---
title: "Windows Forms Uygulamalarındaki Yardım Sistemleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [Windows Forms], adding to Windows applications
- Windows applications [Windows Forms], providing Help systems
- What's This? Help
- Help [Windows Forms], Windows Forms
- HelpProvider component [Windows Forms], providing Help in Windows applications
ms.assetid: 2a96a278-432c-41fc-9e3c-5bfedf5e1267
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b2f5d067d487bbd5b91576927aee21a9a44fde0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="help-systems-in-windows-forms-applications"></a><span data-ttu-id="744a0-102">Windows Forms Uygulamalarındaki Yardım Sistemleri</span><span class="sxs-lookup"><span data-stu-id="744a0-102">Help Systems in Windows Forms Applications</span></span>
<span data-ttu-id="744a0-103">Aşağıdakilerden en önemli courtesies, uygulamaların, geliştirici furnish Kullanıcılarınızla aynıdır yetkin Yardım sistemi.</span><span class="sxs-lookup"><span data-stu-id="744a0-103">One of the most important courtesies you, as a developer of applications, can furnish your users with is a competent Help system.</span></span> <span data-ttu-id="744a0-104">Disoriented kafası veya hale burada bunlar dönüşecektir budur.</span><span class="sxs-lookup"><span data-stu-id="744a0-104">This is where they will turn when they become confused or disoriented.</span></span> <span data-ttu-id="744a0-105">Windows tabanlı bir uygulama Yardım sisteminde sağlama kolayca yapılır kullanarak [HelpProvider bileşeni](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="744a0-105">Providing a Help system in a Windows-based application is easily done by using the [HelpProvider Component](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md).</span></span>  
  
## <a name="different-types-of-help"></a><span data-ttu-id="744a0-106">Farklı türde Yardım</span><span class="sxs-lookup"><span data-stu-id="744a0-106">Different Types of Help</span></span>  
 <span data-ttu-id="744a0-107">Windows Forms <xref:System.Windows.Forms.HelpProvider> bileşen bir HTML Yardımı 1.x Yardım dosyası (HTML Yardım Atölyesi ile üretilen bir .chm dosyasını veya bir .htm dosyasının) ilişkilendirmek için kullanılan Windows tabanlı uygulamanızla.</span><span class="sxs-lookup"><span data-stu-id="744a0-107">The Windows Forms <xref:System.Windows.Forms.HelpProvider> component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows-based application.</span></span> <span data-ttu-id="744a0-108"><xref:System.Windows.Forms.HelpProvider> Bileşeni, Windows formlarında denetimleri veya özel denetimler bağlama duyarlı Yardım sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="744a0-108">The <xref:System.Windows.Forms.HelpProvider> component can be used to provide context-sensitive Help for controls on Windows Forms or specific controls.</span></span> <span data-ttu-id="744a0-109">Ayrıca, <xref:System.Windows.Forms.HelpProvider> bileşen ana sayfasının içeriği, bir dizin veya arama işlevini tablosunun gibi belirli alanlar için bir Yardım dosyası açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="744a0-109">Additionally, the <xref:System.Windows.Forms.HelpProvider> component can open a Help file to specific areas, such as the main page of a table of contents, an index, or a search function.</span></span> <span data-ttu-id="744a0-110">İlgili genel bilgiler için <xref:System.Windows.Forms.HelpProvider> bileşeni Bkz [HelpProvider bileşenine genel bakış](../../../../docs/framework/winforms/controls/helpprovider-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="744a0-110">For general information about the <xref:System.Windows.Forms.HelpProvider> component, see [HelpProvider Component Overview](../../../../docs/framework/winforms/controls/helpprovider-component-overview-windows-forms.md).</span></span> <span data-ttu-id="744a0-111">Nasıl kullanılacağı hakkında bilgi için <xref:System.Windows.Forms.HelpProvider> Windows formlarında açılır Yardım göstermek için bileşen bakın [nasıl yapılır: Görüntü açılır Yardım](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).</span><span class="sxs-lookup"><span data-stu-id="744a0-111">For information on how to use the <xref:System.Windows.Forms.HelpProvider> component to show pop-up Help on Windows Forms, see [How to: Display Pop-up Help](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).</span></span> <span data-ttu-id="744a0-112">Kullanma hakkında bilgi için <xref:System.Windows.Forms.ToolTip> denetim özgü Yardım göstermek için bileşen bakın [kullanarak denetim Yardımı ipuçlarını](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md).</span><span class="sxs-lookup"><span data-stu-id="744a0-112">For information on using the <xref:System.Windows.Forms.ToolTip> component to show control-specific Help, see [Control Help Using ToolTips](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md).</span></span>  
  
 <span data-ttu-id="744a0-113">HTML Yardımı 1.x HTML Yardım Atölyesi dosyalarıyla oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="744a0-113">You can generate HTML Help 1.x files with the HTML Help Workshop.</span></span> <span data-ttu-id="744a0-114">HTML Yardımı hakkında daha fazla bilgi için "HTML Yardım Atölyesi" veya MSDN'deki diğer "HTML Yardım" konularına bakın.</span><span class="sxs-lookup"><span data-stu-id="744a0-114">For more information on HTML Help, see the "HTML Help Workshop" or the other "HTML Help" topics in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="744a0-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="744a0-115">See Also</span></span>  
 [<span data-ttu-id="744a0-116">Windows Forms'ta Kullanıcı Yardımını Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="744a0-116">Integrating User Help in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [<span data-ttu-id="744a0-117">HelpProvider Bileşeni</span><span class="sxs-lookup"><span data-stu-id="744a0-117">HelpProvider Component</span></span>](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)  
 [<span data-ttu-id="744a0-118">ToolTip Bileşeni</span><span class="sxs-lookup"><span data-stu-id="744a0-118">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)  
 [<span data-ttu-id="744a0-119">Windows Forms'a Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="744a0-119">Windows Forms Overview</span></span>](../../../../docs/framework/winforms/windows-forms-overview.md)  
 [<span data-ttu-id="744a0-120">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="744a0-120">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
