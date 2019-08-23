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
ms.openlocfilehash: 9e40a9656bd1d89203b167860ef6951d5e30377c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918396"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a><span data-ttu-id="50e45-102">GlyphRun Nesnesi ve Karakter Öğesine Giriş</span><span class="sxs-lookup"><span data-stu-id="50e45-102">Introduction to the GlyphRun Object and Glyphs Element</span></span>
<span data-ttu-id="50e45-103">Bu konu, <xref:System.Windows.Media.GlyphRun> nesnesini <xref:System.Windows.Documents.Glyphs> ve öğesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="50e45-103">This topic describes the <xref:System.Windows.Media.GlyphRun> object and the <xref:System.Windows.Documents.Glyphs> element.</span></span>  

<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a><span data-ttu-id="50e45-104">GlyphRun 'a giriş</span><span class="sxs-lookup"><span data-stu-id="50e45-104">Introduction to GlyphRun</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="50e45-105">biçimlendirmeden sonra metni kesme ve kalıcı hale getirmek isteyen müşterilere doğrudan erişim <xref:System.Windows.Documents.Glyphs> ile glif düzeyinde biçimlendirme dahil gelişmiş metin desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="50e45-105">provides advanced text support including glyph-level markup with direct access to <xref:System.Windows.Documents.Glyphs> for customers who want to intercept and persist text after formatting.</span></span> <span data-ttu-id="50e45-106">Bu özellikler, aşağıdaki senaryolardan her birinde farklı metin işleme gereksinimleri için kritik destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="50e45-106">These features provide critical support for the different text rendering requirements in each of the following scenarios.</span></span>  
  
1. <span data-ttu-id="50e45-107">Sabit biçimli belgelerin ekran görüntüsü.</span><span class="sxs-lookup"><span data-stu-id="50e45-107">Screen display of fixed-format documents.</span></span>  
  
