---
title: Yol Biçimlendirme Sözdizimi
description: Windows Presentation Foundation (WPF) ' de Compact Path geometrileri belirtmek için kullanabileceğiniz güçlü ve karmaşık mini dil hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- attribute usage in XAML [WPF]
- XAML [WPF], attribute usage
- graphics [WPF], PathGeometry class
- XAML [WPF], object element usage
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
ms.openlocfilehash: 6d2778522b622f0b0dcb59673e793a6d772a4b4f
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853654"
---
# <a name="path-markup-syntax"></a>Yol Biçimlendirme Sözdizimi
Yollar [şekil ve WPF genel bakış bölümünde](shapes-and-basic-drawing-in-wpf-overview.md) ele alınmıştır. ancak, bu [konuda, kullanarak](geometry-overview.md)yol geometrileri belirlemek için kullanabileceğiniz güçlü ve karmaşık mini dil ayrıntılı olarak açıklanmaktadır [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] .  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için nesnelerin temel özellikleri hakkında bilgi sahibi olmanız gerekir <xref:System.Windows.Media.Geometry> . Daha fazla bilgi için bkz. [geometriye genel bakış](geometry-overview.md).  
  
<a name="abouthisdocument"></a>
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a>StreamGeometry ve PathFigureCollection mini dilleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]geometrik yolları açıklamak için mini diller sağlayan iki sınıf sağlar: <xref:System.Windows.Media.StreamGeometry> ve <xref:System.Windows.Media.PathFigureCollection> .  
  
- <xref:System.Windows.Media.StreamGeometry>Türünün özelliği <xref:System.Windows.Media.Geometry> veya bir <xref:System.Windows.UIElement.Clip%2A> <xref:System.Windows.UIElement> <xref:System.Windows.Shapes.Path.Data%2A> öğenin özelliği gibi bir özelliği ayarlarken mini dili kullanırsınız <xref:System.Windows.Shapes.Path> . Aşağıdaki örnek, oluşturmak için öznitelik sözdizimini kullanır <xref:System.Windows.Media.StreamGeometry> .  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
- <xref:System.Windows.Media.PathFigureCollection>Bir öğesinin özelliğini ayarlarken mini dili kullanın <xref:System.Windows.Media.PathGeometry.Figures%2A> <xref:System.Windows.Media.PathGeometry> . Aşağıdaki örnek bir için oluşturmak üzere bir öznitelik söz dizimini kullanır <xref:System.Windows.Media.PathFigureCollection> <xref:System.Windows.Media.PathGeometry> .  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 Yukarıdaki örneklerden görebileceğiniz gibi, iki mini dil de çok benzerdir. ' İ kullanabileceğiniz herhangi bir durumda, <xref:System.Windows.Media.PathGeometry> hangisini kullanmak zorunda olacak şekilde kullanmak her zaman mümkündür <xref:System.Windows.Media.StreamGeometry> . Yolu oluşturduktan <xref:System.Windows.Media.StreamGeometry> sonra değiştirmeniz gerekmiyorsa bir kullanın; <xref:System.Windows.Media.PathGeometry> yolu değiştirmeniz gerekiyorsa bir kullanın.  
  
 Ve nesneleri arasındaki farklılıklar hakkında daha fazla bilgi için <xref:System.Windows.Media.PathGeometry> <xref:System.Windows.Media.StreamGeometry> bkz. [geometriye genel bakış](geometry-overview.md).  
  
### <a name="a-note-about-white-space"></a>Boşluk hakkında bir göz  
 Kısaltma için, izleyen söz dizimi bölümlerinde tek bir boşluk gösterilir, ancak tek bir boşluk gösterildiğinde birden çok boşluk da kabul edilebilir.  
  
 İki sayının gerçekten virgül veya boşluk ile ayrılması gerekmez, ancak bu yalnızca elde edilen dize belirsiz olduğunda yapılabilir. Örneğin, `2..3` aslında iki sayı: "2." Ve ". 3". Benzer şekilde, `2-3` "2" ve "-3". Boşluklar, komutlardan önce veya sonra gerekli değildir.  
  
### <a name="syntax"></a>Syntax  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]Bir için öznitelik kullanım sözdizimi, <xref:System.Windows.Media.StreamGeometry> isteğe bağlı bir <xref:System.Windows.Media.FillRule> değerden ve bir veya daha fazla şekil açıklamalarından oluşur.  
  
