---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Nesneye Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 7dc49bc6b3f9156507cb821bfc32b269365b206c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558546"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a><span data-ttu-id="64a2a-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Nesneye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="64a2a-102">How to: Animate an Object by Using Key Frames</span></span>
<span data-ttu-id="64a2a-103">Bu örnekte olduğu bir nesne animasyon gösterilmektedir <xref:System.Windows.Controls.Page.Background%2A> özelliği bir <xref:System.Windows.Controls.Page> anahtar çerçeveler kullanarak denetim.</span><span class="sxs-lookup"><span data-stu-id="64a2a-103">This example shows how to animate an object, which in this example is the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64a2a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="64a2a-104">Example</span></span>  
 <span data-ttu-id="64a2a-105">Aşağıdaki örnek kullanır <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> renk animasyon sınıfı değişiklikler için <xref:System.Windows.Controls.Page.Background%2A> özelliği bir <xref:System.Windows.Controls.Page> denetim.</span><span class="sxs-lookup"><span data-stu-id="64a2a-105">The following example uses the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class to animate color changes for the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control.</span></span> <span data-ttu-id="64a2a-106">Farklı bir arka plan Fırçası düzenli aralıklarla örnek animasyon geçer.</span><span class="sxs-lookup"><span data-stu-id="64a2a-106">The example animation changes to a different background brush at regular intervals.</span></span> <span data-ttu-id="64a2a-107">Bu animasyon kullanır <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> üç farklı anahtar çerçeve oluşturmak için sınıfı.</span><span class="sxs-lookup"><span data-stu-id="64a2a-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> class to create three different key frames.</span></span> <span data-ttu-id="64a2a-108">Animasyon ana kare aşağıdaki şekilde kullanır:</span><span class="sxs-lookup"><span data-stu-id="64a2a-108">The animation uses key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="64a2a-109">Örneği ilk saniye sonunda canlandırır <xref:System.Windows.Media.LinearGradientBrush> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="64a2a-109">At the end of the first second, animates an instance of the <xref:System.Windows.Media.LinearGradientBrush> class.</span></span> <span data-ttu-id="64a2a-110">Bu bölümde Örneğin, doğrusal gradyan arka plan rengi uygular rengi kırmızı turuncu sarı geçiş.</span><span class="sxs-lookup"><span data-stu-id="64a2a-110">This section of the example applies a linear gradient to the background color so that the color transitions from yellow to orange to red.</span></span>  
  
2.  <span data-ttu-id="64a2a-111">Sonraki saniye sonunda örneği canlandırır <xref:System.Windows.Media.RadialGradientBrush> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="64a2a-111">At the end of the next second, animates an instance of the <xref:System.Windows.Media.RadialGradientBrush> class.</span></span> <span data-ttu-id="64a2a-112">Bu bölümde Örneğin, Radyal gradyan arka plan rengi uygular rengi siyah mavi için Beyaz'den geçiş.</span><span class="sxs-lookup"><span data-stu-id="64a2a-112">This section of the example applies a radial gradient to the background color so that the color transitions from white to blue to black.</span></span>  
  
3.  <span data-ttu-id="64a2a-113">Üçüncü saniye sonunda örneği canlandırır <xref:System.Windows.Media.DrawingBrush> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="64a2a-113">At the end of the third second, animates an instance of the <xref:System.Windows.Media.DrawingBrush> class.</span></span> <span data-ttu-id="64a2a-114">Bu bölüm örneğin Damalı bir desen arka plana geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="64a2a-114">This section of the example applies a checkerboard pattern to the background.</span></span>  
  
4.  <span data-ttu-id="64a2a-115">Animasyon yeniden başlar ve sonsuza kadar yinelenir.</span><span class="sxs-lookup"><span data-stu-id="64a2a-115">The animation begins again and repeats indefinitely.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64a2a-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> ile birlikte kullanabileceğiniz anahtar çerçevesi yalnızca türü <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="64a2a-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> is the only type of key frame that you can use with the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class.</span></span> <span data-ttu-id="64a2a-117">Anahtar çerçeveleri gibi <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> ani değişiklikler değerleri, yani oluşturmak, bu örnekteki renk değişiklikleri aniden ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="64a2a-117">Key frames like <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> create sudden changes in values, that is, the color changes in this example occur suddenly.</span></span>  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="64a2a-118">Tam bir örnek için bkz: [ana kare animasyon örneği](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="64a2a-118">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64a2a-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="64a2a-119">See Also</span></span>  
 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.Page.Background%2A>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>  
 <xref:System.Windows.Media.LinearGradientBrush>  
 <xref:System.Windows.Media.RadialGradientBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 [<span data-ttu-id="64a2a-120">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="64a2a-120">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="64a2a-121">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="64a2a-121">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
