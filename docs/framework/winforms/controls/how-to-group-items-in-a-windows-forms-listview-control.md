---
title: ListView Denetiminde Öğeleri Grupla
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
ms.openlocfilehash: a1754d10de2bbb5895ae861cd17f4af1f18810e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141997"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="8966c-102">Nasıl yapılır Windows Forms ListView Denetimindeki Öğeleri Gruplama</span><span class="sxs-lookup"><span data-stu-id="8966c-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="8966c-103"><xref:System.Windows.Forms.ListView> Denetimin gruplandırma özelliğiyle, ilgili öğe kümelerini gruplar halinde görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8966c-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="8966c-104">Bu gruplar, grup başlıklarını içeren yatay grup başlıkları yla ekranda ayrılır.</span><span class="sxs-lookup"><span data-stu-id="8966c-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="8966c-105">Büyük listelerde gezinmeyi, öğeleri alfabetik olarak, tarihe göre veya başka bir mantıksal gruplandırmaya göre gruplandırmayı kolaylaştırmak için grupları kullanabilirsiniz. <xref:System.Windows.Forms.ListView></span><span class="sxs-lookup"><span data-stu-id="8966c-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="8966c-106">Aşağıdaki resimde bazı gruplanmış öğeler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8966c-106">The following image shows some grouped items.</span></span>  
  
 ![Tek ve çift ListView gruplarının ekran görüntüsü.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  

 <span data-ttu-id="8966c-108">Gruplandırmayı etkinleştirmek için önce tasarımcıda veya programlı olarak bir veya daha fazla grup oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8966c-108">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="8966c-109">Bir grup tanımlandıktan sonra, gruplara öğe atayabilirsiniz. <xref:System.Windows.Forms.ListView></span><span class="sxs-lookup"><span data-stu-id="8966c-109">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="8966c-110">Öğeleri bir gruptan diğerine programlı olarak da taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8966c-110">You can also move items from one group to another programmatically.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="8966c-111">Grup eklemek için</span><span class="sxs-lookup"><span data-stu-id="8966c-111">To add groups</span></span>  
  
1. <span data-ttu-id="8966c-112">Toplama <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> yöntemini <xref:System.Windows.Forms.ListView.Groups%2A> kullanın.</span><span class="sxs-lookup"><span data-stu-id="8966c-112">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="8966c-113">Grupları kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="8966c-113">To remove groups</span></span>  
  
1. <span data-ttu-id="8966c-114">Koleksiyonun <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> yöntemini <xref:System.Windows.Forms.ListView.Groups%2A> veya yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8966c-114">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="8966c-115">Yöntem <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> tek bir grubu kaldırır; <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> yöntem tüm grupları listeden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8966c-115">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8966c-116">Bir grubu kaldırmak, bu gruptaki öğeleri kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="8966c-116">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="8966c-117">Maddeleri gruplara atamak veya maddeleri gruplar arasında taşımak için</span><span class="sxs-lookup"><span data-stu-id="8966c-117">To assign items to groups or move items between groups</span></span>  
  
1. <span data-ttu-id="8966c-118">Tek <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> tek öğelerin özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8966c-118">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="8966c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8966c-119">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="8966c-120">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="8966c-120">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="8966c-121">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8966c-121">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="8966c-122">Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="8966c-122">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
