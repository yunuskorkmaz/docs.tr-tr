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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051474"
---
# <a name="how-to-manipulate-a-tables-columns-through-the-columns-property"></a>Nasıl yapılır: Sütunlar Özelliği Aracılığıyla bir Tablonun Sütunlarını Düzenleme
Bu örnekte aracılığıyla bir tablonun sütunlarını gerçekleştirilebilir daha yaygın işlemleri bazılarını göstermektedir <xref:System.Windows.Documents.Table.Columns%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir tablo oluşturur ve ardından <xref:System.Windows.Documents.TableColumnCollection.Add%2A> tablonun sütunlar eklemek yöntemi <xref:System.Windows.Documents.Table.Columns%2A> koleksiyonu.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir ekler <xref:System.Windows.Documents.TableColumn>.  Konumunda yeni bir ilk sütun tabloda getirerek dizin 0, yeni bir sütun eklenir.  
  
> [!NOTE]
>  <xref:System.Windows.Documents.TableColumnCollection> Koleksiyonun kullandığı standart sıfır tabanlı dizin.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek rastgele bazı özellikler sütunlarında erişen <xref:System.Windows.Documents.TableColumnCollection> belirli sütunları dizine göre başvuran koleksiyonu.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tablo tarafından şu anda barındırılan sütunların sayısını alır.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, belirli bir sütuna göre başvuruyu kaldırır.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, belirli bir sütuna dizin tarafından kaldırılır.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm sütunları tablonun sütun koleksiyondan kaldırır.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tabloya Genel Bakış](table-overview.md)
- [XAML ile Tablo Tanımlama](how-to-define-a-table-with-xaml.md)
- [Program Aracılığıyla Tablo Oluşturma](how-to-build-a-table-programmatically.md)
- [RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [FlowDocument'ı Blokların Özelliği ile Düzenleme](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
