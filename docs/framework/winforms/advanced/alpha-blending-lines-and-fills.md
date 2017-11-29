---
title: "Çizgi ve Dolgularda Alfa Karışım Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5b3c0ee3ec82d4d8447c43b7dc9b275591ebe890
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="alpha-blending-lines-and-fills"></a><span data-ttu-id="2a0fa-102">Çizgi ve Dolgularda Alfa Karışım Kullanma</span><span class="sxs-lookup"><span data-stu-id="2a0fa-102">Alpha Blending Lines and Fills</span></span>
<span data-ttu-id="2a0fa-103">İçinde [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], bir renk 32-bit 8 bit her alfa, kırmızı, yeşil ve mavi ile değerdir.</span><span class="sxs-lookup"><span data-stu-id="2a0fa-103">In [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], a color is a 32-bit value with 8 bits each for alpha, red, green, and blue.</span></span> <span data-ttu-id="2a0fa-104">Renk saydam alfa değeri gösterir — için renk karıştırılan arka plan rengiyle uzantı.</span><span class="sxs-lookup"><span data-stu-id="2a0fa-104">The alpha value indicates the transparency of the color — the extent to which the color is blended with the background color.</span></span> <span data-ttu-id="2a0fa-105">Alfa değerleri aralık 0 ile 255, 0 tamamen saydam rengi temsil ettiği ile 255 arasında bir tam olarak donuk rengi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2a0fa-105">Alpha values range from 0 through 255, where 0 represents a fully transparent color, and 255 represents a fully opaque color.</span></span>  
  
 <span data-ttu-id="2a0fa-106">Alfa karıştırma piksel piksel karıştırma kaynak ve arka plan rengi verilerini olur.</span><span class="sxs-lookup"><span data-stu-id="2a0fa-106">Alpha blending is a pixel-by-pixel blending of source and background color data.</span></span> <span data-ttu-id="2a0fa-107">Belirtilen kaynak rengin üç bileşenlerinin (kırmızı, yeşil, mavi) her biri aşağıdaki formülü göre arka plan rengi karşılık gelen bileşeni ile karıştırılan:</span><span class="sxs-lookup"><span data-stu-id="2a0fa-107">Each of the three components (red, green, blue) of a given source color is blended with the corresponding component of the background color according to the following formula:</span></span>  
  
 <span data-ttu-id="2a0fa-108">displayColor sourceColor × alfa = / 255 + backgroundColor × (255 – alfa) / 255</span><span class="sxs-lookup"><span data-stu-id="2a0fa-108">displayColor = sourceColor × alpha / 255 + backgroundColor × (255 – alpha) / 255</span></span>  
  
 <span data-ttu-id="2a0fa-109">Örneğin, kaynak rengi kırmızı bileşeninin 150 ve arka plan rengi kırmızı bileşeninin 100 varsayalım.</span><span class="sxs-lookup"><span data-stu-id="2a0fa-109">For example, suppose the red component of the source color is 150 and the red component of the background color is 100.</span></span> <span data-ttu-id="2a0fa-110">Alfa değeri 200 ise, sonuç rengi kırmızı bileşeninin aşağıdaki gibi hesaplanır:</span><span class="sxs-lookup"><span data-stu-id="2a0fa-110">If the alpha value is 200, the red component of the resultant color is calculated as follows:</span></span>  
  
 <span data-ttu-id="2a0fa-111">150 × 200 / 255 + 100 × (255 – 200) / 255 = 139</span><span class="sxs-lookup"><span data-stu-id="2a0fa-111">150 × 200 / 255 + 100 × (255 – 200) / 255 = 139</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2a0fa-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2a0fa-112">In This Section</span></span>  
 [<span data-ttu-id="2a0fa-113">Nasıl yapılır: donuk ve yarı saydam çizgiler çizme</span><span class="sxs-lookup"><span data-stu-id="2a0fa-113">How to: Draw Opaque and Semitransparent Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)  
 <span data-ttu-id="2a0fa-114">Alfa karışık çizgiler çizme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2a0fa-114">Shows how to draw alpha-blended lines.</span></span>  
  
 [<span data-ttu-id="2a0fa-115">Nasıl yapılır: donuk ve yarı saydam fırçalarla çizme</span><span class="sxs-lookup"><span data-stu-id="2a0fa-115">How to: Draw with Opaque and Semitransparent Brushes</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 <span data-ttu-id="2a0fa-116">Alfa karışım fırçalar ile açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2a0fa-116">Explains how to alpha-blend with brushes.</span></span>  
  
 [<span data-ttu-id="2a0fa-117">Nasıl yapılır: denetim Alfa karışım için birleştirme modunu kullanma</span><span class="sxs-lookup"><span data-stu-id="2a0fa-117">How to: Use Compositing Mode to Control Alpha Blending</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-compositing-mode-to-control-alpha-blending.md)  
 <span data-ttu-id="2a0fa-118">Alfa karıştırma kullanarak denetlemek açıklar <xref:System.Drawing.Drawing2D.CompositingMode>.</span><span class="sxs-lookup"><span data-stu-id="2a0fa-118">Describes how to control alpha blending using <xref:System.Drawing.Drawing2D.CompositingMode>.</span></span>  
  
 [<span data-ttu-id="2a0fa-119">Nasıl yapılır: görüntüleri alfa değerleri ayarlamak için renk matrisi kullanma</span><span class="sxs-lookup"><span data-stu-id="2a0fa-119">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 <span data-ttu-id="2a0fa-120">Nasıl kullanılacağı açıklanmaktadır bir <xref:System.Drawing.Imaging.ColorMatrix> Alfa karışım denetlemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="2a0fa-120">Explains how to use a <xref:System.Drawing.Imaging.ColorMatrix> object to control alpha blending.</span></span>
