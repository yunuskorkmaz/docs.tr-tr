---
title: "HelpProvider Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- HelpProvider
helpviewer_keywords:
- HelpProvider component [Windows Forms], about HelpProvider component
- Help [Windows Forms], adding to Windows applications
- F1 Help [Windows Forms], adding to Windows Forms
- dialog boxes [Windows Forms], context-sensitive Help
- Windows Forms, context-sensitive Help
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 23a9db5f7c5286eaab50f2499845f7294af878ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="helpprovider-component-overview-windows-forms"></a><span data-ttu-id="4b1ac-102">HelpProvider Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="4b1ac-102">HelpProvider Component Overview (Windows Forms)</span></span>
<span data-ttu-id="4b1ac-103">Windows Forms [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) bileşen bir HTML Yardımı 1.x Yardım dosyası (HTML Yardım Atölyesi ile üretilen bir .chm dosyasını veya bir .htm dosyasının), Windows uygulama ile ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4b1ac-103">The Windows Forms [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows application.</span></span> <span data-ttu-id="4b1ac-104">Çeşitli şekillerde Yardım sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4b1ac-104">You can provide help in a variety of ways:</span></span>  
  
-   <span data-ttu-id="4b1ac-105">Windows Forms denetimleri için bağlama duyarlı Yardım sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b1ac-105">Provide context-sensitive Help for controls on Windows Forms.</span></span>  
  
-   <span data-ttu-id="4b1ac-106">Belirli iletişim kutusu veya belirli bir iletişim kutusu denetimlere bağlama duyarlı Yardım sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b1ac-106">Provide context-sensitive Help on a particular dialog box or specific controls on a dialog box.</span></span>  
  
-   <span data-ttu-id="4b1ac-107">Ana sayfanın içindekiler tablosu, dizin veya arama işlevi gibi belirli alanlar için bir Yardım dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="4b1ac-107">Open a Help file to specific areas, such as the main page of a Table of Contents, the Index, or a search function.</span></span>  
  
## <a name="using-the-help-provider"></a><span data-ttu-id="4b1ac-108">Yardım sağlayıcısını kullanma</span><span class="sxs-lookup"><span data-stu-id="4b1ac-108">Using the Help Provider</span></span>  
 <span data-ttu-id="4b1ac-109">Ekleme bir <xref:System.Windows.Forms.HelpProvider> Windows formunuza bileşeni Yardım özelliklerini göstermek için formdaki diğer denetimleri sağlar <xref:System.Windows.Forms.HelpProvider> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="4b1ac-109">Adding a <xref:System.Windows.Forms.HelpProvider> component to your Windows Form allows the other controls on the form to expose the Help properties of the <xref:System.Windows.Forms.HelpProvider> component.</span></span> <span data-ttu-id="4b1ac-110">Bu, Windows formundaki denetimler için Yardım vermenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b1ac-110">This enables you to provide help for the controls on your Windows Form.</span></span> <span data-ttu-id="4b1ac-111">Yardım dosyası ile ilişkilendirebilirsiniz <xref:System.Windows.Forms.HelpProvider> bileşenini kullanarak <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4b1ac-111">You can associate a Help file with the <xref:System.Windows.Forms.HelpProvider> component using the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property.</span></span> <span data-ttu-id="4b1ac-112">Çağıran sağlanan Yardım türünü belirtin <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> arasında bir değer sağlayarak ve <xref:System.Windows.Forms.HelpNavigator> belirtilen denetim numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="4b1ac-112">You specify the type of Help provided by calling <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> and providing a value from the <xref:System.Windows.Forms.HelpNavigator> enumeration for the specified control.</span></span> <span data-ttu-id="4b1ac-113">Anahtar sözcük ya da konu yardımını çağırarak sağladığınız <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4b1ac-113">You provide the keyword or topic for Help by calling the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> method.</span></span>  
  
 <span data-ttu-id="4b1ac-114">İsteğe bağlı olarak, belirli bir Yardım dizeyi başka bir denetimi ile ilişkilendirmek için kullanın <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4b1ac-114">Optionally, to associate a specific Help string with another control, use the <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> method.</span></span> <span data-ttu-id="4b1ac-115">Kullanıcı denetimi odağa sahipken F1 tuşuna bastığında bu yöntemi kullanarak bir denetimle ilişkilendirme dize açılır pencerede görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4b1ac-115">The string that you associate with a control using this method is displayed in a pop-up window when the user presses the F1 key while the control has focus.</span></span>  
  
 <span data-ttu-id="4b1ac-116">Varsa <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> , kullanmalısınız ayarlanmadı değil <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> Yardım metni sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="4b1ac-116">If <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> has not been set, you must use <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> to provide the Help text.</span></span> <span data-ttu-id="4b1ac-117">Her ikisi de ayarladıysanız <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> ve Yardım dayalı Yardım dizesi <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> öncelikli olur.</span><span class="sxs-lookup"><span data-stu-id="4b1ac-117">If you have set both <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> and the Help string, Help based on <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> will take precedence.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b1ac-118">Göreli yolu kullanarak sorunlarla karşılaşabilirsiniz zaman belirtmeyi Yardım dosyasının yolu içinde <xref:System.Windows.Forms.Help.ShowHelp%2A> yöntemi veya <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> özelliği <xref:System.Windows.Forms.HelpProvider> denetim.</span><span class="sxs-lookup"><span data-stu-id="4b1ac-118">You may encounter problems using the relative path when specifiying the path to the Help file in the <xref:System.Windows.Forms.Help.ShowHelp%2A> method or <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property of the <xref:System.Windows.Forms.HelpProvider> control.</span></span> <span data-ttu-id="4b1ac-119">Bu nedenle, Yardım dosyasını belirtmek için mutlak dosya yolunu kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4b1ac-119">As such, be sure to use the absolute file path to specify the Help file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b1ac-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4b1ac-120">See Also</span></span>  
 [<span data-ttu-id="4b1ac-121">Windows Forms Uygulamalarındaki Yardım Sistemleri</span><span class="sxs-lookup"><span data-stu-id="4b1ac-121">Help Systems in Windows Forms Applications</span></span>](../../../../docs/framework/winforms/advanced/help-systems-in-windows-forms-applications.md)
