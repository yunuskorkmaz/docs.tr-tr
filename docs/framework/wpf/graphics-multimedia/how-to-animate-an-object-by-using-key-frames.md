---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Nesneye Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 0bc33b189fd856dbe8106c1db35bc18e27ea131e
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344713"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a><span data-ttu-id="7f41d-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Nesneye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="7f41d-102">How to: Animate an Object by Using Key Frames</span></span>
<span data-ttu-id="7f41d-103">Bu örnekte, anahtar çerçeveleri kullanarak, bu örnekte <xref:System.Windows.Controls.Page.Background%2A> denetimin özelliği olan bir <xref:System.Windows.Controls.Page> nesnenin nasıl canlandırılanın gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7f41d-103">This example shows how to animate an object, which in this example is the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f41d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f41d-104">Example</span></span>  
 <span data-ttu-id="7f41d-105">Aşağıdaki örnek, <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> bir <xref:System.Windows.Controls.Page.Background%2A> <xref:System.Windows.Controls.Page> denetimin özelliği için renk değişikliklerini canlandırmak için sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="7f41d-105">The following example uses the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class to animate color changes for the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control.</span></span> <span data-ttu-id="7f41d-106">Örnek animasyon, düzenli aralıklarla farklı bir arka plan fırçasına dönüşür.</span><span class="sxs-lookup"><span data-stu-id="7f41d-106">The example animation changes to a different background brush at regular intervals.</span></span> <span data-ttu-id="7f41d-107">Bu animasyon, <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> üç farklı anahtar kare oluşturmak için sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="7f41d-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> class to create three different key frames.</span></span> <span data-ttu-id="7f41d-108">Animasyon aşağıdaki şekilde anahtar kareler kullanır:</span><span class="sxs-lookup"><span data-stu-id="7f41d-108">The animation uses key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="7f41d-109">İlk saniyenin sonunda, sınıfın bir örneğini <xref:System.Windows.Media.LinearGradientBrush> animasyona serer.</span><span class="sxs-lookup"><span data-stu-id="7f41d-109">At the end of the first second, animates an instance of the <xref:System.Windows.Media.LinearGradientBrush> class.</span></span> <span data-ttu-id="7f41d-110">Örneğin bu bölümü, rengin sarıdan turuncuya, kırmızıya geçmesi için arka plan rengine doğrusal bir degrade uygular.</span><span class="sxs-lookup"><span data-stu-id="7f41d-110">This section of the example applies a linear gradient to the background color so that the color transitions from yellow to orange to red.</span></span>  
  
2. <span data-ttu-id="7f41d-111">Sonraki saniyenin sonunda, sınıfın bir örneğini <xref:System.Windows.Media.RadialGradientBrush> animasyona serer.</span><span class="sxs-lookup"><span data-stu-id="7f41d-111">At the end of the next second, animates an instance of the <xref:System.Windows.Media.RadialGradientBrush> class.</span></span> <span data-ttu-id="7f41d-112">Örneğin bu bölümü, rengin beyazdan maviye, siyaha geçmesi için arka plan rengine radyal bir degrade uygular.</span><span class="sxs-lookup"><span data-stu-id="7f41d-112">This section of the example applies a radial gradient to the background color so that the color transitions from white to blue to black.</span></span>  
  
3. <span data-ttu-id="7f41d-113">Üçüncü saniyenin sonunda, sınıfın bir örneğini <xref:System.Windows.Media.DrawingBrush> animasyona serer.</span><span class="sxs-lookup"><span data-stu-id="7f41d-113">At the end of the third second, animates an instance of the <xref:System.Windows.Media.DrawingBrush> class.</span></span> <span data-ttu-id="7f41d-114">Örneğin bu bölümü arka plana bir dama tahtası deseni uygular.</span><span class="sxs-lookup"><span data-stu-id="7f41d-114">This section of the example applies a checkerboard pattern to the background.</span></span>  
  
4. <span data-ttu-id="7f41d-115">Animasyon yeniden başlar ve süresiz olarak yinelenir.</span><span class="sxs-lookup"><span data-stu-id="7f41d-115">The animation begins again and repeats indefinitely.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f41d-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame><xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> sınıfla birlikte kullanabileceğiniz tek anahtar kare türüdür.</span><span class="sxs-lookup"><span data-stu-id="7f41d-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> is the only type of key frame that you can use with the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class.</span></span> <span data-ttu-id="7f41d-117">Değerlerde ani değişiklikler oluşturmak gibi <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> anahtar çerçeveler, yani bu örnekteki renk değişiklikleri aniden oluşur.</span><span class="sxs-lookup"><span data-stu-id="7f41d-117">Key frames like <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> create sudden changes in values, that is, the color changes in this example occur suddenly.</span></span>  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="7f41d-118">Tam örnek için [Anahtar Çerçeve Animasyon Örneği'ne](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)bakın.</span><span class="sxs-lookup"><span data-stu-id="7f41d-118">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f41d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f41d-119">See also</span></span>

- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [<span data-ttu-id="7f41d-120">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7f41d-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="7f41d-121">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="7f41d-121">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
