---
title: "Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Nesneye Animasyon Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f513cda540b3337f1510ee0c46419a12023bcb6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Nesneye Animasyon Ekleme
Bu örnekte olduğu bir nesne animasyon gösterilmektedir <xref:System.Windows.Controls.Page.Background%2A> özelliği bir <xref:System.Windows.Controls.Page> anahtar çerçeveler kullanarak denetim.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> renk animasyon sınıfı değişiklikler için <xref:System.Windows.Controls.Page.Background%2A> özelliği bir <xref:System.Windows.Controls.Page> denetim. Farklı bir arka plan Fırçası düzenli aralıklarla örnek animasyon geçer. Bu animasyon kullanır <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> üç farklı anahtar çerçeve oluşturmak için sınıfı. Animasyon ana kare aşağıdaki şekilde kullanır:  
  
1.  Örneği ilk saniye sonunda canlandırır <xref:System.Windows.Media.LinearGradientBrush> sınıfı. Bu bölümde Örneğin, doğrusal gradyan arka plan rengi uygular rengi kırmızı turuncu sarı geçiş.  
  
2.  Sonraki saniye sonunda örneği canlandırır <xref:System.Windows.Media.RadialGradientBrush> sınıfı. Bu bölümde Örneğin, Radyal gradyan arka plan rengi uygular rengi siyah mavi için Beyaz'den geçiş.  
  
3.  Üçüncü saniye sonunda örneği canlandırır <xref:System.Windows.Media.DrawingBrush> sınıfı. Bu bölüm örneğin Damalı bir desen arka plana geçerlidir.  
  
4.  Animasyon yeniden başlar ve sonsuza kadar yinelenir.  
  
> [!NOTE]
>  <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>ile birlikte kullanabileceğiniz anahtar çerçevesi yalnızca türü <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> sınıfı. Anahtar çerçeveleri gibi <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> ani değişiklikler değerleri, yani oluşturmak, bu örnekteki renk değişiklikleri aniden ortaya çıkar.  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 Tam bir örnek için bkz: [ana kare animasyon örneği](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.Page.Background%2A>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>  
 <xref:System.Windows.Media.LinearGradientBrush>  
 <xref:System.Windows.Media.RadialGradientBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 [Anahtar-Çerçeve Animasyonlara Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
