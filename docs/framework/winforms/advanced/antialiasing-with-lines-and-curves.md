---
title: 'Nasıl yapılır: Çizgiler ve Eğrilerle Düzgünleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- antialiasing
- antialiasing [Windows Forms], smoothing modes
- GDI+, antialiasing
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
ms.openlocfilehash: 871c5cb3cd9356f677633acb04fe82021a9787c5
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506142"
---
# <a name="antialiasing-with-lines-and-curves"></a><span data-ttu-id="88a75-102">Nasıl yapılır: Çizgiler ve Eğrilerle Düzgünleştirme</span><span class="sxs-lookup"><span data-stu-id="88a75-102">Antialiasing with Lines and Curves</span></span>
<span data-ttu-id="88a75-103">GDI +'da bir çizgi çizmek için kullandığınızda, başlangıç ve bitiş noktasını sağlar, ancak satırda tek tek her piksel hakkında hiçbir bilgi sağlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="88a75-103">When you use GDI+ to draw a line, you provide the starting point and ending point of the line, but you do not have to provide any information about the individual pixels on the line.</span></span> <span data-ttu-id="88a75-104">GDI +'da bir özel görüntü cihazında çizgisini göstermek için hangi piksel yanar belirlemek için görüntüleme sürücü yazılım ile birlikte çalışır.</span><span class="sxs-lookup"><span data-stu-id="88a75-104">GDI+ works in conjunction with the display driver software to determine which pixels will be turned on to show the line on a particular display device.</span></span>  
  
## <a name="aliasing"></a><span data-ttu-id="88a75-105">Diğer ad kullanımı</span><span class="sxs-lookup"><span data-stu-id="88a75-105">Aliasing</span></span>  
 <span data-ttu-id="88a75-106">(4, 2) noktadan noktaya (16, 10) giden düz kırmızı çizgi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="88a75-106">Consider the straight red line that goes from the point (4, 2) to the point (16, 10).</span></span> <span data-ttu-id="88a75-107">Koordinat sistemi sol üst köşedeki kaynağına sahip ve ölçü piksel olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="88a75-107">Assume the coordinate system has its origin in the upper-left corner and that the unit of measure is the pixel.</span></span> <span data-ttu-id="88a75-108">X ekseni aşağı sağ ve y ekseni noktaları işaret da varsayılır.</span><span class="sxs-lookup"><span data-stu-id="88a75-108">Also assume that the x-axis points to the right and the y-axis points down.</span></span> <span data-ttu-id="88a75-109">Aşağıdaki çizimde, renkli bir arka plan üzerinde kırmızı çizgi genişletilmiş bir görünümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="88a75-109">The following illustration shows an enlarged view of the red line drawn on a multicolored background.</span></span>  
  
 <span data-ttu-id="88a75-110">![Satır, hiçbir düzgünleştirme](./media/aboutgdip02-art33.gif "AboutGdip02_Art33")</span><span class="sxs-lookup"><span data-stu-id="88a75-110">![Line, no antialiasing](./media/aboutgdip02-art33.gif "AboutGdip02_Art33")</span></span>  
  
 <span data-ttu-id="88a75-111">Satır işlemek için kullanılan kırmızı donuk pikseldir.</span><span class="sxs-lookup"><span data-stu-id="88a75-111">The red pixels used to render the line are opaque.</span></span> <span data-ttu-id="88a75-112">Satırda kısmen saydam piksel vardır.</span><span class="sxs-lookup"><span data-stu-id="88a75-112">There are no partially transparent pixels in the line.</span></span> <span data-ttu-id="88a75-113">Bu tür bir çizgi işleme satır pürüzlü bir görünümünü sağlar ve bir Merdiven bakıma satırı görünür.</span><span class="sxs-lookup"><span data-stu-id="88a75-113">This type of line rendering gives the line a jagged appearance, and the line looks somewhat like a staircase.</span></span> <span data-ttu-id="88a75-114">Bir Merdiven içeren bir satırı temsil eden bu tekniği yumuşatma çağrılır Merdiven, teorik satırı için bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="88a75-114">This technique of representing a line with a staircase is called aliasing; the staircase is an alias for the theoretical line.</span></span>  
  
