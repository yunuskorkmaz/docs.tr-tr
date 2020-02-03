---
title: Tasarımcıyı kullanarak ListView denetimindeki öğeleri gruplandırma
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: 935d8d75517e1028e686ca229f6ada656f58b01e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736675"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="ab989-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları ListView Denetimindeki Öğeleri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="ab989-102">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="ab989-103"><xref:System.Windows.Forms.ListView> denetiminin gruplandırma özelliği, gruplar içindeki ilgili öğe kümelerini görüntülemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ab989-103">The grouping feature of the <xref:System.Windows.Forms.ListView> control enables you to display related sets of items in groups.</span></span> <span data-ttu-id="ab989-104">Bu gruplar, grup başlıklarını içeren yatay grup üst bilgilerine göre ekranda ayrılır.</span><span class="sxs-lookup"><span data-stu-id="ab989-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="ab989-105">Öğeleri alfabetik olarak, tarihe göre veya diğer mantıksal gruplandırmalara göre gruplandırarak büyük listeleri daha kolay gezinmek için <xref:System.Windows.Forms.ListView> gruplarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab989-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="ab989-106">Aşağıdaki görüntüde bazı gruplanmış öğeler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ab989-106">The following image shows some grouped items:</span></span>

![Tek ve hatta gruplara ayrılmış sayılar.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

<span data-ttu-id="ab989-108">Aşağıdaki yordam, bir <xref:System.Windows.Forms.ListView> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ab989-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="ab989-109">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ab989-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

<span data-ttu-id="ab989-110">Gruplamayı etkinleştirmek için önce tasarımcıda veya program aracılığıyla bir veya daha fazla <xref:System.Windows.Forms.ListViewGroup> nesnesi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ab989-110">To enable grouping, you must first create one or more <xref:System.Windows.Forms.ListViewGroup> objects either in the designer or programmatically.</span></span> <span data-ttu-id="ab989-111">Bir grup tanımlandıktan sonra, ona öğe atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab989-111">Once a group has been defined, you can assign items to it.</span></span>

## <a name="to-add-or-remove-groups-in-the-designer"></a><span data-ttu-id="ab989-112">Tasarımcıda grup eklemek veya kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="ab989-112">To add or remove groups in the designer</span></span>

1. <span data-ttu-id="ab989-113">**Özellikler** penceresinde, <xref:System.Windows.Forms.ListView.Groups%2A> özelliğinin yanındaki Visual Studio 'nun Özellikler penceresi](./media/visual-studio-ellipsis-button.png)) düğmesine **üç nokta**![(...) düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="ab989-113">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Groups%2A> property.</span></span>

     <span data-ttu-id="ab989-114">**ListViewGroup koleksiyonu Düzenleyicisi** görünür.</span><span class="sxs-lookup"><span data-stu-id="ab989-114">The **ListViewGroup Collection Editor** appears.</span></span>

2. <span data-ttu-id="ab989-115">Bir grup eklemek için **Ekle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ab989-115">To add a group, click the **Add** button.</span></span> <span data-ttu-id="ab989-116">Daha sonra, <xref:System.Windows.Forms.ListViewGroup.Header%2A> ve <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> özellikleri gibi yeni grubun özelliklerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab989-116">You can then set properties of the new group, such as the <xref:System.Windows.Forms.ListViewGroup.Header%2A> and <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> properties.</span></span> <span data-ttu-id="ab989-117">Bir grubu kaldırmak için, seçin ve **Kaldır** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ab989-117">To remove a group, select it and click the **Remove** button.</span></span>

## <a name="to-assign-items-to-groups-in-the-designer"></a><span data-ttu-id="ab989-118">Tasarımcı 'daki gruplara öğe atamak için</span><span class="sxs-lookup"><span data-stu-id="ab989-118">To assign items to groups in the designer</span></span>

1. <span data-ttu-id="ab989-119">**Özellikler** penceresinde, <xref:System.Windows.Forms.ListView.Items%2A> özelliğinin yanındaki Visual Studio 'nun Özellikler penceresi](./media/visual-studio-ellipsis-button.png)) düğmesine **üç nokta**![(...) düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="ab989-119">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>

     <span data-ttu-id="ab989-120">**ListViewItem koleksiyonu Düzenleyicisi** görünür.</span><span class="sxs-lookup"><span data-stu-id="ab989-120">The **ListViewItem Collection Editor** appears.</span></span>

2. <span data-ttu-id="ab989-121">Yeni bir öğe eklemek için **Ekle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ab989-121">To add a new item, click the **Add** button.</span></span> <span data-ttu-id="ab989-122">Daha sonra, <xref:System.Windows.Forms.ListViewItem.Text%2A> ve <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> özellikleri gibi yeni öğenin özelliklerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab989-122">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListViewItem.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>

3. <span data-ttu-id="ab989-123"><xref:System.Windows.Forms.ListViewItem.Group%2A> özelliğini seçin ve açılan listeden bir grup seçin.</span><span class="sxs-lookup"><span data-stu-id="ab989-123">Select the <xref:System.Windows.Forms.ListViewItem.Group%2A> property and choose a group from the drop-down list.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab989-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab989-124">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="ab989-125">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="ab989-125">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="ab989-126">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ab989-126">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="ab989-127">Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="ab989-127">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
