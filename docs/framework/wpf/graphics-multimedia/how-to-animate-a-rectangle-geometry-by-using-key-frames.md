---
title: "Nasıl yapılır: Anahtar Çerçeveler Kullanarak Dikdörtgen Geometriye Animasyon Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b6c23f894b6fa93a3889356416bd95f61fff8beb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a><span data-ttu-id="f617e-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak Dikdörtgen Geometriye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="f617e-102">How to: Animate a Rectangle Geometry by Using Key Frames</span></span>
<span data-ttu-id="f617e-103">Bu örnek animasyon gösterilmektedir <xref:System.Windows.Media.RectangleGeometry.Rect%2A> özelliği bir <xref:System.Windows.Media.RectangleGeometry> anahtar çerçeveler kullanarak.</span><span class="sxs-lookup"><span data-stu-id="f617e-103">This example shows how to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f617e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f617e-104">Example</span></span>  
 <span data-ttu-id="f617e-105">Aşağıdaki örnek kullanır <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> animasyon sınıfı <xref:System.Windows.Media.RectangleGeometry.Rect%2A> özelliği bir <xref:System.Windows.Media.RectangleGeometry>.</span><span class="sxs-lookup"><span data-stu-id="f617e-105">The following example uses the <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry>.</span></span> <span data-ttu-id="f617e-106">Bu animasyon üç ana kare aşağıdaki şekilde kullanır:</span><span class="sxs-lookup"><span data-stu-id="f617e-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="f617e-107">İlk iki saniye boyunca bir örneğini kullanan <xref:System.Windows.Media.Animation.LinearRectKeyFrame> konum, genişlik ve yükseklik dikdörtgenin dereceli değişim animasyon sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f617e-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearRectKeyFrame> class to animate a gradual change in the position, width, and height of a rectangle.</span></span> <span data-ttu-id="f617e-108">Gibi doğrusal anahtar çerçeveler <xref:System.Windows.Media.Animation.LinearRectKeyFrame> değerler arasında yumuşak bir doğrusal geçiş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f617e-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearRectKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="f617e-109">Sonraki son sırasında yarım ikinci bir örneğini kullanır <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> aniden dikdörtgenin yüksekliğini azaltmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="f617e-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> class to suddenly decrease the height of the rectangle.</span></span> <span data-ttu-id="f617e-110">Gibi ayrık anahtar çerçeveler <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> değerler arasında ani değişiklikler oluşturur, yükseklik düşüş hızla gerçekleşir ve zarif değil.</span><span class="sxs-lookup"><span data-stu-id="f617e-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> create sudden changes between values, that is, the decrease in height occurs quickly and is not subtle.</span></span>  
  
3.  <span data-ttu-id="f617e-111">Son iki saniye boyunca bir örneğini kullanan <xref:System.Windows.Media.Animation.SplineRectKeyFrame> özgün boyutunu ve konumunu geri dikdörtgeni değiştirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="f617e-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame> class to change the rectangle back to its original size and position.</span></span> <span data-ttu-id="f617e-112">Gibi Eğri anahtar çerçeveler <xref:System.Windows.Media.Animation.SplineRectKeyFrame> değerlerine göre değerler arasında değişken geçiş oluşturmak <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f617e-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineRectKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="f617e-113">Bu örnekte, değişiklik yavaş başlar ve zaman diliminin sonuna doğru katlanarak hızlanır.</span><span class="sxs-lookup"><span data-stu-id="f617e-113">In this example, the change begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="f617e-114">Tam bir örnek için bkz: [ana kare animasyon örneği](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="f617e-114">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f617e-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f617e-115">See Also</span></span>  
 <xref:System.Windows.Media.RectangleGeometry>  
 <xref:System.Windows.Media.RectangleGeometry.Rect%2A>  
 <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>  
 [<span data-ttu-id="f617e-116">Anahtar çerçeve animasyonları genel bakış</span><span class="sxs-lookup"><span data-stu-id="f617e-116">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="f617e-117">Anahtar çerçeve nasıl yapılır konuları</span><span class="sxs-lookup"><span data-stu-id="f617e-117">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
