---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak Kenarlık Kalınlığına Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: 884b62e88c347449ae39caa9c028d09db39b9f4b
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344701"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a><span data-ttu-id="00b95-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak Kenarlık Kalınlığına Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="00b95-102">How to: Animate the Thickness of a Border by Using Key Frames</span></span>
<span data-ttu-id="00b95-103">Bu örnek, <xref:System.Windows.Controls.Control.BorderThickness%2A> bir <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="00b95-103">This example shows how to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00b95-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="00b95-104">Example</span></span>  
 <span data-ttu-id="00b95-105">Aşağıdaki örnek, <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> bir <xref:System.Windows.Controls.Border>. özelliğini <xref:System.Windows.Controls.Control.BorderThickness%2A> canlandırmak için sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="00b95-105">The following example uses the <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="00b95-106">Bu animasyon aşağıdaki şekilde üç anahtar kare kullanır:</span><span class="sxs-lookup"><span data-stu-id="00b95-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="00b95-107">İlk yarısında ikinci sırasında, yavaş <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> yavaş sınır kalınlığını artırmak için sınıfın bir örnek kullanır.</span><span class="sxs-lookup"><span data-stu-id="00b95-107">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> class to gradually increase the thickness of the border.</span></span> <span data-ttu-id="00b95-108">Örnek, <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> değerler arasında düzgün bir doğrusal artış oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="00b95-108">The example uses <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> to create a smooth linear increase between values.</span></span>  
  
2. <span data-ttu-id="00b95-109">Sonraki yarım saniyenin sonunda, aniden sınır <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> kalınlığını artırmak için sınıfın bir örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="00b95-109">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> class to suddenly increase the thickness of the border.</span></span> <span data-ttu-id="00b95-110">Değerler arasında ani atlar <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> oluşturmak türetilen gibi ayrık anahtar kareler, yani animasyon hareketi sarsıntılı.</span><span class="sxs-lookup"><span data-stu-id="00b95-110">Discrete key frames like those derived from <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
3. <span data-ttu-id="00b95-111">Son iki saniye boyunca, kenarlık <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> kalınlığını azaltmak için sınıfın bir örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="00b95-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> class to decrease the thickness of the border.</span></span> <span data-ttu-id="00b95-112">Bu tür spline anahtar <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> çerçeveleri özelliğin <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> değerlerine göre değerler arasında değişken bir geçiş oluşturmak türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="00b95-112">Spline key frames like those derived from <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="00b95-113">Bu anahtar karede, animasyon yavaş başlar ve zaman diliminin sonuna doğru katlanarak hızlandırılır.</span><span class="sxs-lookup"><span data-stu-id="00b95-113">In this key frame, the animation starts off slow and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="00b95-114">Tam örnek için [Anahtar Çerçeve Animasyon Örneği'ne](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)bakın.</span><span class="sxs-lookup"><span data-stu-id="00b95-114">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b95-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00b95-115">See also</span></span>

- <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>
- [<span data-ttu-id="00b95-116">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="00b95-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="00b95-117">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="00b95-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
- [<span data-ttu-id="00b95-118">BorderThickness Değerine Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="00b95-118">Animate a BorderThickness Value</span></span>](../controls/how-to-animate-a-borderthickness-value.md)
