---
title: Akış Belgesine Genel Bakış
description: Pencere boyutuna, cihaz çözümlemesine ve kullanıcı tercihlerine göre içeriği dinamik olarak ayarlama Windows Presentation Foundation içindeki akış belgeleri hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'documents [WPF], flow documents [WPF], , '
- ', '
- flow documents [WPF]
ms.assetid: ef236a50-d44f-43c8-ba7c-82b0c733c0b7
ms.openlocfilehash: dac0cb91175a1398a0124020c048e14d7bcd1f76
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165240"
---
# <a name="flow-document-overview"></a>Akış Belgesine Genel Bakış

Akış belgeleri, görüntüleme ve okunabilirliği iyileştirmek için tasarlanmıştır. Akış belgeleri, önceden tanımlanmış bir düzene ayarlanmaktansa, pencere boyutu, cihaz çözünürlüğü ve isteğe bağlı Kullanıcı tercihleri gibi çalışma zamanı değişkenlerine göre içeriğini dinamik olarak ayarlayıp yeniden düzenler. Ayrıca, akış belgeleri, sayfalandırma ve sütunlar gibi gelişmiş belge özellikleri sunar. Bu konuda, akış belgelerine genel bir bakış ve bunların nasıl oluşturulacağı açıklanır.

<a name="what_is_a_flow_document"></a>

## <a name="what-is-a-flow-document"></a>Flow belgesi nedir?

Akış belgesi, pencere boyutuna, cihaz çözümlemesine ve diğer ortam değişkenlerine bağlı olarak "içeriği yeniden akıtma" için tasarlanmıştır. Ayrıca, akış belgelerinin arama, okunabilirliği en iyileştiren modlar ve yazı tiplerinin boyutunu ve görünümünü değiştirme özelliği dahil olmak üzere çeşitli yerleşik özellikleri vardır. Akış belgeleri, okunması kolay bir şekilde birincil belge tüketim senaryosu olduğunda en iyi şekilde kullanılır. Buna karşılık, sabit belgeler statik bir sunuya sahip olacak şekilde tasarlanmıştır. Sabit belgeler, kaynak içeriğin uygunluğu önemli olduğunda faydalıdır. Farklı belge türleri hakkında daha fazla bilgi için bkz. [WPF Içindeki belgeler](documents-in-wpf.md) .

Aşağıdaki çizimde, farklı boyutlarda birkaç pencere halinde görüntülenen örnek akış belgeleri gösterilmektedir. Görüntüleme alanı değiştikçe, içerik kullanılabilir alanın en iyi şekilde kullanılmasını sağlamak için yeniden akıtıldığında.

![Akış belgesi Içerik yeniden akışı](./media/edocs-flowdocument.png "eDocs_FlowDocument")

