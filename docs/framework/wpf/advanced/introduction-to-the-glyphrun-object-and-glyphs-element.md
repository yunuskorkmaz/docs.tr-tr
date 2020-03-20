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
ms.openlocfilehash: 32e8ab7104b8ea2f985395065868ed154ca1e378
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181958"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a><span data-ttu-id="70a9e-102">GlyphRun Nesnesi ve Karakter Öğesine Giriş</span><span class="sxs-lookup"><span data-stu-id="70a9e-102">Introduction to the GlyphRun Object and Glyphs Element</span></span>
<span data-ttu-id="70a9e-103">Bu konu <xref:System.Windows.Media.GlyphRun> nesne ve <xref:System.Windows.Documents.Glyphs> öğeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="70a9e-103">This topic describes the <xref:System.Windows.Media.GlyphRun> object and the <xref:System.Windows.Documents.Glyphs> element.</span></span>  

<a name="text_glyphrunovw_intro"></a>
## <a name="introduction-to-glyphrun"></a><span data-ttu-id="70a9e-104">GlyphRun'a Giriş</span><span class="sxs-lookup"><span data-stu-id="70a9e-104">Introduction to GlyphRun</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="70a9e-105">biçimlendirmeden sonra metni engellemek ve devam etmek isteyen <xref:System.Windows.Documents.Glyphs> müşterilere doğrudan erişim sağlayan glyph düzeyinde biçimlendirme dahil olmak üzere gelişmiş metin desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="70a9e-105">provides advanced text support including glyph-level markup with direct access to <xref:System.Windows.Documents.Glyphs> for customers who want to intercept and persist text after formatting.</span></span> <span data-ttu-id="70a9e-106">Bu özellikler, aşağıdaki senaryoların her birinde farklı metin oluşturma gereksinimleri için kritik destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="70a9e-106">These features provide critical support for the different text rendering requirements in each of the following scenarios.</span></span>  
  
1. <span data-ttu-id="70a9e-107">Sabit biçimli belgelerin ekran görüntüsü.</span><span class="sxs-lookup"><span data-stu-id="70a9e-107">Screen display of fixed-format documents.</span></span>  
  
2. <span data-ttu-id="70a9e-108">Senaryoları yazdırın.</span><span class="sxs-lookup"><span data-stu-id="70a9e-108">Print scenarios.</span></span>  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]<span data-ttu-id="70a9e-109">bir aygıt yazıcı dili olarak.</span><span class="sxs-lookup"><span data-stu-id="70a9e-109">as a device printer language.</span></span>  
  
    - <span data-ttu-id="70a9e-110">Microsoft XPS Belge Yazarı.</span><span class="sxs-lookup"><span data-stu-id="70a9e-110">Microsoft XPS Document Writer.</span></span>  
  
    - <span data-ttu-id="70a9e-111">Önceki yazıcı sürücüleri, Win32 uygulamalarından sabit formata çıktı.</span><span class="sxs-lookup"><span data-stu-id="70a9e-111">Previous printer drivers, output from Win32 applications to the fixed format.</span></span>  
  
    - <span data-ttu-id="70a9e-112">Makara biçimini yazdırın.</span><span class="sxs-lookup"><span data-stu-id="70a9e-112">Print spool format.</span></span>  
  
3. <span data-ttu-id="70a9e-113">Windows'un önceki sürümleri ve diğer bilgi işlem aygıtları için istemciler de dahil olmak üzere sabit biçimli belge gösterimi.</span><span class="sxs-lookup"><span data-stu-id="70a9e-113">Fixed-format document representation, including clients for previous versions of Windows and other computing devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="70a9e-114"><xref:System.Windows.Documents.Glyphs>ve <xref:System.Windows.Media.GlyphRun> sabit biçimli belge sunumu ve yazdırma senaryoları için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="70a9e-114"><xref:System.Windows.Documents.Glyphs> and <xref:System.Windows.Media.GlyphRun> are designed for fixed-format document presentation and print scenarios.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="70a9e-115">gibi genel düzen ve [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] senaryolar <xref:System.Windows.Controls.Label> için <xref:System.Windows.Controls.TextBlock>çeşitli öğeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="70a9e-115">provides several elements for general layout and [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenarios such as <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="70a9e-116">Düzen ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] senaryolar hakkında daha fazla bilgi için [WPF'deki Tipografi'ye](typography-in-wpf.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="70a9e-116">For more information on layout and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios, see the [Typography in WPF](typography-in-wpf.md).</span></span>  
  
