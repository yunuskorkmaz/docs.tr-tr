---
title: TextElement İçerik Modeline Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], flow documents
- TextElement content model [WPF]
- flow content elements [WPF], TextElement content model
ms.assetid: d0a7791c-b090-438c-812f-b9d009d83ee9
ms.openlocfilehash: 21df7228f8dca884c5f36be23ae1aced7b31cc9a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942212"
---
# <a name="textelement-content-model-overview"></a>TextElement İçerik Modeline Genel Bakış
Bu içerik modeline genel bakış, için <xref:System.Windows.Documents.TextElement>desteklenen içeriği açıklar. <xref:System.Windows.Documents.Paragraph> Sınıfı bir <xref:System.Windows.Documents.TextElement>türüdür. Bir içerik modeli, hangi nesnelerin/öğelerin başkaları tarafından içerildiğini açıklar. Bu genel bakışta, öğesinden <xref:System.Windows.Documents.TextElement>türetilmiş nesneler için kullanılan içerik modeli özetlenmektedir. Daha fazla bilgi için bkz. [Flow belgesine genel bakış](flow-document-overview.md).  

<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>İçerik modeli diyagramı  
 Aşağıdaki diyagramda, ' den <xref:System.Windows.Documents.TextElement> türetilen sınıfların içerik modeli ve diğer `TextElement` sınıfların bu modele nasıl sığması özetlenmektedir.  
  
 ![Çizimindeki Flow içerik kapsama şeması](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 Önceki diyagramdan görünebileceği gibi, bir öğe için izin verilen alt öğeler, bir sınıfın <xref:System.Windows.Documents.Block> sınıftan mı yoksa bir <xref:System.Windows.Documents.Inline> sınıftan mi türetilmediği tarafından belirlenmeyebilir. Örneğin <xref:System.Windows.Documents.Span> , bir (bir <xref:System.Windows.Documents.Inline>türetilmiş sınıf) yalnızca <xref:System.Windows.Documents.Inline>alt öğelere sahip <xref:System.Windows.Documents.Inline> olabilir, ancak bir <xref:System.Windows.Documents.Figure> (Ayrıca,-türetilmiş sınıf) yalnızca <xref:System.Windows.Documents.Block> alt öğeleri olabilir. Bu nedenle, bir diyagram, başka bir öğenin hangi öğeye dahil edilebilir olduğunu hızlı bir şekilde belirlemek için faydalıdır. Örnek olarak, ' ın <xref:System.Windows.Controls.RichTextBox>akış içeriğinin nasıl oluşturulacağını öğrenmek için diyagramı kullanalım.  
  
1. , ' In bir <xref:System.Windows.Documents.FlowDocument> iletüretilmişnesneiçermesigerekenbiriçermelidir.<xref:System.Windows.Documents.Block> <xref:System.Windows.Controls.RichTextBox> Yukarıdaki diyagramda karşılık gelen segment aşağıda verilmiştir.  
  
     ![Çizimindeki RichTextBox kapsama kuralları](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     Bu nedenle, biçimlendirmenin şu şekilde görünebileceğini burada bulabilirsiniz.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2. Diyagrama göre,,, <xref:System.Windows.Documents.Block> , ve <xref:System.Windows.Documents.Section> <xref:System.Windows.Documents.Table> <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.List>dahil olmaküzereseçebileceğinizbirkaçöğevardır(öncekidiyagramdabloktüretilmişsınıflarabakın).<xref:System.Windows.Documents.BlockUIContainer> Diyelim ki bir <xref:System.Windows.Documents.Table>. <xref:System.Windows.Documents.Table> Önceki diyagrama göre, bir <xref:System.Windows.Documents.TableRow> <xref:System.Windows.Documents.TableRowGroup> içerenöğeleri<xref:System.Windows.Documents.Block>içeren öğeleri içeren bir öğesi içerir.<xref:System.Windows.Documents.TableCell> Aşağıda, önceki diyagramdan <xref:System.Windows.Documents.Table> alınan karşılık gelen segment verilmiştir.  
  
     ![Çizimindeki &#47;Tablo](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2") için üst alt şema  
  
     Karşılık gelen biçimlendirme aşağıda verilmiştir.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3. Yine, bir veya daha <xref:System.Windows.Documents.Block> fazla öğe bir <xref:System.Windows.Documents.TableCell>altında gereklidir. Basit hale getirmek için hücrenin içine biraz metin yerleştirelim. Bunu bir <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Run> öğesi ile kullanarak yapabiliriz. Aşağıda <xref:System.Windows.Documents.Paragraph> , bir <xref:System.Windows.Documents.Inline> öğesinin bir öğe <xref:System.Windows.Documents.Run> ( <xref:System.Windows.Documents.Inline> bir öğe) yalnızca düz metin alabilir olduğunu gösteren diyagramda karşılık gelen segmentler verilmiştir.  
  
     ![Çizimindeki &#47;Paragraf](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3") için üst alt şema  
  
     ![Çizimindeki &#47;Run](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4") için üst alt şema  
  
 Biçimlendirme içindeki tüm örnek aşağıda verilmiştir.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>Programlı olarak TextElement Içeriğiyle çalışma  
 A <xref:System.Windows.Documents.TextElement> 'nın içeriği koleksiyonlar tarafından yapılır ve böylece bu koleksiyonlar ile çalışarak <xref:System.Windows.Documents.TextElement> nesne içeriğini programlı olarak işleme yapılır. Türetilmiş sınıflar tarafından <xref:System.Windows.Documents.TextElement> kullanılan üç farklı koleksiyon vardır:  
  
- <xref:System.Windows.Documents.InlineCollection>: Bir <xref:System.Windows.Documents.Inline> öğe koleksiyonunu temsil eder. <xref:System.Windows.Documents.InlineCollection><xref:System.Windows.Documents.Paragraph> ,<xref:System.Windows.Documents.Span>, ve<xref:System.Windows.Controls.TextBlock> öğelerinin izin verilen alt içeriğini tanımlar.  
  
- <xref:System.Windows.Documents.BlockCollection>: Bir <xref:System.Windows.Documents.Block> öğe koleksiyonunu temsil eder. <xref:System.Windows.Documents.BlockCollection><xref:System.Windows.Documents.FlowDocument> ,<xref:System.Windows.Documents.Section> ,,<xref:System.Windows.Documents.Figure> , ve öğelerinin izin verilen alt içeriğini tanımlar. <xref:System.Windows.Documents.ListItem> <xref:System.Windows.Documents.TableCell> <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.ListItemCollection>: Sıralı veya sırasız <xref:System.Windows.Documents.List>bir şekilde belirli bir içerik öğesini temsil eden bir akış içerik öğesi.  
  
 **Inlines**, **Blocks**ve **ListItems**öğelerinin ilgili özelliklerini kullanarak bu koleksiyonlardan öğe işleyebilir (öğeleri ekleyebilir veya kaldırabilirsiniz). Aşağıdaki örneklerde, **Inlines** özelliğini kullanarak bir yayılma içeriğinin nasıl kullanılacağı gösterilmektedir.  
  
> [!NOTE]
> Tablo, içeriğini işlemek için çeşitli koleksiyonlar kullanır, ancak burada kapsanmaz. Daha fazla bilgi için bkz. [tabloya genel bakış](table-overview.md).  
  
 Aşağıdaki örnek, yeni <xref:System.Windows.Documents.Span> bir nesne oluşturur ve sonra ' nin içerik alt öğesi <xref:System.Windows.Documents.Span>olarak iki metin çalıştırması eklemek için `Add` yöntemini kullanır.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 Aşağıdaki örnek yeni <xref:System.Windows.Documents.Run> bir öğesi oluşturur ve <xref:System.Windows.Documents.Span>öğesinin başlangıcına ekler.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 Aşağıdaki örnek, <xref:System.Windows.Documents.Inline> <xref:System.Windows.Documents.Span>içindeki son öğeyi siler.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 Aşağıdaki örnek,<xref:System.Windows.Documents.Inline> <xref:System.Windows.Documents.Span>içindeki tüm içeriği (öğeleri) temizler.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>Bu Içerik modelini paylaşan türler  
 Aşağıdaki türler <xref:System.Windows.Documents.TextElement> sınıftan devralınır ve bu genel bakışta açıklanan içeriği göstermek için kullanılabilir.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Bu listenin yalnızca ile [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]dağıtılan soyut olmayan türler içerdiğini unutmayın. Öğesinden <xref:System.Windows.Documents.TextElement>devraldığı diğer türleri kullanabilirsiniz.  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>TextElement nesneleri Içerebilen türler  
 Bkz. [WPF Içerik modeli](../controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [FlowDocument'ı Blokların Özelliği ile Düzenleme](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Akış İçeriği Öğelerini Blokların Özelliği ile Düzenleme](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [FlowDocument'ı Blokların Özelliği ile Düzenleme](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Sütunlar Özelliği Aracılığıyla bir Tablonun Sütunlarını Düzenleme](how-to-manipulate-table-columns-through-the-columns-property.md)
- [RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
