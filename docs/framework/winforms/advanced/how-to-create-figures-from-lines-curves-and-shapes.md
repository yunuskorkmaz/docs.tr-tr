---
title: "Nasıl yapılır: Çizgiler, Eğriler ve Şekillerden Şekiller Oluşturma"
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
- figures [Windows Forms], creating from shapes
- figures [Windows Forms], creating from lines
ms.assetid: 82fd56c7-b443-4765-9b7c-62ce030656ec
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 40520f566beafc83075d0563148b5d0f9bd4fe85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-figures-from-lines-curves-and-shapes"></a><span data-ttu-id="53018-102">Nasıl yapılır: Çizgiler, Eğriler ve Şekillerden Şekiller Oluşturma</span><span class="sxs-lookup"><span data-stu-id="53018-102">How to: Create Figures from Lines, Curves, and Shapes</span></span>
<span data-ttu-id="53018-103">Bir şekil oluşturmak için oluşturmak bir <xref:System.Drawing.Drawing2D.GraphicsPath>ve yöntemleri gibi çağrısı <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> ve <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>, ilkel yolunu eklemek için.</span><span class="sxs-lookup"><span data-stu-id="53018-103">To create a figure, construct a <xref:System.Drawing.Drawing2D.GraphicsPath>, and then call methods, such as <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>, to add primitives to the path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53018-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="53018-104">Example</span></span>  
 <span data-ttu-id="53018-105">Aşağıdaki kod örnekleri rakamları sahip yolları oluşturun:</span><span class="sxs-lookup"><span data-stu-id="53018-105">The following code examples create paths that have figures:</span></span>  
  
-   <span data-ttu-id="53018-106">İlk örnek tek bir şekil sahip bir yol oluşturur.</span><span class="sxs-lookup"><span data-stu-id="53018-106">The first example creates a path that has a single figure.</span></span> <span data-ttu-id="53018-107">Şekil, tek bir yay oluşur. Yayı varsayılan koordinat sistemi saatin tarama açısı – 180 derece vardır.</span><span class="sxs-lookup"><span data-stu-id="53018-107">The figure consists of a single arc. The arc has a sweep angle of –180 degrees, which is counterclockwise in the default coordinate system.</span></span>  
  
-   <span data-ttu-id="53018-108">İkinci örnekte iki şekilde sahip bir yol oluşturur.</span><span class="sxs-lookup"><span data-stu-id="53018-108">The second example creates a path that has two figures.</span></span> <span data-ttu-id="53018-109">İlk satırı tarafından izlenen bir yay sayıdır.</span><span class="sxs-lookup"><span data-stu-id="53018-109">The first figure is an arc followed by a line.</span></span> <span data-ttu-id="53018-110">İkinci şekil satırı tarafından izlenen bir eğri arkasından bir satırdır.</span><span class="sxs-lookup"><span data-stu-id="53018-110">The second figure is a line followed by a curve followed by a line.</span></span> <span data-ttu-id="53018-111">İlk şekil açık kalır ve ikinci şekil kapalı.</span><span class="sxs-lookup"><span data-stu-id="53018-111">The first figure is left open, and the second figure is closed.</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#21)]  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#22)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="53018-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="53018-112">Compiling the Code</span></span>  
 <span data-ttu-id="53018-113">Önceki örneklerde Windows Forms ile kullanılmak üzere tasarlanmıştır ve ihtiyaç <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="53018-113">The previous examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53018-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="53018-114">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 [<span data-ttu-id="53018-115">Yollar Oluşturma ve Çizme</span><span class="sxs-lookup"><span data-stu-id="53018-115">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)  
 [<span data-ttu-id="53018-116">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="53018-116">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
