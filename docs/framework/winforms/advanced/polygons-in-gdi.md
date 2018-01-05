---
title: "GDI+'daki Çokgenler"
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
- polygons
- drawing [Windows Forms], polygons
- GDI+, polygons
ms.assetid: a72213d2-d69a-4c2b-a75c-be7b20390c13
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26068ab72473a541b1f16aeb2a1f0d43ec7a7313
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="polygons-in-gdi"></a><span data-ttu-id="600a5-102">GDI+'daki Çokgenler</span><span class="sxs-lookup"><span data-stu-id="600a5-102">Polygons in GDI+</span></span>
<span data-ttu-id="600a5-103">Çokgen üç veya daha fazla düz kenarlar ile kapalı bir Şekil ' dir.</span><span class="sxs-lookup"><span data-stu-id="600a5-103">A polygon is a closed shape with three or more straight sides.</span></span> <span data-ttu-id="600a5-104">Örneğin, bir üçgen üç kenarı sahip bir çokgenin, bir Çokgen dört kenara dikdörtgen şeklinde ve beş kenara sahip bir çokgenin bir pentagon olduğu.</span><span class="sxs-lookup"><span data-stu-id="600a5-104">For example, a triangle is a polygon with three sides, a rectangle is a polygon with four sides, and a pentagon is a polygon with five sides.</span></span> <span data-ttu-id="600a5-105">Aşağıda birkaç çokgenler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="600a5-105">The following illustration shows several polygons.</span></span>  
  
 <span data-ttu-id="600a5-106">![Çokgenler](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art07.gif "Aboutgdip02_art07")</span><span class="sxs-lookup"><span data-stu-id="600a5-106">![Polygons](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art07.gif "Aboutgdip02_art07")</span></span>  
  
## <a name="drawing-a-polygon"></a><span data-ttu-id="600a5-107">Çokgen çizme</span><span class="sxs-lookup"><span data-stu-id="600a5-107">Drawing a Polygon</span></span>  
 <span data-ttu-id="600a5-108">Çokgen çizmek için size gereken bir <xref:System.Drawing.Graphics> nesne, bir <xref:System.Drawing.Pen> nesne ve bir dizi <xref:System.Drawing.Point> (veya <xref:System.Drawing.PointF>) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="600a5-108">To draw a polygon, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Pen> object, and an array of <xref:System.Drawing.Point> (or <xref:System.Drawing.PointF>) objects.</span></span> <span data-ttu-id="600a5-109"><xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.DrawPolygon%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="600a5-109">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawPolygon%2A> method.</span></span> <span data-ttu-id="600a5-110"><xref:System.Drawing.Pen> Nesne depolar genişlik ve Çokgen ve dizi oluşturmak için kullanılan çizginin rengini gibi öznitelikleri <xref:System.Drawing.Point> nesnelerini depolayan noktaları düz çizgilerle bağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="600a5-110">The <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the polygon, and the array of <xref:System.Drawing.Point> objects stores the points to be connected by straight lines.</span></span> <span data-ttu-id="600a5-111"><xref:System.Drawing.Pen> Nesne ve bir dizi <xref:System.Drawing.Point> nesneleri bağımsız değişken olarak geçirilen <xref:System.Drawing.Graphics.DrawPolygon%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="600a5-111">The <xref:System.Drawing.Pen> object and the array of <xref:System.Drawing.Point> objects are passed as arguments to the <xref:System.Drawing.Graphics.DrawPolygon%2A> method.</span></span> <span data-ttu-id="600a5-112">Aşağıdaki örnekte, üç taraflı çokgen çizer.</span><span class="sxs-lookup"><span data-stu-id="600a5-112">The following example draws a three-sided polygon.</span></span> <span data-ttu-id="600a5-113">Yalnızca üç noktaları olduğuna dikkat edin `myPointArray`: (0, 0), (50, 30) ve (30, 60).</span><span class="sxs-lookup"><span data-stu-id="600a5-113">Note that there are only three points in `myPointArray`: (0, 0), (50, 30), and (30, 60).</span></span> <span data-ttu-id="600a5-114"><xref:System.Drawing.Graphics.DrawPolygon%2A> Yöntemi otomatik olarak bir satırından çizerek Çokgen kapatır (30, 60) başlangıç noktası (0, 0) dön.</span><span class="sxs-lookup"><span data-stu-id="600a5-114">The <xref:System.Drawing.Graphics.DrawPolygon%2A> method automatically closes the polygon by drawing a line from (30, 60) back to the starting point (0, 0).</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#111](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#111)]
 [!code-vb[LinesCurvesAndShapes#111](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#111)]  
  
 <span data-ttu-id="600a5-115">Aşağıdaki çizimde Çokgen gösterir.</span><span class="sxs-lookup"><span data-stu-id="600a5-115">The following illustration shows the polygon.</span></span>  
  
 <span data-ttu-id="600a5-116">![Çokgen](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art08.gif "Aboutgdip02_art08")</span><span class="sxs-lookup"><span data-stu-id="600a5-116">![Polygon](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art08.gif "Aboutgdip02_art08")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="600a5-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="600a5-117">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [<span data-ttu-id="600a5-118">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="600a5-118">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="600a5-119">Nasıl yapılır: Kalem Oluşturma</span><span class="sxs-lookup"><span data-stu-id="600a5-119">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
