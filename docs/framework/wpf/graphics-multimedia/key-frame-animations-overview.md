---
title: Anahtar-Çerçeve Animasyonlara Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], key-frame
- key frames [WPF], about key-frame animations
- multiple animation target values [WPF]
ms.assetid: 10028f97-bb63-41fc-b8ad-663dac7ea203
ms.openlocfilehash: caad7d5694139729ebe89e686ea70a981a0a94d2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191594"
---
# <a name="key-frame-animations-overview"></a>Anahtar-Çerçeve Animasyonlara Genel Bakış
Bu konu, anahtar-çerçeve animasyonlara tanıtır. Anahtar-çerçeve animasyonlara ikiden fazla hedef değerleri kullanarak animasyon olanak sağlar ve animasyonun ilişkilendirme metodunu denetleyebilirsiniz.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu genel bakışta anlamak için aşina olmalısınız [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] animasyonları ve zaman çizelgeleri. Animasyonlar giriş için bkz: [animasyona genel bakış](animation-overview.md). Gelen/için/göre animasyonlarına ile ilgili bilgi sahibi olmasını da sağlar. Daha fazla bilgi için bkz: u animasyonlarına genel bakış.  
  
<a name="whatisakeyframeanimation"></a>   
## <a name="what-is-a-key-frame-animation"></a>Anahtar çerçeve animasyonu nedir?  
 Gibi bir From/To/By animasyonu, anahtar çerçeve animasyonu canlandırır hedef özelliğinin değeri. Üzerinden hedef değerleri arasında bir geçiş oluşturur, <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Ancak, while From/To/By animasyonu iki değer arasındaki bir geçiş oluşturur, tek bir anahtar çerçeve animasyon hedef değerleri herhangi bir sayıda arasında geçiş oluşturabilirsiniz. Farklı bir From/To/By animasyonu, anahtar çerçeve animasyonu sahip hiçbir kaynak veya hedef değerleri belirlemek özellikleri tarafından. Nesneleri anahtar çerçeveler kullanarak bir anahtar-çerçeve animasyonun hedef değerleri açıklanan (Bu nedenle terimi, "anahtar çerçeve animasyonu"). Animasyonun hedef değerleri belirlemek için anahtar kare nesneleri oluşturmak ve bunları animasyonun eklemek <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> koleksiyonu. Animasyon çalıştığında, belirttiğiniz kareleri arasında geçiş yapar.  
  
 Birden çok hedef değer hizmetinin yanı sıra, bazı anahtar-çerçeve yöntemleri bile birden çok ilişkilendirme yöntemleri destekler. Animasyonun ilişkilendirme yöntemi nasıl bir değerden sonraki geçişleri tanımlar. İlişkilendirme üç tür vardır: ayrık, doğrusal ve eğri.  
  
 Anahtar çerçeve animasyonu ile animasyon uygulamak için aşağıdaki adımları tamamlayın.  
  
-   Animasyonu bildirin ve belirtin, <xref:System.Windows.Media.Animation.Timeline.Duration%2A>gelen/için/göre animasyon için yaptığınız gibi.  
  
-   Her bir hedef değer için uygun türde bir anahtar kare oluşturmak için kendi değerini ayarlayın ve <xref:System.Windows.Media.Animation.KeyTime>, animasyonun ekleyin <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> koleksiyonu.  
  
-   From/To/By ile olduğu gibi bir özelliğe animasyon ilişkilendirmek animasyon. Bir görsel taslak kullanarak özelliğe animasyon uygulama hakkında daha fazla bilgi için bkz. [görsel taslaklara genel bakış](storyboards-overview.md).  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> animasyon uygulamak için bir <xref:System.Windows.Shapes.Rectangle> dört farklı konumlara öğesi.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
 From/To/By gibi animasyon kullanarak bir özellik için bir anahtar çerçeve animasyonu uygulanabilir bir <xref:System.Windows.Media.Animation.Storyboard> işaretleme ve kod veya kullanarak <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> kodda yöntemi. Anahtar çerçeve animasyon oluşturmak için kullanabilirsiniz bir <xref:System.Windows.Media.Animation.AnimationClock> ve bir veya daha fazla özellikler için geçerlidir. Animasyonlara uygulama için farklı yöntemler hakkında daha fazla bilgi için bkz. [özellik Animasyon Tekniklerine Genel Bakış](property-animation-techniques-overview.md).  
  
