---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak Kenarlık Kalınlığına Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: 884b62e88c347449ae39caa9c028d09db39b9f4b
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344701"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak Kenarlık Kalınlığına Animasyon Ekleme
Bu örnek, <xref:System.Windows.Controls.Control.BorderThickness%2A> bir <xref:System.Windows.Controls.Border>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> bir <xref:System.Windows.Controls.Border>. özelliğini <xref:System.Windows.Controls.Control.BorderThickness%2A> canlandırmak için sınıfı kullanır. Bu animasyon aşağıdaki şekilde üç anahtar kare kullanır:  
  
1. İlk yarısında ikinci sırasında, yavaş <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> yavaş sınır kalınlığını artırmak için sınıfın bir örnek kullanır. Örnek, <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> değerler arasında düzgün bir doğrusal artış oluşturmak için kullanır.  
  
2. Sonraki yarım saniyenin sonunda, aniden sınır <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> kalınlığını artırmak için sınıfın bir örneğini kullanır. Değerler arasında ani atlar <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> oluşturmak türetilen gibi ayrık anahtar kareler, yani animasyon hareketi sarsıntılı.  
  
3. Son iki saniye boyunca, kenarlık <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> kalınlığını azaltmak için sınıfın bir örneğini kullanır. Bu tür spline anahtar <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> çerçeveleri özelliğin <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> değerlerine göre değerler arasında değişken bir geçiş oluşturmak türetilmiştir. Bu anahtar karede, animasyon yavaş başlar ve zaman diliminin sonuna doğru katlanarak hızlandırılır.  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 Tam örnek için [Anahtar Çerçeve Animasyon Örneği'ne](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](key-frame-animation-how-to-topics.md)
- [BorderThickness Değerine Animasyon Ekleme](../controls/how-to-animate-a-borderthickness-value.md)
