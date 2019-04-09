---
title: 'Nasıl yapılır: Görsel Taslakla Özelliğe Animasyon Ekledikten Sonra Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], changing property values after
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
ms.openlocfilehash: 2e1389392c6465ed56b2c71e53b2e3c1947acbe2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188324"
---
# <a name="how-to-set-a-property-after-animating-it-with-a-storyboard"></a><span data-ttu-id="a9277-102">Nasıl yapılır: Görsel Taslakla Özelliğe Animasyon Ekledikten Sonra Ayarlama</span><span class="sxs-lookup"><span data-stu-id="a9277-102">How to: Set a Property After Animating It with a Storyboard</span></span>
<span data-ttu-id="a9277-103">Bazı durumlarda, animasyon sonra bir özelliğin değerini değiştiremezsiniz görünebilir.</span><span class="sxs-lookup"><span data-stu-id="a9277-103">In some cases, it might appear that you can't change the value of a property after it has been animated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9277-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9277-104">Example</span></span>  
 <span data-ttu-id="a9277-105">Aşağıdaki örnekte, bir <xref:System.Windows.Media.Animation.Storyboard> rengine animasyon uygulamak için kullanılan bir <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="a9277-105">In the following example, a <xref:System.Windows.Media.Animation.Storyboard> is used to animate the color of a <xref:System.Windows.Media.SolidColorBrush>.</span></span> <span data-ttu-id="a9277-106">Düğmeye tıklandığında film şeridi tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="a9277-106">The storyboard is triggered when the button is clicked.</span></span> <span data-ttu-id="a9277-107"><xref:System.Windows.Media.Animation.Timeline.Completed> Olayı, böylece programın bildirim işlenir, <xref:System.Windows.Media.Animation.ColorAnimation> tamamlar.</span><span class="sxs-lookup"><span data-stu-id="a9277-107">The <xref:System.Windows.Media.Animation.Timeline.Completed> event is handled so that the program is notified when the <xref:System.Windows.Media.Animation.ColorAnimation> completes.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton1Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## <a name="example"></a><span data-ttu-id="a9277-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9277-108">Example</span></span>  
 <span data-ttu-id="a9277-109">Sonra <xref:System.Windows.Media.Animation.ColorAnimation> fırça rengini Mavi olarak değiştirmek için programın denemeleri tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="a9277-109">After the <xref:System.Windows.Media.Animation.ColorAnimation> completes, the program attempts to change the brush's color to blue.</span></span>  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 <span data-ttu-id="a9277-110">Önceki kodun herhangi bir şey gibi görünmüyor: değer olan fırça sarı olarak kalır verdiği <xref:System.Windows.Media.Animation.ColorAnimation> fırça animasyonlu.</span><span class="sxs-lookup"><span data-stu-id="a9277-110">The previous code doesn't appear to do anything: the brush remains yellow, which is the value supplied by the <xref:System.Windows.Media.Animation.ColorAnimation> that animated the brush.</span></span> <span data-ttu-id="a9277-111">Temel özellik değeri (Temel), aslında mavi olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="a9277-111">The underlying property value (the base value) is actually changed to blue.</span></span> <span data-ttu-id="a9277-112">Ancak, etkin veya geçerli bir değer sarı kalır çünkü <xref:System.Windows.Media.Animation.ColorAnimation> hala temel değerin geçersiz kılıyor.</span><span class="sxs-lookup"><span data-stu-id="a9277-112">However, the effective, or current, value remains yellow because the <xref:System.Windows.Media.Animation.ColorAnimation> is still overriding the base value.</span></span> <span data-ttu-id="a9277-113">Temel değerin yeniden etkili değer olmasını istiyorsanız, animasyonu özelliği etkilemesini durdurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a9277-113">If you want the base value to become the effective value again, you must stop the animation from influencing the property.</span></span> <span data-ttu-id="a9277-114">Görsel taslak animasyonları ile bunun için üç yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="a9277-114">There are three ways to do this with storyboard animations:</span></span>  
  
