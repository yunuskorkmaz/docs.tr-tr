---
title: Yol Biçimlendirme Sözdizimi
ms.date: 03/30/2017
helpviewer_keywords:
- attribute usage in XAML [WPF]
- XAML [WPF], attribute usage
- graphics [WPF], PathGeometry class
- XAML [WPF], object element usage
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
ms.openlocfilehash: d681cd15fa3daa3698edc5e0ad3d3c2669c1dfdf
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43804538"
---
# <a name="path-markup-syntax"></a>Yol Biçimlendirme Sözdizimi
Yolları açıklanmıştır [şekiller ve temel çizimlere WPF genel bakışında](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md) ve [geometrisi](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md), ancak bu konuda yol belirtmek için kullanabileceğiniz güçlü ve karmaşık mini dil ayrıntılı olarak açıklanmaktadır. geometriler daha sıkı bir şekilde kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda anlamak için temel özellikleriyle ilgili bilgi sahibi olmalısınız <xref:System.Windows.Media.Geometry> nesneleri. Daha fazla bilgi için [geometrisi](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="abouthisdocument"></a>   
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a>StreamGeometry ve PathFigureCollection Mini dilleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Geometrik yollar açıklamak için mini-diller sağlayan iki sınıf sağlar: <xref:System.Windows.Media.StreamGeometry> ve <xref:System.Windows.Media.PathFigureCollection>.  
  
-   Kullandığınız <xref:System.Windows.Media.StreamGeometry> türünün özelliğini ayarlarken mini dil <xref:System.Windows.Media.Geometry>, gibi <xref:System.Windows.UIElement.Clip%2A> özelliği bir <xref:System.Windows.UIElement> veya <xref:System.Windows.Shapes.Path.Data%2A> özelliği bir <xref:System.Windows.Shapes.Path> öğesi. Aşağıdaki örnek oluşturmak için öznitelik sözdizimi kullanan bir <xref:System.Windows.Media.StreamGeometry>.  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
-   Kullandığınız <xref:System.Windows.Media.PathFigureCollection> ayarlarken mini dil <xref:System.Windows.Media.PathGeometry.Figures%2A> özelliği bir <xref:System.Windows.Media.PathGeometry>. Aşağıdaki örnek oluşturmak için bir öznitelik sözdizimi kullanan bir <xref:System.Windows.Media.PathFigureCollection> için bir <xref:System.Windows.Media.PathGeometry>.  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 Önceki örneklerde de görebileceğiniz gibi iki küçük dil oldukça benzerdir. Her zaman kullanmak mümkün mü bir <xref:System.Windows.Media.PathGeometry> kullanabileceğiniz herhangi bir durumda bir <xref:System.Windows.Media.StreamGeometry>; bu nedenle, hangisini kullanmalısınız? Kullanan bir <xref:System.Windows.Media.StreamGeometry> yolu; oluşturduktan sonra değiştirmek ihtiyacınız kalmadığında kullanmak bir <xref:System.Windows.Media.PathGeometry> yolun değişiklik yapmanız gerekiyorsa.  
  
 Arasındaki farklar hakkında daha fazla bilgi için <xref:System.Windows.Media.PathGeometry> ve <xref:System.Windows.Media.StreamGeometry> nesneleri bkz [geometrisi](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
### <a name="a-note-about-white-space"></a>Boşluk hakkında bir Not  
 Kısaltma, tek bir boşluk, aşağıdaki sözdizimi bölümlerinde gösterilen, ancak tek bir boşluk gösterilen yerde birden çok boşluklar da kabul edilir.  
  
 İki sayı aslında noktalı virgül veya boşluk ayrılmış gerekmez, ancak sonuç dizesi belirsiz olduğunda bu yalnızca yapılabilir. Örneğin, `2..3` gerçekte iki sayıdır: "2." Ve ". 3". Benzer şekilde, `2-3` "2" ve "-3". Boşluk önce veya sonra komutları ya da gerekli değildir.  
  
### <a name="syntax"></a>Sözdizimi  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Özniteliği için kullanım söz dizimine bir <xref:System.Windows.Media.StreamGeometry> isteğe oluşan <xref:System.Windows.Media.FillRule> değer ve bir veya daha fazla açıklamaları şekil.  
  
|StreamGeometry XAML öznitelik kullanımı|  
|-----------------------------------------|  
|`<` *Nesne* *özelliği* `="`[ `fillRule`] `figureDescription`[ `figureDescription`] * `" ... />`|  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Özniteliği için kullanım söz dizimine bir <xref:System.Windows.Media.PathFigureCollection> bir veya daha fazla şekil açıklamalarını oluşur.  
  
|PathFigureCollection XAML öznitelik kullanımı|  
|-----------------------------------------------|  
|`<` *Nesne* *özelliği* `="` `figureDescription`[ `figureDescription`] * `" ... />`|  
  
|Terim|Açıklama|  
|----------|-----------------|  
|*fillRule*|<xref:System.Windows.Media.FillRule?displayProperty=nameWithType><br /><br /> Belirtir olup olmadığını <xref:System.Windows.Media.StreamGeometry> kullanan <xref:System.Windows.Media.FillRule.EvenOdd> veya <xref:System.Windows.Media.FillRule.Nonzero> <xref:System.Windows.Media.PathGeometry.FillRule%2A>.<br /><br /> -   `F0` belirtir <xref:System.Windows.Media.FillRule.EvenOdd> doldurma kuralı.<br />-   `F1` belirtir <xref:System.Windows.Media.FillRule.Nonzero> doldurma kuralı.<br /><br /> Bu komut atlarsanız, yükleme kökü olan varsayılan davranışı kullanan <xref:System.Windows.Media.FillRule.EvenOdd>. Bu komut belirtirseniz, bu ilk yerleştirmeniz gerekir.|  
|*figureDescription*|Taşı komutu, oluşan bir şekil, komutlar ve isteğe bağlı bir Kapat komut çizin.<br /><br /> `moveCommand` `drawCommands`  `[` `closeCommand` `]`|  
|*moveCommand*|Şekil başlangıç noktasını belirten bir taşıma komutu. Bkz: [Taşı komutunu](#themovecommand) bölümü.|  
|*drawCommands*|Şekil'ın içeriğini açıklayan bir veya daha fazla çizim komutları. Bkz: [çizim komutları](#drawcommands) bölümü.|  
|*closeCommand*|Şekil kapatır isteğe bağlı bir kapatma komutu. Bkz: [Kapat komut](#closecommand) bölümü.|  
  
<a name="themovecommand"></a>   
## <a name="move-command"></a>Taşı komutu  
 Yeni bir şekil başlangıç noktasını belirtir.  
  
|Sözdizimi|  
|------------|  
|`M` *startPoint*<br /><br /> - veya -<br /><br /> `m` *startPoint*|  
  
|Terim|Açıklama|  
|----------|-----------------|  
|*startPoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Yeni bir şekil başlangıç noktası.|  
  
 Bir büyük harf `M` gösterir `startPoint` mutlak bir değerdir; bir küçük harf `m` belirten `startPoint` bir uzaklık önceki noktaya veya yoksa (0,0). Taşıma komutundan sonra birden çok noktaları listesinde, bir çizgi komut satırı belirtildi ancak bu noktalarına çizilir.  
  
<a name="drawcommands"></a>   
## <a name="draw-commands"></a>Çizim komutlarını  
 Çizim komutu, birden çok şekil komutlarından oluşabilir. Aşağıdaki şekil komutları kullanılabilir: satır, yatay çizgi, dikey çizgi, üçüncü dereceden Bezier eğrisi, ikinci dereceden Bezier eğrisi, kesintisiz üçüncü dereceden Bezier eğrisi, kesintisiz ikinci dereceden Bezier eğrisi ve elips yay.  
  
 Bir büyük harf veya küçük harf kullanarak her komutu girin: büyük harfler mutlak değerler belirtmek ve küçük harfler göreli değerlerini göstermek: önceki örneğe göre bitiş noktasını bu kesimi için denetim noktaları olan. Sıralı olarak aynı türde birden fazla komutu girerken, yinelenen komut girişini atlayabilirsiniz; Örneğin, `L 100,200 300,400` eşdeğerdir `L 100,200 L 300,400`. Aşağıdaki tabloda açıklanmıştır **taşıma** ve **çizmek** komutları.  
  
### <a name="line-command"></a>Komut satırı  
 Geçerli nokta ile belirtilen uç nokta arasında düz bir çizgi oluşturur. `l 20 30` ve `L 20,30` geçerli örnekleri **satırı** komutları.  
  
|Sözdizimi|  
|------------|  
|`L` *uç noktası*<br /><br /> - veya -<br /><br /> `l` *uç noktası*|  
  
|Terim|Açıklama|  
|----------|-----------------|  
|*endPoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Çizginin bitiş noktası.|  

Bir büyük harf `L` gösterir `endPoint` mutlak bir değerdir; bir küçük harf `l` belirten `endPoint` bir uzaklık önceki noktaya veya yoksa (0,0).

### <a name="horizontal-line-command"></a>Yatay çizgi komutu  
 Geçerli nokta ile belirtilen x koordinatını arasındaki yatay çizgi oluşturur. `H 90` Geçerli yatay çizgi komut bir örnektir.

  
|Sözdizimi|  
|------------|  
|`H`  *x*<br /><br /> - veya -<br /><br /> `h`  *x*|  
  
|Terim|Açıklama|  
|----------|-----------------|  
|*x*|<xref:System.Double?displayProperty=nameWithType><br /><br /> X koordinatını çizginin bitiş noktası.|  
  
Bir büyük harf `H` gösterir `x` mutlak bir değerdir; bir küçük harf `h` belirten `x` bir uzaklık önceki noktaya veya yoksa (0,0).
  
### <a name="vertical-line-command"></a>Dikey çizgi komutu  
 Geçerli nokta ile belirtilen y koordinatını arasında bir dikey çizgi oluşturur. `v 90` Geçerli bir dikey çizgi komut bir örnektir.

  
|Sözdizimi|  
|------------|  
|`V`  *y*<br /><br /> - veya -<br /><br /> `v`  *y*|  
  
|Terim|Açıklama|  
|----------|-----------------|  
|*Y*|<xref:System.Double?displayProperty=nameWithType><br /><br /> Y koordinatını çizginin bitiş noktası.|  

Bir büyük harf `V` gösterir `y` mutlak bir değerdir; bir küçük harf `v` belirten `y` bir uzaklık önceki noktaya veya yoksa (0,0).  
    
### <a name="cubic-bezier-curve-command"></a>Üçüncü dereceden Bezier eğrisi komutu  
 Bir üçüncü dereceden Bezier eğrisi geçerli nokta ile belirtilen bitiş noktası arasında iki belirtilen denetim noktalarına kullanarak oluşturur (`controlPoint`1 ve `controlPoint`2). `C 100,200 200,400 300,200` Geçerli bir eğri komutu örneğidir.  
  
|Sözdizimi|  
|------------|  
|`C` `controlPoint`1`controlPoint`2`endPoint`<br /><br /> - veya -<br /><br /> `c` `controlPoint`1`controlPoint`2`endPoint`|  
  
|Terim|Açıklama|  
|----------|-----------------|  
|`controlPoint`1|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> İlk denetim noktası eğrisinin eğri başlangıç tanjantını belirler.|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> İkinci denetim noktası eğrisinin eğri bitiş tanjantını belirler.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Noktası çizilen eğri için.|  
  
### <a name="quadratic-bezier-curve-command"></a>İkinci dereceden Bezier eğrisi komutu  
 Belirtilen denetim noktasını kullanarak bir ikinci dereceden Bezier eğrisi geçerli nokta ile belirtilen bitiş noktası arasında oluşturur (`controlPoint`). `q 100,200 300,200` Geçerli bir ikinci dereceden Bezier eğrisi komutu örneğidir.  
  
|Sözdizimi|  
|------------|  
|`Q` `controlPoint` `endPoint`<br /><br /> - veya -<br /><br /> `q` `controlPoint` `endPoint`|  
  
|Terim|Açıklama|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Denetim noktası eğrisinin başlangıç ve bitiş eğrinin eğimleri belirler.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Noktası çizilen eğri için.|  
  
### <a name="smooth-cubic-bezier-curve-command"></a>Kesintisiz üçüncü dereceden Bezier eğrisi komutu  
 Bir üçüncü dereceden Bezier eğrisi arasında geçerli nokta ile belirtilen uç noktası oluşturur. İlk denetim noktası, önceki komutun geçerli noktasına göre ikinci kontrol noktasının yansıma olduğu varsayılır. Önceki komut ise ya da önceki komutun bir üçüncü dereceden Bezier eğrisi komutu veya bir kesintisiz üçüncü dereceden Bezier eğrisi komutu değilse ilk denetim noktası geçerli noktasıyla çakışık olduğunu varsayalım. İkinci denetim noktası eğrinin bitişi için denetim noktası tarafından belirtilen `controlPoint`2. Örneğin, `S 100,200 200,300` geçerli bir kesintisiz üçüncü dereceden Bezier eğrisi komutudur.  
  
|Sözdizimi|  
|------------|  
|`S` `controlPoint`2`endPoint`<br /><br /> - veya -<br /><br /> `s` `controlPoint`2`endPoint`|  
  
|Terim|Açıklama|  
|----------|-----------------|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Denetim noktası eğrisinin eğri bitiş tanjantını belirler.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Noktası çizilen eğri için.|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a>Kesintisiz ikinci dereceden Bezier eğrisi komutu  
 Geçerli nokta ile belirtilen bitiş noktası arasında bir ikinci dereceden Bezier eğrisi oluşturur. Denetim noktası, önceki komutun geçerli noktasına göre kontrol noktasının yansıma olduğu varsayılır. Önceki komut veya önceki komutun bir ikinci dereceden Bezier eğrisi komutu veya sorunsuz bir ikinci dereceden Bezier eğrisi komutu başarısız olduysa, denetim noktası geçerli nokta ile çakışık ise.  
  
|Sözdizimi|  
|------------|  
|`T` `controlPoint` `endPoint`<br /><br /> - veya -<br /><br /> `t` `controlPoint` `endPoint`|  
  
|Terim|Açıklama|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Denetim noktası eğrisinin başlangıç ve eğrinin Eğim belirler.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Noktası çizilen eğri için.|  
  
### <a name="elliptical-arc-command"></a>Elips yay komutu  
 Elips yay arasında geçerli nokta ile belirtilen uç noktası oluşturur.  
  
|Sözdizimi|  
|------------|  
|`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`<br /><br /> - veya -<br /><br /> `a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`|  
  
|Terim|Açıklama|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=nameWithType><br /><br /> X ve y yarıçapını yayın.|  
|`rotationAngle`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Elipsin derece döndürme.|  
|`isLargeArcFlag`|180 derece Yayı açısı gerekiyorsa 1 olarak ayarlayın veya üzeri; Aksi durumda 0 olarak ayarlayın.|  
|`sweepDirectionFlag`|Yayı açı olumlu yönde çizilirse 1 olarak ayarlayın; Aksi durumda 0 olarak ayarlayın.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Noktanın Ark çizilen.|  
  
<a name="closecommand"></a>   
## <a name="the-close-command"></a>Kapatma komutu  
 Geçerli şekil sona erer ve geçerli noktasını şekil başlangıç noktasına bağlayan bir satır oluşturur. Bu komut, son segmenti şekil ilk kesimi arasındaki bir satır katılım (köşe) oluşturur.  
  
|Sözdizimi|  
|------------|  
|`Z`<br /><br /> - veya -<br /><br /> `z`|  

<a name="pointsyntax"></a>   
## <a name="point-syntax"></a>Nokta sözdizimi  
 X ve y-koordinatları noktası açıklar nerede (0,0) sol üst köşedeki olduğu.
  
|Sözdizimi|  
|------------|  
|`x` `,` `y`<br /><br /> - veya -<br /><br /> `x``y`|  
  
|Terim|Açıklama|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=nameWithType><br /><br /> X koordinatını noktası.|  
|`y`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Y koordinatını noktası.|  
  
<a name="specialvalues"></a>   
## <a name="special-values"></a>Özel değerler  
 Standart bir sayısal değer yerine aşağıdaki özel değerler kullanabilirsiniz. Bu değerler büyük/küçük harfe duyarlıdır.  
  
 sonsuz  
 Temsil eden <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.  
  
 -Infinity  
 Temsil eden <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>.  
  
 NaN  
 Temsil eden <xref:System.Double.NaN?displayProperty=nameWithType>.  
  
 Bilimsel gösterim de kullanabilir. Örneğin, `+1.e17` , geçerli bir değer.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.StreamGeometry>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Media.PathFigureCollection>  
 [WPF’de Şekiller ve Temel Çizimlere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Geometriye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/geometries-how-to-topics.md)
