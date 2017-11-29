---
title: "Nasıl yapılır: bir tablo &#39; işlemek sütunlar özelliği aracılığıyla s sütunları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], manipulating table columns
- properties [WPF], Columns [WPF], manipulating table columns
- tables [WPF], manipulating columns
- Columns property [WPF]
ms.assetid: 3f8884f4-7e1f-456b-be06-fbd3cf469bf3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d0f15339b829335798d7ee21dcc90b81cb536cf2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-manipulate-a-table39s-columns-through-the-columns-property"></a><span data-ttu-id="4ad95-102">Nasıl yapılır: bir tablo &#39; işlemek sütunlar özelliği aracılığıyla s sütunları</span><span class="sxs-lookup"><span data-stu-id="4ad95-102">How to: Manipulate a Table&#39;s Columns through the Columns Property</span></span>
<span data-ttu-id="4ad95-103">Bu örnek bir tablonun sütunlar üzerinde gerçekleştirilen daha yaygın işlemlerin bazılarını göstermektedir <xref:System.Windows.Documents.Table.Columns%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4ad95-103">This example demonstrates some of the more common operations that can be performed on a table's columns through the <xref:System.Windows.Documents.Table.Columns%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ad95-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ad95-104">Example</span></span>  
 <span data-ttu-id="4ad95-105">Aşağıdaki örnek yeni bir tablo oluşturur ve ardından <xref:System.Windows.Documents.TableColumnCollection.Add%2A> tablonun sütunlar ekleme yöntemi <xref:System.Windows.Documents.Table.Columns%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="4ad95-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableColumnCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## <a name="example"></a><span data-ttu-id="4ad95-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ad95-106">Example</span></span>  
 <span data-ttu-id="4ad95-107">Aşağıdaki örnek yeni bir ekler <xref:System.Windows.Documents.TableColumn>.</span><span class="sxs-lookup"><span data-stu-id="4ad95-107">The following example inserts a new <xref:System.Windows.Documents.TableColumn>.</span></span>  <span data-ttu-id="4ad95-108">Yeni bir sütun konumunda tablosunda yeni bir ilk sütun kolaylaştırarak dizin 0, eklenir.</span><span class="sxs-lookup"><span data-stu-id="4ad95-108">The new column is inserted at index position 0, making it the new first column in the table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ad95-109"><xref:System.Windows.Documents.TableColumnCollection> Koleksiyonu kullanan standart sıfır tabanlı dizin.</span><span class="sxs-lookup"><span data-stu-id="4ad95-109">The <xref:System.Windows.Documents.TableColumnCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## <a name="example"></a><span data-ttu-id="4ad95-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ad95-110">Example</span></span>  
 <span data-ttu-id="4ad95-111">Aşağıdaki örnek sütunlar üzerinde bazı rasgele özelliklere erişir <xref:System.Windows.Documents.TableColumnCollection> dizini tarafından belirli sütunlara başvuran koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="4ad95-111">The following example accesses some arbitrary properties on columns in the <xref:System.Windows.Documents.TableColumnCollection> collection, referring to particular columns by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## <a name="example"></a><span data-ttu-id="4ad95-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ad95-112">Example</span></span>  
 <span data-ttu-id="4ad95-113">Aşağıdaki örnek şu anda tablo tarafından barındırılan sütun sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="4ad95-113">The following example gets the number of columns currently hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## <a name="example"></a><span data-ttu-id="4ad95-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ad95-114">Example</span></span>  
 <span data-ttu-id="4ad95-115">Aşağıdaki örnekte belirli bir sütuna başvuru tarafından kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="4ad95-115">The following example removes a particular column by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## <a name="example"></a><span data-ttu-id="4ad95-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ad95-116">Example</span></span>  
 <span data-ttu-id="4ad95-117">Aşağıdaki örnek, belirli bir sütun dizini tarafından kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="4ad95-117">The following example removes a particular column by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## <a name="example"></a><span data-ttu-id="4ad95-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ad95-118">Example</span></span>  
 <span data-ttu-id="4ad95-119">Aşağıdaki örnek, tüm sütunlar tablonun sütunlar koleksiyonundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4ad95-119">The following example removes all columns from the table's columns collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="4ad95-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4ad95-120">See Also</span></span>  
 [<span data-ttu-id="4ad95-121">Tablo genel bakış</span><span class="sxs-lookup"><span data-stu-id="4ad95-121">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)  
 [<span data-ttu-id="4ad95-122">XAML içeren bir tablo tanımlayın</span><span class="sxs-lookup"><span data-stu-id="4ad95-122">Define a Table with XAML</span></span>](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)  
 [<span data-ttu-id="4ad95-123">Programlı olarak bir tablo oluşturma</span><span class="sxs-lookup"><span data-stu-id="4ad95-123">Build a Table Programmatically</span></span>](../../../../docs/framework/wpf/advanced/how-to-build-a-table-programmatically.md)  
 [<span data-ttu-id="4ad95-124">Tablonun satır grupları RowGroups özelliği aracılığıyla denetlemek</span><span class="sxs-lookup"><span data-stu-id="4ad95-124">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)  
 [<span data-ttu-id="4ad95-125">Blokların özelliği aracılığıyla FlowDocument işlemek</span><span class="sxs-lookup"><span data-stu-id="4ad95-125">Manipulate a FlowDocument through the Blocks Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [<span data-ttu-id="4ad95-126">Tablonun satır grupları RowGroups özelliği aracılığıyla denetlemek</span><span class="sxs-lookup"><span data-stu-id="4ad95-126">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
