---
title: "Özel Denetim Boyama ve İşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 355a5842348aa4395d1841d0343080ddef634456
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-control-painting-and-rendering"></a><span data-ttu-id="e5826-102">Özel Denetim Boyama ve İşleme</span><span class="sxs-lookup"><span data-stu-id="e5826-102">Custom Control Painting and Rendering</span></span>
<span data-ttu-id="e5826-103">Denetimlerin özel boyama .NET Framework tarafından kolay pek çok karmaşık görevlerden biridir.</span><span class="sxs-lookup"><span data-stu-id="e5826-103">Custom painting of controls is one of the many complicated tasks made easy by the .NET Framework.</span></span> <span data-ttu-id="e5826-104">Bir özel denetim yazarken denetiminizin grafik görünümü ile ilgili birçok seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="e5826-104">When authoring a custom control, you have many options regarding your control's graphical appearance.</span></span> <span data-ttu-id="e5826-105">Öğesinden devralan bir denetim yazıyorsanız `Control`, grafik gösterimi işlemek, denetim kodu sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="e5826-105">If you are authoring a control that inherits from the `Control`, you must provide code that allows your control to render its graphical representation.</span></span> <span data-ttu-id="e5826-106">İçinden devralma tarafından bir kullanıcı denetimi oluşturuyorsanız `UserControl`, veya devralan Windows Forms denetimleri her birinden, standart grafik gösterimi geçersiz kılabilir ya da kendi grafik kodunuzu girin.</span><span class="sxs-lookup"><span data-stu-id="e5826-106">If you are creating a user control by inheriting from the `UserControl`, or are inheriting from one of the Windows Forms controls, you may override the standard graphical representation and provide your own graphics code.</span></span> <span data-ttu-id="e5826-107">Özel işleme bağlı denetimler için sağlamak istiyorsanız bir `UserControl` geliştirmekte olduğunuz, seçeneklerinizi daha kısıtlı hale, ancak hala çok çeşitli grafik olasılıklarını denetimleri ve uygulamaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5826-107">If you want to provide custom rendering for the constituent controls of a `UserControl` you are authoring, your options become more limited, but still allow a wide range of graphical possibilities for your controls and applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e5826-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e5826-108">In This Section</span></span>  
 [<span data-ttu-id="e5826-109">Windows Forms Denetimini İşleme</span><span class="sxs-lookup"><span data-stu-id="e5826-109">Rendering a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 <span data-ttu-id="e5826-110">Bir denetim görüntüler mantığı program gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e5826-110">Shows how to program the logic that displays a control.</span></span>  
  
 [<span data-ttu-id="e5826-111">Kullanıcı Çizimli Denetimler</span><span class="sxs-lookup"><span data-stu-id="e5826-111">User-Drawn Controls</span></span>](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 <span data-ttu-id="e5826-112">Yazma ve işleme kodu denetlemek için geçersiz kılma adımlarını genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5826-112">Gives an overview of the steps involved in writing and overriding rendering code for your control.</span></span>  
  
 [<span data-ttu-id="e5826-113">Bağlı Denetimler</span><span class="sxs-lookup"><span data-stu-id="e5826-113">Constituent Controls</span></span>](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 <span data-ttu-id="e5826-114">Kullanıcı denetimleri ve formlarında bağlı denetimler için özel işleme kodu uygulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5826-114">Describes how to implement custom rendering code for constituent controls in your user controls and forms.</span></span>  
  
 [<span data-ttu-id="e5826-115">Nasıl yapılır: Çalışma Zamanında Denetiminizi Görünmez Yapma</span><span class="sxs-lookup"><span data-stu-id="e5826-115">How to: Make Your Control Invisible at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-make-your-control-invisible-at-run-time.md)  
 <span data-ttu-id="e5826-116">Nasıl kullanılacağını gösterir <xref:System.Windows.Forms.Control.Visible%2A> denetim gösterme ve gizleme için özellik.</span><span class="sxs-lookup"><span data-stu-id="e5826-116">Shows how to use the <xref:System.Windows.Forms.Control.Visible%2A> property to hide and show a control.</span></span>  
  
 [<span data-ttu-id="e5826-117">Nasıl yapılır: Denetiminize Saydam Arka Plan Verme</span><span class="sxs-lookup"><span data-stu-id="e5826-117">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 <span data-ttu-id="e5826-118">Nasıl kullanılacağını gösterir <xref:System.Windows.Forms.Control.SetStyle%2A> opak, saydam veya kısmen saydam arka plan rengi oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e5826-118">Shows how to use the <xref:System.Windows.Forms.Control.SetStyle%2A> method to create a background color that is opaque, transparent, or partially transparent.</span></span>  
  
 [<span data-ttu-id="e5826-119">Denetimleri Görsel Stilde İşleme</span><span class="sxs-lookup"><span data-stu-id="e5826-119">Rendering Controls with Visual Styles</span></span>](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 <span data-ttu-id="e5826-120">Görsel stiller işletim sistemlerinde desteklemek kullanarak denetimlerini işlemeye gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e5826-120">Shows how to render controls using visual styles in operating systems that support them.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e5826-121">Başvuru</span><span class="sxs-lookup"><span data-stu-id="e5826-121">Reference</span></span>  
 <xref:System.Windows.Forms.Control>  
 <span data-ttu-id="e5826-122">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="e5826-122">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="e5826-123">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="e5826-123">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <span data-ttu-id="e5826-124">Bu yöntem açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5826-124">Describes this method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e5826-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e5826-125">Related Sections</span></span>  
 [<span data-ttu-id="e5826-126">Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e5826-126">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 <span data-ttu-id="e5826-127">Tanıtır [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] daha fazla bilgi için Visual Studio Perspektif ve verir bağlantılardan grafik işlevselliği.</span><span class="sxs-lookup"><span data-stu-id="e5826-127">Introduces [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] graphics functionality from a Visual Studio perspective and gives links to more information.</span></span>  
  
 [<span data-ttu-id="e5826-128">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="e5826-128">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 <span data-ttu-id="e5826-129">Özel denetimler, yazabilirsiniz türlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5826-129">Describes the kinds of custom controls you can author.</span></span>
