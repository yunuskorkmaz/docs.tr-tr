---
title: 'Nasıl yapılır: Bir Şekli Tarama Deseniyle Doldurma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
ms.openlocfilehash: b80708f0ce722b1809fe49190639231e7e4c8329
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320066"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a><span data-ttu-id="124eb-102">Nasıl yapılır: Bir Şekli Tarama Deseniyle Doldurma</span><span class="sxs-lookup"><span data-stu-id="124eb-102">How to: Fill a Shape with a Hatch Pattern</span></span>
<span data-ttu-id="124eb-103">İki renkten bir tarama kalıbı yapılır: biri arka plan ve diğeri arka plan üzerinde model oluşturan satırlar için.</span><span class="sxs-lookup"><span data-stu-id="124eb-103">A hatch pattern is made from two colors: one for the background and one for the lines that form the pattern over the background.</span></span> <span data-ttu-id="124eb-104">Kapalı bir şekli tarama düzeniyle doldurmanız için <xref:System.Drawing.Drawing2D.HatchBrush> nesnesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="124eb-104">To fill a closed shape with a hatch pattern, use a <xref:System.Drawing.Drawing2D.HatchBrush> object.</span></span> <span data-ttu-id="124eb-105">Aşağıdaki örnek, bir elipsin bir tarama düzeniyle nasıl doldurulacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="124eb-105">The following example demonstrates how to fill an ellipse with a hatch pattern:</span></span>  
  
## <a name="example"></a><span data-ttu-id="124eb-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="124eb-106">Example</span></span>  
 <span data-ttu-id="124eb-107"><xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> Oluşturucu üç bağımsız değişken alır: tarama stili, tarama çizgisinin rengi ve arka plan rengi.</span><span class="sxs-lookup"><span data-stu-id="124eb-107">The <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> constructor takes three arguments: the hatch style, the color of the hatch line, and the color of the background.</span></span> <span data-ttu-id="124eb-108">Tarama stili bağımsız değişkeni <xref:System.Drawing.Drawing2D.HatchStyle> numaralandırmasından herhangi bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="124eb-108">The hatch style argument can be any value from the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration.</span></span> <span data-ttu-id="124eb-109"><xref:System.Drawing.Drawing2D.HatchStyle> numaralandırmasında 50 taneden fazla öğe var; Bu öğelerin bazıları aşağıdaki listede gösteriliyor:</span><span class="sxs-lookup"><span data-stu-id="124eb-109">There are more than fifty elements in the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration; a few of those elements are shown in the following list:</span></span>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 <span data-ttu-id="124eb-110">Aşağıdaki çizimde doldurulmuş elips gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="124eb-110">The following illustration shows the filled ellipse.</span></span>  
  
  <span data-ttu-id="124eb-111">![Bir tarama deseninin doldurulduğu bir elips ekran görüntüsü.](./media/how-to-fill-a-shape-with-a-hatch-pattern/ellipse-filled-hatch.png "hatch1")</span><span class="sxs-lookup"><span data-stu-id="124eb-111">![Screenshot of what an ellipse filled with a hatch pattern looks like.](./media/how-to-fill-a-shape-with-a-hatch-pattern/ellipse-filled-hatch.png "hatch1")</span></span>
  
 [!code-csharp[System.Drawing.UsingABrush#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="124eb-112">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="124eb-112">Compiling the Code</span></span>  
 <span data-ttu-id="124eb-113">Yukarıdaki örnek, Windows Forms kullanımı için tasarlanmıştır ve <xref:System.Windows.Forms.Control.Paint> olay işleyicisinin bir parametresi olan <xref:System.Windows.Forms.PaintEventArgs>`e`gerektirir.</span><span class="sxs-lookup"><span data-stu-id="124eb-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="124eb-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="124eb-114">See also</span></span>

- [<span data-ttu-id="124eb-115">Şekilleri Doldurmak için Fırça Kullanma</span><span class="sxs-lookup"><span data-stu-id="124eb-115">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
