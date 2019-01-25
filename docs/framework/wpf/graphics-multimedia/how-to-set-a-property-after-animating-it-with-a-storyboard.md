---
title: 'Nasıl yapılır: Görsel Taslakla Özelliğe Animasyon Ekledikten Sonra Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], changing property values after
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
ms.openlocfilehash: e150a576ed6edb365e9e1468becc1a9e55b5aacc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532791"
---
# <a name="how-to-set-a-property-after-animating-it-with-a-storyboard"></a>Nasıl yapılır: Görsel Taslakla Özelliğe Animasyon Ekledikten Sonra Ayarlama
Bazı durumlarda, animasyon sonra bir özelliğin değerini değiştiremezsiniz görünebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir <xref:System.Windows.Media.Animation.Storyboard> rengine animasyon uygulamak için kullanılan bir <xref:System.Windows.Media.SolidColorBrush>. Düğmeye tıklandığında film şeridi tetiklenir. <xref:System.Windows.Media.Animation.Timeline.Completed> Olayı, böylece programın bildirim işlenir, <xref:System.Windows.Media.Animation.ColorAnimation> tamamlar.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton1Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## <a name="example"></a>Örnek  
 Sonra <xref:System.Windows.Media.Animation.ColorAnimation> fırça rengini Mavi olarak değiştirmek için programın denemeleri tamamlanır.  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 Önceki kodun herhangi bir şey gibi görünmüyor: değer olan fırça sarı olarak kalır verdiği <xref:System.Windows.Media.Animation.ColorAnimation> fırça animasyonlu. Temel özellik değeri (Temel), aslında mavi olarak değiştirilir. Ancak, etkin veya geçerli bir değer sarı kalır çünkü <xref:System.Windows.Media.Animation.ColorAnimation> hala temel değerin geçersiz kılıyor. Temel değerin yeniden etkili değer olmasını istiyorsanız, animasyonu özelliği etkilemesini durdurmanız gerekir. Görsel taslak animasyonları ile bunun için üç yolu vardır:  
  
-   Animasyonun ayarlamak <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özelliği <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
  
-   Tüm film şeridini kaldırın.  
  
-   Animasyon bireysel özellikten kaldırın.  
  
## <a name="set-the-animations-fillbehavior-property-to-stop"></a>Animasyonun FillBehavior özelliği Durma noktasına ayarlayın  
 Ayarlayarak <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> için <xref:System.Windows.Media.Animation.FillBehavior.Stop>, etkin süresinin sonuna ulaştıktan sonra hedef özelliği etkileyen durdurmak için animasyon söyleyin.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton2Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## <a name="remove-the-entire-storyboard"></a>Tüm film şeridini Kaldır  
 Kullanarak bir <xref:System.Windows.Media.Animation.RemoveStoryboard> tetikleyici veya <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> yöntemi, hedef özelliklerini etkileyen durdurmak için görsel taslak animasyonları söyleyin. Bu yaklaşım ve ayarı arasındaki farkı <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özelliğidir, film şeridini kaldırabilirsiniz, her zaman, while <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özelliği yalnızca bir etkisi animasyon etkin süresinin sona erdiğinde.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton3Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## <a name="remove-an-animation-from-an-individual-property"></a>Bir animasyonu tek bir özelliği Kaldır  
 Animasyonun özellik etkilemesini durdurmak için başka bir teknik kullanmaktır <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> animasyon uygulanan nesneyi yöntemi. İlk parametre olarak animasyon uygulanan bir özellik belirtin ve `null` ikinci olarak.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton4Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 Bu teknik, görsel taslak olmayan animasyon için de kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.Animation.RemoveStoryboard>
- [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Özellik Animasyon Tekniklerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
