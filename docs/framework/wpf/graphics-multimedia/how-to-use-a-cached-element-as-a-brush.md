---
title: 'Nasıl yapılır: Önbelleğe Alınan Öğeyi Fırça Olarak Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
ms.openlocfilehash: 78df242c7f00b69e36ea4ab6751f51509d9e2220
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229374"
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a>Nasıl yapılır: Önbelleğe Alınan Öğeyi Fırça Olarak Kullanma
Kullanım <xref:System.Windows.Media.BitmapCacheBrush> verimli bir şekilde önbelleğe alınan öğeyi yeniden sınıfı. Bir öğeyi önbelleğe almak için yeni bir örneğini oluşturma <xref:System.Windows.Media.BitmapCache> sınıfı ve öğenin atayın <xref:System.Windows.UIElement.CacheMode%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, önbelleğe alınan öğeyi yeniden gösterilmektedir. Önbelleğe alınan öğe bir <xref:System.Windows.Controls.Image> büyük resim görüntüleyen denetim. <xref:System.Windows.Controls.Image> Denetim önbelleğe alınma bir bit eşlem olarak kullanarak <xref:System.Windows.Media.BitmapCache> sınıfı ve önbelleği yeniden atayarak o bir <xref:System.Windows.Media.BitmapCacheBrush>. Fırça yirmi beş düğmelerinin arka plan için etkili bir biçimde yeniden gösterecek şekilde atanır.  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [Nasıl yapılır: Öğeyi Önbelleğe Alarak İşleme Performansını Artırma](how-to-improve-rendering-performance-by-caching-an-element.md)