2. <span data-ttu-id="50e45-108">Yazdırma senaryoları.</span><span class="sxs-lookup"><span data-stu-id="50e45-108">Print scenarios.</span></span>  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]<span data-ttu-id="50e45-109">bir cihaz yazıcı dili olarak.</span><span class="sxs-lookup"><span data-stu-id="50e45-109">as a device printer language.</span></span>  
  
    - <span data-ttu-id="50e45-110">Microsoft XPS Belge Yazıcısı.</span><span class="sxs-lookup"><span data-stu-id="50e45-110">Microsoft XPS Document Writer.</span></span>  
  
    - <span data-ttu-id="50e45-111">Önceki yazıcı sürücüleri, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] uygulamalardan Sabit biçime çıkış.</span><span class="sxs-lookup"><span data-stu-id="50e45-111">Previous printer drivers, output from [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications to the fixed format.</span></span>  
  
    - <span data-ttu-id="50e45-112">Yazdırma kuyruğu biçimi.</span><span class="sxs-lookup"><span data-stu-id="50e45-112">Print spool format.</span></span>  
  
3. <span data-ttu-id="50e45-113">Önceki Windows sürümleri ve diğer bilgi işlem cihazlarının istemcileri de dahil olmak üzere, sabit biçimli belge temsili.</span><span class="sxs-lookup"><span data-stu-id="50e45-113">Fixed-format document representation, including clients for previous versions of Windows and other computing devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50e45-114"><xref:System.Windows.Documents.Glyphs>ve <xref:System.Windows.Media.GlyphRun> sabit biçimli belge sunumu ve yazdırma senaryoları için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="50e45-114"><xref:System.Windows.Documents.Glyphs> and <xref:System.Windows.Media.GlyphRun> are designed for fixed-format document presentation and print scenarios.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="50e45-115"><xref:System.Windows.Controls.Label> , [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ve<xref:System.Windows.Controls.TextBlock>gibi genel düzen ve senaryolar için birkaç öğe sağlar.</span><span class="sxs-lookup"><span data-stu-id="50e45-115">provides several elements for general layout and [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenarios such as <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="50e45-116">Düzen ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] senaryolar hakkında daha fazla bilgi için bkz. [WPF 'de tipografi](typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="50e45-116">For more information on layout and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios, see the [Typography in WPF](typography-in-wpf.md).</span></span>  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a><span data-ttu-id="50e45-117">GlyphRun nesnesi</span><span class="sxs-lookup"><span data-stu-id="50e45-117">The GlyphRun Object</span></span>  
 <span data-ttu-id="50e45-118"><xref:System.Windows.Media.GlyphRun> Nesnesi tek bir yazı tipindeki tek bir yüzden ve tek bir işleme stiliyle bir karakter dizisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="50e45-118">The <xref:System.Windows.Media.GlyphRun> object represents a sequence of glyphs from a single face of a single font at a single size, and with a single rendering style.</span></span>  
  
 <span data-ttu-id="50e45-119"><xref:System.Windows.Media.GlyphRun>glif <xref:System.Windows.Documents.Glyphs.Indices%2A> ve ayrı karakter konumları gibi yazı tipi ayrıntılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="50e45-119"><xref:System.Windows.Media.GlyphRun> includes both font details such as glyph <xref:System.Windows.Documents.Glyphs.Indices%2A> and individual glyph positions.</span></span> <span data-ttu-id="50e45-120">Ayrıca, çalıştırmanın oluşturulduğu orijinal [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] kod noktalarını, karakter-karakter arabelleği fark eşleme bilgilerini ve karakter başına ve karakter başına bayrakları da içerir.</span><span class="sxs-lookup"><span data-stu-id="50e45-120">It also includes the original [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] code points the run was generated from, character-to-glyph buffer offset mapping information, and per-character and per-glyph flags.</span></span>  
  
 <span data-ttu-id="50e45-121"><xref:System.Windows.Media.GlyphRun><xref:System.Windows.FrameworkElement> ,<xref:System.Windows.Documents.Glyphs>karşılık gelen bir üst düzeydir.</span><span class="sxs-lookup"><span data-stu-id="50e45-121"><xref:System.Windows.Media.GlyphRun> has a corresponding high-level <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="50e45-122"><xref:System.Windows.Documents.Glyphs>öğe ağacında ve çıktıyı göstermek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Media.GlyphRun> için biçimlendirme içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="50e45-122"><xref:System.Windows.Documents.Glyphs> can be used in the element tree and in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup to represent <xref:System.Windows.Media.GlyphRun> output.</span></span>  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a><span data-ttu-id="50e45-123">Glyphs öğesi</span><span class="sxs-lookup"><span data-stu-id="50e45-123">The Glyphs Element</span></span>  
 <span data-ttu-id="50e45-124">Öğesi, <xref:System.Windows.Media.GlyphRun> içindeki[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]çıktısınıtemsileder. <xref:System.Windows.Documents.Glyphs></span><span class="sxs-lookup"><span data-stu-id="50e45-124">The <xref:System.Windows.Documents.Glyphs> element represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="50e45-125">Aşağıdaki biçimlendirme sözdizimi, <xref:System.Windows.Documents.Glyphs> öğesini tanımlamakta kullanılır.</span><span class="sxs-lookup"><span data-stu-id="50e45-125">The following markup syntax is used to describe the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="50e45-126">Aşağıdaki özellik tanımları, örnek biçimlendirmesinde ilk dört özniteliğe karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="50e45-126">The following property definitions correspond to the first four attributes in the sample markup.</span></span>  
  
|<span data-ttu-id="50e45-127">Özellik</span><span class="sxs-lookup"><span data-stu-id="50e45-127">Property</span></span>|<span data-ttu-id="50e45-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50e45-128">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|<span data-ttu-id="50e45-129">Kaynak tanımlayıcısını belirtir: dosya adı, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]veya kaynak başvurusu. exe veya kapsayıcı.</span><span class="sxs-lookup"><span data-stu-id="50e45-129">Specifies a resource identifier: file name, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], or resource reference in the application .exe or container.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|<span data-ttu-id="50e45-130">Çizim yüzeyi birimlerinde yazı tipi boyutunu belirtir (varsayılan. 96 inç).</span><span class="sxs-lookup"><span data-stu-id="50e45-130">Specifies the font size in drawing surface units (default is .96 inches).</span></span>|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|<span data-ttu-id="50e45-131">Kalın ve Italik stiller için bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="50e45-131">Specifies flags for bold and Italic styles.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|<span data-ttu-id="50e45-132">Çift yönlü düzen düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="50e45-132">Specifies the bidirectional layout level.</span></span> <span data-ttu-id="50e45-133">Çift sayılı ve sıfır değerler soldan sağa düzeni göstermez; tek sayılı değerler sağdan sola düzeni göstermez.</span><span class="sxs-lookup"><span data-stu-id="50e45-133">Even-numbered and zero values imply left-to-right layout; odd-numbered values imply right-to-left layout.</span></span>|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a><span data-ttu-id="50e45-134">Dizinler özelliği</span><span class="sxs-lookup"><span data-stu-id="50e45-134">Indices property</span></span>  
 <span data-ttu-id="50e45-135"><xref:System.Windows.Documents.Glyphs.Indices%2A> Özelliği, glif belirtimlerinin bir dizesidir.</span><span class="sxs-lookup"><span data-stu-id="50e45-135">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property is a string of glyph specifications.</span></span> <span data-ttu-id="50e45-136">Bir karakter dizisinin tek bir küme olarak ayarlandığı yerlerde, kümedeki ilk glifin belirtimi, küme oluşturmak için kaç karakter ve kaç tane kod noktasının birleştirildiği hakkında bir belirtimdir.</span><span class="sxs-lookup"><span data-stu-id="50e45-136">Where a sequence of glyphs forms a single cluster, the specification of the first glyph in the cluster is preceded by a specification of how many glyphs and how many code points combine to form the cluster.</span></span> <span data-ttu-id="50e45-137"><xref:System.Windows.Documents.Glyphs.Indices%2A> Özelliği, aşağıdaki özellikleri bir dizede toplar.</span><span class="sxs-lookup"><span data-stu-id="50e45-137">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property collects in one string the following properties.</span></span>  
  
