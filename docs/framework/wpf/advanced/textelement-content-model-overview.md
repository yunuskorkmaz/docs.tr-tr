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
ms.openlocfilehash: ddb2613dc924424b5f4b9d90f06d44b45b7b5e77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186900"
---
# <a name="textelement-content-model-overview"></a>TextElement İçerik Modeline Genel Bakış
Bu içerik modeline genel bakış, <xref:System.Windows.Documents.TextElement>bir . Sınıf <xref:System.Windows.Documents.Paragraph> bir tür <xref:System.Windows.Documents.TextElement>. İçerik modeli, hangi nesnelerin/öğelerin başkalarında bulunabileceğini açıklar. Bu genel bakış, türetilen nesneler için <xref:System.Windows.Documents.TextElement>kullanılan içerik modelini özetler. Daha fazla bilgi için [Akış Belgesine Genel Bakış'a](flow-document-overview.md)bakın.  

<a name="text_element_classes"></a>
## <a name="content-model-diagram"></a>İçerik Modeli Diyagramı  
 Aşağıdaki diyagram, türetilen sınıfların içerik <xref:System.Windows.Documents.TextElement> modelini ve `TextElement` diğer sınıf dışı sınıfların bu modele nasıl uyduğunu özetleyilmiştir.  
  
 ![Diyagram: Akış içeriği içeren şema](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 Önceki diyagramdan da görüleceği gibi, bir öğe için izin verilen alt öğe, bir <xref:System.Windows.Documents.Block> sınıfın <xref:System.Windows.Documents.Inline> sınıftan mı yoksa sınıftan mı türetildiğine göre belirlenmez. Örneğin, (türetilmiş <xref:System.Windows.Documents.Span> bir <xref:System.Windows.Documents.Inline>sınıf) <xref:System.Windows.Documents.Inline> yalnızca alt öğelere sahip olabilir, ancak (türetilmiş <xref:System.Windows.Documents.Figure> bir <xref:System.Windows.Documents.Inline>sınıf) yalnızca alt öğelere sahip <xref:System.Windows.Documents.Block> olabilir. Bu nedenle, bir diyagram, başka bir öğenin içinde bulunabileceğini hızlı bir şekilde belirlemek için yararlıdır. Örnek olarak, bir <xref:System.Windows.Controls.RichTextBox>'nin akış içeriğini nasıl oluşturabildiğini belirlemek için diyagramı kullanalım.  
  
1. A <xref:System.Windows.Controls.RichTextBox> sırayla <xref:System.Windows.Documents.FlowDocument> bir <xref:System.Windows.Documents.Block>-türetilmiş nesne içermelidir. Aşağıdaki önceki diyagramdan karşılık gelen segmenttir.  
  
     ![Diyagram: RichTextBox çevreleme kuralları](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     Şimdiye kadar, bu biçimlendirme gibi görünebilir.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2. Diyagrama göre, <xref:System.Windows.Documents.Block> <xref:System.Windows.Documents.Paragraph>, , , <xref:System.Windows.Documents.Section> <xref:System.Windows.Documents.Table> <xref:System.Windows.Documents.List>, , ve <xref:System.Windows.Documents.BlockUIContainer> (bkz. önceki diyagramda Blok türetilmiş sınıflar) dahil olmak üzere seçim için çeşitli öğeler vardır. Diyelim ki. <xref:System.Windows.Documents.Table> Önceki diyagrama göre, <xref:System.Windows.Documents.Table> a-türetilmiş nesne <xref:System.Windows.Documents.TableCell> içeren öğeleri <xref:System.Windows.Documents.Block>içeren bir <xref:System.Windows.Documents.TableRowGroup> içeren <xref:System.Windows.Documents.TableRow> öğeler içerir. Aşağıda, önceki diyagramdan <xref:System.Windows.Documents.Table> alınan karşılık gelen kesim verilmiştir.  
  
     ![Diyagram: Tablo için alt&#47;alt şema](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     Aşağıdaki karşılık gelen biçimlendirme olduğunu.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3. Yine, bir <xref:System.Windows.Documents.Block> veya daha fazla <xref:System.Windows.Documents.TableCell>öğe nin altında gereklidir. Basit hale getirmek için, hücrenin içine biraz metin yerleştirelim. Bunu bir <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Run> elementle yapabiliriz. Aşağıdaki, diyagramdan <xref:System.Windows.Documents.Paragraph> bir <xref:System.Windows.Documents.Inline> öğeyi alabileceğinizi ve bir <xref:System.Windows.Documents.Run> (bir <xref:System.Windows.Documents.Inline> öğe) yalnızca düz metin alabileceğinizi gösteren karşılık gelen segmentler verilmiştir.  
  
     ![Diyagram: Paragraf için alt&#47;alt şema](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![Diyagram: Run için Üst&#47;Çocuk şeması](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Aşağıdaki biçimlendirme tüm örnektir.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>
## <a name="working-with-textelement-content-programmatically"></a>TextElement İçeriği ile Programlı Çalışma  
 A'nın <xref:System.Windows.Documents.TextElement> içeriği koleksiyonlardan oluşur ve böylece <xref:System.Windows.Documents.TextElement> nesnelerin içeriğini programlı bir şekilde manipüle etmek bu koleksiyonlarla çalışarak yapılır. -türetilmiş sınıflar tarafından <xref:System.Windows.Documents.TextElement> kullanılan üç farklı koleksiyon vardır:  
  
- <xref:System.Windows.Documents.InlineCollection>: Elementlerin <xref:System.Windows.Documents.Inline> bir koleksiyonunu temsil eder. <xref:System.Windows.Documents.InlineCollection><xref:System.Windows.Documents.Paragraph>, , <xref:System.Windows.Documents.Span>ve <xref:System.Windows.Controls.TextBlock> öğelerin izin verilebilir alt içeriğini tanımlar.  
  
- <xref:System.Windows.Documents.BlockCollection>: Elementlerin <xref:System.Windows.Documents.Block> bir koleksiyonunu temsil eder. <xref:System.Windows.Documents.BlockCollection><xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.ListItem> <xref:System.Windows.Documents.TableCell>, , <xref:System.Windows.Documents.Floater>, ve <xref:System.Windows.Documents.Figure> öğelerin izin verilebilir alt içeriğini tanımlar.  
  
- <xref:System.Windows.Documents.ListItemCollection>: Belirli bir içerik öğesini sıralı veya sıralanmamış <xref:System.Windows.Documents.List>bir öğede temsil eden akış içeriği öğesi.  
  
 **İç Çizgiler**, **Bloklar**ve **ListItems'ın**ilgili özelliklerini kullanarak bu koleksiyonlardan öğe leri işleyebilir (öğe ekleyebilir veya kaldırabilirsiniz). Aşağıdaki örnekler, **Inlines** özelliğini kullanarak Bir Yayılma Alanının içeriğini nasıl manipüle edileteceğimi gösterir.  
  
> [!NOTE]
> Tablo içeriğini işlemek için çeşitli koleksiyonlar kullanır, ancak burada kapsamda değildir. Daha fazla bilgi için [Tabloya Genel Bakış'a](table-overview.md)bakın.  
  
 Aşağıdaki örnekte yeni <xref:System.Windows.Documents.Span> bir nesne oluşturulur `Add` ve sonra iki metin eklemek için <xref:System.Windows.Documents.Span>yöntemi kullanır.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 Aşağıdaki örnek yeni <xref:System.Windows.Documents.Run> bir öğe oluşturur ve <xref:System.Windows.Documents.Span>'nin başına ekler.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 Aşağıdaki örnekte <xref:System.Windows.Documents.Inline> <xref:System.Windows.Documents.Span>son öğe siler.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 Aşağıdaki örnek, tüm içeriğini (öğeleri)<xref:System.Windows.Documents.Inline> temizler. <xref:System.Windows.Documents.Span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>
## <a name="types-that-share-this-content-model"></a>Bu İçerik Modelini Paylaşan Türler  
 Aşağıdaki türler <xref:System.Windows.Documents.TextElement> sınıftan devralır ve bu genel bakışta açıklanan içeriği görüntülemek için kullanılabilir.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Bu listenin yalnızca Windows SDK ile dağıtılan soyut olmayan türleri içerdiğini unutmayın. 'den <xref:System.Windows.Documents.TextElement>devralan diğer türleri kullanabilirsiniz.  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>
## <a name="types-that-can-contain-textelement-objects"></a>TextElement Nesnelerini İçerebilecek Türler  
 [Bkz. WPF İçerik Modeli.](../controls/wpf-content-model.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [FlowDocument'ı Blokların Özelliği ile Düzenleme](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Akış İçeriği Öğelerini Blokların Özelliği ile Düzenleme](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [FlowDocument'ı Blokların Özelliği ile Düzenleme](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Sütunlar Özelliği Aracılığıyla bir Tablonun Sütunlarını Düzenleme](how-to-manipulate-table-columns-through-the-columns-property.md)
- [RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
