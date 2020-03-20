---
title: 'Nasıl yapılır: Metne Animasyon Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: ed2f3beb904f724ac93e2c4033aa6b2eb3fa1290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174634"
---
# <a name="how-to-apply-animations-to-text"></a><span data-ttu-id="1b40d-102">Nasıl yapılır: Metne Animasyon Uygulama</span><span class="sxs-lookup"><span data-stu-id="1b40d-102">How to: Apply Animations to Text</span></span>
<span data-ttu-id="1b40d-103">Animasyonlar, uygulamanızdaki metnin görünümünü ve görünümünü değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="1b40d-103">Animations can alter the display and appearance of text in your application.</span></span> <span data-ttu-id="1b40d-104">Aşağıdaki örnekler, denetimdeki <xref:System.Windows.Controls.TextBlock> metnin görüntülenmesini etkilemek için farklı animasyon türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b40d-104">The following examples use different types of animations to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b40d-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="1b40d-105">Example</span></span>  
 <span data-ttu-id="1b40d-106">Aşağıdaki örnekte <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğunun genişliğini canlandırmak için a kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b40d-106">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the width of the text block.</span></span> <span data-ttu-id="1b40d-107">Genişlik değeri metin bloğunun genişliğinden 10 saniye lik bir süre içinde 0'a değişir ve ardından genişlik değerlerini tersine çevirir ve devam eder.</span><span class="sxs-lookup"><span data-stu-id="1b40d-107">The width value changes from the width of the text block to 0 over a duration of 10 seconds, and then reverses the width values and continues.</span></span> <span data-ttu-id="1b40d-108">Bu tür animasyonlar silme efekti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1b40d-108">This type of animation creates a wipe effect.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 <span data-ttu-id="1b40d-109">Aşağıdaki örnekte <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğunun opaklığını canlandırmak için a kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b40d-109">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the opacity of the text block.</span></span> <span data-ttu-id="1b40d-110">Opaklık değeri 5 saniyelik bir süre içinde 1,0'dan 0'a değişir ve sonra opaklık değerlerini tersine çevirir ve devam eder.</span><span class="sxs-lookup"><span data-stu-id="1b40d-110">The opacity value changes from 1.0 to 0 over a duration of 5 seconds, and then reverses the opacity values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 <span data-ttu-id="1b40d-111">Aşağıdaki <xref:System.Windows.Controls.TextBlock> diyagram, denetimin opaklığını `1.00` `0.00` 5 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>saniyelik aralıktan .</span><span class="sxs-lookup"><span data-stu-id="1b40d-111">The following diagram shows the effect of the <xref:System.Windows.Controls.TextBlock> control changing its opacity from `1.00` to `0.00` during the 5-second interval defined by the <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span></span>  
  
 ![Donukluğu 1,00'den 0,00'a değiştiren metin.](./media/how-to-apply-animations-to-text/faded-text-opacity-change.png)  

 <span data-ttu-id="1b40d-113">Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.ColorAnimation> metin bloğunun ön plan rengini canlandırmak için a kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b40d-113">The following example uses a <xref:System.Windows.Media.Animation.ColorAnimation> to animate the foreground color of the text block.</span></span> <span data-ttu-id="1b40d-114">Ön plan renk değeri 5 saniye lik bir süre içinde bir renkten ikinci renge dönüşür ve ardından renk değerlerini tersine çevirir ve devam eder.</span><span class="sxs-lookup"><span data-stu-id="1b40d-114">The foreground color value changes from one color to a second color over a duration of 5 seconds, and then reverses the color values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 <span data-ttu-id="1b40d-115">Aşağıdaki örnekte <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğunu döndürmek için a kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b40d-115">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to rotate the text block.</span></span> <span data-ttu-id="1b40d-116">Metin bloğu 20 saniye boyunca tam bir döndürme gerçekleştirir ve sonra döndürmeyi yinelemeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="1b40d-116">The text block performs a full rotation over a duration of 20 seconds, and then continues to repeat the rotation.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a><span data-ttu-id="1b40d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b40d-117">See also</span></span>

- [<span data-ttu-id="1b40d-118">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="1b40d-118">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
