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
ms.openlocfilehash: 5b1fd9c6e12a3dbea6de939ee90c48df716bd265
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395817"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a><span data-ttu-id="cf325-102">GlyphRun Nesnesi ve Karakter Öğesine Giriş</span><span class="sxs-lookup"><span data-stu-id="cf325-102">Introduction to the GlyphRun Object and Glyphs Element</span></span>
<span data-ttu-id="cf325-103">Bu konuda <xref:System.Windows.Media.GlyphRun> nesnesi ve <xref:System.Windows.Documents.Glyphs> öğesi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cf325-103">This topic describes the <xref:System.Windows.Media.GlyphRun> object and the <xref:System.Windows.Documents.Glyphs> element.</span></span>  

<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a><span data-ttu-id="cf325-104">GlyphRun 'a giriş</span><span class="sxs-lookup"><span data-stu-id="cf325-104">Introduction to GlyphRun</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="cf325-105">, biçimlendirmeden sonra metni kesme ve kalıcı hale getirmek isteyen müşteriler için <xref:System.Windows.Documents.Glyphs> ' e doğrudan erişim ile glif düzeyinde biçimlendirme dahil gelişmiş metin desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf325-105">provides advanced text support including glyph-level markup with direct access to <xref:System.Windows.Documents.Glyphs> for customers who want to intercept and persist text after formatting.</span></span> <span data-ttu-id="cf325-106">Bu özellikler, aşağıdaki senaryolardan her birinde farklı metin işleme gereksinimleri için kritik destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf325-106">These features provide critical support for the different text rendering requirements in each of the following scenarios.</span></span>  
  
1. <span data-ttu-id="cf325-107">Sabit biçimli belgelerin ekran görüntüsü.</span><span class="sxs-lookup"><span data-stu-id="cf325-107">Screen display of fixed-format documents.</span></span>  
  