<a name="text_glyphrunovw_glyphrunobject"></a>
## <a name="the-glyphrun-object"></a><span data-ttu-id="70a9e-117">GlyphRun Nesnesi</span><span class="sxs-lookup"><span data-stu-id="70a9e-117">The GlyphRun Object</span></span>  
 <span data-ttu-id="70a9e-118">Nesne, <xref:System.Windows.Media.GlyphRun> tek bir boyutta ve tek bir işleme stiliyle tek bir yazı tipinin tek bir yüzünden gelen bir glifler dizisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="70a9e-118">The <xref:System.Windows.Media.GlyphRun> object represents a sequence of glyphs from a single face of a single font at a single size, and with a single rendering style.</span></span>  
  
 <span data-ttu-id="70a9e-119"><xref:System.Windows.Media.GlyphRun>glyph ve bireysel glyph <xref:System.Windows.Documents.Glyphs.Indices%2A> pozisyonları gibi her iki yazı tipi ayrıntılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="70a9e-119"><xref:System.Windows.Media.GlyphRun> includes both font details such as glyph <xref:System.Windows.Documents.Glyphs.Indices%2A> and individual glyph positions.</span></span> <span data-ttu-id="70a9e-120">Ayrıca, çalıştırmanın oluşturulduğu özgün Unicode kod noktaları, karakterden gph arabelleği eşleme bilgilerini ve karakter başına ve gph başına bayrakları içerir.</span><span class="sxs-lookup"><span data-stu-id="70a9e-120">It also includes the original Unicode code points the run was generated from, character-to-glyph buffer offset mapping information, and per-character and per-glyph flags.</span></span>  
  
 <span data-ttu-id="70a9e-121"><xref:System.Windows.Media.GlyphRun>ilgili bir üst <xref:System.Windows.FrameworkElement>düzey <xref:System.Windows.Documents.Glyphs>vardır.</span><span class="sxs-lookup"><span data-stu-id="70a9e-121"><xref:System.Windows.Media.GlyphRun> has a corresponding high-level <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="70a9e-122"><xref:System.Windows.Documents.Glyphs>öğe ağacında ve çıktıyı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] temsil <xref:System.Windows.Media.GlyphRun> etmek için biçimlendirmede kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="70a9e-122"><xref:System.Windows.Documents.Glyphs> can be used in the element tree and in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup to represent <xref:System.Windows.Media.GlyphRun> output.</span></span>  
  
<a name="text_glyphrunovw_glyphselement"></a>
## <a name="the-glyphs-element"></a><span data-ttu-id="70a9e-123">Glifler Elementi</span><span class="sxs-lookup"><span data-stu-id="70a9e-123">The Glyphs Element</span></span>  
 <span data-ttu-id="70a9e-124">Öğe <xref:System.Windows.Documents.Glyphs> bir <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]çıktısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="70a9e-124">The <xref:System.Windows.Documents.Glyphs> element represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="70a9e-125">Aşağıdaki biçimlendirme sözdizimi öğeyi <xref:System.Windows.Documents.Glyphs> açıklamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="70a9e-125">The following markup syntax is used to describe the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="70a9e-126">Aşağıdaki özellik tanımları örnek biçimlendirmedeki ilk dört özniteliklere karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="70a9e-126">The following property definitions correspond to the first four attributes in the sample markup.</span></span>  
  
|<span data-ttu-id="70a9e-127">Özellik</span><span class="sxs-lookup"><span data-stu-id="70a9e-127">Property</span></span>|<span data-ttu-id="70a9e-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70a9e-128">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|<span data-ttu-id="70a9e-129">Bir kaynak tanımlayıcısı belirtir: dosya adı, Web üniforması kaynak tanımlayıcısı (URI) veya uygulama .exe veya kapsayıcıdaki kaynak başvurusu.</span><span class="sxs-lookup"><span data-stu-id="70a9e-129">Specifies a resource identifier: file name, Web uniform resource identifier (URI), or resource reference in the application .exe or container.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|<span data-ttu-id="70a9e-130">Çizim yüzey birimlerinde yazı tipi boyutunu belirtir (varsayılan değer 0,96 inçtir).</span><span class="sxs-lookup"><span data-stu-id="70a9e-130">Specifies the font size in drawing surface units (default is .96 inches).</span></span>|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|<span data-ttu-id="70a9e-131">Kalın ve Italik stiller için bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="70a9e-131">Specifies flags for bold and Italic styles.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|<span data-ttu-id="70a9e-132">Çift yönlü düzen düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="70a9e-132">Specifies the bidirectional layout level.</span></span> <span data-ttu-id="70a9e-133">Çift numaralı ve sıfır değerleri soldan sağa düzeni ima; tek numaralı değerler sağdan sola düzeni ima.</span><span class="sxs-lookup"><span data-stu-id="70a9e-133">Even-numbered and zero values imply left-to-right layout; odd-numbered values imply right-to-left layout.</span></span>|  
  
