---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Nesneye Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: ffbe1845b634c8f94eb6a10dfa44fcf9903e0cd5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933903"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a><span data-ttu-id="86f89-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Nesneye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="86f89-102">How to: Animate an Object by Using Key Frames</span></span>
<span data-ttu-id="86f89-103">Bu örnek, anahtar çerçeveler kullanarak bu örnekteki <xref:System.Windows.Controls.Page.Background%2A> bir <xref:System.Windows.Controls.Page> denetimin özelliği olan bir nesnenin nasıl hareketlendirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="86f89-103">This example shows how to animate an object, which in this example is the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86f89-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="86f89-104">Example</span></span>  
 <span data-ttu-id="86f89-105">Aşağıdaki örnek, bir <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> <xref:System.Windows.Controls.Page.Background%2A> <xref:System.Windows.Controls.Page> denetimin özelliği için renk değişikliklerine animasyon uygulamak için sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="86f89-105">The following example uses the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class to animate color changes for the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control.</span></span> <span data-ttu-id="86f89-106">Örnek animasyon, düzenli aralıklarla farklı bir arka plan fırçasına değişir.</span><span class="sxs-lookup"><span data-stu-id="86f89-106">The example animation changes to a different background brush at regular intervals.</span></span> <span data-ttu-id="86f89-107">Bu animasyon üç farklı <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> anahtar çerçeve oluşturmak için sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="86f89-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> class to create three different key frames.</span></span> <span data-ttu-id="86f89-108">Animasyon aşağıdaki şekilde anahtar çerçeveler kullanır:</span><span class="sxs-lookup"><span data-stu-id="86f89-108">The animation uses key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="86f89-109">İlk saniyenin sonunda, <xref:System.Windows.Media.LinearGradientBrush> sınıfının bir örneğini hareketlendirir.</span><span class="sxs-lookup"><span data-stu-id="86f89-109">At the end of the first second, animates an instance of the <xref:System.Windows.Media.LinearGradientBrush> class.</span></span> <span data-ttu-id="86f89-110">Örneğin bu bölümü, arka plan rengine doğrusal bir gradyan uygular ve bu sayede renk geçişleri sarıdan turuncu ' a kadar kırmızıya olur.</span><span class="sxs-lookup"><span data-stu-id="86f89-110">This section of the example applies a linear gradient to the background color so that the color transitions from yellow to orange to red.</span></span>  
  
2. <span data-ttu-id="86f89-111">Sonraki saniyenin sonunda, <xref:System.Windows.Media.RadialGradientBrush> sınıfının bir örneğini hareketlendirir.</span><span class="sxs-lookup"><span data-stu-id="86f89-111">At the end of the next second, animates an instance of the <xref:System.Windows.Media.RadialGradientBrush> class.</span></span> <span data-ttu-id="86f89-112">Örneğin bu bölümü, arka plan rengine bir radyal gradyan uygular, böylece renk geçişi beyaz, mavi ile siyah arasında olur.</span><span class="sxs-lookup"><span data-stu-id="86f89-112">This section of the example applies a radial gradient to the background color so that the color transitions from white to blue to black.</span></span>  
  
3. <span data-ttu-id="86f89-113">Üçüncü saniyenin sonunda, <xref:System.Windows.Media.DrawingBrush> sınıfının bir örneğini hareketlendirir.</span><span class="sxs-lookup"><span data-stu-id="86f89-113">At the end of the third second, animates an instance of the <xref:System.Windows.Media.DrawingBrush> class.</span></span> <span data-ttu-id="86f89-114">Örneğin bu bölümü arka plana dama tahtası için bir model uygular.</span><span class="sxs-lookup"><span data-stu-id="86f89-114">This section of the example applies a checkerboard pattern to the background.</span></span>  
  
4. <span data-ttu-id="86f89-115">Animasyon yeniden başlar ve süresiz olarak yinelenir.</span><span class="sxs-lookup"><span data-stu-id="86f89-115">The animation begins again and repeats indefinitely.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86f89-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>, <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> sınıfıyla kullanabileceğiniz tek anahtar çerçevesi türüdür.</span><span class="sxs-lookup"><span data-stu-id="86f89-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> is the only type of key frame that you can use with the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class.</span></span> <span data-ttu-id="86f89-117">Değerlerde ani değişiklikler <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> oluşturma gibi önemli çerçeveler, diğer bir deyişle, bu örnekteki renk değişiklikleri aniden meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="86f89-117">Key frames like <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> create sudden changes in values, that is, the color changes in this example occur suddenly.</span></span>  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="86f89-118">Tüm örnek için bkz. [ana kare animasyon örneği](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="86f89-118">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86f89-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86f89-119">See also</span></span>

- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [<span data-ttu-id="86f89-120">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="86f89-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="86f89-121">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="86f89-121">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
