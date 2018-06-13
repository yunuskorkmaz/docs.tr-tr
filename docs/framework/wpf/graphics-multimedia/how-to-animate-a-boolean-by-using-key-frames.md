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
ms.openlocfilehash: d6273c08881e802595e831cafe120a5bec841c4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556932"
---
# <a name="how-to-animate-a-boolean-by-using-key-frames"></a><span data-ttu-id="01908-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Boole Değerine Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="01908-102">How to: Animate a Boolean by Using Key Frames</span></span>
<span data-ttu-id="01908-103">Bu örnek Boolean özellik değerinin animasyon gösterilmektedir bir <xref:System.Windows.Controls.Button> anahtar çerçeveler kullanarak denetim.</span><span class="sxs-lookup"><span data-stu-id="01908-103">This example shows how to animate the Boolean property value of a <xref:System.Windows.Controls.Button> control by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01908-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="01908-104">Example</span></span>  
 <span data-ttu-id="01908-105">Aşağıdaki örnek kullanır <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> animasyon sınıfı <xref:System.Windows.UIElement.IsEnabled%2A> özelliği bir <xref:System.Windows.Controls.Button> denetim.</span><span class="sxs-lookup"><span data-stu-id="01908-105">The following example uses the <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> class to animate the <xref:System.Windows.UIElement.IsEnabled%2A> property of a <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="01908-106">Bu örnekteki tüm anahtar çerçeveleri bir örneğini kullanması <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="01908-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> class.</span></span> <span data-ttu-id="01908-107">Gibi ayrık anahtar çerçeveler <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> değerler arasında ani atlar oluşturur, animasyonun hareketi düzensiz olur.</span><span class="sxs-lookup"><span data-stu-id="01908-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-csharp[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/BooleanAnimationUsingKeyFramesExample.cs#booleananimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/booleananimationusingkeyframesexample.vb#booleananimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/BooleanAnimationUsingKeyFramesExample.xaml#booleananimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="01908-108">Tam bir örnek için bkz: [ana kare animasyon örneği](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="01908-108">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01908-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="01908-109">See Also</span></span>  
 <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>  
 <xref:System.Windows.UIElement.IsEnabled%2A>  
 <xref:System.Windows.Controls.Button>  
 [<span data-ttu-id="01908-110">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="01908-110">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="01908-111">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="01908-111">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
