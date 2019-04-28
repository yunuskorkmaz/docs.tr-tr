---
title: GDI+'daki Çokgenler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- polygons
- drawing [Windows Forms], polygons
- GDI+, polygons
ms.assetid: a72213d2-d69a-4c2b-a75c-be7b20390c13
ms.openlocfilehash: 2b1e3d387e4d056d9187c54dcef560544206c370
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641313"
---
# <a name="polygons-in-gdi"></a><span data-ttu-id="610fe-102">GDI+'daki Çokgenler</span><span class="sxs-lookup"><span data-stu-id="610fe-102">Polygons in GDI+</span></span>
<span data-ttu-id="610fe-103">Bir çokgenin üç veya daha fazla düz kenarlar ile kapalı şekildir.</span><span class="sxs-lookup"><span data-stu-id="610fe-103">A polygon is a closed shape with three or more straight sides.</span></span> <span data-ttu-id="610fe-104">Örneğin, üç kenarı sahip bir çokgenin bir üçgen olan dört tarafında sahip bir çokgenin dikdörtgen şeklinde ve beş yüz sahip bir çokgenin bir Beşgene olduğu.</span><span class="sxs-lookup"><span data-stu-id="610fe-104">For example, a triangle is a polygon with three sides, a rectangle is a polygon with four sides, and a pentagon is a polygon with five sides.</span></span> <span data-ttu-id="610fe-105">Aşağıdaki resimde, birkaç çokgenler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="610fe-105">The following illustration shows several polygons.</span></span>  
  
 <span data-ttu-id="610fe-106">![Polygons](./media/aboutgdip02-art07.gif "Aboutgdip02_art07")</span><span class="sxs-lookup"><span data-stu-id="610fe-106">![Polygons](./media/aboutgdip02-art07.gif "Aboutgdip02_art07")</span></span>  
  
## <a name="drawing-a-polygon"></a><span data-ttu-id="610fe-107">Bir çokgenin çizme</span><span class="sxs-lookup"><span data-stu-id="610fe-107">Drawing a Polygon</span></span>  
 <span data-ttu-id="610fe-108">Bir çokgenin çizmek için ihtiyacınız bir <xref:System.Drawing.Graphics> nesnesi bir <xref:System.Drawing.Pen> nesnesi ve bir dizi <xref:System.Drawing.Point> (veya <xref:System.Drawing.PointF>) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="610fe-108">To draw a polygon, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Pen> object, and an array of <xref:System.Drawing.Point> (or <xref:System.Drawing.PointF>) objects.</span></span> <span data-ttu-id="610fe-109"><xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.DrawPolygon%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="610fe-109">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawPolygon%2A> method.</span></span> <span data-ttu-id="610fe-110"><xref:System.Drawing.Pen> Nesnesini depolar genişlik ve Çokgen ve dizi oluşturmak için kullanılan çizginin rengi gibi öznitelikleri <xref:System.Drawing.Point> nesneleri tarafından düz çizgiler bağlanması noktalarını depolar.</span><span class="sxs-lookup"><span data-stu-id="610fe-110">The <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the polygon, and the array of <xref:System.Drawing.Point> objects stores the points to be connected by straight lines.</span></span> <span data-ttu-id="610fe-111"><xref:System.Drawing.Pen> Nesne ve dizi <xref:System.Drawing.Point> nesneleri bağımsız değişkenleri olarak geçirilir <xref:System.Drawing.Graphics.DrawPolygon%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="610fe-111">The <xref:System.Drawing.Pen> object and the array of <xref:System.Drawing.Point> objects are passed as arguments to the <xref:System.Drawing.Graphics.DrawPolygon%2A> method.</span></span> <span data-ttu-id="610fe-112">Aşağıdaki örnek, üç taraflı bir çokgen çizer.</span><span class="sxs-lookup"><span data-stu-id="610fe-112">The following example draws a three-sided polygon.</span></span> <span data-ttu-id="610fe-113">Yalnızca üç noktalar olduğunu unutmayın `myPointArray`: (0, 0), (50, 30) ve (30, 60).</span><span class="sxs-lookup"><span data-stu-id="610fe-113">Note that there are only three points in `myPointArray`: (0, 0), (50, 30), and (30, 60).</span></span> <span data-ttu-id="610fe-114"><xref:System.Drawing.Graphics.DrawPolygon%2A> Yöntemi otomatik olarak bir çizgi çizerek Çokgen kapatır (30, 60) tekrar için başlangıç noktası (0, 0).</span><span class="sxs-lookup"><span data-stu-id="610fe-114">The <xref:System.Drawing.Graphics.DrawPolygon%2A> method automatically closes the polygon by drawing a line from (30, 60) back to the starting point (0, 0).</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#111](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#111)]
 [!code-vb[LinesCurvesAndShapes#111](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#111)]  
  
 <span data-ttu-id="610fe-115">Çokgen aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="610fe-115">The following illustration shows the polygon.</span></span>  
  
 <span data-ttu-id="610fe-116">![Polygon](./media/aboutgdip02-art08.gif "Aboutgdip02_art08")</span><span class="sxs-lookup"><span data-stu-id="610fe-116">![Polygon](./media/aboutgdip02-art08.gif "Aboutgdip02_art08")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="610fe-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="610fe-117">See also</span></span>

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [<span data-ttu-id="610fe-118">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="610fe-118">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="610fe-119">Nasıl yapılır: Kalem oluşturma</span><span class="sxs-lookup"><span data-stu-id="610fe-119">How to: Create a Pen</span></span>](how-to-create-a-pen.md)
