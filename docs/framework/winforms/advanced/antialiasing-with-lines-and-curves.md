---
title: "Nasıl yapılır: Çizgiler ve Eğrilerle Düzgünleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- antialiasing
- antialiasing [Windows Forms], smoothing modes
- GDI+, antialiasing
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d69d635fbdd8720937cd189826c1496b8126ddef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="antialiasing-with-lines-and-curves"></a><span data-ttu-id="c1070-102">Nasıl yapılır: Çizgiler ve Eğrilerle Düzgünleştirme</span><span class="sxs-lookup"><span data-stu-id="c1070-102">Antialiasing with Lines and Curves</span></span>
<span data-ttu-id="c1070-103">Kullandığınızda [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] bir çizgi çizmek için başlangıç noktası ve bitiş noktası satırının sağlar, ancak tek pikselleri hakkında hiçbir bilgi satırına sağlamak zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1070-103">When you use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to draw a line, you provide the starting point and ending point of the line, but you do not have to provide any information about the individual pixels on the line.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="c1070-104">belirli görüntü cihazında çizgisini göstermek için hangi piksel yanar belirlemek için görüntüleme sürücü yazılımı ile birlikte çalışır.</span><span class="sxs-lookup"><span data-stu-id="c1070-104"> works in conjunction with the display driver software to determine which pixels will be turned on to show the line on a particular display device.</span></span>  
  
## <a name="aliasing"></a><span data-ttu-id="c1070-105">Diğer ad</span><span class="sxs-lookup"><span data-stu-id="c1070-105">Aliasing</span></span>  
 <span data-ttu-id="c1070-106">(4, 2) noktadan noktaya (16, 10) gider düz kırmızı çizgi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="c1070-106">Consider the straight red line that goes from the point (4, 2) to the point (16, 10).</span></span> <span data-ttu-id="c1070-107">Koordinat sistemi sol üst köşedeki kaynağına sahip ve ölçü piksel olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="c1070-107">Assume the coordinate system has its origin in the upper-left corner and that the unit of measure is the pixel.</span></span> <span data-ttu-id="c1070-108">Ayrıca x ekseni aşağı sağa ve y ekseni noktaları işaret varsayalım.</span><span class="sxs-lookup"><span data-stu-id="c1070-108">Also assume that the x-axis points to the right and the y-axis points down.</span></span> <span data-ttu-id="c1070-109">Aşağıdaki çizimde bir renkli arka planda kırmızı çizgi büyütülmüş bir görünümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1070-109">The following illustration shows an enlarged view of the red line drawn on a multicolored background.</span></span>  
  
 <span data-ttu-id="c1070-110">![Satır, hiçbir düzgünleştirme](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art33.gif "AboutGdip02_Art33")</span><span class="sxs-lookup"><span data-stu-id="c1070-110">![Line, no antialiasing](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art33.gif "AboutGdip02_Art33")</span></span>  
  
 <span data-ttu-id="c1070-111">Çizgiyi işlemek için kullanılan kırmızı donuk pikseldir.</span><span class="sxs-lookup"><span data-stu-id="c1070-111">The red pixels used to render the line are opaque.</span></span> <span data-ttu-id="c1070-112">Satırda kısmen saydam piksel vardır.</span><span class="sxs-lookup"><span data-stu-id="c1070-112">There are no partially transparent pixels in the line.</span></span> <span data-ttu-id="c1070-113">Satır bakıma bir Merdiven arar ve bu tür bir çizgi işleme satır basit bir görünüm sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1070-113">This type of line rendering gives the line a jagged appearance, and the line looks somewhat like a staircase.</span></span> <span data-ttu-id="c1070-114">Bir Merdiven satırıyla temsil eden bu tekniği yumuşatma çağrılır; Merdiven teorik satırı için bir diğer ad değil.</span><span class="sxs-lookup"><span data-stu-id="c1070-114">This technique of representing a line with a staircase is called aliasing; the staircase is an alias for the theoretical line.</span></span>  
  
