---
title: 'Nasıl yapılır: Metne Animasyon Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: 56336c45639168c6432b92fe555c6d37448cb7cd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720515"
---
# <a name="how-to-apply-animations-to-text"></a><span data-ttu-id="84a56-102">Nasıl yapılır: Metne Animasyon Uygulama</span><span class="sxs-lookup"><span data-stu-id="84a56-102">How to: Apply Animations to Text</span></span>
<span data-ttu-id="84a56-103">Animasyonları, görüntü ve metin uygulamanızın görünümünü değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84a56-103">Animations can alter the display and appearance of text in your application.</span></span> <span data-ttu-id="84a56-104">Aşağıdaki örnekler animasyonları farklı türde metin görünümünü kullanın. bir <xref:System.Windows.Controls.TextBlock> denetimi.</span><span class="sxs-lookup"><span data-stu-id="84a56-104">The following examples use different types of animations to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84a56-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="84a56-105">Example</span></span>  
 <span data-ttu-id="84a56-106">Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğu genişliğini animasyon uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="84a56-106">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the width of the text block.</span></span> <span data-ttu-id="84a56-107">Genişlik değeri metin bloğunun genişliğini 0 olarak 10 saniye süresince değiştirir ve ardından genişlik değerleri tersine çevirir ve devam eder.</span><span class="sxs-lookup"><span data-stu-id="84a56-107">The width value changes from the width of the text block to 0 over a duration of 10 seconds, and then reverses the width values and continues.</span></span> <span data-ttu-id="84a56-108">Bu tür bir animasyon bir temizleme efekti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="84a56-108">This type of animation creates a wipe effect.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 <span data-ttu-id="84a56-109">Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğu opaklığına animasyon için.</span><span class="sxs-lookup"><span data-stu-id="84a56-109">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the opacity of the text block.</span></span> <span data-ttu-id="84a56-110">Geçirgenlik değeri 1.0 5 saniye süresince 0 olarak değiştirir ve ardından opaklık değerleri tersine çevirir ve devam eder.</span><span class="sxs-lookup"><span data-stu-id="84a56-110">The opacity value changes from 1.0 to 0 over a duration of 5 seconds, and then reverses the opacity values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 <span data-ttu-id="84a56-111">Aşağıdaki diyagramda etkisini gösterir <xref:System.Windows.Controls.TextBlock> gelen saydamlığını değiştirme denetimi `1.00` için `0.00` tarafından tanımlanan 5 saniyelik aralığına sırasında <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span><span class="sxs-lookup"><span data-stu-id="84a56-111">The following diagram shows the effect of the <xref:System.Windows.Controls.TextBlock> control changing its opacity from `1.00` to `0.00` during the 5-second interval defined by the <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span></span>  
  
 <span data-ttu-id="84a56-112">![Opaklık 1,00 0.00 değiştirme metni](../../../../docs/framework/wpf/advanced/media/fadedtext01.png "FadedText01")</span><span class="sxs-lookup"><span data-stu-id="84a56-112">![Text changing opacity from 1.00 to 0.00](../../../../docs/framework/wpf/advanced/media/fadedtext01.png "FadedText01")</span></span>  
<span data-ttu-id="84a56-113">Metin opaklık 1,00 0.00 değiştirme</span><span class="sxs-lookup"><span data-stu-id="84a56-113">Text Opacity changing from 1.00 to 0.00</span></span>  
  
 <span data-ttu-id="84a56-114">Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.ColorAnimation> metin bloğu ön plan rengini animasyon uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="84a56-114">The following example uses a <xref:System.Windows.Media.Animation.ColorAnimation> to animate the foreground color of the text block.</span></span> <span data-ttu-id="84a56-115">Ön plan rengi değer rengi 5 saniye süre içinde ikinci bir renge değişir ve ardından renk değerleri tersine çevirir ve devam eder.</span><span class="sxs-lookup"><span data-stu-id="84a56-115">The foreground color value changes from one color to a second color over a duration of 5 seconds, and then reverses the color values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 <span data-ttu-id="84a56-116">Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğu döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="84a56-116">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to rotate the text block.</span></span> <span data-ttu-id="84a56-117">Metin bloğu, tam bir dönüşü 20 saniye süresince gerçekleştirir ve ardından tekrar devam eder.</span><span class="sxs-lookup"><span data-stu-id="84a56-117">The text block performs a full rotation over a duration of 20 seconds, and then continues to repeat the rotation.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a><span data-ttu-id="84a56-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84a56-118">See also</span></span>
- [<span data-ttu-id="84a56-119">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="84a56-119">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