Yukarıdaki görüntüde görüldüğü gibi, akış içeriği paragraflar, listeler, görüntüler ve daha fazlasını içeren birçok bileşen içerebilir. Bu bileşenler, yordamsal koddaki biçimlendirme ve nesnelerdeki öğelere karşılık gelir. Bu sınıfların daha sonra bu genel bakışın [Flow Ilgili sınıflar](#flow_related_classes) bölümünde ayrıntılı olarak gidecağız. Şimdilik, bazı kalın metin ve liste içeren bir paragraftan oluşan bir akış belgesi oluşturan basit bir kod örneği aşağıda verilmiştir.

[!code-xaml[FlowOvwSnippets_snip#SimpleFlowExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SimpleFlowExample.xaml#simpleflowexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SimpleFlowExample.cs#simpleflowcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SimpleFlowExample.vb#simpleflowcodeonlyexamplewholepage)]

Aşağıdaki çizimde bu kod parçacığının nasıl göründüğü gösterilmektedir.

![Ekran görüntüsü: Işlenen FlowDocument örneği](./media/flow-ovw-first-example.png "Flow_Ovw_First_Example")

Bu örnekte, <xref:System.Windows.Controls.FlowDocumentReader> akış içeriğini barındırmak için denetim kullanılır. Akış içeriği barındırma denetimleri hakkında daha fazla bilgi için bkz. [Flow belge türleri](#flow_document_types) . <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.List> , <xref:System.Windows.Documents.ListItem> ve <xref:System.Windows.Documents.Bold> öğeleri, biçimlendirme sırasına göre içerik biçimlendirmesini denetlemek için kullanılır. Örneğin, <xref:System.Windows.Documents.Bold> öğe yalnızca paragraftaki metnin bir kısmına yayılır; sonuç olarak, yalnızca metnin bir kısmı kalın olur. HTML kullandıysanız, bu size tanıdık gelecektir.

Yukarıdaki çizimde vurgulanan şekilde, akış belgelerinde yerleşik olarak bulunan çeşitli özellikler vardır:

- Arama: kullanıcının belgenin tamamında tam metin araması gerçekleştirmesini sağlar.

- Görüntüleme modu: Kullanıcı, tercih edilen görüntüleme modunu tek sayfalı (tek seferlik) görüntüleme modu, iki sayfalı bir-sayfa (kitap okuma biçimi) görüntüleme modu ve sürekli kaydırma (bottomless) görüntüleme modu dahil edebilir.  Bu görüntüleme modları hakkında daha fazla bilgi için bkz <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> ..

- Sayfa gezintisi denetimleri: belgenin görüntüleme modu sayfalar kullanıyorsa, sayfa gezinti denetimleri sonraki sayfaya (aşağı ok) veya önceki sayfaya (yukarı ok) veya geçerli sayfa numarası ve toplam sayfa sayısı için göstergeler gibi bir düğme içerir. Sayfalar arasında dolaşma, klavye oku tuşları kullanılarak da gerçekleştirilebilir.

- Yakınlaştır: yakınlaştırma denetimleri, kullanıcının sırasıyla artı veya eksi düğmelerine tıklayarak yakınlaştırma düzeyini arttırmasını veya azaltmasını sağlar. Yakınlaştırma denetimleri, yakınlaştırma düzeyini ayarlamaya yönelik bir kaydırıcı de içerir. Daha fazla bilgi için bkz. <xref:System.Windows.Controls.FlowDocumentReader.Zoom%2A>.

Bu özellikler, akış içeriğini barındırmak için kullanılan denetime göre değiştirilebilir. Sonraki bölümde, farklı denetimler açıklanmıştır.

<a name="flow_document_types"></a>

## <a name="flow-document-types"></a>Akış belge türleri

Flow belgesi içeriğini ve nasıl göründüğünü, akış içeriğini barındırmak için hangi nesnenin kullanıldığı üzerine bağımlıdır. Akış içeriğinin görüntülenmesini destekleyen dört denetim vardır: <xref:System.Windows.Controls.FlowDocumentReader> , <xref:System.Windows.Controls.FlowDocumentPageViewer> , <xref:System.Windows.Controls.RichTextBox> ve <xref:System.Windows.Controls.FlowDocumentScrollViewer> . Bu denetimler kısaca aşağıda açıklanmıştır.

> [!NOTE]
> <xref:System.Windows.Documents.FlowDocument>akış içeriğini doğrudan barındırmak için gereklidir, bu nedenle tüm bu görüntüleme denetimleri <xref:System.Windows.Documents.FlowDocument> akış içeriği barındırmayı etkinleştirmek için bir kullanır.

### <a name="flowdocumentreader"></a>FlowDocumentReader

<xref:System.Windows.Controls.FlowDocumentReader>kullanıcının tek sayfalı (sayfa-bir zaman) görüntüleme modu, iki sayfalı bir-bir-bir-bir-bir-bir-bir-saat (kitap okuma biçimi) görüntüleme modu ve sürekli kaydırma (bottomless) görüntüleme modu dahil çeşitli görüntüleme modları arasında dinamik olarak seçim olanağı sağlayan özellikler içerir. Bu görüntüleme modları hakkında daha fazla bilgi için bkz <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> .. Farklı görüntüleme modları arasında dinamik olarak geçiş yapma <xref:System.Windows.Controls.FlowDocumentPageViewer> ve <xref:System.Windows.Controls.FlowDocumentScrollViewer> belirli bir görüntüleme modunda düzeltilen daha hafif akış içerik görüntüleyicileri sağlama olanağına sahip olmanız gerekmiyorsa.

### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer ve FlowDocumentScrollViewer

<xref:System.Windows.Controls.FlowDocumentPageViewer>tek seferlik görüntüleme modundaki içeriği gösterir, ancak <xref:System.Windows.Controls.FlowDocumentScrollViewer> içeriği sürekli kaydırma modunda gösterir. Her ikisi de <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentScrollViewer> belirli bir görüntüleme moduna sabitlenmiştir. İle karşılaştırın <xref:System.Windows.Controls.FlowDocumentReader> , kullanıcının çeşitli görüntüleme modları arasında (numaralandırma tarafından sağlandığı gibi <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> ), veya ' den daha fazla kaynak kullanımına sahip olan maliyetten dinamik olarak seçmesini sağlayan özellikler içerir <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentScrollViewer> .

Varsayılan olarak, dikey bir kaydırma çubuğu her zaman gösterilir ve gerekirse yatay kaydırma çubuğu görünür hale gelir. İçin varsayılan kullanıcı arabirimi <xref:System.Windows.Controls.FlowDocumentScrollViewer> bir araç çubuğu içermez; ancak, <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> özelliği yerleşik bir araç çubuğunu etkinleştirmek için kullanılabilir.

### <a name="richtextbox"></a>RichTextBox

<xref:System.Windows.Controls.RichTextBox>Kullanıcının akış içeriğini düzenlemesine izin vermek istediğinizde, kullanılır. Örneğin, bir kullanıcının tablolar, italik ve kalın biçimlendirme gibi şeyleri kullanmasına izin veren bir düzenleyici oluşturmak isterseniz, bir kullanabilirsiniz <xref:System.Windows.Controls.RichTextBox> . Daha fazla bilgi için bkz. [RichTextBox genel bakış](../controls/richtextbox-overview.md) .

> [!NOTE]
> A içindeki akış içeriği <xref:System.Windows.Controls.RichTextBox> , diğer denetimlerde yer alan akış içeriği gibi davranır. Örneğin, içinde hiç sütun yok <xref:System.Windows.Controls.RichTextBox> ve bu nedenle otomatik yeniden boyutlandırma davranışı yok. Ayrıca, genellikle arama, görüntüleme modu, sayfa gezintisi ve yakınlaştırma gibi akış içeriğinin yerleşik özellikleri bir içinde kullanılamaz <xref:System.Windows.Controls.RichTextBox> .

<a name="creating_flow_content"></a>

## <a name="creating-flow-content"></a>Akış Içeriği oluşturma

Akış içeriği karmaşık olabilir, metin, görüntüler, tablolar ve hatta <xref:System.Windows.UIElement> denetimler gibi türetilmiş sınıflar gibi çeşitli öğelerden oluşur. Karmaşık akış içeriği oluşturmayı anlamak için aşağıdaki noktaları kritik olarak gösterir:

- **Akışla Ilgili sınıflar**: akış içeriğinde kullanılan her sınıfın belirli bir amacı vardır. Ayrıca, akış sınıfları arasındaki hiyerarşik ilişki nasıl kullanıldığını anlamanıza yardımcı olur. Örneğin, sınıfından türetilen sınıflar, ' <xref:System.Windows.Documents.Block> den türetilen sınıflar görüntülenen nesneleri içerdiğinde diğer nesneleri içerecek şekilde kullanılır <xref:System.Windows.Documents.Inline> .

- **Içerik şeması**: bir akış belgesi, çok sayıda iç içe geçmiş öğe gerektirebilir. İçerik şeması, öğeler arasında olası üst/alt ilişkileri belirler.

Aşağıdaki bölümler, bu alanların her birine daha ayrıntılı bir şekilde gidecektir.

<a name="flow_related_classes"></a>

## <a name="flow-related-classes"></a>Flow ile Ilgili sınıflar

Aşağıdaki diyagramda, genellikle akış içeriğiyle kullanılan nesneler gösterilmektedir:

![Diyagram: akış içeriği öğe sınıfı hiyerarşisi](./media/flow-class-hierarchy.png "Flow_Class_Hierarchy")

Akış içeriğinin amaçları doğrultusunda, iki önemli kategori vardır:

1. **Block ile türetilmiş sınıflar**: "Içerik öğelerini engelle" veya yalnızca "blok öğeleri" olarak da bilinir. Öğesinden devraldığı öğeler <xref:System.Windows.Documents.Block> , ortak bir üst öğe altındaki öğeleri gruplandırmak veya bir gruba ortak öznitelikler uygulamak için kullanılabilir.

2. **Satır içi türetilmiş sınıflar**: "satır içi içerik öğeleri" veya yalnızca "satır içi öğeler" olarak da adlandırılır. Öğesinden devraldığı öğeler <xref:System.Windows.Documents.Inline> bir blok öğesi ya da başka bir satır Içi öğe içinde yer alır. Satır içi öğeler genellikle ekranda işlenen içeriğin doğrudan kapsayıcısı olarak kullanılır. Örneğin, bir <xref:System.Windows.Documents.Paragraph> (blok öğesi) bir <xref:System.Windows.Documents.Run> (satır içi öğe) içerebilir, ancak <xref:System.Windows.Documents.Run> aslında ekranda işlenen metni içerir.

Bu iki kategorideki her bir sınıf aşağıda kısaca açıklanmıştır.

### <a name="block-derived-classes"></a>Blok türetilmiş sınıflar

**Paragraf**

<xref:System.Windows.Documents.Paragraph>genellikle içeriği bir paragrafa gruplamak için kullanılır. Paragrafın en basit ve en yaygın kullanımı, bir metin paragrafı oluşturmaktır.

[!code-xaml[FlowOvwSnippets_snip#ParagraphExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ParagraphExample.xaml#paragraphexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ParagraphExample.cs#paragraphcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ParagraphExample.vb#paragraphcodeonlyexamplewholepage)]

Bununla birlikte, aşağıda göreceğiniz gibi diğer satır içi türetilmiş öğeleri de de kullanabilirsiniz.

**Section**

<xref:System.Windows.Documents.Section>yalnızca diğer türetilmiş öğeleri içermek için kullanılır <xref:System.Windows.Documents.Block> . İçerdiği öğelere herhangi bir varsayılan biçimlendirme uygulamaz. Ancak, bir üzerinde ayarlanan herhangi bir özellik değeri, <xref:System.Windows.Documents.Section> alt öğeleri için geçerlidir. Bir bölüm ayrıca kendi alt koleksiyonu aracılığıyla programlı bir şekilde yineleme yapmanızı sağlar. <xref:System.Windows.Documents.Section>HTML 'deki etikete benzer bir şekilde kullanılır \<DIV> .

Aşağıdaki örnekte, üç paragraf bir altında tanımlanmıştır <xref:System.Windows.Documents.Section> . Bölümünde <xref:System.Windows.Documents.TextElement.Background%2A> kırmızı bir özellik değeri bulunur, bu nedenle paragrafların arka plan rengi de kırmızıdır.

[!code-xaml[FlowOvwSnippets_snip#SectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SectionExample.xaml#sectionexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SectionExample.cs#sectioncodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SectionExample.vb#sectioncodeonlyexamplewholepage)]

**Blockufıcontainer**

<xref:System.Windows.Documents.BlockUIContainer><xref:System.Windows.UIElement>öğelerin (örn. a <xref:System.Windows.Controls.Button> ), blok ile türetilmiş akış içeriğine gömülmesini sağlar. <xref:System.Windows.Documents.InlineUIContainer>(aşağıya bakın) <xref:System.Windows.UIElement> öğeleri satır içi türetilmiş akış içeriğine eklemek için kullanılır. <xref:System.Windows.Documents.BlockUIContainer>ve, <xref:System.Windows.Documents.InlineUIContainer> <xref:System.Windows.UIElement> Bu iki öğeden biri içinde bulunmadığı müddetçe Flow içeriğini kullanmanın başka bir yolu olmadığından önemlidir.

Aşağıdaki örnek, <xref:System.Windows.Documents.BlockUIContainer> <xref:System.Windows.UIElement> akış içeriği içinde nesneleri barındırmak için öğesinin nasıl kullanılacağını gösterir.

[!code-xaml[SpanSnippets#_BlockUIXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml#_blockuixaml)]

Aşağıdaki şekilde bu örneğin nasıl işlediğini gösterilmektedir:

![Akış içeriğine gömülü bir UIElement gösteren ekran görüntüsü.](./media/flow-document-overview/embedded-blockuicontainer.png)

**Liste**

<xref:System.Windows.Documents.List>Madde işaretli veya sayısal bir liste oluşturmak için kullanılır. <xref:System.Windows.Documents.List.MarkerStyle%2A> <xref:System.Windows.TextMarkerStyle> Listenin stilini belirleyebilmek için özelliği bir numaralandırma değeri olarak ayarlayın. Aşağıdaki örnekte nasıl basit bir liste oluşturulacağı gösterilmektedir.

[!code-xaml[FlowOvwSnippets_snip#ListExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ListExample.xaml#listexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ListExample.cs#listcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ListExample.vb#listcodeonlyexamplewholepage)]

> [!NOTE]
> <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItemCollection> alt öğeleri yönetmek için kullanan tek Flow öğesidir.

**Tablo**

<xref:System.Windows.Documents.Table>bir tablo oluşturmak için kullanılır. <xref:System.Windows.Documents.Table>öğesi ile benzerdir, <xref:System.Windows.Controls.Grid> ancak daha fazla özelliğe sahiptir ve bu nedenle daha fazla kaynak yükü gerektirir. <xref:System.Windows.Controls.Grid>Bir olduğundan <xref:System.Windows.UIElement> , veya içinde içerilmediği takdirde akış içeriğinde kullanılamaz <xref:System.Windows.Documents.BlockUIContainer> <xref:System.Windows.Documents.InlineUIContainer> . Hakkında daha fazla bilgi için <xref:System.Windows.Documents.Table> bkz. [tabloya genel bakış](table-overview.md).

### <a name="inline-derived-classes"></a>Satır içi türetilmiş sınıflar

**Çalışmaz**

<xref:System.Windows.Documents.Run>biçimlendirilmemiş metin içermesi için kullanılır. <xref:System.Windows.Documents.Run>Akış içeriğinde kapsamlı olarak kullanılacak nesneleri beklemeniz gerekebilir. Ancak, biçimlendirme ' de <xref:System.Windows.Documents.Run> öğelerin açıkça kullanılması gerekmez. <xref:System.Windows.Documents.Run>kod kullanarak akış belgeleri oluştururken veya düzenleme sırasında kullanılması gerekir. Örneğin, aşağıdaki biçimlendirmede ilki, <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Run> ikinci kez öğesini açıkça belirtir. Her iki paragraf de özdeş çıkış oluşturur.

[!code-xaml[FlowOvwSnippets_snip#RunExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/RunSnippetsExample.xaml#runexample1)]

> [!NOTE]
> .NET Framework 4 ' te başlayarak, <xref:System.Windows.Documents.Run.Text%2A> <xref:System.Windows.Documents.Run> nesnesinin özelliği bir bağımlılık özelliğidir. Özelliğini, gibi bir <xref:System.Windows.Documents.Run.Text%2A> veri kaynağına bağlayabilirsiniz <xref:System.Windows.Controls.TextBlock> . <xref:System.Windows.Documents.Run.Text%2A>Özelliği tek yönlü bağlamayı tam olarak destekler. <xref:System.Windows.Documents.Run.Text%2A>Özelliği, hariç olmak üzere iki yönlü bağlamayı da destekler <xref:System.Windows.Controls.RichTextBox> . Örnek için bkz. <xref:System.Windows.Documents.Run.Text%2A?displayProperty=nameWithType>

**Kapsamı**

<xref:System.Windows.Documents.Span>diğer satır içi içerik öğelerini birlikte gruplandırır. Bir öğe içindeki içeriğe hiçbir devralınmış işleme uygulanmaz <xref:System.Windows.Documents.Span> . Ancak,, ve dahil,, ve ' den devralma öğeleri <xref:System.Windows.Documents.Span> <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Documents.Bold> <xref:System.Windows.Documents.Italic> <xref:System.Windows.Documents.Underline> metne biçimlendirme uygular.

Aşağıda <xref:System.Windows.Documents.Span> metin, öğe ve içeren satır içi içerik içeren bir örneği verilmiştir <xref:System.Windows.Documents.Bold> <xref:System.Windows.Controls.Button> .

[!code-xaml[FlowOvwSnippets_snip#SpanExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SpanExample.xaml#spanexamplewholepage)]

Aşağıdaki ekran görüntüsünde bu örneğin nasıl işlediğini gösterilmektedir.

![Ekran görüntüsü: Işlenen span örneği](./media/flow-spanexample.gif "Flow_SpanExample")

**Inlineuiconcontainer**

<xref:System.Windows.Documents.InlineUIContainer>bir <xref:System.Windows.UIElement> <xref:System.Windows.Controls.Button> içerik öğesine katıştırılması için öğeleri (örneğin, gibi bir denetimi) sağlar <xref:System.Windows.Documents.Inline> . Bu öğe yukarıda açıklanan satır içi eştir <xref:System.Windows.Documents.BlockUIContainer> . Aşağıda <xref:System.Windows.Documents.InlineUIContainer> içine satır içi eklemek için kullanılan bir örnek verilmiştir <xref:System.Windows.Controls.Button> <xref:System.Windows.Documents.Paragraph> .

[!code-xaml[FlowOvwSnippets_snip#InlineUIContainerExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/InlineUIContainerExample.xaml#inlineuicontainerexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/InlineUIContainerExample.cs#inlineuicontainercodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/InlineUIContainerExample.vb#inlineuicontainercodeonlyexamplewholepage)]

> [!NOTE]
> <xref:System.Windows.Documents.InlineUIContainer>açıkça biçimlendirmede kullanılması gerekmez. Bunu atlarsanız, <xref:System.Windows.Documents.InlineUIContainer> kod derlendiğinde yine de oluşturulur.

**Şekil ve Floater**

<xref:System.Windows.Documents.Figure>ve <xref:System.Windows.Documents.Floater> , birincil içerik akışından bağımsız olarak özelleştirilebilecek yerleştirme özellikleriyle akış belgelerine içerik eklemek için kullanılır. <xref:System.Windows.Documents.Figure>ya da <xref:System.Windows.Documents.Floater> öğeler genellikle içeriğin bölümlerini vurgulamak veya tasarımın, ana içerik akışında destekleyici görüntüleri veya diğer içerikleri barındırmak ya da reklamlar gibi gevşek ilişkili içerikleri eklemek için kullanılır.

Aşağıdaki örnek, bir <xref:System.Windows.Documents.Figure> metin paragrafına nasıl ekleneceğini gösterir.

[!code-xaml[FlowOvwSnippets_snip#FigureExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/FigureExample.xaml#figureexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/FigureExample.cs#figurecodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/FigureExample.vb#figurecodeonlyexamplewholepage)]

Aşağıdaki çizimde bu örneğin nasıl işlediğini gösterilmektedir.

![Ekran görüntüsü: şekil örneği](./media/flow-ovw-figure-example.png "Flow_Ovw_Figure_Example")

<xref:System.Windows.Documents.Figure>ve <xref:System.Windows.Documents.Floater> çeşitli yollarla farklılık gösterir ve farklı senaryolar için kullanılır.

**Rakam**

- Konumlandırılabilir: sayfa, içerik, sütun veya paragrafa göre sabitlemek üzere yatay ve dikey tutturucularını ayarlayabilirsiniz. Ayrıca, <xref:System.Windows.Documents.Figure.HorizontalOffset%2A> ve <xref:System.Windows.Documents.Figure.VerticalOffset%2A> özelliklerini rastgele uzaklıklar belirtmek için de kullanabilirsiniz.

- Birden fazla sütuna boyutlandırılabilir: <xref:System.Windows.Documents.Figure> Yükseklik ve genişlik sayfasının, içeriğin veya sütun yüksekliğinin ya da genişliğinin katları olarak ayarlayabilirsiniz. Sayfa ve içerik söz konusu olduğunda, 1 ' den büyük katlara izin verilmeyeceğini unutmayın. Örneğin, a genişliğini <xref:System.Windows.Documents.Figure> "0,5 Page" veya "0,25 Content" veya "2 Column" olarak ayarlayabilirsiniz. Yükseklik ve Genişlik ' i mutlak piksel değerlerine da ayarlayabilirsiniz.

- Sayfalamaz: a içindeki içerik <xref:System.Windows.Documents.Figure> içine uymuyorsa <xref:System.Windows.Documents.Figure> , içeriğin ne kadar uygun olduğunu ve kalan içeriğin kaybedilmesi gerekir

**Floater:**

- Konumlandırılamıyor ve kullanılabilir alan olduğu her yerde işleme alınacaktır. Sapmayı veya bağlantısını ayarlayamazsınız <xref:System.Windows.Documents.Floater> .

- Birden fazla sütuna boyutlandırılabilir: varsayılan olarak, <xref:System.Windows.Documents.Floater> bir sütundaki boyutlar. <xref:System.Windows.Documents.Floater.Width%2A>Mutlak piksel değerine ayarlanılabilen bir özelliği vardır, ancak bu değer bir sütun genişliğinden büyükse yok sayılır ve Floater bir sütunda boyutlandırılır. Doğru piksel genişliğini ayarlayarak, boyutu bir sütundan daha az bir sütuna göre boyutlandırabilir, ancak boyutlandırma sütun göreli değildir, bu nedenle "0,5 sütun" Width için geçerli bir ifade değildir <xref:System.Windows.Documents.Floater> . <xref:System.Windows.Documents.Floater>Height özelliği yok ve bu yükseklik ayarlanamaz, bu da içeriğe bağlıdır

- <xref:System.Windows.Documents.Floater>sayfalar: belirtilen genişliğine sahip içeriği 1 ' den fazla sütun yüksekliğine genişlerse, Floater ve sonraki sütunda, sonraki sayfa vb.

 <xref:System.Windows.Documents.Figure>Boyut ve konumlandırmayı denetlemek istediğiniz tek başına içerikleri yerleştirmek için iyi bir yerdir ve içeriğin belirtilen boyuta sığması önemlidir. <xref:System.Windows.Documents.Floater>Ana sayfa içeriğine benzer, ancak bundan ayrıldığından, akan daha fazla serbest akışlı içerik yerleştirmek için iyi bir yerdir.

**LineBreak**

<xref:System.Windows.Documents.LineBreak>akış içeriğinde satır sonu oluşmasına neden olur. Aşağıdaki örnek öğesinin kullanımını gösterir <xref:System.Windows.Documents.LineBreak> .

[!code-xaml[FlowOvwSnippets_snip#LineBreakExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/LineBreakExample.xaml#linebreakexamplewholepage)]

Aşağıdaki ekran görüntüsünde bu örneğin nasıl işlediğini gösterilmektedir.

![Ekran görüntüsü: LineBreak örneği](./media/flow-ovw-linebreakexample.png "Flow_Ovw_LineBreakExample")

### <a name="flow-collection-elements"></a>Akış koleksiyonu öğeleri

Yukarıdaki örneklerin çoğunda, <xref:System.Windows.Documents.BlockCollection> ve, <xref:System.Windows.Documents.InlineCollection> akış içeriğini programlı bir şekilde oluşturmak için kullanılır. Örneğin, öğesine öğe eklemek için <xref:System.Windows.Documents.Paragraph> söz dizimini kullanabilirsiniz:

```csharp
myParagraph.Inlines.Add(new Run("Some text"));
```

Bu <xref:System.Windows.Documents.Run> öğesine öğesine ekler <xref:System.Windows.Documents.InlineCollection> <xref:System.Windows.Documents.Paragraph> .  Bu, <xref:System.Windows.Documents.Run> bir ın biçimlendirmesinde bulunan örtülü ile aynıdır <xref:System.Windows.Documents.Paragraph> :

```xml
<Paragraph>
Some Text
</Paragraph>
```

Öğesinin kullanılmasına örnek olarak <xref:System.Windows.Documents.BlockCollection> , aşağıdaki örnek yeni bir oluşturur <xref:System.Windows.Documents.Section> ve sonra yeni bir içerik eklemek için **Add** yöntemini kullanır <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Section> .

[!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
[!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]

Akış koleksiyonuna öğe eklemenin yanı sıra öğeleri de kaldırabilirsiniz.  Aşağıdaki örnek <xref:System.Windows.Documents.Inline> , içindeki son öğeyi siler <xref:System.Windows.Documents.Span> .

[!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
[!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]

Aşağıdaki örnek, içindeki tüm içeriği ( <xref:System.Windows.Documents.Inline> öğeleri) temizler <xref:System.Windows.Documents.Span> .

[!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
[!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]

Program aracılığıyla akış içeriğiyle çalışırken, büyük olasılıkla bu koleksiyonların kapsamlı bir şekilde kullanılmasını sağlayabilirsiniz.

Bir akış öğesinin <xref:System.Windows.Documents.InlineCollection> alt öğelerini içermesi için bir (Inlines) veya <xref:System.Windows.Documents.BlockCollection> (bloklar) kullanması, üst öğe tarafından hangi tür alt öğelerin ( <xref:System.Windows.Documents.Block> veya <xref:System.Windows.Documents.Inline> ) dahil edilip edilmeyeceğini belirtir. Akış içeriği öğeleri için kapsama kuralları, sonraki bölümde içerik şemasında özetlenir.

> [!NOTE]
> Akış içeriğiyle kullanılan üçüncü bir tür koleksiyon vardır, <xref:System.Windows.Documents.ListItemCollection> ancak bu koleksiyon yalnızca bir ile kullanılır <xref:System.Windows.Documents.List> . Ayrıca, ile birlikte kullanılan birkaç koleksiyon vardır <xref:System.Windows.Documents.Table> . Daha fazla bilgi için bkz. [tabloya genel bakış](table-overview.md) .

<a name="content_schema"></a>

## <a name="content-schema"></a>İçerik şeması

Farklı akış içeriği öğelerinin sayısı verildiğinde, bir öğenin içerebileceği alt öğe türlerini izlemek çok fazla olabilir. Aşağıdaki diyagramda Flow öğelerinin kapsama kuralları özetlenmektedir. Oklar olası üst/alt ilişkileri temsil eder.

![Diyagram: akış içeriği kapsama şeması](./media/flow-content-schema.png "Flow_Content_Schema")

Yukarıdaki diyagramdan görünebileceği gibi, bir öğe için izin verilen alt öğeler bir öğe veya öğe olup olmadığı tarafından belirlenmeyebilir <xref:System.Windows.Documents.Block> <xref:System.Windows.Documents.Inline> . Örneğin, bir (bir öğe) yalnızca alt öğelere <xref:System.Windows.Documents.Span> <xref:System.Windows.Documents.Inline> sahip <xref:System.Windows.Documents.Inline> olsa <xref:System.Windows.Documents.Figure> da (aynı zamanda bir <xref:System.Windows.Documents.Inline> öğe) yalnızca <xref:System.Windows.Documents.Block> alt öğeleri olabilir. Bu nedenle, bir diyagram, başka bir öğenin hangi öğeye dahil edilebilir olduğunu hızlı bir şekilde belirlemek için faydalıdır. Örnek olarak, ' ın akış içeriğinin nasıl oluşturulacağını öğrenmek için diyagramı kullanalım <xref:System.Windows.Controls.RichTextBox> .

**1.** bir <xref:System.Windows.Controls.RichTextBox> ' ın içermesi gerekir ve bir <xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.Documents.Block> ile türetilmiş nesne içermelidir. Yukarıdaki diyagramda karşılık gelen segment aşağıda verilmiştir.

![Diyagram: RichTextBox kapsama kuralları](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")

Bu nedenle, biçimlendirmenin şu şekilde görünebileceğini burada bulabilirsiniz.

[!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]

**2.** diyagrama göre,,,, <xref:System.Windows.Documents.Block> ve dahil olmak üzere seçebileceğiniz birkaç öğe <xref:System.Windows.Documents.Paragraph> vardır <xref:System.Windows.Documents.Section> <xref:System.Windows.Documents.Table> <xref:System.Windows.Documents.List> <xref:System.Windows.Documents.BlockUIContainer> (yukarıdaki blok türetilmiş sınıflara bakın). Diyelim ki bir <xref:System.Windows.Documents.Table> . Yukarıdaki diyagrama göre, bir <xref:System.Windows.Documents.Table> içeren öğeleri içeren bir <xref:System.Windows.Documents.TableRowGroup> <xref:System.Windows.Documents.TableRow> öğesi içerir <xref:System.Windows.Documents.TableCell> <xref:System.Windows.Documents.Block> . Yukarıdaki diyagramdan alınan karşılık gelen segment aşağıda verilmiştir <xref:System.Windows.Documents.Table> .

![Diyagram: tablo için üst&#47;alt şema](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")

Karşılık gelen biçimlendirme aşağıda verilmiştir.

[!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]

**3.** yeniden, bir veya daha fazla <xref:System.Windows.Documents.Block> öğe bir altında gereklidir <xref:System.Windows.Documents.TableCell> . Basit hale getirmek için hücrenin içine biraz metin yerleştirelim. Bunu bir öğesi ile kullanarak yapabiliriz <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Run> . Aşağıda, bir <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Inline> öğenin <xref:System.Windows.Documents.Run> (bir <xref:System.Windows.Documents.Inline> öğe) yalnızca düz metin alabilir olduğunu gösteren diyagramda karşılık gelen segmentler verilmiştir.

![Diyagram: paragraf için üst&#47;alt şema](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")

![Diyagram: çalıştırma için üst&#47;alt şema](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")

Aşağıda, biçimlendirme içindeki tüm örnek verilmiştir.

[!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]

<a name="customizing_text"></a>

## <a name="customizing-text"></a>Metni özelleştirme

Genellikle metin bir akış belgesinde en yaygın içerik türüdür. Yukarıdaki nesneler, metnin nasıl işlendiğine ilişkin birçok yönü denetlemek için kullanılabilir olsa da, bu bölümde ele alınan metni özelleştirmek için başka yöntemler de vardır.

### <a name="text-decorations"></a>Metin süslemeleri

Metin süslemeleri metne alt çizgi, üst çizgi, taban çizgisi ve üstü çizili etkileri uygulamanıza olanak tanır (aşağıdaki resimlere bakın). Bu düzenlemeleriniz,,, <xref:System.Windows.Documents.Inline.TextDecorations%2A> ve dahil olmak üzere bir dizi nesne tarafından kullanıma sunulan özelliği kullanılarak eklenir <xref:System.Windows.Documents.Inline> <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.TextBox> .

Aşağıdaki örnek, öğesinin özelliğinin nasıl ayarlanacağını gösterir <xref:System.Windows.Documents.Paragraph.TextDecorations%2A> <xref:System.Windows.Documents.Paragraph> .

[!code-xaml[InlineSnippets#_Paragraph_TextDecXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml#_paragraph_textdecxaml)]

[!code-csharp[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml.cs#_paragraph_textdec)]
[!code-vb[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InlineSnippets/visualbasic/window1.xaml.vb#_paragraph_textdec)]

Aşağıdaki şekilde, bu örneğin nasıl işlediğini gösterilmektedir.

![Ekran görüntüsü: varsayılan üstü çizili efektli metin](./media/inline-textdec-strike.png "Inline_TextDec_Strike")

Aşağıdaki rakamlar, sırasıyla **üst çizgi**, **taban çizgisi**ve **alt çizgi** düzenlemelerinin nasıl işleneceğini gösterir.

![Ekran görüntüsü: üst çizgi Textdekoratör](./media/inline-textdec-over.png "Inline_TextDec_Over")

![Ekran görüntüsü: metin üzerinde varsayılan temel efekt](./media/inline-textdec-base.png "Inline_TextDec_Base")

![Ekran görüntüsü: varsayılan altı çizili efektli metin](./media/inline-textdec-under.png "Inline_TextDec_Under")

### <a name="typography"></a>Tipografi

<xref:System.Windows.Documents.TextElement.Typography%2A>Özelliği,,, ve dahil olmak üzere akışla ilgili içerikler tarafından sunulur <xref:System.Windows.Documents.TextElement> <xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.TextBox> . Bu özellik, metnin tipografik karakteristiklerini/çeşitlemelerini (küçük veya büyük harfler, üst simgeler ve alt simgeler, vb.) denetlemek için kullanılır.

Aşağıdaki örnek, <xref:System.Windows.Documents.TextElement.Typography%2A> örnek öğesi olarak kullanarak özniteliğinin nasıl ayarlanacağını gösterir <xref:System.Windows.Documents.Paragraph> .

[!code-xaml[TextElementSnippets#_TextElement_TypogXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]

Aşağıdaki şekilde, bu örneğin nasıl işlediğini gösterilmektedir.

![Ekran görüntüsü: Tipografisi değiştirilmiş metin](./media/textelement-typog.png "TextElement_Typog")

Buna karşılık aşağıdaki şekilde, varsayılan tipografik özelliklerle benzer bir örneğin nasıl işlediğini gösterilmektedir.

![Ekran görüntüsü: Tipografisi değiştirilmiş metin](./media/textelement-typog-default.png "TextElement_Typog_Default")

Aşağıdaki örnek, <xref:System.Windows.Controls.TextBox.Typography%2A> özelliğinin programlı olarak nasıl ayarlanacağını gösterir.

[!code-csharp[TextElementSnippets#_TextElement_Typog](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
[!code-vb[TextElementSnippets#_TextElement_Typog](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]

Tipografi hakkında daha fazla bilgi için bkz. [WPF 'de tipografi](typography-in-wpf.md) .

## <a name="see-also"></a>Ayrıca bkz.

- [Metin](optimizing-performance-text.md)
- [WPF'de Tipografi](typography-in-wpf.md)
- [Nasıl Yapılır Konuları](flow-content-elements-how-to-topics.md)
- [TextElement İçerik Modeline Genel Bakış](textelement-content-model-overview.md)
- [RichTextBox Genel Bakışı](../controls/richtextbox-overview.md)
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Tabloya Genel Bakış](table-overview.md)
- [Ek açıklamalara Genel Bakış](annotations-overview.md)
