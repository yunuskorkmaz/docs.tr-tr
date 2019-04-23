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
ms.openlocfilehash: d379d1a98bff614ff9e16cdd340bb69644988743
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078427"
---
# <a name="how-to-manipulate-a-tables-columns-through-the-columns-property"></a><span data-ttu-id="d43ad-102">Nasıl yapılır: Sütunlar Özelliği Aracılığıyla bir Tablonun Sütunlarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="d43ad-102">How to: Manipulate a Table's Columns through the Columns Property</span></span>
<span data-ttu-id="d43ad-103">Bu örnekte aracılığıyla bir tablonun sütunlarını gerçekleştirilebilir daha yaygın işlemleri bazılarını göstermektedir <xref:System.Windows.Documents.Table.Columns%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d43ad-103">This example demonstrates some of the more common operations that can be performed on a table's columns through the <xref:System.Windows.Documents.Table.Columns%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d43ad-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="d43ad-104">Example</span></span>  
 <span data-ttu-id="d43ad-105">Aşağıdaki örnek yeni bir tablo oluşturur ve ardından <xref:System.Windows.Documents.TableColumnCollection.Add%2A> tablonun sütunlar eklemek yöntemi <xref:System.Windows.Documents.Table.Columns%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d43ad-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableColumnCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## <a name="example"></a><span data-ttu-id="d43ad-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d43ad-106">Example</span></span>  
 <span data-ttu-id="d43ad-107">Aşağıdaki örnek yeni bir ekler <xref:System.Windows.Documents.TableColumn>.</span><span class="sxs-lookup"><span data-stu-id="d43ad-107">The following example inserts a new <xref:System.Windows.Documents.TableColumn>.</span></span>  <span data-ttu-id="d43ad-108">Konumunda yeni bir ilk sütun tabloda getirerek dizin 0, yeni bir sütun eklenir.</span><span class="sxs-lookup"><span data-stu-id="d43ad-108">The new column is inserted at index position 0, making it the new first column in the table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d43ad-109"><xref:System.Windows.Documents.TableColumnCollection> Koleksiyonun kullandığı standart sıfır tabanlı dizin.</span><span class="sxs-lookup"><span data-stu-id="d43ad-109">The <xref:System.Windows.Documents.TableColumnCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## <a name="example"></a><span data-ttu-id="d43ad-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="d43ad-110">Example</span></span>  
 <span data-ttu-id="d43ad-111">Aşağıdaki örnek rastgele bazı özellikler sütunlarında erişen <xref:System.Windows.Documents.TableColumnCollection> belirli sütunları dizine göre başvuran koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d43ad-111">The following example accesses some arbitrary properties on columns in the <xref:System.Windows.Documents.TableColumnCollection> collection, referring to particular columns by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## <a name="example"></a><span data-ttu-id="d43ad-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="d43ad-112">Example</span></span>  
 <span data-ttu-id="d43ad-113">Aşağıdaki örnek tablo tarafından şu anda barındırılan sütunların sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="d43ad-113">The following example gets the number of columns currently hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## <a name="example"></a><span data-ttu-id="d43ad-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="d43ad-114">Example</span></span>  
 <span data-ttu-id="d43ad-115">Aşağıdaki örnek, belirli bir sütuna göre başvuruyu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d43ad-115">The following example removes a particular column by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## <a name="example"></a><span data-ttu-id="d43ad-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="d43ad-116">Example</span></span>  
 <span data-ttu-id="d43ad-117">Aşağıdaki örnek, belirli bir sütuna dizin tarafından kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="d43ad-117">The following example removes a particular column by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## <a name="example"></a><span data-ttu-id="d43ad-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="d43ad-118">Example</span></span>  
 <span data-ttu-id="d43ad-119">Aşağıdaki örnek, tüm sütunları tablonun sütun koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d43ad-119">The following example removes all columns from the table's columns collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="d43ad-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d43ad-120">See also</span></span>

- [<span data-ttu-id="d43ad-121">Tabloya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d43ad-121">Table Overview</span></span>](table-overview.md)
- [<span data-ttu-id="d43ad-122">XAML ile Tablo Tanımlama</span><span class="sxs-lookup"><span data-stu-id="d43ad-122">Define a Table with XAML</span></span>](how-to-define-a-table-with-xaml.md)
- [<span data-ttu-id="d43ad-123">Program Aracılığıyla Tablo Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d43ad-123">Build a Table Programmatically</span></span>](how-to-build-a-table-programmatically.md)
- [<span data-ttu-id="d43ad-124">RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="d43ad-124">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="d43ad-125">FlowDocument'ı Blokların Özelliği ile Düzenleme</span><span class="sxs-lookup"><span data-stu-id="d43ad-125">Manipulate a FlowDocument through the Blocks Property</span></span>](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [<span data-ttu-id="d43ad-126">RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="d43ad-126">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