<a name="animation_types"></a>   
## <a name="key-frame-animation-types"></a>Anahtar çerçeve animasyonu türleri  
 Özellik değerlerini animasyonlar oluşturması nedeniyle farklı özellik türleri için farklı animasyon türü vardır. Alan özelliği oynatmak bir <xref:System.Double> (bir öğenin gibi <xref:System.Windows.FrameworkElement.Width%2A> özelliği), üreten bir animasyon kullandığınız <xref:System.Double> değerleri. Alan özelliği oynatmak bir <xref:System.Windows.Point>, üreten bir animasyon kullandığınız <xref:System.Windows.Point> değerleri ve benzeri.  
  
 Anahtar çerçeve animasyonu sınıfları ait <xref:System.Windows.Media.Animation> ad alanı ve aşağıdaki adlandırma kuralını kullanır:  
  
 *\<türü >* `AnimationUsingKeyFrames`  
  
 Burada  *\<türü >* sınıfı canlandırır değer türüdür.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Aşağıdaki anahtar çerçeve animasyonu sınıflar sağlar.  
  
|Özellik türü|Karşılık gelen/to/by animasyonu sınıfı|Desteklenen ilişkilendirme yöntemleri|  
|-------------------|------------------------------------------------|-------------------------------------|  
|<xref:System.Boolean>|<xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>|Ayrık|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimationUsingKeyFrames>|Ayrık, doğrusal, eğri|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|Ayrık, doğrusal, eğri|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimationUsingKeyFrames>|Ayrık, doğrusal, eğri|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|Ayrık, doğrusal, eğri|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16AnimationUsingKeyFrames>|Ayrık, doğrusal, eğri|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32AnimationUsingKeyFrames>|Ayrık, doğrusal, eğri|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64AnimationUsingKeyFrames>|Ayrık, doğrusal, eğri|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>|Ayrık|  
|<xref:System.Object>|<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>|Ayrık|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|Ayrık, doğrusal, eğri|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames>|Ayrık, doğrusal, eğri|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>|Ayrık, doğrusal, eğri|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames>|Ayrık, doğrusal, eğri|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimationUsingKeyFrames>|Ayrık, doğrusal, eğri|  
|<xref:System.String>|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Ayrık|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>|Ayrık, doğrusal, eğri|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>|Ayrık, doğrusal, eğri|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames>|Ayrık, doğrusal, eğri|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimationUsingKeyFrames>|Ayrık, doğrusal, eğri|  
  
<a name="animation_target_values"></a>   
## <a name="target-values-key-frames-and-key-times"></a>Hedef değer (anahtar çerçeveler) ve anahtar zamanları  
 Sadece gibi farklı türlerde anahtar-çerçeve animasyonlara farklı özellik türleri animasyon ekleme, vardır ayrıca farklı türde ana kare nesne: bir animasyonlu değeri ve desteklenen ilişkilendirme yöntemi her tür. Anahtar çerçeve türleri aşağıdaki adlandırma kuralını uyar:  
  
 *\<InterpolationMethod >\<türü >* `KeyFrame`  
  
 Burada  *\<InterpolationMethod >* ilişkilendirme yöntemidir anahtar çerçeve kullanır ve  *\<türü >* sınıfı canlandırır değer türüdür. Tüm üç ilişkilendirme yöntemini destekleyen bir anahtar çerçeve animasyonu kullanabileceğiniz üç ana kare türüne sahip olacaktır. Örneğin, üç ana kare türleri ile kullanabileceğiniz bir <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>: <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>, <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>, ve <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>. (İlişkilendirme yöntemleri ayrıntılı bir sonraki bölümde açıklanmıştır.)  
  
 Belirtmek için bir anahtar kare birincil amacı olan bir <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> ve <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>. Her anahtar çerçeve türü, bu iki özelliği sağlar.  
  
