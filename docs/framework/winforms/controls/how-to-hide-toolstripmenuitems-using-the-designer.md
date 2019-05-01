---
title: 'Nasıl yapılır: Tasarımcıyı Kullanarak ToolStripMenuItems’ı Gizleme'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: 31c597a0e2cbf41484f19c8d4179823e9fb929ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941212"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="d37ec-102">Nasıl yapılır: Tasarımcıyı Kullanarak ToolStripMenuItems’ı Gizleme</span><span class="sxs-lookup"><span data-stu-id="d37ec-102">How to: Hide ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="d37ec-103">Menü öğelerini gizleme, uygulamanızın kullanıcı arabirimini (UI) denetlemek ve kullanıcı komutları kısıtlamak için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="d37ec-103">Hiding menu items is a way to control the user interface (UI) of your application and restrict user commands.</span></span> <span data-ttu-id="d37ec-104">Genellikle, tüm menü öğeleri kullanılamadığında bir tüm menüyü Gizle isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="d37ec-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="d37ec-105">Bu kullanıcı için daha az dikkat dağıtıcı faktör sunar.</span><span class="sxs-lookup"><span data-stu-id="d37ec-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="d37ec-106">Ayrıca, tek başına bir gizleme kullanıcı bir menü komutu bir kısayol tuşu kullanarak erişmesini önlemez gibi hem gizleyebilir ve menü veya menü öğesi devre dışı bırakmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d37ec-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span> <span data-ttu-id="d37ec-107">Menü öğelerini devre dışı bırakma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Tasarımcıyı kullanarak toolstripmenuıtems öğelerini devre dışı](how-to-disable-toolstripmenuitems-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="d37ec-107">For more information on disabling menu items, see [How to: Disable ToolStripMenuItems Using the Designer](how-to-disable-toolstripmenuitems-using-the-designer.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d37ec-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="d37ec-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d37ec-109">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="d37ec-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d37ec-110">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="d37ec-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a><span data-ttu-id="d37ec-111">Üst düzey menü ve onun alt öğelerini gizlemek için</span><span class="sxs-lookup"><span data-stu-id="d37ec-111">To hide a top-level menu and its submenu items</span></span>  
  
1. <span data-ttu-id="d37ec-112">Üst düzey menü öğesini seçin ve ayarlayın, <xref:System.Windows.Forms.ToolStripItem.Visible%2A> veya <xref:System.Windows.Forms.ToolStripItem.Available%2A> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="d37ec-112">Select the top-level menu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> or <xref:System.Windows.Forms.ToolStripItem.Available%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="d37ec-113">Üst düzey menü öğesi gizlediğinizde, menünün içinde tüm menü öğelerini de gizlenir.</span><span class="sxs-lookup"><span data-stu-id="d37ec-113">When you hide the top-level menu item, all menu items within that menu are also hidden.</span></span> <span data-ttu-id="d37ec-114">Dışındaki bir üzerinde tıklarsanız <xref:System.Windows.Forms.MenuStrip> ayarlanmasından sonra <xref:System.Windows.Forms.ToolStripItem.Visible%2A> için `false`, tüm üst düzey menü öğesi ve onun alt öğelerini, böylece sizin eyleminizi çalışma zamanı etkisini gösteren formunuzun içinden kaybolur.</span><span class="sxs-lookup"><span data-stu-id="d37ec-114">If you click somewhere other than on the <xref:System.Windows.Forms.MenuStrip> after setting <xref:System.Windows.Forms.ToolStripItem.Visible%2A> to `false`, the entire top-level menu item and its submenu items disappear from your form, thus showing you the run-time effect of your action.</span></span> <span data-ttu-id="d37ec-115">Tasarım zamanında gizli en üst düzey menü öğesi görüntülemek için tıklayın <xref:System.Windows.Forms.MenuStrip> içinde **bileşeni Tepsi**, **belge anahattı**, ya da özellik kılavuzunda üstünde.</span><span class="sxs-lookup"><span data-stu-id="d37ec-115">To display the hidden top-level menu item at design time, click on the <xref:System.Windows.Forms.MenuStrip> in the **Component Tray**, in **Document Outline**, or at the top of the property grid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d37ec-116">Birden çok belge arabirimi (MDI) alt menülerini birleştirme senaryosunda hariç tüm bir menü nadiren gizlenir.</span><span class="sxs-lookup"><span data-stu-id="d37ec-116">You will rarely hide an entire menu except for multiple document interface (MDI) child menus in a merging scenario.</span></span>  
  
### <a name="to-hide-a-submenu-item"></a><span data-ttu-id="d37ec-117">Bir alt öğesini gizlemek için</span><span class="sxs-lookup"><span data-stu-id="d37ec-117">To hide a submenu item</span></span>  
  
1. <span data-ttu-id="d37ec-118">Alt menü öğesini seçin ve ayarlayın, <xref:System.Windows.Forms.ToolStripItem.Visible%2A> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="d37ec-118">Select the submenu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="d37ec-119">Bir alt öğesi gizlediğinizde, böylece bunu kolayca için daha fazla iş seçebilirsiniz tasarım zamanında formunuzda görünür kalır.</span><span class="sxs-lookup"><span data-stu-id="d37ec-119">When you hide a submenu item, it remains visible on your form at design time so that you can easily select it for further work.</span></span> <span data-ttu-id="d37ec-120">Çalışma zamanında gerçekten gizlenir.</span><span class="sxs-lookup"><span data-stu-id="d37ec-120">It will actually be hidden at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d37ec-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d37ec-121">See also</span></span>

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>
- <xref:System.Windows.Forms.ToolStripItem.Available%2A>
- <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>
- [<span data-ttu-id="d37ec-122">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d37ec-122">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
- [<span data-ttu-id="d37ec-123">Nasıl yapılır: Tasarımcıyı kullanarak toolstripmenuıtems öğelerini devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="d37ec-123">How to: Disable ToolStripMenuItems Using the Designer</span></span>](how-to-disable-toolstripmenuitems-using-the-designer.md)
