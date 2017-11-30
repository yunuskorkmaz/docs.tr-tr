---
title: "From-To-By animasyonları genel bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f5eba773a290f1100fcea411919c5c16558e01ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="fromtoby-animations-overview"></a>Gelen/İçin/Göre Animasyonlarına Genel Bakış
Bu konuda From/To/By animasyonları bağımlılık özellikleri animasyon için nasıl kullanılacağını açıklar. From/To/By animasyon iki değer arasında bir geçiş oluşturur.  
  
<a name="prereq"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için aşina olmalısınız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyonları özellikleri. Animasyon özelliklerine giriş için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="whatisanimation"></a>   
## <a name="what-is-a-fromtoby-animation"></a>From/To/By animasyon nedir?  
 From/To/By animasyon türüdür <xref:System.Windows.Media.Animation.AnimationTimeline> bir başlangıç ve bitiş değeri arasında bir geçiş oluşturur. Geçişi tamamlamak için gereken süre miktarı tarafından belirlenen <xref:System.Windows.Media.Animation.Timeline.Duration%2A> o animasyonun.  
  
 From/To/By uygulayabilirsiniz animasyon kullanarak bir özellik için bir <xref:System.Windows.Media.Animation.Storyboard> biçimlendirme ve kodun veya kullanarak <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> kodda yöntemi. U animasyon oluşturmak için kullanabilir bir <xref:System.Windows.Media.Animation.AnimationClock> ve bir veya daha fazla özellikleri için geçerlidir. Animasyonları uygulamak için farklı yöntemler hakkında daha fazla bilgi için bkz: [özellik Animasyon Tekniklerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
 From/To/By animasyonları ikiden fazla hedef değerlere sahip olabilir. İkiden fazla hedef değerine sahip bir animasyon gerekiyorsa, bir anahtar çerçeve animasyonu kullanın. Anahtar çerçeve animasyonları açıklanan [anahtar çerçeve animasyonları genel bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
<a name="animation_types"></a>   
## <a name="fromtoby-animation-types"></a>From/To/By animasyon türleri  
 Animasyon özellik değerleri oluşturması nedeniyle farklı özellik türleri için farklı animasyon türü vardır. Alan bir özelliği animasyon uygulamak için bir <xref:System.Double>, gibi <xref:System.Windows.FrameworkElement.Width%2A> bir öğenin özelliğini kullanın üreten bir animasyon <xref:System.Double> değerleri. Alan bir özelliği animasyon uygulamak için bir <xref:System.Windows.Point>, üreten bir animasyon kullanın <xref:System.Windows.Point> değerleri ve benzeri.  
  
 From/To/By animasyon sınıfları ait <xref:System.Windows.Media.Animation> ad alanı ve aşağıdaki adlandırma kuralını kullanın:  
  
 *\<Tür >*`Animation`  
  
 Burada  *\<türü >* sınıfı canlandırır değer türüdür.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Aşağıdaki From/To/By animasyon sınıfları sağlar.  
  
|Özellik türü|Karşılık gelen From/To/By animasyon sınıfı|  
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
 From/To/By animasyon iki hedef değer arasında bir geçiş oluşturur. Başlangıç değerini belirtmek için ortak olan (kullanarak ayarlamak <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği) ve bitiş değeri (kullanarak ayarlamak <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği). Ancak, yalnızca başlangıç değeri, bir hedef değer veya bir uzaklık değeri de belirtebilirsiniz. Bu durumlarda animasyon animasyon eklenir özelliğinden eksik hedef değeri alır. Aşağıdaki listede, animasyonun hedef değerleri belirtmek için farklı yöntemler açıklanmaktadır.  
  
-   **Başlangıç değeri**  
  
     Kullanım <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği açıkça bir animasyon başlangıç değerini belirtmek istediğinizde. Kullanabileceğiniz <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliğini tek başına veya birlikte <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> veya <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliği. Yalnızca belirtirseniz <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özellik, animasyon geçişleri bu değerden temel değerine animasyonlu özelliğin.  
  
-   **Bitiş değeri**  
  
     Animasyonun bitiş değerini belirtmek için kullanın, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği. Kullanırsanız <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği kendisi tarafından animasyon alır başlangıç değeri hareketli özellikten veya aynı özelliğe uygulanan başka bir animasyon çıktısı. Kullanabileceğiniz <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği ile birlikte <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> başlangıç ve bitiş değerlerinin animasyonun açıkça belirtmek için özellik.  
  
-   **Uzaklık değeri**  
  
     <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Özelliği bir açık başlangıç veya bitiş değeri animasyonun yerine bir uzaklık belirtmenize olanak sağlar. <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Animasyonun özellik belirtir ne kadar animasyonun süresi boyunca bir değer değiştirir. Kullanabileceğiniz <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliğini tek başına veya birlikte <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği. Yalnızca belirtirseniz <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özellik, animasyon özelliğin temel değerini veya başka bir animasyon çıktısını uzaklık değeri ekler.  
  
<a name="examples"></a>   
## <a name="using-fromtoby-values"></a>From/To/By değerlerini kullanma  
 Aşağıdaki bölümlerde nasıl kullanılacağını <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özellikleri birlikte veya ayrı olarak.  
  
 Her kullanım örnekleri bu bölüm bir <xref:System.Windows.Media.Animation.DoubleAnimation>, animasyon için From/To/By animasyon türündeki <xref:System.Windows.FrameworkElement.Width%2A> özelliği bir <xref:System.Windows.Shapes.Rectangle> yani yüksek 10 aygıttan bağımsız piksel ve 100 aygıttan bağımsız piksel genişliğinde.  
  
 Her örneğin kullanıyor olsa da bir <xref:System.Windows.Media.Animation.DoubleAnimation>,, için ve tüm From/To/By özelliklerini tarafından animasyonları aynı şekilde davranır. Bu örneklerin herbiri kullanıyor olsa da bir <xref:System.Windows.Media.Animation.Storyboard>, From/To/By animasyonları diğer yollarla kullanabilirsiniz. Daha fazla bilgi için bkz: [özellik Animasyon Tekniklerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
### <a name="fromto"></a>Başlangıç/bitiş  
 Ayarladığınızda <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> birlikte tarafından belirtilen değeri animasyon ilerler değerleri <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği tarafından belirtilen değere <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği.  
  
 Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği <xref:System.Windows.Media.Animation.DoubleAnimation> 50'ye ve kendi <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 300 özelliği. Sonuç olarak, <xref:System.Windows.FrameworkElement.Width%2A> , <xref:System.Windows.Shapes.Rectangle> 50'den 300 animasyonlu.  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>Bitiş  
 Yalnızca ayarlandığında <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özellik, animasyon ilerler animasyonlu özelliğin temel değerinden veya aynı özelliğe tarafından belirtilen değere daha önce uygulanan bir animasyonun çıktısından <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özellik.  
  
 ("Animasyon oluşturma" başvurduğu bir <xref:System.Windows.Media.Animation.ClockState.Active> veya <xref:System.Windows.Media.Animation.ClockState.Filling> geçerli animasyon kullanarak uygulandığında hala etkin olan aynı özelliğe daha önce uygulanan bir animasyon <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> iletim davranışı.)  
  
 Aşağıdaki örnekte yalnızca ayarlar <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği <xref:System.Windows.Media.Animation.DoubleAnimation> 300. Başlangıç değeri belirtilmiş olduğundan <xref:System.Windows.Media.Animation.DoubleAnimation> temel değerini (100) kullanan <xref:System.Windows.FrameworkElement.Width%2A> özellik başlangıç değeri olarak. <xref:System.Windows.FrameworkElement.Width%2A> , <xref:System.Windows.Shapes.Rectangle> 100'den animasyonun hedef değerine 300 animasyonlu.  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>Tarafından  
 Yalnızca ayarlandığında <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> animasyonun özellik, animasyon ilerler hareketli özelliğin temel değerini veya toplamı bu değeri ve tarafından belirtilen değer, animasyonun çıktısından çıktısını <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özellik.  
  
 Aşağıdaki örnekte yalnızca ayarlar <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliği <xref:System.Windows.Media.Animation.DoubleAnimation> 300. Örnek bir başlangıç değeri belirtmediğinden <xref:System.Windows.Media.Animation.DoubleAnimation> taban değerini kullanır <xref:System.Windows.FrameworkElement.Width%2A> özelliği, 100, başlangıç değeri olarak. Bitiş değeri eklenerek belirlenir <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 300'ü başlangıç değeri 100:400 animasyon değeri. Sonuç olarak, <xref:System.Windows.FrameworkElement.Width%2A> , <xref:System.Windows.Shapes.Rectangle> 100'den 400 animasyonlu.  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>Gelen/tarafından  
 Ayarladığınızda <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> animasyon özelliklerini, tarafından belirtilen değeri animasyon ilerler <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> toplamı tarafından belirtilen değere özelliği <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özellikleri.  
  
 Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği <xref:System.Windows.Media.Animation.DoubleAnimation> 50'ye ve kendi <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 300 özelliği. Bitiş değeri eklenerek belirlenir <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 300'ü başlangıç değeri 50:350 animasyon değeri. Sonuç olarak, <xref:System.Windows.FrameworkElement.Width%2A> , <xref:System.Windows.Shapes.Rectangle> 50'den 350 için animasyonlu.  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>Başlangıç  
 Yalnızca belirttiğinizde <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> animasyon ilerler tarafından belirtilen değer, animasyonun değeri <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliğini, hareketli özelliğin temel değerini veya animasyonun çıktısından çıktısı.  
  
 Aşağıdaki örnekte yalnızca ayarlar <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği <xref:System.Windows.Media.Animation.DoubleAnimation> 50. Bitiş değeri belirtilmiş olduğundan <xref:System.Windows.Media.Animation.DoubleAnimation> taban değerini kullanır <xref:System.Windows.FrameworkElement.Width%2A> özelliği, 100 olarak bitiş değeri. <xref:System.Windows.FrameworkElement.Width%2A> , <xref:System.Windows.Shapes.Rectangle> 50'den temel değerini animasyonlu <xref:System.Windows.FrameworkElement.Width%2A> özelliği, 100.  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>/ Tarafından  
 Her ikisini de ayarlarsanız <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> bir animasyon özelliklerini <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliği yoksayılır.  
  
<a name="otheranimationtypes"></a>   
## <a name="other-animation-types"></a>Diğer animasyon türleri  
 From/To/By animasyonları animasyon türü değil, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sağlar: anahtar çerçeve animasyonları ve yol animasyonları de sağlar.  
  
-   Bir anahtar çerçeve animasyonu anahtar çerçeveler kullanarak açıklanan hedef değerlerden herhangi bir sayıda canlandırır. Daha fazla bilgi için bkz: [anahtar çerçeve animasyonları genel bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
-   Yol animasyonu çıkış değerleri oluşturur bir <xref:System.Windows.Media.PathGeometry>. Daha fazla bilgi için bkz: [yol animasyonlarına genel bakış](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Ayrıca, kendi özel animasyon türleri oluşturmanıza olanak sağlar. Daha fazla bilgi için bkz: [özel animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Animation.Timeline>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [Animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Anahtar çerçeve animasyonları genel bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Yol animasyonlarına genel bakış](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)  
 [Özel Animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md)  
 [Öğesinden, için ve animasyon hedef değerleri örneği](http://go.microsoft.com/fwlink/?LinkID=159988)