-   <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> Özelliği, anahtar-çerçeve için hedef değer belirtir.  
  
-   <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> Özelliği belirtir (animasyonun içinde <xref:System.Windows.Media.Animation.Timeline.Duration%2A>) anahtar çerçevesinin <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> ulaşıldı.  
  
 Anahtar çerçeveler tarafından tanımlanan sırayla anahtar çerçeve animasyonu başladığında gezinir kendi <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> özellikleri.  
  
-   0 zamanında bir anahtar çerçeve yok ise, animasyon hedef özelliğinin geçerli değeri arasında bir geçiş oluşturur ve <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> ilk anahtar karesine; Aksi takdirde, animasyon değeri olur ilk anahtar çerçevesi değerini çıkışını.  
  
-   Animasyon arasında bir geçiş oluşturur <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> ikinci anahtar çerçevesi tarafından belirtilen ilişkilendirme yöntemini kullanarak ilk ve ikinci anahtar çerçevesi. Geçiş ilk anahtar çerçeve başlar <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> ve ne zaman sona erer ikinci anahtar çerçeve <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> ulaşıldı.  
  
-   Animasyon, sonraki her anahtar çerçeve ve önceki anahtar çerçevesi arasındaki geçişleri oluşturmaya devam eder.  
  
-   Son olarak, anahtar çerçeve ile anahtar süresi en büyük değerine animasyon geçişleri, animasyonun değerinden küçük veya ona eşit <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.  
  
 Animasyonun <xref:System.Windows.Media.Animation.Timeline.Duration%2A> olduğu <xref:System.Windows.Duration.Automatic%2A> veya kendi <xref:System.Windows.Media.Animation.Timeline.Duration%2A> son anahtar çerçeve animasyon biter saati eşittir. Aksi halde, animasyonun <xref:System.Windows.Duration> son anahtar çerçeve animasyonu tutar kadar anahtar çerçeve değere sonuna ulaşana anahtar saatten büyük, <xref:System.Windows.Duration>. Anahtar çerçeve animasyonu tüm animasyonlar gibi kullanır, <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özelliği etkin süresinin sonuna ulaştığında, son değeri tutan olup olmadığını belirlemek için. Daha fazla bilgi için [Zamanlama Davranışlarına Genel Bakış](timing-behaviors-overview.md).  
  
 Aşağıdaki örnekte <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> göstermek için önceki örnekte tanımlanan nesne nasıl <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> ve <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> özellikleri iş.  
  
-   İlk anahtar çerçevesi, hemen animasyonun çıkış değeri 0 olarak ayarlar.  
  
-   İkinci anahtar kare 0'dan için 350 canlandırır. İlk anahtar kare bittikten sonra başlar (zaman = 0 saniye) ve bitiş zamanı 2 saniye çalar, = 0:0:2.  
  
-   Üçüncü anahtar çerçevesi 50 ' 350 canlandırır. İkinci anahtar çerçevesi bittikten sonra başlar (zaman = 2 saniye) ve bitiş zamanı 5 saniye çalar, = 0:0:7.  
  
-   Dördüncü anahtar kare 50'den 200'e canlandırır. Üçüncü bir anahtar kare bittikten sonra başlar (zaman = 7 saniye) ve bitiş zamanı 1 saniye çalar = 0:0:8.  
  
