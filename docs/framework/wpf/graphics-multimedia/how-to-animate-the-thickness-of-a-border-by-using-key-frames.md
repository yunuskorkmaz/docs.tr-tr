---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak Kenarlık Kalınlığına Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: 0c5dc61ac1a4cc3f2aba83ac3a4a71084b553a2a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087366"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a><span data-ttu-id="ff03a-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak Kenarlık Kalınlığına Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="ff03a-102">How to: Animate the Thickness of a Border by Using Key Frames</span></span>
<span data-ttu-id="ff03a-103">Bu örnek, animasyon ekleme işlemi gösterilmektedir <xref:System.Windows.Controls.Control.BorderThickness%2A> özelliği bir <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="ff03a-103">This example shows how to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff03a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ff03a-104">Example</span></span>  
 <span data-ttu-id="ff03a-105">Aşağıdaki örnekte <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> animasyon uygulamak için sınıfı <xref:System.Windows.Controls.Control.BorderThickness%2A> özelliği bir <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="ff03a-105">The following example uses the <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="ff03a-106">Bu animasyonu üç anahtar çerçeveler şu şekilde kullanılır:</span><span class="sxs-lookup"><span data-stu-id="ff03a-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="ff03a-107">İlk yarım saniye boyunca bir örneği kullanan <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> kenarlık kalınlığı aşamalı olarak artırmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="ff03a-107">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> class to gradually increase the thickness of the border.</span></span> <span data-ttu-id="ff03a-108">Örnekte <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> değerler arasında düzgün ve doğrusal bir artış oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="ff03a-108">The example uses <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> to create a smooth linear increase between values.</span></span>  
  
2.  <span data-ttu-id="ff03a-109">Sonraki sonunda yarım saniye kullanan bir örneğini <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> aniden kenarlık kalınlığı artırmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="ff03a-109">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> class to suddenly increase the thickness of the border.</span></span> <span data-ttu-id="ff03a-110">Bu gibi ayrı anahtar çerçeveler türetilen <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> ani atlama, değerleri arasında oluşturur, bu animasyonu hareketini düzensiz olur.</span><span class="sxs-lookup"><span data-stu-id="ff03a-110">Discrete key frames like those derived from <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
3.  <span data-ttu-id="ff03a-111">Son iki saniye boyunca bir örneği kullanan <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> kenarlık kalınlığı azaltmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="ff03a-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> class to decrease the thickness of the border.</span></span> <span data-ttu-id="ff03a-112">Eğri anahtar çercevesi olanlar gibi türetilen <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> değerlerine göre değerleri arasında bir değişken geçiş oluşturmak <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ff03a-112">Spline key frames like those derived from <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="ff03a-113">Bu anahtar çerçeve animasyonu yavaş başlar ve zaman diliminin sonuna doğru katlanarak hızlandırır.</span><span class="sxs-lookup"><span data-stu-id="ff03a-113">In this key frame, the animation starts off slow and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="ff03a-114">Tam bir örnek için bkz. [ana kare animasyon örnek](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="ff03a-114">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff03a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff03a-115">See also</span></span>

- <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>
- [<span data-ttu-id="ff03a-116">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ff03a-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="ff03a-117">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="ff03a-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
- [<span data-ttu-id="ff03a-118">BorderThickness Değerine Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="ff03a-118">Animate a BorderThickness Value</span></span>](../controls/how-to-animate-a-borderthickness-value.md)