-   <span data-ttu-id="a9277-115">Animasyonun ayarlamak <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özelliği</span><span class="sxs-lookup"><span data-stu-id="a9277-115">Set the animation's <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property to</span></span> <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
  
-   <span data-ttu-id="a9277-116">Tüm film şeridini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="a9277-116">Remove the entire Storyboard.</span></span>  
  
-   <span data-ttu-id="a9277-117">Animasyon bireysel özellikten kaldırın.</span><span class="sxs-lookup"><span data-stu-id="a9277-117">Remove the animation from the individual property.</span></span>  
  
## <a name="set-the-animations-fillbehavior-property-to-stop"></a><span data-ttu-id="a9277-118">Animasyonun FillBehavior özelliği Durma noktasına ayarlayın</span><span class="sxs-lookup"><span data-stu-id="a9277-118">Set the animation's FillBehavior property to Stop</span></span>  
 <span data-ttu-id="a9277-119">Ayarlayarak <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> için <xref:System.Windows.Media.Animation.FillBehavior.Stop>, etkin süresinin sonuna ulaştıktan sonra hedef özelliği etkileyen durdurmak için animasyon söyleyin.</span><span class="sxs-lookup"><span data-stu-id="a9277-119">By setting <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, you tell the animation to stop affecting its target property after it reaches the end of its active period.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton2Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## <a name="remove-the-entire-storyboard"></a><span data-ttu-id="a9277-120">Tüm film şeridini Kaldır</span><span class="sxs-lookup"><span data-stu-id="a9277-120">Remove the entire storyboard</span></span>  
 <span data-ttu-id="a9277-121">Kullanarak bir <xref:System.Windows.Media.Animation.RemoveStoryboard> tetikleyici veya <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> yöntemi, hedef özelliklerini etkileyen durdurmak için görsel taslak animasyonları söyleyin.</span><span class="sxs-lookup"><span data-stu-id="a9277-121">By using a <xref:System.Windows.Media.Animation.RemoveStoryboard> trigger or the <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> method, you tell the storyboard animations to stop affecting their target properties.</span></span> <span data-ttu-id="a9277-122">Bu yaklaşım ve ayarı arasındaki farkı <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özelliğidir, film şeridini kaldırabilirsiniz, her zaman, while <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özelliği yalnızca bir etkisi animasyon etkin süresinin sona erdiğinde.</span><span class="sxs-lookup"><span data-stu-id="a9277-122">The difference between this approach and setting the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property is that you can remove the storyboard at anytime, while the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property only has an effect when the animation reaches the end of its active period.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton3Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## <a name="remove-an-animation-from-an-individual-property"></a><span data-ttu-id="a9277-123">Bir animasyonu tek bir özelliği Kaldır</span><span class="sxs-lookup"><span data-stu-id="a9277-123">Remove an animation from an individual property</span></span>  
 <span data-ttu-id="a9277-124">Animasyonun özellik etkilemesini durdurmak için başka bir teknik kullanmaktır <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> animasyon uygulanan nesneyi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a9277-124">Another technique to stop an animation from affecting a property is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> method of the object being animated.</span></span> <span data-ttu-id="a9277-125">İlk parametre olarak animasyon uygulanan bir özellik belirtin ve `null` ikinci olarak.</span><span class="sxs-lookup"><span data-stu-id="a9277-125">Specify the property being animated as the first parameter and `null` as the second.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton4Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 <span data-ttu-id="a9277-126">Bu teknik, görsel taslak olmayan animasyon için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a9277-126">This technique also works for non-storyboard animations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9277-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9277-127">See also</span></span>

- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.Animation.RemoveStoryboard>
- [<span data-ttu-id="a9277-128">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="a9277-128">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="a9277-129">Özellik Animasyon Tekniklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a9277-129">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
