---
title: "Nasıl yapılır: FlowDocument'ı Blokların Özelliği ile Düzenleme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'documents [WPF], manipulating FlowDocuments through Blocks property [WPF], , '
- ', '
ms.assetid: cbb7291e-3f1b-433e-9e16-f4d93ced14e8
ms.openlocfilehash: c307d85bf24e2d8a20226856181e0758758d40c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051513"
---
# <a name="how-to-manipulate-a-flowdocument-through-the-blocks-property"></a>Nasıl yapılır: FlowDocument'ı Blokların Özelliği ile Düzenleme
Bu örnekler üzerinde gerçekleştirilen işlemleri daha yaygın bazılarını gösterir bir <xref:System.Windows.Documents.FlowDocument> aracılığıyla <xref:System.Windows.Documents.FlowDocument.Blocks%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir oluşturur <xref:System.Windows.Documents.FlowDocument> ve ardından yeni bir ekler <xref:System.Windows.Documents.Paragraph> öğesine <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksadd)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksadd)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir oluşturur <xref:System.Windows.Documents.Paragraph> öğesi ve başında ekler <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksinsert)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksinsert)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, üst düzey sayısını alır. <xref:System.Windows.Documents.Block> içindeki öğe <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksCount](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblockscount)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksCount](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblockscount)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, son silinir <xref:System.Windows.Documents.Block> öğesinde <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksremovelast)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksremovelast)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek içeriğinin tamamını temizler (<xref:System.Windows.Documents.Block> öğeleri) öğesinden <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksClear](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksclear)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksclear)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [Sütunlar Özelliği Aracılığıyla bir Tablonun Sütunlarını Düzenleme](how-to-manipulate-table-columns-through-the-columns-property.md)
- [RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
