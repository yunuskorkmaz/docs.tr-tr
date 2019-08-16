---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetimindeki Öğeleri Gruplandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: b63bcd9e5e357db350cc2987e09af84eb58bdcff
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039408"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="640f4-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetimindeki Öğeleri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="640f4-102">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="640f4-103"><xref:System.Windows.Forms.ListView> Denetimin gruplandırma özelliği, gruplar içindeki ilgili öğe kümelerini görüntülemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="640f4-103">The grouping feature of the <xref:System.Windows.Forms.ListView> control enables you to display related sets of items in groups.</span></span> <span data-ttu-id="640f4-104">Bu gruplar, grup başlıklarını içeren yatay grup üst bilgilerine göre ekranda ayrılır.</span><span class="sxs-lookup"><span data-stu-id="640f4-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="640f4-105">Öğeleri alfabetik olarak <xref:System.Windows.Forms.ListView> , tarihe göre veya diğer mantıksal gruplandırmalara göre gruplandırarak büyük listeleri daha kolay gezinmek için grupları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="640f4-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="640f4-106">Aşağıdaki görüntüde bazı gruplanmış öğeler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="640f4-106">The following image shows some grouped items:</span></span>

![Tek ve hatta gruplara ayrılmış sayılar.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

<span data-ttu-id="640f4-108">Aşağıdaki yordam, bir <xref:System.Windows.Forms.ListView> denetim içeren bir form ile **Windows uygulama** projesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="640f4-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="640f4-109">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="640f4-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

<span data-ttu-id="640f4-110">Gruplamayı etkinleştirmek için önce tasarımcıda veya program aracılığıyla bir veya daha <xref:System.Windows.Forms.ListViewGroup> fazla nesne oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="640f4-110">To enable grouping, you must first create one or more <xref:System.Windows.Forms.ListViewGroup> objects either in the designer or programmatically.</span></span> <span data-ttu-id="640f4-111">Bir grup tanımlandıktan sonra, ona öğe atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="640f4-111">Once a group has been defined, you can assign items to it.</span></span>

> [!NOTE]
> <span data-ttu-id="640f4-112"><xref:System.Windows.Forms.ListView>gruplar yalnızca [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanız <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi çağırdığında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="640f4-112"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="640f4-113">Önceki işletim sistemlerinde, gruplarla ilgili herhangi bir kodun etkisi yoktur ve gruplar görünmez.</span><span class="sxs-lookup"><span data-stu-id="640f4-113">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="640f4-114">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="640f4-114">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>

## <a name="to-add-or-remove-groups-in-the-designer"></a><span data-ttu-id="640f4-115">Tasarımcıda grup eklemek veya kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="640f4-115">To add or remove groups in the designer</span></span>

1. <span data-ttu-id="640f4-116">**Özellikler** penceresinde,![ özelliğin<xref:System.Windows.Forms.ListView.Groups%2A> yanındaki Visual Studio](./media/visual-studio-ellipsis-button.png)'nun Özellikler penceresi (...) üç nokta (...) düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="640f4-116">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Groups%2A> property.</span></span>

     <span data-ttu-id="640f4-117">**ListViewGroup koleksiyonu Düzenleyicisi** görünür.</span><span class="sxs-lookup"><span data-stu-id="640f4-117">The **ListViewGroup Collection Editor** appears.</span></span>

2. <span data-ttu-id="640f4-118">Bir grup eklemek için **Ekle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="640f4-118">To add a group, click the **Add** button.</span></span> <span data-ttu-id="640f4-119">Daha sonra, <xref:System.Windows.Forms.ListViewGroup.Header%2A> ve <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> özellikleri gibi yeni grubun özelliklerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="640f4-119">You can then set properties of the new group, such as the <xref:System.Windows.Forms.ListViewGroup.Header%2A> and <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> properties.</span></span> <span data-ttu-id="640f4-120">Bir grubu kaldırmak için, seçin ve **Kaldır** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="640f4-120">To remove a group, select it and click the **Remove** button.</span></span>

## <a name="to-assign-items-to-groups-in-the-designer"></a><span data-ttu-id="640f4-121">Tasarımcı 'daki gruplara öğe atamak için</span><span class="sxs-lookup"><span data-stu-id="640f4-121">To assign items to groups in the designer</span></span>

1. <span data-ttu-id="640f4-122">**Özellikler** penceresinde,![ özelliğin<xref:System.Windows.Forms.ListView.Items%2A> yanındaki Visual Studio](./media/visual-studio-ellipsis-button.png)'nun Özellikler penceresi (...) üç nokta (...) düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="640f4-122">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>

     <span data-ttu-id="640f4-123">**ListViewItem koleksiyonu Düzenleyicisi** görünür.</span><span class="sxs-lookup"><span data-stu-id="640f4-123">The **ListViewItem Collection Editor** appears.</span></span>

2. <span data-ttu-id="640f4-124">Yeni bir öğe eklemek için **Ekle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="640f4-124">To add a new item, click the **Add** button.</span></span> <span data-ttu-id="640f4-125">Ardından, <xref:System.Windows.Forms.ListViewItem.Text%2A> ve <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> özellikleri gibi yeni öğenin özelliklerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="640f4-125">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListViewItem.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>

3. <span data-ttu-id="640f4-126"><xref:System.Windows.Forms.ListViewItem.Group%2A> Özelliği seçin ve açılan listeden bir grup seçin.</span><span class="sxs-lookup"><span data-stu-id="640f4-126">Select the <xref:System.Windows.Forms.ListViewItem.Group%2A> property and choose a group from the drop-down list.</span></span>

## <a name="see-also"></a><span data-ttu-id="640f4-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="640f4-127">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="640f4-128">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="640f4-128">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="640f4-129">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="640f4-129">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="640f4-130">Nasıl yapılır: Windows Forms ListView denetimiyle öğe ekleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="640f4-130">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
