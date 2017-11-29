---
title: "Windows Forms'ta Kullanıcı Yardımını Tümleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [Windows Forms], Windows Forms (using designer)
- Windows Forms, Help (using designer)
- HTML Help [Windows Forms], Windows Forms (using designer)
- Help [Windows Forms], Windows applications (using designer)
- forms. Help (using designer)
- Windows applications [Windows Forms], Help (using designer)
ms.assetid: a8563d25-8a75-4bc7-a024-f1870591b50f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b7ec4d32c5f025cb3e48b1403387273268d83fb8
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="integrating-user-help-in-windows-forms"></a><span data-ttu-id="2b43a-102">Windows Forms'ta Kullanıcı Yardımını Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="2b43a-102">Integrating User Help in Windows Forms</span></span>
<span data-ttu-id="2b43a-103">Windows tabanlı uygulamalar oluşturmanın gerekli, ancak genellikle gözden kaçan önemli, bir boyut Yardım sistemi aynıdır burada zamanlarında Karışıklığı önlemek için Yardım için kullanıcıların kapatma budur.</span><span class="sxs-lookup"><span data-stu-id="2b43a-103">An essential, but often overlooked, aspect of building Windows-based applications is the Help system, as this is where users turn for assistance in times of confusion.</span></span> <span data-ttu-id="2b43a-104">Windows Forms iki farklı türde Yardım desteği, her tarafından sağlanan [HelpProvider bileşeni](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2b43a-104">Windows Forms support two different types of Help, each provided by the [HelpProvider Component](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md).</span></span> <span data-ttu-id="2b43a-105">İlk kullanıcı bir HTML veya HTML Yardım 1 Yardım dosyasına işaret eden içerir. *x* veya büyük biçimi.</span><span class="sxs-lookup"><span data-stu-id="2b43a-105">The first involves pointing the user to a Help file of either HTML or HTML Help 1.*x* or greater format.</span></span> <span data-ttu-id="2b43a-106">İkinci kısa "Bu nedir" görüntüleyebilirsiniz-üzerindeki ayrı ayrı denetimler; Yardım yazın Bu iletişim kutularında özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="2b43a-106">The second can display brief "What's This"-type Help on individual controls; this is especially useful on dialog boxes.</span></span> <span data-ttu-id="2b43a-107">Her iki tür Yardım aynı formda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2b43a-107">Both types of Help can be used on the same form.</span></span>  
  
 <span data-ttu-id="2b43a-108">Ayrıca, [ToolTip bileşeni](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md) Windows formlarında denetimleri için tek tek Yardım sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2b43a-108">Additionally, the [ToolTip Component](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md) can be used to provide individual Help for controls on Windows Forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2b43a-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2b43a-109">In This Section</span></span>  
 [<span data-ttu-id="2b43a-110">Nasıl yapılır: bir Windows uygulamasında Yardım sağlama</span><span class="sxs-lookup"><span data-stu-id="2b43a-110">How to: Provide Help in a Windows Application</span></span>](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md)  
 <span data-ttu-id="2b43a-111">Nasıl kullanılacağı açıklanmaktadır `HelpProvider` denetimleri dosyaları Yardım sisteminde bağlamak için bileşen.</span><span class="sxs-lookup"><span data-stu-id="2b43a-111">Explains how to use the `HelpProvider` component to link controls to files in a Help system.</span></span>  
  
 [<span data-ttu-id="2b43a-112">Nasıl yapılır: açılır Yardımı görüntüleme</span><span class="sxs-lookup"><span data-stu-id="2b43a-112">How to: Display Pop-up Help</span></span>](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)  
 <span data-ttu-id="2b43a-113">Nasıl kullanılacağı açıklanmaktadır `HelpProvider` Windows Forms'ta açılır Yardım göstermek için bileşeni.</span><span class="sxs-lookup"><span data-stu-id="2b43a-113">Explains how to use the `HelpProvider` component to show pop-up Help on Windows Forms.</span></span>  
  
 [<span data-ttu-id="2b43a-114">ToolTips kullanarak denetim Yardımı</span><span class="sxs-lookup"><span data-stu-id="2b43a-114">Control Help Using ToolTips</span></span>](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 <span data-ttu-id="2b43a-115">Kullanmayı açıklar `ToolTip` denetim özgü Yardım göstermek için bileşeni.</span><span class="sxs-lookup"><span data-stu-id="2b43a-115">Describes using the `ToolTip` component to show control-specific Help.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2b43a-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="2b43a-116">Related Sections</span></span>  
 [<span data-ttu-id="2b43a-117">HelpProvider bileşeni</span><span class="sxs-lookup"><span data-stu-id="2b43a-117">HelpProvider Component</span></span>](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)  
 <span data-ttu-id="2b43a-118">Temelleri açıklanır `HelpProvider` bileşeni.</span><span class="sxs-lookup"><span data-stu-id="2b43a-118">Explains the basics of the `HelpProvider` component.</span></span>  
  
 [<span data-ttu-id="2b43a-119">ToolTip bileşeni</span><span class="sxs-lookup"><span data-stu-id="2b43a-119">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)  
 <span data-ttu-id="2b43a-120">Temelleri açıklanır `ToolTip` bileşeni.</span><span class="sxs-lookup"><span data-stu-id="2b43a-120">Explains the basics of the `ToolTip` component.</span></span>  
  
 [<span data-ttu-id="2b43a-121">Windows Forms'a genel bakış</span><span class="sxs-lookup"><span data-stu-id="2b43a-121">Windows Forms Overview</span></span>](../../../../docs/framework/winforms/windows-forms-overview.md)  
 <span data-ttu-id="2b43a-122">Windows Forms temelleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="2b43a-122">Explains the basics of Windows Forms.</span></span>  
  
 [<span data-ttu-id="2b43a-123">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2b43a-123">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)  
 <span data-ttu-id="2b43a-124">Windows Forms genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b43a-124">Provides an overview of Windows Forms.</span></span>
