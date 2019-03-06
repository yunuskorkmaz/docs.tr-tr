---
title: 'Nasıl yapılır: Bir Animasyonu Hızlandırma veya Yavaşlatma'
ms.date: 03/30/2017
helpviewer_keywords:
- decelerating animation [WPF]
- accelerating animation [WPF]
- animation [WPF], accelerating
- animation [WPF], decelerating
ms.assetid: 4f383b2c-f94d-4a4e-9a06-f56f5dae95f9
ms.openlocfilehash: d4fcaf4a684c37590f27d603ef5cb2c86a6fb854
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376253"
---
# <a name="how-to-accelerate-or-decelerate-an-animation"></a><span data-ttu-id="394fc-102">Nasıl yapılır: Bir Animasyonu Hızlandırma veya Yavaşlatma</span><span class="sxs-lookup"><span data-stu-id="394fc-102">How to: Accelerate or Decelerate an Animation</span></span>
<span data-ttu-id="394fc-103">Bu örnek, animasyonun hızlandırın ve zaman içinde yavaşlatma sağlamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="394fc-103">This example demonstrates how to make an animation accelerate and decelerate over time.</span></span> <span data-ttu-id="394fc-104">Aşağıdaki örnekte, birkaç dikdörtgenler farklı ile animasyonlar animasyonlu <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> ve <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> ayarları.</span><span class="sxs-lookup"><span data-stu-id="394fc-104">In the following example, several rectangles are animated by animations with different <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> and <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="394fc-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="394fc-105">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AccelDecelExample.xaml#1)]  
  
 <span data-ttu-id="394fc-106">Bu örnekte, kod çıkarıldı.</span><span class="sxs-lookup"><span data-stu-id="394fc-106">Code has been omitted from this example.</span></span> <span data-ttu-id="394fc-107">Tüm kod için bkz: [animasyon zamanlama davranış (C#)](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp) veya [animasyon zamanlama davranış (Visual Basic)](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic).</span><span class="sxs-lookup"><span data-stu-id="394fc-107">For the complete code, see the [Animation Timing Behavior (C#)](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp) or [Animation Timing Behavior (Visual Basic)](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic).</span></span>
