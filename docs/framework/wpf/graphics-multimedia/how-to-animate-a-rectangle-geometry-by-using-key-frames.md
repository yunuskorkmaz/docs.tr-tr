---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak Dikdörtgen Geometriye Animasyon Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
ms.openlocfilehash: bcc9e7f198b8a20ffe13daf6508fb8a735937652
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344686"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a><span data-ttu-id="9a404-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak Dikdörtgen Geometriye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="9a404-102">How to: Animate a Rectangle Geometry by Using Key Frames</span></span>
<span data-ttu-id="9a404-103">Bu örnek, anahtar çerçeveleri <xref:System.Windows.Media.RectangleGeometry.Rect%2A> kullanarak <xref:System.Windows.Media.RectangleGeometry> bir özelliği animasyon nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a404-103">This example shows how to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a404-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a404-104">Example</span></span>  
 <span data-ttu-id="9a404-105">Aşağıdaki örnek, <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> bir <xref:System.Windows.Media.RectangleGeometry>. özelliğini <xref:System.Windows.Media.RectangleGeometry.Rect%2A> canlandırmak için sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a404-105">The following example uses the <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry>.</span></span> <span data-ttu-id="9a404-106">Bu animasyon aşağıdaki şekilde üç anahtar kare kullanır:</span><span class="sxs-lookup"><span data-stu-id="9a404-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="9a404-107">İlk iki saniye boyunca, dikdörtgenin <xref:System.Windows.Media.Animation.LinearRectKeyFrame> konumu, genişliği ve yüksekliğinde kademeli bir değişikliği canlandırmak için sınıfın bir örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a404-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearRectKeyFrame> class to animate a gradual change in the position, width, and height of a rectangle.</span></span> <span data-ttu-id="9a404-108">Değerler arasında düzgün <xref:System.Windows.Media.Animation.LinearRectKeyFrame> doğrusal geçiş oluşturma gibi doğrusal anahtar çerçeveler.</span><span class="sxs-lookup"><span data-stu-id="9a404-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearRectKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="9a404-109">Sonraki yarım saniyenin sonunda, aniden dikdörtgenin <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> yüksekliğini azaltmak için sınıfın bir örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a404-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> class to suddenly decrease the height of the rectangle.</span></span> <span data-ttu-id="9a404-110">Değerler arasında ani <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> değişiklikler oluşturmak gibi ayrık anahtar çerçeveleri, yani yükseklik düşüşü hızlı bir şekilde oluşur ve ince değildir.</span><span class="sxs-lookup"><span data-stu-id="9a404-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> create sudden changes between values, that is, the decrease in height occurs quickly and is not subtle.</span></span>  
  
3. <span data-ttu-id="9a404-111">Son iki saniye boyunca, dikdörtgeni <xref:System.Windows.Media.Animation.SplineRectKeyFrame> orijinal boyutuna ve konumuna geri değiştirmek için sınıfın bir örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a404-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame> class to change the rectangle back to its original size and position.</span></span> <span data-ttu-id="9a404-112">Özellik değerlerine <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> göre <xref:System.Windows.Media.Animation.SplineRectKeyFrame> değerler arasında değişken bir geçiş oluşturmak gibi spline anahtar çerçeveleri.</span><span class="sxs-lookup"><span data-stu-id="9a404-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineRectKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="9a404-113">Bu örnekte, değişim yavaş yavaş başlar ve zaman diliminin sonuna doğru katlanarak hızlar.</span><span class="sxs-lookup"><span data-stu-id="9a404-113">In this example, the change begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="9a404-114">Tam örnek için [Anahtar Çerçeve Animasyon Örneği'ne](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)bakın.</span><span class="sxs-lookup"><span data-stu-id="9a404-114">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a404-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a404-115">See also</span></span>

- <xref:System.Windows.Media.RectangleGeometry>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>
- [<span data-ttu-id="9a404-116">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9a404-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="9a404-117">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="9a404-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
