---
title: 'Nasıl yapılır: FrameworkElement Boyutuna Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], FrameworkElement size
- FrameworkElement [WPF], animating size of
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
ms.openlocfilehash: d1995deec5ab2c9bf405911af43b4d242d599119
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776915"
---
# <a name="how-to-animate-the-size-of-a-frameworkelement"></a>Nasıl yapılır: FrameworkElement Boyutuna Animasyon Ekleme
Boyutuna animasyon ekleme için bir <xref:System.Windows.FrameworkElement>, ya da animasyon uygulayabilirsiniz, <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özellikleri veya kullanım animasyonlu <xref:System.Windows.Media.ScaleTransform>.  
  
 Aşağıdaki örnekte, bu iki yaklaşımı kullanarak iki düğmenin boyutu canlandırır. Bir düğmeyi yeniden boyutlandırılır animasyon tarafından kendi <xref:System.Windows.FrameworkElement.Width%2A> özelliği ve başka yeniden boyutlandırılır animasyon tarafından bir <xref:System.Windows.Media.ScaleTransform> uygulanan kendi <xref:System.Windows.UIElement.RenderTransform%2A> özelliği. Her düğme bazı metinler içerir. Başlangıçta, metni hem düğmeleri aynı görünür, ancak ikinci düğme metni düğmeleri yeniden boyutlandırıldığında bozulur.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[transformanimations_snip#1](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 Bir öğe dönüştürdüğünüzde, tüm öğeyi ve içeriği dönüştürülür. Doğrudan ilk düğme olduğu gibi bir öğenin boyutu değiştirdiğinizde, boyut ve konum, üst öğenin boyutuna bağlı sürece öğenin içeriği yeniden boyutlandırılıyor değil.  
  
 Animasyonlu dönüşüm uygulayarak bir öğe boyutuna animasyon ekleme, <xref:System.Windows.UIElement.RenderTransform%2A> özelliği animasyonlu daha iyi performans sağlar, <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> doğrudan, çünkü <xref:System.Windows.UIElement.RenderTransform%2A> özelliğinin bir düzen geçişi tetiklemez.  
  
 Özellikleri hakkında daha fazla bilgi için bkz. [animasyona genel bakış](../graphics-multimedia/animation-overview.md). Dönüşümler hakkında daha fazla bilgi için bkz. [dönüştüren genel bakış](../graphics-multimedia/transforms-overview.md).
