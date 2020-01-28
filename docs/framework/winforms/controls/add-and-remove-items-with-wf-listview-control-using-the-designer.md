---
title: Tasarımcıyı kullanarak ListView denetimiyle öğe ekleme ve kaldırma
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: cab40c556d9e5d21ce15bcd3d4da367bc08f33ab
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732302"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="f8ed2-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları ListView Denetimi ile Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="f8ed2-102">How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="f8ed2-103">Bir Windows Forms <xref:System.Windows.Forms.ListView> denetimine öğe ekleme işlemi, öncelikle öğeyi belirtmesinin ve bu öğeye özellikler atamaktan oluşur.</span><span class="sxs-lookup"><span data-stu-id="f8ed2-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="f8ed2-104">Liste öğelerini ekleme veya kaldırma işlemi herhangi bir zamanda yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="f8ed2-104">Adding or removing list items can be done at any time.</span></span>

<span data-ttu-id="f8ed2-105">Aşağıdaki yordam, bir <xref:System.Windows.Forms.ListView> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f8ed2-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="f8ed2-106">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f8ed2-106">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-add-or-remove-items-using-the-designer"></a><span data-ttu-id="f8ed2-107">Tasarımcı kullanarak öğe eklemek veya kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="f8ed2-107">To add or remove items using the designer</span></span>

1. <span data-ttu-id="f8ed2-108"><xref:System.Windows.Forms.ListView> denetimini seçin.</span><span class="sxs-lookup"><span data-stu-id="f8ed2-108">Select the <xref:System.Windows.Forms.ListView> control.</span></span>

2. <span data-ttu-id="f8ed2-109">**Özellikler** penceresinde, <xref:System.Windows.Forms.ListView.Items%2A> özelliğinin yanındaki Visual Studio 'nun Özellikler penceresi](./media/visual-studio-ellipsis-button.png)) düğmesine **üç nokta**![(...) düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f8ed2-109">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>

     <span data-ttu-id="f8ed2-110">**ListViewItem koleksiyonu Düzenleyicisi** görünür.</span><span class="sxs-lookup"><span data-stu-id="f8ed2-110">The **ListViewItem Collection Editor** appears.</span></span>

3. <span data-ttu-id="f8ed2-111">Bir öğe eklemek için **Ekle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f8ed2-111">To add an item, click the **Add** button.</span></span> <span data-ttu-id="f8ed2-112">Daha sonra, <xref:System.Windows.Forms.ListView.Text%2A> ve <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> özellikleri gibi yeni öğenin özelliklerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8ed2-112">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListView.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>

4. <span data-ttu-id="f8ed2-113">Bir öğeyi kaldırmak için, seçin ve **Kaldır** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f8ed2-113">To remove an item, select it and click the **Remove** button.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8ed2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8ed2-114">See also</span></span>

- [<span data-ttu-id="f8ed2-115">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f8ed2-115">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="f8ed2-116">Nasıl yapılır: Windows Forms ListView Denetimine Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="f8ed2-116">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="f8ed2-117">Nasıl yapılır: Windows Forms ListView Denetimiyle Sütunlardaki Alt Öğeleri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="f8ed2-117">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="f8ed2-118">Nasıl yapılır: Windows Forms ListView Denetimi için Simgeler Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="f8ed2-118">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="f8ed2-119">Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="f8ed2-119">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [<span data-ttu-id="f8ed2-120">Nasıl yapılır: Windows Forms ListView Denetimindeki Öğeleri Gruplama</span><span class="sxs-lookup"><span data-stu-id="f8ed2-120">How to: Group Items in a Windows Forms ListView Control</span></span>](how-to-group-items-in-a-windows-forms-listview-control.md)
