---
title: "Kolaylaştırıcı İşlevler"
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
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 570a065d3f28befe8db4887ff908c3bd60a639a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="easing-functions"></a>Kolaylaştırıcı İşlevler
Hareket hızı işlevleri, animasyonların özel matematiksel formüller olanak sağlar. Örneğin, bir nesnenin gerçekçi Sıçrama veya dizinindeymiş gibi yay üzerinde davranır isteyebilirsiniz. Bu etkilerle yaklaşık için anahtar çerçeve veya From/To/By bile animasyonları kullanabilirsiniz, ancak iş önemli miktarda götürecek ve animasyon matematiksel formül kullanmaktan daha az doğru olacaktır.  
  
 Devralarak kendi özel hareket hızı işlevi oluşturma yanı sıra <xref:System.Windows.Media.Animation.EasingFunctionBase>, çalışma zamanı tarafından sağlanan çeşitli hareket hızı işlevlerini birini ortak efektleri oluşturmak için kullanabilirsiniz.  
  
-   <xref:System.Windows.Media.Animation.BackEase>: Bir animasyon hareketini biraz belirtilen yolda animasyon başlamadan önce geri çeker.  
  
-   <xref:System.Windows.Media.Animation.BounceEase>: Sıçrama efekti oluşturur.  
  
-   <xref:System.Windows.Media.Animation.CircleEase>: Bir döngüsel işlevi kullanarak hızlandırır/yavaşlayan bir animasyon oluşturur.  
  
-   <xref:System.Windows.Media.Animation.CubicEase>: Formülü kullanarak hızlandırır/yavaşlayan bir animasyon oluşturur *f*(*t*) = *t*<sup>3</sup>.  
  
-   <xref:System.Windows.Media.Animation.ElasticEase>: Kalanına gelene kadar ve geriye salınım yapan yay benzer bir animasyon oluşturur.  
  
-   <xref:System.Windows.Media.Animation.ExponentialEase>: Bir üstel formülü kullanarak hızlandırır/yavaşlayan bir animasyon oluşturur.  
  
-   <xref:System.Windows.Media.Animation.PowerEase>: Formülü kullanarak hızlandırır/yavaşlayan bir animasyon oluşturur *f*(*t*) = *t*<sup>p</sup> p olduğu içineşit<xref:System.Windows.Media.Animation.PowerEase.Power%2A> özelliği.  
  
-   <xref:System.Windows.Media.Animation.QuadraticEase>: Formülü kullanarak hızlandırır/yavaşlayan bir animasyon oluşturur *f*(*t*) = *t*<sup>2</sup>.  
  
-   <xref:System.Windows.Media.Animation.QuarticEase>: Formülü kullanarak hızlandırır/yavaşlayan bir animasyon oluşturur *f*(*t*) = *t*<sup>4</sup>.  
  
-   <xref:System.Windows.Media.Animation.QuinticEase>: Formülü kullanarak hızlandırır/yavaşlayan bir animasyon oluşturmak *f*(*t*) = *t*<sup>5</sup>.  
  