## <a name="antialiasing"></a><span data-ttu-id="88a75-115">Düzgünleştirme</span><span class="sxs-lookup"><span data-stu-id="88a75-115">Antialiasing</span></span>  
 <span data-ttu-id="88a75-116">Bir satır işlemek için daha karmaşık bir teknik, kısmen saydam piksel donuk piksel ile birlikte kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="88a75-116">A more sophisticated technique for rendering a line involves using partially transparent pixels along with opaque pixels.</span></span> <span data-ttu-id="88a75-117">Bazı blend'e kırmızı ve arka plan rengi, bağlı olarak ne kadar yakın satırına oldukları veya piksel saf kırmızı belirlenmesi.</span><span class="sxs-lookup"><span data-stu-id="88a75-117">Pixels are set to pure red, or to some blend of red and the background color, depending on how close they are to the line.</span></span> <span data-ttu-id="88a75-118">Bu tür bir işleme düzgünleştirme olarak adlandırılır ve İnsan gözüyle daha kesintisiz olarak algılar. bir satır sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="88a75-118">This type of rendering is called antialiasing and results in a line that the human eye perceives as more smooth.</span></span> <span data-ttu-id="88a75-119">Aşağıdaki çizim, belirli piksel antialiased çizgi oluşturmak için arka plan ile nasıl karışık gösterir.</span><span class="sxs-lookup"><span data-stu-id="88a75-119">The following illustration shows how certain pixels are blended with the background to produce an antialiased line.</span></span>  
  
 <span data-ttu-id="88a75-120">![Bir satır düzgünleştirme](./media/aboutgdip02-art34.gif "AboutGdip02_Art34")</span><span class="sxs-lookup"><span data-stu-id="88a75-120">![Antialiasing a Line](./media/aboutgdip02-art34.gif "AboutGdip02_Art34")</span></span>  
  
 <span data-ttu-id="88a75-121">Düzgünleştirme düzgünleştirme, olarak da bilinir, ayrıca eğrilere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="88a75-121">Antialiasing, also called smoothing, can also be applied to curves.</span></span> <span data-ttu-id="88a75-122">Aşağıdaki çizim düzleştirilmiş bir elips genişletilmiş bir görünümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="88a75-122">The following illustration shows an enlarged view of a smoothed ellipse.</span></span>  
  
 <span data-ttu-id="88a75-123">![Düzgünleştirme Eğriler](./media/aboutgdip02-art35.gif "AboutGdip02_Art35")</span><span class="sxs-lookup"><span data-stu-id="88a75-123">![Antialiasing Curves](./media/aboutgdip02-art35.gif "AboutGdip02_Art35")</span></span>  
  
 <span data-ttu-id="88a75-124">Aşağıdaki çizimde aynı elips gerçek boyutuna, düzgünleştirme olmadan bir kez ve bir kez düzgünleştirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="88a75-124">The following illustration shows the same ellipse in its actual size, once without antialiasing and once with antialiasing.</span></span>  
  
 <span data-ttu-id="88a75-125">![Düzgünleştirme örnek](./media/aboutgdip02-art36.gif "AboutGdip02_Art36")</span><span class="sxs-lookup"><span data-stu-id="88a75-125">![Antialiasing example](./media/aboutgdip02-art36.gif "AboutGdip02_Art36")</span></span>  
  
 <span data-ttu-id="88a75-126">Çizgiler ve eğrilerle düzgünleştirme kullanan çizmek için bir örneğini oluşturmak <xref:System.Drawing.Graphics> ayarlayın ve sınıf kendi <xref:System.Drawing.Graphics.SmoothingMode%2A> özelliğini <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> veya <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>.</span><span class="sxs-lookup"><span data-stu-id="88a75-126">To draw lines and curves that use antialiasing, create an instance of the <xref:System.Drawing.Graphics> class and set its <xref:System.Drawing.Graphics.SmoothingMode%2A> property to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> or <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>.</span></span> <span data-ttu-id="88a75-127">Ardından, söz konusu çizim yöntemlerden birini aynı çağrı <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="88a75-127">Then call one of the drawing methods of that same <xref:System.Drawing.Graphics> class.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#81](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## <a name="see-also"></a><span data-ttu-id="88a75-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88a75-128">See also</span></span>

- <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=nameWithType>
- [<span data-ttu-id="88a75-129">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="88a75-129">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="88a75-130">Nasıl yapılır: Metinle düzgünleştirme kullanma</span><span class="sxs-lookup"><span data-stu-id="88a75-130">How to: Use Antialiasing with Text</span></span>](how-to-use-antialiasing-with-text.md)
