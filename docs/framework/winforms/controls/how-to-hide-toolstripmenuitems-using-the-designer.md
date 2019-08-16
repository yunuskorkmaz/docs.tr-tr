---
title: 'Nasıl yapılır: Tasarımcıyı Kullanarak ToolStripMenuItems’ı Gizleme'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: 968d34a5f79d469ef62beaa8ac96742d73391b22
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039753"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="e20d6-102">Nasıl yapılır: Tasarımcıyı Kullanarak ToolStripMenuItems’ı Gizleme</span><span class="sxs-lookup"><span data-stu-id="e20d6-102">How to: Hide ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="e20d6-103">Menü öğelerini gizlemek, uygulamanızın kullanıcı arabirimini (UI) denetlemek ve Kullanıcı komutlarını kısıtlamak için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="e20d6-103">Hiding menu items is a way to control the user interface (UI) of your application and restrict user commands.</span></span> <span data-ttu-id="e20d6-104">Genellikle, üzerindeki tüm menü öğeleri kullanılamadığında, tüm menüyü gizlemek isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="e20d6-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="e20d6-105">Bu, Kullanıcı için daha az ayırt eden olanaklar sunar.</span><span class="sxs-lookup"><span data-stu-id="e20d6-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="e20d6-106">Ayrıca, menüyü veya menü öğesini de gizlemek ve devre dışı bırakmak isteyebilirsiniz, tek başına gizleme, kullanıcının bir kısayol tuşu kullanarak bir menü komutuna erişmesini engellemez.</span><span class="sxs-lookup"><span data-stu-id="e20d6-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span> <span data-ttu-id="e20d6-107">Menü öğelerini devre dışı bırakma hakkında daha fazla bilgi [için bkz. nasıl yapılır: Tasarımcıyı](how-to-disable-toolstripmenuitems-using-the-designer.md)kullanarak ToolStripMenuItems 'ı devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="e20d6-107">For more information on disabling menu items, see [How to: Disable ToolStripMenuItems Using the Designer](how-to-disable-toolstripmenuitems-using-the-designer.md).</span></span>

## <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a><span data-ttu-id="e20d6-108">Üst düzey menüyü ve alt menü öğelerini gizlemek için</span><span class="sxs-lookup"><span data-stu-id="e20d6-108">To hide a top-level menu and its submenu items</span></span>

1. <span data-ttu-id="e20d6-109">Üst düzey menü öğesini seçin ve <xref:System.Windows.Forms.ToolStripItem.Visible%2A> veya <xref:System.Windows.Forms.ToolStripItem.Available%2A> özelliğini olarak `false`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e20d6-109">Select the top-level menu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> or <xref:System.Windows.Forms.ToolStripItem.Available%2A> property to `false`.</span></span>

     <span data-ttu-id="e20d6-110">Üst düzey menü öğesini gizlediğinizde, bu menüdeki tüm menü öğeleri de gizlenir.</span><span class="sxs-lookup"><span data-stu-id="e20d6-110">When you hide the top-level menu item, all menu items within that menu are also hidden.</span></span> <span data-ttu-id="e20d6-111">' Den <xref:System.Windows.Forms.MenuStrip> `false`sonra ' i ' den sonra biryeretıkladığınızda,enüstdüzeymenüöğesivealtmenüöğeleriformdankaybolurvebusayedeeyleminiziçinçalışmazamanıetkisinigösterir.<xref:System.Windows.Forms.ToolStripItem.Visible%2A></span><span class="sxs-lookup"><span data-stu-id="e20d6-111">If you click somewhere other than on the <xref:System.Windows.Forms.MenuStrip> after setting <xref:System.Windows.Forms.ToolStripItem.Visible%2A> to `false`, the entire top-level menu item and its submenu items disappear from your form, thus showing you the run-time effect of your action.</span></span> <span data-ttu-id="e20d6-112">Gizli üst düzey menü öğesini tasarım zamanında göstermek için **bileşen tepsisinde**, **belge anahattından**veya <xref:System.Windows.Forms.MenuStrip> Özellik kılavuzunun en üstünde bulunan öğesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e20d6-112">To display the hidden top-level menu item at design time, click on the <xref:System.Windows.Forms.MenuStrip> in the **Component Tray**, in **Document Outline**, or at the top of the property grid.</span></span>

> [!NOTE]
>  <span data-ttu-id="e20d6-113">Birleştirme senaryosunda birden çok belge arabirimi (MDI) alt menüleri hariç, tüm menüyü nadiren gizlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e20d6-113">You will rarely hide an entire menu except for multiple document interface (MDI) child menus in a merging scenario.</span></span>

## <a name="to-hide-a-submenu-item"></a><span data-ttu-id="e20d6-114">Bir alt menü öğesini gizlemek için</span><span class="sxs-lookup"><span data-stu-id="e20d6-114">To hide a submenu item</span></span>

1. <span data-ttu-id="e20d6-115">Alt menü öğesini seçin ve <xref:System.Windows.Forms.ToolStripItem.Visible%2A> özelliğini olarak `false`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e20d6-115">Select the submenu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>

     <span data-ttu-id="e20d6-116">Bir alt menü öğesini gizlediğinizde, tasarım zamanında formunuzda görünür kalır, böylece daha fazla iş için kolayca seçim yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e20d6-116">When you hide a submenu item, it remains visible on your form at design time so that you can easily select it for further work.</span></span> <span data-ttu-id="e20d6-117">Çalışma zamanında gizli olmayacak.</span><span class="sxs-lookup"><span data-stu-id="e20d6-117">It will actually be hidden at run time.</span></span>

## <a name="see-also"></a><span data-ttu-id="e20d6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e20d6-118">See also</span></span>

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>
- <xref:System.Windows.Forms.ToolStripItem.Available%2A>
- <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>
- [<span data-ttu-id="e20d6-119">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e20d6-119">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
- [<span data-ttu-id="e20d6-120">Nasıl yapılır: Tasarımcıyı kullanarak ToolStripMenuItems 'ı devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="e20d6-120">How to: Disable ToolStripMenuItems Using the Designer</span></span>](how-to-disable-toolstripmenuitems-using-the-designer.md)
