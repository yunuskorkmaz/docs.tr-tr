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
ms.openlocfilehash: ecb9441bc63eae41cfbbadf3bf81b0e5392bd0cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125126"
---
# <a name="textelement-content-model-overview"></a>TextElement İçerik Modeline Genel Bakış
Bu içerik modeline genel bakış desteklenen içeriğini açıklayan bir <xref:System.Windows.Documents.TextElement>. <xref:System.Windows.Documents.Paragraph> Sınıfı, bir tür <xref:System.Windows.Documents.TextElement>. İçerik modeli, diğer hangi nesneleri/öğeleri bulunabilir açıklar. Bu genel bakışta öğesinden türetilen nesneler için kullanılan içerik modeli özetler <xref:System.Windows.Documents.TextElement>. Daha fazla bilgi için [akış belgesine genel bakış](flow-document-overview.md).  

<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>İçerik modeli diyagramı  
 Türetilmiş sınıflar için aşağıdaki diyagramda içerik modeli özetlenmektedir <xref:System.Windows.Documents.TextElement> yanı sıra diğer nasıl olmayan `TextElement` sınıfları Bu modele uyar.  
  
 ![Diyagram: Akış içeriği kapsama şeması](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 Yukarıdaki diyagramdan görüldüğü gibi bir öğe için izin verilen alt öğe mutlaka olup bir sınıf türetilir tarafından belirlenir değil <xref:System.Windows.Documents.Block> sınıfı veya <xref:System.Windows.Documents.Inline> sınıfı. Örneğin, bir <xref:System.Windows.Documents.Span> (bir <xref:System.Windows.Documents.Inline>-türetilmiş sınıf) yalnızca <xref:System.Windows.Documents.Inline> alt öğeleri, ancak bir <xref:System.Windows.Documents.Figure> (Ayrıca bir <xref:System.Windows.Documents.Inline>-türetilmiş sınıf) yalnızca <xref:System.Windows.Documents.Block> alt öğeleri. Bu nedenle, bir diyagram hızla başka hangi öğe bulunabilir belirlemek için yararlıdır. Örnek olarak, akış içeriği oluşturmak nasıl belirlemek için diyagram şimdi kullanın. bir <xref:System.Windows.Controls.RichTextBox>.  
  
1.  A <xref:System.Windows.Controls.RichTextBox> içermelidir bir <xref:System.Windows.Documents.FlowDocument> hangi sırayla içermelidir bir <xref:System.Windows.Documents.Block>-türetilmiş bir nesneye. Önceki şemada karşılık gelen bir segmentten verilmiştir.  
  
     ![Diyagram: RichTextBox kapsama kuralları](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     Şimdiye kadar biçimlendirmeyi aşağıdaki gibi görünmelidir budur.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2.  Diyagram göre vardır <xref:System.Windows.Documents.Block> öğeleri dahil olmak üzere seçmek için <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List>, ve <xref:System.Windows.Documents.BlockUIContainer> (önceki şemada blok türetilmiş sınıflara bakın). İstediğimizi varsayalım bir <xref:System.Windows.Documents.Table>. Önceki şemada göre bir <xref:System.Windows.Documents.Table> içeren bir <xref:System.Windows.Documents.TableRowGroup> içeren <xref:System.Windows.Documents.TableRow> içeren öğeleri <xref:System.Windows.Documents.TableCell> içeren bir <xref:System.Windows.Documents.Block>-türetilmiş bir nesneye. Karşılık gelen kesim için verilmiştir <xref:System.Windows.Documents.Table> yukarıdaki diyagramdan alınan.  
  
     ![Diyagram: Üst&#47;tablosu için alt şema](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     Karşılık gelen biçimlendirme verilmiştir.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3.  Yine, bir veya daha fazla <xref:System.Windows.Documents.Block> altında gerekli öğelerden bir <xref:System.Windows.Documents.TableCell>. Basit hale getirmek için şimdi metin hücre içine yerleştirin. Bunu kullanarak yapabiliriz bir <xref:System.Windows.Documents.Paragraph> ile bir <xref:System.Windows.Documents.Run> öğesi. Karşılık gelen gösteren diyagram kesimlerinden verilmiştir bir <xref:System.Windows.Documents.Paragraph> sürebilir bir <xref:System.Windows.Documents.Inline> öğesi ve bu bir <xref:System.Windows.Documents.Run> (bir <xref:System.Windows.Documents.Inline> öğesi) yalnızca düz metin alabilir.  
  
     ![Diyagram: Üst&#47;paragraf için alt şema](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![Diyagram: Üst&#47;çalıştırma için alt şema](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Tüm biçimlendirme örneği verilmiştir.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>TextElement içerik ile program aracılığıyla çalışma  
 İçeriği bir <xref:System.Windows.Documents.TextElement> koleksiyonları ve bunu programlı olarak içeriğini düzenleme oluşur <xref:System.Windows.Documents.TextElement> nesneleri, bu koleksiyonlarla çalışma tarafından gerçekleştirilir. Tarafından kullanılan üç farklı koleksiyon <xref:System.Windows.Documents.TextElement> -türetilmiş sınıflar:  
  
-   <xref:System.Windows.Documents.InlineCollection>: Bir koleksiyonunu temsil eder <xref:System.Windows.Documents.Inline> öğeleri. <xref:System.Windows.Documents.InlineCollection> izin verilen alt içeriğini tanımlayan <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Span>, ve <xref:System.Windows.Controls.TextBlock> öğeleri.  
  
-   <xref:System.Windows.Documents.BlockCollection>: Bir koleksiyonunu temsil eder <xref:System.Windows.Documents.Block> öğeleri. <xref:System.Windows.Documents.BlockCollection> izin verilen alt içeriğini tanımlayan <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.TableCell>, <xref:System.Windows.Documents.Floater>, ve <xref:System.Windows.Documents.Figure> öğeleri.  
  
-   <xref:System.Windows.Documents.ListItemCollection>: Bir sıralı içindeki belirli bir içerik öğesini temsil eden bir akış içerik öğesi veya sıralanmamış <xref:System.Windows.Documents.List>.  
  
 Yönetebilirsiniz (ekler veya öğeleri kaldırma) ilgili özelliklerini kullanarak bu koleksiyonların **satır içleri**, **blokları**, ve **ListItems**. Aşağıdaki örnekler bir aralık kullanmanın içeriğini yönetmek nasıl **satır içleri** özelliği.  
  
> [!NOTE]
>  Tablo içeriğini işlemek için birden fazla koleksiyon kullanır, ancak burada incelenmemiştir. Daha fazla bilgi için [tabloya genel bakış](table-overview.md).  
  
 Aşağıdaki örnek yeni bir oluşturur <xref:System.Windows.Documents.Span> nesne ve kullandığı `Add` çalışan içerik alt öğe olarak iki metin eklemek için yöntemini <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 Aşağıdaki örnek yeni bir oluşturur <xref:System.Windows.Documents.Run> öğesi ve başında ekler <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 Aşağıdaki örnekte, son silinir <xref:System.Windows.Documents.Inline> öğesinde <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 Aşağıdaki örnek içeriğinin tamamını temizler (<xref:System.Windows.Documents.Inline> öğeleri) öğesinden <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>Bu içerik modeli paylaşan türleri  
 Şu türlerden devralınan <xref:System.Windows.Documents.TextElement> sınıfı ve bu genel bakışta açıklanan içeriği görüntülemek için kullanılabilir.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Bu liste yalnızca soyut olmayan türleri ile dağıtılmış içerdiğine dikkat [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]. Devralınan diğer türleri kullanabilir <xref:System.Windows.Documents.TextElement>.  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>TextElement nesneleri içeren türleri  
 Bkz: [WPF içerik modeli](../controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [FlowDocument'ı Blokların Özelliği ile Düzenleme](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Akış İçeriği Öğelerini Blokların Özelliği ile Düzenleme](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [FlowDocument'ı Blokların Özelliği ile Düzenleme](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Sütunlar Özelliği Aracılığıyla bir Tablonun Sütunlarını Düzenleme](how-to-manipulate-table-columns-through-the-columns-property.md)
- [RowGroups Özelliği Aracılığıyla bir Tablonun Satır Gruplarını Düzenleme](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
