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
ms.openlocfilehash: e579c4beb757ccf58eb1b9ca1f3852a5b96cac1a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326092"
---
# <a name="how-to-animate-color-by-using-key-frames"></a><span data-ttu-id="80469-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak Renge Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="80469-102">How to: Animate Color by Using Key Frames</span></span>
<span data-ttu-id="80469-103">Bu örnek, animasyon ekleme işlemi gösterilmektedir <xref:System.Windows.Media.SolidColorBrush.Color%2A> , bir <xref:System.Windows.Media.SolidColorBrush> anahtar çerçeveler kullanarak.</span><span class="sxs-lookup"><span data-stu-id="80469-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> of a <xref:System.Windows.Media.SolidColorBrush> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80469-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="80469-104">Example</span></span>  
 <span data-ttu-id="80469-105">Aşağıdaki örnekte <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> animasyon uygulamak için sınıfı <xref:System.Windows.Media.SolidColorBrush.Color%2A> özelliği bir <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="80469-105">The following example uses the <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> property of a <xref:System.Windows.Media.SolidColorBrush>.</span></span> <span data-ttu-id="80469-106">Bu animasyonu üç anahtar çerçeveler şu şekilde kullanılır:</span><span class="sxs-lookup"><span data-stu-id="80469-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="80469-107">İlk iki saniye boyunca bir örneği kullanan <xref:System.Windows.Media.Animation.LinearColorKeyFrame> rengi yeşilden kırmızıya kademeli olarak değiştirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="80469-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearColorKeyFrame> class to gradually change the color from green to red.</span></span> <span data-ttu-id="80469-108">Gibi anahtar doğrusal çerçeveler <xref:System.Windows.Media.Animation.LinearColorKeyFrame> değerler arasında sorunsuz bir doğrusal geçişi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="80469-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearColorKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="80469-109">Sonraki sonuna sırasında yarım saniye kullanan bir örneğini <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> sınıfı hızlı bir şekilde kırmızı rengi sarı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="80469-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> class to quickly change the color from red to yellow.</span></span> <span data-ttu-id="80469-110">Gibi ayrı anahtar çerçeveler <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> ani değişiklikleri değerler arasında oluşturur, bu bölümü animasyonun rengi değişiklik hızla gerçekleşir ve ince değil.</span><span class="sxs-lookup"><span data-stu-id="80469-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> create sudden changes between values, that is, the color change in this part of the animation occurs quickly and is not subtle.</span></span>  
  
3. <span data-ttu-id="80469-111">Son iki saniye boyunca bir örneği kullanan <xref:System.Windows.Media.Animation.SplineColorKeyFrame> yeniden rengini değiştirmek için sınıf — yeşil sarı arka bu süre.</span><span class="sxs-lookup"><span data-stu-id="80469-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame> class to change the color again—this time from yellow back to green.</span></span> <span data-ttu-id="80469-112">Eğri anahtar çercevesi ister <xref:System.Windows.Media.Animation.SplineColorKeyFrame> değerlerine göre değerleri arasında bir değişken geçiş oluşturmak <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="80469-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineColorKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="80469-113">Bu örnekte, renginde de değişiklik yavaş başlar ve zaman diliminin sonuna doğru katlanarak hızlandırır.</span><span class="sxs-lookup"><span data-stu-id="80469-113">In this example, the change in color begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="80469-114">Tam bir örnek için bkz. [ana kare animasyon örnek](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="80469-114">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80469-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80469-115">See also</span></span>

- <xref:System.Windows.Media.SolidColorBrush.Color%2A>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>
- [<span data-ttu-id="80469-116">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="80469-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="80469-117">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="80469-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
