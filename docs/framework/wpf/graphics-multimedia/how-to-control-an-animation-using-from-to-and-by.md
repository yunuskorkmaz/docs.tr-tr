---
title: 'Nasıl yapılır: Bir Animasyonu Gelen, İçin ve Göre Kullanarak Denetleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
ms.openlocfilehash: 56522ee5bd4391e43c261558b2fa622234c9ea3b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073278"
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>Nasıl yapılır: Bir Animasyonu Gelen, İçin ve Göre Kullanarak Denetleme
"From/To/By" veya "Basit animasyon" iki hedef değer arasında bir geçiş oluşturur (bkz [animasyona genel bakış](animation-overview.md) giriş animasyon farklı türleri için). Temel animasyon hedef değerleri ayarlamak için kullanın, <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özellikleri.  Aşağıdaki tabloda özetlenmiştir nasıl <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özellikleri bir arada kullanılabilir veya animasyonun hedef belirlemek için ayrı ayrı değerler.  
  
|Belirtilen özellikleri|Sonuç davranış|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|Tarafından belirtilen değere animasyon ilerler <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliğini animasyon uygulanan özellik için taban değerini veya önceki bir animasyon çıkış değeri, önceki animasyon nasıl yapılandırıldığına bağlı olarak.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Tarafından belirtilen değere animasyon ilerler <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliği tarafından belirtilen değere <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|Tarafından belirtilen değere animasyon ilerler <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> toplamı tarafından belirtilen değere özellik <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özellikleri.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|Animasyonun ilerledikçe özelliğin temel değerden veya önceki bir animasyon çıkış değeri tarafından belirtilen değere <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|Bu değer tarafından belirtilen değere ve toplam değere animasyon uygulanan özellik için taban değerini animasyon ilerler veya önceki bir animasyon çıkışını <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> özelliği.|  
  
> [!NOTE]
>  Her ikisini birden ayarlamayın <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliği ve <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> aynı animasyon özelliği.  
  
 İkiden fazla hedef değerleri arasında animasyon ekleme ya da diğer ilişkilendirme yöntemlerini kullanmak için bir anahtar çerçeve animasyonu kullanın. Bkz: [anahtar-çerçeve animasyonlara genel bakış](key-frame-animations-overview.md) daha fazla bilgi için.  
  
 Tek bir özellik için birden çok animasyonlara uygulama hakkında daha fazla bilgi için bkz: [anahtar-çerçeve animasyonlara genel bakış](key-frame-animations-overview.md).  
  
 Aşağıdaki örnek, farklı ayar etkilerini gösterir <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>, ve <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> animasyonları özellikleri.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Gelen, için ve göre animasyon hedef değerleri örneği](https://go.microsoft.com/fwlink/?LinkID=159988)
