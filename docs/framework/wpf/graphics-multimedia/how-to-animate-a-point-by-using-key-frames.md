---
title: "Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Noktaya Animasyon Ekleme"
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
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c115d31c6ace26f8fd9dd6cff3fdeead89eea33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Noktaya Animasyon Ekleme
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> animasyon sınıfı bir <xref:System.Windows.Point>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek elips üçgen yol boyunca taşır. Örnek kullanır <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> animasyon sınıfı <xref:System.Windows.Media.EllipseGeometry.Center%2A> özelliği bir <xref:System.Windows.Media.EllipseGeometry>. Bu animasyon üç ana kare aşağıdaki şekilde kullanır:  
  
1.  Birinci yarım saniye boyunca bir örneğini kullanan <xref:System.Windows.Media.Animation.LinearPointKeyFrame> elips yol boyunca bir hızda başlangıç konumundan taşımak için sınıf. Gibi doğrusal anahtar çerçeveler <xref:System.Windows.Media.Animation.LinearPointKeyFrame> değerler arasında yumuşak doğrusal bir ilişkilendirme oluşturun.  
  
2.  Sonraki son sırasında yarım ikinci bir örneğini kullanır <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> elips yol boyunca sonraki konumuna aniden taşımak için sınıf. Gibi ayrık anahtar çerçeveler <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> değerler arasında ani atlar oluşturun.  
  
3.  Son iki saniye boyunca bir örneğini kullanan <xref:System.Windows.Media.Animation.SplinePointKeyFrame> elips başlangıç konumuna geri taşımak için sınıf. Gibi Eğri anahtar çerçeveler <xref:System.Windows.Media.Animation.SplinePointKeyFrame> değerlerine göre değerler arasında değişken geçiş oluşturmak <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> özelliği. Bu örnekte, animasyon yavaş başlar ve zaman diliminin sonuna doğru katlanarak hızlanır.  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 Tam bir örnek için bkz: [ana kare animasyon örneği](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
 Diğer animasyon örnekleriyle tutarlılık için bu örnek kodu sürümlerini kullanan bir <xref:System.Windows.Media.Animation.Storyboard> uygulanacak nesne <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>. Ancak, kodda tek bir animasyonu uygularken, bunu kullanmak daha basittir <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> kullanmak yerine yöntemi bir <xref:System.Windows.Media.Animation.Storyboard>. Bir örnek için bkz: [özelliği olmadan kullanarak bir film şeridi animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.EllipseGeometry>  
 [Anahtar-Çerçeve Animasyonlara Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
