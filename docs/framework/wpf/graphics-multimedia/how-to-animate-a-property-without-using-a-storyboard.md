---
title: 'Nasıl yapılır: Görsel Taslak Kullanmadan Özelliğe Animasyon Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- non-Storyboard animation
- local animation [WPF]
- animation [WPF], non-Storyboard (local)
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
ms.openlocfilehash: 71711c0392576930e97986078ec5926ff6ca9813
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963019"
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a><span data-ttu-id="dd0e5-102">Nasıl yapılır: Görsel Taslak Kullanmadan Özelliğe Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="dd0e5-102">How to: Animate a Property Without Using a Storyboard</span></span>
<span data-ttu-id="dd0e5-103">Bu örnek, bir özelliğini kullanmadan bir özelliği bir <xref:System.Windows.Media.Animation.Storyboard>animasyon uygulamak için bir yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="dd0e5-103">This example shows one way to apply an animation to a property without using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd0e5-104">Bu işlev ' de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dd0e5-104">This functionality is not available in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="dd0e5-105">İçindeki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bir özelliği hareketlendirme hakkında daha fazla bilgi için bkz. [görsel taslak kullanarak özelliğe animasyon ekleme](how-to-animate-a-property-by-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="dd0e5-105">For information about animating a property in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md).</span></span>  
  
 <span data-ttu-id="dd0e5-106">Bir özelliğe yerel animasyon uygulamak için <xref:System.Windows.UIElement.BeginAnimation%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd0e5-106">To apply a local animation to a property, use the <xref:System.Windows.UIElement.BeginAnimation%2A> method.</span></span> <span data-ttu-id="dd0e5-107">Bu yöntem iki parametre alır: bir <xref:System.Windows.DependencyProperty> animasyon uygulanacak özelliği belirten ve bu özelliğe uygulanacak animasyon.</span><span class="sxs-lookup"><span data-stu-id="dd0e5-107">This method takes two parameters: a <xref:System.Windows.DependencyProperty> that specifies the property to animate, and the animation to apply to that property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd0e5-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="dd0e5-108">Example</span></span>  
 <span data-ttu-id="dd0e5-109">Aşağıdaki örnek, öğesinin <xref:System.Windows.Controls.Button>genişlik ve arka plan rengine nasıl animasyon ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="dd0e5-109">The following example shows how to animate the width and background color of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 <span data-ttu-id="dd0e5-110">Farklı özellik türlerini hareketlendirmek için <xref:System.Windows.Media.Animation> ad alanındaki çeşitli animasyon sınıfları mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="dd0e5-110">A variety of animation classes in the <xref:System.Windows.Media.Animation> namespace exist for animating different types of properties.</span></span> <span data-ttu-id="dd0e5-111">Hareketlendirilen özellikler hakkında daha fazla bilgi için bkz. [animasyon genel bakış](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="dd0e5-111">For more information about animating properties, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="dd0e5-112">Bağımlılık özellikleri (Bu örneklerde gösterilen özelliklerin türü) ve özellikleri hakkında daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](../advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="dd0e5-112">For more information about dependency properties (the type of properties that are shown in these examples) and their features, see [Dependency Properties Overview](../advanced/dependency-properties-overview.md).</span></span>  
  
 <span data-ttu-id="dd0e5-113">Nesneleri kullanmadan <xref:System.Windows.Media.Animation.Storyboard> hareketlendirmek için başka yollar vardır; daha fazla bilgi için bkz. [özellik animasyon tekniklerine genel bakış](property-animation-techniques-overview.md).</span><span class="sxs-lookup"><span data-stu-id="dd0e5-113">There are other ways to animate without using <xref:System.Windows.Media.Animation.Storyboard> objects; for more information, see [Property Animation Techniques Overview](property-animation-techniques-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd0e5-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd0e5-114">See also</span></span>

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Animation.Storyboard>
- [<span data-ttu-id="dd0e5-115">Özellik Animasyon Tekniklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dd0e5-115">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
- [<span data-ttu-id="dd0e5-116">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="dd0e5-116">Animation Overview</span></span>](animation-overview.md)
