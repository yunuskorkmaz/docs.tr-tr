---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 62665746ea9fcd1553717b02b1f1349dc6415ab2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040081"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="74d5f-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="74d5f-102">How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="74d5f-103">Bir Windows Forms <xref:System.Windows.Forms.ListView> denetimine öğe ekleme işlemi, öncelikle öğeyi belirtmektir ve bu öğeye özellikler atamaktan oluşur.</span><span class="sxs-lookup"><span data-stu-id="74d5f-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="74d5f-104">Liste öğelerini ekleme veya kaldırma işlemi herhangi bir zamanda yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="74d5f-104">Adding or removing list items can be done at any time.</span></span>

<span data-ttu-id="74d5f-105">Aşağıdaki yordam, bir <xref:System.Windows.Forms.ListView> denetim içeren bir form ile **Windows uygulama** projesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="74d5f-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="74d5f-106">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="74d5f-106">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-add-or-remove-items-using-the-designer"></a><span data-ttu-id="74d5f-107">Tasarımcı kullanarak öğe eklemek veya kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="74d5f-107">To add or remove items using the designer</span></span>

1. <span data-ttu-id="74d5f-108"><xref:System.Windows.Forms.ListView> Denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="74d5f-108">Select the <xref:System.Windows.Forms.ListView> control.</span></span>

2. <span data-ttu-id="74d5f-109">**Özellikler** penceresinde,![ özelliğin<xref:System.Windows.Forms.ListView.Items%2A> yanındaki Visual Studio](./media/visual-studio-ellipsis-button.png)'nun Özellikler penceresi (...) üç nokta (...) düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74d5f-109">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>

     <span data-ttu-id="74d5f-110">**ListViewItem koleksiyonu Düzenleyicisi** görünür.</span><span class="sxs-lookup"><span data-stu-id="74d5f-110">The **ListViewItem Collection Editor** appears.</span></span>

3. <span data-ttu-id="74d5f-111">Bir öğe eklemek için **Ekle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74d5f-111">To add an item, click the **Add** button.</span></span> <span data-ttu-id="74d5f-112">Ardından, <xref:System.Windows.Forms.ListView.Text%2A> ve <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> özellikleri gibi yeni öğenin özelliklerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74d5f-112">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListView.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>

4. <span data-ttu-id="74d5f-113">Bir öğeyi kaldırmak için, seçin ve **Kaldır** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74d5f-113">To remove an item, select it and click the **Remove** button.</span></span>

## <a name="see-also"></a><span data-ttu-id="74d5f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74d5f-114">See also</span></span>

- [<span data-ttu-id="74d5f-115">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="74d5f-115">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="74d5f-116">Nasıl yapılır: Windows Forms ListView Denetimine sütun ekleme</span><span class="sxs-lookup"><span data-stu-id="74d5f-116">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="74d5f-117">Nasıl yapılır: Windows Forms ListView denetimiyle alt öğeleri sütunlarda görüntüleme</span><span class="sxs-lookup"><span data-stu-id="74d5f-117">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="74d5f-118">Nasıl yapılır: Windows Forms ListView denetimi için simgeler görüntüleme</span><span class="sxs-lookup"><span data-stu-id="74d5f-118">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="74d5f-119">Nasıl yapılır: Bir TreeView veya ListView denetimine özel bilgi ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="74d5f-119">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [<span data-ttu-id="74d5f-120">Nasıl yapılır: Windows Forms ListView denetimindeki öğeleri gruplandırma</span><span class="sxs-lookup"><span data-stu-id="74d5f-120">How to: Group Items in a Windows Forms ListView Control</span></span>](how-to-group-items-in-a-windows-forms-listview-control.md)
