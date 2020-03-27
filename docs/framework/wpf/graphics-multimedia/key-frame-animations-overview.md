---
title: Anahtar-Çerçeve Animasyonlara Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], key-frame
- key frames [WPF], about key-frame animations
- multiple animation target values [WPF]
ms.assetid: 10028f97-bb63-41fc-b8ad-663dac7ea203
ms.openlocfilehash: 8eb590b07eae3b76b3a206b9731997a6bc2c90d7
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344901"
---
# <a name="key-frame-animations-overview"></a>Anahtar-Çerçeve Animasyonlara Genel Bakış
Bu konu, anahtar kare animasyonları ile tanıştırır. Anahtar kare animasyonları, ikiden fazla hedef değeri kullanarak animasyon yapmanızı ve animasyonun enterpolasyon yöntemini denetlemenizi sağlar.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Ön koşullar  
 Bu genel bakışı anlamak için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] animasyonlara ve zaman çizelgelerine aşina olmalısınız. Animasyonlara giriş için [Animasyona Genel Bakış'a](animation-overview.md)bakın. Ayrıca, From/To/By animasyonlarına aşina olmak da yardımcı olur. Daha fazla bilgi için, Gelen/To/By Animasyonlara Genel Bakış'a bakın.  
  
<a name="whatisakeyframeanimation"></a>
## <a name="what-is-a-key-frame-animation"></a>Anahtar Kare Animasyonu Nedir?  
 Bir From/To/By animasyonu gibi, anahtar kare animasyonu hedef özelliğin değerini animasyona salar. Onun üzerinde hedef değerleri arasında bir <xref:System.Windows.Media.Animation.Timeline.Duration%2A>geçiş oluşturur. Ancak, Biri/To/By animasyonu iki değer arasında geçiş oluştururken, tek bir anahtar kare animasyonu herhangi bir hedef değer sayısı arasında geçişler oluşturabilir. Bir Gelen/To/By animasyonundan farklı olarak, hedef değerlerini ayarladığı Bir Anahtar Kare animasyonundan, From, To veya By özellikleri yoktur. Anahtar kare animasyonun hedef değerleri anahtar kare nesneleri kullanılarak tanımlanır (dolayısıyla "anahtar kare animasyonu" terimi). Animasyonun hedef değerlerini belirtmek için anahtar kare nesneleri oluşturur ve bunları <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> animasyonun koleksiyonuna eklersiniz. Animasyon çalıştığında, belirttiğiniz kareler arasında geçiş eder.  
  
 Birden çok hedef değerlerini desteklemenin yanı sıra, bazı anahtar kare yöntemleri birden çok enterpolasyon yöntemini bile destekler. Animasyonun enterpolasyon yöntemi, bir değerden diğerine nasıl geçiş yapılacağını tanımlar. Üç tür enterpolasyon vardır: ayrık, doğrusal ve splined.  
  
 Anahtar kare animasyonuyla animasyon yapmak için aşağıdaki adımları tamamlarsınız.  
  
- Animasyonu bildirin <xref:System.Windows.Media.Animation.Timeline.Duration%2A>ve tıpkı bir from/to/by animasyonu için yaptığınız gibi animasyonunu belirtin.  
  
- Her hedef değer için, uygun türde bir anahtar <xref:System.Windows.Media.Animation.KeyTime>çerçevesi oluşturun, değerini ayarlayın <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> ve animasyonun koleksiyonuna ekleyin.  
  
- Animasyonu, tıpkı Bir Gelen/To/By animasyonuyla yaptığınız gibi bir özellik ile ilişkilendirin. Bir film şeridini kullanarak bir tesise animasyon uygulama hakkında daha fazla bilgi için [Storyboards Genel Bakış'a](storyboards-overview.md)bakın.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> bir <xref:System.Windows.Shapes.Rectangle> öğeyi dört farklı konuma animasyonyapmak için a kullanır.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
 Bir Gelen/To/By animasyonu gibi, bir anahtar kare animasyonu <xref:System.Windows.Media.Animation.Storyboard> da bir biçimlendirme ve <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> kod kullanılarak veya koddaki yöntemi kullanarak bir özelliğe uygulanabilir. Bir anahtar kare animasyonu oluşturmak <xref:System.Windows.Media.Animation.AnimationClock> ve bir veya daha fazla özele uygulamak için de kullanabilirsiniz. Animasyonları uygulamak için farklı yöntemler hakkında daha fazla bilgi [için, Özellik Animasyon Teknikleri Genel Bakış](property-animation-techniques-overview.md)bakın.  
  
<a name="animation_types"></a>
## <a name="key-frame-animation-types"></a>Anahtar Kare Animasyon Türleri  
 Animasyonlar özellik değerleri oluşturduğundan, farklı özellik türleri için farklı animasyon türleri vardır. Bir <xref:System.Double> özelliği (öğenin <xref:System.Windows.FrameworkElement.Width%2A> özelliği gibi) alan bir özelliği canlandırmak için değerler <xref:System.Double> üreten bir animasyon kullanırsınız. Bir özelliği canlandırmak için , <xref:System.Windows.Point>değerler üreten <xref:System.Windows.Point> bir animasyon kullanırsınız ve böyle devam edin.  
  
 Anahtar kare animasyon sınıfları <xref:System.Windows.Media.Animation> ad alanına aittir ve aşağıdaki adlandırma kuralına uyar:  
  
 * \<Tip>*`AnimationUsingKeyFrames`  
  
 * \<Tür>* sınıf animasyonları değer türüdür.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aşağıdaki anahtar kare animasyon sınıflarını sağlar.  
  
|Özellik türü|Animasyon sınıfından/to/by animasyon sınıfına karşılık gelen|Enterpolasyon yöntemleri desteklendi|  
|-------------------|------------------------------------------------|-------------------------------------|  
|<xref:System.Boolean>|<xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>|Ayrık|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimationUsingKeyFrames>|Ayrık, Doğrusal, Splined|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|Ayrık, Doğrusal, Splined|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimationUsingKeyFrames>|Ayrık, Doğrusal, Splined|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|Ayrık, Doğrusal, Splined|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16AnimationUsingKeyFrames>|Ayrık, Doğrusal, Splined|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32AnimationUsingKeyFrames>|Ayrık, Doğrusal, Splined|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64AnimationUsingKeyFrames>|Ayrık, Doğrusal, Splined|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>|Ayrık|  
|<xref:System.Object>|<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>|Ayrık|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|Ayrık, Doğrusal, Splined|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames>|Ayrık, Doğrusal, Splined|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>|Ayrık, Doğrusal, Splined|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames>|Ayrık, Doğrusal, Splined|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimationUsingKeyFrames>|Ayrık, Doğrusal, Splined|  
|<xref:System.String>|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Ayrık|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>|Ayrık, Doğrusal, Splined|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>|Ayrık, Doğrusal, Splined|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames>|Ayrık, Doğrusal, Splined|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimationUsingKeyFrames>|Ayrık, Doğrusal, Splined|  
  
<a name="animation_target_values"></a>
## <a name="target-values-key-frames-and-key-times"></a>Hedef Değerler (anahtar kareler) ve Anahtar Saatler  
 Farklı özellik türlerini animasyonlaştırmak için farklı anahtar kare animasyontürleri olduğu gibi, farklı anahtar kare nesneleri de vardır: desteklenen her değer türü için bir tane. Anahtar kare türleri aşağıdaki adlandırma kuralına bağlıdır:  
  
 *EnterpolasyonYöntemi \<>Tip>\<*`KeyFrame`  
  
 EnterpolasyonYöntemi>anahtar çerçevenin kullandığı enterpolasyon yöntemidir ve * \<>yazın* sınıf animasyonu yaptığı değer türüdür. * \<* Üç enterpolasyon yöntemini destekleyen bir anahtar kare animasyonu, kullanabileceğiniz üç anahtar kare türüne sahip olur. Örneğin, üç anahtar kare türü kullanabilirsiniz: <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>, <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>, ve . (Enterpolasyon yöntemleri daha sonraki bir bölümde ayrıntılı olarak açıklanmıştır.)  
  
 Bir anahtar çerçevenin birincil amacı <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> a <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>ve a . Her anahtar kare türü bu iki özelliği sağlar.  
  
- Özellik, <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> bu anahtar çerçevesinin hedef değerini belirtir.  
  
- Özellik, <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> (animasyonun <xref:System.Windows.Media.Animation.Timeline.Duration%2A>içinde) bir anahtar çerçeveye ne <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> zaman ulaşılalı olduğunu belirtir.  
  
 Bir anahtar kare animasyonu başladığında, <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> anahtar kareleri arasından özellikleriyle tanımlanan sırada yineler.  
  
- Saat 0'da anahtar çerçevesi yoksa, animasyon hedef özelliğin geçerli değeri ile <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> ilk anahtar çerçevenin değeri arasında bir geçiş oluşturur; aksi takdirde, animasyonun çıkış değeri ilk anahtar çerçevenin değeri olur.  
  
- Animasyon, ikinci anahtar çerçevesi <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> tarafından belirtilen enterpolasyon yöntemini kullanarak birinci ve ikinci anahtar kareler arasında bir geçiş oluşturur. Geçiş ilk anahtar çerçevenin başlar <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> ve ikinci anahtar çerçevesine <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> ulaşıldığında sona erer.  
  
- Animasyon, sonraki her anahtar kare ve önceki anahtar çerçevesi arasında geçişler oluşturarak devam eder.  
  
- Son olarak, animasyon, animasyonunkine eşit veya daha küçük olan en büyük anahtar <xref:System.Windows.Media.Animation.Timeline.Duration%2A>süresiyle anahtar çerçevenin değerine geçiş eder.  
  
 Animasyonunki <xref:System.Windows.Media.Animation.Timeline.Duration%2A> <xref:System.Windows.Duration.Automatic%2A> veya son <xref:System.Windows.Media.Animation.Timeline.Duration%2A> anahtar karesinin zamanına eşitse, animasyon sona erer. Aksi takdirde, animasyonunki <xref:System.Windows.Duration> son anahtar çerçevenin anahtar saatinden büyükse, animasyon anahtar kare değerini <xref:System.Windows.Duration>sonuna ulaşana kadar tutar. Tüm animasyonlar gibi, anahtar kare <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> animasyonu da etkin döneminin sonuna ulaştığında son değerini tutup tutmadığını belirlemek için özelliğini kullanır. Daha fazla bilgi için [Zamanlama Davranışlarına Genel Bakış'a](timing-behaviors-overview.md)bakın.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> önceki örnekte tanımlanan nesneyi, <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> özelliklerin ve <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> özelliklerin nasıl çalıştığını göstermek için kullanır.  
  
- İlk anahtar kare hemen animasyonun çıkış değerini 0 olarak ayarlar.  
  
- İkinci anahtar kare 0'dan 350'ye kadar animasyonyapar. İlk anahtar kare sona erdikten sonra başlar (zaman = 0 saniye) ve 2 saniye boyunca çalar, zaman = 0:0:2'de biter.  
  
- Üçüncü anahtar kare 350'den 50'ye yükseltiler. İkinci anahtar kare sona erdiğinde (zaman = 2 saniye) başlar ve 5 saniye boyunca çalış, saat = 0:0:7'de biter.  
  
- Dördüncü anahtar kare 50'den 200'e yükseltiler. Üçüncü anahtar kare sona erdiğinde (zaman = 7 saniye) başlar ve 1 saniye boyunca oynar ve saat = 0:0:8'de biter.  
  
- Animasyonun <xref:System.Windows.Media.Animation.Timeline.Duration%2A> özelliği 10 saniye olarak ayarlandığından, animasyon son değerini saat = 0:0:10'da sona ermeden önce iki saniye tutar.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
<a name="interpolationmethods"></a>
## <a name="interpolation-methods"></a>İnterpolasyon Yöntemleri  
 Önceki bölümlerde, bazı anahtar kare animasyonlarının birden çok enterpolasyon yöntemini desteklediği belirtilmiştir. Animasyonun enterpolasyonu, animasyonun süresi boyunca değerler arasında nasıl geçiş yaptığıaçıklanır. Animasyonunuzda hangi anahtar kare türünü kullandığınızı seçerek, bu anahtar kare kesimi için enterpolasyon yöntemini tanımlayabilirsiniz. Üç farklı enterpolasyon yöntemi vardır: doğrusal, ayrık ve splined.  
  
### <a name="linear-interpolation"></a>Lineer Enterpolasyon  
 Doğrusal enterpolasyon ile animasyon, segment süresinin sabit bir hızında ilerler. Örneğin, bir anahtar kare kesimi 5 saniyelik bir süre içinde 0'dan 10'a geçiş yaparsa, animasyon belirtilen zamanlarda aşağıdaki değerleri çıkaracaktır:  
  
|Zaman|Çıkış değeri|  
|----------|------------------|  
|0|0|  
|1|2|  
|2|4|  
|3|6|  
|4|8|  
|4.25|8.5|  
|4,5|9|  
|5|10|  
  
### <a name="discrete-interpolation"></a>Ayrık Enterpolasyon  
 Ayrık enterpolasyon ile animasyon işlevi enterpolasyon olmadan bir değerden diğerine atlar. Bir anahtar kare kesimi 5 saniyelik bir süre içinde 0'dan 10'a geçiş yaparsa, animasyon belirtilen zamanlarda aşağıdaki değerleri çıkaracaktır:  
  
|Zaman|Çıkış değeri|  
|----------|------------------|  
|0|0|  
|1|0|  
|2|0|  
|3|0|  
|4|0|  
|4.25|0|  
|4,5|0|  
|5|10|  
  
 Animasyonun, segment süresinin sonuna kadar çıktı değerini nasıl değiştirmediğini öğrenin.  
  
 Splined enterpolasyon daha karmaşıktır. Bir sonraki bölümde açıklanmıştır.  
  
<a name="anim_spline"></a>
### <a name="splined-interpolation"></a>Splined Enterpolasyon  
 Splined enterpolasyon daha gerçekçi zamanlama efektleri elde etmek için kullanılabilir. Animasyonlar genellikle gerçek dünyada meydana gelen efektleri taklit etmek için kullanıldığından, geliştiricilerin nesnelerin hızlanması ve yavaşlaması üzerinde ince denetime ve zamanlama segmentlerinin yakın manipülasyonuna ihtiyacı olabilir. Spline anahtar kareler, splined enterpolasyon ile animasyon yapmanızı sağlar. Diğer anahtar çerçevelerde, bir <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>ve . Spline anahtar çerçevesi ile, aynı <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>zamanda bir . Aşağıdaki örnekte, bir <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>. için tek bir spline anahtar çerçevesi gösterilmektedir. Tesise <xref:System.Windows.Media.Animation.KeySpline> dikkat edin; bu, bir spline anahtar çerçevesinin diğer anahtar kare türlerinden farklı olduğunu gösteriyor.  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Kübik Bezier eğrisi bir başlangıç noktası, bir bitiş noktası ve iki kontrol noktası ile tanımlanır. Spline anahtar çerçevesinin özelliği, <xref:System.Windows.Media.Animation.KeySpline> (0,0) ile (1,1) arasında uzanan bir Bezier eğrisinin iki denetim noktasını tanımlar. İlk kontrol noktası Bezier eğrisinin ilk yarısının eğri faktörünün kontrol eder, ikinci kontrol noktası ise Bezier segmentinin ikinci yarısının eğri faktörünün kontrol eder. Elde edilen eğri, o spline anahtar çerçevesi için değişim oranını açıklar. Eğri ne kadar dikse, anahtar kare değerlerini o kadar hızlı değiştirir. Eğri düzleştikçe, anahtar kare değerlerini daha yavaş değiştirir.  
  
 Düşen su <xref:System.Windows.Media.Animation.KeySpline> veya zıplayan toplar gibi fiziksel yörüngeleri simüle etmek veya hareket animasyonlarına diğer "kolaylık" ve "kolaylaş" efektlerini uygulamak için kullanabilirsiniz. Arka plan soluklukları veya denetim düğmesi geri tepmesi gibi kullanıcı etkileşimi efektleri için, bir animasyonun değişim hızını belirli bir şekilde hızlandırmak veya yavaşlatmak için splined enterpolasyon uygulayabilirsiniz.  
  
 Aşağıdaki örnekte 0,1 1,0'ın bir <xref:System.Windows.Media.Animation.KeySpline> bölümü belirtilir ve bu da aşağıdaki Bezier eğrisini oluşturur.  
  
 ![Bir Bezier eğrisi](./media/graphicsmm-keyspline-0-1-1-0.png "graphicsmm_keyspline_0_1_1_0")  
Kontrol noktaları (0,0, 1,0) ve (1,0, 0,0) olan bir anahtar spline  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Bu anahtar kare başladığında hızla canlanır, yavaşlar ve sona ermeden önce tekrar hızlanır.  
  
 Aşağıdaki örnek, aşağıdaki <xref:System.Windows.Media.Animation.KeySpline> Bezier eğrisini oluşturan 0,5,0,25 0,75,1,0'ın bir  
  
 ![Bir Bezier eğrisi](./media/graphicsmm-keyspline-025-050-075-10.png "graphicsmm_keyspline_025_050_075_10")  
Kontrol noktaları (0,25, 0,5) ve (0,75, 1,0) ile bir anahtar spline  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexampleinline3)]  
  
 Bezier eğrisinin eğriliği çok az değiştiğinden, bu anahtar kare neredeyse sabit bir hızda canlandırır; sonuna doğru biraz yavaşlar.  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> dikdörtgenin konumunu canlandırmak için a kullanır. Nesneleri <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> kullandığından, <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> her anahtar kare değeri arasındaki geçiş, splined enterpolasyon kullanır.  
  
 [!code-xaml[keyframes_ovw_snippet#SplinedInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#splinedinterpolationexample)]  
  
 Splined enterpolasyon anlamak zor olabilir; farklı ayarlarla denemeler yardımcı olabilir. [Key Spline Animasyon Örneği,](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/KeySplineAnimations) anahtar spline değerlerini değiştirmenizi ve bir animasyonda elde ettiği sonucu görmenizi sağlar.  
  
<a name="combininginterpolationmethods"></a>
### <a name="combining-interpolation-methods"></a>İnterpolasyon Yöntemlerini Birleştirme  
 Tek bir anahtar kare animasyonunda farklı enterpolasyon türlerine sahip anahtar kareler kullanabilirsiniz. Farklı enterpolasyonlara sahip iki anahtar kare animasyonları birbirini takip ettiğinde, ikinci anahtar karenin enterpolasyon yöntemi, birinci değerden ikinciye geçişi oluşturmak için kullanılır.  
  
 Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> doğrusal, splined ve ayrık enterpolasyon kullanan bir oluşturulur.  
  
 [!code-xaml[keyframes_ovw_snippet#ComboInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#combointerpolationexample)]  
  
<a name="keytimes"></a>
## <a name="more-about-duration-and-key-times"></a>Süre ve Anahtar Saatler hakkında daha fazla şey  
 Diğer animasyonlar gibi, anahtar kare <xref:System.Windows.Duration> animasyonların da bir özelliği vardır. Animasyonun <xref:System.Windows.Duration>, bu sürenin her anahtar karesine hangi bölümünün verildiğini belirtmeniz gerekir. Bunu, animasyonun anahtar <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> karelerinin her biri için a'yı tanımlayarak yaparsınız. Her anahtar kare, bu anahtar çerçevenin ne zaman sona erdiğini <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> belirtir.  
  
 Özellik, <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> anahtar süresinin ne kadar süreceğini belirtmez. Bir anahtar çerçevenin oynamacı, anahtar çerçevenin ne zaman sona ereceği, önceki anahtar kare sona erdiğinde ve animasyonun süresine göre belirlenir. Anahtar saatler bir zaman değeri, bir yüzde veya özel <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>değerler veya .  
  
 Aşağıdaki liste, anahtar saatlerini belirtmenin farklı yollarını açıklar.  
  
### <a name="timespan-values"></a>Zaman Aralığı Değerleri  
 Bir <xref:System.Windows.Media.Animation.KeyTime>. <xref:System.TimeSpan> belirtmek için değerleri kullanabilirsiniz Değer, 0'dan büyük veya eşit ve animasyonun süresinden daha az veya eşit olmalıdır. Aşağıdaki örnekte, 10 saniye lik bir süreye sahip bir animasyon ve anahtar süreleri zaman değerleri olarak belirtilen dört anahtar kare gösterilmektedir.  
  
- İlk anahtar kare, ilk 3 saniye içinde temel değerden 100'e çıkar ve saat = 0:0:03'te sona erer.  
  
- İkinci anahtar kare 100'den 200'e yükseltiler. İlk anahtar kare sona erdikten sonra başlar (zaman = 3 saniye) ve 5 saniye boyunca oynar, zaman = 0:0:8 biter.  
  
- Üçüncü anahtar kare 200'den 500'e yükseltiler. İkinci anahtar kare sona erdiğinde (zaman = 8 saniye) başlar ve 1 saniye boyunca oynar ve saat = 0:0:9'da biter.  
  
- Dördüncü anahtar kare 500'den 600'e yükseltiler. Üçüncü anahtar kare sona erdiğinde (zaman = 9 saniye) başlar ve 1 saniye boyunca oynar ve saat = 0:0:10'da biter.  
  
 [!code-xaml[keyframes_ovw_snippet#TimeSpanKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#timespankeytimeexample)]  
  
### <a name="percentage-values"></a>Yüzde Değerleri  
 Yüzde değeri, anahtar çerçevenin animasyonun bazı yüzdesi <xref:System.Windows.Media.Animation.Timeline.Duration%2A>ile sona erdiğini belirtir. , [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]yüzdeyi `%` sembol tarafından izlenen bir sayı olarak belirtirsiniz. Kod olarak, <xref:System.Windows.Media.Animation.KeyTime.FromPercent%2A> yöntemi kullanın ve <xref:System.Double> yüzde gösteren bir geçmek. Değer 0'dan büyük veya eşit ve yüzde 100'den küçük veya eşit olmalıdır. Aşağıdaki örnekte, 10 saniye lik bir süreye sahip bir animasyon ve anahtar süreleri yüzde olarak belirtilen dört anahtar kare gösterilmektedir.  
  
- İlk anahtar kare, ilk 3 saniye içinde temel değerden 100'e çıkar ve saat = 0:0:3'te sona erer.  
  
- İkinci anahtar kare 100'den 200'e yükseltiler. İlk anahtar kare sona erdikten sonra başlar (zaman = 3 saniye) ve 5 saniye boyunca oynar, zaman = 0:0:8 (0,8 * 10 = 8) biter.  
  
- Üçüncü anahtar kare 200'den 500'e yükseltiler. İkinci anahtar kare sona erdiğinde (zaman = 8 saniye) başlar ve 1 saniye boyunca oynar ve zaman = 0:0:9 (0,9 * 10 = 9) ile biter.  
  
- Dördüncü anahtar kare 500'den 600'e yükseltiler. Üçüncü anahtar kare sona erdiğinde (zaman = 9 saniye) başlar ve 1 saniye boyunca oynar ve zaman = 0:0:10 (1 * 10 = 10) ile biter.  
  
 [!code-xaml[keyframes_ovw_snippet#PercentageKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#percentagekeytimeexample)]  
  
### <a name="special-value-uniform"></a>Özel Değer, Üniforma  
 Her <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> anahtar çerçevenin aynı süreyi almasını istediğinizde zamanlamayı kullanın.  
  
 Anahtar <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> zaman, kullanılabilir zamanı her anahtar çerçevenin bitiş saatini belirlemek için anahtar kare sayısına eşit olarak böler. Aşağıdaki örnekte, 10 saniye lik bir süreye sahip bir animasyon <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>ve anahtar süreleri . olarak belirtilen dört anahtar kare gösterilmektedir.  
  
- İlk anahtar kare, ilk 2,5 saniye içinde temel değerden 100'e çıkar ve saat = 0:0:2,5'te biter.  
  
- İkinci anahtar kare 100'den 200'e yükseltiler. İlk anahtar kare sona erdikten sonra başlar (zaman = 2,5 saniye) ve yaklaşık 2,5 saniye boyunca çalar, zaman = 0:0:5'te biter.  
  
- Üçüncü anahtar kare 200'den 500'e yükseltiler. İkinci anahtar kare sona erdiğinde (zaman = 5 saniye) başlar ve 2,5 saniye boyunca çalış, saat = 0:0:7.5'te biter.  
  
- Dördüncü anahtar kare 500'den 600'e yükseltiler. İkinci anahtar kare sona erdiğinde (zaman = 7,5 saniye) başlar ve 2,5 saniye boyunca çalış, saat = 0:0:1'de sona erer.  
  
 [!code-xaml[keyframes_ovw_snippet#UniformKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#uniformkeytimeexample)]  
  
### <a name="special-value-paced"></a>Özel Değer, Tempolu  
 Sabit <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> bir hızda animasyon yapmak istediğinizde zamanlamayı kullanın.  
  
 Anahtar <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> zaman, her bir çerçevenin süresini belirlemek için anahtar çerçevelerin her birinin uzunluğuna göre kullanılabilir zamanı ayırır.  Bu, animasyonun hızının veya hızının sabit kalması davranışını sağlar.  Aşağıdaki örnekte, 10 saniye lik bir süreye sahip bir animasyon <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>ve anahtar süreleri . olarak belirtilen üç anahtar kare gösterilmektedir.  
  
 [!code-xaml[keyframes_ovw_snippet#PacedKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#pacedkeytimeexample)]  
  
 Son anahtar çerçevesinin anahtar zamanı veya <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>çözümlenmiş anahtar zamanı yüzde 100 olarak ayarlanır. Çok çerçeveli animasyondaki ilk anahtar kare paced ise, çözülmüş anahtar süresi 0 olarak ayarlanır. (Anahtar kare koleksiyonu yalnızca tek bir anahtar çerçevesi içeriyorsa ve tempolu bir anahtar çerçevesiyse, çözülmüş anahtar süresi yüzde 100 olarak ayarlanır.)  
  
 Tek bir anahtar kare animasyonu içindeki farklı anahtar kareler farklı anahtar zaman türlerini kullanabilir.  
  
<a name="combiningkeytimes"></a>
## <a name="combining-key-times-out-of-order-key-frames"></a>Anahtar Süreleri Birleştirme, Sıra Dışı Anahtar Çerçeveler  
 Aynı animasyonda farklı <xref:System.Windows.Media.Animation.KeyTime> değer türlerine sahip anahtar kareler kullanabilirsiniz. Ve, oynamaları gereken sırayla anahtar kareeklemeniz önerilir, ancak bu gerekli değildir. Animasyon ve zamanlama sistemi sırayla anahtar çerçeveleri çözme yeteneğine sahiptir. Geçersiz anahtar saatleri olan anahtar kareler yoksayılır.  
  
 Aşağıdaki liste, anahtar kare animasyonun anahtar kareleri için anahtar saatlerinin çözümlendiği yordamı açıklar.  
  
1. Değerleri <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> çözümle.  
  
2. Animasyonun toplam *enterpolasyon süresini*, ileri yinelemeyi tamamlamak için anahtar kare animasyonun gereken toplam süreyi belirleyin.  
  
    1. Animasyonunki <xref:System.Windows.Media.Animation.Timeline.Duration%2A> <xref:System.Windows.Duration.Automatic%2A> veya, <xref:System.Windows.Duration.Forever%2A>toplam enterpolasyon süresi animasyonun <xref:System.Windows.Media.Animation.Timeline.Duration%2A> özelliğinin değeriyse.  
  
    2. Aksi takdirde, toplam enterpolasyon <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> süresi, varsa, anahtar çerçeveleri arasında belirtilen en büyük değerdir.  
  
    3. Aksi takdirde, toplam enterpolasyon süresi 1 saniyedir.  
  
3. Değerleri çözmek <xref:System.Windows.Media.Animation.KeyTimeType.Percent> <xref:System.Windows.Media.Animation.KeyTime> için toplam enterpolasyon süresi değerini kullanın.  
  
4. Önceki adımlarda zaten çözülmemişse, son anahtar kareyi çözümle. Son <xref:System.Windows.Media.Animation.KeyTime> anahtar çerçevenin <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> veya <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>, çözümlenmiş süresinin toplam enterpolasyon süresine eşit olması durumunda.  
  
     İlk <xref:System.Windows.Media.Animation.KeyTime> anahtar çerçevenin değeri <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> ise ve bu animasyon anahtar karelerde <xref:System.Windows.Media.Animation.KeyTime> daha fazlaysa, değerini sıfıra çözün; yalnızca bir anahtar çerçeve varsa <xref:System.Windows.Media.Animation.KeyTime> ve <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>değeri, önceki adımda açıklandığı gibi toplam enterpolasyon süresine çözülür.  
  
5. Kalan <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> değerleri çözün: her birine kullanılabilir zaman eşit bir pay verilir.  Bu işlem sırasında, <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> çözülmemiş değerler <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> geçici olarak değer olarak kabul edilir ve geçici olarak çözülmüş bir süre alırsınız.  
  
6. Anahtar <xref:System.Windows.Media.Animation.KeyTime> karelerin değerlerini, çözümlenmiş <xref:System.Windows.Media.Animation.KeyTime> değerleri en yakın olarak bildirilen anahtar çerçeveleri kullanarak, belirtilmemiş anahtar lık süreleri olan değerleri çözümleyin.  
  
7. Kalan <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> değerleri çözümle. <xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime> çözümlenmiş <xref:System.Windows.Media.Animation.KeyTime> zamanlarını belirlemek için komşu anahtar çerçevelerin değerlerini kullanın.  Amaç, animasyonun hızının bu anahtar çerçevenin çözümlenmiş süresi etrafında sabit olmasını sağlamaktır.  
  
8. Anahtar çerçeveleri çözümlenmiş zaman (birincil anahtar) ve bildirim sırası (ikincil anahtar) sırasına göre sıralayın, yani <xref:System.Windows.Media.Animation.KeyTime> çözülmüş anahtar kare değerlerini temel alan kararlı bir sıralama kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Animation.KeyTime>
- <xref:System.Windows.Media.Animation.KeySpline>
- <xref:System.Windows.Media.Animation.Timeline>
- [Anahtar Spline Animasyon Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/KeySplineAnimations)
- [Anahtar Kare Animasyon Örneği](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)
- [Animasyona Genel bakış](animation-overview.md)
- [Görsel Taslaklara Genel Bakış](storyboards-overview.md)
- [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](key-frame-animation-how-to-topics.md)
- [Zamanlama Davranışlarına Genel Bakış](timing-behaviors-overview.md)
