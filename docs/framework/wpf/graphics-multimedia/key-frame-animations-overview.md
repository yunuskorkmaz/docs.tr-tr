---
title: "Anahtar-Çerçeve Animasyonlara Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], key-frame
- key frames [WPF], about key-frame animations
- multiple animation target values [WPF]
ms.assetid: 10028f97-bb63-41fc-b8ad-663dac7ea203
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 38f0f6ac030af08039438b7e766c3f0f5bed7534
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="key-frame-animations-overview"></a>Anahtar-Çerçeve Animasyonlara Genel Bakış
Bu konu anahtarı çerçeve animasyonlarını tanıtır. Anahtar çerçeve animasyonları ikiden fazla hedef değerleri kullanarak animasyon olanak sağlar ve animasyonun ilişkilendirme metodunu denetleyebilirsiniz.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu genel bakışta anlamak için aşina olmalısınız [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] animasyonları ve zamanlamaları. Animasyon giriş için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Ayrıca From/To/By animasyonlarını da tanımanıza yardımcı olabilir. Daha fazla bilgi için bkz: u animasyonları genel bakış.  
  
<a name="whatisakeyframeanimation"></a>   
## <a name="what-is-a-key-frame-animation"></a>Bir anahtar çerçeve animasyonu nedir?  
 Gibi bir From/To/By animasyon, anahtar çerçeve animasyonu canlandırır hedef özelliğinin değeri. Hedef değerleri arasında geçişi üzerinden oluşturur, <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Ancak, while From/To/By animasyon iki değer arasında bir geçiş oluşturur, tek bir anahtar çerçeve animasyonu herhangi bir sayıda hedef değerler arasında geçiş oluşturabilirsiniz. From/To/By aksine animasyon anahtar çerçeve animasyonu hiçbir kaynak veya hedef değerlerini ayarlamak özellikleri tarafından sahiptir. Bir anahtar çerçeve animasyonun hedef değerleri anahtar çerçeveleri nesneleri kullanarak açıklanan (Bu nedenle bir terim, "anahtar çerçeve animasyonu"). Animasyonun hedef değerleri belirtmek için anahtar çerçeve nesneleri oluşturmak ve bunları animasyonun Ekle <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> koleksiyonu. Animasyonu çalıştırdığında, belirttiğiniz çerçeveler arasında geçiş yapar.  
  
 Birden çok hedef değerler'ı desteklemenin yanında bazı anahtar çerçeve yöntemleri bile birden çok ilişkilendirme yöntemleri destekler. Animasyonun ilişkilendirme yöntemini nasıl bir değerden sonrakine geçmeden tanımlar. İlişkilendirme üç tür vardır: ayrık, doğrusal ve eğri.  
  
 Bir anahtar çerçeve animasyonu ile animasyon eklemek için aşağıdaki adımları tamamlayın.  
  
-   Animasyonu bildirin ve belirtin, <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, bir from/to/by animasyon için gibi.  
  
-   Her bir hedef değer için uygun türde anahtar çerçevesi oluşturun, değerini ayarlayın ve <xref:System.Windows.Media.Animation.KeyTime>, animasyonun ekleyin <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> koleksiyonu.  
  
