---
title: 'Nasıl yapılır: Öğe Ölçeklendirme'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: e95a5ed091621d27a462bc691e62a5f00bab49ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504320"
---
# <a name="how-to-scale-an-element"></a><span data-ttu-id="5da39-102">Nasıl yapılır: Öğe Ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="5da39-102">How to: Scale an Element</span></span>
<span data-ttu-id="5da39-103">Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.ScaleTransform> öğe ölçeklendirme için.</span><span class="sxs-lookup"><span data-stu-id="5da39-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to scale an element.</span></span>  
  
 <span data-ttu-id="5da39-104">Kullanım <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> ve <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> Belirttiğiniz faktörle öğeyi yeniden boyutlandırmak için özellikler.</span><span class="sxs-lookup"><span data-stu-id="5da39-104">Use the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties to resize the element by the factor you specify.</span></span> <span data-ttu-id="5da39-105">Örneğin, bir <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> özgün genişliğinin yüzde 150 öğesine 1.5 değerini uzatır.</span><span class="sxs-lookup"><span data-stu-id="5da39-105">For example, a <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> value of 1.5 stretches the element to 150 percent of its original width.</span></span> <span data-ttu-id="5da39-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 0,5 değeri öğenin yüksekliğini yüzde 50 küçültür.</span><span class="sxs-lookup"><span data-stu-id="5da39-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> value of 0.5 shrinks the height of an element by 50 percent.</span></span>  
  
 <span data-ttu-id="5da39-107">Kullanım <xref:System.Windows.Media.ScaleTransform.CenterX%2A> ve <xref:System.Windows.Media.ScaleTransform.CenterY%2A> ölçeklendirme işleminin merkez noktası belirtmek için özellikleri.</span><span class="sxs-lookup"><span data-stu-id="5da39-107">Use the <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> properties to specify the point that is the center of the scale operation.</span></span> <span data-ttu-id="5da39-108">Varsayılan olarak, bir <xref:System.Windows.Media.ScaleTransform> dikdörtgenin sol üst köşesinin karşılık gelir (0,0) noktasında ortalanır.</span><span class="sxs-lookup"><span data-stu-id="5da39-108">By default, a <xref:System.Windows.Media.ScaleTransform> is centered at the point (0,0), which corresponds to the upper-left corner of the rectangle.</span></span> <span data-ttu-id="5da39-109">Bu öğeyi taşımak ve ayrıca uyguladığınızda olduğundan daha büyük görünmesini sağlama etkisi bir <xref:System.Windows.Media.Transform>, nesnenin bulunduğu koordinat değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5da39-109">This has the effect of moving the element and also of making it appear larger, because when you apply a <xref:System.Windows.Media.Transform>, you change the coordinate space in which the object resides.</span></span>  
  
 <span data-ttu-id="5da39-110">Aşağıdaki örnekte bir <xref:System.Windows.Media.ScaleTransform> boyutu 50-tarafından-50 çift <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="5da39-110">The following example uses a <xref:System.Windows.Media.ScaleTransform> to double the size of a 50-by-50 <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="5da39-111"><xref:System.Windows.Media.ScaleTransform> Her ikisi için 0 (varsayılan) değerini içeren <xref:System.Windows.Media.ScaleTransform.CenterX%2A> ve <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span><span class="sxs-lookup"><span data-stu-id="5da39-111">The <xref:System.Windows.Media.ScaleTransform> has a value of 0 (the default) for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5da39-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="5da39-112">Example</span></span>  
 [!code-xaml[transformsSample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 <span data-ttu-id="5da39-113">Genellikle, ayarladığınız <xref:System.Windows.Media.ScaleTransform.CenterX%2A> ve <xref:System.Windows.Media.ScaleTransform.CenterY%2A> ölçeklendirilir nesnenin Merkezi: (<xref:System.Windows.FrameworkElement.Width%2A>/2,  <xref:System.Windows.FrameworkElement.Height%2A> /2).</span><span class="sxs-lookup"><span data-stu-id="5da39-113">Typically, you set <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> to the center of the object that is scaled: (<xref:System.Windows.FrameworkElement.Width%2A>/2, <xref:System.Windows.FrameworkElement.Height%2A>/2).</span></span>  
  
 <span data-ttu-id="5da39-114">Aşağıdaki örnek başka gösterir <xref:System.Windows.Shapes.Rectangle> ; boyutundaki işledi ancak bu <xref:System.Windows.Media.ScaleTransform> her ikisi için 25 değerini içeren <xref:System.Windows.Media.ScaleTransform.CenterX%2A> ve <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, dikdörtgen merkezine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="5da39-114">The following example shows another <xref:System.Windows.Shapes.Rectangle> that is doubled in size; however, this <xref:System.Windows.Media.ScaleTransform> has a value of 25 for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, which corresponds to the center of the rectangle.</span></span>  
  
 [!code-xaml[transformsSample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 <span data-ttu-id="5da39-115">İkisi arasındaki fark aşağıdaki çizimde <xref:System.Windows.Media.ScaleTransform> operations.</span><span class="sxs-lookup"><span data-stu-id="5da39-115">The following illustration shows the difference between the two <xref:System.Windows.Media.ScaleTransform> operations.</span></span> <span data-ttu-id="5da39-116">Noktalı çizgi ölçeklendirmeden önce boyutunu ve konumunu dikdörtgenin gösterir.</span><span class="sxs-lookup"><span data-stu-id="5da39-116">The dotted line shows the size and position of the rectangle before scaling.</span></span>  
  
 <span data-ttu-id="5da39-117">![Farklı orta noktaları 2 x ölçekler](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span><span class="sxs-lookup"><span data-stu-id="5da39-117">![2x scales with different center points](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span></span>  
<span data-ttu-id="5da39-118">Aynı ScaleX ve ScaleY değerleri ancak farklı olan iki ScaleTransform işlem</span><span class="sxs-lookup"><span data-stu-id="5da39-118">Two ScaleTransform operations with identical ScaleX and ScaleY values but different centers</span></span>  
  
 <span data-ttu-id="5da39-119">Tam bir örnek için bkz. [2B dönüşüm örnek](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="5da39-119">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5da39-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5da39-120">See also</span></span>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [<span data-ttu-id="5da39-121">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5da39-121">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
- [<span data-ttu-id="5da39-122">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="5da39-122">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
