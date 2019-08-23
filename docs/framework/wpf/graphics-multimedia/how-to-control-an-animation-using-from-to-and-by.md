---
title: 'Nasıl yapılır: Bir Animasyonu Gelen, İçin ve Göre Kullanarak Denetleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
ms.openlocfilehash: 812217a2905671567271687b974a435dd85cea47
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930080"
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>Nasıl yapılır: Bir Animasyonu Gelen, İçin ve Göre Kullanarak Denetleme
"From/to/by" veya "Basic Animation" iki hedef değer arasında bir geçiş oluşturur (farklı animasyon türlerine giriş için bkz. [animasyona genel bakış](animation-overview.md) ). Temel animasyonun hedef değerlerini ayarlamak için, ve <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliklerini kullanın <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.  Aşağıdaki tabloda <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliklerinin bir animasyonun hedef değerlerini belirlemekte nasıl birlikte veya ayrı ayrı kullanılabileceği özetlenmektedir.  
  
|Belirtilen özellikler|Sonuç davranışı|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|Animasyon, önceki animasyonun nasıl yapılandırıldığına bağlı olarak, <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği tarafından belirtilen değerden hareketlendirilen özelliğin temel değerine veya önceki animasyonun çıkış değerine ilerler.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Animasyon, özelliği tarafından <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> belirtilen değerden <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği tarafından belirtilen değere ilerler.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|Animasyon, <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği tarafından belirtilen değerden <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliklerinin toplamı tarafından belirtilen değere ilerler.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Animasyon, animasyonlu özelliğin temel değerinden veya önceki animasyonun çıkış değerinden <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği tarafından belirtilen değere ilerler.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|Animasyon, hareketlendirilen özelliğin temel değerinden veya önceki animasyonun çıkış değerinden bu değerin toplamına ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özellik tarafından belirtilen değere kadar ilerler.|  
  
> [!NOTE]
> Hem <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> hem de özelliğini aynı animasyon üzerinde ayarlamayın.  
  
 Diğer enterpolasyon yöntemlerini kullanmak veya ikiden fazla hedef değer arasında animasyon uygulamak için, anahtar çerçeve animasyonunu kullanın. Daha fazla bilgi için bkz. [anahtar çerçeve animasyonlarına genel bakış](key-frame-animations-overview.md) .  
  
 Tek bir özelliğe birden çok animasyon uygulama hakkında daha fazla bilgi için bkz. [anahtar-çerçeve animasyonlara genel bakış](key-frame-animations-overview.md).  
  
 Aşağıdaki örnekte animasyonlarda <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>ve <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliklerinin farklı etkileri gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [From, to ve By animasyon hedefi değerleri örneği](https://go.microsoft.com/fwlink/?LinkID=159988)
