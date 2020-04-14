---
title: 'Nasıl yapılır: Bir Animasyonu Hızlandırma veya Yavaşlatma'
ms.date: 03/30/2017
helpviewer_keywords:
- decelerating animation [WPF]
- accelerating animation [WPF]
- animation [WPF], accelerating
- animation [WPF], decelerating
ms.assetid: 4f383b2c-f94d-4a4e-9a06-f56f5dae95f9
ms.openlocfilehash: 7ab55ba44b866a992b9021284f170858f0108d15
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243017"
---
# <a name="how-to-accelerate-or-decelerate-an-animation"></a><span data-ttu-id="baed5-102">Nasıl yapilir: Animasyonu hızlandırma veya yavaşlama</span><span class="sxs-lookup"><span data-stu-id="baed5-102">How to: Accelerate or decelerate an animation</span></span>

<span data-ttu-id="baed5-103">Bu örnek, bir animasyonun zaman içinde nasıl hızlandığını ve yavaşlamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="baed5-103">This example demonstrates how to make an animation accelerate and decelerate over time.</span></span> <span data-ttu-id="baed5-104">Aşağıdaki örnekte, birkaç dikdörtgen farklı <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> ve <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> ayarları ile animasyonlar tarafından animasyonlu.</span><span class="sxs-lookup"><span data-stu-id="baed5-104">In the following example, several rectangles are animated by animations with different <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> and <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="baed5-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="baed5-105">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AccelDecelExample.xaml#1)]  
  
 <span data-ttu-id="baed5-106">Kod bu örnekten atlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="baed5-106">Code has been omitted from this example.</span></span> <span data-ttu-id="baed5-107">Kodun tamamı için [Animasyon Zamanlama Davranışı (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp) veya [Animasyon Zamanlama Davranışı (Visual Basic)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic)bakın.</span><span class="sxs-lookup"><span data-stu-id="baed5-107">For the complete code, see the [Animation Timing Behavior (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp) or [Animation Timing Behavior (Visual Basic)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic).</span></span>
