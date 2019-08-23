---
title: ToolBar Denetimi (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
ms.openlocfilehash: 13a56af0e52897a6fd4e11516fbf4c0b8f6d6b5d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929560"
---
# <a name="toolbar-control-windows-forms"></a><span data-ttu-id="e3854-102">ToolBar Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e3854-102">ToolBar Control (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="e3854-103">Denetim yerini alır ve `ToolBar` `ToolBar` denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.ToolStrip></span><span class="sxs-lookup"><span data-stu-id="e3854-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the `ToolBar` control; however, the `ToolBar` control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="e3854-104">Windows Forms `ToolBar` denetimi, açılan menülerin ve komutları etkinleştirmek için bit eşlenmiş düğmelerin bir satırını görüntüleyen bir denetim çubuğu olarak formlarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e3854-104">The Windows Forms `ToolBar` control is used on forms as a control bar that displays a row of drop-down menus and bitmapped buttons that activate commands.</span></span> <span data-ttu-id="e3854-105">Bu nedenle, bir araç çubuğu düğmesine tıklamak, bir menü komutu seçmeye eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="e3854-105">Thus, clicking a toolbar button is equivalent to choosing a menu command.</span></span> <span data-ttu-id="e3854-106">Düğmeler görüntülenecek ve basma düğmeleri, açılan menüler veya ayırıcılar olarak davranacak şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e3854-106">The buttons can be configured to appear and behave as push buttons, drop-down menus, or separators.</span></span> <span data-ttu-id="e3854-107">Genellikle bir araç çubuğu, uygulamanın menü yapısındaki öğelere karşılık gelen düğme ve menüleri içerir ve uygulamanın en sık kullanılan işlevlerine ve komutlarına hızlı erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3854-107">Typically, a toolbar contains buttons and menus that correspond to items in an application's menu structure, providing quick access to an application's most frequently used functions and commands.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3854-108">Denetimin özelliği, bir başvuru olarak <xref:System.Windows.Forms.ContextMenu> sınıfının bir örneğini alır. <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> `ToolBar`</span><span class="sxs-lookup"><span data-stu-id="e3854-108">The `ToolBar` control's <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> property takes an instance of the <xref:System.Windows.Forms.ContextMenu> class as a reference.</span></span> <span data-ttu-id="e3854-109">Özelliği, <xref:System.Windows.Forms.Menu> sınıfından devralan herhangi bir nesneyi kabul edecek şekilde uygulamanızdaki araç çubuklarında bu sıralamayı uygularken geçirdiğiniz başvuruyu dikkatle düşünün.</span><span class="sxs-lookup"><span data-stu-id="e3854-109">Carefully consider the reference you pass when implementing this sort of button on toolbars in your application, as the property will accept any object that inherits from the <xref:System.Windows.Forms.Menu> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e3854-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e3854-110">In This Section</span></span>  
 [<span data-ttu-id="e3854-111">ToolBar Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e3854-111">ToolBar Control Overview</span></span>](toolbar-control-overview-windows-forms.md)  
 <span data-ttu-id="e3854-112">, Kullanıcılarınızın birlikte çalışabileceği özel `ToolBar` araç çubukları tasarlamanıza olanak sağlayan denetimin genel kavramlarını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="e3854-112">Introduces the general concepts of the `ToolBar` control, which allows you to design custom toolbars that your users can work with.</span></span>  
  
 [<span data-ttu-id="e3854-113">Nasıl yapılır: Araç çubuğu denetimine düğme ekleme</span><span class="sxs-lookup"><span data-stu-id="e3854-113">How to: Add Buttons to a ToolBar Control</span></span>](how-to-add-buttons-to-a-toolbar-control.md)  
 <span data-ttu-id="e3854-114">Bir `ToolBar` denetime düğmelerin nasıl ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e3854-114">Describes how to add buttons to a `ToolBar` control.</span></span>  
  
 [<span data-ttu-id="e3854-115">Nasıl yapılır: Bir araç çubuğu düğmesi için simge tanımlama</span><span class="sxs-lookup"><span data-stu-id="e3854-115">How to: Define an Icon for a ToolBar Button</span></span>](how-to-define-an-icon-for-a-toolbar-button.md)  
 <span data-ttu-id="e3854-116">Bir `ToolBar` denetimin düğmeleri içinde simgelerin nasıl görüntüleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e3854-116">Describes how to display icons within a `ToolBar` control's buttons.</span></span>  
  
 [<span data-ttu-id="e3854-117">Nasıl yapılır: Araç çubuğu düğmeleri için tetikleyici menü olayları</span><span class="sxs-lookup"><span data-stu-id="e3854-117">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)  
 <span data-ttu-id="e3854-118">Kullanıcının bir `ToolBar` denetimde tıkladığı düğmeyi yorumlamak için kod yazma yönergeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3854-118">Gives directions on writing code to interpret which button the user clicks in a `ToolBar` control.</span></span>  
  
 <span data-ttu-id="e3854-119">Ayrıca bkz [. nasıl yapılır: Tasarımcı](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md)kullanarak bir araç çubuğu düğmesi için simge tanımlayın, [nasıl yapılır: Tasarımcıyı](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md)kullanarak bir araç çubuğu denetimine düğme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e3854-119">Also see [How to: Define an Icon for a ToolBar Button Using the Designer](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [How to: Add Buttons to a ToolBar Control Using the Designer](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e3854-120">Başvuru</span><span class="sxs-lookup"><span data-stu-id="e3854-120">Reference</span></span>  
 <span data-ttu-id="e3854-121"><xref:System.Windows.Forms.ToolBar>sınıfı</span><span class="sxs-lookup"><span data-stu-id="e3854-121"><xref:System.Windows.Forms.ToolBar> class</span></span>  
 <span data-ttu-id="e3854-122">Sınıf ve üyeleri hakkında başvuru bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3854-122">Provides reference information on the class and its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e3854-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e3854-123">Related Sections</span></span>  
 [<span data-ttu-id="e3854-124">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="e3854-124">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="e3854-125">Windows Forms denetimlerinin tüm listesini, kullanımları hakkındaki bilgilerin bağlantılarıyla birlikte sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3854-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="e3854-126">ToolStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="e3854-126">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)  
 <span data-ttu-id="e3854-127">Windows Forms uygulamalarında menüleri, denetimleri ve kullanıcı denetimlerini barındırabilirler araç çubuklarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e3854-127">Describes toolbars that can host menus, controls, and user controls in Windows Forms applications.</span></span>
