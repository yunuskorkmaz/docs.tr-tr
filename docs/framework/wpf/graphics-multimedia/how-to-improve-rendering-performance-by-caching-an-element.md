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
ms.openlocfilehash: 118e8b0cca52c44788c9d5b291d710f765e7af2a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153380"
---
# <a name="how-to-improve-rendering-performance-by-caching-an-element"></a><span data-ttu-id="f1bbd-102">Nasıl yapılır: Öğeyi Önbelleğe Alarak İşleme Performansını Artırma</span><span class="sxs-lookup"><span data-stu-id="f1bbd-102">How to: Improve Rendering Performance by Caching an Element</span></span>
<span data-ttu-id="f1bbd-103">Kullanım <xref:System.Windows.Media.BitmapCache> karmaşık bir işleme performansını artırmak için sınıf <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="f1bbd-103">Use the <xref:System.Windows.Media.BitmapCache> class to improve rendering performance of a complex <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="f1bbd-104">Bir öğeyi önbelleğe almak için yeni bir örneğini oluşturma <xref:System.Windows.Media.BitmapCache> sınıfı ve öğenin atayın <xref:System.Windows.UIElement.CacheMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f1bbd-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span> <span data-ttu-id="f1bbd-105">Yeniden kullanabileceğiniz bir <xref:System.Windows.Media.BitmapCache> verimli bir şekilde de bir <xref:System.Windows.Media.BitmapCacheBrush>.</span><span class="sxs-lookup"><span data-stu-id="f1bbd-105">You can reuse a <xref:System.Windows.Media.BitmapCache> efficiently in a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1bbd-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1bbd-106">Example</span></span>  
 <span data-ttu-id="f1bbd-107">Aşağıdaki kod örneği, karmaşık bir öğe oluşturun ve öğe animasyonlu performansı artıran bir bit eşlem olarak önbelleğe gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f1bbd-107">The following code example shows how to create a complex element and cache it as a bitmap, which improves performance when the element is animated.</span></span> <span data-ttu-id="f1bbd-108">Öğe şekli geometriler ile birçok köşeler tutan bir tuvaldir.</span><span class="sxs-lookup"><span data-stu-id="f1bbd-108">The element is a canvas that holds shape geometries with many vertices.</span></span> <span data-ttu-id="f1bbd-109">A <xref:System.Windows.Media.BitmapCache> varsayılan değerler atanır <xref:System.Windows.UIElement.CacheMode%2A> tuvalinin ve animasyon ve sorunsuz ölçeklendirme önbelleğe alınan bit eşlemin gösterir.</span><span class="sxs-lookup"><span data-stu-id="f1bbd-109">A <xref:System.Windows.Media.BitmapCache> with default values is assigned to the <xref:System.Windows.UIElement.CacheMode%2A> of the canvas, and an animation shows the smooth scaling of the cached bitmap.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## <a name="see-also"></a><span data-ttu-id="f1bbd-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1bbd-110">See also</span></span>

- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [<span data-ttu-id="f1bbd-111">Nasıl yapılır: Önbelleğe Alınan Öğeyi Fırça Olarak Kullanma</span><span class="sxs-lookup"><span data-stu-id="f1bbd-111">How to: Use a Cached Element as a Brush</span></span>](how-to-use-a-cached-element-as-a-brush.md)
