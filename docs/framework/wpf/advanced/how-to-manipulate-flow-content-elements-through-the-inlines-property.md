---
title: 'Nasıl yapılır: Akış İçeriği Öğelerini Satır İçlerinin Özelliği ile Düzenleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], manipulating through Inlines property
- documents [WPF], manipulating flow Content elements through Inlines property
- Inlines property [WPF], manipulating flow Content elements
- properties [WPF], Inlines [WPF], manipulating flow Content elements
ms.assetid: 510780d2-3da1-4360-8763-7054bda22ea3
ms.openlocfilehash: 3bbeac2eda8811939be3c710a8ce28349e7f0759
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-manipulate-flow-content-elements-through-the-inlines-property"></a>Nasıl yapılır: Akış İçeriği Öğelerini Satır İçlerinin Özelliği ile Düzenleme
Bu örnekler satır içi akış içeriği öğeleri üzerinde gerçekleştirilen daha yaygın işlemlerin bazılarını gösterir (ve bu öğelerin kapsayıcıları gibi <xref:System.Windows.Controls.TextBlock>) aracılığıyla **Inlines** özelliği. Bu özellik eklemek ve öğeleri kaldırmak için kullanılan <xref:System.Windows.Documents.InlineCollection>. Akış içerik öğeleri bu özellik bir **Inlines** özellik içerir:  
  
-   <xref:System.Windows.Documents.Bold>  
  
-   <xref:System.Windows.Documents.Hyperlink>  
  
-   <xref:System.Windows.Documents.Italic>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Span>  
  
-   <xref:System.Windows.Documents.Underline>  
  
 Kullanmak için bu örnekler durum <xref:System.Windows.Documents.Span> akış halinde content öğesi, ancak bu teknikler tüm öğeleri veya ana bilgisayar denetimleri için geçerli bir <xref:System.Windows.Documents.InlineCollection> koleksiyonu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir oluşturur <xref:System.Windows.Documents.Span> nesne ve kullandığı **Ekle** içerik alt öğeleri olarak çalışan iki metin eklemek için yöntemini <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir oluşturur <xref:System.Windows.Documents.Run> öğesi ve başında ekler <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek en üst düzey sayısını alır <xref:System.Windows.Documents.Inline> içindeki öğe <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesCount](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinescount)]
 [!code-vb[SpanSnippets#_SpanInlinesCount](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinescount)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, son siler <xref:System.Windows.Documents.Inline> öğesinde <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte tüm içeriği siler (<xref:System.Windows.Documents.Inline> öğeleri) gelen <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Documents.BlockCollection>  
 <xref:System.Windows.Documents.InlineCollection>  
 <xref:System.Windows.Documents.ListItemCollection>  
 [Akış Belgesine Genel Bakış](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [FlowDocument'ı Blokların Özelliği ile Düzenleme](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [Sütunlar Özelliği Aracılığıyla bir Tablonun Sütunlarını Düzenleme](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)  
 [RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
