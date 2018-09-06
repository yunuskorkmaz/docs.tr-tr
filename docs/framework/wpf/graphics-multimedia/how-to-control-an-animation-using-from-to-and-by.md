---
title: 'Nasıl yapılır: Bir Animasyonu Gelen, İçin ve Göre Kullanarak Denetleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
ms.openlocfilehash: e422c008ae3051ecd69b3278eb05fc0e2d1b1a0b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43734739"
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>Nasıl yapılır: Bir Animasyonu Gelen, İçin ve Göre Kullanarak Denetleme
"From/To/By" veya "Basit animasyon" iki hedef değer arasında bir geçiş oluşturur (bkz [animasyona genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) giriş animasyon farklı türleri için). Temel animasyon hedef değerleri ayarlamak için kullanın, <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özellikleri.  Aşağıdaki tabloda özetlenmiştir nasıl <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özellikleri bir arada kullanılabilir veya animasyonun hedef belirlemek için ayrı ayrı değerler.  
  
|Belirtilen özellikleri|Sonuç davranış|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|Tarafından belirtilen değere animasyon ilerler <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliğini animasyon uygulanan özellik için taban değerini veya önceki bir animasyon çıkış değeri, önceki animasyon nasıl yapılandırıldığına bağlı olarak.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Tarafından belirtilen değere animasyon ilerler <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği tarafından belirtilen değere <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|Tarafından belirtilen değere animasyon ilerler <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> toplamı tarafından belirtilen değere özellik <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özellikleri.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Animasyonun ilerledikçe özelliğin temel değerden veya önceki bir animasyon çıkış değeri tarafından belirtilen değere <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|Bu değer tarafından belirtilen değere ve toplam değere animasyon uygulanan özellik için taban değerini animasyon ilerler veya önceki bir animasyon çıkışını <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliği.|  
  
> [!NOTE]
>  Her ikisini birden ayarlamayın <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> aynı animasyon özelliği.  
  
 İkiden fazla hedef değerleri arasında animasyon ekleme ya da diğer ilişkilendirme yöntemlerini kullanmak için bir anahtar çerçeve animasyonu kullanın. Bkz: [anahtar-çerçeve animasyonlara genel bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md) daha fazla bilgi için.  
  
 Tek bir özellik için birden çok animasyonlara uygulama hakkında daha fazla bilgi için bkz: [anahtar-çerçeve animasyonlara genel bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
 Aşağıdaki örnek, farklı ayar etkilerini gösterir <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>, ve <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> animasyonları özellikleri.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Anahtar-Çerçeve Animasyonlara Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Gelen, için ve göre animasyon hedef değerleri örneği](https://go.microsoft.com/fwlink/?LinkID=159988)
