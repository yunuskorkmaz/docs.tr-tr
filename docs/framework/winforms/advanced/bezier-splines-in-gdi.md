---
title: B&#233;zier GDI +'daki eğrileri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines
- splines [Windows Forms], Bezier
- GDI+, Bezier splines
ms.assetid: 5774ce1e-87d4-4bc7-88c4-4862052781b8
ms.openlocfilehash: 440c532aeb4492711fc533023606cb49c661d989
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537621"
---
# <a name="b233zier-splines-in-gdi"></a><span data-ttu-id="42c74-102">B&#233;zier GDI +'daki eğrileri</span><span class="sxs-lookup"><span data-stu-id="42c74-102">B&#233;zier Splines in GDI+</span></span>
<span data-ttu-id="42c74-103">Dört noktası tarafından belirtilen eğri Bézier eğri olduğu: iki uç noktaları (p1 ve p2) ve iki denetim noktaları (c1 ve c2).</span><span class="sxs-lookup"><span data-stu-id="42c74-103">A Bézier spline is a curve specified by four points: two end points (p1 and p2) and two control points (c1 and c2).</span></span> <span data-ttu-id="42c74-104">Eğriyi, başlar p1 ve p2 sona erer.</span><span class="sxs-lookup"><span data-stu-id="42c74-104">The curve begins at p1 and ends at p2.</span></span> <span data-ttu-id="42c74-105">Eğri denetim noktaları üzerinden geçmez, ancak denetim noktaları belirli yönde eğri çekmek ve bends eğrinin şeklini etkileyen mıknatıs davranır.</span><span class="sxs-lookup"><span data-stu-id="42c74-105">The curve does not pass through the control points, but the control points act as magnets, pulling the curve in certain directions and influencing the way the curve bends.</span></span> <span data-ttu-id="42c74-106">Bézier eğri denetim noktalarını ve uç noktaları ile birlikte aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="42c74-106">The following illustration shows a Bézier curve along with its endpoints and control points.</span></span>  
  
 <span data-ttu-id="42c74-107">![Bezier Splines](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")</span><span class="sxs-lookup"><span data-stu-id="42c74-107">![Bezier Splines](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")</span></span>  
  
 <span data-ttu-id="42c74-108">Eğriyi, p1 başlatır ve kontrol noktası c1 doğru taşır.</span><span class="sxs-lookup"><span data-stu-id="42c74-108">The curve starts at p1 and moves toward the control point c1.</span></span> <span data-ttu-id="42c74-109">Eğim satırına kıvrımın p1, p1 c1 için çizgi ' dir.</span><span class="sxs-lookup"><span data-stu-id="42c74-109">The tangent line to the curve at p1 is the line drawn from p1 to c1.</span></span> <span data-ttu-id="42c74-110">Uç nokta p2 Eğim satırında c2 p2 için çizgi ' dir.</span><span class="sxs-lookup"><span data-stu-id="42c74-110">The tangent line at the endpoint p2 is the line drawn from c2 to p2.</span></span>  
  
## <a name="drawing-bzier-splines"></a><span data-ttu-id="42c74-111">Çizim Bézier eğrileri</span><span class="sxs-lookup"><span data-stu-id="42c74-111">Drawing Bézier Splines</span></span>  
 <span data-ttu-id="42c74-112">Örneği ihtiyacınız Bézier eğri çizmek için <xref:System.Drawing.Graphics> sınıfı ve <xref:System.Drawing.Pen>.</span><span class="sxs-lookup"><span data-stu-id="42c74-112">To draw a Bézier spline, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Pen>.</span></span> <span data-ttu-id="42c74-113">Örneğini <xref:System.Drawing.Graphics> sağlar sınıfını <xref:System.Drawing.Graphics.DrawBezier%2A> yöntemi ve <xref:System.Drawing.Pen> genişlik ve eğri işlemek için kullanılan çizginin rengi gibi özniteliklerini depolar.</span><span class="sxs-lookup"><span data-stu-id="42c74-113">The instance of the <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.DrawBezier%2A> method, and the <xref:System.Drawing.Pen> stores attributes, such as width and color, of the line used to render the curve.</span></span> <span data-ttu-id="42c74-114"><xref:System.Drawing.Pen> Bir bağımsız değişken olarak geçirilen <xref:System.Drawing.Graphics.DrawBezier%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="42c74-114">The <xref:System.Drawing.Pen> is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawBezier%2A> method.</span></span> <span data-ttu-id="42c74-115">Kalan bağımsız değişkenleri geçirilen <xref:System.Drawing.Graphics.DrawBezier%2A> yöntemi olan uç noktaları ve denetim noktaları.</span><span class="sxs-lookup"><span data-stu-id="42c74-115">The remaining arguments passed to the <xref:System.Drawing.Graphics.DrawBezier%2A> method are the endpoints and the control points.</span></span> <span data-ttu-id="42c74-116">Aşağıdaki örnek, başlangıç noktası (0, 0) ile bir Bézier eğrisi çizer kontrol noktaları (40, 20) ve (80, 150) ve bitiş noktası (100, 10):</span><span class="sxs-lookup"><span data-stu-id="42c74-116">The following example draws a Bézier spline with starting point (0, 0), control points (40, 20) and (80, 150), and ending point (100, 10):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 <span data-ttu-id="42c74-117">Eğri denetim noktalarını ve Eğim satırlarını aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="42c74-117">The following illustration shows the curve, the control points, and two tangent lines.</span></span>  
  
 <span data-ttu-id="42c74-118">![Bezier Splines](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art12.gif "Aboutgdip02_art12")</span><span class="sxs-lookup"><span data-stu-id="42c74-118">![Bezier Splines](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art12.gif "Aboutgdip02_art12")</span></span>  
  
 <span data-ttu-id="42c74-119">Bézier eğrileri Pierre Bézier tarafından otomotiv sektöründe tasarımı için ilk olarak geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="42c74-119">Bézier splines were originally developed by Pierre Bézier for design in the automotive industry.</span></span> <span data-ttu-id="42c74-120">Bunlar, bilgisayar destekli tasarım birçok türde kullanışlı olması için beri kanıtlanmış ve yazı tipleri anahatlarını tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="42c74-120">They have since proven to be useful in many types of computer-aided design and are also used to define the outlines of fonts.</span></span> <span data-ttu-id="42c74-121">Şekiller, bazıları aşağıda gösterilen çeşitli Bézier eğrileri sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="42c74-121">Bézier splines can yield a wide variety of shapes, some of which are shown in the following illustration.</span></span>  
  
 <span data-ttu-id="42c74-122">![Paths](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art13.gif "Aboutgdip02_art13")</span><span class="sxs-lookup"><span data-stu-id="42c74-122">![Paths](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art13.gif "Aboutgdip02_art13")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42c74-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42c74-123">See also</span></span>
- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [<span data-ttu-id="42c74-124">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="42c74-124">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [<span data-ttu-id="42c74-125">Eğriler Oluşturma ve Çizme</span><span class="sxs-lookup"><span data-stu-id="42c74-125">Constructing and Drawing Curves</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
- [<span data-ttu-id="42c74-126">Nasıl yapılır: Çizim için grafik nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="42c74-126">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="42c74-127">Nasıl yapılır: Kalem oluşturma</span><span class="sxs-lookup"><span data-stu-id="42c74-127">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