-   Tıpkı bir From/To/By ile olduğu gibi bir özellik, animasyon ilişkilendirmek animasyon. Film şeridi kullanarak bir özelliğe bir animasyon uygulama hakkında daha fazla bilgi için bkz: [film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> animasyon uygulamak için bir <xref:System.Windows.Shapes.Rectangle> dört farklı konumlara öğesi.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
 Gibi bir From/To/By animasyon kullanarak bir özellik için bir anahtar çerçeve animasyonu uygulanabilir bir <xref:System.Windows.Media.Animation.Storyboard> biçimlendirme ve kodun veya kullanarak <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> kodda yöntemi. Bir anahtar çerçeve animasyon oluşturmak için kullanabilir bir <xref:System.Windows.Media.Animation.AnimationClock> ve bir veya daha fazla özellikleri için geçerlidir. Animasyonları uygulamak için farklı yöntemler hakkında daha fazla bilgi için bkz: [özellik Animasyon Tekniklerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
<a name="animation_types"></a>   
## <a name="key-frame-animation-types"></a>Anahtar çerçeve animasyon türleri  
 Animasyon özellik değerleri oluşturması nedeniyle farklı özellik türleri için farklı animasyon türü vardır. Alan bir özelliği animasyon uygulamak için bir <xref:System.Double> (bir öğenin gibi <xref:System.Windows.FrameworkElement.Width%2A> özelliği), üreten bir animasyon kullandığınız <xref:System.Double> değerleri. Alan bir özelliği animasyon uygulamak için bir <xref:System.Windows.Point>, üreten bir animasyon kullandığınız <xref:System.Windows.Point> değerleri ve benzeri.  
  
 Anahtar çerçeve animasyon sınıfları ait <xref:System.Windows.Media.Animation> ad alanı ve aşağıdaki adlandırma kuralını uyar:  
  
 *\<Tür >*`AnimationUsingKeyFrames`  
  
 Burada  *\<türü >* sınıfı canlandırır değer türüdür.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Aşağıdaki anahtar çerçeve animasyon sınıfları sağlar.  
  
|Özellik türü|Karşılık gelen from/to/by animasyon sınıfı|Desteklenen ilişkilendirme yöntemleri|  
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
 Yalnızca bulunduğundan farklı türdeki farklı özellik türleri animasyon için anahtar çerçeve animasyonları, ayrıca farklı tür vardır anahtar çerçeve nesneleri: her tür animasyonlu değeri ve desteklenen ilişkilendirme yöntemi için bir tane. Anahtar çerçeve türleri aşağıdaki adlandırma kuralını uyar:  
  
 *\<InterpolationMethod >\<türü >*`KeyFrame`  
  
 Burada  *\<InterpolationMethod >* anahtar çerçevesinin kullandığı ilişkilendirme yöntemidir ve  *\<türü >* sınıfı canlandırır değer türüdür. Tüm üç ilişkilendirme yöntemini destekleyen bir anahtar çerçeve animasyonu kullanabileceğiniz üç anahtar çerçeve türüne sahip olacaktır. Örneğin, üç anahtar çerçeve türleri ile kullanabileceğiniz bir <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>: <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>, <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>, ve <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>. (İlişkilendirme yöntemleri sonraki bölümünde ayrıntılı olarak açıklanmıştır.)  
  
 Belirtmek için bir anahtar çerçevesinin birincil amacı olan bir <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> ve <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>. Her anahtar çerçevesi türü bu iki özellik sağlar.  
  
-   <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> Özelliği, bu anahtar çerçeve hedef değerini belirtir.  
  
-   <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> Özellik belirtir (animasyonun içinde <xref:System.Windows.Media.Animation.Timeline.Duration%2A>) anahtar çerçevesinin <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> ulaşıldı.  
  
 Bir anahtar çerçeve animasyonu başladığında, anahtar çerçeveleri tarafından tanımlanan sırayla dolaşır kendi <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> özellikleri.  
  
-   0 zamanında hiçbir anahtar çerçevesi ise, animasyon hedef özelliğin geçerli değeri arasında bir geçiş oluşturur ve <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> ilk anahtar çerçevenin; değeri olur ilk anahtar çerçevesi değeri animasyonun Aksi takdirde, çıktı.  
  
-   Animasyon arasında bir geçiş oluşturur <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> ikinci anahtar çerçevesi tarafından belirlenen ilişkilendirme yöntemini kullanarak ilk ve ikinci anahtar çerçevesi. Geçiş ilk anahtar çerçevesinin başlatır <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> ve ne zaman sona erer ikinci anahtar çerçevesinin <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> ulaşıldı.  
  
-   Animasyon, izleyen her anahtar çerçevesi ve önceki anahtar çerçevesi arasında geçişler oluşturmaya devam eder.  
  
-   Son olarak, anahtar süresi en büyük olan anahtar çerçevesi değerine animasyon geçişlerini olan eşit veya bundan küçük animasyonun <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.  
  
 Varsa animasyonun <xref:System.Windows.Media.Animation.Timeline.Duration%2A> olan <xref:System.Windows.Duration.Automatic%2A> veya kendi <xref:System.Windows.Media.Animation.Timeline.Duration%2A> son anahtar çerçevesinin animasyon biter zamana eşit. Aksi halde, eğer animasyonun <xref:System.Windows.Duration> son anahtar çerçeve, bu kadar anahtar çerçeve değerini sonuna ulaştığında animasyon ayrı tutma anahtar saatten büyük, <xref:System.Windows.Duration>. Tüm animasyon gibi anahtar çerçeve animasyonu kullanır, <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> etkin süresinin sonuna ulaştığında, son değeri kalıp kalmadığını belirlemek amacıyla özelliği. Daha fazla bilgi için bkz: [Zamanlama Davranışlarına Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md).  
  
 Aşağıdaki örnek kullanır <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> göstermek için önceki örnekte tanımlanan nesne nasıl <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> ve <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> özellikleri çalışma.  
  
-   İlk anahtar çerçevesi, hemen animasyonun çıkış değerini 0 olarak ayarlar.  
  
-   İkinci anahtar çerçevesi 350 için 0'dan canlandırır. İlk anahtar çerçevesi bittikten sonra başlar (aynı anda = 0 saniye) ve 2 bitiş zamanı saniye çalar = 0:0:2.  
  
-   Üçüncü anahtar çerçevesi 350 50'ye canlandırır. İkinci anahtar çerçevesi bittikten sonra başlar (aynı anda = 2 saniye) ve bitiş zamanı 5 saniye çalar = 0:0:7.  
  
-   Dördüncü anahtar çerçevesi 200'e 50'den canlandırır. Üçüncü anahtar çerçevesi bittikten sonra başlar (aynı anda = 7 saniye) ve bitiş zamanı 1 saniye çalar = 0:0:8.  
  
-   Çünkü <xref:System.Windows.Media.Animation.Timeline.Duration%2A> animasyonun özelliğini 10 saniye olarak ayarlandığından, animasyonun bitmeden önce iki saniye için son değeri tutan zaman = 0:0:10.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
<a name="interpolationmethods"></a>   
## <a name="interpolation-methods"></a>İlişkilendirme yöntemleri  
 Önceki bölümlerde bazı anahtar çerçeve animasyonları birden çok ilişkilendirme yöntemi desteklediği belirtilmişti. Animasyonun ilişkilendirme animasyon süresi boyunca değerler arasında nasıl geçiş açıklar. Animasyon ile kullandığınız anahtar çerçeve türünü seçerek, o anahtar çerçeve kesimi için ilişkilendirme yöntemi tanımlayabilirsiniz. Üç farklı türde ilişkilendirme yöntemleri vardır: Doğrusal, ayrık ve eğri.  
  
### <a name="linear-interpolation"></a>Doğrusal ilişkilendirme  
 Doğrusal ilişkilendirme animasyon ilerler bir sabit kesim süresi. Örneğin, bir anahtar çerçevesi kesimi 0 ile 10 5 saniye süresince geçerse, animasyon aşağıdaki değerleri belirtilen çıkarır saatleri:  
  
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
 Ayrık ilişkilendirme animasyon işlevi bir değerden sonrakine ilişkilendirme olmadan atlar. Bir anahtar çerçevesi kesimi 0 ile 10 5 saniye süresince geçerse, animasyon aşağıdaki değerleri belirtilen çıkış saatleri:  
  
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
  
 Nasıl animasyonun çıkış değerini kesim süresinin sonuna kadar değiştirmez dikkat edin.  
  
 Eğri ilişkilendirme daha karmaşıktır. Sonraki bölümde açıklanmıştır.  
  
<a name="anim_spline"></a>   
### <a name="splined-interpolation"></a>Eğri ilişkilendirme  
 Eğri ilişkilendirme daha gerçekçi zamanlama efektleri elde etmek için kullanılabilir. Animasyon kadar sık gerçek dünyada gerçekleşen efektleri benzetmek için kullanıldığından, geliştiricilerin hızlandırma denetimini ve nesnelerin yavaşlama ince ve zamanlama segmentlerine kapatın. Eğri anahtar çerçeveleri Eğri ilişkilendirme animasyon olanak sağlar. Belirttiğiniz anahtar diğer çerçeveler ile bir <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> ve <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>. Eğri anahtar çerçevesi ile da belirttiğiniz bir <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>. Tek bir eğri anahtar çerçevesi için aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>. Bildirim <xref:System.Windows.Media.Animation.KeySpline> eğri anahtar çerçevesi anahtar çerçeveler diğer türlerinden farklı kılan özelliği;.  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Küp Bezier eğrisi bir başlangıç noktası, bitiş noktası ve iki denetim noktaları tarafından tanımlanır. <xref:System.Windows.Media.Animation.KeySpline> Eğri anahtar çerçevesi özelliği (0,0)'dan (1,1) genişleten bir Bezier eğrisini iki denetim noktası tanımlar. Bezier eğrisini ilk yarısı eğri faktörü ilk denetim noktası denetler ve ikinci denetim noktası Bezier segment ikinci yarısında faktörünü denetler. Sonuçta elde edilen eğri bu eğri anahtar çerçevesini değişim oranı açıklar. Dik eğri o kadar hızlı anahtar çerçevesi değerlerini değiştirir. Eğriyi daha düz alır, anahtar çerçevesi değerlerini daha yavaş değişir.  
  
 Kullanabileceğinize <xref:System.Windows.Media.Animation.KeySpline> su dönmeden veya geçirmek Top gibi fiziksel eğrilerin benzetimini yapmak veya diğer "içinde kolaylaştırır" ve "out kolaylaştırır" efektlerini hareket animasyonlarına uygulamak için. Arka plan silinmeleri veya denetim düğmesi yay gibi kullanıcı etkileşim efektleri için hızlandırma veya animasyonun değişme oranı aşağı belirli bir şekilde yavaş Eğri ilişkilendirme uygulanabilir.  
  
 Aşağıdaki örnek belirtir bir <xref:System.Windows.Media.Animation.KeySpline> aşağıdaki Bezier eğrisini oluşturan 0,1 1,0 biri.  
  
 ![Bezier eğrisi](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyspline-0-1-1-0.png "graphicsmm_keyspline_0_1_1_0")  
Anahtar eğrisi denetim noktaları (0.0, 1.0) ile ve (1.0, 0.0)  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Bu anahtar çerçeve hızlı bir şekilde ne zaman başlar, yavaşlar ve onu sona ermeden önce sonra yeniden hızlanır canlandırır.  
  
 Aşağıdaki örnek belirtir bir <xref:System.Windows.Media.Animation.KeySpline> aşağıdaki Bezier eğrisini oluşturan 0.5,0.25 0.75,1.0.  
  
 ![Bezier eğrisi](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyspline-025-050-075-10.png "graphicsmm_keyspline_025_050_075_10")  
Anahtar eğrisi denetim noktaları (0.25, 0,5) ve (0,75, 1.0)  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexampleinline3)]  
  
 Bezier eğrisini eğimi çok az değiştiğinden, bu anahtar çerçeve neredeyse sabit bir oranda canlandırır; Bunu kendi sonuna doğru biraz yavaşlatır.  
  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> dikdörtgen konumunu hareketli hale getirmeyi için. Çünkü <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> kullanan <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> nesneleri, her anahtar çerçeve değeri arasında geçiş Eğri ilişkilendirme kullanır.  
  
 [!code-xaml[keyframes_ovw_snippet#SplinedInterpolationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#splinedinterpolationexample)]  
  
 Eğri ilişkilendirme anlaşılması zor olabilir; farklı ayarlarla denemek yardımcı olabilir. [Anahtar eğri animasyon örneği](http://go.microsoft.com/fwlink/?LinkID=160011) anahtar eğri değerleri değiştirmek ve bir animasyon sonucunu görmenizi sağlar.  
  
<a name="combininginterpolationmethods"></a>   
### <a name="combining-interpolation-methods"></a>İlişkilendirme yöntemleri birleştirme  
 Farklı ilişkilendirme türleriyle tek anahtar çerçeve animasyon ana kare kullanabilirsiniz. Farklı ilişkilendirmeye sahip iki anahtar çerçeve animasyonları birbirini izlediğinde, ikinci anahtar çerçevesi ilişkilendirme yöntemi geçiş ilk değeri ikinci oluşturmak için kullanılır.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> bu kullanan doğrusal, eğri ve ayrık ilişkilendirme oluşturulur.  
  
 [!code-xaml[keyframes_ovw_snippet#ComboInterpolationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#combointerpolationexample)]  
  
<a name="keytimes"></a>   
## <a name="more-about-duration-and-key-times"></a>Süre ve anahtar süreleri hakkında daha fazla bilgi  
 Diğer animasyonları gibi anahtar çerçeve animasyonları sahip bir <xref:System.Windows.Duration> özelliği. Animasyonun belirtme yanı sıra <xref:System.Windows.Duration>, her anahtar çerçeveye sürenin hangi bölümünü verilen belirtmeniz gerekir. Açıklayarak bunu bir <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> her animasyonun anahtar çerçevesi. Her anahtar çerçevesinin <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> ne zaman sona ereceğini o anahtar çerçevenin belirtir.  
  
 <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> Özelliği anahtar süresinin ne kadar süreyle oynadığı belirtmiyor. Anahtar çerçevesi oynadığı süreyi anahtar çerçevesi sona erdiğinde, önceki anahtar çerçevenin ne zaman sona erdi ve animasyonun süresi tarafından belirlenir. Anahtar zaman zaman değeri, bir yüzde veya özel değerler olarak belirtilebilir <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> veya <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>.  
  
 Aşağıdaki listede anahtar sürelerini belirtmek farklı yolları açıklanmaktadır.  
  
### <a name="timespan-values"></a>TimeSpan değerleri  
 Kullanabilirsiniz <xref:System.TimeSpan> belirtmek için değerleri bir <xref:System.Windows.Media.Animation.KeyTime>. Değer sıfırdan büyük veya 0 değerine eşit olmalıdır ve animasyonun süresini küçük veya buna eşit. Aşağıdaki örnek bir animasyon süresi 10 saniye ve anahtar süreleri saat değeri olarak belirtilen dört ana kare gösterir.  
  
-   İlk 3 bitiş zamanı saniye, üzerinden ilk anahtar çerçevesi temel değerden 100 canlandırır = 0:0:03.  
  
-   İkinci anahtar çerçevesi 100 ila 200'e canlandırır. İlk anahtar çerçevesi bittikten sonra başlar (aynı anda = 3 saniye) ve bitiş zamanı 5 saniye çalar = 0:0:8.  
  
-   Üçüncü anahtar çerçevesi 200'den 500'e canlandırır. İkinci anahtar çerçevesi bittikten sonra başlar (aynı anda = 8 saniye) ve bitiş zamanı 1 saniye çalar = 0:0:9.  
  
-   Dördüncü anahtar çerçevesi 500'den 600 olarak canlandırır. Üçüncü anahtar çerçevesi bittikten sonra başlar (aynı anda = 9 saniye) ve bitiş zamanı 1 saniye çalar = 0:0:10.  
  
 [!code-xaml[keyframes_ovw_snippet#TimeSpanKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#timespankeytimeexample)]  
  
### <a name="percentage-values"></a>Yüzde değerleri  
 Bir yüzde değeri anahtar çerçevesi animasyonun bazı yüzdesiyle sona ereceğini belirten <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], arkasından bir sayı olarak yüzdesini belirtin `%` simgesi. Kodda, kullandığınız <xref:System.Windows.Media.Animation.KeyTime.FromPercent%2A> yöntemi ve bu geçirin bir <xref:System.Double> yüzdeyi gösteren. Değer sıfırdan büyük veya 0 değerine eşit olmalıdır ve yüzde 100'den küçük veya buna eşit. Aşağıdaki örnek bir animasyon süresi 10 saniye ve anahtar süreleri yüzde olarak belirtilen dört ana kare gösterir.  
  
-   İlk 3 bitiş zamanı saniye, üzerinden ilk anahtar çerçevesi temel değerden 100 canlandırır = 0:0:3.  
  
-   İkinci anahtar çerçevesi 100 ila 200'e canlandırır. İlk anahtar çerçevesi bittikten sonra başlar (aynı anda = 3 saniye) ve bitiş zamanı 5 saniye çalar = 0:0:8 (0,8 * 10 = 8).  
  
-   Üçüncü anahtar çerçevesi 200'den 500'e canlandırır. İkinci anahtar çerçevesi bittikten sonra başlar (aynı anda = 8 saniye) ve bitiş zamanı 1 saniye çalar = 0:0:9 (0.9 * 10 = 9).  
  
-   Dördüncü anahtar çerçevesi 500'den 600 olarak canlandırır. Üçüncü anahtar çerçevesi bittikten sonra başlar (aynı anda = 9 saniye) ve bitiş zamanı 1 saniye çalar = 0:0:10 (1 * 10 = 10).  
  
 [!code-xaml[keyframes_ovw_snippet#PercentageKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#percentagekeytimeexample)]  
  
### <a name="special-value-uniform"></a>Özel değer, Tekdüzen  
 Kullanım <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> her anahtar çerçevesinin aynı miktarda süre almasını istediğiniz zaman.  
  
 A <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> anahtar zaman böler kullanılabilir zamanı eşit olarak her anahtar çerçeve bitiş zamanını belirlemek için anahtar çerçeve sayısına göre. Aşağıdaki örnek, bir animasyon süresi 10 saniye ile gösterir ve anahtar süreleri dört ana kare olarak belirtilen <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>.  
  
-   İlk 2.5 bitiş zamanı saniye içinde ilk anahtar çerçevesi temel değerden 100 canlandırır 0:0:2.5 =.  
  
-   İkinci anahtar çerçevesi 100 ila 200'e canlandırır. İlk anahtar çerçevesi bittikten sonra başlar (aynı anda 2.5 saniye =) ve yaklaşık 2,5 bitiş zamanı saniye çalar = 0:0:5.  
  
-   Üçüncü anahtar çerçevesi 200'den 500'e canlandırır. İkinci anahtar çerçevesi bittikten sonra başlar (aynı anda = 5 saniye) ve bitiş zamanı 2.5 saniye çalar 0:0:7.5 =.  
  
-   Dördüncü anahtar çerçevesi 500'den 600 olarak canlandırır. İkinci anahtar çerçevesi bittikten sonra başlar (aynı anda = 7.5 saniye) ve bitiş zamanı 2.5 saniye çalar = 0:0:1.  
  
 [!code-xaml[keyframes_ovw_snippet#UniformKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#uniformkeytimeexample)]  
  
### <a name="special-value-paced"></a>Özel değer, hızını belirleyebileceği  
 Kullanım <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> sabit bir oranda animasyon uygulamak istediğinizde zamanlama.  
  
 A <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> anahtar zamanı kullanılabilir zamanı her her çerçevenin süresini belirlemek için anahtar çerçeve uzunluğunu göre ayırır.  Bu hız veya animasyonun hızını sabit kalır davranış sağlar.  Aşağıdaki örnek, bir animasyon süresi 10 saniye ile gösterir ve anahtar süreleri üç ana kare olarak belirtilen <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>.  
  
 [!code-xaml[keyframes_ovw_snippet#PacedKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#pacedkeytimeexample)]  
  
 Son anahtar çerçevesinin anahtar saat ise, Not <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> veya <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>, kendi çözülmüş anahtar zamanı yüzde 100'e ayarlanır. İlk anahtar çerçevesi kareli animasyonda hızını belirleyebileceği, kendi çözülmüş anahtar zamanı 0 olarak ayarlanır. (Kendi çözülmüş anahtar zamanı anahtar çerçeve koleksiyonu yalnızca tek bir anahtar çerçeve içerir ve uygulanan bir anahtar çerçeve ise, yüzde 100'e ayarlanır.)  
  
 Tek anahtar çerçeve animasyonu içindeki farklı anahtar çerçeveler farklı anahtar zaman türleri kullanabilir.  
  
<a name="combiningkeytimes"></a>   
## <a name="combining-key-times-out-of-order-key-frames"></a>Anahtar zamanlarını birleştirme, sipariş anahtar çerçeveleri  
 Farklı anahtar çerçevelerini kullanabilirsiniz <xref:System.Windows.Media.Animation.KeyTime> değer türleri aynı animasyonda. Ve yürütmesi gereken sırayla anahtar çerçeveleri ekleyin önerilir ancak gerekli değildir. Animasyon ve zamanlama sistemi bozuk anahtar çerçeveleri çözme yeteneğine sahiptir. Geçersiz anahtar sürelerine sahip anahtar çerçeveler göz ardı edilir.  
  
 Aşağıdaki liste, anahtar süreleri için bir anahtar çerçeve animasyonunun anahtar çerçevelerinin çözümlendiği yordamı açıklar.  
  
1.  Gidermek <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> değerleri.  
  
2.  Animasyonun belirlemek *toplam ilişkilendirme süre*, anahtar çerçeve animasyon ileriye doğru yineleme tamamlamak için geçen toplam süreyi.  
  
    1.  Varsa animasyonun <xref:System.Windows.Media.Animation.Timeline.Duration%2A> değil <xref:System.Windows.Duration.Automatic%2A> veya <xref:System.Windows.Duration.Forever%2A>, toplam ilişkilendirme zamanı animasyonun değeri <xref:System.Windows.Media.Animation.Timeline.Duration%2A> özelliği.  
  
    2.  Aksi takdirde, toplam ilişkilendirme zamanı en büyük değer <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> varsa anahtar çerçeveleri arasındaki, belirtilen değeri.  
  
    3.  Aksi takdirde, toplam ilişkilendirme zamanı 1 saniyedir.  
  
3.  Gidermek için toplam ilişkilendirme zaman değerini kullanın <xref:System.Windows.Media.Animation.KeyTimeType.Percent> <xref:System.Windows.Media.Animation.KeyTime> değerleri.  
  
4.  Önceki adımlarda zaten çözülmüş değil ise son anahtar çerçeveyi çözümleyin. Varsa <xref:System.Windows.Media.Animation.KeyTime> son anahtar dilimidir <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> veya <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>, kendi çözülmüş zamanı toplam ilişkilendirme zamanına eşit olacaktır.  
  
     Varsa <xref:System.Windows.Media.Animation.KeyTime> ilk anahtar çerçevenin <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> ve bu animasyon sahip birden fazla anahtar çerçevesine çözmek kendi <xref:System.Windows.Media.Animation.KeyTime> değeri sıfır olarak; yalnızca bir anahtar çerçevesi ise ve kendi <xref:System.Windows.Media.Animation.KeyTime> değer <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>, toplam çözümlendiği Önceki adımda açıklandığı gibi ilişkilendirme zamanı.  
  
5.  Kalan gidermek <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> değerleri: her kullanılabilir zamanı eşit bir pay verilir.  Bu işlem sırasında çözümlenmemiş <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> değerleri geçici olarak kabul edilir <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> değerleri ve geçici bir çözümlenen zamanı alın.  
  
6.  Gidermek <xref:System.Windows.Media.Animation.KeyTime> anahtar çerçeveler ile değerlerini çözdükten anahtar çerçeveler bunları en yakın bildirilen kullanarak anahtar süreleri belirtilmeyen <xref:System.Windows.Media.Animation.KeyTime> değerleri.  
  
7.  Kalan gidermek <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> değerleri. <xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime> kullanmak <xref:System.Windows.Media.Animation.KeyTime> anahtar komşu değerleri kullanarak çözümlenmiş zamanı belirlemek için çerçeve.  Animasyon hızı bu anahtar çerçevesinin çözümlenmiş zamanı çevresinde sabit olduğundan emin olmak için hedeftir.  
  
8.  Çözümlenmiş zamanı (birincil anahtar) sırasını ve bildirim (ikincil anahtar), sırasına göre ana kare yani sıralamak için tutarlı bir sıralama kullanım tabanlı çözümlenmiş anahtar çerçevesi <xref:System.Windows.Media.Animation.KeyTime> değerleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Animation.KeyTime>  
 <xref:System.Windows.Media.Animation.KeySpline>  
 <xref:System.Windows.Media.Animation.Timeline>  
 [Anahtar eğri animasyon örneği](http://go.microsoft.com/fwlink/?LinkID=160011)  
 [Ana kare animasyon örneği](http://go.microsoft.com/fwlink/?LinkID=160012)  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Görsel Taslaklara Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)  
 [Zamanlama Davranışlarına Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)
