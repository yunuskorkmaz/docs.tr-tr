---
title: "Akış Belgesine Genel Bakış"
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
- 'documents [WPF], flow documents [WPF], , '
- ', '
- flow documents [WPF]
ms.assetid: ef236a50-d44f-43c8-ba7c-82b0c733c0b7
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a99bd2336de41366d27c15e4bc4cfb2b2aff3cd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="flow-document-overview"></a>Akış Belgesine Genel Bakış
Akış belgeleri görüntülemeyi ve okunabilirliği iyileştirmek için tasarlanmıştır. Önceden tanımlanmış bir düzene ayarlanan, yerine akan belgeler dinamik olarak ayarlayın ve çalışma zamanı değişkenleri pencere boyutu, aygıt çözünürlüğü ve isteğe bağlı kullanıcı tercihleri gibi temel içeriklerini yeniden akışı. Ayrıca, akış belgeleri sayfalandırma ve sütunlar gibi gelişmiş belge özellikleri sunar. Bu konu, akış belgeleri ve bunların nasıl oluşturulacağı hakkında genel bir bakış sağlar.  
  

  
<a name="what_is_a_flow_document"></a>   
## <a name="what-is-a-flow-document"></a>Bir akış belge nedir  
 Akış belge pencere boyutu, aygıt çözünürlüğü ve diğer ortam değişkenlerine bağlı olarak "yeniden akış içeriği" için tasarlanmıştır. Ayrıca, akış belgeleri görüntüleme okunabilirlik ve boyutunu ve yazı tipleri görünümünü değiştirme yeteneğini en iyi duruma modları arama da dahil olmak üzere özellikleri yerleşik bir dizi sahip. Okuma Kolaylığı birincil belge tüketim senaryosu olduğunda akış belgeleri en iyi yararlanılmıştır. Buna karşılık, sabit belgeleri statik sunu sağlamak için tasarlanmıştır. Sabit belgeleri doğruluğu kaynak içerik, gerekli olduğunda faydalıdır. Bkz: [WPF belgelerde](../../../../docs/framework/wpf/advanced/documents-in-wpf.md) belgeleri farklı türleri hakkında daha fazla bilgi için.  
  
 Aşağıda birkaç farklı boyutlarda Windows'da görüntülenen örnek akış belge gösterilmektedir. Görüntü alanını değiştikçe kullanılabilir alanı en iyi kullanılmasını sağlamak için içeriği yeniden akar.  
  
 ![Belge içerik yeniden akışı akış](../../../../docs/framework/wpf/advanced/media/edocs-flowdocument.png "eDocs_FlowDocument")  
  
 Yukarıdaki resimde görüldüğü gibi akış içeriğini paragraflar, listeler, görüntüler ve daha fazla dahil birçok bileşen içerebilir. Bu bileşenlerin biçimlendirme öğelerinde ve yordam kodu nesneleri karşılık gelir. Bu sınıfların ayrıntılı üzerinden daha sonra ele alacağız [akış ilgili sınıflar](#flow_related_classes) bu genel bakış bölümünde. Şimdilik, bazı kalın metin ve bir liste paragrafı oluşan bir akış belge oluşturan basit bir kod örneğidir aşağıdadır.
  
 [!code-xaml[FlowOvwSnippets_snip#SimpleFlowExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SimpleFlowExample.xaml#simpleflowexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SimpleFlowExample.cs#simpleflowcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SimpleFlowExample.vb#simpleflowcodeonlyexamplewholepage)]  
  
 Aşağıdaki çizimde, bu kod parçacığını nasıl göründüğünü gösterir.  
  
 ![Ekran görüntüsü: İşlenmiş FlowDocument örneği](../../../../docs/framework/wpf/advanced/media/flow-ovw-first-example.png "Flow_Ovw_First_Example")  
  
 Bu örnekte, <xref:System.Windows.Controls.FlowDocumentReader> denetimi akış içeriğini barındırmak için kullanılır. Bkz: [akış belge türlerinin](#flow_document_types) denetimleri barındırma akış içeriği hakkında daha fazla bilgi için. <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, ve <xref:System.Windows.Documents.Bold> öğeleri içerik biçimlendirme, denetlemek için kullanılan biçimlendirme içindeki sıralarına göre. Örneğin, <xref:System.Windows.Documents.Bold> öğe kapsar paragraf metni yalnızca bir kısmını boyunca; sonuç olarak, yalnızca o metni kalın bir parçasıdır. HTML kullandıysanız, bu size tanıdık gelecektir.  
  
 Vurgulanan Yukarıdaki çizimde, akış belgelere yerleşik birkaç özellik vardır:
  
-   Arama: tüm belgenin tam metin araması olanak tanır.  
  
-   Görüntüleme modu: Kullanıcı bir tek sayfalı (sayfa--bir zamanda) görüntüleme modu, bir iki-sayfası--a-modu ve sürekli bir kayan (sınırsız) görüntüleme modu zamanda (defter okuma biçimi) dahil olmak üzere, tercih edilen görüntüleme modu seçebilirsiniz.  Bu görüntüleme modları hakkında daha fazla bilgi için bkz: <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  
  
-   Sayfa Gezinti denetimlerinin: belgenin görüntüleme modu sayfaları kullanıyorsa, sonraki sayfaya (aşağı ok) veya önceki sayfaya (yukarı ok), hem de geçerli sayfa numarası ve toplam sayfa sayısı için göstergeleri atlamak için bir düğmeye sayfa gezinti denetimlerinin içerir. Sayfalarıyla çevirme klavye ok tuşlarını kullanarak da gerçekleştirilebilir.  
  
-   Yakınlaştırma: Yakınlaştırma denetimlerini artırmak veya artı tıklayarak veya eksi düğmelerini, yakınlaştırma düzeyini azaltmak kullanıcının sırasıyla etkinleştirir. Yakınlaştırma denetimlerini yakınlaştırma düzeyini ayarlamak için kaydırıcıyı de içerir. Daha fazla bilgi için bkz. <xref:System.Windows.Controls.FlowDocumentReader.Zoom%2A>.  
  
 Bu özellikler akış içeriğini barındırmak için kullanılan denetim göre değiştirilebilir. Sonraki bölümde farklı denetimleri açıklar.  
  
<a name="flow_document_types"></a>   
## <a name="flow-document-types"></a>Akış belge türleri  
 Belge içerik akışı ve görünme görüntüsünü hangi nesne akış içeriğini barındırmak için kullanılan üzerine bağlıdır. Akış içeriğinin görüntülenmesi destekleyen dört denetimleri vardır: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.RichTextBox>, ve <xref:System.Windows.Controls.FlowDocumentScrollViewer>. Bu denetimler, aşağıda kısaca açıklanmıştır.  
  
 **Not:** <xref:System.Windows.Documents.FlowDocument> görüntüleme denetimleri bunların tümü tüketen doğrudan akış içeriği barındırmak için gerekli olduğundan, bir <xref:System.Windows.Documents.FlowDocument> akış içerik barındırma etkinleştirmek için.
  
### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader>kullanıcının bir tek sayfalı (sayfa--bir zamanda) görüntüleme modu, bir iki-sayfası--a-modu ve sürekli bir kayan (sınırsız) görüntüleme modu zamanda (defter okuma biçimi) dahil olmak üzere çeşitli görüntüleme modları arasında dinamik olarak seçmesini sağlayan özellikler içerir. Bu görüntüleme modları hakkında daha fazla bilgi için bkz: <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>. Farklı görüntüleme modları arasında dinamik geçiş özelliği gerekmiyorsa <xref:System.Windows.Controls.FlowDocumentPageViewer> ve <xref:System.Windows.Controls.FlowDocumentScrollViewer> hafifletilmiş akış belirli görüntüleme modunda sabit içerik görüntüleyicileri sağlar.  
  
### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer ve FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer>Sayfa--bir zamanda içinde içerik gösterir modu, görüntülerken <xref:System.Windows.Controls.FlowDocumentScrollViewer> sürekli kaydırma modunda içerik gösterir. Her ikisi de <xref:System.Windows.Controls.FlowDocumentPageViewer> ve <xref:System.Windows.Controls.FlowDocumentScrollViewer> belirli görüntüleme moduna sabitlenmiştir. Karşılaştırılacak <xref:System.Windows.Controls.FlowDocumentReader>, kullanıcının çeşitli görüntüleme modları arasında dinamik olarak seçmesini sağlayan özellikler içerir (tarafından sağlanan gibi <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> numaralandırması), daha fazla kaynak yoğunluğu olan artırılabilir <xref:System.Windows.Controls.FlowDocumentPageViewer> veya <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Varsayılan olarak, dikey kaydırma çubuğu her zaman gösterilir ve yatay kaydırma çubuğu gerektiğinde görünür duruma gelir. Varsayılan kullanıcı Arabirimi <xref:System.Windows.Controls.FlowDocumentScrollViewer> bir araç çubuğu içermez; ancak, <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> özelliği, yerleşik bir araç çubuğunu etkinleştirmek için kullanılabilir.  
  
### <a name="richtextbox"></a>RichTextBox  
 Kullandığınız bir <xref:System.Windows.Controls.RichTextBox> akış içeriği düzenlemek kullanıcı izin vermek istediğinizde. Örneğin, bir kullanıcının işlemek için izin verilen bir düzenleyici oluşturmak istediyseniz şeyler gibi tablolar, italik ve kalın biçimlendirme, vb., kullanacağınız bir <xref:System.Windows.Controls.RichTextBox>. Bkz: [RichTextBox Genel Bakış](../../../../docs/framework/wpf/controls/richtextbox-overview.md) daha fazla bilgi için.  
  
 **Not:** içindeki akış içeriği bir <xref:System.Windows.Controls.RichTextBox> tam olarak diğer denetimlerde akış içeriği gibi davranırlar değil. Örneğin, hiç sütun yok bir <xref:System.Windows.Controls.RichTextBox> ve bu nedenle hiçbir otomatik yeniden boyutlandırma davranışı. Ayrıca, arama, mod, sayfa gezintisi ve yakınlaştırma görüntüleme gibi içerik akışı genellikle yerleşik özelliklerini içinde kullanılabilir olmayan bir <xref:System.Windows.Controls.RichTextBox>.  
  
<a name="creating_flow_content"></a>   
## <a name="creating-flow-content"></a>İçerik akışı oluşturma  
 Akış içeriği, karmaşık, metin, görüntüler, tablolar dahil olmak üzere çeşitli öğeden oluşan ve hatta olabilir <xref:System.Windows.UIElement> türetilmiş sınıfları denetimleri gibi. Karmaşık akış içeriğinin nasıl oluşturulacağını anlamak için aşağıdaki noktaları önemlidir:  
  
-   **Akış ile ilgili sınıflar**: akış içeriği kullanılan her sınıfın belirli bir amacı vardır. Ayrıca, akış sınıflar arasındaki hiyerarşik ilişkiyi, bunların nasıl kullanıldığı anlamanıza yardımcı olur. Örneğin, türetilmiş sınıflar <xref:System.Windows.Documents.Block> türetilmiş sınıflar sırada diğer nesneleri içeren için kullanılan sınıf <xref:System.Windows.Documents.Inline> görüntülenen nesneleri içerir.  
  
-   **İçerik şeması**: akış belge önemli bir iç içe öğelerin sayısı gerektirebilir. İçerik şeması olası üst/alt öğeleri arasında ilişkiler belirtir.  
  
 Aşağıdaki bölümlerde daha ayrıntılı bu alanlardan her birini üzerinden geçer.  
  
<a name="flow_related_classes"></a>   
## <a name="flow-related-classes"></a>İlgili sınıflar akış  
 Aşağıdaki diyagramda, en yaygın akış içeriği ile kullanılan nesneleri gösterir:  
  
 ![Diyagram: Akış içeriği öğesi sınıf hiyerarşisi](../../../../docs/framework/wpf/advanced/media/flow-class-hierarchy.png "Flow_Class_Hierarchy")  
  
 Akış içeriği amaçları doğrultusunda, iki önemli kategorisi vardır:  
  
1.  **Blok türetilmiş sınıfları**: "Blok içerik öğeleri" veya "Blok öğeleri" yalnızca olarak da bilinir. Devralınan öğeleri <xref:System.Windows.Documents.Block> öğeleri ortak bir üst altında gruplandırmak için veya bir gruba genel öznitelikler uygulamak için kullanılabilir.  
  
2.  **Satır içi türetilmiş sınıfları**: "Satır içi içeriği öğeleri" veya "Satır içi öğeleri" yalnızca olarak da bilinir. Devralınan öğeleri <xref:System.Windows.Documents.Inline> ya da bir blok öğede veya başka bir satır içi öğe içinde yer alır. Satır içi öğeleri genelde ekrana işlenen içerik doğrudan kapsayıcı olarak kullanılır. Örneğin, bir <xref:System.Windows.Documents.Paragraph> (blok öğe) içerebilir bir <xref:System.Windows.Documents.Run> (satır içi öğenin) ancak <xref:System.Windows.Documents.Run> gerçekten ekranda işlenen metni içerir.  
  
 Bu iki kategoride her sınıf aşağıda kısaca açıklanmıştır.  
  
### <a name="block-derived-classes"></a>Blok türetilmiş sınıflar  
 **Paragraf**  
  
 <xref:System.Windows.Documents.Paragraph>genellikle Grup içeriği paragrafa kullanılır. En basit ve en yaygın paragrafın bir paragraf metni oluşturmak için kullanılır.  
  
 [!code-xaml[FlowOvwSnippets_snip#ParagraphExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ParagraphExample.xaml#paragraphexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ParagraphExample.cs#paragraphcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ParagraphExample.vb#paragraphcodeonlyexamplewholepage)]  
  
 Ancak, aşağıda göreceğiniz gibi satır içi türetilmiş diğer öğeleri de içerebilir. 
  
 **Bölüm**  
  
 <xref:System.Windows.Documents.Section>yalnızca diğer kapsamak için kullanılmış <xref:System.Windows.Documents.Block>-öğeleri türetilmiş. İçerdiği öğeleri biçimlendirme herhangi bir varsayılan uygulanmaz. Ancak, üzerinde kümesi herhangi bir özellik değerleri bir <xref:System.Windows.Documents.Section> ve alt öğeleri için geçerlidir. Bir bölüm program aracılığıyla kendi alt toplulukta tekrarlama sağlar. <xref:System.Windows.Documents.Section>benzer şekilde kullanılan \<DIV > HTML etiketi.  
  
 Aşağıdaki örnekte, üç paragraf altında bir tane tanımlanan <xref:System.Windows.Documents.Section>. Bölümüne sahip bir <xref:System.Windows.Documents.TextElement.Background%2A> özellik değeri kırmızı, bu nedenle paragrafları arka plan rengi kırmızı de.  
  
 [!code-xaml[FlowOvwSnippets_snip#SectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SectionExample.xaml#sectionexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SectionExample.cs#sectioncodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SectionExample.vb#sectioncodeonlyexamplewholepage)]  
  
 **BlockUIContainer**  
  
 <xref:System.Windows.Documents.BlockUIContainer>etkinleştirir <xref:System.Windows.UIElement> öğeleri (yani bir <xref:System.Windows.Controls.Button>) bloktan türetilmiş akış içeriği katıştırılmış. <xref:System.Windows.Documents.InlineUIContainer>(aşağıya bakın) katıştırmak için kullanılan <xref:System.Windows.UIElement> türetilmiş satır içi akış içeriği öğelerinde. <xref:System.Windows.Documents.BlockUIContainer>ve <xref:System.Windows.Documents.InlineUIContainer> kullanmak üzere başka hiçbir yolu olmadığı için önemli olan bir <xref:System.Windows.UIElement> akıştaki iki bu öğelerden birini içinde bulunmadığı sürece içerik.  
  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.Documents.BlockUIContainer> konak öğesine <xref:System.Windows.UIElement> akış içeriği içindeki nesneleri.  
  
 [!code-xaml[SpanSnippets#_BlockUIXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml#_blockuixaml)]  
  
 Bu örneğin nasıl işlediğini aşağıdaki şekilde gösterilmiştir.  
  
 ![Ekran görüntüsü: Akış içeriğine UIElement katıştırılmış](../../../../docs/framework/wpf/advanced/media/blockuicontainer.png "BlockUIContainer")  
  
 **Liste**  
  
 <xref:System.Windows.Documents.List>Madde işaretli veya sayısal listesini oluşturmak için kullanılır. Ayarlama <xref:System.Windows.Documents.List.MarkerStyle%2A> özelliğine bir <xref:System.Windows.TextMarkerStyle> listesi stilini belirlemek için numaralandırma değeri. Aşağıdaki örnekte basit bir liste oluşturulacağını gösterir.  
  
 [!code-xaml[FlowOvwSnippets_snip#ListExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ListExample.xaml#listexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ListExample.cs#listcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ListExample.vb#listcodeonlyexamplewholepage)]  
  
 **Not:** <xref:System.Windows.Documents.List> kullanan yalnızca akış öğesi <xref:System.Windows.Documents.ListItemCollection> alt öğelerini yönetmek için.  
  
 **Tablo**  
  
 <xref:System.Windows.Documents.Table>bir tablo oluşturmak için kullanılır. <xref:System.Windows.Documents.Table>benzer <xref:System.Windows.Controls.Grid> öğesi, ancak daha fazla özellik içerir ve bu nedenle, daha yüksek kaynak yükü gerektirir. Çünkü <xref:System.Windows.Controls.Grid> olan bir <xref:System.Windows.UIElement>, içeren sürece bu akış içeriği kullanılamaz bir <xref:System.Windows.Documents.BlockUIContainer> veya <xref:System.Windows.Documents.InlineUIContainer>. Daha fazla bilgi için <xref:System.Windows.Documents.Table>, bkz: [tablo genel bakışı](../../../../docs/framework/wpf/advanced/table-overview.md).  
  
### <a name="inline-derived-classes"></a>Satır içi türetilmiş sınıflar  
 **Çalıştır**  
  
 <xref:System.Windows.Documents.Run>biçimlendirilmemiş metin içermek üzere kullanılır. Beklediğiniz <xref:System.Windows.Documents.Run> yaygın olarak kullanılan nesneler akış içeriği. Ancak, biçimlendirmede <xref:System.Windows.Documents.Run> öğeleri açıkça kullanılacak gerekli değildir. <xref:System.Windows.Documents.Run>oluştururken veya kod kullanarak akış belgeleri düzenleme kullanılacak gereklidir. Örneğin, ilk aşağıdaki biçimlendirmede <xref:System.Windows.Documents.Paragraph> belirtir <xref:System.Windows.Documents.Run> açıkça ikinci sırasında öğesi yok. Her iki özdeş çıktı oluşturur.  
  
 [!code-xaml[FlowOvwSnippets_snip#RunExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/RunSnippetsExample.xaml#runexample1)]  
  
 **Not:** başlayarak [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], <xref:System.Windows.Documents.Run.Text%2A> özelliği <xref:System.Windows.Documents.Run> bağımlılık özelliği nesnesidir. Bağlayabilirsiniz <xref:System.Windows.Documents.Run.Text%2A> gibi özelliği bir veri kaynağı bir <xref:System.Windows.Controls.TextBlock>. <xref:System.Windows.Documents.Run.Text%2A> Özelliği, tek yönlü bağlama tam olarak destekler. <xref:System.Windows.Documents.Run.Text%2A> Özelliğini de destekleyen iki yönlü bağlama dışında <xref:System.Windows.Controls.RichTextBox>. Örnek için bkz. <xref:System.Windows.Documents.Run.Text%2A?displayProperty=nameWithType>  
  
 **Aralık**  
  
 <xref:System.Windows.Documents.Span>diğer satır içi içeriği öğelerini birlikte gruplar. Devralınan bir işleme içerik içinde uygulanan bir <xref:System.Windows.Documents.Span> öğesi. Öğeleri, ancak devral gelen <xref:System.Windows.Documents.Span> dahil olmak üzere <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Italic> ve <xref:System.Windows.Documents.Underline> biçimlendirmeyi metne uygular.  
  
 Bir örneği aşağıdadır bir <xref:System.Windows.Documents.Span> metin gibi satır içi içeriği için kullanılan bir <xref:System.Windows.Documents.Bold> öğesi ve bir <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[FlowOvwSnippets_snip#SpanExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SpanExample.xaml#spanexamplewholepage)]  
  
 Aşağıdaki ekran görüntüsünde, bu örnek nasıl işlediğini gösterir.  
  
 ![Ekran görüntüsü: İşlenmiş Span örneği](../../../../docs/framework/wpf/advanced/media/flow-spanexample.gif "Flow_SpanExample")  
  
 **InlineUIContainer**  
  
 <xref:System.Windows.Documents.InlineUIContainer>etkinleştirir <xref:System.Windows.UIElement> öğeleri (yani bir denetim ister <xref:System.Windows.Controls.Button>) katıştırılmış bir <xref:System.Windows.Documents.Inline> içerik öğesi. Bu öğe satır içi eşdeğer olan <xref:System.Windows.Documents.BlockUIContainer> yukarıda açıklanan. Kullanan bir örnek aşağıdadır <xref:System.Windows.Documents.InlineUIContainer> eklemek için bir <xref:System.Windows.Controls.Button> satır içinde bir <xref:System.Windows.Documents.Paragraph>.  
  
 [!code-xaml[FlowOvwSnippets_snip#InlineUIContainerExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/InlineUIContainerExample.xaml#inlineuicontainerexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/InlineUIContainerExample.cs#inlineuicontainercodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/InlineUIContainerExample.vb#inlineuicontainercodeonlyexamplewholepage)]  
  
 **Not:** <xref:System.Windows.Documents.InlineUIContainer> açıkça biçimlendirmede kullanılan gerekmez. Bunu, atlarsanız bir <xref:System.Windows.Documents.InlineUIContainer> kodu derlendiğinde yine de oluşturulacak.  
  
 **Şekil ve Floater**  
  
 <xref:System.Windows.Documents.Figure>ve <xref:System.Windows.Documents.Floater> içeriği birincil içerik akışı bağımsız özelleştirilebilir yerleşim özellikleri ile akış belgelere katıştırma için kullanılır. <xref:System.Windows.Documents.Figure>veya <xref:System.Windows.Documents.Floater> geniş eklemesine reklamlar gibi içerik ilgili veya öğelerini vurgulayın veya görüntü veya diğer içerik ana içerik akışı içinde destekleyen bir konağa içerik bölümlerini vurgulamak için genellikle kullanılır.  
  
 Aşağıdaki örnek, katıştırmak gösterilmiştir bir <xref:System.Windows.Documents.Figure> bir paragraf metni içine.  
  
 [!code-xaml[FlowOvwSnippets_snip#FigureExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/FigureExample.xaml#figureexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/FigureExample.cs#figurecodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/FigureExample.vb#figurecodeonlyexamplewholepage)]  
  
 Aşağıdaki çizimde, bu örnek nasıl işlediğini gösterir.  
  
 ![Ekran görüntüsü: Şekil örnek](../../../../docs/framework/wpf/advanced/media/flow-ovw-figure-example.png "Flow_Ovw_Figure_Example")  
  
 <xref:System.Windows.Documents.Figure>ve <xref:System.Windows.Documents.Floater> çeşitli yollarla farklıdır ve farklı senaryolar için kullanılır.  
  
 **Şekil:**  
  
-   Konumlandırılmış olabilir: sayfa, içerik, sütun veya paragraf göre sabitlemek için kendi yatay ve dikey bağlayıcılarını ayarlayabilirsiniz. Aynı zamanda kendi <xref:System.Windows.Documents.Figure.HorizontalOffset%2A> ve <xref:System.Windows.Documents.Figure.VerticalOffset%2A> özellikleri rasgele uzaklıkları belirtir.  
  
-   Birden fazla sütuna boyutlandırılıp boyutlandırılmayacağını: ayarlayabileceğiniz <xref:System.Windows.Documents.Figure> sayfası, içeriğin veya sütun yüksekliği veya genişliği katları genişliği ve yüksekliği. Sayfa ve içerik söz konusu olduğunda, 1'den büyük katları izin verilmeyeceğini unutmayın. Örneğin, genişliğini ayarlayabilirsiniz bir <xref:System.Windows.Documents.Figure> "0,5 sayfa" veya "0,25 içeriğe" veya "sütununda 2" olmalıdır. Yüksekliğini ve genişliğini mutlak piksel değerlerini ayarlayabilirsiniz.  
  
-   Değil sayfalara bölme: varsa içeriğini bir <xref:System.Windows.Documents.Figure> içine uymuyor <xref:System.Windows.Documents.Figure>, hangi içeriğin sığması işlemez ve kalan içeriği kaybolur  
  
 **Floater:**  
  
-   Konumlandırılmış olabilir ve alanı için kullanılabilir hale getirilebilir her yerde oluşturmaz. Uzaklık ya da bağlantı ayarlanamıyor bir <xref:System.Windows.Documents.Floater>.  
  
-   Birden fazla sütuna boyutta: varsayılan olarak, <xref:System.Windows.Documents.Floater> bir sütun boyutlarda. Bunun bir <xref:System.Windows.Documents.Floater.Width%2A> bir sütunu bu değer yok sayıldığını bir sütun genişliği floater'dan büyük olup olmadığını ancak bir mutlak piksel değerine ayarlayabilirsiniz özelliği boyuta sahip. Doğru piksel genişliği ayarlayarak, kısa bir sütuna boyutlandırabilirsiniz ancak boyutlandırma değil sütun göreli "0.5Column" geçerli bir ifade değildir <xref:System.Windows.Documents.Floater> genişliği. <xref:System.Windows.Documents.Floater>hiçbir height özelliği sahipse ve bu yüksekliği ayarlanamaz, buna ait yükseklik içerik bağlıdır  
  
-   <xref:System.Windows.Documents.Floater>paginates: içeriğini, belirtilen uzaklığında 1'den fazla sütun yüksekliğini geçerse, floater keser ve paginates sonraki sütun, sonraki sayfada, vs.  
  
 <xref:System.Windows.Documents.Figure>boyutunu denetlemek istediğiniz tek başına içerik yerleştirme için uygun bir yerdir konumlandırma ve içeriği belirtilen boyuta sığması emin. <xref:System.Windows.Documents.Floater>ana sayfa içeriği benzer akışlar, ancak ondan ayrılmış daha fazla ve serbest akışlı içerik yerleştirme için uygun bir yerdir.  
  
 **LineBreak**  
  
 <xref:System.Windows.Documents.LineBreak>akış içeriği gerçekleşmesi bir satır sonu neden olur. Aşağıdaki örnek kullanımını gösteren <xref:System.Windows.Documents.LineBreak>.  
  
 [!code-xaml[FlowOvwSnippets_snip#LineBreakExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/LineBreakExample.xaml#linebreakexamplewholepage)]  
  
 Aşağıdaki ekran görüntüsünde, bu örnek nasıl işlediğini gösterir.  
  
 ![Ekran görüntüsü: LineBreak örnek](../../../../docs/framework/wpf/advanced/media/flow-ovw-linebreakexample.png "Flow_Ovw_LineBreakExample")  
  
### <a name="flow-collection-elements"></a>Koleksiyon öğeleri akış  
 Yukarıdaki örneklerde birçok <xref:System.Windows.Documents.BlockCollection> ve <xref:System.Windows.Documents.InlineCollection> akış içeriği program aracılığıyla oluşturmak için kullanılır. Örneğin, öğelere eklemek için bir <xref:System.Windows.Documents.Paragraph>, sözdizimini kullanın:  
  
 `…`  
  
 `myParagraph.Inlines.Add(new Run("Some text"));`  
  
 `…`  
  
 Bu ekler bir <xref:System.Windows.Documents.Run> için <xref:System.Windows.Documents.InlineCollection> , <xref:System.Windows.Documents.Paragraph>.  Bu örtülü aynıdır <xref:System.Windows.Documents.Run> içinde bulunan bir <xref:System.Windows.Documents.Paragraph> biçimlendirmede:  
  
 `…`  
  
 `<Paragraph>`  
  
 `Some Text`  
  
 `</Paragraph>`  
  
 `…`  
  
 Kullanarak bir örnek olarak <xref:System.Windows.Documents.BlockCollection>, aşağıdaki örnek yeni bir oluşturur <xref:System.Windows.Documents.Section> ve ardından **Ekle** yeni bir ekleme yöntemi <xref:System.Windows.Documents.Paragraph> için <xref:System.Windows.Documents.Section> içeriği.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
 Bir akış koleksiyona öğe ekleme ek olarak, öğeleri de kaldırabilirsiniz.  Aşağıdaki örnek, son siler <xref:System.Windows.Documents.Inline> öğesinde <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 Aşağıdaki örnekte tüm içeriği siler (<xref:System.Windows.Documents.Inline> öğeleri) gelen <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
 Akış içeriği ile programlı olarak çalışırken, büyük olasılıkla bu koleksiyonları kapsamlı kullanımını hale getirir.  
  
 Akış öğesi kullanıp kullanmadığını bir <xref:System.Windows.Documents.InlineCollection> (Inlines) veya <xref:System.Windows.Documents.BlockCollection> (alt içerecek şekilde engeller) öğeleri alt öğe türüne bağlıdır (<xref:System.Windows.Documents.Block> veya <xref:System.Windows.Documents.Inline>) üst tarafından bulunabilir. Kapsama kuralları için içerik öğeleri sonraki bölümde içerik şemasında özetlenmiştir akışı.  
  
 **Not:** akış içeriği ile kullanılan koleksiyon üçüncü bir tür <xref:System.Windows.Documents.ListItemCollection>, ancak bu koleksiyon yalnızca ile kullanılan bir <xref:System.Windows.Documents.List>. Ayrıca, kullanılan birkaç koleksiyon vardır <xref:System.Windows.Documents.Table>. Bkz: [tablo genel bakışı](../../../../docs/framework/wpf/advanced/table-overview.md) daha fazla bilgi için.  
  
<a name="content_schema"></a>   
## <a name="content-schema"></a>İçerik şeması  
 Farklı akış içeriği öğeleri sayısı verildiğinde, ne tür bir öğe içerebilir alt öğelerini izlemek için zorlamayı olabilir. Aşağıdaki diyagram akış öğeleri için kapsama kuralları özetler. Oklar, olası üst/alt ilişkileri temsil eder.  
  
 ![Diyagram: Akış içeriği kapsama şeması](../../../../docs/framework/wpf/advanced/media/flow-content-schema.png "Flow_Content_Schema")  
  
 Yukarıdaki diyagramda görüldüğü gibi bir öğe için izin verilen alt öğe mutlaka olup olmadığı tarafından belirlenir olmayan bir <xref:System.Windows.Documents.Block> öğesi veya bir <xref:System.Windows.Documents.Inline> öğesi. Örneğin, bir <xref:System.Windows.Documents.Span> (bir <xref:System.Windows.Documents.Inline> öğesi) yalnızca olabilir <xref:System.Windows.Documents.Inline> sırasında alt öğelerini bir <xref:System.Windows.Documents.Figure> (aynı zamanda bir <xref:System.Windows.Documents.Inline> öğesi) yalnızca olabilir <xref:System.Windows.Documents.Block> alt öğeleri. Bu nedenle, bir diyagram hangi öğe başka bir programda bulunabilir hızla belirlemede yararlıdır. Örnek olarak, diyagram oluşturma akış içeriğini belirlemek için kullanalım bir <xref:System.Windows.Controls.RichTextBox>.  
  
 **1.** A <xref:System.Windows.Controls.RichTextBox> içermesi gereken bir <xref:System.Windows.Documents.FlowDocument> hangi sırayla içermesi gerekir bir <xref:System.Windows.Documents.Block>-türetilmiş bir nesne içermelidir. Yukarıdaki diyagramdan karşılık gelen kesim aşağıdadır.  
  
 ![Diyagram: RichTextBox kapsama kuralları](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
 Bugüne kadarki biçimlendirmeyi aşağıdaki gibi görünmelidir budur.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
 **2.** Aşağıdaki diyagramda göre birkaç yolu vardır <xref:System.Windows.Documents.Block> dahil olmak üzere seçmek için öğeleri <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List>, ve <xref:System.Windows.Documents.BlockUIContainer> (yukarıdaki bloktan türetilmiş sınıflara bakın). İstiyoruz diyelim bir <xref:System.Windows.Documents.Table>. Yukarıdaki diyagramda göre bir <xref:System.Windows.Documents.Table> içeren bir <xref:System.Windows.Documents.TableRowGroup> içeren <xref:System.Windows.Documents.TableRow> içeren öğeleri <xref:System.Windows.Documents.TableCell> içeren öğeleri bir <xref:System.Windows.Documents.Block>-türetilmiş bir nesne içermelidir. İçin karşılık gelen kesim aşağıdadır <xref:System.Windows.Documents.Table> yukarıdaki diyagramdan alınan.  
  
 ![Diyagram: Üst &#47;/; alt tablo için şema](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
 Karşılık gelen biçimlendirme aşağıdadır.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
 **3.** Yeniden, bir veya daha fazla <xref:System.Windows.Documents.Block> altında gerekli öğelerden bir <xref:System.Windows.Documents.TableCell>. Basit hale getirmek için şirketinizdeki bazı metinleri hücresinin içine koyun. Bu kullanarak yapabiliriz bir <xref:System.Windows.Documents.Paragraph> ile bir <xref:System.Windows.Documents.Run> öğesi. Gösteren diyagramdan karşılık gelen kesim aşağıdadır bir <xref:System.Windows.Documents.Paragraph> gerçekleştirebileceğiniz bir <xref:System.Windows.Documents.Inline> öğesi ve, bir <xref:System.Windows.Documents.Run> (bir <xref:System.Windows.Documents.Inline> öğesi) yalnızca düz metin alabilir.  
  
 ![Diyagram: Üst &#47;/; paragraf için alt şema](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
 ![Diyagram: Üst &#47; Çalışma için alt şema](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Tüm biçimlendirme örneği aşağıdadır.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="customizing_text"></a>   
## <a name="customizing-text"></a>Metin özelleştirme  
 Genellikle metin içeriği akış belgesinde en yaygın türüdür. Yukarıdaki sunulan nesneleri çoğu yönlerini metin nasıl işleneceğini denetlemek için kullanılabilir olmasa da, bu bölümde yer alan metni özelleştirmek için diğer bazı yöntemler vardır.  
  
### <a name="text-decorations"></a>Metin düzenlemelerinin  
 Metin düzenlemelerinin alt çizgi, üst çizgi, taban çizgisi ve üstü çizili etkileri metne izin ver (resimleri aşağıya bakın). Bu dekorasyonlar kullanılarak eklenen <xref:System.Windows.Documents.Inline.TextDecorations%2A> nesneler de dahil olmak üzere çeşitli tarafından kullanıma sunulan özelliği <xref:System.Windows.Documents.Inline>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Controls.TextBlock>, ve <xref:System.Windows.Controls.TextBox>.  
  
 Aşağıdaki örnekte nasıl ayarlanacağını gösterir <xref:System.Windows.Documents.Paragraph.TextDecorations%2A> özelliği bir <xref:System.Windows.Documents.Paragraph>.  
  
 [!code-xaml[InlineSnippets#_Paragraph_TextDecXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml#_paragraph_textdecxaml)]  
  
 [!code-csharp[InlineSnippets#_Paragraph_TextDec](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml.cs#_paragraph_textdec)]
 [!code-vb[InlineSnippets#_Paragraph_TextDec](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InlineSnippets/visualbasic/window1.xaml.vb#_paragraph_textdec)]  
  
 Bu örneğin nasıl işlediğini aşağıdaki şekilde gösterilmiştir.  
  
 ![Ekran görüntüsü: Varsayılan üstü çizili etkisi metinle](../../../../docs/framework/wpf/advanced/media/inline-textdec-strike.png "Inline_TextDec_Strike")  
  
 Aşağıdakiler rakamları Göster nasıl **üst çizgi**, **temel**, ve **altı çizili** sırasıyla düzenlemelerini işleme.  
  
 ![Ekran görüntüsü: Üst çizgi çizgi TextDecorator](../../../../docs/framework/wpf/advanced/media/inline-textdec-over.png "Inline_TextDec_Over")  
  
 ![Ekran görüntüsü: Varsayılan metni taban çizgisi efekti](../../../../docs/framework/wpf/advanced/media/inline-textdec-base.png "Inline_TextDec_Base")  
  
 ![Ekran görüntüsü: Varsayılan altı çizili efekti metinle](../../../../docs/framework/wpf/advanced/media/inline-textdec-under.png "Inline_TextDec_Under")  
  
### <a name="typography"></a>Tipografi  
 <xref:System.Windows.Documents.TextElement.Typography%2A> Özelliği çoğu akışıyla ilgili içerik ekleyerek gösterilir <xref:System.Windows.Documents.TextElement>, <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Controls.TextBlock>, ve <xref:System.Windows.Controls.TextBox>. Bu özellik, tipografik özellikleri/varyasyonları metin (yapmadan üst ve alt simgeler, vb. yani küçük veya büyük harfleri,) denetlemek için kullanılır.  
  
 Aşağıdaki örnekte nasıl ayarlanacağını gösterir <xref:System.Windows.Documents.TextElement.Typography%2A> özniteliğini kullanarak <xref:System.Windows.Documents.Paragraph> örnek öğesi olarak.  
  
 [!code-xaml[TextElementSnippets#_TextElement_TypogXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 Bu örneğin nasıl işlediğini aşağıdaki şekilde gösterilmiştir.  
  
 ![Ekran görüntüsü: Değiştirilen tipografi metinle](../../../../docs/framework/wpf/advanced/media/textelement-typog.png "TextElement_Typog")  
  
 Buna karşılık, varsayılan tipografik özellikleri ile benzer bir örneğin nasıl işlediğini aşağıdaki şekilde gösterilmiştir.  
  
 ![Ekran görüntüsü: Değiştirilen tipografi metinle](../../../../docs/framework/wpf/advanced/media/textelement-typog-default.png "TextElement_Typog_Default")  
  
 Aşağıdaki örnekte nasıl ayarlanacağını gösterir <xref:System.Windows.Controls.TextBox.Typography%2A> özelliği programlı olarak.  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
 Bkz: [WPF'de tipografi](../../../../docs/framework/wpf/advanced/typography-in-wpf.md) tipografi hakkında daha fazla bilgi için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Metin](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [WPF'de Tipografi](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/advanced/flow-content-elements-how-to-topics.md)  
 [TextElement İçerik Modeline Genel Bakış](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md)  
 [RichTextBox Genel Bakış](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [WPF'deki Belgeler](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Tabloya Genel Bakış](../../../../docs/framework/wpf/advanced/table-overview.md)  
 [Ek Açıklamalara Genel Bakış](../../../../docs/framework/wpf/advanced/annotations-overview.md)
