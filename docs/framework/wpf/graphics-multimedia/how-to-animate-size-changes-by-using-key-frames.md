---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak Boyut Değişikliklerine Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 69845d1d75f81042bbeb20ee6b1015f5c2f53b81
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43479938"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a><span data-ttu-id="e6460-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak Boyut Değişikliklerine Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="e6460-102">How to: Animate Size Changes by Using Key Frames</span></span>
<span data-ttu-id="e6460-103">Bu örnekte anahtar çerçeveler kullanarak boyut değişikliklerine animasyon ekleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e6460-103">This example shows how to animate size changes by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6460-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6460-104">Example</span></span>  
 <span data-ttu-id="e6460-105">Aşağıdaki örnekte <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> animasyon uygulamak için sınıfı <xref:System.Windows.Media.ArcSegment.Size%2A> özelliği bir <xref:System.Windows.Media.ArcSegment>.</span><span class="sxs-lookup"><span data-stu-id="e6460-105">The following example uses the <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.ArcSegment.Size%2A> property of an <xref:System.Windows.Media.ArcSegment>.</span></span> <span data-ttu-id="e6460-106">Bu animasyonu üç anahtar çerçeveler şu şekilde kullanılır:</span><span class="sxs-lookup"><span data-stu-id="e6460-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="e6460-107">Animasyonun ilk yarım saniye boyunca bir örneği kullanan <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> kademeli olarak Yayı boyutunu artırmak için sınıf. Gibi anahtar doğrusal çerçeveler <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> değerler arasında sorunsuz bir doğrusal geçişi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e6460-107">During the first half second of the animation, uses an instance of the <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> class to gradually increase the size of the arc. Linear key frames like <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="e6460-108">Sonraki sonunda yarım saniye kullanan bir örneğini <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> aniden Yayı boyutunu artırmak için sınıf. Gibi ayrı anahtar çerçeveler <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> ani atlama, değerleri arasında oluşturur, boyut değişikliklerine aniden ortaya çıkar ve ince değildir.</span><span class="sxs-lookup"><span data-stu-id="e6460-108">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> class to suddenly increase the size of the arc. Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> create sudden jumps between values, that is, the size changes occur suddenly and are not subtle.</span></span>  
  
3.  <span data-ttu-id="e6460-109">Son iki saniye içinde bir örneği kullanan <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> yay boyutunu artırmak için sınıf. Eğri anahtar çercevesi ister <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> değerlerine göre değerleri arasında bir değişken geçiş oluşturmak <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e6460-109">Over the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> class to increase the size of the arc. Spline key frames like <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="e6460-110">Bu örnekte, yay boyutunu yavaş ilk başta artırır ve zaman diliminin sonuna doğru katlanarak artar.</span><span class="sxs-lookup"><span data-stu-id="e6460-110">In this example, the size of the arc increases slowly at first and then increases exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="e6460-111">Tam bir örnek için bkz. [ana kare animasyon örnek](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="e6460-111">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6460-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e6460-112">See Also</span></span>  
 <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.ArcSegment.Size%2A>  
 <xref:System.Windows.Media.ArcSegment>  
 <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>  
 [<span data-ttu-id="e6460-113">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e6460-113">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="e6460-114">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="e6460-114">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