2. <span data-ttu-id="cf325-108">Yazdırma senaryoları.</span><span class="sxs-lookup"><span data-stu-id="cf325-108">Print scenarios.</span></span>  
  
    - <span data-ttu-id="cf325-109">cihaz yazıcı dili olarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cf325-109">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] as a device printer language.</span></span>  
  
    - <span data-ttu-id="cf325-110">Microsoft XPS Belge Yazıcısı.</span><span class="sxs-lookup"><span data-stu-id="cf325-110">Microsoft XPS Document Writer.</span></span>  
  
    - <span data-ttu-id="cf325-111">Önceki yazıcı sürücüleri, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] uygulamalarından sabit biçime çıkış.</span><span class="sxs-lookup"><span data-stu-id="cf325-111">Previous printer drivers, output from [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications to the fixed format.</span></span>  
  
    - <span data-ttu-id="cf325-112">Yazdırma kuyruğu biçimi.</span><span class="sxs-lookup"><span data-stu-id="cf325-112">Print spool format.</span></span>  
  
3. <span data-ttu-id="cf325-113">Önceki Windows sürümleri ve diğer bilgi işlem cihazlarının istemcileri de dahil olmak üzere, sabit biçimli belge temsili.</span><span class="sxs-lookup"><span data-stu-id="cf325-113">Fixed-format document representation, including clients for previous versions of Windows and other computing devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf325-114"><xref:System.Windows.Documents.Glyphs> ve <xref:System.Windows.Media.GlyphRun> sabit biçimli belge sunumu ve yazdırma senaryoları için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cf325-114"><xref:System.Windows.Documents.Glyphs> and <xref:System.Windows.Media.GlyphRun> are designed for fixed-format document presentation and print scenarios.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="cf325-115">, genel düzen ve <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.TextBlock> gibi @no__t 1 senaryolar için birkaç öğe sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf325-115">provides several elements for general layout and [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenarios such as <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="cf325-116">Düzen ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] senaryoları hakkında daha fazla bilgi için [WPF 'de tipografi](typography-in-wpf.md)'e bakın.</span><span class="sxs-lookup"><span data-stu-id="cf325-116">For more information on layout and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios, see the [Typography in WPF](typography-in-wpf.md).</span></span>  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a><span data-ttu-id="cf325-117">GlyphRun nesnesi</span><span class="sxs-lookup"><span data-stu-id="cf325-117">The GlyphRun Object</span></span>  
 <span data-ttu-id="cf325-118">@No__t-0 nesnesi tek bir yazı tipindeki tek bir yüzden ve tek bir işleme stiliyle bir karakter dizisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cf325-118">The <xref:System.Windows.Media.GlyphRun> object represents a sequence of glyphs from a single face of a single font at a single size, and with a single rendering style.</span></span>  
  
 <span data-ttu-id="cf325-119"><xref:System.Windows.Media.GlyphRun>, hem karakter <xref:System.Windows.Documents.Glyphs.Indices%2A> hem de tek karakter konumları gibi yazı tipi ayrıntılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="cf325-119"><xref:System.Windows.Media.GlyphRun> includes both font details such as glyph <xref:System.Windows.Documents.Glyphs.Indices%2A> and individual glyph positions.</span></span> <span data-ttu-id="cf325-120">Ayrıca, çalıştırmanın oluşturulduğu orijinal Unicode kod noktalarını, karakter-karakter arabelleği fark eşleme bilgilerini ve karakter başına ve karakter başına bayrakları da içerir.</span><span class="sxs-lookup"><span data-stu-id="cf325-120">It also includes the original Unicode code points the run was generated from, character-to-glyph buffer offset mapping information, and per-character and per-glyph flags.</span></span>  
  
 <span data-ttu-id="cf325-121"><xref:System.Windows.Media.GlyphRun> ' a karşılık gelen bir üst düzey <xref:System.Windows.FrameworkElement> <xref:System.Windows.Documents.Glyphs> ' dir.</span><span class="sxs-lookup"><span data-stu-id="cf325-121"><xref:System.Windows.Media.GlyphRun> has a corresponding high-level <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="cf325-122"><xref:System.Windows.Documents.Glyphs>, öğe ağacında ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirmesinde <xref:System.Windows.Media.GlyphRun> çıkışını temsil edecek şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cf325-122"><xref:System.Windows.Documents.Glyphs> can be used in the element tree and in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup to represent <xref:System.Windows.Media.GlyphRun> output.</span></span>  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a><span data-ttu-id="cf325-123">Glyphs öğesi</span><span class="sxs-lookup"><span data-stu-id="cf325-123">The Glyphs Element</span></span>  
 <span data-ttu-id="cf325-124">@No__t-0 öğesi, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ' de bir <xref:System.Windows.Media.GlyphRun> çıktısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cf325-124">The <xref:System.Windows.Documents.Glyphs> element represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="cf325-125">Aşağıdaki biçimlendirme sözdizimi <xref:System.Windows.Documents.Glyphs> öğesini tanımlamakta kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cf325-125">The following markup syntax is used to describe the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="cf325-126">Aşağıdaki özellik tanımları, örnek biçimlendirmesinde ilk dört özniteliğe karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="cf325-126">The following property definitions correspond to the first four attributes in the sample markup.</span></span>  
  
|<span data-ttu-id="cf325-127">Özellik</span><span class="sxs-lookup"><span data-stu-id="cf325-127">Property</span></span>|<span data-ttu-id="cf325-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf325-128">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|<span data-ttu-id="cf325-129">Bir kaynak tanımlayıcısı belirtir: dosya adı, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] veya Application. exe veya Container içinde kaynak başvurusu.</span><span class="sxs-lookup"><span data-stu-id="cf325-129">Specifies a resource identifier: file name, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], or resource reference in the application .exe or container.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|<span data-ttu-id="cf325-130">Çizim yüzeyi birimlerinde yazı tipi boyutunu belirtir (varsayılan. 96 inç).</span><span class="sxs-lookup"><span data-stu-id="cf325-130">Specifies the font size in drawing surface units (default is .96 inches).</span></span>|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|<span data-ttu-id="cf325-131">Kalın ve Italik stiller için bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf325-131">Specifies flags for bold and Italic styles.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|<span data-ttu-id="cf325-132">Çift yönlü düzen düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf325-132">Specifies the bidirectional layout level.</span></span> <span data-ttu-id="cf325-133">Çift sayılı ve sıfır değerler soldan sağa düzeni göstermez; tek sayılı değerler sağdan sola düzeni göstermez.</span><span class="sxs-lookup"><span data-stu-id="cf325-133">Even-numbered and zero values imply left-to-right layout; odd-numbered values imply right-to-left layout.</span></span>|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a><span data-ttu-id="cf325-134">Dizinler özelliği</span><span class="sxs-lookup"><span data-stu-id="cf325-134">Indices property</span></span>  
 <span data-ttu-id="cf325-135">@No__t-0 özelliği, karakter belirtimlerinin bir dizesidir.</span><span class="sxs-lookup"><span data-stu-id="cf325-135">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property is a string of glyph specifications.</span></span> <span data-ttu-id="cf325-136">Bir karakter dizisinin tek bir küme olarak ayarlandığı yerlerde, kümedeki ilk glifin belirtimi, küme oluşturmak için kaç karakter ve kaç tane kod noktasının birleştirildiği hakkında bir belirtimdir.</span><span class="sxs-lookup"><span data-stu-id="cf325-136">Where a sequence of glyphs forms a single cluster, the specification of the first glyph in the cluster is preceded by a specification of how many glyphs and how many code points combine to form the cluster.</span></span> <span data-ttu-id="cf325-137">@No__t-0 özelliği aşağıdaki özellikleri tek bir dizede toplar.</span><span class="sxs-lookup"><span data-stu-id="cf325-137">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property collects in one string the following properties.</span></span>  
  
