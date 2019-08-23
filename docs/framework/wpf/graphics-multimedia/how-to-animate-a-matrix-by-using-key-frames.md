---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Matrise Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: 6aa3e27cdfda7597c9b6acbf2980a2774f2b667b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963032"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a><span data-ttu-id="0ce78-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Matrise Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="0ce78-102">How to: Animate a Matrix by Using Key Frames</span></span>
<span data-ttu-id="0ce78-103">Bu örnek, <xref:System.Windows.Media.MatrixTransform.Matrix%2A> anahtar çerçeveler kullanarak bir <xref:System.Windows.Media.MatrixTransform> öğesinin özelliğinin nasıl hareketlendirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ce78-103">This example shows how to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ce78-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ce78-104">Example</span></span>  
 <span data-ttu-id="0ce78-105">Aşağıdaki örnek, öğesinin <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> <xref:System.Windows.Media.MatrixTransform.Matrix%2A> özelliğine animasyon uygulamak için sınıfını kullanır. <xref:System.Windows.Media.MatrixTransform></span><span class="sxs-lookup"><span data-stu-id="0ce78-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="0ce78-106">Örnek, görünümünü ve <xref:System.Windows.Media.MatrixTransform> konumunu <xref:System.Windows.Controls.Button>dönüştürmek için nesnesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ce78-106">The example uses the <xref:System.Windows.Media.MatrixTransform> object to transform the appearance and position of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="0ce78-107">Bu animasyon iki anahtar <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> çerçeve oluşturmak için sınıfını kullanır ve aşağıdakiler ile birlikte şunları yapar:</span><span class="sxs-lookup"><span data-stu-id="0ce78-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> class to create two key frames and does the following with them:</span></span>  
  
1. <span data-ttu-id="0ce78-108">İlk 0,2 saniye <xref:System.Windows.Media.Matrix> boyunca ilk olarak hareketlenir.</span><span class="sxs-lookup"><span data-stu-id="0ce78-108">Animates the first <xref:System.Windows.Media.Matrix> during the first 0.2 seconds.</span></span> <span data-ttu-id="0ce78-109">Örnek, <xref:System.Windows.Media.Matrix.M11%2A> ve <xref:System.Windows.Media.Matrix.M12%2A> özelliklerini <xref:System.Windows.Media.Matrix>değiştirir.</span><span class="sxs-lookup"><span data-stu-id="0ce78-109">The example changes the <xref:System.Windows.Media.Matrix.M11%2A> and <xref:System.Windows.Media.Matrix.M12%2A> properties of the <xref:System.Windows.Media.Matrix>.</span></span> <span data-ttu-id="0ce78-110">Bu değişiklik, düğmenin genişlemesine ve çarpıtılmış olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="0ce78-110">This change causes the button to stretch and become skewed.</span></span> <span data-ttu-id="0ce78-111">Örnek ayrıca, <xref:System.Windows.Media.Matrix.OffsetX%2A> düğme konumu değişmek için ve <xref:System.Windows.Media.Matrix.OffsetY%2A> özelliklerini de değiştirir.</span><span class="sxs-lookup"><span data-stu-id="0ce78-111">The example also changes the <xref:System.Windows.Media.Matrix.OffsetX%2A> and <xref:System.Windows.Media.Matrix.OffsetY%2A> properties so that the button changes position.</span></span>  
  
2. <span data-ttu-id="0ce78-112">Saniyeyi <xref:System.Windows.Media.Matrix> 1,0 saniye içinde hareketlendirir.</span><span class="sxs-lookup"><span data-stu-id="0ce78-112">Animates the second <xref:System.Windows.Media.Matrix> at 1.0 seconds.</span></span> <span data-ttu-id="0ce78-113">Düğme artık Eğilemez veya uzatılmadıysa düğme başka bir konuma gider.</span><span class="sxs-lookup"><span data-stu-id="0ce78-113">The button moves to another position while the button is no longer skewed or stretched.</span></span>  
  
3. <span data-ttu-id="0ce78-114">Animasyonu süresiz olarak yineler.</span><span class="sxs-lookup"><span data-stu-id="0ce78-114">Repeats the animation indefinitely.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ce78-115"><xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> Nesneden türetilen anahtar çerçeveler değerler arasında ani zıplamalar oluştur, diğer bir deyişle, animasyonun hareketi düzensiz olur.</span><span class="sxs-lookup"><span data-stu-id="0ce78-115">Key frames that derive from the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> object create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="0ce78-116">Tüm örnek için bkz. [ana kare animasyon örneği](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="0ce78-116">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ce78-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ce78-117">See also</span></span>

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [<span data-ttu-id="0ce78-118">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0ce78-118">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="0ce78-119">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="0ce78-119">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
