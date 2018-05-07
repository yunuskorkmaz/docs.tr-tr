---
title: 'Nasıl yapılır: Öğeyi Önbelleğe Alarak İşleme Performansını Artırma'
ms.date: 03/30/2017
helpviewer_keywords:
- rendering performance [WPF], caching an element
- BitmapCache [WPF], improving rendering performance
- CacheMode [WPF], improving rendering performance
- performance [WPF], caching an element
- UIElement [WPF], caching
ms.assetid: 4739c1fc-60ba-4c46-aba6-f6c1a2688f19
ms.openlocfilehash: a92909c623db0c10e3434677b4275fa82b787fa7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-improve-rendering-performance-by-caching-an-element"></a>Nasıl yapılır: Öğeyi Önbelleğe Alarak İşleme Performansını Artırma
Kullanım <xref:System.Windows.Media.BitmapCache> karmaşık bir işleme performansını artırmak için sınıf <xref:System.Windows.UIElement>. Bir öğenin önbelleğe almak için yeni bir örneğini oluşturmak <xref:System.Windows.Media.BitmapCache> sınıfı ve öğenin atayın <xref:System.Windows.UIElement.CacheMode%2A> özelliği. Yeniden kullanabileceğiniz bir <xref:System.Windows.Media.BitmapCache> verimli bir şekilde, bir <xref:System.Windows.Media.BitmapCacheBrush>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, karmaşık bir öğe oluşturun ve performans öğesi animasyonlu artıran bir bitmap olarak önbelleğe gösterilmektedir. Şekil geometri birçok köşe ile tutan bir tuval öğedir. A <xref:System.Windows.Media.BitmapCache> varsayılan değerler atanır <xref:System.Windows.UIElement.CacheMode%2A> Kanvasın ve önbelleğe alınan bit eşlem sorunsuz ölçeklendirme animasyon gösterir.  
  
 [!code-xaml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [Nasıl yapılır: Önbelleğe Alınan Öğeyi Fırça Olarak Kullanma](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-cached-element-as-a-brush.md)
