---
title: 'Nasıl yapılır: BorderThickness Değerine Animasyon Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF], animating changes to
- animation [WPF], changes to border thickness
ms.assetid: fd021978-f74b-4e7b-a7f7-3987dcad9e0f
ms.openlocfilehash: 4533ce6f2a1fe7243267ee8d638e2ad0a4f9cf3a
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124669"
---
# <a name="how-to-animate-a-borderthickness-value"></a>Nasıl yapılır: BorderThickness Değerine Animasyon Ekleme
Bu örnek, <xref:System.Windows.Media.Animation.ThicknessAnimation> sınıfını kullanarak bir kenarlık kalınlığına yapılan değişikliklere nasıl animasyon ekleneceğini gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.Media.Animation.ThicknessAnimation>kullanarak bir kenarlık kalınlığını hareketlendirir. Örnek, <xref:System.Windows.Controls.Border><xref:System.Windows.Controls.Border.BorderThickness%2A> özelliğini kullanır.  
  
 [!code-csharp[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/ThicknessAnimationExample.cs#thicknessanimationwholepage)]
 [!code-vb[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/ThicknessAnimationExample.vb#thicknessanimationwholepage)]  
  
 Tüm örnek için bkz. [animasyon örnek Galerisi](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Animation.ThicknessAnimation>
- <xref:System.Windows.Controls.Border.BorderThickness%2A>
- <xref:System.Windows.Controls.Border>
- [Animasyona Genel bakış](../graphics-multimedia/animation-overview.md)
- [Animasyon ve zamanlama ile ilgili nasıl yapılır konuları](../graphics-multimedia/animation-and-timing-how-to-topics.md)
- [Anahtar Çerçeveler Kullanarak Kenarlık Kalınlığına Animasyon Ekleme](../graphics-multimedia/how-to-animate-the-thickness-of-a-border-by-using-key-frames.md)
