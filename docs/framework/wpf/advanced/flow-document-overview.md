---
title: Akış Belgesine Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'documents [WPF], flow documents [WPF], , '
- ', '
- flow documents [WPF]
ms.assetid: ef236a50-d44f-43c8-ba7c-82b0c733c0b7
ms.openlocfilehash: f8e5a7475765bffb76e7b07e81db25b4a62ae038
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59303498"
---
# <a name="flow-document-overview"></a>Akış Belgesine Genel Bakış
Akış belgeleri görüntüleme ve okunabilirliği iyileştirmek için tasarlanmıştır. Önceden tanımlanmış bir düzene ayarlanıyor, yerine akış belgeleri dinamik olarak ayarlama ve çalışma zamanı değişkenleri isteğe bağlı kullanıcı tercihlerini pencere boyutunu ve cihaz çözünürlüğü gibi temel alarak kendi içerik yeniden akışı. Ayrıca, akış belgeleri sayfalandırma ve sütunlar gibi gelişmiş belge özellikleri sunar. Bu konu, akış belgeleri ve bunların nasıl oluşturulacağı hakkında genel bir bakış sağlar.  

<a name="what_is_a_flow_document"></a>   
## <a name="what-is-a-flow-document"></a>Bir akış belge nedir  
 Akış belgesi, "yeniden akış içerik" pencere boyutu, cihaz çözüm ve diğer ortam değişkenlerine bağlı olarak tasarlanmıştır. Ayrıca, akış belge özelliklerini görüntüleme okunabilirlik ve boyutunu ve yazı tipleri görünümünü değiştirme özelliği en iyi duruma modları, arama da dahil olmak üzere yerleşik bir dizi mevcuttur. Kolay okunması birincil belge tüketimi senaryo olduğunda akış belgeleri en iyi şekilde kullanılır. Buna karşılık, sabit belgeleri, statik bir sunu sağlamak için tasarlanmıştır. Sabit belgeleri, kaynak içerik kalitesini gerekli olduğunda yararlıdır. Bkz: [WPF'deki Belgeler](documents-in-wpf.md) farklı belge türleri hakkında daha fazla bilgi için.  
  
 Örnek, farklı boyutlardaki birden fazla pencerelerinde bir akış belge aşağıda gösterilmiştir. Görüntü alanını değiştikçe kullanılabilir alanı en iyi kullanılmasını sağlamak için içeriği yeniden akar.  
  
 ![Belge içerik boyutlandırıldığında akış](./media/edocs-flowdocument.png "eDocs_FlowDocument")  
  
 Yukarıdaki görüntüde görüldüğü gibi akış içeriği paragraflar, listeler, görüntüleri ve benzeri birçok bileşen dahil edebilirsiniz. Bu bileşenler işaretleme öğeleri ve nesneleri yordam kodu karşılık gelir. Bu sınıfların ayrıntılı üzerinden daha sonra ele alacağız [akış ilgili sınıflar](#flow_related_classes) bu genel bakış bölümünde. Şimdilik, kalın metin ve bir liste paragrafı oluşan bir akış belgesi oluşturur bir basit kod örneği aşağıda verilmiştir.
  
 [!code-xaml[FlowOvwSnippets_snip#SimpleFlowExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SimpleFlowExample.xaml#simpleflowexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SimpleFlowExample.cs#simpleflowcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SimpleFlowExample.vb#simpleflowcodeonlyexamplewholepage)]  
  
 Aşağıdaki çizimde, bu kod parçacığı nasıl göründüğünü gösterir.  
  
 ![Ekran: İşlenmiş FlowDocument örneği](./media/flow-ovw-first-example.png "Flow_Ovw_First_Example")  
  
 Bu örnekte, <xref:System.Windows.Controls.FlowDocumentReader> denetim akış içeriğini barındırmak için kullanılır. Bkz: [akış belge türleri](#flow_document_types) denetimleri barındırma akış içeriği hakkında daha fazla bilgi için. <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, ve <xref:System.Windows.Documents.Bold> öğeleri içerik biçimlendirme, denetim için kullanılan biçimlendirme sıralarına göre. Örneğin, <xref:System.Windows.Documents.Bold> öğesi yayılan paragraf metni yalnızca bir kısmını arasında; sonuç olarak, yalnızca bu metin kalın bölümüdür. HTML kullandıysanız, bu size tanıdık gelecektir.  
  
 Vurgulanmış olarak Yukarıdaki çizimde, Flow belgelerine yerleşik birkaç özellik vardır:
  
-   Arama: Tüm belgeyi bir tam metin arama gerçekleştirmesine izin verir.  
  
-   Görüntüleme modu: Kullanıcı, bir tek sayfa (sayfa--bir zamanda) görüntüleme modu, bir iki-sayfası--a-mod ve sürekli bir kayan (sınırsız) görüntüleme modunda görüntüleme zamanda (kitap Okuma biçimi) dahil olmak üzere, tercih edilen görüntüleme modunda seçebilirsiniz.  Bu izleme modları hakkında daha fazla bilgi için bkz. <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  
  
-   Sayfa Gezinti denetimlerinin: Sayfa Gezinti denetimlerinin, belge görüntüleme modunda sayfaları kullanıyorsa, sonraki sayfaya (aşağı ok) veya önceki sayfa (yukarı ok), hem de geçerli sayfa numarası ve toplam sayfa sayısı için göstergeleri atlamak için bir düğme bulunur. Sayfalar arasında çevirme klavye oklarını kullanarak da gerçekleştirilebilir.  
  
-   Yakınlaştırma: Yakınlaştırma denetimleri, sırasıyla artırmak ya da artı veya eksi düğmelerini, yakınlaştırma düzeyi azaltmak kullanıcı sağlar. Yakınlaştırma denetimlerini yakınlaştırma düzeyini ayarlamak için bir kaydırıcı de içerir. Daha fazla bilgi için bkz. <xref:System.Windows.Controls.FlowDocumentReader.Zoom%2A>.  
  
 Bu özellikler, akış içeriğini barındırmak için kullanılan denetim göre değiştirilebilir. Farklı denetimler sonraki bölümde açıklanmıştır.  
  
<a name="flow_document_types"></a>   
## <a name="flow-document-types"></a>Akış belge türleri  
 Hangi nesne akış içeriği barındırmak için kullanılan temel akış belge içeriği ve görünme görüntüsünü bağlıdır. Akış içeriği görüntülemeyi destekleyen dört denetimleri vardır: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.RichTextBox>, ve <xref:System.Windows.Controls.FlowDocumentScrollViewer>. Bu denetimler, aşağıda kısaca açıklanmıştır.  
  
 **Not:** <xref:System.Windows.Documents.FlowDocument> görüntüleme denetimleri bunların tümü kullanmak için doğrudan akış içeriği barındırmak için gerekli olan bir <xref:System.Windows.Documents.FlowDocument> akış içerik barındırma olanağı.
  
### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader> dinamik olarak bir tek sayfa (sayfa--bir zamanda) görüntüleme modu, bir iki-sayfası--a-mod ve sürekli bir kayan (sınırsız) görüntüleme modunda görüntüleme zamanda (kitap Okuma biçimi) dahil olmak üzere çeşitli görüntüleme modları arasında seçim yapması sağlayan özellikler içerir. Bu izleme modları hakkında daha fazla bilgi için bkz. <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>. Dinamik olarak farklı görüntüleme modları arasında geçiş yapma özelliğini gerekmiyorsa <xref:System.Windows.Controls.FlowDocumentPageViewer> ve <xref:System.Windows.Controls.FlowDocumentScrollViewer> hafifletilmiş akış belirli görüntüleme modunda sabit içerik görüntüleyicileri sağlar.  
  
### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer and FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> içerik sayfası--bir zamanda içinde gösterir modu, görüntülerken <xref:System.Windows.Controls.FlowDocumentScrollViewer> sürekli kaydırma modunda içerik gösterir. Her ikisi de <xref:System.Windows.Controls.FlowDocumentPageViewer> ve <xref:System.Windows.Controls.FlowDocumentScrollViewer> belirli görüntüleme moduna düzeltildi. Karşılaştırılacak <xref:System.Windows.Controls.FlowDocumentReader>, dinamik olarak çeşitli görüntüleme modları arasında seçim yapması özellikleri içerir (tarafından sağlanan <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> numaralandırma), daha fazla kaynak yoğunluğu olan karşılığında <xref:System.Windows.Controls.FlowDocumentPageViewer> veya <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Varsayılan olarak, dikey bir kaydırma çubuğuna her zaman gösterilir ve yatay bir ScrollBar'ın gerektiğinde görünür duruma gelir. Varsayılan kullanıcı Arabirimi için <xref:System.Windows.Controls.FlowDocumentScrollViewer> araç dahil değildir; ancak <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> özelliği, yerleşik bir araç çubuğu etkinleştirmek için kullanılabilir.  
  
### <a name="richtextbox"></a>RichTextBox  
 Kullandığınız bir <xref:System.Windows.Controls.RichTextBox> akış içeriği düzenlemek kullanıcı izin vermek istediğinizde. Örneğin, işlemek bir kullanıcının verilen bir düzenleyici oluşturmak istediyseniz ister tablolar italik ve biçimlendirme vb. kalın, kullanacağınız bir <xref:System.Windows.Controls.RichTextBox>. Bkz: [RichTextBox Genel Bakış](../controls/richtextbox-overview.md) daha fazla bilgi için.  
  
 **Not:** Akış içeriği içinde bir <xref:System.Windows.Controls.RichTextBox> tam olarak diğer denetimlerde akış içeriği gibi davranmaz. Örneğin, hiç sütun yok bir <xref:System.Windows.Controls.RichTextBox> ve bu nedenle otomatik boyutlandırma davranışı. Ayrıca, arama, yakınlaştırma modu ve sayfa gezintisi görüntüleme gibi akış içeriği genellikle yerleşik özellikleri içinde kullanılabilir olmayan bir <xref:System.Windows.Controls.RichTextBox>.  
  
<a name="creating_flow_content"></a>   
## <a name="creating-flow-content"></a>Akış içeriği oluşturma  
 Akış içeriği, karmaşık, metin, resimler, tablolar da dahil olmak üzere çeşitli öğelerinin ve hatta olabilir <xref:System.Windows.UIElement> türetilmiş sınıflar gibi denetimleri. Karmaşık akış içeriği oluşturma işlemini anlamak için aşağıdaki noktaları önemlidir:  
  
-   **Flow ile ilgili sınıflar**: Akış içeriği içinde kullanılan her bir sınıfın belirli bir amacı vardır. Ayrıca, akış sınıfları arasındaki hiyerarşik ilişkiyi nasıl kullanıldığını anlamanıza yardımcı olur. Örneğin, türetilmiş sınıflar <xref:System.Windows.Documents.Block> türetilmiş sınıflar sırasında diğer nesneleri kapsamak üzere kullanılan sınıf <xref:System.Windows.Documents.Inline> görüntülenen nesneleri içerir.  
  
-   **İçerik şeması**: Akış belgesi, iç içe öğelerin önemli miktarda gerektirebilir. İçerik şeması öğeleri arasındaki olası üst/alt ilişkilerini belirler.  
  
 Aşağıdaki bölümlerde daha ayrıntılı bir şekilde bu alanların her biri üzerinden geçer.  
  
<a name="flow_related_classes"></a>   
## <a name="flow-related-classes"></a>İlgili sınıflar akış  
 Akış içeriği en yaygın kullanılan nesneler Aşağıdaki diyagramda gösterilmektedir:  
  
 ![Diyagram: Flow content element class hierarchy](./media/flow-class-hierarchy.png "Flow_Class_Hierarchy")  
  
 Akış içeriği amaçları için iki önemli kategorisi vardır:  
  
1. **Blok türetilmiş sınıflar**: "Blok içerik öğeleri" veya "Blok öğeleri" yalnızca olarak da adlandırılır. Devralınan öğeleri <xref:System.Windows.Documents.Block> ortak bir üst öğe altında öğeleri gruplandırmak için veya bir gruba ortak öznitelikleri uygulamak için kullanılabilir.  
  
2. **Satır içi türetilmiş sınıflar**: "Satır içi içeriği öğelerini" veya yeni "satır içi öğeleri" olarak da adlandırılır. Devralınan öğeleri <xref:System.Windows.Documents.Inline> ya da bir blok öğede veya başka bir satır içi öğenin içinde yer alır. Satır içi öğeleri genellikle ekran için içeriği doğrudan kapsayıcı olarak kullanılır. Örneğin, bir <xref:System.Windows.Documents.Paragraph> (blok öğede) içerebilir bir <xref:System.Windows.Documents.Run> (satır içi öğesini) ancak <xref:System.Windows.Documents.Run> gerçekten ekranında işlenmeden metni içerir.  
  
 Bu iki kategori her sınıfta, aşağıda kısaca açıklanmıştır.  
  
### <a name="block-derived-classes"></a>Blok türetilmiş sınıfları  
 **Paragraf**  
  
 <xref:System.Windows.Documents.Paragraph> genellikle Grup içeriğini paragrafa kullanılır. Paragraf basit ve en yaygın kullanımı, bir metin paragrafı sağlandığında oluşturmaktır.  
  
 [!code-xaml[FlowOvwSnippets_snip#ParagraphExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ParagraphExample.xaml#paragraphexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ParagraphExample.cs#paragraphcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ParagraphExample.vb#paragraphcodeonlyexamplewholepage)]  
  
 Ancak, aşağıda göreceğiniz gibi satır içi türetilen diğer öğeleri de içerebilir. 
  
 **Bölüm**  
  
 <xref:System.Windows.Documents.Section> yalnızca diğer kapsamak için kullanılmış <xref:System.Windows.Documents.Block>-türetilmiş öğeler. Herhangi bir varsayılan biçimlendirme içerdiği öğeler için geçerli değildir. Ancak, herhangi bir özellik üzerinde kümesi değerleri bir <xref:System.Windows.Documents.Section> alt öğeleri için geçerlidir. Bölüm ayrıca programlı olarak alt koleksiyonu yineleme yapmak sağlar. <xref:System.Windows.Documents.Section> benzer şekilde kullanılan \<DIV > HTML etiketinde.  
  
 Aşağıdaki örnekte, üç paragraf biri altında tanımlanan <xref:System.Windows.Documents.Section>. Bölümü bir <xref:System.Windows.Documents.TextElement.Background%2A> özelliğini kırmızı, bu nedenle arka plan rengi paragrafların değeri de kırmızı.  
  
 [!code-xaml[FlowOvwSnippets_snip#SectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SectionExample.xaml#sectionexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SectionExample.cs#sectioncodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SectionExample.vb#sectioncodeonlyexamplewholepage)]  
  
 **BlockUIContainer**  
  
 <xref:System.Windows.Documents.BlockUIContainer> sağlar <xref:System.Windows.UIElement> öğeleri (yani bir <xref:System.Windows.Controls.Button>) içinde blok türetilmiş akış içeriği katıştırılmış. <xref:System.Windows.Documents.InlineUIContainer> (aşağıya bakın) katıştırmak için kullanılan <xref:System.Windows.UIElement> türetilmiş satır içi akış içeriği öğeleri. <xref:System.Windows.Documents.BlockUIContainer> ve <xref:System.Windows.Documents.InlineUIContainer> kullanmak için başka hiçbir yolu olmadığı için önemli olan bir <xref:System.Windows.UIElement> flow'da bir bu iki öğenin içinde bulunmadığı sürece içerik.  
  
 Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Documents.BlockUIContainer> ana öğesine <xref:System.Windows.UIElement> akış içeriği içindeki nesneleri.  
  
 [!code-xaml[SpanSnippets#_BlockUIXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml#_blockuixaml)]  
  
 Bu örneğin nasıl işlediğini aşağıdaki şekilde gösterilmiştir:  
  
 ![Akış içeriği bir UIElement gösteren ekran görüntüsü katıştırılmış.](./media/flow-document-overview/embedded-blockuicontainer.png)  
  
 **Liste**  
  
 <xref:System.Windows.Documents.List> Madde işaretli veya sayısal bir liste oluşturmak için kullanılır. Ayarlama <xref:System.Windows.Documents.List.MarkerStyle%2A> özelliğini bir <xref:System.Windows.TextMarkerStyle> liste stilini belirlemek için sabit listesi değeri. Aşağıdaki örnek, basit bir listesi oluşturma işlemi gösterilmektedir.  
  
 [!code-xaml[FlowOvwSnippets_snip#ListExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ListExample.xaml#listexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ListExample.cs#listcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ListExample.vb#listcodeonlyexamplewholepage)]  
  
 **Not:** <xref:System.Windows.Documents.List> kullanan yalnızca akış öğesi <xref:System.Windows.Documents.ListItemCollection> alt öğelerini yönetmek için.  
  
 **Tablo**  
  
 <xref:System.Windows.Documents.Table> bir tablo oluşturmak için kullanılır. <xref:System.Windows.Documents.Table> benzer <xref:System.Windows.Controls.Grid> öğe ancak daha fazla özellik içerir ve bu nedenle büyük kaynağı ek yükü gerektirir. Çünkü <xref:System.Windows.Controls.Grid> olduğu bir <xref:System.Windows.UIElement>, içeren sürece akış içeriği kullanılamaz bir <xref:System.Windows.Documents.BlockUIContainer> veya <xref:System.Windows.Documents.InlineUIContainer>. Daha fazla bilgi için <xref:System.Windows.Documents.Table>, bkz: [tabloya genel bakış](table-overview.md).  
  
### <a name="inline-derived-classes"></a>Satır içi türetilmiş sınıfları  
 **Çalıştır**  
  
 <xref:System.Windows.Documents.Run> biçimlendirilmemiş metinleri kapsamak için kullanılmış. Beklediğiniz <xref:System.Windows.Documents.Run> kapsamlı olarak kullanılmak üzere nesneleri akış içeriği. Ancak, biçimlendirmede <xref:System.Windows.Documents.Run> öğeleri açıkça kullanılacak gerekli değildir. <xref:System.Windows.Documents.Run> oluşturma veya kod kullanarak akış belgeleri işlemek amacıyla gereklidir. Örneğin, ilk aşağıdaki biçimlendirmede <xref:System.Windows.Documents.Paragraph> belirtir <xref:System.Windows.Documents.Run> açıkça sırasında ikinci öğe yok. Her iki benzer bir çıktı oluşturur.  
  
 [!code-xaml[FlowOvwSnippets_snip#RunExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/RunSnippetsExample.xaml#runexample1)]  
  
 **Not:**  İtibariyle [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], <xref:System.Windows.Documents.Run.Text%2A> özelliği <xref:System.Windows.Documents.Run> bağımlılık özelliği nesnedir. Bağlayabilirsiniz <xref:System.Windows.Documents.Run.Text%2A> gibi özellik bir veri kaynağı bir <xref:System.Windows.Controls.TextBlock>. <xref:System.Windows.Documents.Run.Text%2A> Özelliği, tek yönlü bağlamaya tam olarak destekler. <xref:System.Windows.Documents.Run.Text%2A> Özelliğini de destekleyen iki yönlü bağlama dışında <xref:System.Windows.Controls.RichTextBox>. Örnek için bkz. <xref:System.Windows.Documents.Run.Text%2A?displayProperty=nameWithType>  
  
 **yayılma**  
  
 <xref:System.Windows.Documents.Span> Satır içi içeriği diğer öğelerini birlikte gruplar. İçerik içinde hiçbir devralınan işleme uygulanan bir <xref:System.Windows.Documents.Span> öğesi. Ancak, öğeler, devralmanız <xref:System.Windows.Documents.Span> dahil olmak üzere <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Italic> ve <xref:System.Windows.Documents.Underline> için metin biçimlendirmesi uygular.  
  
 Bir örnek aşağıdadır bir <xref:System.Windows.Documents.Span> metin dahil olmak üzere satır içi içeriği için kullanılan bir <xref:System.Windows.Documents.Bold> öğesi ve bir <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[FlowOvwSnippets_snip#SpanExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SpanExample.xaml#spanexamplewholepage)]  
  
 Aşağıdaki ekran görüntüsünde, bu örneğin nasıl işlediğini gösterir.  
  
 ![Ekran: İşlenmiş span örneği](./media/flow-spanexample.gif "Flow_SpanExample")  
  
 **InlineUIContainer**  
  
 <xref:System.Windows.Documents.InlineUIContainer> sağlar <xref:System.Windows.UIElement> öğeleri (yani bir denetimi gibi <xref:System.Windows.Controls.Button>) katıştırılmış bir <xref:System.Windows.Documents.Inline> içerik öğesi. Bu öğe satır içi eşdeğeri olan <xref:System.Windows.Documents.BlockUIContainer> yukarıda açıklanan. Kullanan bir örnek aşağıdadır <xref:System.Windows.Documents.InlineUIContainer> eklemek için bir <xref:System.Windows.Controls.Button> satır içinde bir <xref:System.Windows.Documents.Paragraph>.  
  
 [!code-xaml[FlowOvwSnippets_snip#InlineUIContainerExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/InlineUIContainerExample.xaml#inlineuicontainerexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/InlineUIContainerExample.cs#inlineuicontainercodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/InlineUIContainerExample.vb#inlineuicontainercodeonlyexamplewholepage)]  
  
 **Not:** <xref:System.Windows.Documents.InlineUIContainer> açıkça işaretlemede kullanılabilmesi gerekmez. Bunu kullanmazsanız bir <xref:System.Windows.Documents.InlineUIContainer> kodu derlendiğinde yine de oluşturulur.  
  
 **Şekil ve Floater**  
  
 <xref:System.Windows.Documents.Figure> ve <xref:System.Windows.Documents.Floater> içeriği birincil içerik akışının bağımsız olarak özelleştirilebilir yerleştirme özellikleri ile akış belgelerde eklemek için kullanılır. <xref:System.Windows.Documents.Figure> veya <xref:System.Windows.Documents.Floater> tanıtımlar gibi içerik ilgili gevşek ekleme veya öğeleri vurgulama veya içeriği, görüntüleri veya diğer içerik ana içerik akışı içinde destekleyen konak kısımlarını vurgulamak için sık sık kullanılır.  
  
 Aşağıdaki örnek nasıl ekleyeceğinizi gösterir. bir <xref:System.Windows.Documents.Figure> içine bir paragraf metni.  
  
 [!code-xaml[FlowOvwSnippets_snip#FigureExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/FigureExample.xaml#figureexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/FigureExample.cs#figurecodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/FigureExample.vb#figurecodeonlyexamplewholepage)]  
  
 Aşağıdaki çizim, bu örneğin nasıl işlediğini gösterir.  
  
 ![Ekran: Şekil örnek](./media/flow-ovw-figure-example.png "Flow_Ovw_Figure_Example")  
  
 <xref:System.Windows.Documents.Figure> ve <xref:System.Windows.Documents.Floater> çeşitli yollarla farklıdır ve farklı senaryolar için kullanılırlar.  
  
 **Şekil:**  
  
-   Yerleştirilebilir: Sayfa, içerik, sütun veya paragraf göre sabitlemek için yatay ve dikey bağlayıcılarını ayarlayabilirsiniz. Ayrıca kendi <xref:System.Windows.Documents.Figure.HorizontalOffset%2A> ve <xref:System.Windows.Documents.Figure.VerticalOffset%2A> özellikler rastgele uzaklıkları belirtir.  
  
-   Birden fazla sütuna boyutlandırılıp boyutlandırılmayacağını: Ayarlayabileceğiniz <xref:System.Windows.Documents.Figure> yükseklik ve genişlik katlarıyla sayfası, içeriğin ya da sütun yükseklik veya genişlik. Sayfa ve içerik söz konusu olduğunda, çarpan 1'den büyük olmayan izin verildiğini unutmayın. Örneğin, genişliği ayarlayabilirsiniz bir <xref:System.Windows.Documents.Figure> "0,5 sayfası" veya "0,25 içerik" veya "2 sütun". Yükseklik ve genişlik piksel mutlak değerlerini ayarlayabilirsiniz.  
  
-   Sayfalandırma değil: İçerik içinde bir <xref:System.Windows.Documents.Figure> içine uymayan <xref:System.Windows.Documents.Figure>, hangi içeriği sığacak şekilde işlenir ve kalan içeriği kaybolur  
  
 **Floater:**  
  
-   Konumlandırılmış olabilir ve boşluk için kullanılabilir hale getirilebilir her yerde işlenir. Uzaklık ya da bağlantı ayarlanamıyor bir <xref:System.Windows.Documents.Floater>.  
  
-   Birden fazla sütuna boyutta olması: Varsayılan olarak, <xref:System.Windows.Documents.Floater> boyutlarda bir sütun. Bunun bir <xref:System.Windows.Documents.Floater.Width%2A> bu değer bir sütun genişliği yok sayıldı ve floater büyük olup olmadığını ancak bir mutlak piksel değere ayarlanabilir özelliği bir sütununda boyutu. Doğru piksel genişliği ayarlayarak bu saatten daha az bir sütuna boyutlandırabilirsiniz ancak boyutlandırma değil sütun göreli "0.5Column" için geçerli bir ifade değil. Bu nedenle <xref:System.Windows.Documents.Floater> genişliği. <xref:System.Windows.Documents.Floater> hiçbir height özelliği sahipse ve bu yükseklik ayarlanamaz, onun yükseklik içerik bağlıdır  
  
-   <xref:System.Windows.Documents.Floater> paginates: İçeriğini, belirtilen uzaklığında 1'den fazla sütun yüksekliği geçerse, floater keser ve paginates sonraki sütun, sonraki sayfaya, vs.  
  
 <xref:System.Windows.Documents.Figure> boyutunu denetlemek istediğiniz tek başına içerik yerleştirmek için iyi bir yerdir konumlandırma ve içerik belirtilen boyutu sığmasını eminiz. <xref:System.Windows.Documents.Floater> Akışlar için ana sayfa içeriği benzer, ancak ondan ayrılmış daha fazla ve ücretsiz akan içerik yerleştirmek için iyi bir yerdir.  
  
 **LineBreak**  
  
 <xref:System.Windows.Documents.LineBreak> satır sonu akış içeriği oluşmasına neden olur. Aşağıdaki örnek, kullanımını gösterir <xref:System.Windows.Documents.LineBreak>.  
  
 [!code-xaml[FlowOvwSnippets_snip#LineBreakExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/LineBreakExample.xaml#linebreakexamplewholepage)]  
  
 Aşağıdaki ekran görüntüsünde, bu örneğin nasıl işlediğini gösterir.  
  
 ![Ekran: LineBreak örnek](./media/flow-ovw-linebreakexample.png "Flow_Ovw_LineBreakExample")  
  
### <a name="flow-collection-elements"></a>Akış koleksiyonu öğeleri  
 Yukarıdaki örneklerde birçok <xref:System.Windows.Documents.BlockCollection> ve <xref:System.Windows.Documents.InlineCollection> akış içeriği programlı olarak oluşturmak için kullanılır. Örneğin, öğeleri eklemek için bir <xref:System.Windows.Documents.Paragraph>, sözdizimini kullanabilirsiniz:  
  
 `…`  
  
 `myParagraph.Inlines.Add(new Run("Some text"));`  
  
 `…`  
  
 Bu ekler bir <xref:System.Windows.Documents.Run> için <xref:System.Windows.Documents.InlineCollection> , <xref:System.Windows.Documents.Paragraph>.  Örtük olarak aynı budur <xref:System.Windows.Documents.Run> içinde bulunan bir <xref:System.Windows.Documents.Paragraph> biçimlendirme içinde:  
  
 `…`  
  
 `<Paragraph>`  
  
 `Some Text`  
  
 `</Paragraph>`  
  
 `…`  
  
 Kullanarak bir örnek olarak <xref:System.Windows.Documents.BlockCollection>, aşağıdaki örnekte yeni bir oluşturur <xref:System.Windows.Documents.Section> ve ardından **Ekle** yeni bir yöntem <xref:System.Windows.Documents.Paragraph> için <xref:System.Windows.Documents.Section> içeriği.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
 Bir akış koleksiyonu için öğe eklemenin yanı sıra, öğeleri de kaldırabilirsiniz.  Aşağıdaki örnekte, son silinir <xref:System.Windows.Documents.Inline> öğesinde <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 Aşağıdaki örnek içeriğinin tamamını temizler (<xref:System.Windows.Documents.Inline> öğeleri) öğesinden <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
 Akış içeriği ile programlı olarak çalışırken, büyük olasılıkla bu koleksiyonlara kapsamlı kullanımını hale getirir.  
  
 Bir akış öğesi kullanıp kullanmadığını bir <xref:System.Windows.Documents.InlineCollection> (satır içleri) veya <xref:System.Windows.Documents.BlockCollection> alt içerecek şekilde (bloklar) öğeleri alt öğeleri türüne bağlıdır (<xref:System.Windows.Documents.Block> veya <xref:System.Windows.Documents.Inline>) üst öğe tarafından bulunabilir. İçerme kuralları için içerik öğeleri sonraki bölümde içerik şemasında özetlenmiştir akış.  
  
 **Not:** Üçüncü bir tür ile akış içeriği, kullanılan koleksiyon <xref:System.Windows.Documents.ListItemCollection>, ancak bu koleksiyon yalnızca ile kullanılan bir <xref:System.Windows.Documents.List>. Ayrıca, çeşitli koleksiyonları ile kullanılan vardır <xref:System.Windows.Documents.Table>. Bkz: [tabloya genel bakış](table-overview.md) daha fazla bilgi için.  
  
<a name="content_schema"></a>   
## <a name="content-schema"></a>İçerik şeması  
 Farklı akış içeriği öğelerini sayısını göz önünde bulundurulduğunda, ne tür bir öğe içerebilir alt öğelerini izlemek için yorucu bir süreç olabilir. Aşağıdaki diyagramda, akış öğelerini kapsama kuralları özetlenmektedir. Oklar olası üst/alt ilişkilerini temsil eder.  
  
 ![Diyagram: Akış içeriği kapsama şeması](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 Yukarıdaki diyagramda görüldüğü gibi bir öğe için izin verilen alt öğe mutlaka olmasına göre belirlenir değil bir <xref:System.Windows.Documents.Block> öğesi veya bir <xref:System.Windows.Documents.Inline> öğesi. Örneğin, bir <xref:System.Windows.Documents.Span> (bir <xref:System.Windows.Documents.Inline> öğesi) yalnızca <xref:System.Windows.Documents.Inline> sırasında alt öğeleri bir <xref:System.Windows.Documents.Figure> (Ayrıca bir <xref:System.Windows.Documents.Inline> öğesi) yalnızca <xref:System.Windows.Documents.Block> alt öğeleri. Bu nedenle, bir diyagram hızla başka hangi öğe bulunabilir belirlemek için yararlıdır. Örnek olarak, akış içeriği oluşturmak nasıl belirlemek için diyagram şimdi kullanın. bir <xref:System.Windows.Controls.RichTextBox>.  
  
 **1.** A <xref:System.Windows.Controls.RichTextBox> içermelidir bir <xref:System.Windows.Documents.FlowDocument> hangi sırayla içermelidir bir <xref:System.Windows.Documents.Block>-türetilmiş bir nesneye. Yukarıdaki diyagramda karşılık gelen bir segmentten aşağıdadır.  
  
 ![Diyagram: RichTextBox kapsama kuralları](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
 Şimdiye kadar biçimlendirmeyi aşağıdaki gibi görünmelidir budur.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
 **2.** Diyagram göre vardır <xref:System.Windows.Documents.Block> öğeleri dahil olmak üzere seçmek için <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List>, ve <xref:System.Windows.Documents.BlockUIContainer> (yukarıdaki bloktan türetilmiş sınıflara bakın). İstediğimizi varsayalım bir <xref:System.Windows.Documents.Table>. Yukarıdaki diyagramda göre bir <xref:System.Windows.Documents.Table> içeren bir <xref:System.Windows.Documents.TableRowGroup> içeren <xref:System.Windows.Documents.TableRow> içeren öğeleri <xref:System.Windows.Documents.TableCell> içeren bir <xref:System.Windows.Documents.Block>-türetilmiş bir nesneye. Karşılık gelen kesim için aşağıdadır <xref:System.Windows.Documents.Table> yukarıdaki diyagramdan alınan.  
  
 ![Diyagram: Üst&#47;tablosu için alt şema](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
 Karşılık gelen biçimlendirme aşağıda verilmiştir.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
 **3.** Yine, bir veya daha fazla <xref:System.Windows.Documents.Block> altında gerekli öğelerden bir <xref:System.Windows.Documents.TableCell>. Basit hale getirmek için şimdi metin hücre içine yerleştirin. Bunu kullanarak yapabiliriz bir <xref:System.Windows.Documents.Paragraph> ile bir <xref:System.Windows.Documents.Run> öğesi. Aşağıda ilgili kesimlerinden gösteren diyagram bir <xref:System.Windows.Documents.Paragraph> sürebilir bir <xref:System.Windows.Documents.Inline> öğesi ve bu bir <xref:System.Windows.Documents.Run> (bir <xref:System.Windows.Documents.Inline> öğesi) yalnızca düz metin alabilir.  
  
 ![Diyagram: Üst&#47;paragraf için alt şema](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
 ![Diyagram: Üst&#47;çalıştırma için alt şema](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Tüm biçimlendirme örneği aşağıda verilmiştir.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="customizing_text"></a>   
## <a name="customizing-text"></a>Metin özelleştirme  
 Genellikle bir akış belgede içerik en yaygın türü metindir. Yukarıda sunulan nesneleri metin nasıl oluşturulacağını çoğu yönleri denetlemek için kullanılabilir olsa da, bu bölümde yer alan metni özelleştirmek için diğer bazı yöntemler vardır.  
  
### <a name="text-decorations"></a>Metin süslemeleri  
 Metin süslemeleri, alt çizgi, üst çizgi, temel ve üstü çizili etkileri metnine uygulanacak izin ver (Aşağıdaki resim bakın). Bu süslemeleri kullanılarak eklenen <xref:System.Windows.Documents.Inline.TextDecorations%2A> nesneler de dahil olmak üzere bir dizi tarafından kullanıma sunulan bir özellik <xref:System.Windows.Documents.Inline>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Controls.TextBlock>, ve <xref:System.Windows.Controls.TextBox>.  
  
 Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:System.Windows.Documents.Paragraph.TextDecorations%2A> özelliği bir <xref:System.Windows.Documents.Paragraph>.  
  
 [!code-xaml[InlineSnippets#_Paragraph_TextDecXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml#_paragraph_textdecxaml)]  
  
 [!code-csharp[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml.cs#_paragraph_textdec)]
 [!code-vb[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InlineSnippets/visualbasic/window1.xaml.vb#_paragraph_textdec)]  
  
 Aşağıdaki şekil, bu örneğin nasıl işlediğini gösterir.  
  
 ![Ekran: Varsayılan üstü çizili etkisi olan metin](./media/inline-textdec-strike.png "Inline_TextDec_Strike")  
  
 Aşağıdaki şekil show nasıl **dekorasyonu**, **temel**, ve **Underline** düzenlemelerini işleme, sırasıyla.  
  
 ![Ekran: TextDecorator üst çizgi](./media/inline-textdec-over.png "Inline_TextDec_Over")  
  
 ![Ekran: Varsayılan metin temel etkisi](./media/inline-textdec-base.png "Inline_TextDec_Base")  
  
 ![Ekran: Varsayılan çizgi etkisi olan metin](./media/inline-textdec-under.png "Inline_TextDec_Under")  
  
### <a name="typography"></a>Tipografi  
 <xref:System.Windows.Documents.TextElement.Typography%2A> Özelliği kullanıma sunulan çoğu akışıyla ilgili içerik dahil ederek <xref:System.Windows.Documents.TextElement>, <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Controls.TextBlock>, ve <xref:System.Windows.Controls.TextBox>. Bu özellik, metin (üst ve alt simgeler vb. yapmadan yani küçük veya büyük CAP,) tipografik özellikleri/Çeşitlemeleri denetlemek için kullanılır.  
  
 Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:System.Windows.Documents.TextElement.Typography%2A> özniteliği kullanarak <xref:System.Windows.Documents.Paragraph> örnek öğesi olarak.  
  
 [!code-xaml[TextElementSnippets#_TextElement_TypogXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 Aşağıdaki şekil, bu örneğin nasıl işlediğini gösterir.  
  
 ![Ekran: Değiştirilen tipografi metinle](./media/textelement-typog.png "TextElement_Typog")  
  
 Buna karşılık, varsayılan tipografik özellikleri ile benzer bir örnek nasıl işlediğini aşağıdaki şekilde gösterilmektedir.  
  
 ![Ekran: Değiştirilen tipografi metinle](./media/textelement-typog-default.png "TextElement_Typog_Default")  
  
 Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:System.Windows.Controls.TextBox.Typography%2A> özelliğini program aracılığıyla.  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
 Bkz: [WPF'de tipografi](typography-in-wpf.md) tipografi hakkında daha fazla bilgi için.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Metin](optimizing-performance-text.md)
- [WPF'de Tipografi](typography-in-wpf.md)
- [Nasıl Yapılır Konuları](flow-content-elements-how-to-topics.md)
- [TextElement İçerik Modeline Genel Bakış](textelement-content-model-overview.md)
- [RichTextBox Genel Bakış](../controls/richtextbox-overview.md)
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Tabloya Genel Bakış](table-overview.md)
- [Ek Açıklamalara Genel Bakış](annotations-overview.md)
