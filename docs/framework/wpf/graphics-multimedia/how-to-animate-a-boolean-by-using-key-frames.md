---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Boole Değerine Animasyon Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Booleans [WPF], animating with key frames
- animation [WPF], Booleans with key frames
- key frames [WPF], animating Booleans with
ms.assetid: 4b0fac96-6231-4fcf-9775-4dd673ddc785
ms.openlocfilehash: 59a72916721cccbe66f704253f148828fa8cd418
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175038"
---
# <a name="how-to-animate-a-boolean-by-using-key-frames"></a><span data-ttu-id="0ef1b-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Boole Değerine Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="0ef1b-102">How to: Animate a Boolean by Using Key Frames</span></span>
<span data-ttu-id="0ef1b-103">Bu örnekte, Boolean özelliği değerini animasyon ekleme işlemi gösterilmektedir bir <xref:System.Windows.Controls.Button> anahtar çerçeveler kullanarak bir denetim.</span><span class="sxs-lookup"><span data-stu-id="0ef1b-103">This example shows how to animate the Boolean property value of a <xref:System.Windows.Controls.Button> control by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ef1b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ef1b-104">Example</span></span>  
 <span data-ttu-id="0ef1b-105">Aşağıdaki örnekte <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> animasyon uygulamak için sınıfı <xref:System.Windows.UIElement.IsEnabled%2A> özelliği bir <xref:System.Windows.Controls.Button> denetimi.</span><span class="sxs-lookup"><span data-stu-id="0ef1b-105">The following example uses the <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> class to animate the <xref:System.Windows.UIElement.IsEnabled%2A> property of a <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="0ef1b-106">Anahtar çerçeveler Bu örnekte bir örneğini kullanması <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0ef1b-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> class.</span></span> <span data-ttu-id="0ef1b-107">Gibi ayrı anahtar çerçeveler <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> ani atlama, değerleri arasında oluşturur, bu animasyonu hareketini düzensiz olur.</span><span class="sxs-lookup"><span data-stu-id="0ef1b-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-csharp[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/BooleanAnimationUsingKeyFramesExample.cs#booleananimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/booleananimationusingkeyframesexample.vb#booleananimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/BooleanAnimationUsingKeyFramesExample.xaml#booleananimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="0ef1b-108">Tam bir örnek için bkz. [ana kare animasyon örnek](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="0ef1b-108">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ef1b-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ef1b-109">See also</span></span>

- <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>
- <xref:System.Windows.UIElement.IsEnabled%2A>
- <xref:System.Windows.Controls.Button>
- [<span data-ttu-id="0ef1b-110">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0ef1b-110">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="0ef1b-111">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="0ef1b-111">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
