---
title: Yol Biçimlendirme Sözdizimi
ms.date: 03/30/2017
helpviewer_keywords:
- attribute usage in XAML [WPF]
- XAML [WPF], attribute usage
- graphics [WPF], PathGeometry class
- XAML [WPF], object element usage
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
ms.openlocfilehash: 86901f357c43dc7c0c1402bf313e674603eaccbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="path-markup-syntax"></a>Yol Biçimlendirme Sözdizimi
Yolları açıklanmıştır [şekilleri ve WPF genel bakış temel çizim](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md) ve [geometrisi](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md), ancak, bu konuda yolunu belirtmek için kullanabileceğiniz güçlü ve karmaşık Mini dili ayrıntılı olarak açıklanmaktadır. geometri kullanarak daha sıkı şekilde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için temel özellikleri ile bilgi sahibi olmanız <xref:System.Windows.Media.Geometry> nesneleri. Daha fazla bilgi için bkz: [geometrisi](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="abouthisdocument"></a>   
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a>StreamGeometry ve PathFigureCollection Mini dilleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Geometrik yolları açıklamak için mini-diller sağlayan iki sınıfı sağlar: <xref:System.Windows.Media.StreamGeometry> ve <xref:System.Windows.Media.PathFigureCollection>.  
  
-   Kullandığınız <xref:System.Windows.Media.StreamGeometry> türünde bir özellik ayarlarken mini dil <xref:System.Windows.Media.Geometry>, gibi <xref:System.Windows.UIElement.Clip%2A> özelliği bir <xref:System.Windows.UIElement> veya <xref:System.Windows.Shapes.Path.Data%2A> özelliği bir <xref:System.Windows.Shapes.Path> öğesi. Aşağıdaki örnek oluşturmak için öznitelik sözdizimini kullanır bir <xref:System.Windows.Media.StreamGeometry>.  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
-   Kullandığınız <xref:System.Windows.Media.PathFigureCollection> ayarlarken mini dil <xref:System.Windows.Media.PathGeometry.Figures%2A> özelliği bir <xref:System.Windows.Media.PathGeometry>. Aşağıdaki örnek oluşturmak için bir öznitelik sözdizimi kullanan bir <xref:System.Windows.Media.PathFigureCollection> için bir <xref:System.Windows.Media.PathGeometry>.  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 Önceki örneklerde görüldüğü gibi iki mini dil çok benzer. Kullanmak her zaman mümkündür bir <xref:System.Windows.Media.PathGeometry> kullanabileceğiniz durumda bir <xref:System.Windows.Media.StreamGeometry>; bunu hangisinin kullanmalısınız? Kullanan bir <xref:System.Windows.Media.StreamGeometry> ; oluşturduktan sonra yolu değiştirmek gerekmediğinde kullanmak bir <xref:System.Windows.Media.PathGeometry> yolu değiştirmek ihtiyacınız varsa.  
  
 Arasındaki farklar hakkında daha fazla bilgi için <xref:System.Windows.Media.PathGeometry> ve <xref:System.Windows.Media.StreamGeometry> nesneleri bkz [geometrisi](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
### <a name="a-note-about-white-space"></a>Boşluk hakkında bir Not  
 Kısaltma amacıyla, tek bir boşluk izleyen sözdizimi bölümlerinde gösterilen, ancak birden fazla boşlukları da tek bir boşluk gösterilen her yerde kabul edilir.  
  
 İki sayı gerçekte bir virgül veya boşluk ile ayrılmış olması gerekmez, ancak sonuç dizesini anlaşılır olduğunda bu yalnızca yapılabilir. Örneğin, `2..3` gerçekte iki sayıdır: "2." Ve ". 3". Benzer şekilde, `2-3` "2" ve "-3" olur. Alanları komutlardan, önce veya sonra ya da gerekli değildir.  
  
### <a name="syntax"></a>Sözdizimi  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Öznitelik kullanım sözdizimi için bir <xref:System.Windows.Media.StreamGeometry> isteğe oluşur <xref:System.Windows.Media.FillRule> değer ve bir veya daha fazla açıklamaları şekil.  
  
|StreamGeometry XAML öznitelik kullanımı|  
|-----------------------------------------|  
|`<` *Nesne* *özelliği* `="`[ `fillRule`] `figureDescription`[ `figureDescription`] * `" ... />`|  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Öznitelik kullanım sözdizimi için bir <xref:System.Windows.Media.PathFigureCollection> bir veya daha fazla şekil açıklamalarını oluşur.  
  
|PathFigureCollection XAML öznitelik kullanımı|  
|-----------------------------------------------|  
|`<` *Nesne* *özelliği* `="` `figureDescription`[ `figureDescription`] * `" ... />`|  
  
|Terim|Açıklama|  
|----------|-----------------|  
|*fillRule*|<xref:System.Windows.Media.FillRule?displayProperty=nameWithType><br /><br /> Belirtir olup olmadığını <xref:System.Windows.Media.StreamGeometry> kullanan <xref:System.Windows.Media.FillRule.EvenOdd> veya <xref:System.Windows.Media.FillRule.Nonzero> <xref:System.Windows.Media.PathGeometry.FillRule%2A>.<br /><br /> -   `F0` belirtir <xref:System.Windows.Media.FillRule.EvenOdd> dolgu kuralı.<br />-   `F1` belirtir <xref:System.Windows.Media.FillRule.Nonzero> dolgu kuralı.<br /><br /> Bu komut atlarsanız, alt yolu olan varsayılan davranışı kullanacağını <xref:System.Windows.Media.FillRule.EvenOdd>. Bu komut belirtirseniz, bu ilk yerleştirmeniz gerekir.|  
|*figureDescription*|Bir taşı komutu, oluşan bir şekil komutlar ve isteğe bağlı bir Kapat komutunu çizin.<br /><br /> `moveCommand` `drawCommands`  `[` `closeCommand` `]`|  
|*moveCommand*|Şekil başlangıç noktasını belirtir taşıma komutu. Bkz: [Taşı komutunu](#themovecommand) bölümü.|  
|*drawCommands*|Şekil 's içeriğini açıklayan bir veya daha fazla çizim komutları. Bkz: [çizim komutları](#drawcommands) bölümü.|  
|*closeCommand*|Şekil kapatan bir isteğe bağlı Kapat komutu. Bkz: [Kapat komutunu](#closecommand) bölümü.|  
  
<a name="themovecommand"></a>   
## <a name="move-command"></a>Move komutu  
 Yeni bir şekil başlangıç noktasını belirtir.  
  
|Sözdizimi|  
|------------|  
|`M` *startPoint*<br /><br /> - veya -<br /><br /> `m` *startPoint*|  
  
|Terim|Açıklama|  
|----------|-----------------|  
|*startPoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Yeni bir şekil başlangıç noktası.|  
  
 Büyük harf `M` belirten `startPoint` mutlak bir değer; olan küçük harf `m` belirten `startPoint` önceki noktasına bir uzaklık ya da (yoksa 0,0). Taşıma komutundan sonra birden çok nokta listelerseniz komut satırı belirtilen rağmen bir çizgi bu noktalarına çizilir.  
  
<a name="drawcommands"></a>   
## <a name="draw-commands"></a>Çizim komutları  
 Çizim komutu çeşitli şekil komutlarından oluşabilir. Aşağıdaki şekil komutları kullanılabilir: satır, yatay çizgi, dikey çizgi, küp Bezier eğrisi, ikinci dereceden Bezier eğrisi, kesintisiz küp Bezier eğrisi, kesintisiz ikinci dereceden Bezier eğrisi ve elips yay.  
  
 Bir büyük veya küçük harf kullanarak her komutu girin: büyük harfler mutlak değerler belirtmek ve küçük harfler göreli değerlerini göstermek: denetim Bu kesimin göre uç noktası önceki örnekte noktalarıdır. Aynı türde birden fazla komut sırayla girerken, yinelenen komut girişini atlayabilirsiniz; Örneğin, `L 100,200 300,400` eşdeğerdir `L 100,200 L 300,400`. Aşağıdaki tabloda açıklanmaktadır **taşıma** ve **çizin** komutları.  
  
### <a name="line-command"></a>Komut satırı  
 Güncel nokta ve belirtilen bitiş noktası arasında düz bir çizgi oluşturur. `l 20 30` ve `L 20,30` geçerli örnekleri **satır** komutları.  
  
|Sözdizimi|  
|------------|  
|`L` *uç noktası*<br /><br /> - veya -<br /><br /> `l` *uç noktası*|  
  
|Terim|Açıklama|  
|----------|-----------------|  
|*endPoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Çizginin bitiş noktası.|  

Büyük harf `L` belirten `endPoint` mutlak bir değer; olan küçük harf `l` belirten `endPoint` önceki noktasına bir uzaklık ya da (yoksa 0,0).

### <a name="horizontal-line-command"></a>Yatay çizgi komutu  
 Belirtilen x koordinatını geçerli noktası arasındaki yatay çizgi oluşturur. `H 90` Geçerli bir yatay çizgi komutu örneğidir.

  
|Sözdizimi|  
|------------|  
|`H`  *x*<br /><br /> - veya -<br /><br /> `h`  *x*|  
  
|Terim|Açıklama|  
|----------|-----------------|  
|*x*|<xref:System.Double?displayProperty=nameWithType><br /><br /> X koordinatını satırının bitiş noktası.|  
  
Büyük harf `H` belirten `x` mutlak bir değer; olan küçük harf `h` belirten `x` önceki noktasına bir uzaklık ya da (yoksa 0,0).
  
### <a name="vertical-line-command"></a>Dikey çizgi komutu  
 Güncel nokta ve belirtilen y koordinatını arasında dikey çizgi oluşturur. `v 90` Geçerli bir dikey çizgi komutu örneğidir.

  
|Sözdizimi|  
|------------|  
|`V`  *y*<br /><br /> - veya -<br /><br /> `v`  *y*|  
  
|Terim|Açıklama|  
|----------|-----------------|  
|*Y*|<xref:System.Double?displayProperty=nameWithType><br /><br /> Y koordinatını satırının bitiş noktası.|  

Büyük harf `V` belirten `y` mutlak bir değer; olan küçük harf `v` belirten `y` önceki noktasına bir uzaklık ya da (yoksa 0,0).  
    
### <a name="cubic-bezier-curve-command"></a>Küp Bezier eğrisi komutu  
 İki belirtilen denetim noktalarını kullanarak güncel nokta ve belirtilen bitiş noktası arasında bir küp Bezier eğrisi oluşturur (`controlPoint`1 ve `controlPoint`2). `C 100,200 200,400 300,200` Geçerli bir eğri komutu örneğidir.  
  
|Sözdizimi|  
|------------|  
|`C` `controlPoint`1`controlPoint`2`endPoint`<br /><br /> - veya -<br /><br /> `c` `controlPoint`1`controlPoint`2`endPoint`|  
  
|Terim|Açıklama|  
|----------|-----------------|  
|`controlPoint`1|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Eğriyi başlangıç tanjantını belirleyen eğrinin ilk denetim noktası.|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Eğriyi bitiş tanjantını belirleyen eğrinin ikinci denetim noktası.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Noktası çizilen eğri.|  
  
### <a name="quadratic-bezier-curve-command"></a>İkinci dereceden Bezier eğrisi komutu  
 Belirtilen denetim noktasını kullanarak güncel nokta ve belirtilen bitiş noktası arasında ikinci dereceden Bezier eğrisi oluşturur (`controlPoint`). `q 100,200 300,200` Geçerli bir ikinci dereceden Bezier eğrisi komutu örneğidir.  
  
|Sözdizimi|  
|------------|  
|`Q` `controlPoint` `endPoint`<br /><br /> - veya -<br /><br /> `q` `controlPoint` `endPoint`|  
  
|Terim|Açıklama|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Denetim noktası eğrinin başlangıç ve bitiş eğrinin tanjantları belirler.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Noktası çizilen eğri.|  
  
### <a name="smooth-cubic-bezier-curve-command"></a>Kesintisiz küp Bezier eğrisi komutu  
 Güncel nokta ve belirtilen bitiş noktası arasında küp Bezier eğrisi oluşturur. İlk denetim noktasının geçerli noktaya göre önceki komutun ikinci denetim noktası yansıma olduğu varsayılır. Önceki komut ise veya önceki komutu bir küp Bezier eğrisi komutu veya kesintisiz bir küp Bezier eğrisi komutu değilse ilk denetim noktasının güncel nokta ile çakışık olduğunu varsayın. İkinci denetim noktası, eğrinin bitişi için denetim noktası tarafından belirtilir `controlPoint`2. Örneğin, `S 100,200 200,300` geçerli bir kesintisiz küp Bezier eğrisi komutudur.  
  
|Sözdizimi|  
|------------|  
|`S` `controlPoint`2`endPoint`<br /><br /> - veya -<br /><br /> `s` `controlPoint`2`endPoint`|  
  
|Terim|Açıklama|  
|----------|-----------------|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Eğriyi bitiş tanjantını belirleyen eğrisi denetim noktası.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Noktası çizilen eğri.|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a>Kesintisiz ikinci dereceden Bezier eğrisi komutu  
 Güncel nokta ve belirtilen bitiş noktası arasında ikinci derece Bezier eğrisi oluşturur. Denetim noktası önceki komutun geçerli noktaya göre kontrol noktasının yansıma olduğu varsayılır. Önceki komut yok veya önceki komutu bir ikinci dereceden Bezier eğrisi komutu veya sorunsuz bir ikinci dereceden Bezier eğrisi komutu değilse, denetim noktasının güncel nokta ile çakışık olduğunu ise.  
  
|Sözdizimi|  
|------------|  
|`T` `controlPoint` `endPoint`<br /><br /> - veya -<br /><br /> `t` `controlPoint` `endPoint`|  
  
|Terim|Açıklama|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Denetim noktası eğrinin başlangıç ve eğri tanjantını belirler.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Noktası çizilen eğri.|  
  
### <a name="elliptical-arc-command"></a>Elips yay komutu  
 Güncel nokta ve belirtilen bitiş noktası arasında elips bir yay oluşturur.  
  
|Sözdizimi|  
|------------|  
|`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`<br /><br /> - veya -<br /><br /> `a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`|  
  
|Terim|Açıklama|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=nameWithType><br /><br /> X - ve y-yarıçapı Yayı.|  
|`rotationAngle`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Derece cinsinden elipsin dönmesi.|  
|`isLargeArcFlag`|Yayın açısı 180 derece olacaksa, 1 olarak ayarlayın veya daha büyük; Aksi halde 0 olarak ayarlayın.|  
|`sweepDirectionFlag`|Yayı pozitif açı yönünde çizilir, 1 olarak ayarlayın; Aksi halde 0 olarak ayarlayın.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Noktası Yayı çizilen.|  
  
<a name="closecommand"></a>   
## <a name="the-close-command"></a>Kapat komutu  
 Geçerli şekil sonlandırır ve geçerli noktası şekil başlangıç noktasına bağlanan bir satır oluşturur. Bu komut satırı-arasında bir birleşim (köşe) son kesimi ve Şekil ilk bölümü oluşturur.  
  
|Sözdizimi|  
|------------|  
|`Z`<br /><br /> - veya -<br /><br /> `z`|  

<a name="pointsyntax"></a>   
## <a name="point-syntax"></a>Nokta sözdizimi  
 X ve y-koordinatları noktasının açıklar nerede (0,0) sol üst köşede değil.
  
|Sözdizimi|  
|------------|  
|`x` `,` `y`<br /><br /> - veya -<br /><br /> `x``y`|  
  
|Terim|Açıklama|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Noktanın x-koordinatı.|  
|`y`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Noktanın y-koordinatı.|  
  
<a name="specialvalues"></a>   
## <a name="special-values"></a>Özel değerler  
 Standart bir sayısal değer yerine aşağıdaki özel değerler de kullanabilirsiniz. Bu değerleri büyük/küçük harfe duyarlıdır.  
  
 Sonsuz  
 Temsil eden <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.  
  
 -Sonsuz  
 Temsil eden <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>.  
  
 NaN  
 Temsil eden <xref:System.Double.NaN?displayProperty=nameWithType>.  
  
 Bilimsel gösterim de kullanabilirsiniz. Örneğin, `+1.e17` geçerli bir değer.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.StreamGeometry>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Media.PathFigureCollection>  
 [WPF’de Şekiller ve Temel Çizimlere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Geometriye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/geometries-how-to-topics.md)
