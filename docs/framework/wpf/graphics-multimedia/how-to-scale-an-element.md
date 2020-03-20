---
title: 'Nasıl yapılır: Öğe Ölçeklendirme'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: a383ad84f1db4d937469943092a03517f68777ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187444"
---
# <a name="how-to-scale-an-element"></a><span data-ttu-id="97941-102">Nasıl yapılır: Öğe Ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="97941-102">How to: Scale an Element</span></span>
<span data-ttu-id="97941-103">Bu örnek, bir <xref:System.Windows.Media.ScaleTransform> öğeyi ölçeklendirmek için a'nın nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="97941-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to scale an element.</span></span>  
  
 <span data-ttu-id="97941-104">Öğeyi <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> belirttiğiniz faktöre göre yeniden boyutlandırmak için ve özellikleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="97941-104">Use the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties to resize the element by the factor you specify.</span></span> <span data-ttu-id="97941-105">Örneğin, 1,5 <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> değeri öğeyi özgün genişliğinin yüzde 150'sine kadar genişletir.</span><span class="sxs-lookup"><span data-stu-id="97941-105">For example, a <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> value of 1.5 stretches the element to 150 percent of its original width.</span></span> <span data-ttu-id="97941-106">0,5 değeri, <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> bir öğenin yüksekliğini yüzde 50 küçültür.</span><span class="sxs-lookup"><span data-stu-id="97941-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> value of 0.5 shrinks the height of an element by 50 percent.</span></span>  
  
 <span data-ttu-id="97941-107">Ölçek <xref:System.Windows.Media.ScaleTransform.CenterX%2A> işleminin merkezi olan noktayı belirtmek için ve <xref:System.Windows.Media.ScaleTransform.CenterY%2A> özellikleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="97941-107">Use the <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> properties to specify the point that is the center of the scale operation.</span></span> <span data-ttu-id="97941-108">Varsayılan olarak, <xref:System.Windows.Media.ScaleTransform> a, dikdörtgenin sol üst köşesine karşılık gelen noktada (0,0) ortalanır.</span><span class="sxs-lookup"><span data-stu-id="97941-108">By default, a <xref:System.Windows.Media.ScaleTransform> is centered at the point (0,0), which corresponds to the upper-left corner of the rectangle.</span></span> <span data-ttu-id="97941-109">Bu, öğeyi hareket ettirme ve aynı zamanda daha büyük görünmesini <xref:System.Windows.Media.Transform>sağlama etkisine sahiptir, çünkü bir , nesnenin bulunduğu koordinat alanını değiştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97941-109">This has the effect of moving the element and also of making it appear larger, because when you apply a <xref:System.Windows.Media.Transform>, you change the coordinate space in which the object resides.</span></span>  
  
 <span data-ttu-id="97941-110">Aşağıdaki örnek, <xref:System.Windows.Media.ScaleTransform> 50'ye 50 boyutunda a <xref:System.Windows.Shapes.Rectangle>kullanır.</span><span class="sxs-lookup"><span data-stu-id="97941-110">The following example uses a <xref:System.Windows.Media.ScaleTransform> to double the size of a 50-by-50 <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="97941-111">Her <xref:System.Windows.Media.ScaleTransform> ikisi <xref:System.Windows.Media.ScaleTransform.CenterX%2A> için 0 (varsayılan) değeri <xref:System.Windows.Media.ScaleTransform.CenterY%2A>vardır ve.</span><span class="sxs-lookup"><span data-stu-id="97941-111">The <xref:System.Windows.Media.ScaleTransform> has a value of 0 (the default) for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97941-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="97941-112">Example</span></span>  
 [!code-xaml[transformsSample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 <span data-ttu-id="97941-113">Genellikle, ölçeklenmiş <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A> nesnenin ortasına ayarlarsınız: (<xref:System.Windows.FrameworkElement.Width%2A>/2, <xref:System.Windows.FrameworkElement.Height%2A>/2).</span><span class="sxs-lookup"><span data-stu-id="97941-113">Typically, you set <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> to the center of the object that is scaled: (<xref:System.Windows.FrameworkElement.Width%2A>/2, <xref:System.Windows.FrameworkElement.Height%2A>/2).</span></span>  
  
 <span data-ttu-id="97941-114">Aşağıdaki örnek, <xref:System.Windows.Shapes.Rectangle> boyutu iki katına başka bir gösterir; ancak, <xref:System.Windows.Media.ScaleTransform> bu her ikisi <xref:System.Windows.Media.ScaleTransform.CenterX%2A> için 25 değerine sahiptir ve <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, dikdörtgenin merkezine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="97941-114">The following example shows another <xref:System.Windows.Shapes.Rectangle> that is doubled in size; however, this <xref:System.Windows.Media.ScaleTransform> has a value of 25 for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, which corresponds to the center of the rectangle.</span></span>  
  
 [!code-xaml[transformsSample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 <span data-ttu-id="97941-115">Aşağıdaki resimde iki <xref:System.Windows.Media.ScaleTransform> işlem arasındaki farkı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="97941-115">The following illustration shows the difference between the two <xref:System.Windows.Media.ScaleTransform> operations.</span></span> <span data-ttu-id="97941-116">Noktalı çizgi ölçekleme den önce dikdörtgenin boyutunu ve konumunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="97941-116">The dotted line shows the size and position of the rectangle before scaling.</span></span>  
  
 <span data-ttu-id="97941-117">![Farklı merkez noktaları ile 2x ölçekler](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span><span class="sxs-lookup"><span data-stu-id="97941-117">![2x scales with different center points](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span></span>  
<span data-ttu-id="97941-118">Aynı ScaleX ve ScaleY değerlerine sahip ancak farklı merkezlere sahip iki ÖlçekDönüştürme işlemi</span><span class="sxs-lookup"><span data-stu-id="97941-118">Two ScaleTransform operations with identical ScaleX and ScaleY values but different centers</span></span>  
  
 <span data-ttu-id="97941-119">Numunenin tamamı için [2-B Dönüşüm Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)bakın.</span><span class="sxs-lookup"><span data-stu-id="97941-119">For the complete sample, see [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97941-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97941-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [<span data-ttu-id="97941-121">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="97941-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="97941-122">Nasıl Dır Konular</span><span class="sxs-lookup"><span data-stu-id="97941-122">How-to Topics</span></span>](transformations-how-to-topics.md)
