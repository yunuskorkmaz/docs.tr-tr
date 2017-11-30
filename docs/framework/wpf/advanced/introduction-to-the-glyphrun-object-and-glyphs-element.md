---
title: "GlyphRun Nesnesi ve Karakter Öğesine Giriş"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typography [WPF], Glyphs element
- Glyphs elements [WPF]
- GlyphRun object [WPF]
- text [WPF], glyphs
- glyphs [WPF]
- typography [WPF], GlyphRun object
ms.assetid: 746ca769-a331-4435-9b95-f72a883b67c1
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2e1b61b098d24857d6f1bc54165a5937d8887ee8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a><span data-ttu-id="e5081-102">GlyphRun Nesnesi ve Karakter Öğesine Giriş</span><span class="sxs-lookup"><span data-stu-id="e5081-102">Introduction to the GlyphRun Object and Glyphs Element</span></span>
<span data-ttu-id="e5081-103">Bu konuda açıklanmaktadır <xref:System.Windows.Media.GlyphRun> nesne ve <xref:System.Windows.Documents.Glyphs> öğesi.</span><span class="sxs-lookup"><span data-stu-id="e5081-103">This topic describes the <xref:System.Windows.Media.GlyphRun> object and the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
  
<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a><span data-ttu-id="e5081-104">GlyphRun'a</span><span class="sxs-lookup"><span data-stu-id="e5081-104">Introduction to GlyphRun</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="e5081-105">doğrudan erişimli karakter düzeyinde biçimlendirme dahil olmak üzere Gelişmiş metin desteği sağlar <xref:System.Windows.Documents.Glyphs> kesecek ve metin biçimlendirme sonra devam etmek isteyen müşteriler için.</span><span class="sxs-lookup"><span data-stu-id="e5081-105"> provides advanced text support including glyph-level markup with direct access to <xref:System.Windows.Documents.Glyphs> for customers who want to intercept and persist text after formatting.</span></span> <span data-ttu-id="e5081-106">Bu özellikler, işleme gereksinimleri aşağıdaki senaryoların her biri için farklı metin kritik destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5081-106">These features provide critical support for the different text rendering requirements in each of the following scenarios.</span></span>  
  
1.  <span data-ttu-id="e5081-107">Sabit biçimli belgelerin ekran görüntüsü.</span><span class="sxs-lookup"><span data-stu-id="e5081-107">Screen display of fixed-format documents.</span></span>  
  
