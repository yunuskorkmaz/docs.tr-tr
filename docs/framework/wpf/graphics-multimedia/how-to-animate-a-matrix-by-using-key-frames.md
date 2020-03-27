---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Matrise Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: eb596cf728f8a7cc1964963b8509f42bdd7a392a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344913"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a><span data-ttu-id="bd696-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Matrise Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="bd696-102">How to: Animate a Matrix by Using Key Frames</span></span>
<span data-ttu-id="bd696-103">Bu örnek, anahtar çerçeveleri <xref:System.Windows.Media.MatrixTransform.Matrix%2A> kullanarak <xref:System.Windows.Media.MatrixTransform> bir özelliği animasyon nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="bd696-103">This example shows how to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd696-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd696-104">Example</span></span>  
 <span data-ttu-id="bd696-105">Aşağıdaki örnek, <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> bir <xref:System.Windows.Media.MatrixTransform>. özelliğini <xref:System.Windows.Media.MatrixTransform.Matrix%2A> canlandırmak için sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="bd696-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="bd696-106">Örnek, <xref:System.Windows.Media.MatrixTransform> bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="bd696-106">The example uses the <xref:System.Windows.Media.MatrixTransform> object to transform the appearance and position of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="bd696-107">Bu animasyon, <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> iki anahtar kare oluşturmak için sınıfı kullanır ve onlarla aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="bd696-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> class to create two key frames and does the following with them:</span></span>  
  
1. <span data-ttu-id="bd696-108">İlk 0.2 <xref:System.Windows.Media.Matrix> saniye boyunca ilk animasyon.</span><span class="sxs-lookup"><span data-stu-id="bd696-108">Animates the first <xref:System.Windows.Media.Matrix> during the first 0.2 seconds.</span></span> <span data-ttu-id="bd696-109">Örnek, .'ın <xref:System.Windows.Media.Matrix.M11%2A> <xref:System.Windows.Media.Matrix.M12%2A> <xref:System.Windows.Media.Matrix>özelliklerini ve özelliklerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bd696-109">The example changes the <xref:System.Windows.Media.Matrix.M11%2A> and <xref:System.Windows.Media.Matrix.M12%2A> properties of the <xref:System.Windows.Media.Matrix>.</span></span> <span data-ttu-id="bd696-110">Bu değişiklik düğmenin esnemesine ve eğrilmeye neden olur.</span><span class="sxs-lookup"><span data-stu-id="bd696-110">This change causes the button to stretch and become skewed.</span></span> <span data-ttu-id="bd696-111">Örnek, düğmenin <xref:System.Windows.Media.Matrix.OffsetX%2A> <xref:System.Windows.Media.Matrix.OffsetY%2A> konumunu değiştirmesi için de ve özelliklerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bd696-111">The example also changes the <xref:System.Windows.Media.Matrix.OffsetX%2A> and <xref:System.Windows.Media.Matrix.OffsetY%2A> properties so that the button changes position.</span></span>  
  
2. <span data-ttu-id="bd696-112">Saniyeyi <xref:System.Windows.Media.Matrix> 1.0 saniyede canlandırın.</span><span class="sxs-lookup"><span data-stu-id="bd696-112">Animates the second <xref:System.Windows.Media.Matrix> at 1.0 seconds.</span></span> <span data-ttu-id="bd696-113">Düğme artık eğriltilmiş veya uzatılmış değilken düğme başka bir konuma taşınır.</span><span class="sxs-lookup"><span data-stu-id="bd696-113">The button moves to another position while the button is no longer skewed or stretched.</span></span>  
  
3. <span data-ttu-id="bd696-114">Animasyonu süresiz olarak yineler.</span><span class="sxs-lookup"><span data-stu-id="bd696-114">Repeats the animation indefinitely.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd696-115"><xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> Nesneden türeyen anahtar kareler değerler arasında ani atlar oluşturur, yani animasyonun hareketi sarsıntılıdır.</span><span class="sxs-lookup"><span data-stu-id="bd696-115">Key frames that derive from the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> object create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="bd696-116">Tam örnek için [Anahtar Çerçeve Animasyon Örneği'ne](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)bakın.</span><span class="sxs-lookup"><span data-stu-id="bd696-116">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd696-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd696-117">See also</span></span>

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [<span data-ttu-id="bd696-118">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bd696-118">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="bd696-119">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="bd696-119">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
