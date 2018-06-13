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
ms.openlocfilehash: 74710c4a6dd58cf2836cd7671a3e39401a5ea774
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544556"
---
# <a name="how-to-manipulate-flow-content-elements-through-the-blocks-property"></a>Nasıl yapılır: Akış İçeriği Öğelerini Blokların Özelliği ile Düzenleme
Bu örneklerin üzerinden akış içerik öğelerinde gerçekleştirilen daha yaygın işlemlerin bazılarını göstermek **blokları** özelliği. Bu özellik eklemek ve öğeleri kaldırmak için kullanılan <xref:System.Windows.Documents.BlockCollection>. Akış içerik öğeleri bu özellik bir **blokları** özellik içerir:  
  
-   <xref:System.Windows.Documents.Figure>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.ListItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
 Kullanmak için bu örnekler durum <xref:System.Windows.Documents.Section> akış halinde content öğesi, ancak bu teknikler akış içerik öğe koleksiyonu barındıran tüm öğeler için geçerlidir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir oluşturur <xref:System.Windows.Documents.Section> ve ardından **Ekle** için yeni bir paragraf ekleme yöntemi **bölüm** içeriği.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir oluşturur <xref:System.Windows.Documents.Paragraph> öğesi ve başında ekler <xref:System.Windows.Documents.Section>.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksinsert)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksinsert)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek en üst düzey sayısını alır <xref:System.Windows.Documents.Block> içindeki öğe <xref:System.Windows.Documents.Section>.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksCount](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblockscount)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksCount](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblockscount)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, son siler <xref:System.Windows.Documents.Block> öğesinde <xref:System.Windows.Documents.Section>.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksremovelast)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksremovelast)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte tüm içeriği siler (<xref:System.Windows.Documents.Block> öğeleri) gelen <xref:System.Windows.Documents.Section>.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksclear)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksclear)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Documents.BlockCollection>  
 <xref:System.Windows.Documents.InlineCollection>  
 <xref:System.Windows.Documents.ListItemCollection>  
 [Akış Belgesine Genel Bakış](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)  
 [Sütunlar Özelliği Aracılığıyla bir Tablonun Sütunlarını Düzenleme](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)  
 [RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
