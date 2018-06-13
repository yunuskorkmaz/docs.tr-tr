---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak Boyut Değişikliklerine Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 0c2828215527a285943a79920de51fa42fe7a8a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559898"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a><span data-ttu-id="e87fb-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak Boyut Değişikliklerine Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="e87fb-102">How to: Animate Size Changes by Using Key Frames</span></span>
<span data-ttu-id="e87fb-103">Bu örnekte, anahtar çerçeveler kullanarak boyutu değişiklikleri animasyon gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e87fb-103">This example shows how to animate size changes by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e87fb-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e87fb-104">Example</span></span>  
 <span data-ttu-id="e87fb-105">Aşağıdaki örnek kullanır <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> animasyon sınıfı <xref:System.Windows.Media.ArcSegment.Size%2A> özelliği bir <xref:System.Windows.Media.ArcSegment>.</span><span class="sxs-lookup"><span data-stu-id="e87fb-105">The following example uses the <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.ArcSegment.Size%2A> property of an <xref:System.Windows.Media.ArcSegment>.</span></span> <span data-ttu-id="e87fb-106">Bu animasyon üç ana kare aşağıdaki şekilde kullanır:</span><span class="sxs-lookup"><span data-stu-id="e87fb-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="e87fb-107">Animasyonun ilk yarım saniye boyunca bir örneğini kullanan <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> yavaş yavaş yay boyutunu artırmak için sınıf. Gibi doğrusal anahtar çerçeveler <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> değerler arasında yumuşak bir doğrusal geçiş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e87fb-107">During the first half second of the animation, uses an instance of the <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> class to gradually increase the size of the arc. Linear key frames like <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="e87fb-108">Sonraki sonunda yarım ikinci bir örneğini kullanır <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> aniden yay boyutunu artırmak için sınıf. Gibi ayrık anahtar çerçeveler <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> değerler arasında ani atlar oluşturur, bu boyut değişiklikleri aniden ortaya çıkar ve zarif değildir.</span><span class="sxs-lookup"><span data-stu-id="e87fb-108">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> class to suddenly increase the size of the arc. Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> create sudden jumps between values, that is, the size changes occur suddenly and are not subtle.</span></span>  
  
3.  <span data-ttu-id="e87fb-109">Son iki saniye içinde bir örneğini kullanan <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> yay boyutunu artırmak için sınıf. Gibi Eğri anahtar çerçeveler <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> değerlerine göre değerler arasında değişken geçiş oluşturmak <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e87fb-109">Over the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> class to increase the size of the arc. Spline key frames like <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="e87fb-110">Bu örnekte, yay boyutunu yavaş ilk başta artırır ve zaman diliminin sonuna doğru katlanarak artırır.</span><span class="sxs-lookup"><span data-stu-id="e87fb-110">In this example, the size of the arc increases slowly at first and then increases exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="e87fb-111">Tam bir örnek için bkz: [ana kare animasyon örneği](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="e87fb-111">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e87fb-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e87fb-112">See Also</span></span>  
 <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.ArcSegment.Size%2A>  
 <xref:System.Windows.Media.ArcSegment>  
 <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>  
 [<span data-ttu-id="e87fb-113">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e87fb-113">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="e87fb-114">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="e87fb-114">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
