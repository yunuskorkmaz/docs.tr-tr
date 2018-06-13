---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Matrise Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: edb7074dffab23810872f4347f5339270af86bd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557023"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a><span data-ttu-id="808bb-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Matrise Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="808bb-102">How to: Animate a Matrix by Using Key Frames</span></span>
<span data-ttu-id="808bb-103">Bu örnek animasyon gösterilmektedir <xref:System.Windows.Media.MatrixTransform.Matrix%2A> özelliği bir <xref:System.Windows.Media.MatrixTransform> anahtar çerçeveler kullanarak.</span><span class="sxs-lookup"><span data-stu-id="808bb-103">This example shows how to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="808bb-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="808bb-104">Example</span></span>  
 <span data-ttu-id="808bb-105">Aşağıdaki örnek kullanır <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> animasyon sınıfı <xref:System.Windows.Media.MatrixTransform.Matrix%2A> özelliği bir <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="808bb-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="808bb-106">Örnek kullanır <xref:System.Windows.Media.MatrixTransform> görünümünü ve konumunu dönüştürmek için nesne bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="808bb-106">The example uses the <xref:System.Windows.Media.MatrixTransform> object to transform the appearance and position of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="808bb-107">Bu animasyon kullanır <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> iki anahtar çerçeve oluşturmak için sınıf ve bunlar ile aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="808bb-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> class to create two key frames and does the following with them:</span></span>  
  
1.  <span data-ttu-id="808bb-108">İlk canlandırır <xref:System.Windows.Media.Matrix> ilk 0.2 saniye sırasında.</span><span class="sxs-lookup"><span data-stu-id="808bb-108">Animates the first <xref:System.Windows.Media.Matrix> during the first 0.2 seconds.</span></span> <span data-ttu-id="808bb-109">Örnek değişiklikleri <xref:System.Windows.Media.Matrix.M11%2A> ve <xref:System.Windows.Media.Matrix.M12%2A> özelliklerini <xref:System.Windows.Media.Matrix>.</span><span class="sxs-lookup"><span data-stu-id="808bb-109">The example changes the <xref:System.Windows.Media.Matrix.M11%2A> and <xref:System.Windows.Media.Matrix.M12%2A> properties of the <xref:System.Windows.Media.Matrix>.</span></span> <span data-ttu-id="808bb-110">Bu değişiklik düğmesine uzatma ve eğri duruma neden olur.</span><span class="sxs-lookup"><span data-stu-id="808bb-110">This change causes the button to stretch and become skewed.</span></span> <span data-ttu-id="808bb-111">Bu örnek ayrıca değiştirir <xref:System.Windows.Media.Matrix.OffsetX%2A> ve <xref:System.Windows.Media.Matrix.OffsetY%2A> özellikleri böylece düğme konumunu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="808bb-111">The example also changes the <xref:System.Windows.Media.Matrix.OffsetX%2A> and <xref:System.Windows.Media.Matrix.OffsetY%2A> properties so that the button changes position.</span></span>  
  
2.  <span data-ttu-id="808bb-112">İkinci canlandırır <xref:System.Windows.Media.Matrix> 1.0 saniye adresindeki.</span><span class="sxs-lookup"><span data-stu-id="808bb-112">Animates the second <xref:System.Windows.Media.Matrix> at 1.0 seconds.</span></span> <span data-ttu-id="808bb-113">Düğme artık eğri veya uzatılmış düğme başka bir konuma taşır.</span><span class="sxs-lookup"><span data-stu-id="808bb-113">The button moves to another position while the button is no longer skewed or stretched.</span></span>  
  
3.  <span data-ttu-id="808bb-114">Animasyonun süresiz olarak tekrarlar.</span><span class="sxs-lookup"><span data-stu-id="808bb-114">Repeats the animation indefinitely.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="808bb-115">Anahtarı türetin çerçeveler <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> nesnesi oluşturma değerler arasında ani atlar, diğer bir deyişle, animasyonun hareketi düzensiz olur.</span><span class="sxs-lookup"><span data-stu-id="808bb-115">Key frames that derive from the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> object create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="808bb-116">Tam bir örnek için bkz: [ana kare animasyon örneği](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="808bb-116">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="808bb-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="808bb-117">See Also</span></span>  
 <xref:System.Windows.Media.MatrixTransform.Matrix%2A>  
 <xref:System.Windows.Media.MatrixTransform>  
 [<span data-ttu-id="808bb-118">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="808bb-118">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="808bb-119">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="808bb-119">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
