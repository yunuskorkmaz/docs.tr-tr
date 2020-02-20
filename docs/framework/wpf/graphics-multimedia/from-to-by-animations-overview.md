---
title: Öğesinden By Animasyonlarına Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
ms.openlocfilehash: 661c035f55ba1fb550726d75921cd01a72b2eecc
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449016"
---
# <a name="fromtoby-animations-overview"></a>Gelen/İçin/Göre Animasyonlarına Genel Bakış
Bu konu başlığı altında, bağımlılık özelliklerine animasyon uygulamak için From/To/By animasyonlarını kullanma açıklanmaktadır. From/To/By animasyonu iki değer arasında bir geçiş oluşturur.  
  
<a name="prereq"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyonları özellikleriyle ilgili bilgi sahibi olmanız gerekir. Animasyon özelliklerine giriş için [animasyon genel bakış](animation-overview.md)bölümüne bakın.  
  
<a name="whatisanimation"></a>   
## <a name="what-is-a-fromtoby-animation"></a>From/To/By animasyonu nedir?  
 From/To/By animasyonu, başlangıç değeri ile bitiş değeri arasında bir geçiş oluşturan <xref:System.Windows.Media.Animation.AnimationTimeline> türüdür. Geçişin tamamlaması için gereken süre, bu animasyonun <xref:System.Windows.Media.Animation.Timeline.Duration%2A> belirlenir.  
  
 Biçimlendirme ve koddaki <xref:System.Windows.Media.Animation.Storyboard> kullanarak veya koddaki <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemini kullanarak bir özelliğe From/To/By animasyonu uygulayabilirsiniz. Ayrıca, bir <xref:System.Windows.Media.Animation.AnimationClock> oluşturup bir veya daha fazla özelliğe uygulamak için From/To/By animasyonu kullanabilirsiniz. Animasyonları uygulamaya yönelik farklı yöntemler hakkında daha fazla bilgi için bkz. [animasyon tekniklerine genel bakış](property-animation-techniques-overview.md).  
  
 From/To/By animasyonları ikiden fazla hedef değere sahip olamaz. İkiden fazla hedef değere sahip bir animasyon gerekiyorsa, anahtar çerçeve animasyonunu kullanın. Anahtar çerçeve animasyonları, [anahtar çerçeve animasyonlarında genel bakış](key-frame-animations-overview.md)bölümünde açıklanmıştır.  
  
<a name="animation_types"></a>   
## <a name="fromtoby-animation-types"></a>From/To/By animasyon türleri  
 Animasyonlar özellik değerleri oluşturduğundan, farklı özellik türleri için farklı animasyon türleri vardır. Bir öğenin <xref:System.Windows.FrameworkElement.Width%2A> özelliği gibi <xref:System.Double>alan bir özelliğe animasyon uygulamak için <xref:System.Double> değerler üreten bir animasyon kullanın. <xref:System.Windows.Point>alan bir özelliğe animasyon uygulamak için <xref:System.Windows.Point> değerleri üreten bir animasyon kullanın ve bu şekilde devam edin.  
  
 From/To/By animasyon sınıfları <xref:System.Windows.Media.Animation> ad alanına aittir ve aşağıdaki adlandırma kuralını kullanır:  
  
 *\<türü >* `Animation`  
  
 *\<tür >* , sınıfın canlandırır değer türüdür.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], aşağıdaki From/To/By animasyon sınıflarını sağlar.  
  
|Özellik türü|Karşılık gelen/to/by animasyon sınıfı|  
|-------------------|------------------------------------------------|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimation>|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimation>|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16Animation>|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32Animation>|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64Animation>|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimation>|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimation>|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimation>|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimation>|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimation>|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimation>|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimation>|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimation>|  
  
