---
title: GDI+'da Elipsler ve Yaylar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- arcs
- GDI+, arcs
- drawing [Windows Forms], ellipses
- GDI+, ellipses
- ellipses
- drawing [Windows Forms], arcs
ms.assetid: 34f35133-a835-4ca4-81f6-0dfedee8b683
ms.openlocfilehash: 6835127d03f984bda8a95cf5b9ca9798122de804
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522115"
---
# <a name="ellipses-and-arcs-in-gdi"></a><span data-ttu-id="f543f-102">GDI+'da Elipsler ve Yaylar</span><span class="sxs-lookup"><span data-stu-id="f543f-102">Ellipses and Arcs in GDI+</span></span>
<span data-ttu-id="f543f-103">Elipsler ve yaylar kullanarak kolayca çizebilirsiniz <xref:System.Drawing.Graphics.DrawEllipse%2A> ve <xref:System.Drawing.Graphics.DrawArc%2A> yöntemlerinin <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f543f-103">You can easily draw ellipses and arcs using the <xref:System.Drawing.Graphics.DrawEllipse%2A> and <xref:System.Drawing.Graphics.DrawArc%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="drawing-an-ellipse"></a><span data-ttu-id="f543f-104">Elips çizme</span><span class="sxs-lookup"><span data-stu-id="f543f-104">Drawing an Ellipse</span></span>  
 <span data-ttu-id="f543f-105">Elips çizmek için size gereken bir <xref:System.Drawing.Graphics> nesne ve <xref:System.Drawing.Pen> nesne.</span><span class="sxs-lookup"><span data-stu-id="f543f-105">To draw an ellipse, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="f543f-106"><xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.DrawEllipse%2A> yöntemi ve <xref:System.Drawing.Pen> nesnesi genişlik ve üç nokta işlemek için kullanılan çizginin rengini gibi özniteliklerini depolar.</span><span class="sxs-lookup"><span data-stu-id="f543f-106">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawEllipse%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the ellipse.</span></span> <span data-ttu-id="f543f-107"><xref:System.Drawing.Pen> Nesne bağımsız değişkenlerinden biri olarak geçirilir <xref:System.Drawing.Graphics.DrawEllipse%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f543f-107">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="f543f-108">Kalan bağımsız değişkenleri geçirilen <xref:System.Drawing.Graphics.DrawEllipse%2A> yöntemi elips için sınırlayıcı dikdörtgenini belirtin.</span><span class="sxs-lookup"><span data-stu-id="f543f-108">The remaining arguments passed to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method specify the bounding rectangle for the ellipse.</span></span> <span data-ttu-id="f543f-109">Elips sınırlayıcı dikdörtgenini birlikte aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f543f-109">The following illustration shows an ellipse along with its bounding rectangle.</span></span>  
  
 <span data-ttu-id="f543f-110">![Elipsler ve yaylar](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")</span><span class="sxs-lookup"><span data-stu-id="f543f-110">![Ellipses and arcs](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")</span></span>  
  
 <span data-ttu-id="f543f-111">Aşağıdaki örnekte bir elips çizer; 80, 40 yüksekliğini ve sol üst köşesindeki genişliğini sınırlayıcı dikdörtgenini sahiptir (100, 50):</span><span class="sxs-lookup"><span data-stu-id="f543f-111">The following example draws an ellipse; the bounding rectangle has a width of 80, a height of 40, and an upper-left corner of (100, 50):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <span data-ttu-id="f543f-112"><xref:System.Drawing.Graphics.DrawEllipse%2A> Aşırı yüklenmiş bir yöntemi <xref:System.Drawing.Graphics> sağladığınız, bağımsız değişkenlerle çeşitli yollardan olduklarından sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f543f-112"><xref:System.Drawing.Graphics.DrawEllipse%2A> is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="f543f-113">Örneğin, oluşturabileceğiniz bir <xref:System.Drawing.Rectangle> ve geçirin <xref:System.Drawing.Rectangle> için <xref:System.Drawing.Graphics.DrawEllipse%2A> yöntemi bağımsız değişken olarak:</span><span class="sxs-lookup"><span data-stu-id="f543f-113">For example, you can construct a <xref:System.Drawing.Rectangle> and pass the <xref:System.Drawing.Rectangle> to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method as an argument:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#52](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## <a name="drawing-an-arc"></a><span data-ttu-id="f543f-114">Yay çizme</span><span class="sxs-lookup"><span data-stu-id="f543f-114">Drawing an Arc</span></span>  
 <span data-ttu-id="f543f-115">Yayı elips bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="f543f-115">An arc is a portion of an ellipse.</span></span> <span data-ttu-id="f543f-116">Yay çizmek için arama <xref:System.Drawing.Graphics.DrawArc%2A> yöntemi <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f543f-116">To draw an arc, you call the <xref:System.Drawing.Graphics.DrawArc%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="f543f-117">Parametreleri <xref:System.Drawing.Graphics.DrawArc%2A> yöntemi aynıdır parametrelerinin <xref:System.Drawing.Graphics.DrawEllipse%2A> hariç yöntemi <xref:System.Drawing.Graphics.DrawArc%2A> Başlangıç açısı ve tarama açısı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f543f-117">The parameters of the <xref:System.Drawing.Graphics.DrawArc%2A> method are the same as the parameters of the <xref:System.Drawing.Graphics.DrawEllipse%2A> method, except that <xref:System.Drawing.Graphics.DrawArc%2A> requires a starting angle and sweep angle.</span></span> <span data-ttu-id="f543f-118">Aşağıdaki örnekte bir yay 30 derece Başlangıç açısı ve tarama açısı 180 derece çizilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f543f-118">The following example draws an arc with a starting angle of 30 degrees and a sweep angle of 180 degrees:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#53](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 <span data-ttu-id="f543f-119">Aşağıdaki çizimde, arc, üç nokta ve sınırlayıcı dikdörtgenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f543f-119">The following illustration shows the arc, the ellipse, and the bounding rectangle.</span></span>  
  
 <span data-ttu-id="f543f-120">![Elipsler ve yaylar](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.gif "Aboutgdip02_art06")</span><span class="sxs-lookup"><span data-stu-id="f543f-120">![Ellipses and arcs](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.gif "Aboutgdip02_art06")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f543f-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f543f-121">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [<span data-ttu-id="f543f-122">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="f543f-122">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="f543f-123">Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f543f-123">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="f543f-124">Nasıl yapılır: Kalem Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f543f-124">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [<span data-ttu-id="f543f-125">Nasıl yapılır: Ana Hatlı Şekil Çizme</span><span class="sxs-lookup"><span data-stu-id="f543f-125">How to: Draw an Outlined Shape</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)