2.  <span data-ttu-id="e5081-108">Yazdırma senaryoları.</span><span class="sxs-lookup"><span data-stu-id="e5081-108">Print scenarios.</span></span>  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]<span data-ttu-id="e5081-109">bir aygıt yazıcı dili olarak.</span><span class="sxs-lookup"><span data-stu-id="e5081-109"> as a device printer language.</span></span>  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)]<span data-ttu-id="e5081-110">.</span><span class="sxs-lookup"><span data-stu-id="e5081-110">.</span></span>  
  
    -   <span data-ttu-id="e5081-111">Çıktı önceki yazıcı sürücüleri [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] uygulamalarından sabit biçimde.</span><span class="sxs-lookup"><span data-stu-id="e5081-111">Previous printer drivers, output from [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications to the fixed format.</span></span>  
  
    -   <span data-ttu-id="e5081-112">Yazdırma biriktirme biçimi.</span><span class="sxs-lookup"><span data-stu-id="e5081-112">Print spool format.</span></span>  
  
3.  <span data-ttu-id="e5081-113">Önceki sürümlerinde istemciler dahil olmak üzere sabit biçimli belge gösterimi [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] ve diğer programlama cihazları.</span><span class="sxs-lookup"><span data-stu-id="e5081-113">Fixed-format document representation, including clients for previous versions of [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] and other computing devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5081-114"><xref:System.Windows.Documents.Glyphs>ve <xref:System.Windows.Media.GlyphRun> sabit biçimli belge sunumları ve yazdırma senaryoları için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e5081-114"><xref:System.Windows.Documents.Glyphs> and <xref:System.Windows.Media.GlyphRun> are designed for fixed-format document presentation and print scenarios.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="e5081-115">Çeşitli öğeleri için genel yerleşimi sağlar ve [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] gibi senaryoları <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="e5081-115"> provides several elements for general layout and [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenarios such as <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="e5081-116">Düzen hakkında daha fazla bilgi ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] senaryoları bkz [WPF'de tipografi](../../../../docs/framework/wpf/advanced/typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="e5081-116">For more information on layout and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios, see the [Typography in WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md).</span></span>  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a><span data-ttu-id="e5081-117">GlyphRun Nesnesi</span><span class="sxs-lookup"><span data-stu-id="e5081-117">The GlyphRun Object</span></span>  
 <span data-ttu-id="e5081-118"><xref:System.Windows.Media.GlyphRun> Nesne dizisi karakterlerin tek boyutta ve tek işleme stiliyle tek bir yazı tipinin tek bir yazıtipi temsil.</span><span class="sxs-lookup"><span data-stu-id="e5081-118">The <xref:System.Windows.Media.GlyphRun> object represents a sequence of glyphs from a single face of a single font at a single size, and with a single rendering style.</span></span>  
  
 <span data-ttu-id="e5081-119"><xref:System.Windows.Media.GlyphRun>karakter gibi her iki yazı tipi ayrıntıları içerir <xref:System.Windows.Documents.Glyphs.Indices%2A> ve bireysel karakter konumları.</span><span class="sxs-lookup"><span data-stu-id="e5081-119"><xref:System.Windows.Media.GlyphRun> includes both font details such as glyph <xref:System.Windows.Documents.Glyphs.Indices%2A> and individual glyph positions.</span></span> <span data-ttu-id="e5081-120">Ayrıca özgün içerir [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] kod Çalıştır karakter simgesi arabellek uzaklığı eşleme bilgileri ve karakter olmayan ve simge başına bayrakları, üretilen noktaları.</span><span class="sxs-lookup"><span data-stu-id="e5081-120">It also includes the original [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] code points the run was generated from, character-to-glyph buffer offset mapping information, and per-character and per-glyph flags.</span></span>  
  
 <span data-ttu-id="e5081-121"><xref:System.Windows.Media.GlyphRun>üst düzey karşılık gelen <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="e5081-121"><xref:System.Windows.Media.GlyphRun> has a corresponding high-level <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="e5081-122"><xref:System.Windows.Documents.Glyphs>öğe ağacı ve kullanılabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] temsil etmek için işaretleme <xref:System.Windows.Media.GlyphRun> çıktı.</span><span class="sxs-lookup"><span data-stu-id="e5081-122"><xref:System.Windows.Documents.Glyphs> can be used in the element tree and in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup to represent <xref:System.Windows.Media.GlyphRun> output.</span></span>  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a><span data-ttu-id="e5081-123">Karakterlerin öğesi</span><span class="sxs-lookup"><span data-stu-id="e5081-123">The Glyphs Element</span></span>  
 <span data-ttu-id="e5081-124"><xref:System.Windows.Documents.Glyphs> Öğesi çıktısını temsil eden bir <xref:System.Windows.Media.GlyphRun> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5081-124">The <xref:System.Windows.Documents.Glyphs> element represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="e5081-125">Aşağıdaki biçimlendirme sözdizimi tanımlamak için kullanılan <xref:System.Windows.Documents.Glyphs> öğesi.</span><span class="sxs-lookup"><span data-stu-id="e5081-125">The following markup syntax is used to describe the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="e5081-126">Aşağıdaki özellik tanımları örnek biçimlendirme ilk dört özniteliklerin karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="e5081-126">The following property definitions correspond to the first four attributes in the sample markup.</span></span>  
  
|<span data-ttu-id="e5081-127">Özellik</span><span class="sxs-lookup"><span data-stu-id="e5081-127">Property</span></span>|<span data-ttu-id="e5081-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5081-128">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|<span data-ttu-id="e5081-129">Bir kaynak tanımlayıcısını belirtir: dosya adı, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], veya uygulama .exe veya kapsayıcısındaki kaynak başvurusu.</span><span class="sxs-lookup"><span data-stu-id="e5081-129">Specifies a resource identifier: file name, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], or resource reference in the application .exe or container.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|<span data-ttu-id="e5081-130">(.96 inç varsayılandır) Yüzey birimlerindeki çizim yazı tipi boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5081-130">Specifies the font size in drawing surface units (default is .96 inches).</span></span>|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|<span data-ttu-id="e5081-131">Kalın ve italik stillerinde bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5081-131">Specifies flags for bold and Italic styles.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|<span data-ttu-id="e5081-132">Çift yönlü Düzen düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5081-132">Specifies the bidirectional layout level.</span></span> <span data-ttu-id="e5081-133">Tek sayılı ve sıfır değerleri soldan sağa düzeni belirtir; Tek sayılı değerler sağdan sola düzeni belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5081-133">Even-numbered and zero values imply left-to-right layout; odd-numbered values imply right-to-left layout.</span></span>|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a><span data-ttu-id="e5081-134">Dizinler özelliği</span><span class="sxs-lookup"><span data-stu-id="e5081-134">Indices property</span></span>  
 <span data-ttu-id="e5081-135"><xref:System.Windows.Documents.Glyphs.Indices%2A> Özelliği karakter belirtimleri dizesidir.</span><span class="sxs-lookup"><span data-stu-id="e5081-135">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property is a string of glyph specifications.</span></span> <span data-ttu-id="e5081-136">Tek bir küme dizisi karakterlerin forms burada küme içindeki ilk karakter belirtimi belirtimi kaç karakterlerin ve kümeyi oluşturmak için kaç tane kod noktaları birleştirme tarafından gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="e5081-136">Where a sequence of glyphs forms a single cluster, the specification of the first glyph in the cluster is preceded by a specification of how many glyphs and how many code points combine to form the cluster.</span></span> <span data-ttu-id="e5081-137"><xref:System.Windows.Documents.Glyphs.Indices%2A> Özelliği bir dize içinde aşağıdaki özellikleri toplar.</span><span class="sxs-lookup"><span data-stu-id="e5081-137">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property collects in one string the following properties.</span></span>  
  