<a name="anim_values"></a>   
## <a name="target-values"></a>Hedef değerler  
 From/To/By animasyonu iki hedef değer arasında bir geçiş oluşturur. Başlangıç değeri (<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliğini kullanarak ayarla) ve bir bitiş değeri (<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliğini kullanarak ayarlayın) belirtilmesi yaygındır. Bununla birlikte, yalnızca bir başlangıç değeri, bir hedef değer veya bir konum değeri de belirtebilirsiniz. Bu durumlarda animasyon, hareketli olmayan özelliğinden eksik hedef değeri edinir. Aşağıdaki listede bir animasyonun hedef değerlerini belirtmek için farklı yollar açıklanmaktadır.  
  
- **Başlangıç değeri**  
  
     Bir animasyonun başlangıç değerini açıkça belirtmek istediğinizde <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliğini kullanın. <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliğini kendi başına veya <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> veya <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliği ile kullanabilirsiniz. Yalnızca <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliğini belirtirseniz, animasyon bu değerden animasyon özelliğinin temel değerine geçiş yapar.  
  
- **Bitiş değeri**  
  
     Animasyonun bitiş değerini belirtmek için, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliğini kullanın. <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliğini tek başına kullanırsanız, animasyon, kendi başlangıç değerini hareketlendirilen özelliğinden veya aynı özelliğe uygulanan başka bir animasyonun çıktısından alır. Animasyonun başlangıç ve bitiş değerlerini açıkça belirtmek için <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliğini <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliğiyle birlikte kullanabilirsiniz.  
  
- **Konum değeri**  
  
     <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliği, animasyon için açık bir başlangıç veya bitiş değeri yerine bir konum belirtmenizi sağlar. Bir animasyonun <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliği, animasyonun bir değeri süresi boyunca ne kadar değiştirdiğine göre belirtir. <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliğini kendi başına veya <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği ile kullanabilirsiniz. Yalnızca <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliğini belirtirseniz, animasyon, Aralık değerini özelliğin temel değerine veya başka bir animasyonun çıktısına ekler.  
  
<a name="examples"></a>   
## <a name="using-fromtoby-values"></a>From/To/By değerlerini kullanma  
 Aşağıdaki bölümlerde <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliklerinin birlikte nasıl kullanılacağı ve ayrı olarak nasıl kullanılacağı açıklanır.  
  
 Bu bölümdeki örneklerde her biri, 10 cihazdan bağımsız piksel yüksekliğinde ve 100 cihazdan bağımsız piksel genişliğinde bir <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.FrameworkElement.Width%2A> özelliğine animasyon uygulamak için From/To/By animasyon türünde bir <xref:System.Windows.Media.Animation.DoubleAnimation>kullanır.  
  
 Her örnek bir <xref:System.Windows.Media.Animation.DoubleAnimation>kullansa da, tüm From/To/By animasyonlarını from, to ve By özellikleri aynı şekilde davranır. Bu örneklerin her biri bir <xref:System.Windows.Media.Animation.Storyboard>kullansa da, diğer yollarla From/To/By animasyonlarını kullanabilirsiniz. Daha fazla bilgi için bkz. [özellik animasyon tekniklerine genel bakış](property-animation-techniques-overview.md).  
  
