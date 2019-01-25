---
title: 'Nasıl yapılır: Bir öğeyi önbelleğe alarak işleme performansını artırma'
ms.date: 03/30/2017
helpviewer_keywords:
- rendering performance [WPF], caching an element
- BitmapCache [WPF], improving rendering performance
- CacheMode [WPF], improving rendering performance
- performance [WPF], caching an element
- UIElement [WPF], caching
ms.assetid: 4739c1fc-60ba-4c46-aba6-f6c1a2688f19
ms.openlocfilehash: 79f427198be370d9cb48cab429906202a62bb72d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647588"
---
# <a name="how-to-improve-rendering-performance-by-caching-an-element"></a>Nasıl yapılır: Bir öğeyi önbelleğe alarak işleme performansını artırma
Kullanım <xref:System.Windows.Media.BitmapCache> karmaşık bir işleme performansını artırmak için sınıf <xref:System.Windows.UIElement>. Bir öğeyi önbelleğe almak için yeni bir örneğini oluşturma <xref:System.Windows.Media.BitmapCache> sınıfı ve öğenin atayın <xref:System.Windows.UIElement.CacheMode%2A> özelliği. Yeniden kullanabileceğiniz bir <xref:System.Windows.Media.BitmapCache> verimli bir şekilde de bir <xref:System.Windows.Media.BitmapCacheBrush>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, karmaşık bir öğe oluşturun ve öğe animasyonlu performansı artıran bir bit eşlem olarak önbelleğe gösterilmektedir. Öğe şekli geometriler ile birçok köşeler tutan bir tuvaldir. A <xref:System.Windows.Media.BitmapCache> varsayılan değerler atanır <xref:System.Windows.UIElement.CacheMode%2A> tuvalinin ve animasyon ve sorunsuz ölçeklendirme önbelleğe alınan bit eşlemin gösterir.  
  
 [!code-xaml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [Nasıl yapılır: Önbelleğe alınan öğeyi fırça olarak kullanma](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-cached-element-as-a-brush.md)
