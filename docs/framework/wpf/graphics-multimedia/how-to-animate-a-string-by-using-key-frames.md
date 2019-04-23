---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Dizeye Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: 4a37408ad90fda12a95e66c1b44018967b376837
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204178"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a><span data-ttu-id="b0c9e-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Dizeye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="b0c9e-102">How to: Animate a String by Using Key Frames</span></span>
<span data-ttu-id="b0c9e-103">Bu örnekte, bu örnekte, bir dizeye animasyon ekleme işlemi gösterilmektedir <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği bir <xref:System.Windows.Controls.Button> anahtar çerçeveler kullanarak denetimi.</span><span class="sxs-lookup"><span data-stu-id="b0c9e-103">This example shows how to animate a string, which in this example is the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0c9e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0c9e-104">Example</span></span>  
 <span data-ttu-id="b0c9e-105">Aşağıdaki örnekte <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> animasyon uygulamak için sınıfı <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="b0c9e-105">The following example uses the <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="b0c9e-106">Anahtar çerçeveler Bu örnekte bir örneğini kullanması <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> anahtar çerçeveler ile oluşturulan bir dize animasyon yalnızca ayrık anahtar çerçeveler kullanabileceğinizden sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b0c9e-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> class because a string animation that is created with key frames can only use discrete key frames.</span></span> <span data-ttu-id="b0c9e-107">Gibi ayrı anahtar çerçeveler <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> ani atlama, değerleri arasında oluşturur, animasyon değişiklikleri hızlı ve hafif değildir.</span><span class="sxs-lookup"><span data-stu-id="b0c9e-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> create sudden jumps between values, that is, changes to the animation occur quickly and are not subtle.</span></span>  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="b0c9e-108">Tam bir örnek için bkz. [ana kare animasyon örnek](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="b0c9e-108">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0c9e-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0c9e-109">See also</span></span>

- <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.ContentControl.Content%2A>
- <xref:System.Windows.Controls.Button>
- <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>
- [<span data-ttu-id="b0c9e-110">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b0c9e-110">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="b0c9e-111">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="b0c9e-111">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