## <a name="antialiasing"></a><span data-ttu-id="c1070-115">Düzgünleştirme</span><span class="sxs-lookup"><span data-stu-id="c1070-115">Antialiasing</span></span>  
 <span data-ttu-id="c1070-116">Bir satır işlemek için daha karmaşık bir teknik kısmen saydam piksel donuk piksel birlikte kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c1070-116">A more sophisticated technique for rendering a line involves using partially transparent pixels along with opaque pixels.</span></span> <span data-ttu-id="c1070-117">Piksel saf kırmızı şeklinde ayarlanır veya bazı karışım kırmızı ve arka plan rengi, bağlı olarak ne kadar yakın satırına oldukları.</span><span class="sxs-lookup"><span data-stu-id="c1070-117">Pixels are set to pure red, or to some blend of red and the background color, depending on how close they are to the line.</span></span> <span data-ttu-id="c1070-118">Bu tür bir işleme düzgünleştirme denir ve İnsan göz daha kesintisiz olarak algılar bir satır ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="c1070-118">This type of rendering is called antialiasing and results in a line that the human eye perceives as more smooth.</span></span> <span data-ttu-id="c1070-119">Aşağıdaki çizimde, belirli piksel antialiased satır üretmek için arka plan nasıl karıştırılan gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1070-119">The following illustration shows how certain pixels are blended with the background to produce an antialiased line.</span></span>  
  
 <span data-ttu-id="c1070-120">![Çizgiyi düzgünleştirme](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art34.gif "AboutGdip02_Art34")</span><span class="sxs-lookup"><span data-stu-id="c1070-120">![Antialiasing a Line](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art34.gif "AboutGdip02_Art34")</span></span>  
  
 <span data-ttu-id="c1070-121">Yumuşatma, olarak da bilinir Düzgünleştirme eğrileri da uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c1070-121">Antialiasing, also called smoothing, can also be applied to curves.</span></span> <span data-ttu-id="c1070-122">Aşağıdaki çizimde bir düzleştirilmiş elips büyütülmüş bir görünümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1070-122">The following illustration shows an enlarged view of a smoothed ellipse.</span></span>  
  
 <span data-ttu-id="c1070-123">![Düzgünleştirme eğrileri](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art35.gif "AboutGdip02_Art35")</span><span class="sxs-lookup"><span data-stu-id="c1070-123">![Antialiasing Curves](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art35.gif "AboutGdip02_Art35")</span></span>  
  
 <span data-ttu-id="c1070-124">Aşağıdaki çizimde aynı elips gerçek boyutuna, düzgünleştirme olmadan bir kez ve bir kez düzgünleştirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1070-124">The following illustration shows the same ellipse in its actual size, once without antialiasing and once with antialiasing.</span></span>  
  
 <span data-ttu-id="c1070-125">![Düzgünleştirme örneği](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art36.gif "AboutGdip02_Art36")</span><span class="sxs-lookup"><span data-stu-id="c1070-125">![Antialiasing example](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art36.gif "AboutGdip02_Art36")</span></span>  
  
 <span data-ttu-id="c1070-126">Çizgiler ve eğrilerle düzgünleştirme kullanma çizmek için bir örneğini oluşturmak <xref:System.Drawing.Graphics> sınıfı ve ayarlayın, <xref:System.Drawing.Graphics.SmoothingMode%2A> özelliğine <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> veya <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>.</span><span class="sxs-lookup"><span data-stu-id="c1070-126">To draw lines and curves that use antialiasing, create an instance of the <xref:System.Drawing.Graphics> class and set its <xref:System.Drawing.Graphics.SmoothingMode%2A> property to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> or <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>.</span></span> <span data-ttu-id="c1070-127">Ardından çizim yöntemlerinden birini, aynı çağrı <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c1070-127">Then call one of the drawing methods of that same <xref:System.Drawing.Graphics> class.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## <a name="see-also"></a><span data-ttu-id="c1070-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1070-128">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=nameWithType>  
 [<span data-ttu-id="c1070-129">Çizgiler, eğriler ve şekiller</span><span class="sxs-lookup"><span data-stu-id="c1070-129">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="c1070-130">Nasıl yapılır: metinle düzgünleştirme kullanma</span><span class="sxs-lookup"><span data-stu-id="c1070-130">How to: Use Antialiasing with Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)