-   <span data-ttu-id="e5081-138">Karakter dizinler</span><span class="sxs-lookup"><span data-stu-id="e5081-138">Glyph indices</span></span>  
  
-   <span data-ttu-id="e5081-139">Karakter öncelikli genişlikler</span><span class="sxs-lookup"><span data-stu-id="e5081-139">Glyph advance widths</span></span>  
  
-   <span data-ttu-id="e5081-140">Karakter eki vektörlerini birleştirme</span><span class="sxs-lookup"><span data-stu-id="e5081-140">Combining glyph attachment vectors</span></span>  
  
-   <span data-ttu-id="e5081-141">Karakterlerin kod noktaları küme eşleme</span><span class="sxs-lookup"><span data-stu-id="e5081-141">Cluster mapping from code points to glyphs</span></span>  
  
-   <span data-ttu-id="e5081-142">Karakter bayrakları</span><span class="sxs-lookup"><span data-stu-id="e5081-142">Glyph flags</span></span>  
  
 <span data-ttu-id="e5081-143">Her karakter belirtimi aşağıdaki biçime sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e5081-143">Each glyph specification has the following form.</span></span>  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a><span data-ttu-id="e5081-144">Karakter ölçümü</span><span class="sxs-lookup"><span data-stu-id="e5081-144">Glyph Metrics</span></span>  
 <span data-ttu-id="e5081-145">Her karakteri nasıl diğer hizalar belirtin ölçüleri tanımlar <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="e5081-145">Each glyph defines metrics that specify how it aligns with other <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="e5081-146">Aşağıdaki grafikte iki farklı simge karakteri çeşitli tipografi niteliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e5081-146">The following graphic defines the various typographic qualities of two different glyph characters.</span></span>  
  
 <span data-ttu-id="e5081-147">![Karakter ölçümleri diyagramı](../../../../docs/framework/wpf/advanced/media/glyph-example.png "glyph_example")</span><span class="sxs-lookup"><span data-stu-id="e5081-147">![Diagraph of glyph measurements](../../../../docs/framework/wpf/advanced/media/glyph-example.png "glyph_example")</span></span>  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a><span data-ttu-id="e5081-148">Karakterlerin biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e5081-148">Glyphs Markup</span></span>  
 <span data-ttu-id="e5081-149">Aşağıdaki kod örneğinde çeşitli özelliklerini kullanmayı gösterir <xref:System.Windows.Documents.Glyphs> öğesinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5081-149">The following code example shows how to use various properties of the <xref:System.Windows.Documents.Glyphs> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e5081-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e5081-150">See Also</span></span>  
 [<span data-ttu-id="e5081-151">WPF'de tipografi</span><span class="sxs-lookup"><span data-stu-id="e5081-151">Typography in WPF</span></span>](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [<span data-ttu-id="e5081-152">WPF belgeleri</span><span class="sxs-lookup"><span data-stu-id="e5081-152">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="e5081-153">Metin</span><span class="sxs-lookup"><span data-stu-id="e5081-153">Text</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)
