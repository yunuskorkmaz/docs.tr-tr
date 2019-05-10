---
title: 'Nasıl yapılır: Akış İçeriği Öğelerini Blokların Özelliği ile Düzenleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], manipulating flow content elements through Blocks property
- flow content elements [WPF], manipulating through Blocks property
- properties [WPF], Blocks [WPF], manipulating flow content elements
- Blocks property [WPF], manipulating flow content elements
ms.assetid: aeda4ece-b979-4818-a093-ef938e908751
ms.openlocfilehash: 3ca05590bd1adf7f9c486382a08cb334b4731ac9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614608"
---
# <a name="how-to-manipulate-flow-content-elements-through-the-blocks-property"></a><span data-ttu-id="524b7-102">Nasıl yapılır: Akış İçeriği Öğelerini Blokların Özelliği ile Düzenleme</span><span class="sxs-lookup"><span data-stu-id="524b7-102">How to: Manipulate Flow Content Elements through the Blocks Property</span></span>
<span data-ttu-id="524b7-103">Akış içeriği öğelerini gerçekleştirilebilir daha yaygın işlemlerin bazıları bu örneklerde görüldüğü **blokları** özelliği.</span><span class="sxs-lookup"><span data-stu-id="524b7-103">These examples demonstrate some of the more common operations that can be performed on flow content elements through the **Blocks** property.</span></span> <span data-ttu-id="524b7-104">Bu özellik öğesinden öğeleri eklemek ve kaldırmak için kullanılan <xref:System.Windows.Documents.BlockCollection>.</span><span class="sxs-lookup"><span data-stu-id="524b7-104">This property is used to add and remove items from <xref:System.Windows.Documents.BlockCollection>.</span></span> <span data-ttu-id="524b7-105">Akış içerik öğeleri bu özellik bir **blokları** özellik içerir:</span><span class="sxs-lookup"><span data-stu-id="524b7-105">Flow content elements that feature a **Blocks** property include:</span></span>  
  
- <xref:System.Windows.Documents.Figure>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.ListItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.TableCell>  
  
 <span data-ttu-id="524b7-106">Kullanmak için bu örnekleri meydana <xref:System.Windows.Documents.Section> akışı olarak içerik öğesi, ancak bu tekniklerin bir akış içerik öğe koleksiyonu barındıran tüm öğeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="524b7-106">These examples happen to use <xref:System.Windows.Documents.Section> as the flow content element, but these techniques are applicable to all elements that host a flow content element collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="524b7-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="524b7-107">Example</span></span>  
 <span data-ttu-id="524b7-108">Aşağıdaki örnek yeni bir oluşturur <xref:System.Windows.Documents.Section> ve ardından **Ekle** yöntemi yeni bir paragrafa eklemek için **bölümü** içeriği.</span><span class="sxs-lookup"><span data-stu-id="524b7-108">The following example creates a new <xref:System.Windows.Documents.Section> and then uses the **Add** method to add a new Paragraph to the **Section** contents.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
## <a name="example"></a><span data-ttu-id="524b7-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="524b7-109">Example</span></span>  
 <span data-ttu-id="524b7-110">Aşağıdaki örnek yeni bir oluşturur <xref:System.Windows.Documents.Paragraph> öğesi ve başında ekler <xref:System.Windows.Documents.Section>.</span><span class="sxs-lookup"><span data-stu-id="524b7-110">The following example creates a new <xref:System.Windows.Documents.Paragraph> element and inserts it at the beginning of the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksinsert)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksinsert)]  
  
## <a name="example"></a><span data-ttu-id="524b7-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="524b7-111">Example</span></span>  
 <span data-ttu-id="524b7-112">Aşağıdaki örnek, üst düzey sayısını alır. <xref:System.Windows.Documents.Block> içindeki öğe <xref:System.Windows.Documents.Section>.</span><span class="sxs-lookup"><span data-stu-id="524b7-112">The following example gets the number of top-level <xref:System.Windows.Documents.Block> elements contained in the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksCount](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblockscount)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksCount](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblockscount)]  
  
## <a name="example"></a><span data-ttu-id="524b7-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="524b7-113">Example</span></span>  
 <span data-ttu-id="524b7-114">Aşağıdaki örnekte, son silinir <xref:System.Windows.Documents.Block> öğesinde <xref:System.Windows.Documents.Section>.</span><span class="sxs-lookup"><span data-stu-id="524b7-114">The following example deletes the last <xref:System.Windows.Documents.Block> element in the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksremovelast)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksremovelast)]  
  
## <a name="example"></a><span data-ttu-id="524b7-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="524b7-115">Example</span></span>  
 <span data-ttu-id="524b7-116">Aşağıdaki örnek içeriğinin tamamını temizler (<xref:System.Windows.Documents.Block> öğeleri) öğesinden <xref:System.Windows.Documents.Section>.</span><span class="sxs-lookup"><span data-stu-id="524b7-116">The following example clears all of the contents (<xref:System.Windows.Documents.Block> elements) from the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksClear](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksclear)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksclear)]  
  
## <a name="see-also"></a><span data-ttu-id="524b7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="524b7-117">See also</span></span>

- <xref:System.Windows.Documents.BlockCollection>
- <xref:System.Windows.Documents.InlineCollection>
- <xref:System.Windows.Documents.ListItemCollection>
- [<span data-ttu-id="524b7-118">Akış Belgesine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="524b7-118">Flow Document Overview</span></span>](flow-document-overview.md)
- [<span data-ttu-id="524b7-119">RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="524b7-119">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="524b7-120">Sütunlar Özelliği Aracılığıyla bir Tablonun Sütunlarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="524b7-120">Manipulate a Table's Columns through the Columns Property</span></span>](how-to-manipulate-table-columns-through-the-columns-property.md)
- [<span data-ttu-id="524b7-121">RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="524b7-121">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
