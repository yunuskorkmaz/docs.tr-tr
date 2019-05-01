---
title: 'Nasıl yapılır: Akış İçeriği Öğelerini Blokların Özelliği ile Düzenleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], manipulating flow content elements through Blocks property
- flow content elements [WPF], manipulating through Blocks property
- properties [WPF], Blocks [WPF], manipulating flow content elements
- Blocks property [WPF], manipulating flow content elements
ms.assetid: aeda4ece-b979-4818-a093-ef938e908751
ms.openlocfilehash: e0e1e1333a54946f3bdf474e353de0301eb42447
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942837"
---
# <a name="how-to-manipulate-flow-content-elements-through-the-blocks-property"></a>Nasıl yapılır: Akış İçeriği Öğelerini Blokların Özelliği ile Düzenleme
Akış içeriği öğelerini gerçekleştirilebilir daha yaygın işlemlerin bazıları bu örneklerde görüldüğü **blokları** özelliği. Bu özellik öğesinden öğeleri eklemek ve kaldırmak için kullanılan <xref:System.Windows.Documents.BlockCollection>. Akış içerik öğeleri bu özellik bir **blokları** özellik içerir:  
  
- <xref:System.Windows.Documents.Figure>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.ListItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.TableCell>  
  
 Kullanmak için bu örnekleri meydana <xref:System.Windows.Documents.Section> akışı olarak içerik öğesi, ancak bu tekniklerin bir akış içerik öğe koleksiyonu barındıran tüm öğeler için geçerlidir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir oluşturur <xref:System.Windows.Documents.Section> ve ardından **Ekle** yöntemi yeni bir paragrafa eklemek için **bölümü** içeriği.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir oluşturur <xref:System.Windows.Documents.Paragraph> öğesi ve başında ekler <xref:System.Windows.Documents.Section>.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksinsert)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksinsert)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, üst düzey sayısını alır. <xref:System.Windows.Documents.Block> içindeki öğe <xref:System.Windows.Documents.Section>.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksCount](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblockscount)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksCount](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblockscount)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, son silinir <xref:System.Windows.Documents.Block> öğesinde <xref:System.Windows.Documents.Section>.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksremovelast)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksremovelast)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek içeriğinin tamamını temizler (<xref:System.Windows.Documents.Block> öğeleri) öğesinden <xref:System.Windows.Documents.Section>.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksClear](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksclear)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksclear)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Documents.BlockCollection>
- <xref:System.Windows.Documents.InlineCollection>
- <xref:System.Windows.Documents.ListItemCollection>
- [Akış Belgesine Genel Bakış](flow-document-overview.md)
- [RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [Sütunlar Özelliği Aracılığıyla bir Tablonun Sütunlarını Düzenleme](how-to-manipulate-table-columns-through-the-columns-property.md)
- [RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
