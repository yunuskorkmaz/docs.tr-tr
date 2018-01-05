---
title: "Nasıl yapılır: Yineleme Döngüsü Sırasında Animasyon Değerlerini Biriktirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- accumulating animation values across repeating cycles [WPF]
- animation [WPF], accumulating values across repeating cycles
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96a91856cdfcf1ca7ae87e8e571306170feecb7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-accumulate-animation-values-during-repeat-cycles"></a><span data-ttu-id="879e1-102">Nasıl yapılır: Yineleme Döngüsü Sırasında Animasyon Değerlerini Biriktirme</span><span class="sxs-lookup"><span data-stu-id="879e1-102">How to: Accumulate Animation Values During Repeat Cycles</span></span>
<span data-ttu-id="879e1-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> Yinelenen döngüler arasında animasyon değerlerini birikmesine özelliği.</span><span class="sxs-lookup"><span data-stu-id="879e1-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate animation values across repeating cycles.</span></span>  
  
## <a name="example"></a><span data-ttu-id="879e1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="879e1-104">Example</span></span>  
 <span data-ttu-id="879e1-105">Kullanım <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> Yinelenen döngüler arasında bir animasyonun temel değerlerini birikmesine özelliği.</span><span class="sxs-lookup"><span data-stu-id="879e1-105">Use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate base values of an animation across repeating cycles.</span></span> <span data-ttu-id="879e1-106">Örneğin, bir animasyon 9 kez yinelenmesi ayarlarsanız (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9 x") ve 10-15 arasında animasyon için özelliğini ayarlayın (= 10 = 15), özelliği 10-15'ten 20 ikinci döngü sırasında ilk döngü sırasında 15'e canlandırır , üçüncü döngü vb. sırasında 25 20.</span><span class="sxs-lookup"><span data-stu-id="879e1-106">For example, if you set an animation to repeat 9 times (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9x") and you set the property to animate between 10 and 15 (From = 10 To = 15), the property animates from 10 to 15 during the first cycle, from 15 to 20 during the second cycle, from 20 to 25 during the third cycle, and so on.</span></span> <span data-ttu-id="879e1-107">Bu nedenle, her animasyon döngüsünün önceki animasyon döngüsünün bitiş animasyon değerden temel değer olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="879e1-107">Hence, each animation cycle uses the ending animation value from the previous animation cycle as its base value.</span></span>  
  
 <span data-ttu-id="879e1-108">Kullanabileceğiniz `IsCumulative` en temel animasyonları ve çoğu anahtar çerçeve animasyonları özelliği.</span><span class="sxs-lookup"><span data-stu-id="879e1-108">You can use the `IsCumulative` property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="879e1-109">Daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) ve [anahtar çerçeve animasyonları genel bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="879e1-109">For more information, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) and [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="879e1-110">Aşağıdaki örnek, dört dikdörtgenin genişliği animasyon tarafından bu davranış gösterir.</span><span class="sxs-lookup"><span data-stu-id="879e1-110">The following example shows this behavior by animating the width of four rectangles.</span></span> <span data-ttu-id="879e1-111">Örnek:</span><span class="sxs-lookup"><span data-stu-id="879e1-111">The example:</span></span>  
  
-   <span data-ttu-id="879e1-112">İlk dikdörtgen canlandırır <xref:System.Windows.Media.Animation.DoubleAnimation> ve ayarlar <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="879e1-112">Animates the first rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to `true`.</span></span>  
  
-   <span data-ttu-id="879e1-113">İkinci dikdörtgen canlandırır <xref:System.Windows.Media.Animation.DoubleAnimation> ve ayarlar <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> varsayılan değerini özelliğine `false`.</span><span class="sxs-lookup"><span data-stu-id="879e1-113">Animates the second rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to the default value of `false`.</span></span>  
  
-   <span data-ttu-id="879e1-114">Üçüncü dikdörtgen canlandırır <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> ve ayarlar <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="879e1-114">Animates the third rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `true`.</span></span>  
  
-   <span data-ttu-id="879e1-115">Son dikdörtgen canlandırır <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> ve ayarlar <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> özelliğine `false`.</span><span class="sxs-lookup"><span data-stu-id="879e1-115">Animates the last rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `false`.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="879e1-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="879e1-116">See Also</span></span>  
 [<span data-ttu-id="879e1-117">Animasyon Başlangıç Değerine Animasyon Çıkış Değeri Ekleme</span><span class="sxs-lookup"><span data-stu-id="879e1-117">Add an Animation Output Value to an Animation Starting Value</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-add-an-animation-output-value-to-an-animation-starting-value.md)  
 [<span data-ttu-id="879e1-118">Animasyonu Yineleme</span><span class="sxs-lookup"><span data-stu-id="879e1-118">Repeat an Animation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md)  
 [<span data-ttu-id="879e1-119">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="879e1-119">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="879e1-120">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="879e1-120">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="879e1-121">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="879e1-121">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
