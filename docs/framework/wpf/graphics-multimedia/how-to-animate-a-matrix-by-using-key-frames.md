---
title: "Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Matrise Animasyon Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8c67b5c8e179485083a40aa8a196fbee3e0fc24
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a><span data-ttu-id="2d117-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Matrise Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="2d117-102">How to: Animate a Matrix by Using Key Frames</span></span>
<span data-ttu-id="2d117-103">Bu örnek animasyon gösterilmektedir <xref:System.Windows.Media.MatrixTransform.Matrix%2A> özelliği bir <xref:System.Windows.Media.MatrixTransform> anahtar çerçeveler kullanarak.</span><span class="sxs-lookup"><span data-stu-id="2d117-103">This example shows how to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d117-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="2d117-104">Example</span></span>  
 <span data-ttu-id="2d117-105">Aşağıdaki örnek kullanır <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> animasyon sınıfı <xref:System.Windows.Media.MatrixTransform.Matrix%2A> özelliği bir <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="2d117-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="2d117-106">Örnek kullanır <xref:System.Windows.Media.MatrixTransform> görünümünü ve konumunu dönüştürmek için nesne bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="2d117-106">The example uses the <xref:System.Windows.Media.MatrixTransform> object to transform the appearance and position of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="2d117-107">Bu animasyon kullanır <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> iki anahtar çerçeve oluşturmak için sınıf ve bunlar ile aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="2d117-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> class to create two key frames and does the following with them:</span></span>  
  
1.  <span data-ttu-id="2d117-108">İlk canlandırır <xref:System.Windows.Media.Matrix> ilk 0.2 saniye sırasında.</span><span class="sxs-lookup"><span data-stu-id="2d117-108">Animates the first <xref:System.Windows.Media.Matrix> during the first 0.2 seconds.</span></span> <span data-ttu-id="2d117-109">Örnek değişiklikleri <xref:System.Windows.Media.Matrix.M11%2A> ve <xref:System.Windows.Media.Matrix.M12%2A> özelliklerini <xref:System.Windows.Media.Matrix>.</span><span class="sxs-lookup"><span data-stu-id="2d117-109">The example changes the <xref:System.Windows.Media.Matrix.M11%2A> and <xref:System.Windows.Media.Matrix.M12%2A> properties of the <xref:System.Windows.Media.Matrix>.</span></span> <span data-ttu-id="2d117-110">Bu değişiklik düğmesine uzatma ve eğri duruma neden olur.</span><span class="sxs-lookup"><span data-stu-id="2d117-110">This change causes the button to stretch and become skewed.</span></span> <span data-ttu-id="2d117-111">Bu örnek ayrıca değiştirir <xref:System.Windows.Media.Matrix.OffsetX%2A> ve <xref:System.Windows.Media.Matrix.OffsetY%2A> özellikleri böylece düğme konumunu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="2d117-111">The example also changes the <xref:System.Windows.Media.Matrix.OffsetX%2A> and <xref:System.Windows.Media.Matrix.OffsetY%2A> properties so that the button changes position.</span></span>  
  
2.  <span data-ttu-id="2d117-112">İkinci canlandırır <xref:System.Windows.Media.Matrix> 1.0 saniye adresindeki.</span><span class="sxs-lookup"><span data-stu-id="2d117-112">Animates the second <xref:System.Windows.Media.Matrix> at 1.0 seconds.</span></span> <span data-ttu-id="2d117-113">Düğme artık eğri veya uzatılmış düğme başka bir konuma taşır.</span><span class="sxs-lookup"><span data-stu-id="2d117-113">The button moves to another position while the button is no longer skewed or stretched.</span></span>  
  
3.  <span data-ttu-id="2d117-114">Animasyonun süresiz olarak tekrarlar.</span><span class="sxs-lookup"><span data-stu-id="2d117-114">Repeats the animation indefinitely.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d117-115">Anahtarı türetin çerçeveler <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> nesnesi oluşturma değerler arasında ani atlar, diğer bir deyişle, animasyonun hareketi düzensiz olur.</span><span class="sxs-lookup"><span data-stu-id="2d117-115">Key frames that derive from the <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> object create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="2d117-116">Tam bir örnek için bkz: [ana kare animasyon örneği](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="2d117-116">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d117-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2d117-117">See Also</span></span>  
 <xref:System.Windows.Media.MatrixTransform.Matrix%2A>  
 <xref:System.Windows.Media.MatrixTransform>  
 [<span data-ttu-id="2d117-118">Anahtar çerçeve animasyonları genel bakış</span><span class="sxs-lookup"><span data-stu-id="2d117-118">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="2d117-119">Anahtar çerçeve nasıl yapılır konuları</span><span class="sxs-lookup"><span data-stu-id="2d117-119">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
