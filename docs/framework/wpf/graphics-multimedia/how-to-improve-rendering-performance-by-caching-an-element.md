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
ms.locfileid: "33559304"
---
# <a name="how-to-improve-rendering-performance-by-caching-an-element"></a><span data-ttu-id="51581-102">Nasıl yapılır: Öğeyi Önbelleğe Alarak İşleme Performansını Artırma</span><span class="sxs-lookup"><span data-stu-id="51581-102">How to: Improve Rendering Performance by Caching an Element</span></span>
<span data-ttu-id="51581-103">Kullanım <xref:System.Windows.Media.BitmapCache> karmaşık bir işleme performansını artırmak için sınıf <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="51581-103">Use the <xref:System.Windows.Media.BitmapCache> class to improve rendering performance of a complex <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="51581-104">Bir öğenin önbelleğe almak için yeni bir örneğini oluşturmak <xref:System.Windows.Media.BitmapCache> sınıfı ve öğenin atayın <xref:System.Windows.UIElement.CacheMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="51581-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span> <span data-ttu-id="51581-105">Yeniden kullanabileceğiniz bir <xref:System.Windows.Media.BitmapCache> verimli bir şekilde, bir <xref:System.Windows.Media.BitmapCacheBrush>.</span><span class="sxs-lookup"><span data-stu-id="51581-105">You can reuse a <xref:System.Windows.Media.BitmapCache> efficiently in a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51581-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="51581-106">Example</span></span>  
 <span data-ttu-id="51581-107">Aşağıdaki kod örneğinde, karmaşık bir öğe oluşturun ve performans öğesi animasyonlu artıran bir bitmap olarak önbelleğe gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="51581-107">The following code example shows how to create a complex element and cache it as a bitmap, which improves performance when the element is animated.</span></span> <span data-ttu-id="51581-108">Şekil geometri birçok köşe ile tutan bir tuval öğedir.</span><span class="sxs-lookup"><span data-stu-id="51581-108">The element is a canvas that holds shape geometries with many vertices.</span></span> <span data-ttu-id="51581-109">A <xref:System.Windows.Media.BitmapCache> varsayılan değerler atanır <xref:System.Windows.UIElement.CacheMode%2A> Kanvasın ve önbelleğe alınan bit eşlem sorunsuz ölçeklendirme animasyon gösterir.</span><span class="sxs-lookup"><span data-stu-id="51581-109">A <xref:System.Windows.Media.BitmapCache> with default values is assigned to the <xref:System.Windows.UIElement.CacheMode%2A> of the canvas, and an animation shows the smooth scaling of the cached bitmap.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## <a name="see-also"></a><span data-ttu-id="51581-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="51581-110">See Also</span></span>  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [<span data-ttu-id="51581-111">Nasıl yapılır: Önbelleğe Alınan Öğeyi Fırça Olarak Kullanma</span><span class="sxs-lookup"><span data-stu-id="51581-111">How to: Use a Cached Element as a Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-cached-element-as-a-brush.md)
