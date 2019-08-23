---
title: Kolaylaştırıcı İşlevler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applying mathematical formulas to animations [WPF]
- applying easing functions to animations [WPF]
- mathematical formulas [WPF], applying to animations
- animations [WPF], realistic movement
- easing functions [WPF]
- customizing easing functions [WPF]
- easing functions [WPF], definition
- easing functions [WPF], customizing
- animations [WPF], applying
ms.assetid: 075b9c2b-82c4-43fa-b3cd-de0b6236eb38
ms.openlocfilehash: 72118711dfd40ad8c665157e09f01c60085db903
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965728"
---
# <a name="easing-functions"></a>Kolaylaştırıcı İşlevler
Kolaylaştırıcı işlevler, animasyonlarınız için özel matematik formülleri uygulamanıza olanak tanır. Örneğin, bir nesnenin bir yay üzerinde olmasına rağmen gerçekçi bir şekilde sıçramasını veya davranmasını isteyebilirsiniz. Bu etkileri tahmin etmek, ancak önemli miktarda iş yapmak ve animasyon matematiksel bir formül kullanmaktan daha az doğru olması için, anahtar çerçevesini veya bunlara ait/-/-by animasyonlarını kullanabilirsiniz.  
  
 ' Dan <xref:System.Windows.Media.Animation.EasingFunctionBase>devralarak kendi özel kolaylaştırıcı işlevinizi oluşturmanın yanı sıra, ortak efektler oluşturmak için çalışma zamanı tarafından sunulan birkaç kolaylaştırıcı işlevden birini kullanabilirsiniz.  
  
- <xref:System.Windows.Media.Animation.BackEase>: Bir animasyonun hareketini, belirtilen yoldaki animasyon başlamadan önce biraz daha geri çeker.  
  
- <xref:System.Windows.Media.Animation.BounceEase>: Sıçrama efekti oluşturur.  
  
- <xref:System.Windows.Media.Animation.CircleEase>: Döngüsel bir işlevi kullanarak hızlanan/veya yavaşlalayan bir animasyon oluşturur.  
  
- <xref:System.Windows.Media.Animation.CubicEase>: *F*(*t*) = *t*<sup>3</sup>formülünü kullanarak hızlanan/veya yavaşlalayan bir animasyon oluşturur.  
  
- <xref:System.Windows.Media.Animation.ElasticEase>: Rest 'e gelene kadar yay ve geri getirme durumuna benzeyen bir animasyon oluşturur.  
  
- <xref:System.Windows.Media.Animation.ExponentialEase>: Üstel bir formülü kullanarak hızlanan/veya yavaşlayan bir animasyon oluşturur.  
  
- <xref:System.Windows.Media.Animation.PowerEase>: P 'nin özelliğe<xref:System.Windows.Media.Animation.PowerEase.Power%2A> eşit olduğu *f*(*t*) = *t*<sup>p</sup> formülünü kullanarak hızlanan ve/veya yavaşlalayan bir animasyon oluşturur.  
  
- <xref:System.Windows.Media.Animation.QuadraticEase>: *F*(*t*) = *t*<sup>2</sup>formülünü kullanarak hızlanan/veya yavaşlalayan bir animasyon oluşturur.  
  
- <xref:System.Windows.Media.Animation.QuarticEase>: *F*(*t*) = *t*<sup>4</sup>formülünü kullanarak hızlanan/veya yavaşlalayan bir animasyon oluşturur.  
  
- <xref:System.Windows.Media.Animation.QuinticEase>: *F*(*t*) = *t*<sup>5</sup>formülünü kullanarak hızlanan/veya yavaşlalayan bir animasyon oluşturun.  
  
