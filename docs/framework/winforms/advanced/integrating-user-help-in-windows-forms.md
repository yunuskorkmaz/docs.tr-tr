---
title: Kullanıcı yardımını tümleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], Windows Forms (using designer)
- Windows Forms, Help (using designer)
- HTML Help [Windows Forms], Windows Forms (using designer)
- Help [Windows Forms], Windows applications (using designer)
- forms. Help (using designer)
- Windows applications [Windows Forms], Help (using designer)
ms.assetid: a8563d25-8a75-4bc7-a024-f1870591b50f
ms.openlocfilehash: c402615d68c75327613d21bd35f1587b10f1dbf3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731572"
---
# <a name="integrating-user-help-in-windows-forms"></a><span data-ttu-id="16d87-102">Windows Forms'ta Kullanıcı Yardımını Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="16d87-102">Integrating User Help in Windows Forms</span></span>
<span data-ttu-id="16d87-103">Önemli olan, ancak genellikle daha fazla bakmış olan, Windows tabanlı uygulamalar oluşturmanın en çok olduğu, kullanıcıların karışıklık süreleriyle ilgili olarak yardım ettiği yerdir.</span><span class="sxs-lookup"><span data-stu-id="16d87-103">An essential, but often overlooked, aspect of building Windows-based applications is the Help system, as this is where users turn for assistance in times of confusion.</span></span> <span data-ttu-id="16d87-104">Windows Forms, her biri [HelpProvider bileşeni](../controls/helpprovider-component-windows-forms.md)tarafından sağlanan Iki farklı yardım türünü destekler.</span><span class="sxs-lookup"><span data-stu-id="16d87-104">Windows Forms support two different types of Help, each provided by the [HelpProvider Component](../controls/helpprovider-component-windows-forms.md).</span></span> <span data-ttu-id="16d87-105">Birincisi, kullanıcının HTML veya HTML Yardımı 1 ' in bir yardım dosyasına işaret eder. *x* veya daha büyük biçim.</span><span class="sxs-lookup"><span data-stu-id="16d87-105">The first involves pointing the user to a Help file of either HTML or HTML Help 1.*x* or greater format.</span></span> <span data-ttu-id="16d87-106">İkincisi, tek denetimler üzerinde kısa "Bu nedir"-Type yardımını gösterebilir; Bu, özellikle iletişim kutularında yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="16d87-106">The second can display brief "What's This"-type Help on individual controls; this is especially useful on dialog boxes.</span></span> <span data-ttu-id="16d87-107">Her iki tür yardım da aynı formda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16d87-107">Both types of Help can be used on the same form.</span></span>  
  
 <span data-ttu-id="16d87-108">Ayrıca, [araç Ipucu bileşeni](../controls/tooltip-component-windows-forms.md) Windows Forms denetimleri Için bireysel yardım sağlamak üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16d87-108">Additionally, the [ToolTip Component](../controls/tooltip-component-windows-forms.md) can be used to provide individual Help for controls on Windows Forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="16d87-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="16d87-109">In This Section</span></span>  
 [<span data-ttu-id="16d87-110">Nasıl yapılır: Bir Windows Uygulamasında Yardım Sağlama</span><span class="sxs-lookup"><span data-stu-id="16d87-110">How to: Provide Help in a Windows Application</span></span>](how-to-provide-help-in-a-windows-application.md)  
 <span data-ttu-id="16d87-111">`HelpProvider` bileşeninin, denetimleri bir Yardım sistemindeki dosyalara bağlamak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="16d87-111">Explains how to use the `HelpProvider` component to link controls to files in a Help system.</span></span>  
  
 [<span data-ttu-id="16d87-112">Nasıl yapılır: Açılır Yardımı Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="16d87-112">How to: Display Pop-up Help</span></span>](how-to-display-pop-up-help.md)  
 <span data-ttu-id="16d87-113">Windows Forms açılan menü yardımını göstermek için `HelpProvider` bileşeninin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="16d87-113">Explains how to use the `HelpProvider` component to show pop-up Help on Windows Forms.</span></span>  
  
 [<span data-ttu-id="16d87-114">ToolTips Kullanarak Denetim Yardımı</span><span class="sxs-lookup"><span data-stu-id="16d87-114">Control Help Using ToolTips</span></span>](control-help-using-tooltips.md)  
 <span data-ttu-id="16d87-115">Denetime özgü Yardımı göstermek için `ToolTip` bileşenin kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="16d87-115">Describes using the `ToolTip` component to show control-specific Help.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="16d87-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="16d87-116">Related Sections</span></span>  
 [<span data-ttu-id="16d87-117">HelpProvider Bileşeni</span><span class="sxs-lookup"><span data-stu-id="16d87-117">HelpProvider Component</span></span>](../controls/helpprovider-component-windows-forms.md)  
 <span data-ttu-id="16d87-118">`HelpProvider` bileşeni hakkında temel bilgileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="16d87-118">Explains the basics of the `HelpProvider` component.</span></span>  
  
 [<span data-ttu-id="16d87-119">ToolTip Bileşeni</span><span class="sxs-lookup"><span data-stu-id="16d87-119">ToolTip Component</span></span>](../controls/tooltip-component-windows-forms.md)  
 <span data-ttu-id="16d87-120">`ToolTip` bileşeni hakkında temel bilgileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="16d87-120">Explains the basics of the `ToolTip` component.</span></span>  
  
 [<span data-ttu-id="16d87-121">Windows Forms'a Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="16d87-121">Windows Forms Overview</span></span>](../windows-forms-overview.md)  
 <span data-ttu-id="16d87-122">Windows Forms ilgili temel bilgileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="16d87-122">Explains the basics of Windows Forms.</span></span>  
  
 [<span data-ttu-id="16d87-123">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="16d87-123">Windows Forms</span></span>](../index.md)  
 <span data-ttu-id="16d87-124">Windows Forms genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="16d87-124">Provides an overview of Windows Forms.</span></span>
