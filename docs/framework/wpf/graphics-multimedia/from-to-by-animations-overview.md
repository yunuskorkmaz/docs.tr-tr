---
title: Gelen-için-göre animasyonlarına genel bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
ms.openlocfilehash: 9708a4d06e8a2aa65fb4d3bb959f4699237a2bc6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209157"
---
# <a name="fromtoby-animations-overview"></a>Gelen/İçin/Göre Animasyonlarına Genel Bakış
Bu konuda, gelen/için/göre animasyonlarına bağımlılık özelliklerine animasyon uygulamak için kullanmayı açıklar. From/To/By animasyonu iki değer arasındaki bir geçiş oluşturur.  
  
<a name="prereq"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda anlamak için aşina olmalısınız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyonları özellikleri. Animasyon özelliklerine bir giriş için bkz [animasyona genel bakış](animation-overview.md).  
  
<a name="whatisanimation"></a>   
## <a name="what-is-a-fromtoby-animation"></a>From/To/By animasyon nedir?  
 From/To/By animasyonu türüdür <xref:System.Windows.Media.Animation.AnimationTimeline> bir başlangıç ve bitiş değeri arasında bir geçiş oluşturur. Geçişi tamamlamak için gereken süreyi tarafından belirlenen <xref:System.Windows.Media.Animation.Timeline.Duration%2A> o animasyonun.  
  
 From/To/By uygulayabilirsiniz kullanarak bir özelliğe animasyon bir <xref:System.Windows.Media.Animation.Storyboard> işaretleme ve kod veya kullanarak <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> kodda yöntemi. U animasyon oluşturmak için kullanabilirsiniz bir <xref:System.Windows.Media.Animation.AnimationClock> ve bir veya daha fazla özellikler için geçerlidir. Animasyonlara uygulama için farklı yöntemler hakkında daha fazla bilgi için bkz. [özellik Animasyon Tekniklerine Genel Bakış](property-animation-techniques-overview.md).  
  
 Gelen/için/göre animasyonlarına ikiden fazla hedef değerine sahip olabilir. Anahtar çerçeve animasyonu ikiden fazla hedef değeri olan animasyon gerekiyorsa kullanın. Anahtar-çerçeve animasyonlara açıklanan [anahtar-çerçeve animasyonlara genel bakış](key-frame-animations-overview.md).  
  
<a name="animation_types"></a>   
## <a name="fromtoby-animation-types"></a>From/To/By animasyon türü  
 Özellik değerlerini animasyonlar oluşturması nedeniyle farklı özellik türleri için farklı animasyon türü vardır. Alan özelliği oynatmak bir <xref:System.Double>, gibi <xref:System.Windows.FrameworkElement.Width%2A> bir öğe özelliğini kullanın üreten bir animasyon <xref:System.Double> değerleri. Alan özelliği oynatmak bir <xref:System.Windows.Point>, üreten bir animasyon kullanın <xref:System.Windows.Point> değerleri ve benzeri.  
  
 From/To/By animasyon sınıfları ait <xref:System.Windows.Media.Animation> ad alanı ve şu adlandırma kuralını kullanır:  
  
 *\<türü >* `Animation`  
  
 Burada  *\<türü >* sınıfı canlandırır değer türüdür.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Aşağıdaki From/To/By animasyonu sınıflar sağlar.  
  
|Özellik türü|Karşılık gelen From/To/By animasyonu sınıfı|  
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
## <a name="target-values"></a>Hedef değerleri  
 From/To/By animasyonu iki hedef değer arasında bir geçiş oluşturur. Başlangıç değerini belirtmek yaygındır (kullanarak ayarlamak <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği) ve bitiş değeri (kullanarak ayarlamak <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği). Ancak, yalnızca bir başlangıç değeri, bir hedef değer veya bir uzaklık değeri de belirtebilirsiniz. Bu gibi durumlarda animasyon eksik hedef değer animasyon uygulanan özelliğinden alır. Aşağıdaki listede, animasyon hedef değerleri belirlemek için farklı yollar açıklanmaktadır.  
  
