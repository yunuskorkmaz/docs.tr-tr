---
title: ListView denetimindeki öğeleri gruplandırma
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
ms.openlocfilehash: 45846751780f433c29b186fe8b9a908f5d295ab3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736633"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="7048d-102">Nasıl yapılır Windows Forms ListView Denetimindeki Öğeleri Gruplama</span><span class="sxs-lookup"><span data-stu-id="7048d-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="7048d-103"><xref:System.Windows.Forms.ListView> denetiminin gruplandırma özelliği ile, gruplar içindeki ilgili öğe kümelerini görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7048d-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="7048d-104">Bu gruplar, grup başlıklarını içeren yatay grup üst bilgilerine göre ekranda ayrılır.</span><span class="sxs-lookup"><span data-stu-id="7048d-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="7048d-105">Öğeleri alfabetik olarak, tarihe göre veya diğer mantıksal gruplandırmalara göre gruplandırarak büyük listeleri daha kolay gezinmek için <xref:System.Windows.Forms.ListView> gruplarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7048d-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="7048d-106">Aşağıdaki görüntüde bazı gruplanmış öğeler gösteriliyor.</span><span class="sxs-lookup"><span data-stu-id="7048d-106">The following image shows some grouped items.</span></span>  
  
 ![Tek ve hatta ListView gruplarının ekran görüntüsü.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  
   
 <span data-ttu-id="7048d-108">Gruplamayı etkinleştirmek için önce tasarımcıda veya program aracılığıyla bir veya daha fazla grup oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7048d-108">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="7048d-109">Bir grup tanımlandıktan sonra gruplara <xref:System.Windows.Forms.ListView> öğeleri atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7048d-109">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="7048d-110">Ayrıca, öğeleri programlama yoluyla bir gruptan diğerine taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7048d-110">You can also move items from one group to another programmatically.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="7048d-111">Grup eklemek için</span><span class="sxs-lookup"><span data-stu-id="7048d-111">To add groups</span></span>  
  
1. <span data-ttu-id="7048d-112"><xref:System.Windows.Forms.ListView.Groups%2A> koleksiyonunun <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7048d-112">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="7048d-113">Grupları kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="7048d-113">To remove groups</span></span>  
  
1. <span data-ttu-id="7048d-114"><xref:System.Windows.Forms.ListView.Groups%2A> koleksiyonunun <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> veya <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7048d-114">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="7048d-115"><xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> yöntemi tek bir grubu kaldırır; <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> yöntemi, tüm grupları listeden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7048d-115">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7048d-116">Bir grubun kaldırılması bu gruptaki öğeleri kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="7048d-116">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="7048d-117">Gruplara öğe atamak veya öğeleri gruplar arasında taşımak için</span><span class="sxs-lookup"><span data-stu-id="7048d-117">To assign items to groups or move items between groups</span></span>  
  
1. <span data-ttu-id="7048d-118">Ayrı öğelerin <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7048d-118">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="7048d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7048d-119">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="7048d-120">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="7048d-120">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="7048d-121">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7048d-121">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="7048d-122">Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="7048d-122">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
