---
title: 'Nasıl yapılır: Animasyon Başlangıç Değerine Animasyon Çıkış Değeri Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
ms.openlocfilehash: 945675d03a280e2394fdb0eab27c0978dc7cc320
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102615"
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a><span data-ttu-id="0f68d-102">Nasıl yapılır: Animasyon Başlangıç Değerine Animasyon Çıkış Değeri Ekleme</span><span class="sxs-lookup"><span data-stu-id="0f68d-102">How to: Add an Animation Output Value to an Animation Starting Value</span></span>
<span data-ttu-id="0f68d-103">Bu örnek, bir animasyon başlangıç değerine animasyon çıkış değeri ekleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f68d-103">This example shows how to add an animation output value to an animation starting value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f68d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f68d-104">Example</span></span>  
 <span data-ttu-id="0f68d-105"><xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> Özelliği, bir animasyonlu özelliğinin başlangıç değerine (temel değer) eklenen bir animasyon çıkış değeri isteyip istemediğinizi belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f68d-105">The <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property specifies whether you want the output value of an animation added to the starting value (base value) of an animated property.</span></span> <span data-ttu-id="0f68d-106">Kullanabileceğiniz <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> en temel animasyon ve çoğu anahtar çerçeve animasyon özelliği.</span><span class="sxs-lookup"><span data-stu-id="0f68d-106">You can use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="0f68d-107">Daha fazla bilgi için [animasyona genel bakış](animation-overview.md) ve [anahtar-çerçeve animasyonlara genel bakış](key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0f68d-107">For more information, see [Animation Overview](animation-overview.md) and [Key-Frame Animations Overview](key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="0f68d-108">Aşağıdaki örnek kullanarak etkisini gösterir <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> özelliğiyle <xref:System.Windows.Media.Animation.DoubleAnimation> ve kullanarak <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> özelliğiyle <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="0f68d-108">The following example shows the effect of using the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimation> and using the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="0f68d-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f68d-109">See also</span></span>

- [<span data-ttu-id="0f68d-110">Yineleme Döngüsü Sırasında Animasyon Değerlerini Biriktirme</span><span class="sxs-lookup"><span data-stu-id="0f68d-110">Accumulate Animation Values During Repeat Cycles</span></span>](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [<span data-ttu-id="0f68d-111">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="0f68d-111">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="0f68d-112">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0f68d-112">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="0f68d-113">Animasyon ve zamanlama ile ilgili nasıl yapılır konuları</span><span class="sxs-lookup"><span data-stu-id="0f68d-113">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
