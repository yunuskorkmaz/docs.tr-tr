---
title: Yol Biçimlendirme Sözdizimi
ms.date: 03/30/2017
helpviewer_keywords:
- attribute usage in XAML [WPF]
- XAML [WPF], attribute usage
- graphics [WPF], PathGeometry class
- XAML [WPF], object element usage
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
ms.openlocfilehash: adcedcea6c8d6d988021cbbccf87bd25a042fd16
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181855"
---
# <a name="path-markup-syntax"></a>Yol Biçimlendirme Sözdizimi
Yollar [WPF Genel Bakış ve](shapes-and-basic-drawing-in-wpf-overview.md) Geometri Genel [Bakış](geometry-overview.md)Şekiller ve Temel Çizim ele alınır, ancak, bu konu ayrıntılı olarak daha [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]kompakt kullanarak yol geometrileri belirtmek için kullanabileceğiniz güçlü ve karmaşık mini dil açıklar.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için <xref:System.Windows.Media.Geometry> nesnelerin temel özelliklerine aşina olmalısınız. Daha fazla bilgi için [Geometriye Genel Bakış'a](geometry-overview.md)bakın.  
  
<a name="abouthisdocument"></a>
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a>StreamGeometri ve PathFigureCollection Mini Diller  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]geometrik yolları açıklamak için mini diller sağlayan <xref:System.Windows.Media.StreamGeometry> <xref:System.Windows.Media.PathFigureCollection>iki sınıf sağlar: ve .  
  
