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
# <a name="how-to-manipulate-a-table39s-columns-through-the-columns-property"></a>Nasıl yapılır: bir tablo &#39; işlemek sütunlar özelliği aracılığıyla s sütunları
Bu örnek bir tablonun sütunlar üzerinde gerçekleştirilen daha yaygın işlemlerin bazılarını göstermektedir <xref:System.Windows.Documents.Table.Columns%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir tablo oluşturur ve ardından <xref:System.Windows.Documents.TableColumnCollection.Add%2A> tablonun sütunlar ekleme yöntemi <xref:System.Windows.Documents.Table.Columns%2A> koleksiyonu.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir ekler <xref:System.Windows.Documents.TableColumn>.  Yeni bir sütun konumunda tablosunda yeni bir ilk sütun kolaylaştırarak dizin 0, eklenir.  
  
> [!NOTE]
>  <xref:System.Windows.Documents.TableColumnCollection> Koleksiyonu kullanan standart sıfır tabanlı dizin.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek sütunlar üzerinde bazı rasgele özelliklere erişir <xref:System.Windows.Documents.TableColumnCollection> dizini tarafından belirli sütunlara başvuran koleksiyonu.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek şu anda tablo tarafından barındırılan sütun sayısını alır.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte belirli bir sütuna başvuru tarafından kaldırılır.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, belirli bir sütun dizini tarafından kaldırılır.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm sütunlar tablonun sütunlar koleksiyonundan kaldırır.  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tablo genel bakış](../../../../docs/framework/wpf/advanced/table-overview.md)  
 [XAML içeren bir tablo tanımlayın](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)  
 [Programlı olarak bir tablo oluşturma](../../../../docs/framework/wpf/advanced/how-to-build-a-table-programmatically.md)  
 [Tablonun satır grupları RowGroups özelliği aracılığıyla denetlemek](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)  
 [Blokların özelliği aracılığıyla FlowDocument işlemek](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [Tablonun satır grupları RowGroups özelliği aracılığıyla denetlemek](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
