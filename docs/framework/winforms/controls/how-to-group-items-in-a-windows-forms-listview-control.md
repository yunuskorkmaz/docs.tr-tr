---
title: 'Nasıl yapılır: Bir Windows Forms ListView denetimi içinde öğeleri gruplandırma'
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
ms.openlocfilehash: a14d4560a229e62bc0759b6b4eab8087eb53f030
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722964"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="0dd8b-102">Nasıl yapılır: Bir Windows Forms ListView denetimi içinde öğeleri gruplandırma</span><span class="sxs-lookup"><span data-stu-id="0dd8b-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="0dd8b-103">Gruplandırma özelliğini de ile <xref:System.Windows.Forms.ListView> denetimi öğe kümeleri ilgili gruplar halinde görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0dd8b-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="0dd8b-104">Bu grupları ekranda grup başlıklarını içeren yatay grup üstbilgileri tarafından ayrılır.</span><span class="sxs-lookup"><span data-stu-id="0dd8b-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="0dd8b-105">Kullanabileceğiniz <xref:System.Windows.Forms.ListView> öğeleri alfabetik olarak tarih veya diğer bir mantıksal gruplama gruplandırarak büyük listeler daha kolay gezinme olmak için grupları.</span><span class="sxs-lookup"><span data-stu-id="0dd8b-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="0dd8b-106">Aşağıdaki resimde, bazı gruplandırılmış öğeler gösterilir.</span><span class="sxs-lookup"><span data-stu-id="0dd8b-106">The following image shows some grouped items.</span></span>  
  
 <span data-ttu-id="0dd8b-107">![ListView grupları](./media/listviewgroups.gif "ListViewGroups")</span><span class="sxs-lookup"><span data-stu-id="0dd8b-107">![ListView Groups](./media/listviewgroups.gif "ListViewGroups")</span></span>  
<span data-ttu-id="0dd8b-108">ListView gruplandırılmış öğeler</span><span class="sxs-lookup"><span data-stu-id="0dd8b-108">ListView grouped items</span></span>  
  
 <span data-ttu-id="0dd8b-109">Gruplandırma etkinleştirmek için önce bir veya daha fazla Grup Tasarımcısı'nda veya programlama yoluyla oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0dd8b-109">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="0dd8b-110">Bir grubu tanımlandıktan sonra atayabilirsiniz <xref:System.Windows.Forms.ListView> gruplara öğeleri.</span><span class="sxs-lookup"><span data-stu-id="0dd8b-110">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="0dd8b-111">Ayrıca öğeleri bir gruptan başka bir program aracılığıyla taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0dd8b-111">You can also move items from one group to another programmatically.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0dd8b-112"><xref:System.Windows.Forms.ListView> gruplar yalnızca [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanızı çağırdığında <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0dd8b-112"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0dd8b-113">Önceki işletim sistemlerinde herhangi bir kod gruplarına ilgili hiçbir etkisi yoktur ve grupları görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="0dd8b-113">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="0dd8b-114">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0dd8b-114">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="0dd8b-115">Gruplar eklemek için</span><span class="sxs-lookup"><span data-stu-id="0dd8b-115">To add groups</span></span>  
  
1.  <span data-ttu-id="0dd8b-116">Kullanım <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> yöntemi <xref:System.Windows.Forms.ListView.Groups%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="0dd8b-116">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="0dd8b-117">Grubu kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="0dd8b-117">To remove groups</span></span>  
  
1.  <span data-ttu-id="0dd8b-118">Kullanım <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> veya <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> yöntemi <xref:System.Windows.Forms.ListView.Groups%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="0dd8b-118">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="0dd8b-119"><xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> Yöntemi, tek bir grup kaldırır; <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> yöntemi listeden tüm grupları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0dd8b-119">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0dd8b-120">Grup kaldırma, o grup içindeki öğeleri kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="0dd8b-120">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="0dd8b-121">Öğeleri gruplara veya öğeleri grupları arasında taşıma</span><span class="sxs-lookup"><span data-stu-id="0dd8b-121">To assign items to groups or move items between groups</span></span>  
  
1.  <span data-ttu-id="0dd8b-122">Ayarlama <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> tek tek öğelerin özelliği.</span><span class="sxs-lookup"><span data-stu-id="0dd8b-122">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="0dd8b-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dd8b-123">See also</span></span>
- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="0dd8b-124">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="0dd8b-124">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="0dd8b-125">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0dd8b-125">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="0dd8b-126">Nasıl yapılır: Windows Forms ListView denetimi ile öğe ekleyip</span><span class="sxs-lookup"><span data-stu-id="0dd8b-126">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
