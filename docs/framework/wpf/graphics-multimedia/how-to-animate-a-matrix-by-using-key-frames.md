---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Matrise Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: fff550a5a3a85575fe86c5290aa604ab00f1437f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518520"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a><span data-ttu-id="3fb5a-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Matrise Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="3fb5a-102">How to: Animate a Matrix by Using Key Frames</span></span>
<span data-ttu-id="3fb5a-103">Bu örnek, animasyon ekleme işlemi gösterilmektedir <xref:System.Windows.Media.MatrixTransform.Matrix%2A> özelliği bir <xref:System.Windows.Media.MatrixTransform> anahtar çerçeveler kullanarak.</span><span class="sxs-lookup"><span data-stu-id="3fb5a-103">This example shows how to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fb5a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="3fb5a-104">Example</span></span>  
 <span data-ttu-id="3fb5a-105">Aşağıdaki örnekte <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> animasyon uygulamak için sınıfı <xref:System.Windows.Media.MatrixTransform.Matrix%2A> özelliği bir <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="3fb5a-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="3fb5a-106">Örnekte <xref:System.Windows.Media.MatrixTransform> konumunu ve görünümünü dönüştürmesini nesne bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="3fb5a-106">The example uses the <xref:System.Windows.Media.MatrixTransform> object to transform the appearance and position of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="3fb5a-107">Bu animasyon kullanır <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> iki anahtar kare oluşturmak için sınıf ve bunları ile aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="3fb5a-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> class to create two key frames and does the following with them:</span></span>  
  
1.  <span data-ttu-id="3fb5a-108">İlk canlandırır <xref:System.Windows.Media.Matrix> ilk 0.2 saniye boyunca.</span><span class="sxs-lookup"><span data-stu-id="3fb5a-108">Animates the first <xref:System.Windows.Media.Matrix> during the first 0.2 seconds.</span></span> <span data-ttu-id="3fb5a-109">Örnek değişiklikleri <xref:System.Windows.Media.Matrix.M11%2A> ve <xref:System.Windows.Media.Matrix.M12%2A> özelliklerini <xref:System.Windows.Media.Matrix>.</span><span class="sxs-lookup"><span data-stu-id="3fb5a-109">The example changes the <xref:System.Windows.Media.Matrix.M11%2A> and <xref:System.Windows.Media.Matrix.M12%2A> properties of the <xref:System.Windows.Media.Matrix>.</span></span> <span data-ttu-id="3fb5a-110">Bu değişiklik, esnetme için dengesiz hale düğmesini neden olur.</span><span class="sxs-lookup"><span data-stu-id="3fb5a-110">This change causes the button to stretch and become skewed.</span></span> <span data-ttu-id="3fb5a-111">Örnek ayrıca değiştirir <xref:System.Windows.Media.Matrix.OffsetX%2A> ve <xref:System.Windows.Media.Matrix.OffsetY%2A> özellikleri böylece düğmeyi konumunu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="3fb5a-111">The example also changes the <xref:System.Windows.Media.Matrix.OffsetX%2A> and <xref:System.Windows.Media.Matrix.OffsetY%2A> properties so that the button changes position.</span></span>  
  
2.  <span data-ttu-id="3fb5a-112">İkinci canlandırır <xref:System.Windows.Media.Matrix> 1.0 saniye.</span><span class="sxs-lookup"><span data-stu-id="3fb5a-112">Animates the second <xref:System.Windows.Media.Matrix> at 1.0 seconds.</span></span> <span data-ttu-id="3fb5a-113">Düğme artık dengesiz esnetildiğini veya sırasında düğmeyi başka bir konuma taşır.</span><span class="sxs-lookup"><span data-stu-id="3fb5a-113">The button moves to another position while the button is no longer skewed or stretched.</span></span>  
  
3.  <span data-ttu-id="3fb5a-114">Animasyon süresiz olarak tekrarlar.</span><span class="sxs-lookup"><span data-stu-id="3fb5a-114">Repeats the animation indefinitely.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3fb5a-115">Anahtarı türetin çerçeveler <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> nesnesi değerleri arasında ani atlamalar oluşturur, diğer bir deyişle, animasyon hareketini düzensiz olur.</span><span class="sxs-lookup"><span data-stu-id="3fb5a-115">Key frames that derive from the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> object create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="3fb5a-116">Tam bir örnek için bkz. [ana kare animasyon örnek](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="3fb5a-116">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fb5a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fb5a-117">See also</span></span>
- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [<span data-ttu-id="3fb5a-118">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3fb5a-118">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [<span data-ttu-id="3fb5a-119">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="3fb5a-119">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
