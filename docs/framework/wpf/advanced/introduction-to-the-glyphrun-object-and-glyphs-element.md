---
title: GlyphRun Nesnesi ve Karakter Öğesine Giriş
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], Glyphs element
- Glyphs elements [WPF]
- GlyphRun object [WPF]
- text [WPF], glyphs
- glyphs [WPF]
- typography [WPF], GlyphRun object
ms.assetid: 746ca769-a331-4435-9b95-f72a883b67c1
ms.openlocfilehash: 7c78853aef9dfa96c49a0f2a4b585a2bd0cd5e98
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206986"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a><span data-ttu-id="379bc-102">GlyphRun Nesnesi ve Karakter Öğesine Giriş</span><span class="sxs-lookup"><span data-stu-id="379bc-102">Introduction to the GlyphRun Object and Glyphs Element</span></span>
<span data-ttu-id="379bc-103">Bu konu başlığı altında açıklanır <xref:System.Windows.Media.GlyphRun> nesne ve <xref:System.Windows.Documents.Glyphs> öğesi.</span><span class="sxs-lookup"><span data-stu-id="379bc-103">This topic describes the <xref:System.Windows.Media.GlyphRun> object and the <xref:System.Windows.Documents.Glyphs> element.</span></span>  

<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a><span data-ttu-id="379bc-104">GlyphRun giriş</span><span class="sxs-lookup"><span data-stu-id="379bc-104">Introduction to GlyphRun</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="379bc-105">Glif düzeyinde biçimlendirme doğrudan erişimle dahil olmak üzere gelişmiş destek sağlar <xref:System.Windows.Documents.Glyphs> kesebilir ve metin biçimlendirme sonra devam etmek isteyen müşteriler için.</span><span class="sxs-lookup"><span data-stu-id="379bc-105">provides advanced text support including glyph-level markup with direct access to <xref:System.Windows.Documents.Glyphs> for customers who want to intercept and persist text after formatting.</span></span> <span data-ttu-id="379bc-106">Bu özellikler, aşağıdaki senaryolardan her işleme gereksinimleri için farklı metin kritik destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="379bc-106">These features provide critical support for the different text rendering requirements in each of the following scenarios.</span></span>  
  
1.  <span data-ttu-id="379bc-107">Sabit biçim belgeleri ekran görüntüsü.</span><span class="sxs-lookup"><span data-stu-id="379bc-107">Screen display of fixed-format documents.</span></span>  
  
