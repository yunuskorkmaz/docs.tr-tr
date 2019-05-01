---
title: Windows Forms'ta Kullanıcı Yardımını Tümleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], Windows Forms (using designer)
- Windows Forms, Help (using designer)
- HTML Help [Windows Forms], Windows Forms (using designer)
- Help [Windows Forms], Windows applications (using designer)
- forms. Help (using designer)
- Windows applications [Windows Forms], Help (using designer)
ms.assetid: a8563d25-8a75-4bc7-a024-f1870591b50f
ms.openlocfilehash: 207ceeafa2ea06340310577c636deb5ea1977aae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942928"
---
# <a name="integrating-user-help-in-windows-forms"></a><span data-ttu-id="79e19-102">Windows Forms'ta Kullanıcı Yardımını Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="79e19-102">Integrating User Help in Windows Forms</span></span>
<span data-ttu-id="79e19-103">Windows tabanlı uygulamalar oluşturmanın önemli, ancak genellikle kaçan bir boyut bu burada kez karışıklık, Yardım almak için kullanıcıları açın, Yardım sistemi aynıdır.</span><span class="sxs-lookup"><span data-stu-id="79e19-103">An essential, but often overlooked, aspect of building Windows-based applications is the Help system, as this is where users turn for assistance in times of confusion.</span></span> <span data-ttu-id="79e19-104">Windows Forms desteği Yardım iki farklı türü tarafından sağlanan her [HelpProvider bileşeni](../controls/helpprovider-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="79e19-104">Windows Forms support two different types of Help, each provided by the [HelpProvider Component](../controls/helpprovider-component-windows-forms.md).</span></span> <span data-ttu-id="79e19-105">İlk kullanıcı, bir HTML veya HTML Yardım 1 Yardım dosyasına işaret eden içerir. *x* veya büyük biçimi.</span><span class="sxs-lookup"><span data-stu-id="79e19-105">The first involves pointing the user to a Help file of either HTML or HTML Help 1.*x* or greater format.</span></span> <span data-ttu-id="79e19-106">İkinci kısa "Şudur" görüntüleyebilirsiniz-üzerindeki ayrı ayrı denetimler; Help yazın Bu iletişim kutularında özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="79e19-106">The second can display brief "What's This"-type Help on individual controls; this is especially useful on dialog boxes.</span></span> <span data-ttu-id="79e19-107">Aynı formda Yardım iki türü kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="79e19-107">Both types of Help can be used on the same form.</span></span>  
  
 <span data-ttu-id="79e19-108">Ayrıca, [ToolTip bileşeni](../controls/tooltip-component-windows-forms.md) Windows Forms'da denetimleri için tek tek Yardım sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="79e19-108">Additionally, the [ToolTip Component](../controls/tooltip-component-windows-forms.md) can be used to provide individual Help for controls on Windows Forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="79e19-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="79e19-109">In This Section</span></span>  
 [<span data-ttu-id="79e19-110">Nasıl yapılır: Bir Windows uygulamasında Yardım sağlama</span><span class="sxs-lookup"><span data-stu-id="79e19-110">How to: Provide Help in a Windows Application</span></span>](how-to-provide-help-in-a-windows-application.md)  
 <span data-ttu-id="79e19-111">Nasıl kullanılacağını açıklar `HelpProvider` denetimleri Yardım sisteminde dosyalarına Bağlama bileşeni.</span><span class="sxs-lookup"><span data-stu-id="79e19-111">Explains how to use the `HelpProvider` component to link controls to files in a Help system.</span></span>  
  
 [<span data-ttu-id="79e19-112">Nasıl yapılır: Açılır Yardımı görüntüleme</span><span class="sxs-lookup"><span data-stu-id="79e19-112">How to: Display Pop-up Help</span></span>](how-to-display-pop-up-help.md)  
 <span data-ttu-id="79e19-113">Nasıl kullanılacağını açıklar `HelpProvider` açılır Yardımı Windows formlarında göstermek için bileşeni.</span><span class="sxs-lookup"><span data-stu-id="79e19-113">Explains how to use the `HelpProvider` component to show pop-up Help on Windows Forms.</span></span>  
  
 [<span data-ttu-id="79e19-114">ToolTips Kullanarak Denetim Yardımı</span><span class="sxs-lookup"><span data-stu-id="79e19-114">Control Help Using ToolTips</span></span>](control-help-using-tooltips.md)  
 <span data-ttu-id="79e19-115">Kullanmayı açıklar `ToolTip` bileşen denetimine özgü Yardımı gösterilemiyor.</span><span class="sxs-lookup"><span data-stu-id="79e19-115">Describes using the `ToolTip` component to show control-specific Help.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="79e19-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="79e19-116">Related Sections</span></span>  
 [<span data-ttu-id="79e19-117">HelpProvider Bileşeni</span><span class="sxs-lookup"><span data-stu-id="79e19-117">HelpProvider Component</span></span>](../controls/helpprovider-component-windows-forms.md)  
 <span data-ttu-id="79e19-118">Temelleri açıklanır `HelpProvider` bileşeni.</span><span class="sxs-lookup"><span data-stu-id="79e19-118">Explains the basics of the `HelpProvider` component.</span></span>  
  
 [<span data-ttu-id="79e19-119">ToolTip Bileşeni</span><span class="sxs-lookup"><span data-stu-id="79e19-119">ToolTip Component</span></span>](../controls/tooltip-component-windows-forms.md)  
 <span data-ttu-id="79e19-120">Temelleri açıklanır `ToolTip` bileşeni.</span><span class="sxs-lookup"><span data-stu-id="79e19-120">Explains the basics of the `ToolTip` component.</span></span>  
  
 [<span data-ttu-id="79e19-121">Windows Forms'a Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="79e19-121">Windows Forms Overview</span></span>](../windows-forms-overview.md)  
 <span data-ttu-id="79e19-122">Windows Forms temellerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="79e19-122">Explains the basics of Windows Forms.</span></span>  
  
 [<span data-ttu-id="79e19-123">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="79e19-123">Windows Forms</span></span>](../index.md)  
 <span data-ttu-id="79e19-124">Windows Forms genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="79e19-124">Provides an overview of Windows Forms.</span></span>
