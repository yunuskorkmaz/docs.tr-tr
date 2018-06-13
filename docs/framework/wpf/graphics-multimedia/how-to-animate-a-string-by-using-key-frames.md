---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Dizeye Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: 5219ce11667c84d3ceca380d5a4ddd52695736b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561065"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a><span data-ttu-id="9b3be-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Dizeye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="9b3be-102">How to: Animate a String by Using Key Frames</span></span>
<span data-ttu-id="9b3be-103">Bu örnek olan bir dize animasyon gösterilmektedir <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği bir <xref:System.Windows.Controls.Button> anahtar çerçeveler kullanarak denetim.</span><span class="sxs-lookup"><span data-stu-id="9b3be-103">This example shows how to animate a string, which in this example is the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b3be-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9b3be-104">Example</span></span>  
 <span data-ttu-id="9b3be-105">Aşağıdaki örnek kullanır <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> animasyon sınıfı <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="9b3be-105">The following example uses the <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="9b3be-106">Bu örnekteki tüm anahtar çerçeveleri bir örneğini kullanması <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> anahtar çerçeveler ile oluşturulan bir dize animasyonu yalnızca ayrı anahtar çerçeveler kullanabileceğinizden sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9b3be-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> class because a string animation that is created with key frames can only use discrete key frames.</span></span> <span data-ttu-id="9b3be-107">Gibi ayrık anahtar çerçeveler <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> değerler arasında ani atlar oluşturur, animasyonun değişiklikleri hızlı bir şekilde oluşur ve zarif değildir.</span><span class="sxs-lookup"><span data-stu-id="9b3be-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> create sudden jumps between values, that is, changes to the animation occur quickly and are not subtle.</span></span>  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="9b3be-108">Tam bir örnek için bkz: [ana kare animasyon örneği](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="9b3be-108">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b3be-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b3be-109">See Also</span></span>  
 <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.ContentControl.Content%2A>  
 <xref:System.Windows.Controls.Button>  
 <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>  
 [<span data-ttu-id="9b3be-110">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9b3be-110">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="9b3be-111">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="9b3be-111">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
