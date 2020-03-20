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
ms.openlocfilehash: a25bde5098af853c3906a174a189fc35f33f0525
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186493"
---
# <a name="easing-functions"></a>Kolaylaştırıcı İşlevler
Kolaylaştırma işlevleri animasyonlarınıza özel matematiksel formüller uygulamanızı sağlar. Örneğin, bir nesnenin gerçekçi bir şekilde sıçramasını veya bir yay üzerindeymiş gibi gibi gibi bir şekilde gibi bir şekilde Bu efektleri yaklaşık olarak belirlemek için Anahtar Çerçeve'yi ve hatta Gelen/To/By animasyonlarını kullanabilirsiniz, ancak önemli miktarda çalışma gerekir ve animasyon matematiksel bir formül kullanmaktan daha az doğru olacaktır.  
  
 Devralarak kendi özel kolaylaştırma işlevi <xref:System.Windows.Media.Animation.EasingFunctionBase>oluşturmanın yanı sıra, ortak efektler oluşturmak için çalışma zamanı tarafından sağlanan birkaç kolaylaştırma işlevlerinden birini kullanabilirsiniz.  
  
- <xref:System.Windows.Media.Animation.BackEase>: Bir animasyonun hareketini, belirtilen yolda canlandırmaya başlamadan biraz önce geri çekilir.  
  
- <xref:System.Windows.Media.Animation.BounceEase>: Zıplayan bir etki yaratır.  
  
- <xref:System.Windows.Media.Animation.CircleEase>: Dairesel bir fonksiyon kullanarak hızlandıran ve/veya yavaşlayan bir animasyon oluşturur.  
  
- <xref:System.Windows.Media.Animation.CubicEase>: *F*(*t*) = *t*<sup>3</sup>formüllerini kullanarak hızlandıran ve/veya yavaşlayan bir animasyon oluşturur.  
  
- <xref:System.Windows.Media.Animation.ElasticEase>: Dinlenmeye gelene kadar ileri geri salınım yapan bir yayı andıran bir animasyon oluşturur.  
  
- <xref:System.Windows.Media.Animation.ExponentialEase>: Üstel bir formül kullanarak hızlandıran ve/veya yavaşlayan bir animasyon oluşturur.  
  
- <xref:System.Windows.Media.Animation.PowerEase>: <xref:System.Windows.Media.Animation.PowerEase.Power%2A> *P'nin*özelliğe eşit olduğu f (*t*) = *t*<sup>p</sup> formüllerini kullanarak hızlandıran ve/veya yavaşlayan bir animasyon oluşturur.  
  
- <xref:System.Windows.Media.Animation.QuadraticEase>: *F*(*t*) = *t*<sup>2</sup>formüllerini kullanarak hızlandıran ve/veya yavaşlayan bir animasyon oluşturur.  
  
- <xref:System.Windows.Media.Animation.QuarticEase>: *F*(*t*) = *t*<sup>4</sup>formüllerini kullanarak hızlandıran ve/veya yavaşlayan bir animasyon oluşturur.  
  
- <xref:System.Windows.Media.Animation.QuinticEase>: *F*(*t*) = *t*<sup>5</sup>formüllerini kullanarak hızlandıran ve/veya yavaşlayan bir animasyon oluşturun.  
  
- <xref:System.Windows.Media.Animation.SineEase>: Sinüs formülü kullanarak hızlandıran ve/veya yavaşlayan bir animasyon oluşturur.  
  
 Animasyona kolaylaştırma işlevi uygulamak için `EasingFunction` animasyonun özelliğini kullanın animasyona uygulamak için kolaylaştırma işlevini belirtin. Aşağıdaki örnek, zıplayan bir <xref:System.Windows.Media.Animation.BounceEase> <xref:System.Windows.Media.Animation.DoubleAnimation> etki oluşturmak için a'ya bir kolaylaştırma işlevi uygular.  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 Önceki örnekte, kolaylaştırma işlevi Bir Gelen/To/By animasyonuna uygulanmıştır. Bu kolaylaştırma işlevlerini Anahtar Kare animasyonlarına da uygulayabilirsiniz. Aşağıdaki örnek, yukarı doğru küçülen, yavaşlayan, sonra aşağı doğru genişleyen (düşüyormuş gibi) ve sonra bir durağa seken bir dikdörtgenin animasyonu oluşturmak için kendileriyle ilişkili kolaylaştırma işlevlerine sahip anahtar çerçevelerin nasıl kullanılacağını gösterir.  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 Özelliği, kolaylaştırma işlevinin nasıl çalıştığını değiştirmek, diğer bir şekilde animasyonun enterpolasyonunu değiştirmek için kullanabilirsiniz. <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> Verebileceğiniz <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>üç olası değer vardır:  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Enterpolasyon, kolaylaştırma fonksiyonu ile ilişkili matematiksel formülü izler.  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Enterpolasyon, kolaylaştırma fonksiyonu ile ilişkili formülün çıktısını eksi %100 enterpolasyon izler.  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Enterpolasyon animasyonun ilk yarısı <xref:System.Windows.Media.Animation.EasingMode.EaseOut> ve ikinci yarısı için kullanır. <xref:System.Windows.Media.Animation.EasingMode.EaseIn>  
  
 Aşağıdaki *grafikler, f*( <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> *x*) animasyon ilerlemesini ve *t'nin* zamanı temsil ettiği yerin farklı değerlerini gösterir.  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![BackEase EasingMode grafikleri.](./media/backease-graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![BounceEase EasingMode grafikleri.](./media/bounceease-graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![CircleEase EasingMode grafikleri.](./media/circleease-graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![CubicEase EasingMode grafikleri.](./media/cubicease-graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![ElasticEase farklı kolaylaştırma modları grafikleri ile.](./media/elasticease-graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![Farklı kolaylaştırma modlarının üstelEase grafikleri.](./media/exponentialease-graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![QuarticFarklı kolaylaştırma modları grafikleri ile kolaylaş.](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![Farklı kolaylaştırma modlarının grafikleri ile QuadraticEase](./media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![QuarticFarklı kolaylaştırma modları grafikleri ile kolaylaş.](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![Farklı kolaylaştırma modları grafikleri ile QuinticEase.](./media/quinticease-graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![Farklı EasingMode değerleri için SineEase](./media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
> <xref:System.Windows.Media.Animation.CubicEase>Aynı davranışı <xref:System.Windows.Media.Animation.PowerEase> oluşturmak için kullanabilirsiniz <xref:System.Windows.Media.Animation.QuadraticEase> <xref:System.Windows.Media.Animation.QuarticEase>, <xref:System.Windows.Media.Animation.QuinticEase> , , <xref:System.Windows.Media.Animation.PowerEase.Power%2A> ve özelliği kullanarak. Örneğin, yerine kullanmak <xref:System.Windows.Media.Animation.PowerEase> <xref:System.Windows.Media.Animation.CubicEase>istiyorsanız, 3'ün <xref:System.Windows.Media.Animation.PowerEase.Power%2A> bir değerini belirtin.  
  
 Çalışma süresine dahil edilen kolaylaştırma işlevlerini kullanmanın yanı sıra, 'den <xref:System.Windows.Media.Animation.EasingFunctionBase>devralarak kendi özel kolaylaştırma işlevlerinizi oluşturabilirsiniz. Aşağıdaki örnek, basit bir özel kolaylaştırma işlevinin nasıl oluşturulabildiğini gösterir. Kolaylaştırma işlevinin yöntemi geçersiz kılarak nasıl işlediğine <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> bağlı olarak kendi matematiksel mantığınızı ekleyebilirsiniz.
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
