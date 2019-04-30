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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769265"
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a><span data-ttu-id="7462d-102">Nasıl yapılır: Önbelleğe Alınan Öğeyi Fırça Olarak Kullanma</span><span class="sxs-lookup"><span data-stu-id="7462d-102">How to: Use a Cached Element as a Brush</span></span>
<span data-ttu-id="7462d-103">Kullanım <xref:System.Windows.Media.BitmapCacheBrush> verimli bir şekilde önbelleğe alınan öğeyi yeniden sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7462d-103">Use the <xref:System.Windows.Media.BitmapCacheBrush> class to reuse a cached element efficiently.</span></span> <span data-ttu-id="7462d-104">Bir öğeyi önbelleğe almak için yeni bir örneğini oluşturma <xref:System.Windows.Media.BitmapCache> sınıfı ve öğenin atayın <xref:System.Windows.UIElement.CacheMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="7462d-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7462d-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="7462d-105">Example</span></span>  
 <span data-ttu-id="7462d-106">Aşağıdaki kod örneği, önbelleğe alınan öğeyi yeniden gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7462d-106">The following code example shows how to reuse a cached element.</span></span> <span data-ttu-id="7462d-107">Önbelleğe alınan öğe bir <xref:System.Windows.Controls.Image> büyük resim görüntüleyen denetim.</span><span class="sxs-lookup"><span data-stu-id="7462d-107">The cached element is an <xref:System.Windows.Controls.Image> control that displays a large image.</span></span> <span data-ttu-id="7462d-108"><xref:System.Windows.Controls.Image> Denetim önbelleğe alınma bir bit eşlem olarak kullanarak <xref:System.Windows.Media.BitmapCache> sınıfı ve önbelleği yeniden atayarak o bir <xref:System.Windows.Media.BitmapCacheBrush>.</span><span class="sxs-lookup"><span data-stu-id="7462d-108">The <xref:System.Windows.Controls.Image> control is cached as a bitmap by using the <xref:System.Windows.Media.BitmapCache> class, and the cache is reused by assigning it to a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span> <span data-ttu-id="7462d-109">Fırça yirmi beş düğmelerinin arka plan için etkili bir biçimde yeniden gösterecek şekilde atanır.</span><span class="sxs-lookup"><span data-stu-id="7462d-109">The brush is assigned to the background of twenty-five buttons to show efficient reuse.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="7462d-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7462d-110">See also</span></span>

- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [<span data-ttu-id="7462d-111">Nasıl yapılır: Bir öğeyi önbelleğe alarak işleme performansını artırma</span><span class="sxs-lookup"><span data-stu-id="7462d-111">How to: Improve Rendering Performance by Caching an Element</span></span>](how-to-improve-rendering-performance-by-caching-an-element.md)
