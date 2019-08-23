---
title: 'Nasıl yapılır: Sütunlar Özelliği Aracılığıyla bir Tablonun Sütunlarını Düzenleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], manipulating table columns
- properties [WPF], Columns [WPF], manipulating table columns
- tables [WPF], manipulating columns
- Columns property [WPF]
ms.assetid: 3f8884f4-7e1f-456b-be06-fbd3cf469bf3
ms.openlocfilehash: 18a26c76688ebf668293cb1254404d6d2cf15208
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913600"
---
# <a name="how-to-manipulate-a-tables-columns-through-the-columns-property"></a><span data-ttu-id="1c945-102">Nasıl yapılır: Sütunlar Özelliği Aracılığıyla bir Tablonun Sütunlarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="1c945-102">How to: Manipulate a Table's Columns through the Columns Property</span></span>
<span data-ttu-id="1c945-103">Bu örnek, bir tablonun sütunlarında, <xref:System.Windows.Documents.Table.Columns%2A> özelliği aracılığıyla gerçekleştirilebilecek daha yaygın işlemlerden bazılarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c945-103">This example demonstrates some of the more common operations that can be performed on a table's columns through the <xref:System.Windows.Documents.Table.Columns%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c945-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c945-104">Example</span></span>  
 <span data-ttu-id="1c945-105">Aşağıdaki örnek yeni bir tablo oluşturur ve ardından <xref:System.Windows.Documents.TableColumnCollection.Add%2A> <xref:System.Windows.Documents.Table.Columns%2A> tablo koleksiyonuna sütun eklemek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1c945-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableColumnCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## <a name="example"></a><span data-ttu-id="1c945-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c945-106">Example</span></span>  
 <span data-ttu-id="1c945-107">Aşağıdaki örnek yeni <xref:System.Windows.Documents.TableColumn>bir ekler.</span><span class="sxs-lookup"><span data-stu-id="1c945-107">The following example inserts a new <xref:System.Windows.Documents.TableColumn>.</span></span>  <span data-ttu-id="1c945-108">Yeni sütun, 0 dizin konumuna eklenir ve tablodaki yeni ilk sütun haline gelir.</span><span class="sxs-lookup"><span data-stu-id="1c945-108">The new column is inserted at index position 0, making it the new first column in the table.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c945-109"><xref:System.Windows.Documents.TableColumnCollection> Koleksiyon standart sıfır tabanlı dizin oluşturmayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="1c945-109">The <xref:System.Windows.Documents.TableColumnCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## <a name="example"></a><span data-ttu-id="1c945-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c945-110">Example</span></span>  
 <span data-ttu-id="1c945-111">Aşağıdaki örnek, <xref:System.Windows.Documents.TableColumnCollection> koleksiyondaki sütunlarda, dizine göre belirli sütunlara başvurarak bazı rastgele özelliklere erişir.</span><span class="sxs-lookup"><span data-stu-id="1c945-111">The following example accesses some arbitrary properties on columns in the <xref:System.Windows.Documents.TableColumnCollection> collection, referring to particular columns by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## <a name="example"></a><span data-ttu-id="1c945-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c945-112">Example</span></span>  
 <span data-ttu-id="1c945-113">Aşağıdaki örnek, şu anda tablo tarafından barındırılan sütun sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="1c945-113">The following example gets the number of columns currently hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## <a name="example"></a><span data-ttu-id="1c945-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c945-114">Example</span></span>  
 <span data-ttu-id="1c945-115">Aşağıdaki örnek, belirli bir sütunu başvuruya göre kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1c945-115">The following example removes a particular column by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## <a name="example"></a><span data-ttu-id="1c945-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c945-116">Example</span></span>  
 <span data-ttu-id="1c945-117">Aşağıdaki örnek, belirli bir sütunu dizine göre kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1c945-117">The following example removes a particular column by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## <a name="example"></a><span data-ttu-id="1c945-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c945-118">Example</span></span>  
 <span data-ttu-id="1c945-119">Aşağıdaki örnek, tüm sütunları tablonun sütun koleksiyonundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1c945-119">The following example removes all columns from the table's columns collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="1c945-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c945-120">See also</span></span>

- [<span data-ttu-id="1c945-121">Tabloya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1c945-121">Table Overview</span></span>](table-overview.md)
- [<span data-ttu-id="1c945-122">XAML ile Tablo Tanımlama</span><span class="sxs-lookup"><span data-stu-id="1c945-122">Define a Table with XAML</span></span>](how-to-define-a-table-with-xaml.md)
- [<span data-ttu-id="1c945-123">Program Aracılığıyla Tablo Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1c945-123">Build a Table Programmatically</span></span>](how-to-build-a-table-programmatically.md)
- [<span data-ttu-id="1c945-124">RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="1c945-124">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="1c945-125">FlowDocument'ı Blokların Özelliği ile Düzenleme</span><span class="sxs-lookup"><span data-stu-id="1c945-125">Manipulate a FlowDocument through the Blocks Property</span></span>](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [<span data-ttu-id="1c945-126">RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="1c945-126">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
