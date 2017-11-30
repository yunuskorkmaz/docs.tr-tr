---
title: ToolBar Denetimi (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18fc87d4ebccd101bec47abd39805746d0b9ef81
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="toolbar-control-windows-forms"></a><span data-ttu-id="ce83f-102">ToolBar Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ce83f-102">ToolBar Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="ce83f-103"><xref:System.Windows.Forms.ToolStrip> Denetimi değiştirir ve işlevlerini ekler `ToolBar` kontrol; ancak, `ToolBar` denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="ce83f-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the `ToolBar` control; however, the `ToolBar` control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="ce83f-104">Windows Forms `ToolBar` denetimi formlarında bir satır aşağı açılan menüler ve komutları etkinleştirmek eşlemli düğmelerinin görüntüleyen bir denetim çubuğu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ce83f-104">The Windows Forms `ToolBar` control is used on forms as a control bar that displays a row of drop-down menus and bitmapped buttons that activate commands.</span></span> <span data-ttu-id="ce83f-105">Bu nedenle, bir araç çubuğu düğmesini tıklatarak menü komutu seçme eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="ce83f-105">Thus, clicking a toolbar button is equivalent to choosing a menu command.</span></span> <span data-ttu-id="ce83f-106">Düğmeleri görünür ve düğmeler, aşağı açılan menüler veya ayırıcı hareket etmesi için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="ce83f-106">The buttons can be configured to appear and behave as push buttons, drop-down menus, or separators.</span></span> <span data-ttu-id="ce83f-107">Genellikle, bir araç çubuğu düğmeleri ve bir uygulamanın en sık kullanılan işlevler ve komutları hızlı erişim sağlayan bir uygulamanın menü yapısı öğelere karşılık gelen menüleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ce83f-107">Typically, a toolbar contains buttons and menus that correspond to items in an application's menu structure, providing quick access to an application's most frequently used functions and commands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce83f-108">`ToolBar` Denetimin <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> özelliği alır örneği <xref:System.Windows.Forms.ContextMenu> sınıfı bir başvuru olarak.</span><span class="sxs-lookup"><span data-stu-id="ce83f-108">The `ToolBar` control's <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> property takes an instance of the <xref:System.Windows.Forms.ContextMenu> class as a reference.</span></span> <span data-ttu-id="ce83f-109">Özellik, herhangi bir nesne kabul edecek şekilde bu tür bir düğme, uygulamanızda çubuklarında uygulama devraldığı geçirdiğiniz başvuru dikkatlice <xref:System.Windows.Forms.Menu> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ce83f-109">Carefully consider the reference you pass when implementing this sort of button on toolbars in your application, as the property will accept any object that inherits from the <xref:System.Windows.Forms.Menu> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ce83f-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ce83f-110">In This Section</span></span>  
 [<span data-ttu-id="ce83f-111">ToolBar denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="ce83f-111">ToolBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 <span data-ttu-id="ce83f-112">Genel kavramlarını tanıtır `ToolBar` kullanıcılarınızın çalışabilirsiniz özel araç çubukları tasarım sayesinde denetim.</span><span class="sxs-lookup"><span data-stu-id="ce83f-112">Introduces the general concepts of the `ToolBar` control, which allows you to design custom toolbars that your users can work with.</span></span>  
  
 [<span data-ttu-id="ce83f-113">Nasıl yapılır: bir ToolBar denetimine düğme ekleme</span><span class="sxs-lookup"><span data-stu-id="ce83f-113">How to: Add Buttons to a ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)  
 <span data-ttu-id="ce83f-114">Düğmelere eklemeyi açıklar bir `ToolBar` denetim.</span><span class="sxs-lookup"><span data-stu-id="ce83f-114">Describes how to add buttons to a `ToolBar` control.</span></span>  
  
 [<span data-ttu-id="ce83f-115">Nasıl yapılır: ToolBar düğmesi için simge tanımlama</span><span class="sxs-lookup"><span data-stu-id="ce83f-115">How to: Define an Icon for a ToolBar Button</span></span>](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 <span data-ttu-id="ce83f-116">İçinde simge görüntülenecek açıklar bir `ToolBar` denetimin düğmeler.</span><span class="sxs-lookup"><span data-stu-id="ce83f-116">Describes how to display icons within a `ToolBar` control's buttons.</span></span>  
  
 [<span data-ttu-id="ce83f-117">Nasıl yapılır: araç çubuğu düğmeleri için menü olaylarını tetikleme</span><span class="sxs-lookup"><span data-stu-id="ce83f-117">How to: Trigger Menu Events for Toolbar Buttons</span></span>](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 <span data-ttu-id="ce83f-118">Hangi kullanıcı düğmesini yorumlamak için kod yazma verir yönergeleri tıklattığında bir `ToolBar` denetim.</span><span class="sxs-lookup"><span data-stu-id="ce83f-118">Gives directions on writing code to interpret which button the user clicks in a `ToolBar` control.</span></span>  
  
 <span data-ttu-id="ce83f-119">Ayrıca bkz. [nasıl yapılır: bir araç çubuğu düğmesini kullanarak için tasarımcı simge tanımlama](http://msdn.microsoft.com/library/ms233659\(v=vs.110\)), [nasıl yapılır: araç çubuğu denetimi kullanarak bir tasarımcı eklemek düğmelere](http://msdn.microsoft.com/library/ms233650\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="ce83f-119">Also see [How to: Define an Icon for a ToolBar Button Using the Designer](http://msdn.microsoft.com/library/ms233659\(v=vs.110\)), [How to: Add Buttons to a ToolBar Control Using the Designer](http://msdn.microsoft.com/library/ms233650\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ce83f-120">Başvuru</span><span class="sxs-lookup"><span data-stu-id="ce83f-120">Reference</span></span>  
 <span data-ttu-id="ce83f-121"><xref:System.Windows.Forms.ToolBar>sınıfı</span><span class="sxs-lookup"><span data-stu-id="ce83f-121"><xref:System.Windows.Forms.ToolBar> class</span></span>  
 <span data-ttu-id="ce83f-122">Sınıf ve üyelerine başvuru bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce83f-122">Provides reference information on the class and its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ce83f-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ce83f-123">Related Sections</span></span>  
 [<span data-ttu-id="ce83f-124">Windows Forms'ta kullanılacak denetimler</span><span class="sxs-lookup"><span data-stu-id="ce83f-124">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="ce83f-125">Windows Forms denetimleri, tam bir listesi ile bunların kullanılması hakkında bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce83f-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="ce83f-126">ToolStrip denetimi</span><span class="sxs-lookup"><span data-stu-id="ce83f-126">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 <span data-ttu-id="ce83f-127">Menüleri, Denetim ve Windows Forms uygulamalarında kullanıcı denetimleri barındırabilir araç çubukları açıklar.</span><span class="sxs-lookup"><span data-stu-id="ce83f-127">Describes toolbars that can host menus, controls, and user controls in Windows Forms applications.</span></span>