- <span data-ttu-id="50e45-138">Glif dizinleri</span><span class="sxs-lookup"><span data-stu-id="50e45-138">Glyph indices</span></span>  
  
- <span data-ttu-id="50e45-139">Glif öncelikli genişlikleri</span><span class="sxs-lookup"><span data-stu-id="50e45-139">Glyph advance widths</span></span>  
  
- <span data-ttu-id="50e45-140">Glif eki vektörlerini birleştirme</span><span class="sxs-lookup"><span data-stu-id="50e45-140">Combining glyph attachment vectors</span></span>  
  
- <span data-ttu-id="50e45-141">Kod noktalarından karakterlere karakter eşleme</span><span class="sxs-lookup"><span data-stu-id="50e45-141">Cluster mapping from code points to glyphs</span></span>  
  
- <span data-ttu-id="50e45-142">Glif bayrakları</span><span class="sxs-lookup"><span data-stu-id="50e45-142">Glyph flags</span></span>  
  
 <span data-ttu-id="50e45-143">Her glif belirtiminin aşağıdaki biçimi vardır.</span><span class="sxs-lookup"><span data-stu-id="50e45-143">Each glyph specification has the following form.</span></span>  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a><span data-ttu-id="50e45-144">Glif ölçümleri</span><span class="sxs-lookup"><span data-stu-id="50e45-144">Glyph Metrics</span></span>  
 <span data-ttu-id="50e45-145">Her glif, nasıl hizalanacağını <xref:System.Windows.Documents.Glyphs>belirleyen ölçümleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="50e45-145">Each glyph defines metrics that specify how it aligns with other <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="50e45-146">Aşağıdaki grafik iki farklı karakter karakterlerinin çeşitli tipografik kalitelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="50e45-146">The following graphic defines the various typographic qualities of two different glyph characters.</span></span>  
  
 <span data-ttu-id="50e45-147">![Glif ölçümlerinin Diagraf](./media/glyph-example.png "glyph_example")</span><span class="sxs-lookup"><span data-stu-id="50e45-147">![Diagraph of glyph measurements](./media/glyph-example.png "glyph_example")</span></span>  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a><span data-ttu-id="50e45-148">Glif biçimlendirmesi</span><span class="sxs-lookup"><span data-stu-id="50e45-148">Glyphs Markup</span></span>  
 <span data-ttu-id="50e45-149">Aşağıdaki kod örneği, içindeki <xref:System.Windows.Documents.Glyphs> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]öğesinin çeşitli özelliklerinin nasıl kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="50e45-149">The following code example shows how to use various properties of the <xref:System.Windows.Documents.Glyphs> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="50e45-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50e45-150">See also</span></span>

- [<span data-ttu-id="50e45-151">WPF'de Tipografi</span><span class="sxs-lookup"><span data-stu-id="50e45-151">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="50e45-152">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="50e45-152">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="50e45-153">Metin</span><span class="sxs-lookup"><span data-stu-id="50e45-153">Text</span></span>](optimizing-performance-text.md)
