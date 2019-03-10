---
title: ToolBar Denetimi (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
ms.openlocfilehash: 3f0a1b6a7f83753ccae1a129528ed320a2613122
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723054"
---
# <a name="toolbar-control-windows-forms"></a><span data-ttu-id="41b03-102">ToolBar Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="41b03-102">ToolBar Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="41b03-103"><xref:System.Windows.Forms.ToolStrip> Denetimi değiştirir ve işlevsellik ekler `ToolBar` denetler; ancak, `ToolBar` denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="41b03-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the `ToolBar` control; however, the `ToolBar` control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="41b03-104">Windows Forms `ToolBar` denetimi form üzerinde bir satır aşağı açılan menüler ve komutlar etkinleştirme bit eşlemli düğmeler görüntüleyen bir denetim çubuğu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="41b03-104">The Windows Forms `ToolBar` control is used on forms as a control bar that displays a row of drop-down menus and bitmapped buttons that activate commands.</span></span> <span data-ttu-id="41b03-105">Bu nedenle, bir araç çubuğu düğmesini tıklatarak bir menü komutu seçme eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="41b03-105">Thus, clicking a toolbar button is equivalent to choosing a menu command.</span></span> <span data-ttu-id="41b03-106">Düğmeler, görünür ve düğmeler, aşağı açılan menüler veya ayırıcı davranır şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="41b03-106">The buttons can be configured to appear and behave as push buttons, drop-down menus, or separators.</span></span> <span data-ttu-id="41b03-107">Genellikle, bir araç çubuğu düğmeleri ve bir uygulamanın en sık kullanılan işlevler ve komutlar için hızlı erişim sağlayan bir uygulama menüsü yapısı öğelere karşılık gelen menüleri içerir.</span><span class="sxs-lookup"><span data-stu-id="41b03-107">Typically, a toolbar contains buttons and menus that correspond to items in an application's menu structure, providing quick access to an application's most frequently used functions and commands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41b03-108">`ToolBar` Denetimin <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> özelliği bir örneğini alır <xref:System.Windows.Forms.ContextMenu> sınıfı başvuru olarak.</span><span class="sxs-lookup"><span data-stu-id="41b03-108">The `ToolBar` control's <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> property takes an instance of the <xref:System.Windows.Forms.ContextMenu> class as a reference.</span></span> <span data-ttu-id="41b03-109">Devralınan özelliği tüm nesne kabul gibi araç, uygulamanızda bu tür bir düğme uygulama, geçirdiğiniz başvuru dikkatlice <xref:System.Windows.Forms.Menu> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="41b03-109">Carefully consider the reference you pass when implementing this sort of button on toolbars in your application, as the property will accept any object that inherits from the <xref:System.Windows.Forms.Menu> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="41b03-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="41b03-110">In This Section</span></span>  
 [<span data-ttu-id="41b03-111">ToolBar Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="41b03-111">ToolBar Control Overview</span></span>](toolbar-control-overview-windows-forms.md)  
 <span data-ttu-id="41b03-112">Genel konseptlerini tanıtan `ToolBar` kullanıcılarınızın çalışabilirsiniz özel araç çubukları tasarım olanak tanıyan bir denetim.</span><span class="sxs-lookup"><span data-stu-id="41b03-112">Introduces the general concepts of the `ToolBar` control, which allows you to design custom toolbars that your users can work with.</span></span>  
  
 [<span data-ttu-id="41b03-113">Nasıl yapılır: Bir ToolBar denetimine düğme ekleme</span><span class="sxs-lookup"><span data-stu-id="41b03-113">How to: Add Buttons to a ToolBar Control</span></span>](how-to-add-buttons-to-a-toolbar-control.md)  
 <span data-ttu-id="41b03-114">Düğmelere eklemeyi açıklar bir `ToolBar` denetimi.</span><span class="sxs-lookup"><span data-stu-id="41b03-114">Describes how to add buttons to a `ToolBar` control.</span></span>  
  
 [<span data-ttu-id="41b03-115">Nasıl yapılır: ToolBar düğmesi için simge tanımlama</span><span class="sxs-lookup"><span data-stu-id="41b03-115">How to: Define an Icon for a ToolBar Button</span></span>](how-to-define-an-icon-for-a-toolbar-button.md)  
 <span data-ttu-id="41b03-116">İçinde simge görüntülenecek açıklar bir `ToolBar` denetim düğmelerinin.</span><span class="sxs-lookup"><span data-stu-id="41b03-116">Describes how to display icons within a `ToolBar` control's buttons.</span></span>  
  
 [<span data-ttu-id="41b03-117">Nasıl yapılır: Araç çubuğu düğmeleri için menü olaylarını tetikleme</span><span class="sxs-lookup"><span data-stu-id="41b03-117">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)  
 <span data-ttu-id="41b03-118">Hangi kullanıcı düğmesi yorumlamak için kod yazma verir yönergeleri tıkladığında içinde bir `ToolBar` denetimi.</span><span class="sxs-lookup"><span data-stu-id="41b03-118">Gives directions on writing code to interpret which button the user clicks in a `ToolBar` control.</span></span>  
  
 <span data-ttu-id="41b03-119">Ayrıca bkz: [nasıl yapılır: Tasarımcı kullanarak ToolBar düğmesi için simge tanımlama](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [nasıl yapılır: Tasarımcı kullanarak bir ToolBar denetimine düğme ekleme](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="41b03-119">Also see [How to: Define an Icon for a ToolBar Button Using the Designer](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [How to: Add Buttons to a ToolBar Control Using the Designer](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="41b03-120">Başvuru</span><span class="sxs-lookup"><span data-stu-id="41b03-120">Reference</span></span>  
 <span data-ttu-id="41b03-121"><xref:System.Windows.Forms.ToolBar> Sınıfı</span><span class="sxs-lookup"><span data-stu-id="41b03-121"><xref:System.Windows.Forms.ToolBar> class</span></span>  
 <span data-ttu-id="41b03-122">Sınıf ve onun üyeleri hakkında başvuru bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="41b03-122">Provides reference information on the class and its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="41b03-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="41b03-123">Related Sections</span></span>  
 [<span data-ttu-id="41b03-124">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="41b03-124">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="41b03-125">Windows Forms denetimlerini, tam bir listesi, kullanımları hakkında bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="41b03-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="41b03-126">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="41b03-126">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)  
 <span data-ttu-id="41b03-127">Menüleri, Denetim ve Windows Forms uygulamalarında kullanıcı denetimleri barındırabilir araç çubukları açıklar.</span><span class="sxs-lookup"><span data-stu-id="41b03-127">Describes toolbars that can host menus, controls, and user controls in Windows Forms applications.</span></span>
