---
title: 'Nasıl yapılır: Animasyon Başlangıç Değerine Animasyon Çıkış Değeri Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
ms.openlocfilehash: 820e03064d331e852a224e1f989685d7a77983db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603033"
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a><span data-ttu-id="91b44-102">Nasıl yapılır: Animasyon Başlangıç Değerine Animasyon Çıkış Değeri Ekleme</span><span class="sxs-lookup"><span data-stu-id="91b44-102">How to: Add an Animation Output Value to an Animation Starting Value</span></span>
<span data-ttu-id="91b44-103">Bu örnek, bir animasyon başlangıç değerine animasyon çıkış değeri ekleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="91b44-103">This example shows how to add an animation output value to an animation starting value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91b44-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="91b44-104">Example</span></span>  
 <span data-ttu-id="91b44-105"><xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> Özelliği, bir animasyonlu özelliğinin başlangıç değerine (temel değer) eklenen bir animasyon çıkış değeri isteyip istemediğinizi belirtir.</span><span class="sxs-lookup"><span data-stu-id="91b44-105">The <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property specifies whether you want the output value of an animation added to the starting value (base value) of an animated property.</span></span> <span data-ttu-id="91b44-106">Kullanabileceğiniz <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> en temel animasyon ve çoğu anahtar çerçeve animasyon özelliği.</span><span class="sxs-lookup"><span data-stu-id="91b44-106">You can use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="91b44-107">Daha fazla bilgi için [animasyona genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) ve [anahtar-çerçeve animasyonlara genel bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="91b44-107">For more information, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) and [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="91b44-108">Aşağıdaki örnek kullanarak etkisini gösterir <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> özelliğiyle <xref:System.Windows.Media.Animation.DoubleAnimation> ve kullanarak <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> özelliğiyle <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="91b44-108">The following example shows the effect of using the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimation> and using the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="91b44-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91b44-109">See also</span></span>
- [<span data-ttu-id="91b44-110">Yineleme Döngüsü Sırasında Animasyon Değerlerini Biriktirme</span><span class="sxs-lookup"><span data-stu-id="91b44-110">Accumulate Animation Values During Repeat Cycles</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)
- [<span data-ttu-id="91b44-111">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="91b44-111">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="91b44-112">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="91b44-112">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [<span data-ttu-id="91b44-113">Animasyon ve zamanlama</span><span class="sxs-lookup"><span data-stu-id="91b44-113">Animation and Timing</span></span>](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)
- [<span data-ttu-id="91b44-114">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="91b44-114">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