-   **Başlangıç değeri**  
  
     Kullanım <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği açıkça bir animasyon başlangıç değerine belirtmek istediğinizde. Kullanabileceğiniz <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliğini tek başına veya birlikte <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> veya <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliği. Yalnızca belirtirseniz <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özellik, animasyon geçişler bu değeri temel değerine özelliğin.  
  
-   **Bitiş değeri**  
  
     Animasyonun bitiş değeri belirtmek için kullanın, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği. Kullanırsanız <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği kendisi tarafından animasyon alır başlangıç değerine animasyon uygulanan bir özellik veya aynı özelliğe uygulanan başka bir animasyon çıktısı. Kullanabileceğiniz <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği ile birlikte <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> başlangıç ve bitiş değerlerinin animasyon için açıkça belirtmek için özellik.  
  
-   **Uzaklık değeri**  
  
     <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Özelliği, bir açık başlangıç veya bitiş değeri animasyonun yerine bir uzaklık belirtmenizi sağlar. <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Animasyonun özellik belirtir tarafından ne kadar animasyon süresi boyunca bir değer değiştirir. Kullanabileceğiniz <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliğini tek başına veya birlikte <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği. Yalnızca belirtirseniz <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özellik, animasyon özelliği için taban değerini veya başka bir animasyon çıktısı için uzaklık değeri ekler.  
  
<a name="examples"></a>   
## <a name="using-fromtoby-values"></a>Gelen/için/göre değerleri kullanarak  
 Aşağıdaki bölümlerde nasıl kullanılacağını <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özellikleri birlikte veya ayrı ayrı.  
  
 Her kullanım bölümdeki Bu örneklerde bir <xref:System.Windows.Media.Animation.DoubleAnimation>, animasyon uygulamak için From/To/By animasyonu, bir tür olduğu <xref:System.Windows.FrameworkElement.Width%2A> özelliği bir <xref:System.Windows.Shapes.Rectangle> diğer bir deyişle, 10 cihaz bağımsız piksel yüksekliğinde ve 100 cihaz bağımsız piksel genişliğinde.  
  
 Her örnek kullansa da bir <xref:System.Windows.Media.Animation.DoubleAnimation>, ve tüm From/To/By özellikleri tarafından animasyonları aynı şekilde davranır. Bu örneklerin her kullansa da bir <xref:System.Windows.Media.Animation.Storyboard>, gelen/için/göre animasyonlarına başka yöntemlerle de kullanabilirsiniz. Daha fazla bilgi için [özellik Animasyon Tekniklerine Genel Bakış](property-animation-techniques-overview.md).  
  