|StreamGeometry XAML öznitelik kullanımı|  
|-----------------------------------------|  
|`<`*Object* *özelliği* `="` [ `fillRule` ] `figureDescription` [ `figureDescription` ] *`" ... />`|  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]İçin öznitelik kullanım sözdizimi bir <xref:System.Windows.Media.PathFigureCollection> veya daha fazla şekil açıklamalarından oluşur.  
  
|PathFigureCollection XAML öznitelik kullanımı|  
|-----------------------------------------------|  
|`<`*Object* *özelliği* `="` `figureDescription` [ `figureDescription` ] *`" ... />`|  
  
|Terim|Description|  
|----------|-----------------|  
|*fillRule*|<xref:System.Windows.Media.FillRule?displayProperty=nameWithType><br /><br /> ' In veya ' nin kullanıp kullanmadığını belirtir <xref:System.Windows.Media.StreamGeometry> <xref:System.Windows.Media.FillRule.EvenOdd> <xref:System.Windows.Media.FillRule.Nonzero> <xref:System.Windows.Media.PathGeometry.FillRule%2A> .<br /><br /> -   `F0`<xref:System.Windows.Media.FillRule.EvenOdd>Fill kuralını belirtir.<br />-   `F1`<xref:System.Windows.Media.FillRule.Nonzero>Fill kuralını belirtir.<br /><br /> Bu komutu atlarsanız, alt yol varsayılan davranışı kullanır <xref:System.Windows.Media.FillRule.EvenOdd> . Bu komutu belirtirseniz, önce yerleştirmeniz gerekir.|  
|*figureDescription*|Bir Move komutundan, çizim komutlarından ve isteğe bağlı bir kapatma komutundan oluşan bir şekil.<br /><br /> `moveCommand` `drawCommands`  `[` `closeCommand` `]`|  
|*moveCommand*|Şeklin başlangıç noktasını belirten bir Move komutu. [Taşıma komut](#themovecommand) bölümüne bakın.|  
|*drawCommands*|Şekil içeriğini tanımlayan bir veya daha fazla çizim komutu. [Çizim komutları](#drawcommands) bölümüne bakın.|  
|*closeCommand*|Şekli kapatan isteğe bağlı bir kapatma komutu. [Kapat komut](#closecommand) bölümüne bakın.|  
  
<a name="themovecommand"></a>
## <a name="move-command"></a>Move komutu  
 Yeni bir şeklin başlangıç noktasını belirtir.  
  
|Syntax|  
|------------|  
|`M`*StartPoint*<br /><br /> - veya -<br /><br /> `m`*StartPoint*|  
  
|Terim|Description|  
|----------|-----------------|  
|*startPoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Yeni bir şeklin başlangıç noktası.|  
  
 Büyük harf `M` `startPoint` , mutlak bir değer olduğunu gösterir; küçük harf, bir `m` `startPoint` önceki noktaya bir konum olduğunu veya yoksa (0, 0) olduğunu gösterir. Move komutundan sonra birden çok noktayı listeseniz, Line komutunu belirtseniz de bu noktalara bir çizgi çizilir.  
  
<a name="drawcommands"></a>
## <a name="draw-commands"></a>Çiz komutları  
 Çizim komutu birkaç şekil komutundan oluşabilir. Aşağıdaki şekil komutları kullanılabilir: çizgi, yatay çizgi, dikey çizgi, üçüncü dereceden Bezier eğrisi, karesel Bezier eğrisi, pürüzsüz üçüncü dereceden Bezier eğrisi, yumuşak ikinci dereceden Bezier eğrisi ve elips yay.  
  
 Her komutu bir büyük harf veya küçük harf kullanarak girersiniz: büyük harfler mutlak değerleri gösterir ve küçük harfler göreli değerleri gösterir: bu segmentin denetim noktaları, önceki örneğin bitiş noktasına göre yapılır. Aynı türde birden fazla komut sıralı olarak girildiğinde, yinelenen komut girişini atlayabilirsiniz; Örneğin, `L 100,200 300,400` öğesine eşdeğerdir `L 100,200 L 300,400` . Aşağıdaki tabloda, **Taşı** ve **Çiz** komutları açıklanmaktadır.  
  
### <a name="line-command"></a>Line komutu  
 Geçerli nokta ile belirtilen bitiş noktası arasında düz bir çizgi oluşturur. `l 20 30`ve `L 20,30` geçerli **satır** komutlarının örnekleridir.  
  
|Syntax|  
|------------|  
|`L`*uç nokta*<br /><br /> - veya -<br /><br /> `l`*uç nokta*|  
  
|Terim|Description|  
|----------|-----------------|  
|*Bkz*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Çizginin bitiş noktası.|  

Büyük harf `L` `endPoint` , mutlak bir değer olduğunu gösterir; küçük harf, bir `l` `endPoint` önceki noktaya bir konum olduğunu veya yoksa (0, 0) olduğunu gösterir.

### <a name="horizontal-line-command"></a>Yatay çizgi komutu  
 Geçerli nokta ile belirtilen x koordinatı arasında yatay bir çizgi oluşturur. `H 90`, geçerli bir yatay çizgi komutuna bir örnektir.

|Syntax|  
|------------|  
|`H`  *sayı*<br /><br /> - veya -<br /><br /> `h`  *sayı*|  
  
|Terim|Description|  
|----------|-----------------|  
|*x*|<xref:System.Double?displayProperty=nameWithType><br /><br /> Çizginin bitiş noktasının x koordinatı.|  
  
Büyük harf `H` `x` , mutlak bir değer olduğunu gösterir; küçük harf, bir `h` `x` önceki noktaya bir konum olduğunu veya yoksa (0, 0) olduğunu gösterir.
  
### <a name="vertical-line-command"></a>Dikey çizgi komutu  
 Geçerli nokta ile belirtilen y koordinatı arasında dikey bir çizgi oluşturur. `v 90`, geçerli bir dikey çizgi komutuna bir örnektir.

|Syntax|  
|------------|  
|`V`  *Iz*<br /><br /> - veya -<br /><br /> `v`  *Iz*|  
  
|Terim|Description|  
|----------|-----------------|  
|*Iz*|<xref:System.Double?displayProperty=nameWithType><br /><br /> Çizginin bitiş noktasının y koordinatı.|  

Büyük harf `V` `y` , mutlak bir değer olduğunu gösterir; küçük harf, bir `v` `y` önceki noktaya bir konum olduğunu veya yoksa (0, 0) olduğunu gösterir.  

### <a name="cubic-bezier-curve-command"></a>Üçüncü dereceden Bezier eğrisi komutu  
 Belirtilen iki denetim noktasını ( `controlPoint` 1 ve 2) kullanarak, geçerli nokta ile belirtilen bitiş noktası arasında üçüncü dereceden Bezier eğrisi oluşturur `controlPoint` . `C 100,200 200,400 300,200`, geçerli bir eğri komutuna örnektir.  
  
|Syntax|  
|------------|  
|`C``controlPoint`1 `controlPoint` 2`endPoint`<br /><br /> - veya -<br /><br /> `c``controlPoint`1 `controlPoint` 2`endPoint`|  
  
|Terim|Description|  
|----------|-----------------|  
|`controlPoint`1|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Eğrinin başlangıç tanjantını belirleyen eğrinin ilk denetim noktası.|  
|`controlPoint`iki|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Eğrinin sonundaki tanjantı belirleyen, eğrinin ikinci denetim noktası.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Eğrinin çizildiği nokta.|  
  
### <a name="quadratic-bezier-curve-command"></a>İkinci dereceden Bezier eğrisi komutu  
 Belirtilen denetim noktasını () kullanarak, geçerli nokta ile belirtilen bitiş noktası arasında ikinci dereceden Bezier eğrisi oluşturur `controlPoint` . `q 100,200 300,200`, geçerli bir ikinci dereceden Bezier eğrisi komutuna bir örnektir.  
  
|Syntax|  
|------------|  
|`Q` `controlPoint` `endPoint`<br /><br /> - veya -<br /><br /> `q` `controlPoint` `endPoint`|  
  
|Terim|Description|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Eğrinin başındaki ve sonundaki tanjantları belirleyen eğrinin denetim noktası.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Eğrinin çizildiği nokta.|  
  
### <a name="smooth-cubic-bezier-curve-command"></a>Pürüzsüz üçüncü dereceden Bezier eğrisi komutu  
 Geçerli nokta ile belirtilen bitiş noktası arasında üçüncü dereceden Bezier eğrisi oluşturur. İlk denetim noktasının, geçerli noktaya göre önceki komutun ikinci denetim noktasının yansıması olduğu varsayılır. Önceki komut yoksa veya önceki komut üçüncü dereceden Bezier eğrisi komutu ya da yumuşak bir üçüncü dereceden Bezier eğrisi komutu değilse, ilk denetim noktasının geçerli nokta ile coıncident olduğunu varsayın. Eğrinin sonundaki denetim noktası olan ikinci denetim noktası 2 ile belirtilir `controlPoint` . Örneğin, `S 100,200 200,300` geçerli bir düz üçüncü dereceden Bezier eğrisi komutu.  
  
|Syntax|  
|------------|  
|`S` `controlPoint`2`endPoint`<br /><br /> - veya -<br /><br /> `s` `controlPoint`2`endPoint`|  
  
|Terim|Description|  
|----------|-----------------|  
|`controlPoint`iki|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Eğrinin bitiş tanjantını belirleyen, eğrinin denetim noktası.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Eğrinin çizildiği nokta.|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a>Yumuşak ikinci dereceden Bezier eğrisi komutu  
 Geçerli nokta ile belirtilen bitiş noktası arasında ikinci dereceden Bezier eğrisi oluşturur. Denetim noktasının, geçerli noktaya göre önceki komutun denetim noktasının yansıması olduğu varsayılır. Önceki komut yoksa veya önceki komut ikinci dereceden Bezier eğrisi komutu veya düzgün bir ikinci dereceden Bezier eğrisi komutu değilse, denetim noktası geçerli noktaya sahip coıncident olur.  
  
|Syntax|  
|------------|  
|`T` `controlPoint` `endPoint`<br /><br /> - veya -<br /><br /> `t` `controlPoint` `endPoint`|  
  
|Terim|Description|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Eğrinin başlangıç ve tanjantını belirleyen, eğrinin denetim noktası.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Eğrinin çizildiği nokta.|  
  
### <a name="elliptical-arc-command"></a>Elips yay komutu  
 Geçerli nokta ile belirtilen bitiş noktası arasında elips bir yay oluşturur.  
  
|Syntax|  
|------------|  
|`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`<br /><br /> - veya -<br /><br /> `a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`|  
  
|Terim|Description|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=nameWithType><br /><br /> Yayı x ve y-yarıçapı.|  
|`rotationAngle`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Elipsin derece cinsinden dönüşü.|  
|`isLargeArcFlag`|Yay açısı 180 derece veya daha fazlaysa, 1 olarak ayarlanır; Aksi takdirde, 0 olarak ayarlayın.|  
|`sweepDirectionFlag`|Yay pozitif açılı bir yönde çizildiyse, 1 olarak ayarlayın; Aksi takdirde, 0 olarak ayarlayın.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Yay çizildiği nokta.|  
  
<a name="closecommand"></a>
## <a name="the-close-command"></a>Close komutu  
 Geçerli şekli sonlandırır ve geçerli noktayı şeklin başlangıç noktasına bağlayan bir çizgi oluşturur. Bu komut, son segment ile şeklin ilk segmenti arasında bir çizgi birleşimi (köşe) oluşturur.  
  
|Syntax|  
|------------|  
|`Z`<br /><br /> - veya -<br /><br /> `z`|  

<a name="pointsyntax"></a>
## <a name="point-syntax"></a>Nokta sözdizimi  
 (0, 0) sol üst köşenin bulunduğu bir noktanın x ve y koordinatlarını açıklar.
  
|Syntax|  
|------------|  
|`x` `,` `y`<br /><br /> - veya -<br /><br /> `x` `y`|  
  
|Terim|Description|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Noktanın x koordinatı.|  
|`y`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Noktanın y koordinatı.|  
  
<a name="specialvalues"></a>
## <a name="special-values"></a>Özel değerler  
 Standart bir sayısal değer yerine aşağıdaki özel değerleri de kullanabilirsiniz. Bu değerler büyük/küçük harfe duyarlıdır.  
  
 Sonsuz  
 Temsil eder <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> .  
  
 -Sonsuzluk  
 Temsil eder <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> .  
  
 NaN  
 Temsil eder <xref:System.Double.NaN?displayProperty=nameWithType> .  
  
 Bilimsel gösterim de kullanabilirsiniz. Örneğin, `+1.e17` geçerli bir değerdir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.PathFigureCollection>
- [WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler](shapes-and-basic-drawing-in-wpf-overview.md)
- [Geometriye Genel Bakış](geometry-overview.md)
- [Nasıl Yapılır Konuları](geometries-how-to-topics.md)
