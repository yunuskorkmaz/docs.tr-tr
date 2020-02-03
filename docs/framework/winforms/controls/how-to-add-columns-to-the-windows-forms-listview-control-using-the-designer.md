---
title: Tasarımcıyı kullanarak ListView Denetimine sütun ekleme
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: 627f8627aac861877a05c13def07427199807754
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744615"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="b0383-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları ListView Denetimine Sütunlar Ekleme</span><span class="sxs-lookup"><span data-stu-id="b0383-102">How to: Add Columns to the Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="b0383-103">Windows Forms <xref:System.Windows.Forms.ListView> denetimi, **Ayrıntılar** görünümünde her liste öğesi için birden çok sütun görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b0383-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item when in the **Details** view.</span></span> <span data-ttu-id="b0383-104">Sütunları, her liste öğesiyle ilgili çeşitli bilgi türlerini göstermek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0383-104">You can use the columns to display several types of information about each list item.</span></span> <span data-ttu-id="b0383-105">Örneğin bir dosya listesi, dosyanın son değiştirilme dosya adını, dosya türünü, boyutunu ve tarihini görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b0383-105">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="b0383-106">Sütunları oluşturulduktan sonra doldurma hakkında daha fazla bilgi için bkz. [nasıl yapılır: öğeleri Windows Forms ListView denetimiyle sütunlarda görüntüleme](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="b0383-106">For information on populating the columns once they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>

<span data-ttu-id="b0383-107">Aşağıdaki yordam, bir <xref:System.Windows.Forms.ListView> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b0383-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="b0383-108">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b0383-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-add-columns-in-the-designer"></a><span data-ttu-id="b0383-109">Tasarımcıya sütun eklemek için</span><span class="sxs-lookup"><span data-stu-id="b0383-109">To add columns in the designer</span></span>

1. <span data-ttu-id="b0383-110">**Özellikler** penceresinde, denetimin <xref:System.Windows.Forms.ListView.View%2A> özelliğini <xref:System.Windows.Forms.View.Details>olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b0383-110">In the **Properties** window, set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>

2. <span data-ttu-id="b0383-111">**Özellikler** penceresinde, <xref:System.Windows.Forms.ListView.Columns%2A> özelliğinin yanındaki Visual Studio.](./media/visual-studio-ellipsis-button.png)) Özellikler penceresi **üç nokta düğmesini** (...)![tıklatın.</span><span class="sxs-lookup"><span data-stu-id="b0383-111">In the **Properties** window, click the **Ellipsis** button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>

     <span data-ttu-id="b0383-112">**ColumnHeader koleksiyon Düzenleyicisi** görünür.</span><span class="sxs-lookup"><span data-stu-id="b0383-112">The **ColumnHeader Collection Editor** appears.</span></span>

3. <span data-ttu-id="b0383-113">Yeni sütunlar eklemek için **Ekle** düğmesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b0383-113">Use the **Add** button to add new columns.</span></span> <span data-ttu-id="b0383-114">Daha sonra sütun başlığını seçebilir ve metnini (sütunun açıklamalı alt yazısı), metin hizalamasını ve genişliği ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0383-114">You can then select the column header and set its text (the caption of the column), text alignment, and width.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0383-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0383-115">See also</span></span>

- [<span data-ttu-id="b0383-116">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b0383-116">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="b0383-117">Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="b0383-117">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="b0383-118">Nasıl yapılır: Windows Forms ListView Denetimiyle Sütunlardaki Alt Öğeleri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="b0383-118">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="b0383-119">Nasıl yapılır: Windows Forms ListView Denetimi için Simgeler Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="b0383-119">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="b0383-120">Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b0383-120">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
