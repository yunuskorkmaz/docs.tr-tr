---
title: Çizgi ve Dolgularda Alfa Karışım Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- lines [Windows Forms], adding transparency
- examples [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with lines
- alpha blending
- lines [Windows Forms], alpha blending
- fills [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with fills
- shapes [Windows Forms], adding transparency
ms.assetid: 5440f48c-3ac9-44c3-b170-c1c110bdbab8
ms.openlocfilehash: 66061341ee6539e2172c537a0b2a6ec9ff87565c
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506110"
---
# <a name="alpha-blending-lines-and-fills"></a><span data-ttu-id="1aca3-102">Çizgi ve Dolgularda Alfa Karışım Kullanma</span><span class="sxs-lookup"><span data-stu-id="1aca3-102">Alpha Blending Lines and Fills</span></span>
<span data-ttu-id="1aca3-103">GDI +'da bir renk 32-bit 8 bit her alfa, kırmızı, yeşil ve mavi için değerdir.</span><span class="sxs-lookup"><span data-stu-id="1aca3-103">In GDI+, a color is a 32-bit value with 8 bits each for alpha, red, green, and blue.</span></span> <span data-ttu-id="1aca3-104">Renk saydam alfa değeri gösterir — istediğiniz rengi karışık arka plan rengi ile uzantısı.</span><span class="sxs-lookup"><span data-stu-id="1aca3-104">The alpha value indicates the transparency of the color — the extent to which the color is blended with the background color.</span></span> <span data-ttu-id="1aca3-105">Alfa değerleri aralığı 0 ile 255, burada 0 tamamen saydam bir rengi temsil eder ve 255 arasında bir tam opak rengi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1aca3-105">Alpha values range from 0 through 255, where 0 represents a fully transparent color, and 255 represents a fully opaque color.</span></span>  
  
 <span data-ttu-id="1aca3-106">Alfa karıştırma piksel piksel karıştırma kaynak ve arka plan rengi veri olur.</span><span class="sxs-lookup"><span data-stu-id="1aca3-106">Alpha blending is a pixel-by-pixel blending of source and background color data.</span></span> <span data-ttu-id="1aca3-107">Her bir verilen kaynak rengin üç bileşen (kırmızı, yeşil, mavi) karşılık gelen bileşenle göre şu formül olarak ayarlayın arka plan renginin harmanlanan:</span><span class="sxs-lookup"><span data-stu-id="1aca3-107">Each of the three components (red, green, blue) of a given source color is blended with the corresponding component of the background color according to the following formula:</span></span>  
  
 <span data-ttu-id="1aca3-108">displayColor sourceColor × alpha = / 255 + backgroundColor × (255 – alfa) / 255</span><span class="sxs-lookup"><span data-stu-id="1aca3-108">displayColor = sourceColor × alpha / 255 + backgroundColor × (255 – alpha) / 255</span></span>  
  
 <span data-ttu-id="1aca3-109">Örneğin, kaynak rengin kırmızı bileşeni 150 ve arka plan rengini kırmızı bileşeni 100 varsayalım.</span><span class="sxs-lookup"><span data-stu-id="1aca3-109">For example, suppose the red component of the source color is 150 and the red component of the background color is 100.</span></span> <span data-ttu-id="1aca3-110">Alfa değeri 200 ise, sonuç rengin kırmızı bileşeni şu şekilde hesaplanır:</span><span class="sxs-lookup"><span data-stu-id="1aca3-110">If the alpha value is 200, the red component of the resultant color is calculated as follows:</span></span>  
  
 <span data-ttu-id="1aca3-111">150 × 200 / 255 + 100 × (255 – 200) / 255 = 139</span><span class="sxs-lookup"><span data-stu-id="1aca3-111">150 × 200 / 255 + 100 × (255 – 200) / 255 = 139</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1aca3-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1aca3-112">In This Section</span></span>  
 [<span data-ttu-id="1aca3-113">Nasıl yapılır: Donuk ve yarı saydam çizgiler çizme</span><span class="sxs-lookup"><span data-stu-id="1aca3-113">How to: Draw Opaque and Semitransparent Lines</span></span>](how-to-draw-opaque-and-semitransparent-lines.md)  
 <span data-ttu-id="1aca3-114">Alfa karışık çizgi çizmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1aca3-114">Shows how to draw alpha-blended lines.</span></span>  
  
 [<span data-ttu-id="1aca3-115">Nasıl yapılır: Donuk ve yarı saydam fırçalarla fırçaları ile çizme</span><span class="sxs-lookup"><span data-stu-id="1aca3-115">How to: Draw with Opaque and Semitransparent Brushes</span></span>](how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 <span data-ttu-id="1aca3-116">Fırçalar ile alfa karıştırma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1aca3-116">Explains how to alpha-blend with brushes.</span></span>  
  
 [<span data-ttu-id="1aca3-117">Nasıl yapılır: Alfa karışım kullanmayı denetlemek için birleştirme modunu kullanma</span><span class="sxs-lookup"><span data-stu-id="1aca3-117">How to: Use Compositing Mode to Control Alpha Blending</span></span>](how-to-use-compositing-mode-to-control-alpha-blending.md)  
 <span data-ttu-id="1aca3-118">Alfa karıştırma kullanarak denetlemek nasıl açıklar <xref:System.Drawing.Drawing2D.CompositingMode>.</span><span class="sxs-lookup"><span data-stu-id="1aca3-118">Describes how to control alpha blending using <xref:System.Drawing.Drawing2D.CompositingMode>.</span></span>  
  
 [<span data-ttu-id="1aca3-119">Nasıl yapılır: Görüntülerdeki alfa değerleri ayarlamak için renk matrisi kullanma</span><span class="sxs-lookup"><span data-stu-id="1aca3-119">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>](how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 <span data-ttu-id="1aca3-120">Nasıl kullanılacağını açıklayan bir <xref:System.Drawing.Imaging.ColorMatrix> alfa karıştırma denetlemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="1aca3-120">Explains how to use a <xref:System.Drawing.Imaging.ColorMatrix> object to control alpha blending.</span></span>
