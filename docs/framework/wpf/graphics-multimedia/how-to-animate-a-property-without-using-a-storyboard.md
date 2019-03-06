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
ms.openlocfilehash: b76afeb0187065ff07c832363d3a52896aa36822
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371175"
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a><span data-ttu-id="34ecd-102">Nasıl yapılır: Görsel Taslak Kullanmadan Özelliğe Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="34ecd-102">How to: Animate a Property Without Using a Storyboard</span></span>
<span data-ttu-id="34ecd-103">Bu örnek, kullanmadan özelliğe animasyon uygulamak için bir yol gösterir. bir <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="34ecd-103">This example shows one way to apply an animation to a property without using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34ecd-104">Bu işlevselliği kullanıma sunulmadı [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="34ecd-104">This functionality is not available in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="34ecd-105">Bir özelliğe animasyon ekleme hakkında bilgi için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], bkz: [görsel taslak kullanarak özelliğe animasyon ekleme](how-to-animate-a-property-by-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="34ecd-105">For information about animating a property in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md).</span></span>  
  
 <span data-ttu-id="34ecd-106">Bir özellik için bir yerel animasyon uygulamak için kullanma <xref:System.Windows.UIElement.BeginAnimation%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="34ecd-106">To apply a local animation to a property, use the <xref:System.Windows.UIElement.BeginAnimation%2A> method.</span></span> <span data-ttu-id="34ecd-107">Bu yöntem iki parametre alır: bir <xref:System.Windows.DependencyProperty> animasyon uygulamak için özellik ve bu özelliğe animasyon belirtir.</span><span class="sxs-lookup"><span data-stu-id="34ecd-107">This method takes two parameters: a <xref:System.Windows.DependencyProperty> that specifies the property to animate, and the animation to apply to that property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34ecd-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="34ecd-108">Example</span></span>  
 <span data-ttu-id="34ecd-109">Aşağıdaki örnekte, genişlik ve arka plan rengini animasyon ekleme işlemi gösterilmektedir bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="34ecd-109">The following example shows how to animate the width and background color of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 <span data-ttu-id="34ecd-110">Animasyon sınıfları çeşitli <xref:System.Windows.Media.Animation> ad mevcut özellikler farklı türde animasyon için.</span><span class="sxs-lookup"><span data-stu-id="34ecd-110">A variety of animation classes in the <xref:System.Windows.Media.Animation> namespace exist for animating different types of properties.</span></span> <span data-ttu-id="34ecd-111">Özellikleri hakkında daha fazla bilgi için bkz. [animasyona genel bakış](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="34ecd-111">For more information about animating properties, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="34ecd-112">Bağımlılık özellikleri (Bu örneklerde gösterilen özellikler türü) ve bunların özellikleri hakkında daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](../advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="34ecd-112">For more information about dependency properties (the type of properties that are shown in these examples) and their features, see [Dependency Properties Overview](../advanced/dependency-properties-overview.md).</span></span>  
  
 <span data-ttu-id="34ecd-113">Kullanmadan animasyon uygulamak için başka bir yöntemle <xref:System.Windows.Media.Animation.Storyboard> nesnelerini; daha fazla bilgi için [özellik Animasyon Tekniklerine Genel Bakış](property-animation-techniques-overview.md).</span><span class="sxs-lookup"><span data-stu-id="34ecd-113">There are other ways to animate without using <xref:System.Windows.Media.Animation.Storyboard> objects; for more information, see [Property Animation Techniques Overview](property-animation-techniques-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34ecd-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34ecd-114">See also</span></span>
- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Animation.Storyboard>
- [<span data-ttu-id="34ecd-115">Özellik Animasyon Tekniklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="34ecd-115">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
- [<span data-ttu-id="34ecd-116">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="34ecd-116">Animation Overview</span></span>](animation-overview.md)
