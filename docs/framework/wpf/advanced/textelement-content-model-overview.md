---
title: "TextElement İçerik Modeline Genel Bakış"
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
- documents [WPF], flow documents
- TextElement content model [WPF]
- flow content elements [WPF], TextElement content model
ms.assetid: d0a7791c-b090-438c-812f-b9d009d83ee9
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81f95ea4582230fe66c59655ab9b98a405c1e173
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="textelement-content-model-overview"></a>TextElement İçerik Modeline Genel Bakış
Bu içerik modeli genel bakış için desteklenen içeriğini açıklayan bir <xref:System.Windows.Documents.TextElement>. <xref:System.Windows.Documents.Paragraph> Sınıfı, bir tür <xref:System.Windows.Documents.TextElement>. İçerik modeli, hangi nesnelerin/öğelerin bazılarında bulunabilir açıklar. Bu genel bakışta türetilen nesneler için kullanılan içerik modelini özetler <xref:System.Windows.Documents.TextElement>. Daha fazla bilgi için bkz: [akış belge genel bakış](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
  
<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>İçerik modeli diyagramı  
 Türetilmiş sınıflar için aşağıdaki diyagramda içerik modelini özetler <xref:System.Windows.Documents.TextElement> yanı sıra nasıl diğer olmayan `TextElement` Bu modele uygun sınıfları.  
  
 ![Diyagram: Akış içeriği kapsama şeması](../../../../docs/framework/wpf/advanced/media/flow-content-schema.png "Flow_Content_Schema")  
  
 Önceki diyagramdan görüldüğü gibi bir öğe için izin verilen alt öğe mutlaka olup bir sınıfın türetildiği tarafından belirlenmiş olmak zorunda değildir <xref:System.Windows.Documents.Block> sınıfı veya bir <xref:System.Windows.Documents.Inline> sınıfı. Örneğin, bir <xref:System.Windows.Documents.Span> (bir <xref:System.Windows.Documents.Inline>-türetilmiş sınıf) yalnızca olabilir <xref:System.Windows.Documents.Inline> alt öğeleri, ancak bir <xref:System.Windows.Documents.Figure> (aynı zamanda bir <xref:System.Windows.Documents.Inline>-türetilmiş sınıf) yalnızca olabilir <xref:System.Windows.Documents.Block> alt öğeleri. Bu nedenle, bir diyagram hangi öğe başka bir programda bulunabilir hızla belirlemede yararlıdır. Örnek olarak, diyagram oluşturma akış içeriğini belirlemek için kullanalım bir <xref:System.Windows.Controls.RichTextBox>.  
  
1.  A <xref:System.Windows.Controls.RichTextBox> içermesi gereken bir <xref:System.Windows.Documents.FlowDocument> hangi sırayla içermesi gerekir bir <xref:System.Windows.Documents.Block>-türetilmiş bir nesne içermelidir. Yukarıdaki diyagramdan karşılık gelen kesim aşağıdadır.  
  
     ![Diyagram: RichTextBox kapsama kuralları](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     Bugüne kadarki biçimlendirmeyi aşağıdaki gibi görünmelidir budur.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2.  Aşağıdaki diyagramda göre birkaç yolu vardır <xref:System.Windows.Documents.Block> dahil olmak üzere seçmek için öğeleri <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List>, ve <xref:System.Windows.Documents.BlockUIContainer> (önceki diyagramda blok türetilmiş sınıflara bakın). İstiyoruz diyelim bir <xref:System.Windows.Documents.Table>. Önceki diyagramda göre bir <xref:System.Windows.Documents.Table> içeren bir <xref:System.Windows.Documents.TableRowGroup> içeren <xref:System.Windows.Documents.TableRow> içeren öğeleri <xref:System.Windows.Documents.TableCell> içeren öğeleri bir <xref:System.Windows.Documents.Block>-türetilmiş bir nesne içermelidir. İçin karşılık gelen kesim aşağıdadır <xref:System.Windows.Documents.Table> önceki diyagramdan gerçekleştirilecek.  
  
     ![Diyagram: Üst &#47;/; alt tablo için şema](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     Karşılık gelen biçimlendirme aşağıdadır.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3.  Yeniden, bir veya daha fazla <xref:System.Windows.Documents.Block> altında gerekli öğelerden bir <xref:System.Windows.Documents.TableCell>. Basit hale getirmek için şirketinizdeki bazı metinleri hücresinin içine koyun. Bu kullanarak yapabiliriz bir <xref:System.Windows.Documents.Paragraph> ile bir <xref:System.Windows.Documents.Run> öğesi. Gösteren diyagramdan karşılık gelen kesim aşağıdadır bir <xref:System.Windows.Documents.Paragraph> gerçekleştirebileceğiniz bir <xref:System.Windows.Documents.Inline> öğesi ve, bir <xref:System.Windows.Documents.Run> (bir <xref:System.Windows.Documents.Inline> öğesi) yalnızca düz metin alabilir.  
  
     ![Diyagram: Üst &#47;/; paragraf için alt şema](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![Diyagram: Üst &#47; Çalışma için alt şema](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Tüm biçimlendirme örneği verilmiştir.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>TextElement içerikle program aracılığıyla çalışma  
 İçeriği bir <xref:System.Windows.Documents.TextElement> koleksiyonları ve bunu programlı olarak içeriğini düzenleme oluşur <xref:System.Windows.Documents.TextElement> nesneler, bu koleksiyonlarla çalışarak yapılır. Tarafından kullanılan üç farklı koleksiyon vardır <xref:System.Windows.Documents.TextElement> -türetilmiş sınıfları:  
  
-   <xref:System.Windows.Documents.InlineCollection>: Bir koleksiyonunu temsil eder <xref:System.Windows.Documents.Inline> öğeleri. <xref:System.Windows.Documents.InlineCollection>izin verilen alt öğe içeriğini tanımlar <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Span>, ve <xref:System.Windows.Controls.TextBlock> öğeleri.  
  
-   <xref:System.Windows.Documents.BlockCollection>: Bir koleksiyonunu temsil eder <xref:System.Windows.Documents.Block> öğeleri. <xref:System.Windows.Documents.BlockCollection>izin verilen alt öğe içeriğini tanımlar <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.TableCell>, <xref:System.Windows.Documents.Floater>, ve <xref:System.Windows.Documents.Figure> öğeleri.  
  
-   <xref:System.Windows.Documents.ListItemCollection>: Sıralı içindeki belirli bir içerik öğesini temsil eder bir akış içerik öğesi veya sırasız <xref:System.Windows.Documents.List>.  
  
 Yönetebilirsiniz (öğeler ekleme veya kaldırma) ilgili özelliklerini kullanarak bu koleksiyonlardan **Inlines**, **blokları**, ve **ListItems**. Aşağıdaki örnekler bir aralık kullanarak içindekiler işlemek nasıl **Inlines** özelliği.  
  
> [!NOTE]
>  Tablo içeriğini işlemek için birkaç koleksiyon kullanır, ancak burada incelenmemiştir. Daha fazla bilgi için bkz: [tablo genel bakışı](../../../../docs/framework/wpf/advanced/table-overview.md).  
  
 Aşağıdaki örnek yeni bir oluşturur <xref:System.Windows.Documents.Span> nesne ve kullandığı `Add` içerik alt öğeleri olarak çalışan iki metin eklemek için yöntemini <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 Aşağıdaki örnek yeni bir oluşturur <xref:System.Windows.Documents.Run> öğesi ve başında ekler <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 Aşağıdaki örnek, son siler <xref:System.Windows.Documents.Inline> öğesinde <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 Aşağıdaki örnekte tüm içeriği siler (<xref:System.Windows.Documents.Inline> öğeleri) gelen <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>Bu içerik modeli paylaşmak türleri  
 Aşağıdaki türlerden devralınmalıdır <xref:System.Windows.Documents.TextElement> sınıfı ve bu genel bakışta açıklanan içeriği görüntülemek için kullanılabilir.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Bu liste yalnızca soyut türleri ile dağıtılmış içerdiğine dikkat [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]. Devralınan diğer türleri kullanabilirsiniz <xref:System.Windows.Documents.TextElement>.  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>TextElement nesnelerini içeren türleri  
 Bkz: [WPF içerik modeli](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Blokların özelliği aracılığıyla FlowDocument işlemek](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [Akış içeriği öğeleri blokların özelliği aracılığıyla düzenleme](../../../../docs/framework/wpf/advanced/how-to-manipulate-flow-content-elements-through-the-blocks-property.md)  
 [Blokların özelliği aracılığıyla FlowDocument işlemek](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [Bir tablonun sütunlar sütunlar özelliği aracılığıyla yönetmek](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)  
 [Tablonun satır grupları RowGroups özelliği aracılığıyla denetlemek](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