2.  <span data-ttu-id="379bc-108">Yazdırma senaryoları.</span><span class="sxs-lookup"><span data-stu-id="379bc-108">Print scenarios.</span></span>  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <span data-ttu-id="379bc-109">bir cihaz yazıcı dili olarak.</span><span class="sxs-lookup"><span data-stu-id="379bc-109">as a device printer language.</span></span>  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)]<span data-ttu-id="379bc-110">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="379bc-110">.</span></span>  
  
    -   <span data-ttu-id="379bc-111">Çıktı, önceki yazıcı sürücülerini [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] sabit biçimde uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="379bc-111">Previous printer drivers, output from [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications to the fixed format.</span></span>  
  
    -   <span data-ttu-id="379bc-112">Yazdırma Biriktiricisi biçimi.</span><span class="sxs-lookup"><span data-stu-id="379bc-112">Print spool format.</span></span>  
  
3.  <span data-ttu-id="379bc-113">Önceki sürümlerini istemciler dahil olmak üzere sabit biçimli belge gösterimi [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] ve diğer bilgi işlem cihazları.</span><span class="sxs-lookup"><span data-stu-id="379bc-113">Fixed-format document representation, including clients for previous versions of [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] and other computing devices.</span></span>  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Glyphs> <span data-ttu-id="379bc-114">ve <xref:System.Windows.Media.GlyphRun> sabit biçimli belge sunumu ve yazdırma senaryoları için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="379bc-114">and <xref:System.Windows.Media.GlyphRun> are designed for fixed-format document presentation and print scenarios.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="379bc-115">çeşitli öğeler için genel yerleşimi sağlar ve [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] gibi senaryoları <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="379bc-115">provides several elements for general layout and [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenarios such as <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="379bc-116">Düzen hakkında daha fazla bilgi ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] senaryoları için bkz: [WPF'de tipografi](typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="379bc-116">For more information on layout and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios, see the [Typography in WPF](typography-in-wpf.md).</span></span>  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a><span data-ttu-id="379bc-117">GlyphRun Nesnesi</span><span class="sxs-lookup"><span data-stu-id="379bc-117">The GlyphRun Object</span></span>  
 <span data-ttu-id="379bc-118"><xref:System.Windows.Media.GlyphRun> Nesnesini temsil eder bir karakter dizisi tek bir yüz tek bir boyutta ve tek bir işleme bir stil ile tek bir yazı tipi.</span><span class="sxs-lookup"><span data-stu-id="379bc-118">The <xref:System.Windows.Media.GlyphRun> object represents a sequence of glyphs from a single face of a single font at a single size, and with a single rendering style.</span></span>  
  
 <xref:System.Windows.Media.GlyphRun> <span data-ttu-id="379bc-119">Glif gibi her iki yazı tipi ayrıntılarını içeren <xref:System.Windows.Documents.Glyphs.Indices%2A> ve tek tek karakter konumları.</span><span class="sxs-lookup"><span data-stu-id="379bc-119">includes both font details such as glyph <xref:System.Windows.Documents.Glyphs.Indices%2A> and individual glyph positions.</span></span> <span data-ttu-id="379bc-120">Ayrıca orijinal içerir [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] noktaları çalıştırma karakter simgesi arabellek uzaklığı eşleme bilgileri ve karakter başına ve simge başına bayrakları, oluşturulan kod.</span><span class="sxs-lookup"><span data-stu-id="379bc-120">It also includes the original [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] code points the run was generated from, character-to-glyph buffer offset mapping information, and per-character and per-glyph flags.</span></span>  
  
 <xref:System.Windows.Media.GlyphRun> <span data-ttu-id="379bc-121">üst düzey karşılık gelen <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="379bc-121">has a corresponding high-level <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span></span> <xref:System.Windows.Documents.Glyphs> <span data-ttu-id="379bc-122">öğe ağacı ve kullanılabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] temsil etmek için işaretleme <xref:System.Windows.Media.GlyphRun> çıktı.</span><span class="sxs-lookup"><span data-stu-id="379bc-122">can be used in the element tree and in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup to represent <xref:System.Windows.Media.GlyphRun> output.</span></span>  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a><span data-ttu-id="379bc-123">Karakter öğesine</span><span class="sxs-lookup"><span data-stu-id="379bc-123">The Glyphs Element</span></span>  
 <span data-ttu-id="379bc-124"><xref:System.Windows.Documents.Glyphs> Öğesi çıktısını temsil eder bir <xref:System.Windows.Media.GlyphRun> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="379bc-124">The <xref:System.Windows.Documents.Glyphs> element represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="379bc-125">Aşağıdaki biçimlendirme sözdizimi tanımlamak için kullanılan <xref:System.Windows.Documents.Glyphs> öğesi.</span><span class="sxs-lookup"><span data-stu-id="379bc-125">The following markup syntax is used to describe the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="379bc-126">Aşağıdaki özellik tanımları örnek biçimlendirmede ilk dört özniteliğine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="379bc-126">The following property definitions correspond to the first four attributes in the sample markup.</span></span>  
  
|<span data-ttu-id="379bc-127">Özellik</span><span class="sxs-lookup"><span data-stu-id="379bc-127">Property</span></span>|<span data-ttu-id="379bc-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="379bc-128">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|<span data-ttu-id="379bc-129">Bir kaynak tanımlayıcısı belirtir: dosya adı, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], ya da uygulama .exe veya kapsayıcı kaynak başvurusu.</span><span class="sxs-lookup"><span data-stu-id="379bc-129">Specifies a resource identifier: file name, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], or resource reference in the application .exe or container.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|<span data-ttu-id="379bc-130">Yazı tipi boyutunu çizim yüzeyi birimleri (varsayılan.96 inç olarak) belirtir.</span><span class="sxs-lookup"><span data-stu-id="379bc-130">Specifies the font size in drawing surface units (default is .96 inches).</span></span>|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|<span data-ttu-id="379bc-131">Kalın ve italik stil bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="379bc-131">Specifies flags for bold and Italic styles.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|<span data-ttu-id="379bc-132">Çift yönlü Düzen düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="379bc-132">Specifies the bidirectional layout level.</span></span> <span data-ttu-id="379bc-133">Tek sayılı ve sıfır değerleri soldan sağa düzen; kapsıyor. Tek sayılı değerleri sağdan sola düzen kapsıyor.</span><span class="sxs-lookup"><span data-stu-id="379bc-133">Even-numbered and zero values imply left-to-right layout; odd-numbered values imply right-to-left layout.</span></span>|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a><span data-ttu-id="379bc-134">Dizinleri özelliği</span><span class="sxs-lookup"><span data-stu-id="379bc-134">Indices property</span></span>  
 <span data-ttu-id="379bc-135"><xref:System.Windows.Documents.Glyphs.Indices%2A> Özelliği karakter belirtimleri dizesidir.</span><span class="sxs-lookup"><span data-stu-id="379bc-135">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property is a string of glyph specifications.</span></span> <span data-ttu-id="379bc-136">Glyphs dizisini tek bir küme oluşturur. Burada, kümedeki ilk karakter belirtimi kaç karakter belirtimi ve kümeyi oluşturmak için kaç tane kod noktaları birleştirmek gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="379bc-136">Where a sequence of glyphs forms a single cluster, the specification of the first glyph in the cluster is preceded by a specification of how many glyphs and how many code points combine to form the cluster.</span></span> <span data-ttu-id="379bc-137"><xref:System.Windows.Documents.Glyphs.Indices%2A> Özelliği bir dize içinde aşağıdaki özellikleri toplar.</span><span class="sxs-lookup"><span data-stu-id="379bc-137">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property collects in one string the following properties.</span></span>  
  
-   <span data-ttu-id="379bc-138">Simge dizinleri</span><span class="sxs-lookup"><span data-stu-id="379bc-138">Glyph indices</span></span>  
  
-   <span data-ttu-id="379bc-139">Karakter öncelikli genişlikler</span><span class="sxs-lookup"><span data-stu-id="379bc-139">Glyph advance widths</span></span>  
  
-   <span data-ttu-id="379bc-140">Karakter eki vektörlerini birleştirme</span><span class="sxs-lookup"><span data-stu-id="379bc-140">Combining glyph attachment vectors</span></span>  
  
-   <span data-ttu-id="379bc-141">Glif kod noktaları küme eşleme</span><span class="sxs-lookup"><span data-stu-id="379bc-141">Cluster mapping from code points to glyphs</span></span>  
  
-   <span data-ttu-id="379bc-142">Glif bayrakları</span><span class="sxs-lookup"><span data-stu-id="379bc-142">Glyph flags</span></span>  
  
 <span data-ttu-id="379bc-143">Her karakter belirtimi aşağıdaki biçime sahiptir.</span><span class="sxs-lookup"><span data-stu-id="379bc-143">Each glyph specification has the following form.</span></span>  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a><span data-ttu-id="379bc-144">Glif ölçümleri</span><span class="sxs-lookup"><span data-stu-id="379bc-144">Glyph Metrics</span></span>  
 <span data-ttu-id="379bc-145">Her karakter, birbirleriyle nasıl hizalandığını belirtin ölçümleri tanımlar <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="379bc-145">Each glyph defines metrics that specify how it aligns with other <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="379bc-146">Aşağıdaki grafikte, çeşitli tipografik nitelikleri iki farklı simge karakteri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="379bc-146">The following graphic defines the various typographic qualities of two different glyph characters.</span></span>  
  
 <span data-ttu-id="379bc-147">![Karakter ölçümleri diyagramı](./media/glyph-example.png "glyph_example")</span><span class="sxs-lookup"><span data-stu-id="379bc-147">![Diagraph of glyph measurements](./media/glyph-example.png "glyph_example")</span></span>  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a><span data-ttu-id="379bc-148">Karakter biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="379bc-148">Glyphs Markup</span></span>  
 <span data-ttu-id="379bc-149">Aşağıdaki kod örneği, çeşitli özelliklerinin nasıl kullanılacağını gösterir <xref:System.Windows.Documents.Glyphs> öğesinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="379bc-149">The following code example shows how to use various properties of the <xref:System.Windows.Documents.Glyphs> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="379bc-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="379bc-150">See also</span></span>

- [<span data-ttu-id="379bc-151">WPF'de Tipografi</span><span class="sxs-lookup"><span data-stu-id="379bc-151">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="379bc-152">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="379bc-152">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="379bc-153">Metin</span><span class="sxs-lookup"><span data-stu-id="379bc-153">Text</span></span>](optimizing-performance-text.md)