<a name="text_glyphrunovw_indicesproperty"></a>
### <a name="indices-property"></a><span data-ttu-id="70a9e-134">Endeks özelliği</span><span class="sxs-lookup"><span data-stu-id="70a9e-134">Indices property</span></span>  
 <span data-ttu-id="70a9e-135">Özellik, <xref:System.Windows.Documents.Glyphs.Indices%2A> bir dizi glyph belirtimidir.</span><span class="sxs-lookup"><span data-stu-id="70a9e-135">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property is a string of glyph specifications.</span></span> <span data-ttu-id="70a9e-136">Bir dizi gliflerin tek bir küme oluşturduğu durumlarda, kümedeki ilk gliflerin belirtimi, kümeyi oluşturmak için kaç gifif ve kaç kod noktasının biraraya geldiğine göre önce gelir.</span><span class="sxs-lookup"><span data-stu-id="70a9e-136">Where a sequence of glyphs forms a single cluster, the specification of the first glyph in the cluster is preceded by a specification of how many glyphs and how many code points combine to form the cluster.</span></span> <span data-ttu-id="70a9e-137">Özellik, <xref:System.Windows.Documents.Glyphs.Indices%2A> aşağıdaki özellikleri tek bir dize de toplar.</span><span class="sxs-lookup"><span data-stu-id="70a9e-137">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property collects in one string the following properties.</span></span>  
  
- <span data-ttu-id="70a9e-138">Glyph endeksleri</span><span class="sxs-lookup"><span data-stu-id="70a9e-138">Glyph indices</span></span>  
  
- <span data-ttu-id="70a9e-139">Glyph ileri genişlikleri</span><span class="sxs-lookup"><span data-stu-id="70a9e-139">Glyph advance widths</span></span>  
  
- <span data-ttu-id="70a9e-140">Gph ek vektörlerinin birleştirilmesi</span><span class="sxs-lookup"><span data-stu-id="70a9e-140">Combining glyph attachment vectors</span></span>  
  
- <span data-ttu-id="70a9e-141">Kod noktalarından gliflere küme eşleme</span><span class="sxs-lookup"><span data-stu-id="70a9e-141">Cluster mapping from code points to glyphs</span></span>  
  
- <span data-ttu-id="70a9e-142">Glyph bayrakları</span><span class="sxs-lookup"><span data-stu-id="70a9e-142">Glyph flags</span></span>  
  
 <span data-ttu-id="70a9e-143">Her gph belirtimi aşağıdaki forma sahiptir.</span><span class="sxs-lookup"><span data-stu-id="70a9e-143">Each glyph specification has the following form.</span></span>  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>
## <a name="glyph-metrics"></a><span data-ttu-id="70a9e-144">Glyph Ölçümleri</span><span class="sxs-lookup"><span data-stu-id="70a9e-144">Glyph Metrics</span></span>  
 <span data-ttu-id="70a9e-145">Her glyph, diğerleriyle <xref:System.Windows.Documents.Glyphs>nasıl hizaladığını belirten ölçümler tanımlar.</span><span class="sxs-lookup"><span data-stu-id="70a9e-145">Each glyph defines metrics that specify how it aligns with other <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="70a9e-146">Aşağıdaki grafik, iki farklı gliflerin çeşitli tipografik özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="70a9e-146">The following graphic defines the various typographic qualities of two different glyph characters.</span></span>  
  
 <span data-ttu-id="70a9e-147">![Gliflerin diyagrafı](./media/glyph-example.png "glyph_example")</span><span class="sxs-lookup"><span data-stu-id="70a9e-147">![Diagraph of glyph measurements](./media/glyph-example.png "glyph_example")</span></span>  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>
## <a name="glyphs-markup"></a><span data-ttu-id="70a9e-148">Glyphs Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="70a9e-148">Glyphs Markup</span></span>  
 <span data-ttu-id="70a9e-149">Aşağıdaki kod örneği, <xref:System.Windows.Documents.Glyphs> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]'deki öğenin çeşitli özelliklerinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="70a9e-149">The following code example shows how to use various properties of the <xref:System.Windows.Documents.Glyphs> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="70a9e-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70a9e-150">See also</span></span>

- [<span data-ttu-id="70a9e-151">WPF'de Tipografi</span><span class="sxs-lookup"><span data-stu-id="70a9e-151">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="70a9e-152">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="70a9e-152">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="70a9e-153">Metin</span><span class="sxs-lookup"><span data-stu-id="70a9e-153">Text</span></span>](optimizing-performance-text.md)
