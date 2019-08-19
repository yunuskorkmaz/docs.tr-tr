---
title: 'Nasıl yapılır: ToolStripMenuItems Öğelerini Taşıma'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], moving
- menus [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], dragging and dropping
- menu items [Windows Forms], moving
- menu items [Windows Forms], cutting and pasting
- menu items [Windows Forms], dragging and dropping
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], cutting and pasting
ms.assetid: cab9e03e-4edd-4c25-b3e3-bd1edc602bd9
ms.openlocfilehash: adf25973fde790937461007bd0106cca02dd83be
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039803"
---
# <a name="how-to-move-toolstripmenuitems"></a><span data-ttu-id="7dd8f-102">Nasıl yapılır: ToolStripMenuItems Öğelerini Taşıma</span><span class="sxs-lookup"><span data-stu-id="7dd8f-102">How to: Move ToolStripMenuItems</span></span>
<span data-ttu-id="7dd8f-103">Tasarım zamanında, en üst düzey menülerin ve menü öğelerinin tamamını üzerinde <xref:System.Windows.Forms.MenuStrip>farklı bir yere taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7dd8f-103">At design time, you can move entire top-level menus and their menu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="7dd8f-104">Ayrıca, ayrı menü öğelerini üst düzey menüler arasında taşıyabilir veya menüdeki menü öğelerinin konumunu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7dd8f-104">You can also move individual menu items between top-level menus or change the position of menu items within a menu.</span></span>

## <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a><span data-ttu-id="7dd8f-105">Üst düzey menüyü ve menü öğelerini başka bir üst düzey konuma taşımak için</span><span class="sxs-lookup"><span data-stu-id="7dd8f-105">To move a top-level menu and its menu items to another top-level location</span></span>

1. <span data-ttu-id="7dd8f-106">Taşımak istediğiniz menüdeki sol fare düğmesine tıklayın ve basılı tutun.</span><span class="sxs-lookup"><span data-stu-id="7dd8f-106">Click and hold down the left mouse button on the menu that you want to move.</span></span>

2. <span data-ttu-id="7dd8f-107">Ekleme noktasını amaçlanan yeni konumdan önce olan en üst düzey menüye sürükleyin ve sol fare düğmesini bırakın.</span><span class="sxs-lookup"><span data-stu-id="7dd8f-107">Drag the insertion point to the top-level menu that is before the intended new location and release the left mouse button.</span></span>

     <span data-ttu-id="7dd8f-108">Seçilen menü, ekleme noktasının sağına gider.</span><span class="sxs-lookup"><span data-stu-id="7dd8f-108">The selected menu moves to the right of the insertion point.</span></span>

## <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a><span data-ttu-id="7dd8f-109">Üst düzey menüyü ve menü öğelerini açılan bir konuma taşımak için</span><span class="sxs-lookup"><span data-stu-id="7dd8f-109">To move a top-level menu and its menu items to a drop-down location</span></span>

1. <span data-ttu-id="7dd8f-110">Taşımak istediğiniz menüye sol tıklayın ve CTRL + X tuşlarına basın ya da menüye sağ tıklayıp kısayol menüsünden **Kes** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="7dd8f-110">Left-click the menu that you want to move and press CTRL+X, or right-click the menu and select **Cut** from the shortcut menu.</span></span>

2. <span data-ttu-id="7dd8f-111">Hedef üst düzey menüsünde, hedeflenen yeni konumun üzerindeki menü öğesine sağ tıklayın ve CTRL + V tuşlarına basın veya hedeflenen yeni konumun üzerindeki menü öğesine sağ tıklayıp kısayol menüsünden **Yapıştır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="7dd8f-111">In the destination top-level menu, left-click the menu item above the intended new location and press CTRL+V, or right-click the menu item above the intended new location and select **Paste** from the shortcut menu.</span></span>

     <span data-ttu-id="7dd8f-112">Kestiğiniz menü, seçilen menü öğesinden sonra eklenir.</span><span class="sxs-lookup"><span data-stu-id="7dd8f-112">The menu that you cut is inserted after the selected menu item.</span></span>

