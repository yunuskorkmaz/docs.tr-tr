---
title: 'Nasıl yapılır: Yineleme Döngüsü Sırasında Animasyon Değerlerini Biriktirme'
ms.date: 03/30/2017
helpviewer_keywords:
- accumulating animation values across repeating cycles [WPF]
- animation [WPF], accumulating values across repeating cycles
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
ms.openlocfilehash: 4b739883322751e2df86e13bfd07249abdb10a08
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762182"
---
# <a name="how-to-accumulate-animation-values-during-repeat-cycles"></a><span data-ttu-id="64b3b-102">Nasıl yapılır: Yineleme Döngüsü Sırasında Animasyon Değerlerini Biriktirme</span><span class="sxs-lookup"><span data-stu-id="64b3b-102">How to: Accumulate Animation Values During Repeat Cycles</span></span>
<span data-ttu-id="64b3b-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> yineleme döngüleri arasında animasyon değerlerini biriktirme özelliği.</span><span class="sxs-lookup"><span data-stu-id="64b3b-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate animation values across repeating cycles.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64b3b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="64b3b-104">Example</span></span>  
 <span data-ttu-id="64b3b-105">Kullanım <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> yineleme döngüleri arasında animasyon değerlerini temel ulaşıncaya kadar özelliği.</span><span class="sxs-lookup"><span data-stu-id="64b3b-105">Use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate base values of an animation across repeating cycles.</span></span> <span data-ttu-id="64b3b-106">Animasyon 9 kez yineler ayarlarsanız, örneğin, (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9 x") ve 10-15 arasında animasyon uygulamak için özelliğini ayarlayın (= 10 = 15), 15-20 ikinci döngüsü sırasında ilk döngü sırasında özelliği 10-15'e canlandırır , 25 üçüncü döngü vb. sırasında 20.</span><span class="sxs-lookup"><span data-stu-id="64b3b-106">For example, if you set an animation to repeat 9 times (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9x") and you set the property to animate between 10 and 15 (From = 10 To = 15), the property animates from 10 to 15 during the first cycle, from 15 to 20 during the second cycle, from 20 to 25 during the third cycle, and so on.</span></span> <span data-ttu-id="64b3b-107">Bu nedenle, her bir animasyon döngüsünün önceki animasyon döngüsünün bitiş animasyon değerini temel değer olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="64b3b-107">Hence, each animation cycle uses the ending animation value from the previous animation cycle as its base value.</span></span>  
  
 <span data-ttu-id="64b3b-108">Kullanabileceğiniz `IsCumulative` en temel animasyon ve çoğu anahtar çerçeve animasyon özelliği.</span><span class="sxs-lookup"><span data-stu-id="64b3b-108">You can use the `IsCumulative` property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="64b3b-109">Daha fazla bilgi için [animasyona genel bakış](animation-overview.md) ve [anahtar-çerçeve animasyonlara genel bakış](key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="64b3b-109">For more information, see [Animation Overview](animation-overview.md) and [Key-Frame Animations Overview](key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="64b3b-110">Aşağıdaki örnekte, dört dikdörtgenin genişliğini animasyon tarafından bu davranış gösterir.</span><span class="sxs-lookup"><span data-stu-id="64b3b-110">The following example shows this behavior by animating the width of four rectangles.</span></span> <span data-ttu-id="64b3b-111">Örnek:</span><span class="sxs-lookup"><span data-stu-id="64b3b-111">The example:</span></span>  
  
- <span data-ttu-id="64b3b-112">İlk dikdörtgen canlandırır <xref:System.Windows.Media.Animation.DoubleAnimation> ve ayarlar <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="64b3b-112">Animates the first rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to `true`.</span></span>  
  
- <span data-ttu-id="64b3b-113">İkinci dikdörtgen canlandırır <xref:System.Windows.Media.Animation.DoubleAnimation> ve ayarlar <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> özelliği varsayılan değerine `false`.</span><span class="sxs-lookup"><span data-stu-id="64b3b-113">Animates the second rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to the default value of `false`.</span></span>  
  
- <span data-ttu-id="64b3b-114">Üçüncü dikdörtgen canlandırır <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> ve ayarlar <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="64b3b-114">Animates the third rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `true`.</span></span>  
  
- <span data-ttu-id="64b3b-115">Son dikdörtgen canlandırır <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> ve ayarlar <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="64b3b-115">Animates the last rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `false`.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="64b3b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64b3b-116">See also</span></span>

- [<span data-ttu-id="64b3b-117">Animasyon Başlangıç Değerine Animasyon Çıkış Değeri Ekleme</span><span class="sxs-lookup"><span data-stu-id="64b3b-117">Add an Animation Output Value to an Animation Starting Value</span></span>](how-to-add-an-animation-output-value-to-an-animation-starting-value.md)
- [<span data-ttu-id="64b3b-118">Animasyonu Yineleme</span><span class="sxs-lookup"><span data-stu-id="64b3b-118">Repeat an Animation</span></span>](how-to-repeat-an-animation.md)
- [<span data-ttu-id="64b3b-119">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="64b3b-119">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="64b3b-120">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="64b3b-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="64b3b-121">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="64b3b-121">How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
