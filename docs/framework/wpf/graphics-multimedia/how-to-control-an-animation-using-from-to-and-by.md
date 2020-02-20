---
title: 'Nasıl yapılır: Bir Animasyonu Gelen, İçin ve Göre Kullanarak Denetleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
ms.openlocfilehash: b06df97dc57c58a01f30be2d70bfeebf104521ad
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451791"
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>Nasıl yapılır: Bir Animasyonu Gelen, İçin ve Göre Kullanarak Denetleme
"From/to/by" veya "Basic Animation" iki hedef değer arasında bir geçiş oluşturur (farklı animasyon türlerine giriş için bkz. [animasyona genel bakış](animation-overview.md) ). Temel animasyonun hedef değerlerini ayarlamak için <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliklerini kullanın.  Aşağıdaki tabloda <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliklerinin bir animasyonun hedef değerlerini belirlemede nasıl birlikte veya ayrı ayrı kullanılabileceği özetlenmektedir.  
  
|Belirtilen özellikler|Sonuç davranışı|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|Animasyon, <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği tarafından belirtilen değerden, önceki animasyonun nasıl yapılandırıldığına bağlı olarak, hareketlendirilen özelliğin temel değerine veya önceki animasyonun çıkış değerine ilerler.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Animasyon, <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği tarafından belirtilen değerden <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği tarafından belirtilen değere ilerler.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|Animasyon, <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği tarafından belirtilen değerden <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliklerinin toplamı tarafından belirtilen değere ilerler.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Animasyon, animasyonlu özelliğin temel değerinden veya önceki animasyonun çıkış değerinden <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği tarafından belirtilen değere ilerler.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|Animasyon, hareketlendirilen özelliğin temel değerinden veya önceki animasyonun çıkış değerinden bu değerin toplamına ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliği tarafından belirtilen değere kadar ilerler.|  
  
> [!NOTE]
> <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliğini ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliğini aynı animasyon üzerinde ayarlamayın.  
  
 Diğer enterpolasyon yöntemlerini kullanmak veya ikiden fazla hedef değer arasında animasyon uygulamak için, anahtar çerçeve animasyonunu kullanın. Daha fazla bilgi için bkz. [anahtar çerçeve animasyonlarına genel bakış](key-frame-animations-overview.md) .  
  
 Tek bir özelliğe birden çok animasyon uygulama hakkında daha fazla bilgi için bkz. [anahtar-çerçeve animasyonlara genel bakış](key-frame-animations-overview.md).  
  
 Aşağıdaki örnekte, animasyonlarda <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>ve <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliklerini ayarlamanın farklı etkileri gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [From, to ve By animasyon hedefi değerleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)