- Bir <xref:System.Windows.Media.StreamGeometry> öğenin özelliği <xref:System.Windows.Media.Geometry> <xref:System.Windows.UIElement.Clip%2A> <xref:System.Windows.UIElement> veya <xref:System.Windows.Shapes.Path.Data%2A> <xref:System.Windows.Shapes.Path> özelliği gibi bir tür özelliği ni ayarlarken mini dili kullanırsınız. Aşağıdaki örnekte bir <xref:System.Windows.Media.StreamGeometry>. oluşturmak için öznitelik sözdizimini kullanır.  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
- Bir <xref:System.Windows.Media.PathGeometry>' <xref:System.Windows.Media.PathFigureCollection> nin özelliğini <xref:System.Windows.Media.PathGeometry.Figures%2A> ayarlarken mini dili kullanırsınız. Aşağıdaki örnek, bir <xref:System.Windows.Media.PathFigureCollection> <xref:System.Windows.Media.PathGeometry>. için bir öznitelik sözdizimi kullanır.  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 Yukarıdaki örneklerden de görebileceğiniz gibi, iki mini dil çok benzer. Her zaman bir kullanabilirsiniz <xref:System.Windows.Media.PathGeometry> herhangi bir durumda kullanmak <xref:System.Windows.Media.StreamGeometry>mümkündür ; bu yüzden hangisini kullanmalısınız? A'yı <xref:System.Windows.Media.StreamGeometry> oluşturduktan sonra yolu değiştirmeniz gerekmediğinde kullanın; yolu <xref:System.Windows.Media.PathGeometry> değiştirmeniz gerekiyorsa a kullanın.  
  
 Nesneler <xref:System.Windows.Media.PathGeometry> ve <xref:System.Windows.Media.StreamGeometry> arasındaki farklar hakkında daha fazla bilgi için [Geometrigenel Bakış'a](geometry-overview.md)bakın.  
  
### <a name="a-note-about-white-space"></a>Beyaz Boşluk Hakkında Bir Not  
 Kısaltma için, izleyen sözdizimi bölümlerinde tek bir boşluk gösterilir, ancak tek bir alanın gösterildiği her yerde birden çok boşluk da kabul edilebilir.  
  
 İki sayının aslında virgül veya beyaz boşlukla ayrılması gerekmese de, bu yalnızca elde edilen dize açık olduğunda yapılabilir. Örneğin, `2..3` aslında iki sayıdır: "2." Ve ".3". Benzer şekilde, `2-3` "2" ve "-3". Boşluklar komutlardan önce veya sonra da gerekli değildir.  
  
### <a name="syntax"></a>Sözdizimi  
 Bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kişinin <xref:System.Windows.Media.StreamGeometry> öznitelik kullanım sözdizimi <xref:System.Windows.Media.FillRule> isteğe bağlı bir değer ve bir veya daha fazla şekil açıklamasından oluşur.  
  
|StreamGeometri XAML Öznitelik Kullanımı|  
|-----------------------------------------|  
|`<`*nesne* *property* `="`özelliği `fillRule` `figureDescription`[ `figureDescription`] [ ]*`" ... />`|  
  
 Bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <xref:System.Windows.Media.PathFigureCollection> in öznitelik kullanım sözdizimi bir veya daha fazla şekil açıklamalarından oluşur.  
  
|PathFigureCollection XAML Öznitelik Kullanımı|  
|-----------------------------------------------|  
|`<`*nesne* *property* `="` `figureDescription`özelliği `figureDescription`[ ]*`" ... />`|  
  
|Sözleşme Dönemi|Açıklama|  
|----------|-----------------|  
|*Fillrule*|<xref:System.Windows.Media.FillRule?displayProperty=nameWithType><br /><br /> Kullanılıp <xref:System.Windows.Media.StreamGeometry> kullanılmayacağını <xref:System.Windows.Media.FillRule.EvenOdd> belirtir. <xref:System.Windows.Media.FillRule.Nonzero> <xref:System.Windows.Media.PathGeometry.FillRule%2A><br /><br /> -   `F0`dolgu kuralını <xref:System.Windows.Media.FillRule.EvenOdd> belirtir.<br />-   `F1`dolgu kuralını <xref:System.Windows.Media.FillRule.Nonzero> belirtir.<br /><br /> Bu komutu atlarsanız, alt ad varsayılan davranışı <xref:System.Windows.Media.FillRule.EvenOdd>kullanır, yani . Bu komutu belirtirseniz, önce yerleştirmeniz gerekir.|  
|*figureDescription*|Hareket komutu, çizim komutları ve isteğe bağlı yakın komuttan oluşan bir şekil.<br /><br /> `moveCommand` `drawCommands`  `[` `closeCommand` `]`|  
|*moveKomut*|Şeklin başlangıç noktasını belirten bir hareket komutu. [Komutu Taşı](#themovecommand) bölümüne bakın.|  
|*drawKomutlar*|Şeklin içeriğini açıklayan bir veya daha fazla çizim komutu. Draw [Komutları](#drawcommands) bölümüne bakın.|  
|*closeCommand*|Şekli kapatan isteğe bağlı bir kapatma komutu. [Komutu Kapat](#closecommand) bölümüne bakın.|  
  
<a name="themovecommand"></a>
## <a name="move-command"></a>Komutu Taşı  
 Yeni bir rakamın başlangıç noktasını belirtir.  
  
|Sözdizimi|  
|------------|  
|`M`*başlangıçNoktası*<br /><br /> - veya -<br /><br /> `m`*başlangıçNoktası*|  
  
|Sözleşme Dönemi|Açıklama|  
|----------|-----------------|  
|*başlangıçNoktası*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Yeni bir figürün başlangıç noktası.|  
  
 Bir büyük `M` harf `startPoint` mutlak bir değer olduğunu gösterir; küçük harf, `m` `startPoint` önceki noktaya mahsup olduğunu gösterir veya (0,0) varsa. Taşıma komutundan sonra birden çok noktayı listelerseniz, satır komutunu belirtmenize rağmen bu noktalara bir çizgi çizilir.  
  
<a name="drawcommands"></a>
## <a name="draw-commands"></a>Komutları Çiz  
 Beraberlik komutu birkaç şekil komutundan oluşabilir. Aşağıdaki şekil komutları mevcuttur: çizgi, yatay çizgi, dikey çizgi, kübik Bezier eğrisi, kuadratik Bezier eğrisi, düzgün kübik Bezier eğrisi, pürüzsüz kuadratik Bezier eğrisi ve eliptik yay.  
  
 Her komutu büyük harf veya küçük harf kullanarak girersiniz: büyük harfler mutlak değerleri gösterir ve küçük harfler göreli değerleri gösterir: bu kesimin denetim noktaları önceki örneğin bitiş noktasına görelidir. Aynı türden birden fazla komutu sırayla girdiğinizde, yinelenen komut girişini atlayabilirsiniz; örneğin, `L 100,200 300,400` `L 100,200 L 300,400`eşdeğerdir . Aşağıdaki tabloda **taşıma** ve **çizim** komutları açıklanmaktadır.  
  
### <a name="line-command"></a>Satır Komutu  
 Geçerli nokta ile belirtilen bitiş noktası arasında düz bir çizgi oluşturur. `l 20 30`ve `L 20,30` geçerli **satır** komutlarına örnektir.  
  
|Sözdizimi|  
|------------|  
|`L`*endPoint*<br /><br /> - veya -<br /><br /> `l`*endPoint*|  
  
|Sözleşme Dönemi|Açıklama|  
|----------|-----------------|  
|*Bitiş noktası*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Çizginin bitiş noktası.|  

Bir büyük `L` harf `endPoint` mutlak bir değer olduğunu gösterir; küçük harf, `l` `endPoint` önceki noktaya mahsup olduğunu gösterir veya (0,0) varsa.

### <a name="horizontal-line-command"></a>Yatay Çizgi Komutu  
 Geçerli nokta ile belirtilen x-koordinatı arasında yatay bir çizgi oluşturur. `H 90`geçerli bir yatay çizgi komutu örneğidir.

|Sözdizimi|  
|------------|  
|`H`  *X*<br /><br /> - veya -<br /><br /> `h`  *X*|  
  
|Sözleşme Dönemi|Açıklama|  
|----------|-----------------|  
|*X*|<xref:System.Double?displayProperty=nameWithType><br /><br /> Çizginin bitiş noktasının x-koordinatı.|  
  
Bir büyük `H` harf `x` mutlak bir değer olduğunu gösterir; küçük harf, `h` `x` önceki noktaya mahsup olduğunu gösterir veya (0,0) varsa.
  
### <a name="vertical-line-command"></a>Dikey Çizgi Komutu  
 Geçerli nokta ile belirtilen y-koordinatı arasında dikey bir çizgi oluşturur. `v 90`geçerli bir dikey çizgi komutu örneğidir.

|Sözdizimi|  
|------------|  
|`V`  *Y*<br /><br /> - veya -<br /><br /> `v`  *Y*|  
  
|Sözleşme Dönemi|Açıklama|  
|----------|-----------------|  
|*Y*|<xref:System.Double?displayProperty=nameWithType><br /><br /> Çizginin bitiş noktasının y-koordinatı.|  

Bir büyük `V` harf `y` mutlak bir değer olduğunu gösterir; küçük harf, `v` `y` önceki noktaya mahsup olduğunu gösterir veya (0,0) varsa.  

### <a name="cubic-bezier-curve-command"></a>Kübik Bezier Eğrisi Komutu  
 Belirtilen iki kontrol noktası (1`controlPoint`ve `controlPoint`2) kullanarak geçerli nokta ile belirtilen bitiş noktası arasında kübik Bezier eğrisi oluşturur. `C 100,200 200,400 300,200`geçerli bir eğri komutu örneğidir.  
  
|Sözdizimi|  
|------------|  
|`C``controlPoint`1`controlPoint`2.2.2.2`endPoint`<br /><br /> - veya -<br /><br /> `c``controlPoint`1`controlPoint`2.2.2.2`endPoint`|  
  
|Sözleşme Dönemi|Açıklama|  
|----------|-----------------|  
|`controlPoint`1|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Eğrinin başlangıç teğetini belirleyen eğrinin ilk kontrol noktası.|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Eğrinin bitiş teğetini belirleyen eğrinin ikinci kontrol noktası.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Eğrinin çizildiği nokta.|  
  
### <a name="quadratic-bezier-curve-command"></a>Quadratic Bezier Eğri Komutu  
 Belirtilen kontrol noktasını kullanarak geçerli nokta ile belirtilen bitiş noktası arasında kuadratik bir Bezier eğrisi oluşturur .`controlPoint` `q 100,200 300,200`geçerli bir kuadratik Bezier eğri komutu örneğidir.  
  
|Sözdizimi|  
|------------|  
|`Q` `controlPoint` `endPoint`<br /><br /> - veya -<br /><br /> `q` `controlPoint` `endPoint`|  
  
|Sözleşme Dönemi|Açıklama|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Eğrinin başlangıç ve bitiş teğetlerini belirleyen eğrinin kontrol noktası.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Eğrinin çizildiği nokta.|  
  
### <a name="smooth-cubic-bezier-curve-command"></a>Düzgün kübik Bezier eğrisi Komutu  
 Geçerli nokta ile belirtilen bitiş noktası arasında bir kübik Bezier eğrisi oluşturur. İlk denetim noktası, geçerli noktaya göre önceki komutun ikinci denetim noktasının yansıması olarak kabul edilir. Önceki komut yoksa veya önceki komut kübik Bezier eğrisi komutu veya düzgün bir kübik Bezier eğrisi komutu değilse, ilk denetim noktasının geçerli noktayla çakıştUğuvarmı varsayıştın. İkinci kontrol noktası, eğrinin sonu için kontrol noktası, `controlPoint`2 ile belirtilir. Örneğin, `S 100,200 200,300` geçerli bir düzgün kübik Bezier eğrisi komutudur.  
  
|Sözdizimi|  
|------------|  
|`S``controlPoint`2.000`endPoint`<br /><br /> - veya -<br /><br /> `s``controlPoint`2.000`endPoint`|  
  
|Sözleşme Dönemi|Açıklama|  
|----------|-----------------|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Eğrinin bitiş teğetini belirleyen eğrinin kontrol noktası.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Eğrinin çizildiği nokta.|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a>Pürüzsüz kuadratik Bezier eğrisi Komutu  
 Geçerli nokta ile belirtilen bitiş noktası arasında kuadratik bir Bezier eğrisi oluşturur. Denetim noktasının, geçerli noktaya göre önceki komutun denetim noktasının yansıması olduğu varsayılır. Önceki komut yoksa veya önceki komut bir kuadratik Bezier eğrisi komutu veya düzgün bir kuadratik Bezier eğri komutu değilse, denetim noktası geçerli nokta ile çakışık olur.  
  
|Sözdizimi|  
|------------|  
|`T` `controlPoint` `endPoint`<br /><br /> - veya -<br /><br /> `t` `controlPoint` `endPoint`|  
  
|Sözleşme Dönemi|Açıklama|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Eğrinin başlangıç ve teğetini belirleyen eğrinin kontrol noktası.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Eğrinin çizildiği nokta.|  
  
### <a name="elliptical-arc-command"></a>Eliptik Yay Komutu  
 Geçerli nokta ile belirtilen bitiş noktası arasında eliptik bir yay oluşturur.  
  
|Sözdizimi|  
|------------|  
|`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`<br /><br /> - veya -<br /><br /> `a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`|  
  
|Sözleşme Dönemi|Açıklama|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=nameWithType><br /><br /> Yay'ın x ve y yarıçapı.|  
|`rotationAngle`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Elipsin derece olarak dönüşü.|  
|`isLargeArcFlag`|Yay açısı 180 derece veya daha büyük olmalıdır eğer 1 ayarlayın; aksi takdirde, 0 olarak ayarlanır.|  
|`sweepDirectionFlag`|Yay pozitif açı yönünde çizilirse 1 olarak ayarlayın; aksi takdirde, 0 olarak ayarlanır.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Yay çizilir noktası.|  
  
<a name="closecommand"></a>
## <a name="the-close-command"></a>Yakın Komut  
 Geçerli rakamı sona erdirer ve geçerli noktayı figürün başlangıç noktasına bağlayan bir çizgi oluşturur. Bu komut, son kesim ile figürün ilk kesimi arasında bir satır birleştirme (köşe) oluşturur.  
  
|Sözdizimi|  
|------------|  
|`Z`<br /><br /> - veya -<br /><br /> `z`|  

<a name="pointsyntax"></a>
## <a name="point-syntax"></a>Nokta Sözdizimi  
 (0,0) sol üst köşe olan bir noktanın x- ve y-koordinatlarını açıklar.
  
|Sözdizimi|  
|------------|  
|`x` `,` `y`<br /><br /> - veya -<br /><br /> `x` `y`|  
  
|Sözleşme Dönemi|Açıklama|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Noktanın x-koordinatı.|  
|`y`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Noktanın y-koordinatı.|  
  
<a name="specialvalues"></a>
## <a name="special-values"></a>Özel Değerler  
 Standart sayısal değer yerine, aşağıdaki özel değerleri de kullanabilirsiniz. Bu değerler büyük/küçük harf duyarlıdır.  
  
 Sonsuz  
 Temsil <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>eder.  
  
 -Sonsuzluk  
 Temsil <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>eder.  
  
 NaN  
 Temsil <xref:System.Double.NaN?displayProperty=nameWithType>eder.  
  
 Ayrıca bilimsel gösterim kullanabilirsiniz. Örneğin, `+1.e17` geçerli bir değerdir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.PathFigureCollection>
- [WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler](shapes-and-basic-drawing-in-wpf-overview.md)
- [Geometriye Genel Bakış](geometry-overview.md)
- [Nasıl Dır Konular](geometries-how-to-topics.md)
