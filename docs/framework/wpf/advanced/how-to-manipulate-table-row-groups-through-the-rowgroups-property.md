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
# <a name="how-to-manipulate-a-tables-row-groups-through-the-rowgroups-property"></a>Nasıl yapılır: RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme
Bu örnek, <xref:System.Windows.Documents.Table.RowGroups%2A> özelliği aracılığıyla bir tablonun satır gruplarında gerçekleştirilebilecek daha yaygın işlemlerden bazılarını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir tablo oluşturur ve ardından <xref:System.Windows.Documents.TableRowGroupCollection.Add%2A> <xref:System.Windows.Documents.Table.RowGroups%2A> tablo koleksiyonuna sütun eklemek için yöntemini kullanır.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Add](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_add)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Add](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_add)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni <xref:System.Windows.Documents.TableRowGroup>bir ekler.  Yeni sütun, 0 dizin konumuna eklenir ve tablodaki yeni bir ilk satır grubu haline gelir.  
  
> [!NOTE]
> <xref:System.Windows.Documents.TableRowGroupCollection> Koleksiyon standart sıfır tabanlı dizin oluşturmayı kullanır.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Insert](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_insert)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Insert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_insert)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tablosuna belirli <xref:System.Windows.Documents.TableRowGroup> bir (dizinine göre belirtilen) birkaç satır ekler.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddRows](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addrows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddRows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addrows)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tablodaki ilk satır grubundaki satırlarda bazı rastgele özelliklere erişir.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipRows](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_maniprows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipRows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_maniprows)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tablodaki belirli <xref:System.Windows.Documents.TableRow> bir (dizinine göre belirtilen) için birkaç hücre ekler.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddCells](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddCells](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addcells)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ilk satır grubundaki ilk satırdaki hücrelerde bazı rastgele yöntemlere ve özelliklere erişir.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipCells](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_manipcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipCells](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_manipcells)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tablosunun barındırdığı <xref:System.Windows.Documents.TableRowGroup> öğe sayısını döndürür.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Count](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_count)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Count](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_count)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, belirli bir satır grubunu başvuruya göre kaldırır.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelRef](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delref)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelRef](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delref)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, belirli bir satır grubunu dizine göre kaldırır.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delindex)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelIndex](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delindex)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm satır gruplarını tablonun satır grupları koleksiyonundan kaldırır.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Clear](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_clear)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Clear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_clear)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Akış Içeriği öğelerini Inlines özelliği aracılığıyla işleme](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [FlowDocument'ı Blokların Özelliği ile Düzenleme](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Sütunlar Özelliği Aracılığıyla bir Tablonun Sütunlarını Düzenleme](how-to-manipulate-table-columns-through-the-columns-property.md)
