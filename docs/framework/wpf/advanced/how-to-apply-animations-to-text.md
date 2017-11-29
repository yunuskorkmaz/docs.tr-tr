---
title: "Nasıl yapılır: Metne Animasyon Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0298462db5897e955bf0a2551cca7fc81bb27d89
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-apply-animations-to-text"></a><span data-ttu-id="df58b-102">Nasıl yapılır: Metne Animasyon Uygulama</span><span class="sxs-lookup"><span data-stu-id="df58b-102">How to: Apply Animations to Text</span></span>
<span data-ttu-id="df58b-103">Animasyon, görüntüleme ve uygulamanızdaki metnin görünümünü değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df58b-103">Animations can alter the display and appearance of text in your application.</span></span> <span data-ttu-id="df58b-104">Aşağıdaki örnekler farklı türdeki animasyonları metin görünümünü kullanın. bir <xref:System.Windows.Controls.TextBlock> denetim.</span><span class="sxs-lookup"><span data-stu-id="df58b-104">The following examples use different types of animations to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df58b-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="df58b-105">Example</span></span>  
 <span data-ttu-id="df58b-106">Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğunun genişliğini animasyon uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="df58b-106">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the width of the text block.</span></span> <span data-ttu-id="df58b-107">Genişlik değeri metin bloğunun genişliğini 10 saniye süresince 0 olarak değiştirir ve ardından genişlik değerleri tersine çevirir ve devam eder.</span><span class="sxs-lookup"><span data-stu-id="df58b-107">The width value changes from the width of the text block to 0 over a duration of 10 seconds, and then reverses the width values and continues.</span></span> <span data-ttu-id="df58b-108">Bu tür bir animasyon silme etkisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="df58b-108">This type of animation creates a wipe effect.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 <span data-ttu-id="df58b-109">Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğunun geçirgenliğini animasyon uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="df58b-109">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the opacity of the text block.</span></span> <span data-ttu-id="df58b-110">Geçirgenlik değeri 1.0 5 saniye süresince 0 olarak değiştirir ve ardından opaklık değerleri tersine çevirir ve devam eder.</span><span class="sxs-lookup"><span data-stu-id="df58b-110">The opacity value changes from 1.0 to 0 over a duration of 5 seconds, and then reverses the opacity values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 <span data-ttu-id="df58b-111">Aşağıdaki diyagramda etkisini gösterir <xref:System.Windows.Controls.TextBlock> saydamlığını gelen değiştirme denetim `1.00` için `0.00` tarafından tanımlanan 5 saniyelik aralık boyunca <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span><span class="sxs-lookup"><span data-stu-id="df58b-111">The following diagram shows the effect of the <xref:System.Windows.Controls.TextBlock> control changing its opacity from `1.00` to `0.00` during the 5-second interval defined by the <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span></span>  
  
 <span data-ttu-id="df58b-112">![Opaklık 1.00 0,00 için değiştirme metin](../../../../docs/framework/wpf/advanced/media/fadedtext01.png "FadedText01")</span><span class="sxs-lookup"><span data-stu-id="df58b-112">![Text changing opacity from 1.00 to 0.00](../../../../docs/framework/wpf/advanced/media/fadedtext01.png "FadedText01")</span></span>  
<span data-ttu-id="df58b-113">Metin geçirgenliği 1.00 0,00 için değiştirme</span><span class="sxs-lookup"><span data-stu-id="df58b-113">Text Opacity changing from 1.00 to 0.00</span></span>  
  
 <span data-ttu-id="df58b-114">Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.Animation.ColorAnimation> metin bloğu ön plan rengini animasyon uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="df58b-114">The following example uses a <xref:System.Windows.Media.Animation.ColorAnimation> to animate the foreground color of the text block.</span></span> <span data-ttu-id="df58b-115">Ön plan rengi değeri bir renkten ikinci bir renge 5 saniye süresince değiştirir ve ardından renk değerleri tersine çevirir ve devam eder.</span><span class="sxs-lookup"><span data-stu-id="df58b-115">The foreground color value changes from one color to a second color over a duration of 5 seconds, and then reverses the color values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 <span data-ttu-id="df58b-116">Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğunu döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="df58b-116">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to rotate the text block.</span></span> <span data-ttu-id="df58b-117">Metin bloğu 20 saniye süresince tam dönmesini gerçekleştirir ve tekrar devam eder.</span><span class="sxs-lookup"><span data-stu-id="df58b-117">The text block performs a full rotation over a duration of 20 seconds, and then continues to repeat the rotation.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a><span data-ttu-id="df58b-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df58b-118">See Also</span></span>  
 [<span data-ttu-id="df58b-119">Animasyon genel bakış</span><span class="sxs-lookup"><span data-stu-id="df58b-119">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