-   <xref:System.Windows.Media.Animation.SineEase>: Bir sinüs formülünü kullanarak hızlandırır/yavaşlayan bir animasyon oluşturur.  
  
 Aşağıdaki örnek ile hareket hızı bu işlevlerin davranış keşfedebilirsiniz.  
  
 [Bu örneği çalıştırmak](http://go.microsoft.com/fwlink/?LinkId=139798&sref=easing_functions_gallery)  
  
 Bir animasyon hareket hızı işlevi uygulamak için kullanmak `EasingFunction` animasyonun özellik animasyon uygulamak için hareket hızı işlevi belirtin. Aşağıdaki örnek uygular bir <xref:System.Windows.Media.Animation.BounceEase> işlevine kolaylaştırma bir <xref:System.Windows.Media.Animation.DoubleAnimation> Sıçrama efekti oluşturmak için.  
  
 [Bu örneği çalıştırmak](http://go.microsoft.com/fwlink/?LinkId=139798&sref=BounceEase)  
  
 [!code-xaml[BounceEase_snippet#BounceEase](../../../../samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 Önceki örnekte, bir From/To/By için hareket hızı işlevi uygulandı animasyon. Bu gibi durumlarda, bu hareket hızı işlevler aynı zamanda anahtar çerçeve animasyonları uygulayabilirsiniz. Aşağıdaki örnek anahtar çerçeveler ilişkili işlevler kolaylaştırma ile sözleşmeleri yukarı, yavaşlatır, ardından aşağı (düşüyor gibi) genişletir ve bir Dur geri dönmeler bir dikdörtgen bir animasyon oluşturmak için nasıl kullanılacağını gösterir.  
  
 [Bu örneği çalıştırmak](http://go.microsoft.com/fwlink/?LinkId=139798&sref=EasingFunctionDoubleKeyFrame)  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 Kullanabileceğiniz <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> nasıl hareket hızı işlevi, diğer bir deyişle, davranacağını özelliğini değiştirin animasyonun nasıl ilişkilendirileceğini. Verebileceğiniz üç olası değerler <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseIn>: İlişkilendirme hareket hızı işlev ile ilişkili matematik formülünü takip eder.  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseOut>: İlişkilendirme % 100'ü çıkış eksi hareket hızı işlev ile ilişkili formülün izler.  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: İlişkilendirme kullanan <xref:System.Windows.Media.Animation.EasingMode.EaseIn> animasyonun ilk yarısı için ve <xref:System.Windows.Media.Animation.EasingMode.EaseOut> ikinci yarısı için.  
  
 Grafikleri farklı değerlerini göstermek <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> nerede *f*(*x*) animasyon ilerlemesini gösterir ve *t* zamanı temsil eder.  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![BackEase EasingMode grafikleri. ] (../../../../docs/framework/wpf/graphics-multimedia/media/backease-graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![BounceEase EasingMode grafikleri. ] (../../../../docs/framework/wpf/graphics-multimedia/media/bounceease-graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![CircleEase EasingMode grafikleri. ] (../../../../docs/framework/wpf/graphics-multimedia/media/circleease-graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![CubicEase EasingMode grafikleri. ] (../../../../docs/framework/wpf/graphics-multimedia/media/cubicease-graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![Farklı gevşeme modlarının ile ElasticEase. ] (../../../../docs/framework/wpf/graphics-multimedia/media/elasticease-graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![Farklı gevşeme modlarının ExponentialEase grafikleri. ] (../../../../docs/framework/wpf/graphics-multimedia/media/exponentialease-graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![Farklı gevşeme modlarının ile QuarticEase. ] (../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![Farklı gevşeme modlarının grafikleriyle](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![Farklı gevşeme modlarının ile QuarticEase. ] (../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![Farklı gevşeme modlarının ile QuinticEase. ] (../../../../docs/framework/wpf/graphics-multimedia/media/quinticease-graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![Farklı EasingMode değerleri için SineEase](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
>  Kullanabileceğiniz <xref:System.Windows.Media.Animation.PowerEase> aynı davranışı oluşturmak için <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, ve <xref:System.Windows.Media.Animation.QuinticEase> kullanarak <xref:System.Windows.Media.Animation.PowerEase.Power%2A> özelliği. Örneğin, kullanmak istediğiniz <xref:System.Windows.Media.Animation.PowerEase> yerine için <xref:System.Windows.Media.Animation.CubicEase>, belirtin bir <xref:System.Windows.Media.Animation.PowerEase.Power%2A> değeri 3.  
  
 Çalışma zamanında dahil hareket hızı işlevlerini kullanmanın yanı sıra, kendi özel hareket hızı işlevler devralarak oluşturabileceğiniz <xref:System.Windows.Media.Animation.EasingFunctionBase>. Aşağıdaki örnekte nasıl basit bir özel hareket hızı işlevin oluşturulacağını gösterir. Geçersiz kılarak hareket hızı işlevi nasıl davranacağını için kendi matematiksel mantığınızı ekleyebilirsiniz <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> yöntemi.  
  
 [Bu örneği çalıştırmak](http://go.microsoft.com/fwlink/?LinkId=139798&sref=CustomEasingFunction)  
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