### <a name="fromto"></a>From/to  
 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> değerlerini birlikte ayarlarsanız, animasyon <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği tarafından belirtilen değerden <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği tarafından belirtilen değere ilerler.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliğini 50 ve <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliğini 300 olarak ayarlar. Sonuç olarak, <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.FrameworkElement.Width%2A> 50 ' den 300 ' e canlandırılır.  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>Alıcı  
 Yalnızca <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliğini ayarladığınızda animasyon, animasyonlu özelliğin temel değerinden veya daha önce aynı özelliğe uygulanan bir oluşturma animasyonunun çıktısından, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği tarafından belirtilen değere ilerler.  
  
 ("Animasyon oluşturma", geçerli animasyon <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> iletim davranışı kullanılarak uygulandığında hala geçerli olan özelliğe uygulanmış bir <xref:System.Windows.Media.Animation.ClockState.Active> veya <xref:System.Windows.Media.Animation.ClockState.Filling> animasyonu anlamına gelir.)  
  
 Aşağıdaki örnek, yalnızca <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliğini 300 olarak ayarlar. Başlangıç değeri belirtilmediğinden <xref:System.Windows.Media.Animation.DoubleAnimation>, başlangıç değeri olarak <xref:System.Windows.FrameworkElement.Width%2A> özelliğinin temel değerini (100) kullanır. <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.FrameworkElement.Width%2A> 100 ' den animasyonun hedef değeri 300 ' den canlandırılır.  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>Tarafından  
 Bir animasyonun yalnızca <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliğini ayarladığınızda animasyon, hareketlendirilen özelliğin temel değerinden veya bir oluşturan animasyonun çıktısından, bu değerin toplamına ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliği tarafından belirtilen değere kadar ilerler.  
  
 Aşağıdaki örnek, yalnızca <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliğini 300 olarak ayarlar. Örnek bir başlangıç değeri belirtmediğinden, <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.FrameworkElement.Width%2A> özelliğinin temel değerini, başlangıç değeri olarak 100 kullanır. Bitiş değeri, 300 değerinin başlangıç değerine, 100:400 ' e animasyon <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> değeri eklenerek belirlenir. Sonuç olarak, <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.FrameworkElement.Width%2A> 100 ' den 400 ' e canlandırılır.  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>Şuradan/bu yana  
 Animasyonun <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliklerini ayarladığınızda, animasyon <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği tarafından belirtilen değerden <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliklerinin toplamı tarafından belirtilen değere ilerlerler.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliğini 50 ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliğini 300 olarak ayarlar. Bitiş değeri, 300 değerinin başlangıç değerine, 50:350 ' e animasyon <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> değeri eklenerek belirlenir. Sonuç olarak, <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.FrameworkElement.Width%2A> 50 ' den 350 ' e canlandırılır.  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>Başlangıç  
 Bir animasyonun yalnızca <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> değerini belirttiğinizde animasyon, <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği tarafından belirtilen değerden, hareketlendirilen özelliğin temel değerine veya bir oluşturma animasyonunun çıkışına kadar ilerler.  
  
 Aşağıdaki örnek, yalnızca <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliğini 50 olarak ayarlar. Bitiş değeri belirtilmediği için <xref:System.Windows.Media.Animation.DoubleAnimation>, <xref:System.Windows.FrameworkElement.Width%2A> özelliğinin temel değerini, 100, onun bitiş değeri olarak kullanır. <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.FrameworkElement.Width%2A> 50 100 ' den <xref:System.Windows.FrameworkElement.Width%2A> özelliğinin temel değerine canlandırılır.  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>To/by  
 Animasyonun hem <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> hem de <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliklerini ayarlarsanız <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliği yok sayılır.  
  
<a name="otheranimationtypes"></a>   
## <a name="other-animation-types"></a>Diğer animasyon türleri  
 From/To/By animasyonları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sağladığı tek animasyon türü değildir: Ayrıca anahtar çerçeve animasyonları ve yol animasyonları sağlar.  
  
- Anahtar çerçeve animasyonu, anahtar çerçeveler kullanılarak tanımlanan herhangi bir sayıda hedef değer üzerinde hareketlenir. Daha fazla bilgi için bkz. [anahtar-çerçeve animasyonlara genel bakış](key-frame-animations-overview.md).  
  
- Yol animasyonu bir <xref:System.Windows.Media.PathGeometry>çıkış değerleri oluşturur. Daha fazla bilgi için bkz. [yol animasyonlara genel bakış](path-animations-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], kendi özel animasyon türlerinizi oluşturmanıza de olanak sağlar. Daha fazla bilgi için bkz. [Özel animasyonlara genel bakış](custom-animations-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Animasyona Genel bakış](animation-overview.md)
- [Görsel Taslaklara Genel Bakış](storyboards-overview.md)
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Yol Animasyonlarına Genel Bakış](path-animations-overview.md)
- [Özel Animasyonlara Genel Bakış](custom-animations-overview.md)
- [From, to ve By animasyon hedefi değerleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)
