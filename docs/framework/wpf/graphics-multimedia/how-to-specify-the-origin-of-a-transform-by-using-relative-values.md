---
title: 'Nasıl yapılır: Göreli Değerler Kullanarak Dönüşümün Kaynağını Belirtme'
ms.date: 03/30/2017
helpviewer_keywords:
- origins of Transforms [WPF]
- Transforms [WPF], origins of
- graphics [WPF], origins of Transforms
ms.assetid: f4dbc29d-93c7-41cd-96d8-5cfd8624b470
ms.openlocfilehash: 48b3b0df8dab8516873495a996074eae57ffe00f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59082964"
---
# <a name="how-to-specify-the-origin-of-a-transform-by-using-relative-values"></a><span data-ttu-id="40d56-102">Nasıl yapılır: Göreli Değerler Kullanarak Dönüşümün Kaynağını Belirtme</span><span class="sxs-lookup"><span data-stu-id="40d56-102">How to: Specify the Origin of a Transform by Using Relative Values</span></span>
<span data-ttu-id="40d56-103">Bu örnekte kaynağını belirtmek için göreli değerlerini kullanmayı gösterir. bir <xref:System.Windows.UIElement.RenderTransform%2A> uygulanan bir <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="40d56-103">This example shows how to use relative values to specify the origin of a <xref:System.Windows.UIElement.RenderTransform%2A> that is applied to a <xref:System.Windows.FrameworkElement>.</span></span>  
  
 <span data-ttu-id="40d56-104">Ne zaman döndürmek, ölçeklendirme veya eğriltme bir <xref:System.Windows.FrameworkElement> kullanarak <xref:System.Windows.UIElement.RenderTransform%2A> özelliği, varsayılan ayar, öğenin sol üst köşesine dönüşüm uygular.</span><span class="sxs-lookup"><span data-stu-id="40d56-104">When you rotate, scale, or skew a <xref:System.Windows.FrameworkElement> by using the <xref:System.Windows.UIElement.RenderTransform%2A> property, the default setting applies the transform to the upper-left corner of the element.</span></span> <span data-ttu-id="40d56-105">Döndürme, ölçeklendirme veya öğenin Merkezi'nden eğriltme istiyorsanız, öğenin merkezine dönüşümünün merkez ayarlayarak dengeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40d56-105">If you want to rotate, scale, or skew from the center of the element, you can compensate by setting the center of the transform to the center of the element.</span></span> <span data-ttu-id="40d56-106">Ancak, bu çözüm, öğe bildiğiniz gerektirir.</span><span class="sxs-lookup"><span data-stu-id="40d56-106">However, that solution requires that you know the size of the element.</span></span> <span data-ttu-id="40d56-107">Bir öğenin merkezine dönüşüm uygulamak için daha kolay bir yolu ayarlamaktır kendi <xref:System.Windows.UIElement.RenderTransformOrigin%2A> özelliğini (0,5, 0,5) dönüştürme üzerinde orta değer ayarlamak yerine.</span><span class="sxs-lookup"><span data-stu-id="40d56-107">An easier way of applying a transform to the center of an element is to set its <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to (0.5, 0.5), instead of setting a center value on the transform itself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40d56-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="40d56-108">Example</span></span>  
 <span data-ttu-id="40d56-109">Aşağıdaki örnekte bir <xref:System.Windows.Media.RotateTransform> döndürmek için bir <xref:System.Windows.Controls.Button> 45 derece saat yönünde.</span><span class="sxs-lookup"><span data-stu-id="40d56-109">The following example uses a <xref:System.Windows.Media.RotateTransform> to rotate a <xref:System.Windows.Controls.Button> 45 degrees clockwise.</span></span> <span data-ttu-id="40d56-110">Örnek bir merkezi belirtmediğinden düğmenin sol üst köşe olan noktası hakkında (0, 0) döndürür.</span><span class="sxs-lookup"><span data-stu-id="40d56-110">Because the example does not specify a center, the button rotates about the point (0, 0), which is its upper-left corner.</span></span> <span data-ttu-id="40d56-111"><xref:System.Windows.Media.RotateTransform> Uygulanan <xref:System.Windows.UIElement.RenderTransform%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="40d56-111">The <xref:System.Windows.Media.RotateTransform> is applied to the <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="40d56-112">Aşağıdaki örnek dönüştürme sonucu aşağıda gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="40d56-112">The following illustration shows the transformation result for the example that follows.</span></span>  
  
 <span data-ttu-id="40d56-113">![RenderTransform kullanılarak dönüştürülen düğme](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")</span><span class="sxs-lookup"><span data-stu-id="40d56-113">![A button transformed using RenderTransform](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")</span></span>  
<span data-ttu-id="40d56-114">RenderTransform özelliği kullanılarak 45 derece saat yönünde bir döndürme</span><span class="sxs-lookup"><span data-stu-id="40d56-114">A 45 degree clockwise rotation by using the RenderTransform property</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 <span data-ttu-id="40d56-115">Aşağıdaki örnekte de kullanan bir <xref:System.Windows.Media.RotateTransform> döndürmek için bir <xref:System.Windows.Controls.Button> 45 derece saat yönünde; ancak bu örnekte ayarlar <xref:System.Windows.UIElement.RenderTransformOrigin%2A> düğmenin (0,5, 0,5).</span><span class="sxs-lookup"><span data-stu-id="40d56-115">The following example also uses a <xref:System.Windows.Media.RotateTransform> to rotate a <xref:System.Windows.Controls.Button> 45 degrees clockwise; however, this example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> of the button to (0.5, 0.5).</span></span> <span data-ttu-id="40d56-116">Sonuç olarak, döndürme merkezini yerine sol üst köşesindeki düğmeyi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="40d56-116">As a result, the rotation is applied to the center of the button instead of to the upper-left corner.</span></span>  
  
 <span data-ttu-id="40d56-117">Aşağıdaki örnek dönüştürme sonucu aşağıda gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="40d56-117">The following illustration shows the transformation result for the example that follows.</span></span>  
  
 <span data-ttu-id="40d56-118">![Dönüştürülen ortasından düğme](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")</span><span class="sxs-lookup"><span data-stu-id="40d56-118">![A button transformed about its center](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")</span></span>  
<span data-ttu-id="40d56-119">RenderTransform özelliği RenderTransformOrigin'i ile kullanarak 45 derece döndürme (0,5, 0,5)</span><span class="sxs-lookup"><span data-stu-id="40d56-119">A 45 degree rotation by using the RenderTransform property with a RenderTransformOrigin of (0.5, 0.5)</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 <span data-ttu-id="40d56-120">Dönüştürme hakkında daha fazla bilgi için <xref:System.Windows.FrameworkElement> nesneleri bkz [dönüştüren genel bakış](transforms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="40d56-120">For more information about transforming <xref:System.Windows.FrameworkElement> objects, see the [Transforms Overview](transforms-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40d56-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40d56-121">See also</span></span>

- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="40d56-122">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="40d56-122">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="40d56-123">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="40d56-123">How-to Topics</span></span>](transformations-how-to-topics.md)
