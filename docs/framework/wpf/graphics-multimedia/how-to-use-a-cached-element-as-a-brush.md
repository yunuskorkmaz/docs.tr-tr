---
title: 'Nasıl yapılır: Önbelleğe alınan öğeyi fırça olarak kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
ms.openlocfilehash: 7ff0e9eb131faaed3874995ee137126eac31f43d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597937"
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a>Nasıl yapılır: Önbelleğe alınan öğeyi fırça olarak kullanma
Kullanım <xref:System.Windows.Media.BitmapCacheBrush> verimli bir şekilde önbelleğe alınan öğeyi yeniden sınıfı. Bir öğeyi önbelleğe almak için yeni bir örneğini oluşturma <xref:System.Windows.Media.BitmapCache> sınıfı ve öğenin atayın <xref:System.Windows.UIElement.CacheMode%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, önbelleğe alınan öğeyi yeniden gösterilmektedir. Önbelleğe alınan öğe bir <xref:System.Windows.Controls.Image> büyük resim görüntüleyen denetim. <xref:System.Windows.Controls.Image> Denetim önbelleğe alınma bir bit eşlem olarak kullanarak <xref:System.Windows.Media.BitmapCache> sınıfı ve önbelleği yeniden atayarak o bir <xref:System.Windows.Media.BitmapCacheBrush>. Fırça yirmi beş düğmelerinin arka plan için etkili bir biçimde yeniden gösterecek şekilde atanır.  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [Nasıl yapılır: Bir öğeyi önbelleğe alarak işleme performansını artırma](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)
