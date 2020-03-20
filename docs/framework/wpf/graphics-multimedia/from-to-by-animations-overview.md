---
title: From-To-By Animasyonlar Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
ms.openlocfilehash: 135f01823d374b30f8d4d41762d2267a254f98c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186457"
---
# <a name="fromtoby-animations-overview"></a>Gelen/İçin/Göre Animasyonlarına Genel Bakış
Bu konu, bağımlılık özelliklerini canlandırmak için Gelen/To/By animasyonlarının nasıl kullanılacağını açıklar. A From/To/By animasyonu iki değer arasında geçiş oluşturur.  
  
<a name="prereq"></a>
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için animasyon [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliklerine aşina olmalısınız. Animasyon özelliklerine giriş için [Animasyona Genel Bakış'a](animation-overview.md)bakın.  
  
<a name="whatisanimation"></a>
## <a name="what-is-a-fromtoby-animation"></a>Kimden/To/By Animasyon nedir?  
 A From/To/By animasyonu, <xref:System.Windows.Media.Animation.AnimationTimeline> başlangıç değeri ile bitiş değeri arasında geçiş oluşturan bir türdür. Geçişin tamamlanması için gereken süre, bu <xref:System.Windows.Media.Animation.Timeline.Duration%2A> animasyonun sayısına göre belirlenir.  
  
 Bir özellik için bir <xref:System.Windows.Media.Animation.Storyboard> biçimlendirme ve kod kullanarak veya koddaki <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi kullanarak Bir Ani/To/By animasyonu uygulayabilirsiniz. Ayrıca, bir <xref:System.Windows.Media.Animation.AnimationClock> veya daha fazla özellik oluşturmak ve uygulamak için Bir Kişi/To/By Animasyonu da kullanabilirsiniz. Animasyonları uygulamak için farklı yöntemler hakkında daha fazla bilgi [için, Özellik Animasyon Teknikleri Genel Bakış](property-animation-techniques-overview.md)bakın.  
  
 Gelen/To/By animasyonlarının en fazla iki hedef değeri olabilir. İkiden fazla hedef değeri olan bir animasyona ihtiyacınız varsa, anahtar kare animasyonu kullanın. Anahtar kare [animasyonları Anahtar Kare Animasyonlar Genel Bakış](key-frame-animations-overview.md)açıklanmıştır.  
  
<a name="animation_types"></a>
## <a name="fromtoby-animation-types"></a>From/To/By Animasyon Türleri  
 Animasyonlar özellik değerleri oluşturduğundan, farklı özellik türleri için farklı animasyon türleri vardır. Bir öğenin <xref:System.Double> <xref:System.Windows.FrameworkElement.Width%2A> özelliği gibi bir özelliği canlandıracak, değerler üreten <xref:System.Double> bir animasyon kullanın. Bir özelliği canlandırmak için , <xref:System.Windows.Point>değerler üreten <xref:System.Windows.Point> bir animasyon kullanın, ve benzeri.  
  
 Gelen/To/By animasyon sınıfları <xref:System.Windows.Media.Animation> ad alanına aittir ve aşağıdaki adlandırma kuralını kullanır:  
  
 * \<Tip>*`Animation`  
  
 * \<Tür>* sınıf animasyonları değer türüdür.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aşağıdaki From/To/By animasyon sınıflarını sağlar.  
  
|Özellik türü|Karşılık Gelen/To/By animasyon sınıfı|  
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
## <a name="target-values"></a>Hedef Değerler  
 A From/To/By animasyonu iki hedef değer arasında geçiş oluşturur. Bir başlangıç değeri <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> (özelliği kullanarak ayarlamak) ve bir bitiş değeri <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> (özelliği kullanarak ayarlayın) belirtmek yaygındır. Ancak, yalnızca başlangıç değeri, hedef değer veya mahsup değeri de belirtebilirsiniz. Bu gibi durumlarda, animasyon animasyonlu özelliğinden eksik hedef değeri alır. Aşağıdaki liste, animasyonun hedef değerlerini belirtmenin farklı yollarını açıklar.  
  
- **Başlangıç Değeri**  
  
     Animasyonun <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> başlangıç değerini açıkça belirtmek istediğinizde özelliği kullanın. <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> Özelliği tek başına veya <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> mülkle birlikte kullanabilirsiniz. Yalnızca <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği belirtirseniz, animasyon bu değerden animasyonlu özelliğin temel değerine geçiş eder.  
  
- **Bitiş Değeri**  
  
     Animasyonun bitiş değerini belirtmek için <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliğini kullanın. <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> Özelliği tek başına kullanırsanız, animasyon başlangıç değerini animasyonlu olan özellikten veya aynı özelliğe uygulanan başka bir animasyonun çıktısından elde eder. Animasyon için <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> başlangıç ve <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> bitiş değerlerini açıkça belirtmek için özelliği özellik ile birlikte kullanabilirsiniz.  
  
- **Mahsup Değeri**  
  
     Özellik, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> animasyon için açık bir başlangıç veya bitiş değeri yerine bir ofset belirtmenizi sağlar. Animasyonun özelliği, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> animasyonun süresi boyunca bir değeri ne kadar değiştirip değiştirinolduğunu belirtir. <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Mülkü tek başına veya <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> mülkle birlikte kullanabilirsiniz. Yalnızca <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliği belirtirseniz, animasyon mahsup değerini özelliğin temel değerine veya başka bir animasyonun çıktısına ekler.  
  
<a name="examples"></a>
## <a name="using-fromtoby-values"></a>From/To/By değerlerini kullanma  
 Aşağıdaki bölümlerde <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, ve <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özellikleribirlikte veya ayrı ayrı nasıl kullanılacağı açıklanmıştır.  
  
 Bu bölümdeki örneklerin <xref:System.Windows.Media.Animation.DoubleAnimation>her biri, 10 aygıtbağımsız piksel ivedi ve <xref:System.Windows.FrameworkElement.Width%2A> 100 aygıt bağımsız piksel genişliğinde bir özelliği canlandırmak için, Bir/To/By animasyon türü olan bir <xref:System.Windows.Shapes.Rectangle> tane kullanır.  
  
 Her örnekte <xref:System.Windows.Media.Animation.DoubleAnimation>,From, To ve By özellikleri kullanılsa da Tüm Gelen/To/By animasyonları aynı şekilde çalışır. Bu örneklerin her <xref:System.Windows.Media.Animation.Storyboard>biri bir , Kişi/To/By animasyonlarını başka şekillerde kullanabilirsiniz. Daha fazla bilgi için Emlak [Animasyon Teknikleri Genel Bakış'a](property-animation-techniques-overview.md)bakın.  
  
### <a name="fromto"></a>Kaynaktan/Için  
 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> Ve <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> değerleri birlikte ayarladığınızda, animasyon <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özellik tarafından belirtilen değerden <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özellik tarafından belirtilen değere doğru ilerler.  
  
 Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 50'nin <xref:System.Windows.Media.Animation.DoubleAnimation> özelliği <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> ve özelliği 300 olarak ayarlanır. Sonuç olarak, <xref:System.Windows.FrameworkElement.Width%2A> 50 <xref:System.Windows.Shapes.Rectangle> ila 300 animasyonlu.  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>Alıcı  
 Sadece <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği ayarladığınızda, animasyon animasyon özelliğinin temel değerinden veya daha önce aynı özelliğe uygulanmış bir oluşturma animasyonunun çıktısından <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özellik tarafından belirtilen değere ilerler.  
  
 ("Animasyon oluşturma", geçerli <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.ClockState.Filling> animasyon <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> teslim davranışı kullanılarak uygulandığında hala yürürlükte olan aynı özelliğe daha önce uygulanan bir veya animasyon anlamına gelir.)  
  
 Aşağıdaki örnek, 300 için sadece <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliğini <xref:System.Windows.Media.Animation.DoubleAnimation> ayarlar. Başlangıç değeri belirtilmedığından, <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.FrameworkElement.Width%2A> özelliğin temel değerini (100) başlangıç değeri olarak kullanır. 100'den <xref:System.Windows.FrameworkElement.Width%2A> animasyonun hedef değeri 300'e <xref:System.Windows.Shapes.Rectangle> yükseltilir.  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>Ölçüt  
 Animasyon, animasyonun <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliğini ayarladığınızda, animasyon animasyonlanan özelliğin temel değerinden veya bir beste animasyonunun çıktısından bu değerin ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliğin belirlediği değerin toplamına doğru ilerler.  
  
 Aşağıdaki örnek, 300 için sadece <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliğini <xref:System.Windows.Media.Animation.DoubleAnimation> ayarlar. Örnek bir başlangıç değeri belirtmedığından, <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.FrameworkElement.Width%2A> özellik başlangıç değeri olarak 100 olan özelliğin temel değerini kullanır. Bitiş değeri, animasyonun <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> değeri olan 300'ün başlangıç değeri olan 100: 400'e eklenerek belirlenir. Sonuç olarak, <xref:System.Windows.FrameworkElement.Width%2A> 100 <xref:System.Windows.Shapes.Rectangle> ila 400 animasyonlu.  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>Gönderen/Tarafından  
 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> Animasyonun özelliklerini <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> ve özelliklerini ayarladığınızda, animasyon <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özellik tarafından belirtilen değerden, ve <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliklerin toplamıyla belirtilen değere ilerler.  
  
 Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 50'nin <xref:System.Windows.Media.Animation.DoubleAnimation> özelliği <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> ve özelliği 300 olarak ayarlanır. Bitiş değeri, animasyonun <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> değeri olan 300'ün başlangıç değeri olan 50: 350'ye eklenerek belirlenir. Sonuç olarak, <xref:System.Windows.FrameworkElement.Width%2A> 50 <xref:System.Windows.Shapes.Rectangle> ila 350 animasyonlu.  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>Başlangıç  
 Animasyonun değerini <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> belirttiğiniz zaman, animasyon <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özellik tarafından belirtilen değerden animasyonlanan özelliğin temel değerine veya bir animasyonun çıktısına ilerler.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> <xref:System.Windows.Media.Animation.DoubleAnimation> 50'ye kadar olan özelliği ni belirler. Bitiş değeri belirtilmedığından, <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.FrameworkElement.Width%2A> özelliğin temel değerini kullanır, 100, bitiş değeri olarak. 50'den <xref:System.Windows.FrameworkElement.Width%2A> mülkün temel değerine, 100'e kadar <xref:System.Windows.Shapes.Rectangle> animasyonludur. <xref:System.Windows.FrameworkElement.Width%2A>  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>To/By  
 Animasyonun hem <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> de <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> animasyonun özelliklerini ayarlarsanız, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özellik yoksayılır.  
  
<a name="otheranimationtypes"></a>
## <a name="other-animation-types"></a>Diğer Animasyon Türleri  
 Gelen/To/By animasyonları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sağlayan tek animasyon türü değildir: anahtar kare animasyonları ve yol animasyonları da sağlar.  
  
- Anahtar kare animasyonu, anahtar kareler kullanılarak açıklanan herhangi bir hedef değer sayısı boyunca animasyonlar. Daha fazla bilgi için [Anahtar Kare Animasyonlarına Genel Bakış'a](key-frame-animations-overview.md)bakın.  
  
- Yol animasyonu bir <xref:System.Windows.Media.PathGeometry>.'den çıkış değerleri oluşturur Daha fazla bilgi için [Yol Animasyonlarına Genel Bakış'a](path-animations-overview.md)bakın.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ayrıca kendi özel animasyon türlerinizi oluşturmanıza olanak tanır. Daha fazla bilgi için [Özel Animasyonlara Genel Bakış'a](custom-animations-overview.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Animasyona Genel bakış](animation-overview.md)
- [Görsel Taslaklara Genel Bakış](storyboards-overview.md)
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Yol Animasyonlarına Genel Bakış](path-animations-overview.md)
- [Özel Animasyonlara Genel Bakış](custom-animations-overview.md)
- [Animasyon Hedef Değerleri Örneği'nden, Den ve Animasyona Göre](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)
