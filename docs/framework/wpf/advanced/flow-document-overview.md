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
ms.openlocfilehash: 1dcba034dd934cb0e103cd131fcaa2088e2f93d3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856152"
---
# <a name="flow-document-overview"></a>Akış Belgesine Genel Bakış

Akış belgeleri, görüntüleme ve okunabilirliği iyileştirmek için tasarlanmıştır. Akış belgeleri, önceden tanımlanmış bir düzene ayarlanmaktansa, pencere boyutu, cihaz çözünürlüğü ve isteğe bağlı Kullanıcı tercihleri gibi çalışma zamanı değişkenlerine göre içeriğini dinamik olarak ayarlayıp yeniden düzenler. Ayrıca, akış belgeleri, sayfalandırma ve sütunlar gibi gelişmiş belge özellikleri sunar. Bu konuda, akış belgelerine genel bir bakış ve bunların nasıl oluşturulacağı açıklanır.

<a name="what_is_a_flow_document"></a>

## <a name="what-is-a-flow-document"></a>Flow belgesi nedir?

Akış belgesi, pencere boyutuna, cihaz çözümlemesine ve diğer ortam değişkenlerine bağlı olarak "içeriği yeniden akıtma" için tasarlanmıştır. Ayrıca, akış belgelerinin arama, okunabilirliği en iyileştiren modlar ve yazı tiplerinin boyutunu ve görünümünü değiştirme özelliği dahil olmak üzere çeşitli yerleşik özellikleri vardır. Akış belgeleri, okunması kolay bir şekilde birincil belge tüketim senaryosu olduğunda en iyi şekilde kullanılır. Buna karşılık, sabit belgeler statik bir sunuya sahip olacak şekilde tasarlanmıştır. Sabit belgeler, kaynak içeriğin uygunluğu önemli olduğunda faydalıdır. Farklı belge türleri hakkında daha fazla bilgi için bkz. [WPF Içindeki belgeler](documents-in-wpf.md) .

Aşağıdaki çizimde, farklı boyutlarda birkaç pencere halinde görüntülenen örnek akış belgeleri gösterilmektedir. Görüntüleme alanı değiştikçe, içerik kullanılabilir alanın en iyi şekilde kullanılmasını sağlamak için yeniden akıtıldığında.

![Akış belgesi içerik yeniden akışı](./media/edocs-flowdocument.png "eDocs_FlowDocument")