## <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a><span data-ttu-id="7dd8f-113">Öğeler koleksiyonu düzenleyicisini kullanarak bir menü öğesini bir menü içinde taşımak için</span><span class="sxs-lookup"><span data-stu-id="7dd8f-113">To move a menu item within a menu using the Items Collection Editor</span></span>

1. <span data-ttu-id="7dd8f-114">Taşımak istediğiniz menü öğesini içeren menüyü sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7dd8f-114">Right-click the menu that contains the menu item you want to move.</span></span>

2. <span data-ttu-id="7dd8f-115">Kısayol menüsünde **DropDownItems Düzenle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7dd8f-115">From the shortcut menu, choose **Edit DropDownItems**.</span></span>

3. <span data-ttu-id="7dd8f-116">**Öğe koleksiyonu düzenleyicisinde**, taşımak istediğiniz menü öğesine sol tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7dd8f-116">In the **Items Collection Editor**, left-click the menu item you want to move.</span></span>

4. <span data-ttu-id="7dd8f-117">Menüdeki menü öğesini taşımak için yukarı ve aşağı ok tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="7dd8f-117">Click the UP and DOWN ARROW keys to move the menu item within the menu.</span></span>

5. <span data-ttu-id="7dd8f-118">          **Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="7dd8f-118">Click **OK**.</span></span>

## <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a><span data-ttu-id="7dd8f-119">Bir menü öğesini klavyeyi kullanarak bir menü içinde taşımak için</span><span class="sxs-lookup"><span data-stu-id="7dd8f-119">To move a menu item within a menu using the keyboard</span></span>

1. <span data-ttu-id="7dd8f-120">ALT tuşuna basın ve basılı tutun.</span><span class="sxs-lookup"><span data-stu-id="7dd8f-120">Press and hold down the ALT key.</span></span>

2. <span data-ttu-id="7dd8f-121">Taşımak istediğiniz menü öğesindeki sol fare düğmesine tıklayın ve basılı tutun.</span><span class="sxs-lookup"><span data-stu-id="7dd8f-121">Click and hold the left mouse button on the menu item that you want to move.</span></span>

3. <span data-ttu-id="7dd8f-122">Menü öğesini yeni konuma sürükleyin ve sol fare düğmesini bırakın.</span><span class="sxs-lookup"><span data-stu-id="7dd8f-122">Drag the menu item to the new location and release the left mouse button.</span></span>

## <a name="to-move-a-menu-item-to-another-menu"></a><span data-ttu-id="7dd8f-123">Bir menü öğesini başka bir menüye taşımak için</span><span class="sxs-lookup"><span data-stu-id="7dd8f-123">To move a menu item to another menu</span></span>

1. <span data-ttu-id="7dd8f-124">Taşımak istediğiniz menü öğesini sol tıklatın ve CTRL + X tuşlarına basın veya menü öğesine sağ tıklayıp kısayol menüsünden **Kes** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="7dd8f-124">Left-click the menu item that you want to move and press CTRL+X, or right-click the menu item and choose **Cut** from the shortcut menu.</span></span>

2. <span data-ttu-id="7dd8f-125">Kestiğiniz menü öğesini içerecek menüye sol tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7dd8f-125">Left-click the menu that will contain the menu item that you cut.</span></span>

3. <span data-ttu-id="7dd8f-126">Hedeflenen yeni konumdan önceki menü öğesine sağ tıklayın ve CTRL + V tuşlarına basın veya amaçlanan yeni konumdan önce gelen menü öğesine sağ tıklayıp kısayol menüsünden **Yapıştır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="7dd8f-126">Left-click the menu item that is before the intended new location and press CTRL+V, or right-click the menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>

     <span data-ttu-id="7dd8f-127">Kestiğiniz menü öğesi seçili menü öğesinden sonra eklenir.</span><span class="sxs-lookup"><span data-stu-id="7dd8f-127">The menu item that you cut is inserted after the selected menu item.</span></span>

## <a name="see-also"></a><span data-ttu-id="7dd8f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7dd8f-128">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="7dd8f-129">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7dd8f-129">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