-   Çünkü <xref:System.Windows.Media.Animation.Timeline.Duration%2A> animasyonun özellik, 10 saniye olarak ayarlanmıştır, animasyon, bitmeden önce iki saniye için son değerini korur. zaman = 0:0:10.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
<a name="interpolationmethods"></a>   
## <a name="interpolation-methods"></a>İlişkilendirme yöntemi  
 Bazı anahtar-çerçeve animasyonlara birden çok ilişkilendirme yöntemlerini desteklediğini önceki bölümlerde belirtilen. Animasyonun ilişkilendirme animasyon'da bu süre boyunca değerler arasında nasıl geçiş açıklar. Animasyonunuzu ile kullandığınız anahtar çerçeve türünü seçerek, o anahtar çerçeve kesimi için ilişkilendirme yöntemi tanımlayabilirsiniz. Üç farklı türde ilişkilendirme yöntemleri vardır: Doğrusal, ayrık ve eğri.  
  
### <a name="linear-interpolation"></a>Doğrusal enterpolasyon  
 Doğrusal ilişkilendirme kesim süresi sabit bir hızda animasyon ilerler. Örneğin, bir anahtar kare segment, 0 ile 10'a 5 saniye süresince geçerse, aşağıdaki değerleri belirtilen animasyon çıkarır saatler:  
  
|Zaman|Çıkış değeri|  
|----------|------------------|  
|0|0|  
|1.|2|  
|2|4|  
|3|6|  
|4|8|  
|4.25|8.5|  
|4,5|9|  
|5|10|  
  
### <a name="discrete-interpolation"></a>Ayrık ilişkilendirme  
 Ayrık ilişkilendirme animasyon işlevi bir değerden sonraki ilişkilendirme olmadan atlar. Bir anahtar kare segment, 0 ile 10'a 5 saniye süresince geçerse, animasyon belirtilen aşağıdaki değerleri çıkarır saatler:  
  
|Zaman|Çıkış değeri|  
|----------|------------------|  
|0|0|  
|1.|0|  
|2|0|  
|3|0|  
|4|0|  
|4.25|0|  
|4,5|0|  
|5|10|  
  
 Nasıl animasyon çıkış değeri kesim süresinin sonuna kadar değiştirmez dikkat edin.  
  
 Eğri ilişkilendirme daha karmaşıktır. Sonraki bölümde açıklanmıştır.  
  
<a name="anim_spline"></a>   
### <a name="splined-interpolation"></a>Eğri ilişkilendirme  
 Eğri ilişkilendirme daha gerçekçi zamanlama efektler elde etmek için kullanılabilir. Animasyonları, çoğunlukla gerçek dünyada oluşan etkileri girdiklerini taklit ederek kullanıldığından geliştiriciler denetimi hızlandırması ve nesnelerin yavaşlama ince ve zamanlama segmentlerine kapatın. Eğri anahtar çercevesi Eğri ilişkilendirme ile animasyon uygulamak etkinleştirin. Diğer anahtar çerçeveler ile belirttiğiniz bir <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> ve <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>. Eğri anahtar çerçeve ile Ayrıca, belirttiğiniz bir <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>. Aşağıdaki örnek, tek bir eğri anahtar çerçevesi için gösterir. bir <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>. Bildirim <xref:System.Windows.Media.Animation.KeySpline> eğri anahtar çerçevesi diğer anahtar çerçeveler türlerinden farklı kılan özelliği;.  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Üçüncü dereceden Bezier eğrisi bir başlangıç noktası, bir uç noktayı ve iki denetim noktası tarafından tanımlanır. <xref:System.Windows.Media.Animation.KeySpline> Eğri anahtar çerçevesi özelliğini (0,0)'dan (1,1) genişleten bir Bezier eğrisini iki denetim noktası tanımlar. Bezier eğrisini ilk yarısında faktörünü ilk denetim noktası denetler ve ikinci denetim noktası Bezier segmenti'nin ikinci yarısındaki faktörünü denetler. Sonuçta elde edilen eğrinin bu eğri anahtar kare için değişiklik oranına açıklar. Dik eğri anahtar daha hızlı çerçeve değerlerini değiştirir. Eğriyi düzleştiren alır, anahtar çerçeve değerleri daha yavaş değişir.  
  
 Kullanabileceğinize <xref:System.Windows.Media.Animation.KeySpline> su dönülüyor veya geçirmek Top gibi fiziksel eğrilerin benzetimini yapmak veya diğer "içeri Yavaşlat" ve "dışarı Yavaşlat" etkileri motion animasyonları uygulamak için. Arka plan yavaşça veya denetim düğmesi yay gibi kullanıcı etkileşimi etkileri için hızını artırın ya da belirli bir şekilde bir animasyonun değişiklik oranına yavaşlatmaz Eğri ilişkilendirme uygulanabilir.  
  
 Aşağıdaki örnek belirtir bir <xref:System.Windows.Media.Animation.KeySpline> aşağıdaki Bezier eğrisini oluşturur 0,1 1,0.  
  
 ![Bezier eğrisi](./media/graphicsmm-keyspline-0-1-1-0.png "graphicsmm_keyspline_0_1_1_0")  