- <xref:System.Windows.Media.Animation.SineEase>: Bir sinüs formülünü kullanarak hızlanan/veya yavaşlalayan bir animasyon oluşturur.  
  
 Bir animasyona bir kolaylaştırıcı işlev uygulamak için animasyon `EasingFunction` özelliğini kullanın animasyon için uygulanacak kolaylaştırıcı işlevi belirtin. Aşağıdaki örnek, bir sıçrama <xref:System.Windows.Media.Animation.BounceEase> efekti oluşturmak için bir <xref:System.Windows.Media.Animation.DoubleAnimation> için bir kolaylaştırıcı işlev uygular.  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 Önceki örnekte, kolaylaştırıcı işlev From/To/By animasyonuna uygulandı. Bu kolaylaştırıcı işlevleri, anahtar çerçeve animasyonlarına da uygulayabilirsiniz. Aşağıdaki örnek, yukarı doğru sözleşme yapan bir dikdörtgenin animasyonunu oluşturmak için kendileriyle ilişkili kolaylaştırıcı işlevlerle anahtar çerçevelerini nasıl kullanacağınızı gösterir, yavaşlatır ve sonra da bir duruma geri rayın.  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> Özelliğini kullanarak, kolaylaştırıcı işlevin nasıl davranacağını, yani animasyonun nasıl ilişkilendirileceğini değiştirme şeklini değiştirebilirsiniz. İçin <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>verebileceğiniz üç olası değer vardır:  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Enterpolasyon, kolaylaştırıcı işlevle ilişkili matematik formülünü izler.  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseOut>: İlişkilendirme,% 100 ilişkilendirme ile kolaylaştırıcı işlevle ilişkili formülün çıkışının% ' u izler.  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: İlişkilendirme animasyonun <xref:System.Windows.Media.Animation.EasingMode.EaseIn> ilk yarısında ve <xref:System.Windows.Media.Animation.EasingMode.EaseOut> ikinci yarı için kullanılır.  
  
 Aşağıdaki grafikler, *f*(*x*) uygulamasının <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> animasyon ilerlemesini temsil ettiği farklı değerleri gösterir ve *t* süreyi temsil eder.  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![Backealıneasingmode grafikleri.](./media/backease-graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![BounceEase EasingMode grafikleri.](./media/bounceease-graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![CircleEase EasingMode grafikleri.](./media/circleease-graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![Küıease EasingMode grafikleri.](./media/cubicease-graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![Farklı easingmodes grafikleriyle ElasticEase.](./media/elasticease-graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![Farklı easingmodes 'ın üs ALease grafikleri.](./media/exponentialease-graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![Farklı easingmodes grafikleriyle Kutıa.](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![Farklı easingmodes grafikleriyle Quadratısonu](./media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![Farklı easingmodes grafikleriyle Kutıa.](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![Farklı easingmodes grafikleriyle Qubaşlatılmadı.](./media/quinticease-graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![Farklı EasingMode değerleri Için SineEase](./media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
> <xref:System.Windows.Media.Animation.PowerEase> <xref:System.Windows.Media.Animation.CubicEase> Özelliğinikullanarak<xref:System.Windows.Media.Animation.QuarticEase>, ,,<xref:System.Windows.Media.Animation.QuinticEase> ve ile aynı davranışı oluşturmak için kullanabilirsiniz. <xref:System.Windows.Media.Animation.QuadraticEase> <xref:System.Windows.Media.Animation.PowerEase.Power%2A> Örneğin, <xref:System.Windows.Media.Animation.PowerEase> <xref:System.Windows.Media.Animation.PowerEase.Power%2A> yerine koymak için kullanmak istiyorsanız ,3değerinibelirtin.<xref:System.Windows.Media.Animation.CubicEase>  
  
 Çalışma zamanında dahil olan kolaylaştırıcı işlevleri kullanmanın yanı sıra, ' dan <xref:System.Windows.Media.Animation.EasingFunctionBase>devralarak kendi özel kolaylaştırıcı işlevlerinizi de oluşturabilirsiniz. Aşağıdaki örnek, basit bir özel kolaylaştırıcı işlevin nasıl oluşturulacağını göstermektedir. <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> Yöntemini geçersiz kılarak kolaylaştırıcı işlevin nasıl davrandığı için kendi matematik mantığınızı ekleyebilirsiniz.   
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
