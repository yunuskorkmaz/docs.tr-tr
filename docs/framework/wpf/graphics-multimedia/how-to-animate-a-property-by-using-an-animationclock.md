---
title: 'Nasıl yapılır: AnimationClock Kullanarak Bir Özelliğe Animasyon Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], properties [WPF], with AnimationClocks
- AnimationClocks [WPF]
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
ms.openlocfilehash: b8c64586d0dc5dc2e565fe4cb002e0f9cd4109af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a>Nasıl yapılır: AnimationClock Kullanarak Bir Özelliğe Animasyon Ekleme
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.Clock> bir özellik animasyon nesnelere.  
  
 Bağımlılık özelliği için üç yol vardır:  
  
-   Oluşturma bir <xref:System.Windows.Media.Animation.AnimationTimeline> ve kullanarak bu özellik ile ilişkilendirin bir <xref:System.Windows.Media.Animation.Storyboard>.  
  
-   Nesnenin kullanmak <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> tek bir uygulamak için yöntemi <xref:System.Windows.Media.Animation.AnimationTimeline> hedef özelliği.  
  
-   Oluşturma bir <xref:System.Windows.Media.Animation.AnimationClock> gelen bir <xref:System.Windows.Media.Animation.AnimationTimeline> ve bir özelliğe uygulayın.  
  
 <xref:System.Windows.Media.Animation.Storyboard> nesneleri ve <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi doğrudan oluşturmadan ve saatler dağıtmadan özelliklerine animasyon olanak tanır (örnekler için bkz: [film şeridi kullanarak bir özelliği animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) ve [bir özelliği olmadan animasyon ekleme Film şeridi kullanarak](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)); Saatler oluşturulan ve sizin için otomatik olarak dağıtılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl oluşturulacağını gösterir bir <xref:System.Windows.Media.Animation.AnimationClock> ve iki benzer özellikleri için geçerlidir.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Etkileşimli olarak denetleme gösteren bir örnek için bir <xref:System.Windows.Media.Animation.Clock> başladıktan sonra bkz [etkileşimli olarak saat denetimi](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [Görsel Taslak Kullanmadan Özelliğe Animasyon Ekleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)  
 [Özellik Animasyon Tekniklerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
