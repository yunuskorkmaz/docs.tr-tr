---
title: "Nasıl yapılır: Animasyon Başlangıç Değerine Animasyon Çıkış Değeri Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a670a29e4bd982418ac92ef0e2ac65635763671
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a><span data-ttu-id="ae32d-102">Nasıl yapılır: Animasyon Başlangıç Değerine Animasyon Çıkış Değeri Ekleme</span><span class="sxs-lookup"><span data-stu-id="ae32d-102">How to: Add an Animation Output Value to an Animation Starting Value</span></span>
<span data-ttu-id="ae32d-103">Bu örnek bir animasyon başlangıç değerine animasyon çıkış değeri eklemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="ae32d-103">This example shows how to add an animation output value to an animation starting value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae32d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae32d-104">Example</span></span>  
 <span data-ttu-id="ae32d-105"><xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> Özelliği, animasyonlu bir özelliğin başlangıç değerine (temel değer) eklenen bir animasyon çıkış değeri isteyip istemediğinizi belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae32d-105">The <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property specifies whether you want the output value of an animation added to the starting value (base value) of an animated property.</span></span> <span data-ttu-id="ae32d-106">Kullanabileceğiniz <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> en temel animasyonları ve çoğu anahtar çerçeve animasyonları özelliği.</span><span class="sxs-lookup"><span data-stu-id="ae32d-106">You can use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="ae32d-107">Daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) ve [anahtar çerçeve animasyonları genel bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ae32d-107">For more information, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) and [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="ae32d-108">Aşağıdaki örnek kullanmanın etkisini gösterir <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> özelliğiyle <xref:System.Windows.Media.Animation.DoubleAnimation> ve kullanarak <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> özelliğiyle <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="ae32d-108">The following example shows the effect of using the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimation> and using the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="ae32d-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ae32d-109">See Also</span></span>  
 [<span data-ttu-id="ae32d-110">Yineleme Döngüsü Sırasında Animasyon Değerlerini Biriktirme</span><span class="sxs-lookup"><span data-stu-id="ae32d-110">Accumulate Animation Values During Repeat Cycles</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [<span data-ttu-id="ae32d-111">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="ae32d-111">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="ae32d-112">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ae32d-112">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="ae32d-113">Animasyon ve zamanlama</span><span class="sxs-lookup"><span data-stu-id="ae32d-113">Animation and Timing</span></span>](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="ae32d-114">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="ae32d-114">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
