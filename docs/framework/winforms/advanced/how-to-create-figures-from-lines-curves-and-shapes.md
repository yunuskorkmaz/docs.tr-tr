---
title: 'Nasıl yapılır: Çizgiler, Eğriler ve Şekillerden Şekiller Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- figures [Windows Forms], creating from shapes
- figures [Windows Forms], creating from lines
ms.assetid: 82fd56c7-b443-4765-9b7c-62ce030656ec
ms.openlocfilehash: eeaf478375e08734b20d83b6f3c8030732495013
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937702"
---
# <a name="how-to-create-figures-from-lines-curves-and-shapes"></a><span data-ttu-id="ad624-102">Nasıl yapılır: Çizgiler, Eğriler ve Şekillerden Şekiller Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ad624-102">How to: Create Figures from Lines, Curves, and Shapes</span></span>
<span data-ttu-id="ad624-103">Bir şekil oluşturmak için oluşturmak bir <xref:System.Drawing.Drawing2D.GraphicsPath>ve ardından yöntemleri çağırmak <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> ve <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>, ilkel yola ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ad624-103">To create a figure, construct a <xref:System.Drawing.Drawing2D.GraphicsPath>, and then call methods, such as <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>, to add primitives to the path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad624-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ad624-104">Example</span></span>  
 <span data-ttu-id="ad624-105">Aşağıdaki kod örnekleri olan şekil yolları oluşturun:</span><span class="sxs-lookup"><span data-stu-id="ad624-105">The following code examples create paths that have figures:</span></span>  
  
- <span data-ttu-id="ad624-106">İlk örnek, tek bir şekil sahip bir yol oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ad624-106">The first example creates a path that has a single figure.</span></span> <span data-ttu-id="ad624-107">Şekilde tek bir yay içerir. Yayı varsayılan koordinat sisteminde saatin bir tarama açısı – 180 derece vardır.</span><span class="sxs-lookup"><span data-stu-id="ad624-107">The figure consists of a single arc. The arc has a sweep angle of –180 degrees, which is counterclockwise in the default coordinate system.</span></span>  
  
- <span data-ttu-id="ad624-108">İkinci örnek, iki şekil sahip bir yol oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ad624-108">The second example creates a path that has two figures.</span></span> <span data-ttu-id="ad624-109">İlk satır tarafından izlenen bir yay sayıdır.</span><span class="sxs-lookup"><span data-stu-id="ad624-109">The first figure is an arc followed by a line.</span></span> <span data-ttu-id="ad624-110">İkinci şekil, bir satır tarafından izlenen bir eğri arkasından bir satırdır.</span><span class="sxs-lookup"><span data-stu-id="ad624-110">The second figure is a line followed by a curve followed by a line.</span></span> <span data-ttu-id="ad624-111">İlk şekil açık kalır ve ikinci şekil kapalı.</span><span class="sxs-lookup"><span data-stu-id="ad624-111">The first figure is left open, and the second figure is closed.</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#21)]  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#22)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ad624-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ad624-112">Compiling the Code</span></span>  
 <span data-ttu-id="ad624-113">Önceki örneklerde, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirdikleri <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="ad624-113">The previous examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad624-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad624-114">See also</span></span>

- <xref:System.Drawing.Drawing2D.GraphicsPath>
- [<span data-ttu-id="ad624-115">Yollar Oluşturma ve Çizme</span><span class="sxs-lookup"><span data-stu-id="ad624-115">Constructing and Drawing Paths</span></span>](constructing-and-drawing-paths.md)
- [<span data-ttu-id="ad624-116">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="ad624-116">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
