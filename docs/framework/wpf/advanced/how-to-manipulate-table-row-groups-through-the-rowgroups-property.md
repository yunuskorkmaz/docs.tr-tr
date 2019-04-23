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
ms.openlocfilehash: edc5fbe552a04387fc3f152cb53444605d142624
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209976"
---
# <a name="how-to-manipulate-a-tables-row-groups-through-the-rowgroups-property"></a>Nasıl yapılır: RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme
Bu örnekte aracılığıyla bir tablonun satır gruplarını gerçekleştirilebilir daha yaygın işlemleri bazılarını göstermektedir <xref:System.Windows.Documents.Table.RowGroups%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir tablo oluşturur ve ardından <xref:System.Windows.Documents.TableRowGroupCollection.Add%2A> tablonun sütunlar eklemek yöntemi <xref:System.Windows.Documents.Table.RowGroups%2A> koleksiyonu.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Add](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_add)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Add](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_add)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir ekler <xref:System.Windows.Documents.TableRowGroup>.  Yeni ilk satırın yapmadan dizin konumunda 0, yeni bir sütun eklenir tablo grubu.  
  
> [!NOTE]
>  <xref:System.Windows.Documents.TableRowGroupCollection> Koleksiyonun kullandığı standart sıfır tabanlı dizin.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Insert](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_insert)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Insert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_insert)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, belirli bir birkaç satır ekler <xref:System.Windows.Documents.TableRowGroup> (dizin tarafından belirtilen) tablosunda.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddRows](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addrows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddRows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addrows)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ilk satır grubu tablodaki satırlar üzerinde rastgele bazı özelliklere erişir.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipRows](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_maniprows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipRows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_maniprows)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, belirli bir birkaç hücre ekler <xref:System.Windows.Documents.TableRow> (dizin tarafından belirtilen) tablosunda.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddCells](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddCells](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addcells)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, rastgele yöntemler ve Özellikler ilk satırda ilk satır grubu hücrelerde erişin.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipCells](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_manipcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipCells](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_manipcells)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek sayısını döndürür <xref:System.Windows.Documents.TableRowGroup> tablo tarafından barındırılan öğeleri.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Count](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_count)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Count](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_count)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, belirli bir satır grubu tarafından başvuruyu kaldırır.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelRef](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delref)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelRef](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delref)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, belirli bir satır grubu dizine göre kaldırır.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delindex)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelIndex](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delindex)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm satır grupları tablonun satır gruplarını koleksiyondan kaldırır.  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Clear](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_clear)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Clear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_clear)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Akış içeriği öğelerini satır İçlerinin özelliği ile düzenleme](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [FlowDocument'ı Blokların Özelliği ile Düzenleme](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Sütunlar Özelliği Aracılığıyla bir Tablonun Sütunlarını Düzenleme](how-to-manipulate-table-columns-through-the-columns-property.md)
