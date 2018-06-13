---
title: 'Nasıl yapılır: Önbelleğe Alınan Öğeyi Fırça Olarak Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
ms.openlocfilehash: c43c4ecbefe99d6e38766705378d85d92ecc5729
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561530"
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a><span data-ttu-id="765ce-102">Nasıl yapılır: Önbelleğe Alınan Öğeyi Fırça Olarak Kullanma</span><span class="sxs-lookup"><span data-stu-id="765ce-102">How to: Use a Cached Element as a Brush</span></span>
<span data-ttu-id="765ce-103">Kullanım <xref:System.Windows.Media.BitmapCacheBrush> önbelleğe alınan öğeyi verimli bir şekilde yeniden sınıfı.</span><span class="sxs-lookup"><span data-stu-id="765ce-103">Use the <xref:System.Windows.Media.BitmapCacheBrush> class to reuse a cached element efficiently.</span></span> <span data-ttu-id="765ce-104">Bir öğenin önbelleğe almak için yeni bir örneğini oluşturmak <xref:System.Windows.Media.BitmapCache> sınıfı ve öğenin atayın <xref:System.Windows.UIElement.CacheMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="765ce-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="765ce-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="765ce-105">Example</span></span>  
 <span data-ttu-id="765ce-106">Aşağıdaki kod örneğinde, önbelleğe alınan öğe yeniden gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="765ce-106">The following code example shows how to reuse a cached element.</span></span> <span data-ttu-id="765ce-107">Önbelleğe alınan öğe bir <xref:System.Windows.Controls.Image> büyük bir görüntü görüntüleyen denetim.</span><span class="sxs-lookup"><span data-stu-id="765ce-107">The cached element is an <xref:System.Windows.Controls.Image> control that displays a large image.</span></span> <span data-ttu-id="765ce-108"><xref:System.Windows.Controls.Image> Denetim önbelleğe alınma bir bit eşlem olarak kullanarak <xref:System.Windows.Media.BitmapCache> sınıfı ve önbellek yeniden atayarak bunu bir <xref:System.Windows.Media.BitmapCacheBrush>.</span><span class="sxs-lookup"><span data-stu-id="765ce-108">The <xref:System.Windows.Controls.Image> control is cached as a bitmap by using the <xref:System.Windows.Media.BitmapCache> class, and the cache is reused by assigning it to a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span> <span data-ttu-id="765ce-109">Fırça etkili bir biçimde yeniden göstermek için yirmi beş düğmelerinin arka plan atanır.</span><span class="sxs-lookup"><span data-stu-id="765ce-109">The brush is assigned to the background of twenty-five buttons to show efficient reuse.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="765ce-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="765ce-110">See Also</span></span>  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [<span data-ttu-id="765ce-111">Nasıl yapılır: Öğeyi Önbelleğe Alarak İşleme Performansını Artırma</span><span class="sxs-lookup"><span data-stu-id="765ce-111">How to: Improve Rendering Performance by Caching an Element</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)