Yukarıdaki görüntüde görüldüğü gibi, akış içeriği paragraflar, listeler, görüntüler ve daha fazlasını içeren birçok bileşen içerebilir. Bu bileşenler, yordamsal koddaki biçimlendirme ve nesnelerdeki öğelere karşılık gelir. Bu sınıfların daha sonra bu genel bakışın [Flow Ilgili sınıflar](#flow_related_classes) bölümünde ayrıntılı olarak gidecağız. Şimdilik, bazı kalın metin ve liste içeren bir paragraftan oluşan bir akış belgesi oluşturan basit bir kod örneği aşağıda verilmiştir.

[!code-xaml[FlowOvwSnippets_snip#SimpleFlowExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SimpleFlowExample.xaml#simpleflowexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SimpleFlowExample.cs#simpleflowcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SimpleFlowExample.vb#simpleflowcodeonlyexamplewholepage)]

Aşağıdaki çizimde bu kod parçacığının nasıl göründüğü gösterilmektedir.

![Yakala İşlenmiş FlowDocument örnek](./media/flow-ovw-first-example.png "Flow_Ovw_First_Example")

Bu örnekte, <xref:System.Windows.Controls.FlowDocumentReader> akış içeriğini barındırmak için denetim kullanılır. Akış içeriği barındırma denetimleri hakkında daha fazla bilgi için bkz. [Flow belge türleri](#flow_document_types) . <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.List>, ve<xref:System.Windows.Documents.Bold> öğeleri, biçimlendirme sırasına göre içerik biçimlendirmesini denetlemek için kullanılır. <xref:System.Windows.Documents.ListItem> Örneğin, <xref:System.Windows.Documents.Bold> öğe yalnızca paragraftaki metnin bir kısmına yayılır; sonuç olarak, yalnızca metnin bir kısmı kalın olur. HTML kullandıysanız, bu size tanıdık gelecektir.

Yukarıdaki çizimde vurgulanan şekilde, akış belgelerinde yerleşik olarak bulunan çeşitli özellikler vardır:

- Aramanız Kullanıcının tüm belge üzerinde tam metin araması gerçekleştirmesini sağlar.

- Görüntüleme modu: Kullanıcı, tek sayfalı (tek seferlik) görüntüleme modu, iki sayfalı bir zaman (kitap okuma biçimi) görüntüleme modu ve sürekli kaydırma (bottomless) görüntüleme modu dahil olmak üzere tercih edilen görüntüleme modunu seçebilir.  Bu görüntüleme modları hakkında daha fazla bilgi için bkz <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.

- Sayfa gezintisi denetimleri: Belgenin görüntüleme modu sayfalar kullanıyorsa, sayfa gezinti denetimleri sonraki sayfaya (aşağı ok) veya önceki sayfaya (yukarı ok) veya geçerli sayfa numarası ve toplam sayfa sayısı için göstergeler gibi bir düğme içerir. Sayfalar arasında dolaşma, klavye oku tuşları kullanılarak da gerçekleştirilebilir.

- Yakınlaştırma Yakınlaştırma denetimleri, kullanıcının sırasıyla artı veya eksi düğmelerine tıklayarak yakınlaştırma düzeyini arttırmasını veya azaltmasını sağlar. Yakınlaştırma denetimleri, yakınlaştırma düzeyini ayarlamaya yönelik bir kaydırıcı de içerir. Daha fazla bilgi için bkz. <xref:System.Windows.Controls.FlowDocumentReader.Zoom%2A>.

Bu özellikler, akış içeriğini barındırmak için kullanılan denetime göre değiştirilebilir. Sonraki bölümde, farklı denetimler açıklanmıştır.

<a name="flow_document_types"></a>

## <a name="flow-document-types"></a>Akış belge türleri

Flow belgesi içeriğini ve nasıl göründüğünü, akış içeriğini barındırmak için hangi nesnenin kullanıldığı üzerine bağımlıdır. Akış içeriğinin görüntülenmesini destekleyen dört denetim vardır <xref:System.Windows.Controls.FlowDocumentReader>:, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.RichTextBox>ve <xref:System.Windows.Controls.FlowDocumentScrollViewer>. Bu denetimler kısaca aşağıda açıklanmıştır.

> [!NOTE]
> <xref:System.Windows.Documents.FlowDocument>akış içeriğini doğrudan barındırmak için gereklidir, bu nedenle tüm bu görüntüleme denetimleri akış içeriği barındırmayı <xref:System.Windows.Documents.FlowDocument> etkinleştirmek için bir kullanır.

### <a name="flowdocumentreader"></a>FlowDocumentReader

<xref:System.Windows.Controls.FlowDocumentReader>kullanıcının tek sayfalı (sayfa-bir zaman) görüntüleme modu, iki sayfalı bir-bir-bir-bir-bir-bir-bir-saat (kitap okuma biçimi) görüntüleme modu ve sürekli kaydırma (bottomless) görüntüleme modu dahil çeşitli görüntüleme modları arasında dinamik olarak seçim olanağı sağlayan özellikler içerir. Bu görüntüleme modları hakkında daha fazla bilgi için bkz <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>. Farklı görüntüleme modları <xref:System.Windows.Controls.FlowDocumentPageViewer> arasında dinamik olarak geçiş yapma ve <xref:System.Windows.Controls.FlowDocumentScrollViewer> belirli bir görüntüleme modunda düzeltilen daha hafif akış içerik görüntüleyicileri sağlama olanağına sahip olmanız gerekmiyorsa.

### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer ve FlowDocumentScrollViewer

<xref:System.Windows.Controls.FlowDocumentPageViewer>tek seferlik görüntüleme modundaki içeriği gösterir, ancak <xref:System.Windows.Controls.FlowDocumentScrollViewer> içeriği sürekli kaydırma modunda gösterir. Her ikisi de <xref:System.Windows.Controls.FlowDocumentPageViewer> belirli bir görüntüleme moduna sabitlenmiştir. <xref:System.Windows.Controls.FlowDocumentScrollViewer> İle <xref:System.Windows.Controls.FlowDocumentReader>karşılaştırın, kullanıcının çeşitli görüntüleme modları arasında ( <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> numaralandırma tarafından sağlandığı gibi), veya <xref:System.Windows.Controls.FlowDocumentScrollViewer>' den <xref:System.Windows.Controls.FlowDocumentPageViewer> daha fazla kaynak kullanımına sahip olan maliyetten dinamik olarak seçmesini sağlayan özellikler içerir.

Varsayılan olarak, dikey bir kaydırma çubuğu her zaman gösterilir ve gerekirse yatay kaydırma çubuğu görünür hale gelir. İçin <xref:System.Windows.Controls.FlowDocumentScrollViewer> varsayılan kullanıcı arabirimi bir araç çubuğu içermez; ancak <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> , özelliği yerleşik bir araç çubuğunu etkinleştirmek için kullanılabilir.

### <a name="richtextbox"></a>RichTextBox

Kullanıcının akış içeriğini <xref:System.Windows.Controls.RichTextBox> düzenlemesine izin vermek istediğinizde, kullanılır. Örneğin, bir kullanıcının tablolar, italik ve kalın biçimlendirme gibi şeyleri kullanmasına izin veren bir düzenleyici oluşturmak isterseniz, bir <xref:System.Windows.Controls.RichTextBox>kullanabilirsiniz. Daha fazla bilgi için bkz. [RichTextBox genel bakış](../controls/richtextbox-overview.md) .

> [!NOTE]
> A <xref:System.Windows.Controls.RichTextBox> içindeki akış içeriği, diğer denetimlerde yer alan akış içeriği gibi davranır. Örneğin, içinde <xref:System.Windows.Controls.RichTextBox> hiç sütun yok ve bu nedenle otomatik yeniden boyutlandırma davranışı yok. Ayrıca, genellikle arama, görüntüleme modu, sayfa gezintisi ve yakınlaştırma gibi akış içeriğinin yerleşik özellikleri bir <xref:System.Windows.Controls.RichTextBox>içinde kullanılamaz.

<a name="creating_flow_content"></a>

## <a name="creating-flow-content"></a>Akış Içeriği oluşturma

Akış içeriği karmaşık olabilir, metin, görüntüler, tablolar ve hatta <xref:System.Windows.UIElement> denetimler gibi türetilmiş sınıflar gibi çeşitli öğelerden oluşur. Karmaşık akış içeriği oluşturmayı anlamak için aşağıdaki noktaları kritik olarak gösterir:

- **Akışla Ilgili sınıflar**: Akış içeriğinde kullanılan her sınıfın belirli bir amacı vardır. Ayrıca, akış sınıfları arasındaki hiyerarşik ilişki nasıl kullanıldığını anlamanıza yardımcı olur. Örneğin, <xref:System.Windows.Documents.Block> sınıfından türetilen sınıflar, ' den <xref:System.Windows.Documents.Inline> türetilen sınıflar görüntülenen nesneleri içerdiğinde diğer nesneleri içerecek şekilde kullanılır.

- **Içerik şeması**: Flow belgesi, çok sayıda iç içe öğe gerektirebilir. İçerik şeması, öğeler arasında olası üst/alt ilişkileri belirler.

Aşağıdaki bölümler, bu alanların her birine daha ayrıntılı bir şekilde gidecektir.

<a name="flow_related_classes"></a>

## <a name="flow-related-classes"></a>Flow ile Ilgili sınıflar

Aşağıdaki diyagramda, genellikle akış içeriğiyle kullanılan nesneler gösterilmektedir:

![Çizimindeki Flow içerik öğesi sınıf hiyerarşisi](./media/flow-class-hierarchy.png "Flow_Class_Hierarchy")

Akış içeriğinin amaçları doğrultusunda, iki önemli kategori vardır:

1. **Blok türetilmiş sınıflar**: "İçerik öğelerini engelle" veya yalnızca "öğeleri engelle" olarak da bilinir. Öğesinden <xref:System.Windows.Documents.Block> devraldığı öğeler, ortak bir üst öğe altındaki öğeleri gruplandırmak veya bir gruba ortak öznitelikler uygulamak için kullanılabilir.

2. **Satır içi türetilmiş sınıflar**: Ayrıca "satır Içi içerik öğeleri" veya yalnızca "satır Içi öğeler" olarak da bilinir. Öğesinden <xref:System.Windows.Documents.Inline> devraldığı öğeler bir blok öğesi ya da başka bir satır içi öğe içinde yer alır. Satır içi öğeler genellikle ekranda işlenen içeriğin doğrudan kapsayıcısı olarak kullanılır. Örneğin, bir <xref:System.Windows.Documents.Paragraph> (blok öğesi) bir <xref:System.Windows.Documents.Run> (satır içi öğe) içerebilir, <xref:System.Windows.Documents.Run> ancak aslında ekranda işlenen metni içerir.

Bu iki kategorideki her bir sınıf aşağıda kısaca açıklanmıştır.

### <a name="block-derived-classes"></a>Blok türetilmiş sınıflar

**Ina**

<xref:System.Windows.Documents.Paragraph>genellikle içeriği bir paragrafa gruplamak için kullanılır. Paragrafın en basit ve en yaygın kullanımı, bir metin paragrafı oluşturmaktır.

[!code-xaml[FlowOvwSnippets_snip#ParagraphExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ParagraphExample.xaml#paragraphexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ParagraphExample.cs#paragraphcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ParagraphExample.vb#paragraphcodeonlyexamplewholepage)]

Bununla birlikte, aşağıda göreceğiniz gibi diğer satır içi türetilmiş öğeleri de de kullanabilirsiniz.

**Kısmı**

<xref:System.Windows.Documents.Section>yalnızca diğer <xref:System.Windows.Documents.Block>türetilmiş öğeleri içermek için kullanılır. İçerdiği öğelere herhangi bir varsayılan biçimlendirme uygulamaz. Ancak, bir üzerinde ayarlanan herhangi bir <xref:System.Windows.Documents.Section> Özellik değeri, alt öğeleri için geçerlidir. Bir bölüm ayrıca kendi alt koleksiyonu aracılığıyla programlı bir şekilde yineleme yapmanızı sağlar. <xref:System.Windows.Documents.Section>, HTML 'deki \<DIV > etiketine benzer bir şekilde kullanılır.

Aşağıdaki örnekte, üç paragraf bir <xref:System.Windows.Documents.Section>altında tanımlanmıştır. Bölümünde kırmızı bir <xref:System.Windows.Documents.TextElement.Background%2A> Özellik değeri bulunur, bu nedenle paragrafların arka plan rengi de kırmızıdır.

[!code-xaml[FlowOvwSnippets_snip#SectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SectionExample.xaml#sectionexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SectionExample.cs#sectioncodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SectionExample.vb#sectioncodeonlyexamplewholepage)]

**Blockufıcontainer**

<xref:System.Windows.Documents.BlockUIContainer>öğelerin <xref:System.Windows.UIElement> (örn. a <xref:System.Windows.Controls.Button>), blok ile türetilmiş akış içeriğine gömülmesini sağlar. <xref:System.Windows.Documents.InlineUIContainer>(aşağıya bakın) öğeleri satır içi türetilmiş <xref:System.Windows.UIElement> akış içeriğine eklemek için kullanılır. <xref:System.Windows.Documents.BlockUIContainer>ve <xref:System.Windows.Documents.InlineUIContainer> , bu iki öğeden biri içinde bulunmadığı müddetçe Flow içeriğini kullanmanın <xref:System.Windows.UIElement> başka bir yolu olmadığından önemlidir.

Aşağıdaki örnek, akış içeriği içinde nesneleri barındırmak <xref:System.Windows.Documents.BlockUIContainer> <xref:System.Windows.UIElement> için öğesinin nasıl kullanılacağını gösterir.

[!code-xaml[SpanSnippets#_BlockUIXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml#_blockuixaml)]

Aşağıdaki şekilde bu örneğin nasıl işlediğini gösterilmektedir:

![Akış içeriğine gömülü bir UIElement gösteren ekran görüntüsü.](./media/flow-document-overview/embedded-blockuicontainer.png)

**Liste**

<xref:System.Windows.Documents.List>Madde işaretli veya sayısal bir liste oluşturmak için kullanılır. Listenin stilini belirleyebilmek için <xref:System.Windows.TextMarkerStyle> özelliğibirnumaralandırmadeğeriolarakayarlayın.<xref:System.Windows.Documents.List.MarkerStyle%2A> Aşağıdaki örnekte nasıl basit bir liste oluşturulacağı gösterilmektedir.

[!code-xaml[FlowOvwSnippets_snip#ListExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ListExample.xaml#listexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ListExample.cs#listcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ListExample.vb#listcodeonlyexamplewholepage)]

> [!NOTE]
> <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItemCollection> alt öğeleri yönetmek için kullanan tek Flow öğesidir.

**Tablo**

<xref:System.Windows.Documents.Table>bir tablo oluşturmak için kullanılır. <xref:System.Windows.Documents.Table><xref:System.Windows.Controls.Grid> öğesi ile benzerdir, ancak daha fazla özelliğe sahiptir ve bu nedenle daha fazla kaynak yükü gerektirir. Bir olduğundan, <xref:System.Windows.Documents.BlockUIContainer> veya içinde<xref:System.Windows.Documents.InlineUIContainer>içerilmediği takdirde akış içeriğinde kullanılamaz. <xref:System.Windows.Controls.Grid> <xref:System.Windows.UIElement> Hakkında <xref:System.Windows.Documents.Table>daha fazla bilgi için bkz. [tabloya genel bakış](table-overview.md).

### <a name="inline-derived-classes"></a>Satır içi türetilmiş sınıflar

**Çalıştır**

<xref:System.Windows.Documents.Run>biçimlendirilmemiş metin içermesi için kullanılır. Akış içeriğinde kapsamlı <xref:System.Windows.Documents.Run> olarak kullanılacak nesneleri beklemeniz gerekebilir. Ancak, biçimlendirme <xref:System.Windows.Documents.Run> ' de öğelerin açıkça kullanılması gerekmez. <xref:System.Windows.Documents.Run>kod kullanarak akış belgeleri oluştururken veya düzenleme sırasında kullanılması gerekir. Örneğin, aşağıdaki biçimlendirmede ilki, ikinci kez <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Run> öğesini açıkça belirtir. Her iki paragraf de özdeş çıkış oluşturur.

[!code-xaml[FlowOvwSnippets_snip#RunExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/RunSnippetsExample.xaml#runexample1)]

> [!NOTE]
> .NET Framework 4 ' te başlayarak, <xref:System.Windows.Documents.Run.Text%2A> <xref:System.Windows.Documents.Run> nesnesinin özelliği bir bağımlılık özelliğidir. <xref:System.Windows.Documents.Run.Text%2A> Özelliğini ,<xref:System.Windows.Controls.TextBlock>gibi bir veri kaynağına bağlayabilirsiniz. <xref:System.Windows.Documents.Run.Text%2A> Özelliği tek yönlü bağlamayı tam olarak destekler. Özelliği, hariç olmak üzere <xref:System.Windows.Controls.RichTextBox>iki yönlü bağlamayı da destekler. <xref:System.Windows.Documents.Run.Text%2A> Örnek için bkz. <xref:System.Windows.Documents.Run.Text%2A?displayProperty=nameWithType>

**Kapsamı**

<xref:System.Windows.Documents.Span>diğer satır içi içerik öğelerini birlikte gruplandırır. Bir <xref:System.Windows.Documents.Span> öğe içindeki içeriğe hiçbir devralınmış işleme uygulanmaz. <xref:System.Windows.Documents.Span> Ancak,, ve<xref:System.Windows.Documents.Italic> dahil <xref:System.Windows.Documents.Hyperlink>,, ve<xref:System.Windows.Documents.Underline> ' den devralma öğeleri metne biçimlendirme uygular. <xref:System.Windows.Documents.Bold>

Aşağıda metin <xref:System.Windows.Documents.Span> <xref:System.Windows.Documents.Bold> , öğe ve <xref:System.Windows.Controls.Button>içeren satır içi içerik içeren bir örneği verilmiştir.

[!code-xaml[FlowOvwSnippets_snip#SpanExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SpanExample.xaml#spanexamplewholepage)]

Aşağıdaki ekran görüntüsünde bu örneğin nasıl işlediğini gösterilmektedir.

![Yakala İşlenmiş span örneği](./media/flow-spanexample.gif "Flow_SpanExample")

**Inlineuiconcontainer**

<xref:System.Windows.Documents.InlineUIContainer>bir <xref:System.Windows.UIElement> <xref:System.Windows.Documents.Inline> içerik öğesine katıştırılması için öğeleri ( <xref:System.Windows.Controls.Button>Örneğin, gibi bir denetimi) sağlar. Bu öğe yukarıda <xref:System.Windows.Documents.BlockUIContainer> açıklanan satır içi eştir. Aşağıda içine <xref:System.Windows.Documents.InlineUIContainer> satıriçi<xref:System.Windows.Controls.Button> eklemek için kullanılan bir örnek verilmiştir. <xref:System.Windows.Documents.Paragraph>

[!code-xaml[FlowOvwSnippets_snip#InlineUIContainerExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/InlineUIContainerExample.xaml#inlineuicontainerexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/InlineUIContainerExample.cs#inlineuicontainercodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/InlineUIContainerExample.vb#inlineuicontainercodeonlyexamplewholepage)]

> [!NOTE]
> <xref:System.Windows.Documents.InlineUIContainer>açıkça biçimlendirmede kullanılması gerekmez. Bunu atlarsanız, <xref:System.Windows.Documents.InlineUIContainer> kod derlendiğinde yine de oluşturulur.

**Şekil ve Floater**

<xref:System.Windows.Documents.Figure>ve <xref:System.Windows.Documents.Floater> , birincil içerik akışından bağımsız olarak özelleştirilebilecek yerleştirme özellikleriyle akış belgelerine içerik eklemek için kullanılır. <xref:System.Windows.Documents.Figure>ya <xref:System.Windows.Documents.Floater> da öğeler genellikle içeriğin bölümlerini vurgulamak veya tasarımın, ana içerik akışında destekleyici görüntüleri veya diğer içerikleri barındırmak ya da reklamlar gibi gevşek ilişkili içerikleri eklemek için kullanılır.

Aşağıdaki örnek, bir <xref:System.Windows.Documents.Figure> metin paragrafına nasıl ekleneceğini gösterir.

[!code-xaml[FlowOvwSnippets_snip#FigureExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/FigureExample.xaml#figureexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/FigureExample.cs#figurecodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/FigureExample.vb#figurecodeonlyexamplewholepage)]

Aşağıdaki çizimde bu örneğin nasıl işlediğini gösterilmektedir.

![Yakala Şekil örneği](./media/flow-ovw-figure-example.png "Flow_Ovw_Figure_Example")

<xref:System.Windows.Documents.Figure>ve <xref:System.Windows.Documents.Floater> çeşitli yollarla farklılık gösterir ve farklı senaryolar için kullanılır.

**Rakam**

- Konumlandırılmış olabilir: Yatay ve dikey tutturucularını sayfa, içerik, sütun veya paragrafa göre yerleştirmek için ayarlayabilirsiniz. Ayrıca, <xref:System.Windows.Documents.Figure.HorizontalOffset%2A> ve <xref:System.Windows.Documents.Figure.VerticalOffset%2A> özelliklerini rastgele uzaklıklar belirtmek için de kullanabilirsiniz.

- Birden fazla sütuna boyutlandırılabilir: Yükseklik ve Genişlik <xref:System.Windows.Documents.Figure> sayfasının, içeriğin veya sütun yüksekliğinin ya da genişliğinin katları olarak ayarlayabilirsiniz. Sayfa ve içerik söz konusu olduğunda, 1 ' den büyük katlara izin verilmeyeceğini unutmayın. Örneğin, a <xref:System.Windows.Documents.Figure> genişliğini "0,5 Page" veya "0,25 Content" veya "2 Column" olarak ayarlayabilirsiniz. Yükseklik ve Genişlik ' i mutlak piksel değerlerine da ayarlayabilirsiniz.

- Sayfalamaz: A <xref:System.Windows.Documents.Figure> içindeki içerik <xref:System.Windows.Documents.Figure>içine uymuyorsa, içeriğin sığması ve kalan içeriğin kaybedilmesi gerekir

**Floater:**

- Konumlandırılamıyor ve kullanılabilir alan olduğu her yerde işleme alınacaktır. Sapmayı veya bağlantısını <xref:System.Windows.Documents.Floater>ayarlayamazsınız.

- Birden fazla sütuna boyutlandırılabilir: Varsayılan olarak, <xref:System.Windows.Documents.Floater> bir sütundaki boyutlar. Mutlak piksel değerine <xref:System.Windows.Documents.Floater.Width%2A> ayarlanılabilen bir özelliği vardır, ancak bu değer bir sütun genişliğinden büyükse yok sayılır ve Floater bir sütunda boyutlandırılır. Doğru piksel genişliğini ayarlayarak, boyutu bir sütundan daha az bir sütuna göre boyutlandırabilir, ancak boyutlandırma sütun göreli değildir, bu nedenle "0,5 sütun" Width için <xref:System.Windows.Documents.Floater> geçerli bir ifade değildir. <xref:System.Windows.Documents.Floater>Height özelliği yok ve bu yükseklik ayarlanamaz, bu da içeriğe bağlıdır

- <xref:System.Windows.Documents.Floater>sayfalanan: Belirtilen genişlikdeki içeriği 1 ' den fazla sütun yüksekliğine genişlerse, Floater ve sonraki sütun, sonraki sayfa vb. için kesme ve sayfalaştırır.

 <xref:System.Windows.Documents.Figure>Boyut ve konumlandırmayı denetlemek istediğiniz tek başına içerikleri yerleştirmek için iyi bir yerdir ve içeriğin belirtilen boyuta sığması önemlidir. <xref:System.Windows.Documents.Floater>Ana sayfa içeriğine benzer, ancak bundan ayrıldığından, akan daha fazla serbest akışlı içerik yerleştirmek için iyi bir yerdir.

**LineBreak**

<xref:System.Windows.Documents.LineBreak>akış içeriğinde satır sonu oluşmasına neden olur. Aşağıdaki örnek öğesinin <xref:System.Windows.Documents.LineBreak>kullanımını gösterir.

[!code-xaml[FlowOvwSnippets_snip#LineBreakExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/LineBreakExample.xaml#linebreakexamplewholepage)]

Aşağıdaki ekran görüntüsünde bu örneğin nasıl işlediğini gösterilmektedir.

![Yakala LineBreak örnek](./media/flow-ovw-linebreakexample.png "Flow_Ovw_LineBreakExample")

### <a name="flow-collection-elements"></a>Akış koleksiyonu öğeleri

Yukarıdaki örneklerin çoğunda, <xref:System.Windows.Documents.BlockCollection> ve <xref:System.Windows.Documents.InlineCollection> , akış içeriğini programlı bir şekilde oluşturmak için kullanılır. Örneğin, öğesine <xref:System.Windows.Documents.Paragraph>öğe eklemek için söz dizimini kullanabilirsiniz:

```csharp
myParagraph.Inlines.Add(new Run("Some text"));
```

Bu <xref:System.Windows.Documents.Run> öğesineöğesine<xref:System.Windows.Documents.Paragraph>ekler. <xref:System.Windows.Documents.InlineCollection>  Bu, bir <xref:System.Windows.Documents.Paragraph> ın biçimlendirmesinde bulunan örtülü <xref:System.Windows.Documents.Run> ile aynıdır:

```xml
<Paragraph>
Some Text
</Paragraph>
```

<xref:System.Windows.Documents.BlockCollection>Öğesinin kullanılmasına örnek olarak, aşağıdaki örnek yeni <xref:System.Windows.Documents.Section> bir oluşturur ve sonra yeni <xref:System.Windows.Documents.Paragraph> bir <xref:System.Windows.Documents.Section> içerik eklemek için **Add** yöntemini kullanır.

[!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
[!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]

Akış koleksiyonuna öğe eklemenin yanı sıra öğeleri de kaldırabilirsiniz.  Aşağıdaki örnek, <xref:System.Windows.Documents.Inline> <xref:System.Windows.Documents.Span>içindeki son öğeyi siler.

[!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
[!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]

Aşağıdaki örnek,<xref:System.Windows.Documents.Inline> <xref:System.Windows.Documents.Span>içindeki tüm içeriği (öğeleri) temizler.

[!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
[!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]

Program aracılığıyla akış içeriğiyle çalışırken, büyük olasılıkla bu koleksiyonların kapsamlı bir şekilde kullanılmasını sağlayabilirsiniz.

Bir akış öğesinin alt öğelerini içermesi <xref:System.Windows.Documents.InlineCollection> için bir (Inlines <xref:System.Windows.Documents.BlockCollection> ) veya (bloklar) kullanması, üst öğe tarafından hangi tür alt öğelerin (<xref:System.Windows.Documents.Block> veya <xref:System.Windows.Documents.Inline>) dahil edilip edilmeyeceğini belirtir. Akış içeriği öğeleri için kapsama kuralları, sonraki bölümde içerik şemasında özetlenir.

> [!NOTE]
> Akış içeriğiyle <xref:System.Windows.Documents.ListItemCollection>kullanılan üçüncü bir tür koleksiyon vardır, ancak bu koleksiyon yalnızca bir <xref:System.Windows.Documents.List>ile kullanılır. Ayrıca, ile birlikte <xref:System.Windows.Documents.Table>kullanılan birkaç koleksiyon vardır. Daha fazla bilgi için bkz. [tabloya genel bakış](table-overview.md) .

<a name="content_schema"></a>

## <a name="content-schema"></a>İçerik şeması

Farklı akış içeriği öğelerinin sayısı verildiğinde, bir öğenin içerebileceği alt öğe türlerini izlemek çok fazla olabilir. Aşağıdaki diyagramda Flow öğelerinin kapsama kuralları özetlenmektedir. Oklar olası üst/alt ilişkileri temsil eder.

![Çizimindeki Flow içerik kapsama şeması](./media/flow-content-schema.png "Flow_Content_Schema")

Yukarıdaki diyagramdan görünebileceği gibi, bir öğe için izin verilen alt öğeler bir <xref:System.Windows.Documents.Block> öğe <xref:System.Windows.Documents.Inline> veya öğe olup olmadığı tarafından belirlenmeyebilir. <xref:System.Windows.Documents.Span> Örneğin, bir <xref:System.Windows.Documents.Inline> (bir öğe) yalnızca alt öğelere <xref:System.Windows.Documents.Figure> sahip <xref:System.Windows.Documents.Inline> olsa da (aynı zamanda <xref:System.Windows.Documents.Inline> bir öğe) yalnızca <xref:System.Windows.Documents.Block> alt öğeleri olabilir. Bu nedenle, bir diyagram, başka bir öğenin hangi öğeye dahil edilebilir olduğunu hızlı bir şekilde belirlemek için faydalıdır. Örnek olarak, ' ın <xref:System.Windows.Controls.RichTextBox>akış içeriğinin nasıl oluşturulacağını öğrenmek için diyagramı kullanalım.

**1.** , ' In bir <xref:System.Windows.Documents.FlowDocument> iletüretilmişnesneiçermesigerekenbiriçermelidir.<xref:System.Windows.Documents.Block> <xref:System.Windows.Controls.RichTextBox> Yukarıdaki diyagramda karşılık gelen segment aşağıda verilmiştir.

![Çizimindeki RichTextBox kapsama kuralları](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")

Bu nedenle, biçimlendirmenin şu şekilde görünebileceğini burada bulabilirsiniz.

[!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]

**2.** Diyagrama göre,,, <xref:System.Windows.Documents.Block> , ve <xref:System.Windows.Documents.Section> <xref:System.Windows.Documents.Table> <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.List>dahil olmaküzereseçebileceğinizbirkaçöğevardır(yukarıdakibloktüretilmişsınıflarabakın)<xref:System.Windows.Documents.BlockUIContainer> . Diyelim ki bir <xref:System.Windows.Documents.Table>. <xref:System.Windows.Documents.Table> Yukarıdaki diyagrama göre, bir <xref:System.Windows.Documents.TableRow> içerenöğeleriiçerenbir<xref:System.Windows.Documents.TableRowGroup> öğesi içerir.<xref:System.Windows.Documents.Block> <xref:System.Windows.Documents.TableCell> Yukarıdaki diyagramdan <xref:System.Windows.Documents.Table> alınan karşılık gelen segment aşağıda verilmiştir.

![Çizimindeki &#47;Tablo](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2") için üst alt şema

Karşılık gelen biçimlendirme aşağıda verilmiştir.

[!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]

**3.** Yine, bir veya daha <xref:System.Windows.Documents.Block> fazla öğe bir <xref:System.Windows.Documents.TableCell>altında gereklidir. Basit hale getirmek için hücrenin içine biraz metin yerleştirelim. Bunu bir <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Run> öğesi ile kullanarak yapabiliriz. Aşağıda <xref:System.Windows.Documents.Paragraph> , bir <xref:System.Windows.Documents.Inline> öğenin <xref:System.Windows.Documents.Run> ( biröğe)yalnızcadüzmetinalabilirolduğunugösterendiyagramdakarşılıkgelensegmentlerverilmiştir.<xref:System.Windows.Documents.Inline>

![Çizimindeki &#47;Paragraf](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3") için üst alt şema

![Çizimindeki &#47;Run](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4") için üst alt şema

Aşağıda, biçimlendirme içindeki tüm örnek verilmiştir.

[!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]

<a name="customizing_text"></a>

## <a name="customizing-text"></a>Metni özelleştirme

Genellikle metin bir akış belgesinde en yaygın içerik türüdür. Yukarıdaki nesneler, metnin nasıl işlendiğine ilişkin birçok yönü denetlemek için kullanılabilir olsa da, bu bölümde ele alınan metni özelleştirmek için başka yöntemler de vardır.

### <a name="text-decorations"></a>Metin süslemeleri

Metin süslemeleri metne alt çizgi, üst çizgi, taban çizgisi ve üstü çizili etkileri uygulamanıza olanak tanır (aşağıdaki resimlere bakın). Bu düzenlemeleriniz,,, <xref:System.Windows.Documents.Inline.TextDecorations%2A> ve <xref:System.Windows.Documents.Inline> <xref:System.Windows.Documents.Paragraph> dahil<xref:System.Windows.Controls.TextBox>olmak üzere <xref:System.Windows.Controls.TextBlock>bir dizi nesne tarafından kullanıma sunulan özelliği kullanılarak eklenir.

Aşağıdaki örnek, <xref:System.Windows.Documents.Paragraph.TextDecorations%2A> <xref:System.Windows.Documents.Paragraph>öğesinin özelliğinin nasıl ayarlanacağını gösterir.

[!code-xaml[InlineSnippets#_Paragraph_TextDecXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml#_paragraph_textdecxaml)]

[!code-csharp[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml.cs#_paragraph_textdec)]
[!code-vb[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InlineSnippets/visualbasic/window1.xaml.vb#_paragraph_textdec)]

Aşağıdaki şekilde, bu örneğin nasıl işlediğini gösterilmektedir.

![Yakala Varsayılan üstü çizgili efektli]metin(./media/inline-textdec-strike.png "Inline_TextDec_Strike")

Aşağıdaki rakamlar, sırasıyla **üst çizgi**, **taban çizgisi**ve **alt çizgi** düzenlemelerinin nasıl işleneceğini gösterir.

![Yakala Üst çizgi textdekoratör](./media/inline-textdec-over.png "Inline_TextDec_Over")

![Yakala Metin](./media/inline-textdec-base.png "Inline_TextDec_Base") üzerinde varsayılan temel efekt

![Yakala Varsayılan altı çizili etkiyle]metin(./media/inline-textdec-under.png "Inline_TextDec_Under")

### <a name="typography"></a>Tipografi

Özelliği,<xref:System.Windows.Documents.FlowDocument> ,,<xref:System.Windows.Controls.TextBox>ve dahil olmak üzere <xref:System.Windows.Documents.TextElement>akışla ilgili içerikler tarafından sunulur. <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Documents.TextElement.Typography%2A> Bu özellik, metnin tipografik karakteristiklerini/çeşitlemelerini (küçük veya büyük harfler, üst simgeler ve alt simgeler, vb.) denetlemek için kullanılır.

Aşağıdaki örnek, örnek öğesi olarak kullanarak <xref:System.Windows.Documents.TextElement.Typography%2A> <xref:System.Windows.Documents.Paragraph> özniteliğinin nasıl ayarlanacağını gösterir.

[!code-xaml[TextElementSnippets#_TextElement_TypogXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]

Aşağıdaki şekilde, bu örneğin nasıl işlediğini gösterilmektedir.

![Yakala Değiştirilen Tipografisi](./media/textelement-typog.png "TextElement_Typog") metin

Buna karşılık aşağıdaki şekilde, varsayılan tipografik özelliklerle benzer bir örneğin nasıl işlediğini gösterilmektedir.

![Yakala Değiştirilen Tipografisi](./media/textelement-typog-default.png "TextElement_Typog_Default") metin

Aşağıdaki örnek, <xref:System.Windows.Controls.TextBox.Typography%2A> özelliğinin programlı olarak nasıl ayarlanacağını gösterir.

[!code-csharp[TextElementSnippets#_TextElement_Typog](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
[!code-vb[TextElementSnippets#_TextElement_Typog](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]

Tipografi hakkında daha fazla bilgi için bkz. [WPF 'de tipografi](typography-in-wpf.md) .

## <a name="see-also"></a>Ayrıca bkz.

- [Metin](optimizing-performance-text.md)
- [WPF'de Tipografi](typography-in-wpf.md)
- [Nasıl Yapılır Konuları](flow-content-elements-how-to-topics.md)
- [TextElement İçerik Modeline Genel Bakış](textelement-content-model-overview.md)
- [RichTextBox Genel Bakış](../controls/richtextbox-overview.md)
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Tabloya Genel Bakış](table-overview.md)
- [Ek Açıklamalara Genel Bakış](annotations-overview.md)
