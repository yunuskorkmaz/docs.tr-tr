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
ms.openlocfilehash: 4fa9efc593461d26eabaee5e2f62c1a17da1b543
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201370"
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a>Nasıl yapılır: AnimationClock Kullanarak Bir Özelliğe Animasyon Ekleme
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.Clock> özelliği oynatmak nesneleri.  
  
 Bağımlılık özelliği için üç yol vardır:  
  
-   Oluşturma bir <xref:System.Windows.Media.Animation.AnimationTimeline> bu özellik ile ilişkilendirin kullanılarak bir <xref:System.Windows.Media.Animation.Storyboard>.  
  
-   Nesnenin kullanın <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi tek bir uygulamaya <xref:System.Windows.Media.Animation.AnimationTimeline> için target özelliği.  
  
-   Oluşturma bir <xref:System.Windows.Media.Animation.AnimationClock> gelen bir <xref:System.Windows.Media.Animation.AnimationTimeline> ve bir özelliğe uygulayın.  
  
 <xref:System.Windows.Media.Animation.Storyboard> nesneleri ve <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemini etkinleştirmek, doğrudan oluşturmadan ve dağıtmadan saatler özelliklerine animasyon uygulamak (örnekler için bkz [görsel taslak kullanarak özelliğe animasyon ekleme](how-to-animate-a-property-by-using-a-storyboard.md) ve [bir özelliği olmadan animasyon ekleme Görsel taslak kullanarak](how-to-animate-a-property-without-using-a-storyboard.md)); Storyboard ve sizin için otomatik olarak dağıtılmış.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Media.Animation.AnimationClock> ve iki benzer özellikleri için geçerlidir.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Etkileşimli olarak denetleme gösteren bir örnek için bir <xref:System.Windows.Media.Animation.Clock> başladıktan sonra bkz [etkileşimli olarak saat denetimi](how-to-interactively-control-a-clock.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme](how-to-animate-a-property-by-using-a-storyboard.md)
- [Görsel Taslak Kullanmadan Özelliğe Animasyon Ekleme](how-to-animate-a-property-without-using-a-storyboard.md)
- [Özellik Animasyon Tekniklerine Genel Bakış](property-animation-techniques-overview.md)
