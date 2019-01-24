---
title: 'Nasıl yapılır: Bir Olay Oluştuğunda Öğeye Dönüşüm Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], transformations as event responses
- properties [WPF], LayoutTransform
- transformations as event responses [WPF]
- properties [WPF], RenderTransform
- LayoutTransform property [WPF]
ms.assetid: 71e4327e-ca57-444c-a3cf-09fb381491a0
ms.openlocfilehash: 3862ffcb8e0dcabd2de67c495204470ac9fa6c14
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726396"
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a><span data-ttu-id="9267c-102">Nasıl yapılır: Bir Olay Oluştuğunda Öğeye Dönüşüm Uygulama</span><span class="sxs-lookup"><span data-stu-id="9267c-102">How to: Apply a Transform to an Element When an Event Occurs</span></span>
<span data-ttu-id="9267c-103">Bu örnek nasıl uygulanacağını gösterir. bir <xref:System.Windows.Media.ScaleTransform> bir olay gerçekleştiğinde.</span><span class="sxs-lookup"><span data-stu-id="9267c-103">This example shows how to apply a <xref:System.Windows.Media.ScaleTransform> when an event occurs.</span></span> <span data-ttu-id="9267c-104">Burada gösterilen diğer tür dönüştürmeleri uygulamak için kullandığınız aynı kavramdır.</span><span class="sxs-lookup"><span data-stu-id="9267c-104">The concept that is shown here is the same that you use for applying other types of transformations.</span></span> <span data-ttu-id="9267c-105">Dönüşümlerin kullanılabilir türleri hakkında daha fazla bilgi için bkz. <xref:System.Windows.Media.Transform> sınıfı veya [dönüştüren genel bakış](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9267c-105">For more information about the available types of transformations, see the <xref:System.Windows.Media.Transform> class or [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span></span>  
  
 <span data-ttu-id="9267c-106">Bu iki yöntemden biriyle öğeye dönüşüm uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9267c-106">You can apply a transform to an element in either of these two ways:</span></span>  
  
-   <span data-ttu-id="9267c-107">Bunu yaparsanız *değil* dönüşümü düzenini etkiler, kullanmak istediğiniz <xref:System.Windows.UIElement.RenderTransform%2A> öğesinin özelliği.</span><span class="sxs-lookup"><span data-stu-id="9267c-107">If you do *not* want the transform to affect layout, use the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
-   <span data-ttu-id="9267c-108">Düzen etkileyen dönüşüm istiyorsanız kullanın <xref:System.Windows.FrameworkElement.LayoutTransform%2A> öğesinin özelliği.</span><span class="sxs-lookup"><span data-stu-id="9267c-108">If you do want the transform to affect layout, use the <xref:System.Windows.FrameworkElement.LayoutTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="9267c-109">Aşağıdaki örnek geçerli bir <xref:System.Windows.Media.ScaleTransform> için <xref:System.Windows.UIElement.RenderTransform%2A> düğmesinin özelliği.</span><span class="sxs-lookup"><span data-stu-id="9267c-109">The following example applies a <xref:System.Windows.Media.ScaleTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a button.</span></span> <span data-ttu-id="9267c-110">Düğme üzerinde fareyi hareket ettirdiğinde <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> ve <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> özelliklerini <xref:System.Windows.Media.ScaleTransform> ayarlandığından `2`, düğmeyi daha büyük hale gelmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="9267c-110">When the mouse moves over the button, the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties of the <xref:System.Windows.Media.ScaleTransform> are set to `2`, which causes the button to become larger.</span></span> <span data-ttu-id="9267c-111">Düğmeyi, fareyi hareket ettirdiğinde <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> ve <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> ayarlandığından `1`, özgün boyutuna döndürmek için düğmeyi neden olur.</span><span class="sxs-lookup"><span data-stu-id="9267c-111">When the mouse moves off the button, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> are set to `1`, which causes the button to return to its original size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9267c-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="9267c-112">Example</span></span>  
 [!code-xaml[ButtonTransform#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a><span data-ttu-id="9267c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9267c-113">See also</span></span>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [<span data-ttu-id="9267c-114">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9267c-114">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
- [<span data-ttu-id="9267c-115">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="9267c-115">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
- [<span data-ttu-id="9267c-116">Yönlendirilmiş Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9267c-116">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
