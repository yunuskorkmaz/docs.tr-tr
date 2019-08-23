---
title: 'Nasıl yapılır: RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- row groups [WPF], manipulating through RowGroups property
- RowGroups property [WPF], manipulating row groups
- documents [WPF], manipulating row groups through RowGroups property
- properties [WPF], RowGroups [WPF], manipulating row groups
ms.assetid: ea61440f-08ae-44ed-b314-5716aaaae3ed
ms.openlocfilehash: 195920af64888bd3671b45befc0fe4cde463ae7b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913555"
---
# <a name="how-to-manipulate-a-tables-row-groups-through-the-rowgroups-property"></a><span data-ttu-id="f408c-102">Nasıl yapılır: RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="f408c-102">How to: Manipulate a Table's Row Groups through the RowGroups Property</span></span>
<span data-ttu-id="f408c-103">Bu örnek, <xref:System.Windows.Documents.Table.RowGroups%2A> özelliği aracılığıyla bir tablonun satır gruplarında gerçekleştirilebilecek daha yaygın işlemlerden bazılarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f408c-103">This example demonstrates some of the more common operations that can be performed on a table's row groups through the <xref:System.Windows.Documents.Table.RowGroups%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f408c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f408c-104">Example</span></span>  
 <span data-ttu-id="f408c-105">Aşağıdaki örnek yeni bir tablo oluşturur ve ardından <xref:System.Windows.Documents.TableRowGroupCollection.Add%2A> <xref:System.Windows.Documents.Table.RowGroups%2A> tablo koleksiyonuna sütun eklemek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f408c-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableRowGroupCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.RowGroups%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Add](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_add)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Add](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_add)]  
  
## <a name="example"></a><span data-ttu-id="f408c-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="f408c-106">Example</span></span>  
 <span data-ttu-id="f408c-107">Aşağıdaki örnek yeni <xref:System.Windows.Documents.TableRowGroup>bir ekler.</span><span class="sxs-lookup"><span data-stu-id="f408c-107">The following example inserts a new <xref:System.Windows.Documents.TableRowGroup>.</span></span>  <span data-ttu-id="f408c-108">Yeni sütun, 0 dizin konumuna eklenir ve tablodaki yeni bir ilk satır grubu haline gelir.</span><span class="sxs-lookup"><span data-stu-id="f408c-108">The new column is inserted at index position 0, making it the new first row group in the table.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f408c-109"><xref:System.Windows.Documents.TableRowGroupCollection> Koleksiyon standart sıfır tabanlı dizin oluşturmayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="f408c-109">The <xref:System.Windows.Documents.TableRowGroupCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Insert](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_insert)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Insert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_insert)]  
  
## <a name="example"></a><span data-ttu-id="f408c-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="f408c-110">Example</span></span>  
 <span data-ttu-id="f408c-111">Aşağıdaki örnek, tablosuna belirli <xref:System.Windows.Documents.TableRowGroup> bir (dizinine göre belirtilen) birkaç satır ekler.</span><span class="sxs-lookup"><span data-stu-id="f408c-111">The following example adds several rows to a particular <xref:System.Windows.Documents.TableRowGroup> (specified by index) in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddRows](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addrows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddRows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addrows)]  
  
## <a name="example"></a><span data-ttu-id="f408c-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="f408c-112">Example</span></span>  
 <span data-ttu-id="f408c-113">Aşağıdaki örnek, tablodaki ilk satır grubundaki satırlarda bazı rastgele özelliklere erişir.</span><span class="sxs-lookup"><span data-stu-id="f408c-113">The following example accesses some arbitrary properties on rows in the first row group in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipRows](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_maniprows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipRows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_maniprows)]  
  
## <a name="example"></a><span data-ttu-id="f408c-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="f408c-114">Example</span></span>  
 <span data-ttu-id="f408c-115">Aşağıdaki örnek, tablodaki belirli <xref:System.Windows.Documents.TableRow> bir (dizinine göre belirtilen) için birkaç hücre ekler.</span><span class="sxs-lookup"><span data-stu-id="f408c-115">The following example adds several cells to a particular <xref:System.Windows.Documents.TableRow> (specified by index) in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddCells](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddCells](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addcells)]  
  
## <a name="example"></a><span data-ttu-id="f408c-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="f408c-116">Example</span></span>  
 <span data-ttu-id="f408c-117">Aşağıdaki örnek, ilk satır grubundaki ilk satırdaki hücrelerde bazı rastgele yöntemlere ve özelliklere erişir.</span><span class="sxs-lookup"><span data-stu-id="f408c-117">The following example access some arbitrary methods and properties on cells in the first row in the first row group.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipCells](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_manipcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipCells](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_manipcells)]  
  
## <a name="example"></a><span data-ttu-id="f408c-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="f408c-118">Example</span></span>  
 <span data-ttu-id="f408c-119">Aşağıdaki örnek, tablosunun barındırdığı <xref:System.Windows.Documents.TableRowGroup> öğe sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f408c-119">The following example returns the number of <xref:System.Windows.Documents.TableRowGroup> elements hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Count](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_count)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Count](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_count)]  
  
## <a name="example"></a><span data-ttu-id="f408c-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="f408c-120">Example</span></span>  
 <span data-ttu-id="f408c-121">Aşağıdaki örnek, belirli bir satır grubunu başvuruya göre kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f408c-121">The following example removes a particular row group by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelRef](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delref)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelRef](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delref)]  
  
## <a name="example"></a><span data-ttu-id="f408c-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="f408c-122">Example</span></span>  
 <span data-ttu-id="f408c-123">Aşağıdaki örnek, belirli bir satır grubunu dizine göre kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f408c-123">The following example removes a particular row group by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delindex)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelIndex](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delindex)]  
  
## <a name="example"></a><span data-ttu-id="f408c-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="f408c-124">Example</span></span>  
 <span data-ttu-id="f408c-125">Aşağıdaki örnek, tüm satır gruplarını tablonun satır grupları koleksiyonundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f408c-125">The following example removes all row groups from the table's row groups collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Clear](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_clear)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Clear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="f408c-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f408c-126">See also</span></span>

- [<span data-ttu-id="f408c-127">Nasıl yapılır: Akış Içeriği öğelerini Inlines özelliği aracılığıyla işleme</span><span class="sxs-lookup"><span data-stu-id="f408c-127">How-to: Manipulate Flow Content Elements through the Inlines Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="f408c-128">FlowDocument'ı Blokların Özelliği ile Düzenleme</span><span class="sxs-lookup"><span data-stu-id="f408c-128">Manipulate a FlowDocument through the Blocks Property</span></span>](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [<span data-ttu-id="f408c-129">Sütunlar Özelliği Aracılığıyla bir Tablonun Sütunlarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="f408c-129">Manipulate a Table's Columns through the Columns Property</span></span>](how-to-manipulate-table-columns-through-the-columns-property.md)
