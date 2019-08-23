---
title: 'Nasıl yapılır: Windows Forms ListView Denetimindeki Öğeleri Gruplama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- lists [Windows Forms], grouping items
- grouping
- list views [Windows Forms], grouping items
- groups
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 610416a1-8da4-436c-af19-5f19e654769b
ms.openlocfilehash: b4cd2b9ed23f377912270d33b1415ad39c9e80c0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966627"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="ab350-102">Nasıl yapılır: Windows Forms ListView Denetimindeki Öğeleri Gruplama</span><span class="sxs-lookup"><span data-stu-id="ab350-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="ab350-103"><xref:System.Windows.Forms.ListView> Denetimin gruplandırma özelliği ile, gruplar içindeki ilgili öğe kümelerini görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab350-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="ab350-104">Bu gruplar, grup başlıklarını içeren yatay grup üst bilgilerine göre ekranda ayrılır.</span><span class="sxs-lookup"><span data-stu-id="ab350-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="ab350-105">Öğeleri alfabetik olarak <xref:System.Windows.Forms.ListView> , tarihe göre veya diğer mantıksal gruplandırmalara göre gruplandırarak büyük listeleri daha kolay gezinmek için grupları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab350-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="ab350-106">Aşağıdaki görüntüde bazı gruplanmış öğeler gösteriliyor.</span><span class="sxs-lookup"><span data-stu-id="ab350-106">The following image shows some grouped items.</span></span>  
  
 ![Tek ve hatta ListView gruplarının ekran görüntüsü.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  
   
 <span data-ttu-id="ab350-108">Gruplamayı etkinleştirmek için önce tasarımcıda veya program aracılığıyla bir veya daha fazla grup oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ab350-108">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="ab350-109">Bir grup tanımlandıktan sonra gruplara öğe atayabilirsiniz <xref:System.Windows.Forms.ListView> .</span><span class="sxs-lookup"><span data-stu-id="ab350-109">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="ab350-110">Ayrıca, öğeleri programlama yoluyla bir gruptan diğerine taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab350-110">You can also move items from one group to another programmatically.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab350-111"><xref:System.Windows.Forms.ListView>gruplar yalnızca [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanız <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi çağırdığında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ab350-111"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ab350-112">Önceki işletim sistemlerinde, gruplarla ilgili herhangi bir kodun etkisi yoktur ve gruplar görünmez.</span><span class="sxs-lookup"><span data-stu-id="ab350-112">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="ab350-113">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ab350-113">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="ab350-114">Grup eklemek için</span><span class="sxs-lookup"><span data-stu-id="ab350-114">To add groups</span></span>  
  
1. <span data-ttu-id="ab350-115"><xref:System.Windows.Forms.ListView.Groups%2A> Koleksiyonun <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ab350-115">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="ab350-116">Grupları kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="ab350-116">To remove groups</span></span>  
  
1. <span data-ttu-id="ab350-117"><xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> Koleksiyonun veya<xref:System.Windows.Forms.ListView.Groups%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ab350-117">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="ab350-118">Yöntemi tek bir grubu kaldırır <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> ; yöntemi listedeki tüm grupları kaldırır. <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A></span><span class="sxs-lookup"><span data-stu-id="ab350-118">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ab350-119">Bir grubun kaldırılması bu gruptaki öğeleri kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="ab350-119">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="ab350-120">Gruplara öğe atamak veya öğeleri gruplar arasında taşımak için</span><span class="sxs-lookup"><span data-stu-id="ab350-120">To assign items to groups or move items between groups</span></span>  
  
1. <span data-ttu-id="ab350-121">Ayrı öğelerin <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ab350-121">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="ab350-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab350-122">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="ab350-123">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="ab350-123">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="ab350-124">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ab350-124">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="ab350-125">Nasıl yapılır: Windows Forms ListView denetimiyle öğe ekleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="ab350-125">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