Anahtar eğrisi denetim noktası (0.0, 1.0) ile ve (1.0, 0.0)  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Bu anahtar çerçeve hızlı bir şekilde ne zaman başlar, yavaşlar ve sona ermeden önce sonra yeniden hızlanır canlandırır.  
  
 Aşağıdaki örnek belirtir bir <xref:System.Windows.Media.Animation.KeySpline> aşağıdaki Bezier eğrisini oluşturur 0.5,0.25 0.75,1.0.  
  
 ![Bezier eğrisi](./media/graphicsmm-keyspline-025-050-075-10.png "graphicsmm_keyspline_025_050_075_10")  
Anahtar eğrisi denetim noktası kullanma (0.25, 0,5) ve (0,75, 1.0)  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexampleinline3)]  
  
 Bezier eğrisini eğimi çok az değiştiğinden, bu anahtar çerçeve neredeyse sabit bir oranda canlandırır; Bu, sonuna doğru biraz yavaşlatır.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> dikdörtgene animasyon ekleme için. Çünkü <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> kullanan <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> nesneler, her bir anahtar kare değeri arasındaki geçiş Eğri ilişkilendirme kullanır.  
  
 [!code-xaml[keyframes_ovw_snippet#SplinedInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#splinedinterpolationexample)]  
  
 Eğri ilişkilendirme anlamak zor olabilir; farklı ayarlarla denemek yardımcı olabilir. [Anahtar eğrisi animasyon örneği](https://go.microsoft.com/fwlink/?LinkID=160011) anahtar eğrisi değerlerini değiştirin ve üzerinde bir animasyon sonucunu görmek sağlar.  
  
<a name="combininginterpolationmethods"></a>   
### <a name="combining-interpolation-methods"></a>İlişkilendirme yöntemleri birleştirme  
 Anahtar çerçeveler ile tek anahtar çerçeve animasyonu farklı ilişkilendirme türleri kullanabilirsiniz. Farklı ilişkilendirme ile iki ana kare animasyonları birbirini izleyen, ikinci anahtar kare ilişkilendirme yöntemi geçişin ikinci ilk değeri oluşturmak için kullanılır.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> doğrusal, eğri ve ayrık ilişkilendirme kullanan oluşturulur.  
  
 [!code-xaml[keyframes_ovw_snippet#ComboInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#combointerpolationexample)]  
  
<a name="keytimes"></a>   
## <a name="more-about-duration-and-key-times"></a>Süre ve anahtar süreleri hakkında daha fazla bilgi  
 Diğer animasyonlar gibi anahtar-çerçeve animasyonlara sahip bir <xref:System.Windows.Duration> özelliği. Animasyonun belirtme yanı sıra <xref:System.Windows.Duration>, hangi kısmını bir bu süre, her anahtar çerçeveye verilen belirtmeniz gerekir. Bunu açıklayarak yapmak bir <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> her animasyonun anahtar çerçeveler. Her anahtar çerçevesinin <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> anahtar çerçeveleyen sona erdiğinde belirtir.  
  
 <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> Özellik ne kadar uygun zamanda yürütülür belirtmiyor. Bir anahtar kare oynatıldığında süreyi anahtar çerçeve sona erdiğinde, önceki anahtar çerçeve bittiğinde ve animasyonun süresini tarafından belirlenir. Bir zaman değeri, bir yüzde veya özel değerler olarak anahtar bir kez belirtilebilir <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> veya <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>.  
  
 Aşağıdaki listede, anahtar zaman belirtmenin farklı yollarını açıklar.  
  
### <a name="timespan-values"></a>TimeSpan değerleri  
 Kullanmanızı <xref:System.TimeSpan> belirtmek için değerleri bir <xref:System.Windows.Media.Animation.KeyTime>. Değer büyük veya 0'a eşit olmalıdır ve animasyonun süresini küçüktür veya eşittir. Aşağıdaki örnek, bir süresi olan bir animasyon anahtar süreleri saat değeri olarak belirtilen dört anahtar çerçeveler ile 10 saniye ve gösterir.  
  
-   İlk anahtar kare temel değerden ilk 3 bitiş zamanı saniye boyunca 100 canlandırır = 0:0:03.  
  
-   İkinci anahtar çerçevesi 100 kullanıcıdan 200'e canlandırır. İlk anahtar kare bittikten sonra başlar (zaman = 3 saniye) ve bitiş zamanı 5 saniye çalar, = 0:0:8.  
  
-   Üçüncü bir anahtar kare 200'den 500'e canlandırır. İkinci anahtar çerçevesi bittikten sonra başlar (zaman = 8 saniye) ve bitiş zamanı 1 saniye çalar = 0:0:9.  
  
-   Dördüncü anahtar kare 500'den 600 olarak canlandırır. Üçüncü bir anahtar kare bittikten sonra başlar (zaman 9 saniye =) ve bitiş zamanı 1 saniye çalar = 0:0:10.  
  
 [!code-xaml[keyframes_ovw_snippet#TimeSpanKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#timespankeytimeexample)]  
  
### <a name="percentage-values"></a>Yüzde değerleri  
 Anahtar çerçeve animasyonun bazı yüzdesiyle biten bir yüzde değeri belirtir <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], arkasından bir sayı olarak yüzde belirtin `%` simgesi. Kod içinde kullanmanız <xref:System.Windows.Media.Animation.KeyTime.FromPercent%2A> yöntemi ve bir <xref:System.Double> yüzdesini gösteren. Değer büyük veya 0'a eşit olmalıdır ve yüzde 100'değerinden küçük veya buna eşit. Aşağıdaki örnek, bir süresi olan bir animasyon 10 saniye ve yüzde olarak belirtilen anahtar süreleri dört anahtar çerçeveler gösterir.  
  
-   İlk anahtar kare temel değerden ilk 3 bitiş zamanı saniye boyunca 100 canlandırır = 0:0:3.  
  
-   İkinci anahtar çerçevesi 100 kullanıcıdan 200'e canlandırır. İlk anahtar kare bittikten sonra başlar (zaman = 3 saniye) ve bitiş zamanı 5 saniye çalar, = 0:0:8 (0,8 * 10 = 8).  
  
-   Üçüncü bir anahtar kare 200'den 500'e canlandırır. İkinci anahtar çerçevesi bittikten sonra başlar (zaman = 8 saniye) ve bitiş zamanı 1 saniye çalar = 0:0:9 (0.9 * 10 = 9).  
  
-   Dördüncü anahtar kare 500'den 600 olarak canlandırır. Üçüncü bir anahtar kare bittikten sonra başlar (zaman 9 saniye =) ve bitiş zamanı 1 saniye çalar = 0:0:10 (1 * 10 = 10).  
  
 [!code-xaml[keyframes_ovw_snippet#PercentageKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#percentagekeytimeexample)]  
  
### <a name="special-value-uniform"></a>Özel değer, Tekdüzen  
 Kullanım <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> her anahtar çerçevesinin aynı sürede almasını istediğiniz zaman.  
  
 A <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> anahtar zaman dilimlerine böler süreden eşit her anahtar çerçeve bitiş zamanı belirlemek için anahtar kare sayısı. Aşağıdaki örnek, 10 saniye süre animasyon gösterir ve anahtar süreleri dört anahtar çerçeveler olarak belirtilen <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>.  
  
-   İlk anahtar kare temel değerden ilk 2,5 bitiş zamanı saniye boyunca 100 canlandırır 0:0:2.5 =.  
  
-   İkinci anahtar çerçevesi 100 kullanıcıdan 200'e canlandırır. İlk anahtar kare bittikten sonra başlar (zaman 2.5 saniye =) ve yaklaşık 2,5 bitiş zamanı saniye çalar, = 0:0:5.  
  
-   Üçüncü bir anahtar kare 200'den 500'e canlandırır. İkinci anahtar çerçevesi bittikten sonra başlar (zaman = 5 saniye) ve bitiş zamanı 2,5 saniye çalar 0:0:7.5 =.  
  
-   Dördüncü anahtar kare 500'den 600 olarak canlandırır. İkinci anahtar çerçevesi bittikten sonra başlar (zaman = 7.5 saniye) ve bitiş zamanı 2,5 saniye çalar, = 0:0:1.  
  
 [!code-xaml[keyframes_ovw_snippet#UniformKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#uniformkeytimeexample)]  
  
### <a name="special-value-paced"></a>Hızını sizin belirlediğiniz özel değer  
 Kullanım <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> sabit bir fiyat karşılığında animasyon uygulamak istediğiniz zaman.  
  
 A <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> anahtar uzunluğu her birinin her çerçevenin süresini belirlemek için anahtar çerçeveler göre süreden ayırır.  Bu hızı veya animasyonun hızı sabit kalır davranışı sağlar.  Aşağıdaki örnek, 10 saniye süre animasyon gösterir ve anahtar süreleri üç anahtar çerçeveler olarak belirtilen <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>.  
  
 [!code-xaml[keyframes_ovw_snippet#PacedKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#pacedkeytimeexample)]  
  
 Son anahtar çerçeve anahtar kez Not <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> veya <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>, kendi çözülmüş anahtar zamanı yüzde 100 olarak ayarlanır. İlk kareli bir animasyon anahtar kare hızını sizin belirlediğiniz, kendi çözülmüş anahtar zamanı 0 olarak ayarlanır. (Kendi çözülmüş anahtar zamanı yalnızca tek bir anahtar kare anahtar çerçeve koleksiyonu içeren ve hızını sizin belirlediğiniz bir anahtar kare ise, yüzde 100 olarak ayarlanır.)  
  
 Farklı anahtar çerçeveler tek anahtar çerçeve animasyonu içinde farklı anahtar saat türleri kullanabilirsiniz.  
  
<a name="combiningkeytimes"></a>   
## <a name="combining-key-times-out-of-order-key-frames"></a>Anahtar zamanlarını birleştirme, sırası anahtar çerçeveler  
 Anahtar çerçeveler ile farklı kullanabilirsiniz <xref:System.Windows.Media.Animation.KeyTime> değer türleri aynı animasyon içerisinde. Ve anahtar çerçeveler yürütmesi gereken sırayla eklemeniz önerilir ancak gerekli değildir. Animasyon ve zamanlama sistemi sıralamaya anahtar çerçeveler çözme yeteneğine sahiptir. Anahtar çerçeveler ile geçersiz anahtar zaman yok sayılır.  
  
 Aşağıdaki listede, anahtar zaman bir anahtar-çerçeve animasyonun anahtar çercevesi için çözümlendiği yordamı açıklar.  
  
1.  Çözmek <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> değerleri.  
  
2.  Animasyonun belirlemek *toplam ilişkilendirme süre*, anahtar çerçeve animasyonu yineleme tamamlamak için gereken toplam süreyi.  
  
    1.  Animasyonun <xref:System.Windows.Media.Animation.Timeline.Duration%2A> değil <xref:System.Windows.Duration.Automatic%2A> veya <xref:System.Windows.Duration.Forever%2A>, toplam ilişkilendirme zaman animasyonun değeri <xref:System.Windows.Media.Animation.Timeline.Duration%2A> özelliği.  
  
    2.  Aksi takdirde, toplam ilişkilendirme en büyük zamandır <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> varsa anahtar çerçeveleri arasında belirtilen değeri.  
  
    3.  Aksi takdirde, toplam ilişkilendirme süresi 1 saniye arasındadır.  
  
3.  Çözümlemek için toplam ilişkilendirme zaman değerini kullanmak <xref:System.Windows.Media.Animation.KeyTimeType.Percent> <xref:System.Windows.Media.Animation.KeyTime> değerleri.  
  
4.  Önceki adımlarda zaten çözülmüş değil ise son anahtar çerçeve çözümleyin. Varsa <xref:System.Windows.Media.Animation.KeyTime> sonuncusuna anahtar çerçevesi olan <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> veya <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>, kendi çözülmüş zamanı toplam ilişkilendirme zamanına eşit olacaktır.  
  
     Varsa <xref:System.Windows.Media.Animation.KeyTime> ilk anahtar çerçevenin <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> ve bu animasyonu sahip birden fazla anahtar kasalarına çözümlemek, <xref:System.Windows.Media.Animation.KeyTime> yalnızca bir anahtar kare ise; sıfır değeri ve <xref:System.Windows.Media.Animation.KeyTime> değer <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>, toplam çözümlenmiş olmasından ilişkilendirme süresi, önceki adımda açıklandığı gibi.  
  
5.  Kalan çözmek <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> değerleri: her süreden eşit bir pay verilir.  Bu işlem sırasında çözümlenmemiş <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> değerleri geçici olarak kabul edilir <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> değerleri ve geçici olarak çözümlenen zamanı alın.  
  
6.  Çözmek <xref:System.Windows.Media.Animation.KeyTime> anahtar çerçeveler ile değerlerini çözdükten anahtar çerçeveler bunları en yakın bildirilen kullanarak anahtar zaman belirtilmeyen <xref:System.Windows.Media.Animation.KeyTime> değerleri.  
  
7.  Kalan çözmek <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> değerleri. <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> kullanma <xref:System.Windows.Media.Animation.KeyTime> anahtar komşu değerleri kullanarak çözümlenmiş zamanı belirlemek için çerçeve.  Animasyonun hızı anahtar bu çerçevenin çözümlenmiş zamanı çevresinde sabit olduğundan emin olmaktır.  
  
8.  Anahtar çerçeveler sırayla çözülen süre (birincil anahtar) ve sırasının bildirim (ikincil anahtarı), yani sıralama, çözümlenmiş anahtar çerçevesi tabanlı kullanma tutarlı bir sıralama <xref:System.Windows.Media.Animation.KeyTime> değerleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Animation.KeyTime>
- <xref:System.Windows.Media.Animation.KeySpline>
- <xref:System.Windows.Media.Animation.Timeline>
- [Anahtar eğrisi animasyon örneği](https://go.microsoft.com/fwlink/?LinkID=160011)
- [Ana kare animasyon örneği](https://go.microsoft.com/fwlink/?LinkID=160012)
- [Animasyona Genel bakış](animation-overview.md)
- [Görsel Taslaklara Genel Bakış](storyboards-overview.md)
- [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](key-frame-animation-how-to-topics.md)
- [Zamanlama Davranışlarına Genel Bakış](timing-behaviors-overview.md)
