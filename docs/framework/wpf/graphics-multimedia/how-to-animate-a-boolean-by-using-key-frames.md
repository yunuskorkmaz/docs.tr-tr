---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Boole Değerine Animasyon Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Booleans [WPF], animating with key frames
- animation [WPF], Booleans with key frames
- key frames [WPF], animating Booleans with
ms.assetid: 4b0fac96-6231-4fcf-9775-4dd673ddc785
ms.openlocfilehash: 35704996dcf21fe463169dc13572941bcd8fbad1
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344924"
---
# <a name="how-to-animate-a-boolean-by-using-key-frames"></a><span data-ttu-id="02bb6-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Boole Değerine Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="02bb6-102">How to: Animate a Boolean by Using Key Frames</span></span>
<span data-ttu-id="02bb6-103">Bu örnek, anahtar çerçeveleri kullanarak bir <xref:System.Windows.Controls.Button> denetimin Boolean özellik değerini nasıl canlandıracaklarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="02bb6-103">This example shows how to animate the Boolean property value of a <xref:System.Windows.Controls.Button> control by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02bb6-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="02bb6-104">Example</span></span>  
 <span data-ttu-id="02bb6-105">Aşağıdaki örnek, <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> bir <xref:System.Windows.UIElement.IsEnabled%2A> <xref:System.Windows.Controls.Button> denetimin özelliğini canlandırmak için sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="02bb6-105">The following example uses the <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> class to animate the <xref:System.Windows.UIElement.IsEnabled%2A> property of a <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="02bb6-106">Bu örnekteki tüm anahtar kareler sınıfın <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> bir örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="02bb6-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> class.</span></span> <span data-ttu-id="02bb6-107">Değerler arasında ani <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> atlar oluşturmak gibi ayrık anahtar kareler, yani animasyonun hareketi sarsıntılı.</span><span class="sxs-lookup"><span data-stu-id="02bb6-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-csharp[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/BooleanAnimationUsingKeyFramesExample.cs#booleananimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/booleananimationusingkeyframesexample.vb#booleananimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/BooleanAnimationUsingKeyFramesExample.xaml#booleananimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="02bb6-108">Tam örnek için [Anahtar Çerçeve Animasyon Örneği'ne](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)bakın.</span><span class="sxs-lookup"><span data-stu-id="02bb6-108">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02bb6-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02bb6-109">See also</span></span>

- <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>
- <xref:System.Windows.UIElement.IsEnabled%2A>
- <xref:System.Windows.Controls.Button>
- [<span data-ttu-id="02bb6-110">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="02bb6-110">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="02bb6-111">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="02bb6-111">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
