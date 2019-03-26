---
title: 'Nasıl yapılır: Metne Animasyon Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: 4cc7932b43f8a3c35d750f9a9020e16257867f76
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463130"
---
# <a name="how-to-apply-animations-to-text"></a><span data-ttu-id="6c8ef-102">Nasıl yapılır: Metne Animasyon Uygulama</span><span class="sxs-lookup"><span data-stu-id="6c8ef-102">How to: Apply Animations to Text</span></span>
<span data-ttu-id="6c8ef-103">Animasyonları, görüntü ve metin uygulamanızın görünümünü değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c8ef-103">Animations can alter the display and appearance of text in your application.</span></span> <span data-ttu-id="6c8ef-104">Aşağıdaki örnekler animasyonları farklı türde metin görünümünü kullanın. bir <xref:System.Windows.Controls.TextBlock> denetimi.</span><span class="sxs-lookup"><span data-stu-id="6c8ef-104">The following examples use different types of animations to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c8ef-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c8ef-105">Example</span></span>  
 <span data-ttu-id="6c8ef-106">Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğu genişliğini animasyon uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="6c8ef-106">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the width of the text block.</span></span> <span data-ttu-id="6c8ef-107">Genişlik değeri metin bloğunun genişliğini 0 olarak 10 saniye süresince değiştirir ve ardından genişlik değerleri tersine çevirir ve devam eder.</span><span class="sxs-lookup"><span data-stu-id="6c8ef-107">The width value changes from the width of the text block to 0 over a duration of 10 seconds, and then reverses the width values and continues.</span></span> <span data-ttu-id="6c8ef-108">Bu tür bir animasyon bir temizleme efekti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6c8ef-108">This type of animation creates a wipe effect.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 <span data-ttu-id="6c8ef-109">Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğu opaklığına animasyon için.</span><span class="sxs-lookup"><span data-stu-id="6c8ef-109">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the opacity of the text block.</span></span> <span data-ttu-id="6c8ef-110">Geçirgenlik değeri 1.0 5 saniye süresince 0 olarak değiştirir ve ardından opaklık değerleri tersine çevirir ve devam eder.</span><span class="sxs-lookup"><span data-stu-id="6c8ef-110">The opacity value changes from 1.0 to 0 over a duration of 5 seconds, and then reverses the opacity values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 <span data-ttu-id="6c8ef-111">Aşağıdaki diyagramda etkisini gösterir <xref:System.Windows.Controls.TextBlock> gelen saydamlığını değiştirme denetimi `1.00` için `0.00` tarafından tanımlanan 5 saniyelik aralığına sırasında <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span><span class="sxs-lookup"><span data-stu-id="6c8ef-111">The following diagram shows the effect of the <xref:System.Windows.Controls.TextBlock> control changing its opacity from `1.00` to `0.00` during the 5-second interval defined by the <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span></span>  
  
 ![Opaklık 1,00 0.00 değiştirme metni.](./media/how-to-apply-animations-to-text/faded-text-opacity-change.png)  
   
 <span data-ttu-id="6c8ef-113">Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.ColorAnimation> metin bloğu ön plan rengini animasyon uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="6c8ef-113">The following example uses a <xref:System.Windows.Media.Animation.ColorAnimation> to animate the foreground color of the text block.</span></span> <span data-ttu-id="6c8ef-114">Ön plan rengi değer rengi 5 saniye süre içinde ikinci bir renge değişir ve ardından renk değerleri tersine çevirir ve devam eder.</span><span class="sxs-lookup"><span data-stu-id="6c8ef-114">The foreground color value changes from one color to a second color over a duration of 5 seconds, and then reverses the color values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 <span data-ttu-id="6c8ef-115">Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğu döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="6c8ef-115">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to rotate the text block.</span></span> <span data-ttu-id="6c8ef-116">Metin bloğu, tam bir dönüşü 20 saniye süresince gerçekleştirir ve ardından tekrar devam eder.</span><span class="sxs-lookup"><span data-stu-id="6c8ef-116">The text block performs a full rotation over a duration of 20 seconds, and then continues to repeat the rotation.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a><span data-ttu-id="6c8ef-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c8ef-117">See also</span></span>
- [<span data-ttu-id="6c8ef-118">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="6c8ef-118">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