- <span data-ttu-id="cf325-138">Glif dizinleri</span><span class="sxs-lookup"><span data-stu-id="cf325-138">Glyph indices</span></span>  
  
- <span data-ttu-id="cf325-139">Glif öncelikli genişlikleri</span><span class="sxs-lookup"><span data-stu-id="cf325-139">Glyph advance widths</span></span>  
  
- <span data-ttu-id="cf325-140">Glif eki vektörlerini birleştirme</span><span class="sxs-lookup"><span data-stu-id="cf325-140">Combining glyph attachment vectors</span></span>  
  
- <span data-ttu-id="cf325-141">Kod noktalarından karakterlere karakter eşleme</span><span class="sxs-lookup"><span data-stu-id="cf325-141">Cluster mapping from code points to glyphs</span></span>  
  
- <span data-ttu-id="cf325-142">Glif bayrakları</span><span class="sxs-lookup"><span data-stu-id="cf325-142">Glyph flags</span></span>  
  
 <span data-ttu-id="cf325-143">Her glif belirtiminin aşağıdaki biçimi vardır.</span><span class="sxs-lookup"><span data-stu-id="cf325-143">Each glyph specification has the following form.</span></span>  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a><span data-ttu-id="cf325-144">Glif ölçümleri</span><span class="sxs-lookup"><span data-stu-id="cf325-144">Glyph Metrics</span></span>  
 <span data-ttu-id="cf325-145">Her glif, diğer <xref:System.Windows.Documents.Glyphs> ' la nasıl hizalanacağını belirten ölçümleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cf325-145">Each glyph defines metrics that specify how it aligns with other <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="cf325-146">Aşağıdaki grafik iki farklı karakter karakterlerinin çeşitli tipografik kalitelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cf325-146">The following graphic defines the various typographic qualities of two different glyph characters.</span></span>  
  
 <span data-ttu-id="cf325-147">![Glif ölçümlerinin Diagraf](./media/glyph-example.png "glyph_example")</span><span class="sxs-lookup"><span data-stu-id="cf325-147">![Diagraph of glyph measurements](./media/glyph-example.png "glyph_example")</span></span>  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a><span data-ttu-id="cf325-148">Glif biçimlendirmesi</span><span class="sxs-lookup"><span data-stu-id="cf325-148">Glyphs Markup</span></span>  
 <span data-ttu-id="cf325-149">Aşağıdaki kod örneği, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ' de <xref:System.Windows.Documents.Glyphs> öğesinin çeşitli özelliklerinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf325-149">The following code example shows how to use various properties of the <xref:System.Windows.Documents.Glyphs> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cf325-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf325-150">See also</span></span>

- [<span data-ttu-id="cf325-151">WPF'de Tipografi</span><span class="sxs-lookup"><span data-stu-id="cf325-151">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="cf325-152">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="cf325-152">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="cf325-153">Metin</span><span class="sxs-lookup"><span data-stu-id="cf325-153">Text</span></span>](optimizing-performance-text.md)
