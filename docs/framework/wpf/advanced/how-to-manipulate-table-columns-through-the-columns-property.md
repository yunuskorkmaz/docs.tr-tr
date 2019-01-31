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
ms.openlocfilehash: e3327b59cb8c387cb554206d1b17c2cd7002ef80
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55258103"
---
# <a name="how-to-manipulate-a-tables-columns-through-the-columns-property"></a><span data-ttu-id="980f5-102">Nasıl yapılır: Sütunlar Özelliği Aracılığıyla bir Tablonun Sütunlarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="980f5-102">How to: Manipulate a Table's Columns through the Columns Property</span></span>
<span data-ttu-id="980f5-103">Bu örnekte aracılığıyla bir tablonun sütunlarını gerçekleştirilebilir daha yaygın işlemleri bazılarını göstermektedir <xref:System.Windows.Documents.Table.Columns%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="980f5-103">This example demonstrates some of the more common operations that can be performed on a table's columns through the <xref:System.Windows.Documents.Table.Columns%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="980f5-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="980f5-104">Example</span></span>  
 <span data-ttu-id="980f5-105">Aşağıdaki örnek yeni bir tablo oluşturur ve ardından <xref:System.Windows.Documents.TableColumnCollection.Add%2A> tablonun sütunlar eklemek yöntemi <xref:System.Windows.Documents.Table.Columns%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="980f5-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableColumnCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## <a name="example"></a><span data-ttu-id="980f5-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="980f5-106">Example</span></span>  
 <span data-ttu-id="980f5-107">Aşağıdaki örnek yeni bir ekler <xref:System.Windows.Documents.TableColumn>.</span><span class="sxs-lookup"><span data-stu-id="980f5-107">The following example inserts a new <xref:System.Windows.Documents.TableColumn>.</span></span>  <span data-ttu-id="980f5-108">Konumunda yeni bir ilk sütun tabloda getirerek dizin 0, yeni bir sütun eklenir.</span><span class="sxs-lookup"><span data-stu-id="980f5-108">The new column is inserted at index position 0, making it the new first column in the table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="980f5-109"><xref:System.Windows.Documents.TableColumnCollection> Koleksiyonun kullandığı standart sıfır tabanlı dizin.</span><span class="sxs-lookup"><span data-stu-id="980f5-109">The <xref:System.Windows.Documents.TableColumnCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## <a name="example"></a><span data-ttu-id="980f5-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="980f5-110">Example</span></span>  
 <span data-ttu-id="980f5-111">Aşağıdaki örnek rastgele bazı özellikler sütunlarında erişen <xref:System.Windows.Documents.TableColumnCollection> belirli sütunları dizine göre başvuran koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="980f5-111">The following example accesses some arbitrary properties on columns in the <xref:System.Windows.Documents.TableColumnCollection> collection, referring to particular columns by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## <a name="example"></a><span data-ttu-id="980f5-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="980f5-112">Example</span></span>  
 <span data-ttu-id="980f5-113">Aşağıdaki örnek tablo tarafından şu anda barındırılan sütunların sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="980f5-113">The following example gets the number of columns currently hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## <a name="example"></a><span data-ttu-id="980f5-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="980f5-114">Example</span></span>  
 <span data-ttu-id="980f5-115">Aşağıdaki örnek, belirli bir sütuna göre başvuruyu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="980f5-115">The following example removes a particular column by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## <a name="example"></a><span data-ttu-id="980f5-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="980f5-116">Example</span></span>  
 <span data-ttu-id="980f5-117">Aşağıdaki örnek, belirli bir sütuna dizin tarafından kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="980f5-117">The following example removes a particular column by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## <a name="example"></a><span data-ttu-id="980f5-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="980f5-118">Example</span></span>  
 <span data-ttu-id="980f5-119">Aşağıdaki örnek, tüm sütunları tablonun sütun koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="980f5-119">The following example removes all columns from the table's columns collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="980f5-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="980f5-120">See also</span></span>
- [<span data-ttu-id="980f5-121">Tabloya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="980f5-121">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)
- [<span data-ttu-id="980f5-122">XAML ile Tablo Tanımlama</span><span class="sxs-lookup"><span data-stu-id="980f5-122">Define a Table with XAML</span></span>](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)
- [<span data-ttu-id="980f5-123">Program Aracılığıyla Tablo Oluşturma</span><span class="sxs-lookup"><span data-stu-id="980f5-123">Build a Table Programmatically</span></span>](../../../../docs/framework/wpf/advanced/how-to-build-a-table-programmatically.md)
- [<span data-ttu-id="980f5-124">RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="980f5-124">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="980f5-125">FlowDocument'ı Blokların Özelliği ile Düzenleme</span><span class="sxs-lookup"><span data-stu-id="980f5-125">Manipulate a FlowDocument through the Blocks Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [<span data-ttu-id="980f5-126">RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="980f5-126">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
