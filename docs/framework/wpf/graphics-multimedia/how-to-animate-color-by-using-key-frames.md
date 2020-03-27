---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak Renge Animasyon Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
ms.openlocfilehash: 8a444706f7541b52722ab8257a88e76c3e1b0938
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344743"
---
# <a name="how-to-animate-color-by-using-key-frames"></a><span data-ttu-id="0da5b-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak Renge Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="0da5b-102">How to: Animate Color by Using Key Frames</span></span>
<span data-ttu-id="0da5b-103">Bu örnek, anahtar kareler <xref:System.Windows.Media.SolidColorBrush.Color%2A> kullanarak <xref:System.Windows.Media.SolidColorBrush> bir animasyon nasıl gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0da5b-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> of a <xref:System.Windows.Media.SolidColorBrush> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0da5b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0da5b-104">Example</span></span>  
 <span data-ttu-id="0da5b-105">Aşağıdaki örnek, <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> bir <xref:System.Windows.Media.SolidColorBrush>. özelliğini <xref:System.Windows.Media.SolidColorBrush.Color%2A> canlandırmak için sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="0da5b-105">The following example uses the <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> property of a <xref:System.Windows.Media.SolidColorBrush>.</span></span> <span data-ttu-id="0da5b-106">Bu animasyon aşağıdaki şekilde üç anahtar kare kullanır:</span><span class="sxs-lookup"><span data-stu-id="0da5b-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="0da5b-107">İlk iki saniye boyunca, rengi <xref:System.Windows.Media.Animation.LinearColorKeyFrame> yavaş yavaş yeşilden kırmızıya değiştirmek için sınıfın bir örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0da5b-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearColorKeyFrame> class to gradually change the color from green to red.</span></span> <span data-ttu-id="0da5b-108">Değerler arasında düzgün <xref:System.Windows.Media.Animation.LinearColorKeyFrame> doğrusal geçiş oluşturma gibi doğrusal anahtar çerçeveler.</span><span class="sxs-lookup"><span data-stu-id="0da5b-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearColorKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="0da5b-109">Sonraki yarım saniyenin sonunda, rengi hızla <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> kırmızıdan sarıya değiştirmek için sınıfın bir örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0da5b-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> class to quickly change the color from red to yellow.</span></span> <span data-ttu-id="0da5b-110">Değerler arasında ani <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> değişiklikler oluşturmak gibi ayrık anahtar çerçeveleri, yani animasyonun bu bölümündeki renk değişikliği hızlı bir şekilde gerçekleşir ve ince değildir.</span><span class="sxs-lookup"><span data-stu-id="0da5b-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> create sudden changes between values, that is, the color change in this part of the animation occurs quickly and is not subtle.</span></span>  
  
3. <span data-ttu-id="0da5b-111">Son iki saniye boyunca, rengi <xref:System.Windows.Media.Animation.SplineColorKeyFrame> yeniden değiştirmek için sınıfın bir örneğini kullanır—bu kez sarıdan yeşile geri.</span><span class="sxs-lookup"><span data-stu-id="0da5b-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame> class to change the color again—this time from yellow back to green.</span></span> <span data-ttu-id="0da5b-112">Özellik değerlerine <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> göre <xref:System.Windows.Media.Animation.SplineColorKeyFrame> değerler arasında değişken bir geçiş oluşturmak gibi spline anahtar çerçeveleri.</span><span class="sxs-lookup"><span data-stu-id="0da5b-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineColorKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="0da5b-113">Bu örnekte, renk değişimi yavaş yavaş başlar ve zaman diliminin sonuna doğru katlanarak hızlar.</span><span class="sxs-lookup"><span data-stu-id="0da5b-113">In this example, the change in color begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="0da5b-114">Tam örnek için [Anahtar Çerçeve Animasyon Örneği'ne](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)bakın.</span><span class="sxs-lookup"><span data-stu-id="0da5b-114">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0da5b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0da5b-115">See also</span></span>

- <xref:System.Windows.Media.SolidColorBrush.Color%2A>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>
- [<span data-ttu-id="0da5b-116">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0da5b-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="0da5b-117">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="0da5b-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
