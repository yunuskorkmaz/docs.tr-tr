---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Dizeye Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: c954806ca901bbfc3ab6d4bbcc237cd0e404f154
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344646"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a><span data-ttu-id="35374-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Dizeye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="35374-102">How to: Animate a String by Using Key Frames</span></span>
<span data-ttu-id="35374-103">Bu örnekte, anahtar çerçeveleri kullanarak, bu örnekte bir denetimin <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği olan bir <xref:System.Windows.Controls.Button> dize nasıl animasyona alınır gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="35374-103">This example shows how to animate a string, which in this example is the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35374-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="35374-104">Example</span></span>  
 <span data-ttu-id="35374-105">Aşağıdaki örnek, <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> bir <xref:System.Windows.Controls.Button>. özelliğini <xref:System.Windows.Controls.ContentControl.Content%2A> canlandırmak için sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="35374-105">The following example uses the <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="35374-106">Bu örnekteki tüm anahtar kareler <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> sınıfın bir örneğini kullanır, çünkü anahtar çerçevelerle oluşturulan bir dize animasyonu yalnızca ayrı anahtar çerçeveleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="35374-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> class because a string animation that is created with key frames can only use discrete key frames.</span></span> <span data-ttu-id="35374-107">Değerler arasında ani <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> sıçramalar oluşturmak gibi ayrık anahtar kareler, yani animasyondeğişiklikleri hızlı bir şekilde oluşur ve ince değildir.</span><span class="sxs-lookup"><span data-stu-id="35374-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> create sudden jumps between values, that is, changes to the animation occur quickly and are not subtle.</span></span>  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="35374-108">Tam örnek için [Anahtar Çerçeve Animasyon Örneği'ne](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)bakın.</span><span class="sxs-lookup"><span data-stu-id="35374-108">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35374-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35374-109">See also</span></span>

- <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.ContentControl.Content%2A>
- <xref:System.Windows.Controls.Button>
- <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>
- [<span data-ttu-id="35374-110">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="35374-110">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="35374-111">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="35374-111">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