### <a name="fromto"></a>/  
 Ayarladığınızda <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> birlikte tarafından belirtilen değere animasyon ilerler değerleri <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği tarafından belirtilen değere <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği.  
  
 Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği <xref:System.Windows.Media.Animation.DoubleAnimation> 50'ye ve kendi <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 300 özelliği. Sonuç olarak, <xref:System.Windows.FrameworkElement.Width%2A> , <xref:System.Windows.Shapes.Rectangle> 50'den 300 bir animasyon görünür.  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>Bitiş  
 Yalnızca ayarlandığında <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özellik, animasyon ilerlemesi için taban değerini animasyonlu özelliği veya çıkış için aynı özelliği tarafından belirtilen değeri daha önce uygulanan bir animasyonun <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özellik.  
  
 ("Animasyon oluşturma" başvurduğu bir <xref:System.Windows.Media.Animation.ClockState.Active> veya <xref:System.Windows.Media.Animation.ClockState.Filling> geçerli animasyon kullanarak uygulandığında hala etkin olan aynı özelliğe daha önce uygulanan bir animasyon <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> iletim davranışı.)  
  
 Aşağıdaki örnek yalnızca ayarlar <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği <xref:System.Windows.Media.Animation.DoubleAnimation> 300. Başlangıç değeri belirtilmiş olduğundan <xref:System.Windows.Media.Animation.DoubleAnimation> taban değerini (100) kullanan <xref:System.Windows.FrameworkElement.Width%2A> özelliği olarak başlangıç değeri. <xref:System.Windows.FrameworkElement.Width%2A> , <xref:System.Windows.Shapes.Rectangle> 100'den 300 animasyonun hedef değer için bir animasyon görünür.  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>Tarafından  
 Yalnızca ayarlandığında <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> animasyonun özellik, animasyon ilerler animasyon uygulanan bir özellik için taban değerini veya animasyonun toplanacak değeri tarafından belirtilen değeri ve çıktıya <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özellik.  
  
 Aşağıdaki örnek yalnızca ayarlar <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliği <xref:System.Windows.Media.Animation.DoubleAnimation> 300. Örnek bir başlangıç değeri belirtmediğinden <xref:System.Windows.Media.Animation.DoubleAnimation> için taban değerini kullanan <xref:System.Windows.FrameworkElement.Width%2A> özelliği, 100 ' Başlangıç değeri olarak. Bitiş değeri eklenerek belirlenir <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> animasyon başlangıç değerine, 100 300 değeri: 400. Sonuç olarak, <xref:System.Windows.FrameworkElement.Width%2A> , <xref:System.Windows.Shapes.Rectangle> 100'den 400'e bir animasyon görünür.  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>Gelen/göre  
 Ayarladığınızda <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> animasyon özelliklerini, tarafından belirtilen değere animasyon ilerler <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> toplamı tarafından belirtilen değere özelliği <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özellikleri.  
  
 Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği <xref:System.Windows.Media.Animation.DoubleAnimation> 50'ye ve kendi <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 300 özelliği. Bitiş değeri eklenerek belirlenir <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> animasyon başlangıç değerine, 50 300 değeri: 350. Sonuç olarak, <xref:System.Windows.FrameworkElement.Width%2A> , <xref:System.Windows.Shapes.Rectangle> 50'den 350 için bir animasyon görünür.  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>Başlangıç  
 Yalnızca belirttiğinizde <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> , animasyon değeri tarafından belirtilen değere animasyon ilerler <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliğini, animasyon uygulanan bir özellik için taban değerini veya animasyonun çıktısı.  
  
 Aşağıdaki örnek yalnızca ayarlar <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği <xref:System.Windows.Media.Animation.DoubleAnimation> 50 '. Hiçbir bitiş değeri belirtilmiş olduğundan <xref:System.Windows.Media.Animation.DoubleAnimation> için taban değerini kullanır <xref:System.Windows.FrameworkElement.Width%2A> özelliği, 100 olarak bitiş değeri. <xref:System.Windows.FrameworkElement.Width%2A> , <xref:System.Windows.Shapes.Rectangle> 50'den taban değerini animasyonlu <xref:System.Windows.FrameworkElement.Width%2A> özelliği, 100.  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>İçin/göre  
 Her ikisi de ayarlarsanız <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> animasyon özelliklerini <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliği yok sayılır.  
  
<a name="otheranimationtypes"></a>   
## <a name="other-animation-types"></a>Diğer animasyon türü  
 Gelen/için/göre animasyonlarına animasyon türü değildir, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sağlar: anahtar-çerçeve animasyonlara ve yol animasyonları da sağlar.  
  
-   Anahtar çerçeve animasyon hedef değerleri, açıklanan anahtar çerçeveler kullanarak herhangi bir sayıda canlandırır. Daha fazla bilgi için [anahtar-çerçeve animasyonlara genel bakış](key-frame-animations-overview.md).  
  
-   Yol animasyonu çıkış değerlerini oluşturur bir <xref:System.Windows.Media.PathGeometry>. Daha fazla bilgi için [yol animasyonlarına genel bakış](path-animations-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ayrıca, kendi özel animasyon türleri oluşturmanıza olanak sağlar. Daha fazla bilgi için [özel animasyonlara genel bakış](custom-animations-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Animasyona Genel bakış](animation-overview.md)
- [Görsel Taslaklara Genel Bakış](storyboards-overview.md)
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Yol Animasyonlarına Genel Bakış](path-animations-overview.md)
- [Özel Animasyonlara Genel Bakış](custom-animations-overview.md)
- [Gelen, için ve göre animasyon hedef değerleri örneği](https://go.microsoft.com/fwlink/?LinkID=159988)
