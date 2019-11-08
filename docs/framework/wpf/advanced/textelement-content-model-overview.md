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
ms.openlocfilehash: acd67dd870c6912eddc368bf674804d98dba2db8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740762"
---
# <a name="textelement-content-model-overview"></a>TextElement İçerik Modeline Genel Bakış
Bu içerik modeline genel bakış, <xref:System.Windows.Documents.TextElement>için desteklenen içeriği açıklar. <xref:System.Windows.Documents.Paragraph> sınıfı bir <xref:System.Windows.Documents.TextElement>türüdür. Bir içerik modeli, hangi nesnelerin/öğelerin başkaları tarafından içerildiğini açıklar. Bu genel bakışta, <xref:System.Windows.Documents.TextElement>türetilen nesneler için kullanılan içerik modeli özetlenmektedir. Daha fazla bilgi için bkz. [Flow belgesine genel bakış](flow-document-overview.md).  

<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>İçerik modeli diyagramı  
 Aşağıdaki diyagramda, <xref:System.Windows.Documents.TextElement> türetilen sınıfların içerik modeli ve `TextElement` olmayan diğer sınıfların bu modele nasıl sığması özetlenmektedir.  
  
 ![Diyagram: akış içeriği kapsama şeması](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 Önceki diyagramdan görünebileceği gibi, bir öğe için izin verilen alt öğeler, bir sınıfın <xref:System.Windows.Documents.Block> sınıfından mi yoksa bir <xref:System.Windows.Documents.Inline> sınıfından mi türetilmediği tarafından belirlenmemelidir. Örneğin, bir <xref:System.Windows.Documents.Span> (<xref:System.Windows.Documents.Inline>türetilmiş bir sınıf) yalnızca <xref:System.Windows.Documents.Inline> alt öğelerine sahip olabilir, ancak bir <xref:System.Windows.Documents.Figure> (Ayrıca <xref:System.Windows.Documents.Inline>türetilen bir sınıf) yalnızca <xref:System.Windows.Documents.Block> alt öğeleri olabilir. Bu nedenle, bir diyagram, başka bir öğenin hangi öğeye dahil edilebilir olduğunu hızlı bir şekilde belirlemek için faydalıdır. Örnek olarak, <xref:System.Windows.Controls.RichTextBox>akış içeriğinin nasıl oluşturulacağını öğrenmek için diyagramı kullanalım.  
  
1. <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Documents.Block>türetilmiş bir nesne içermesi gereken bir <xref:System.Windows.Documents.FlowDocument> içermelidir. Yukarıdaki diyagramda karşılık gelen segment aşağıda verilmiştir.  
  
     ![Diyagram: RichTextBox kapsama kuralları](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     Bu nedenle, biçimlendirmenin şu şekilde görünebileceğini burada bulabilirsiniz.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2. Diyagrama göre, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List>ve <xref:System.Windows.Documents.BlockUIContainer> dahil olmak üzere seçebileceğiniz birkaç <xref:System.Windows.Documents.Block> öğesi vardır (önceki diyagramda blok türetilmiş sınıflara bakın). <xref:System.Windows.Documents.Table>istediğinizi varsayalım. Önceki diyagrama göre <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Block>türetilmiş bir nesne içeren <xref:System.Windows.Documents.TableCell> öğeleri içeren <xref:System.Windows.Documents.TableRow> öğeleri içeren bir <xref:System.Windows.Documents.TableRowGroup> içerir. Aşağıda, önceki diyagramdan alınan <xref:System.Windows.Documents.Table> ilgili segment verilmiştir.  
  
     ![Diyagram: tablo&#47;için üst alt şema](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     Karşılık gelen biçimlendirme aşağıda verilmiştir.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3. Bir <xref:System.Windows.Documents.TableCell>altında bir veya daha fazla <xref:System.Windows.Documents.Block> öğesi gereklidir. Basit hale getirmek için hücrenin içine biraz metin yerleştirelim. Bunu <xref:System.Windows.Documents.Run> öğesi ile bir <xref:System.Windows.Documents.Paragraph> kullanarak yapabiliriz. Aşağıdaki diyagramda, bir <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Inline> bir öğe alıp <xref:System.Windows.Documents.Run> (bir <xref:System.Windows.Documents.Inline> öğesi) yalnızca düz metin alabilir.  
  
     ![Diyagram: paragraf&#47;için üst alt şema](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![Diyagram: çalıştırma&#47;için üst alt şema](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Biçimlendirme içindeki tüm örnek aşağıda verilmiştir.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>Programlı olarak TextElement Içeriğiyle çalışma  
 Bir <xref:System.Windows.Documents.TextElement> içerikleri koleksiyonlar tarafından yapılır ve böylece bu koleksiyonlar ile çalışarak, <xref:System.Windows.Documents.TextElement> nesnelerinin içeriğini programlı bir şekilde işlemek yapılır. <xref:System.Windows.Documents.TextElement> türetilmiş sınıflar tarafından kullanılan üç farklı koleksiyon vardır:  
  
- <xref:System.Windows.Documents.InlineCollection>: bir <xref:System.Windows.Documents.Inline> öğeleri koleksiyonunu temsil eder. <xref:System.Windows.Documents.InlineCollection>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Span>ve <xref:System.Windows.Controls.TextBlock> öğelerinin izin verilen alt içeriğini tanımlar.  
  
- <xref:System.Windows.Documents.BlockCollection>: bir <xref:System.Windows.Documents.Block> öğeleri koleksiyonunu temsil eder. <xref:System.Windows.Documents.BlockCollection>, <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.TableCell>, <xref:System.Windows.Documents.Floater>ve <xref:System.Windows.Documents.Figure> öğelerinin izin verilen alt içeriğini tanımlar.  
  
- <xref:System.Windows.Documents.ListItemCollection>: sıralı veya sıralanmamış <xref:System.Windows.Documents.List>belirli bir içerik öğesini temsil eden bir akış içeriği öğesi.  
  
 **Inlines**, **Blocks**ve **ListItems**öğelerinin ilgili özelliklerini kullanarak bu koleksiyonlardan öğe işleyebilir (öğeleri ekleyebilir veya kaldırabilirsiniz). Aşağıdaki örneklerde, **Inlines** özelliğini kullanarak bir yayılma içeriğinin nasıl kullanılacağı gösterilmektedir.  
  
> [!NOTE]
> Tablo, içeriğini işlemek için çeşitli koleksiyonlar kullanır, ancak burada kapsanmaz. Daha fazla bilgi için bkz. [tabloya genel bakış](table-overview.md).  
  
 Aşağıdaki örnek, yeni bir <xref:System.Windows.Documents.Span> nesnesi oluşturur ve sonra iki metin çalıştırmasını <xref:System.Windows.Documents.Span>içerik alt öğesi olarak eklemek için `Add` yöntemini kullanır.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 Aşağıdaki örnek yeni bir <xref:System.Windows.Documents.Run> öğesi oluşturur ve <xref:System.Windows.Documents.Span>başlangıcına ekler.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 Aşağıdaki örnek, <xref:System.Windows.Documents.Span>son <xref:System.Windows.Documents.Inline> öğeyi siler.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 Aşağıdaki örnek, tüm içeriği (<xref:System.Windows.Documents.Inline> öğeleri) <xref:System.Windows.Documents.Span>temizler.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>Bu Içerik modelini paylaşan türler  
 Aşağıdaki türler <xref:System.Windows.Documents.TextElement> sınıfından devralınır ve bu genel bakışta açıklanan içeriği göstermek için kullanılabilir.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Bu listenin yalnızca Windows SDK ile dağıtılan soyut olmayan türler içerdiğini unutmayın. <xref:System.Windows.Documents.TextElement>devraldığı diğer türleri kullanabilirsiniz.  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>TextElement nesneleri Içerebilen türler  
 Bkz. [WPF Içerik modeli](../controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [FlowDocument'ı Blokların Özelliği ile Düzenleme](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Akış İçeriği Öğelerini Blokların Özelliği ile Düzenleme](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [FlowDocument'ı Blokların Özelliği ile Düzenleme](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Sütunlar Özelliği Aracılığıyla bir Tablonun Sütunlarını Düzenleme](how-to-manipulate-table-columns-through-the-columns-property.md)
- [RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
