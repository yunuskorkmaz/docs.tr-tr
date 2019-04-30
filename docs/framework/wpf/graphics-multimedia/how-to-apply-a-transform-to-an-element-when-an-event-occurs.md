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
ms.openlocfilehash: 973b9267eaef5d55176633ee80a1dc7f8b043909
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698999"
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a><span data-ttu-id="13a85-102">Nasıl yapılır: Bir Olay Oluştuğunda Öğeye Dönüşüm Uygulama</span><span class="sxs-lookup"><span data-stu-id="13a85-102">How to: Apply a Transform to an Element When an Event Occurs</span></span>
<span data-ttu-id="13a85-103">Bu örnek nasıl uygulanacağını gösterir. bir <xref:System.Windows.Media.ScaleTransform> bir olay gerçekleştiğinde.</span><span class="sxs-lookup"><span data-stu-id="13a85-103">This example shows how to apply a <xref:System.Windows.Media.ScaleTransform> when an event occurs.</span></span> <span data-ttu-id="13a85-104">Burada gösterilen diğer tür dönüştürmeleri uygulamak için kullandığınız aynı kavramdır.</span><span class="sxs-lookup"><span data-stu-id="13a85-104">The concept that is shown here is the same that you use for applying other types of transformations.</span></span> <span data-ttu-id="13a85-105">Dönüşümlerin kullanılabilir türleri hakkında daha fazla bilgi için bkz. <xref:System.Windows.Media.Transform> sınıfı veya [dönüştüren genel bakış](transforms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="13a85-105">For more information about the available types of transformations, see the <xref:System.Windows.Media.Transform> class or [Transforms Overview](transforms-overview.md).</span></span>  
  
 <span data-ttu-id="13a85-106">Bu iki yöntemden biriyle öğeye dönüşüm uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="13a85-106">You can apply a transform to an element in either of these two ways:</span></span>  
  
- <span data-ttu-id="13a85-107">Bunu yaparsanız *değil* dönüşümü düzenini etkiler, kullanmak istediğiniz <xref:System.Windows.UIElement.RenderTransform%2A> öğesinin özelliği.</span><span class="sxs-lookup"><span data-stu-id="13a85-107">If you do *not* want the transform to affect layout, use the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
- <span data-ttu-id="13a85-108">Düzen etkileyen dönüşüm istiyorsanız kullanın <xref:System.Windows.FrameworkElement.LayoutTransform%2A> öğesinin özelliği.</span><span class="sxs-lookup"><span data-stu-id="13a85-108">If you do want the transform to affect layout, use the <xref:System.Windows.FrameworkElement.LayoutTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="13a85-109">Aşağıdaki örnek geçerli bir <xref:System.Windows.Media.ScaleTransform> için <xref:System.Windows.UIElement.RenderTransform%2A> düğmesinin özelliği.</span><span class="sxs-lookup"><span data-stu-id="13a85-109">The following example applies a <xref:System.Windows.Media.ScaleTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a button.</span></span> <span data-ttu-id="13a85-110">Düğme üzerinde fareyi hareket ettirdiğinde <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> ve <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> özelliklerini <xref:System.Windows.Media.ScaleTransform> ayarlandığından `2`, düğmeyi daha büyük hale gelmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="13a85-110">When the mouse moves over the button, the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties of the <xref:System.Windows.Media.ScaleTransform> are set to `2`, which causes the button to become larger.</span></span> <span data-ttu-id="13a85-111">Düğmeyi, fareyi hareket ettirdiğinde <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> ve <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> ayarlandığından `1`, özgün boyutuna döndürmek için düğmeyi neden olur.</span><span class="sxs-lookup"><span data-stu-id="13a85-111">When the mouse moves off the button, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> are set to `1`, which causes the button to return to its original size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13a85-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="13a85-112">Example</span></span>  
 [!code-xaml[ButtonTransform#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](~/samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a><span data-ttu-id="13a85-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13a85-113">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [<span data-ttu-id="13a85-114">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="13a85-114">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="13a85-115">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="13a85-115">How-to Topics</span></span>](transformations-how-to-topics.md)
- [<span data-ttu-id="13a85-116">Yönlendirilmiş Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="13a85-116">Routed Events Overview</span></span>](../advanced/routed-events-overview.md)
