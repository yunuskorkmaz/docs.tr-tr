---
title: 'Nasıl yapılır: Tasarımcıyı Kullanarak ToolStripMenuItems’ı Devre Dışı Bırakma'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: 692b6c11f6d58c52a0af29ed04ada45c48cae058
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046233"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="b9bc2-102">Nasıl yapılır: Tasarımcıyı Kullanarak ToolStripMenuItems’ı Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="b9bc2-102">How to: Disable ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="b9bc2-103">Kullanıcı etkinliklerine yanıt olarak menü öğelerini etkinleştirip devre dışı bırakarak bir kullanıcının yapabiliriz olan komutları sınırlayabilirsiniz veya genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9bc2-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="b9bc2-104">Menü öğeleri oluşturulduklarında varsayılan olarak etkindir, ancak bu <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özellik aracılığıyla ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="b9bc2-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="b9bc2-105">Bu özelliği tasarım zamanında **Özellikler** penceresinde veya program aracılığıyla kod içinde ayarlayarak düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9bc2-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span> <span data-ttu-id="b9bc2-106">Daha fazla bilgi için [nasıl yapılır: ToolStripMenuItems](how-to-disable-toolstripmenuitems.md)'ı devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="b9bc2-106">For more information, see [How to: Disable ToolStripMenuItems](how-to-disable-toolstripmenuitems.md).</span></span>

## <a name="to-disable-a-menu-item-at-design-time"></a><span data-ttu-id="b9bc2-107">Tasarım zamanında bir menü öğesini devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="b9bc2-107">To disable a menu item at design time</span></span>

1. <span data-ttu-id="b9bc2-108">Formda menü öğesi seçiliyken, <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliğini olarak `false`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b9bc2-108">With the menu item selected on the form, set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>

    > [!TIP]
    > <span data-ttu-id="b9bc2-109">Bir menüdeki ilk veya üst düzey menü öğesini devre dışı bırakmak, menüde bulunan tüm menü öğelerini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="b9bc2-109">Disabling the first or top-level menu item in a menu disables all the menu items contained within the menu.</span></span> <span data-ttu-id="b9bc2-110">Benzer şekilde, alt menü öğelerinin bulunduğu bir menü öğesini devre dışı bırakmak alt menü öğelerini devre dışı bırakır</span><span class="sxs-lookup"><span data-stu-id="b9bc2-110">Likewise, disabling a menu item that has submenu items disables the submenu items.</span></span> <span data-ttu-id="b9bc2-111">Belirli bir menüdeki tüm komutlar Kullanıcı için kullanılabilir durumda değilse, tüm menüyü gizleme ve devre dışı bırakma, bu da temiz bir kullanıcı arabirimi sunan için iyi bir programlama uygulaması kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="b9bc2-111">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="b9bc2-112">Yalnızca gizleme menü komutuna kısayol tuşu aracılığıyla erişimi önlememek üzere menüyü gizlemeniz ve devre dışı bırakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b9bc2-112">You should both hide and disable the menu, as hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="b9bc2-113">Tüm menüyü gizlemek için üst düzey menü öğesinin `false` özelliğiniolarakayarlayın.<xref:System.Windows.Forms.ToolStripItem.Visible%2A></span><span class="sxs-lookup"><span data-stu-id="b9bc2-113">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9bc2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9bc2-114">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="b9bc2-115">Nasıl yapılır: ToolStripMenuItems 'ı gizle</span><span class="sxs-lookup"><span data-stu-id="b9bc2-115">How to: Hide ToolStripMenuItems</span></span>](how-to-hide-toolstripmenuitems.md)
- [<span data-ttu-id="b9bc2-116">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b9bc2-116">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
