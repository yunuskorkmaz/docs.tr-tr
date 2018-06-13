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
ms.openlocfilehash: 5b6b5b61b83e5be05999099f2cc6b9e715ca35c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521748"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a><span data-ttu-id="86f7b-102">Nasıl yapılır: Bir Şekli Tarama Deseniyle Doldurma</span><span class="sxs-lookup"><span data-stu-id="86f7b-102">How to: Fill a Shape with a Hatch Pattern</span></span>
<span data-ttu-id="86f7b-103">Tarama deseniyle iki renkten yapılır: arka plan, diğeri desen arka plan üzerinde form satırlar için için.</span><span class="sxs-lookup"><span data-stu-id="86f7b-103">A hatch pattern is made from two colors: one for the background and one for the lines that form the pattern over the background.</span></span> <span data-ttu-id="86f7b-104">Kapalı bir şekli tarama deseniyle ile doldurmak için kullanın bir <xref:System.Drawing.Drawing2D.HatchBrush> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="86f7b-104">To fill a closed shape with a hatch pattern, use a <xref:System.Drawing.Drawing2D.HatchBrush> object.</span></span> <span data-ttu-id="86f7b-105">Aşağıdaki örnek, bir elips ile tarama deseniyle doldurma gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="86f7b-105">The following example demonstrates how to fill an ellipse with a hatch pattern:</span></span>  
  
## <a name="example"></a><span data-ttu-id="86f7b-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="86f7b-106">Example</span></span>  
 <span data-ttu-id="86f7b-107"><xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> Oluşturucusu üç bağımsız değişkeni alır: Tarama stilini, tarama çizginin rengini ve arka plan rengi.</span><span class="sxs-lookup"><span data-stu-id="86f7b-107">The <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> constructor takes three arguments: the hatch style, the color of the hatch line, and the color of the background.</span></span> <span data-ttu-id="86f7b-108">Tarama stili bağımsız değişken arasında bir değer olabilir <xref:System.Drawing.Drawing2D.HatchStyle> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="86f7b-108">The hatch style argument can be any value from the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration.</span></span> <span data-ttu-id="86f7b-109">İçinde birden fazla elli öğe <xref:System.Drawing.Drawing2D.HatchStyle> numaralandırma; bu birkaç öğeleri aşağıdaki listede gösterilir:</span><span class="sxs-lookup"><span data-stu-id="86f7b-109">There are more than fifty elements in the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration; a few of those elements are shown in the following list:</span></span>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 <span data-ttu-id="86f7b-110">Aşağıdaki çizimde doldurulmuş elips gösterir.</span><span class="sxs-lookup"><span data-stu-id="86f7b-110">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="86f7b-111">![Tarama deseni](../../../../docs/framework/winforms/advanced/media/hatch1.png "hatch1")</span><span class="sxs-lookup"><span data-stu-id="86f7b-111">![Hatch Pattern](../../../../docs/framework/winforms/advanced/media/hatch1.png "hatch1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="86f7b-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="86f7b-112">Compiling the Code</span></span>  
 <span data-ttu-id="86f7b-113">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="86f7b-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86f7b-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86f7b-114">See Also</span></span>  
 [<span data-ttu-id="86f7b-115">Şekilleri Doldurmak için Fırça Kullanma</span><span class="sxs-lookup"><span data-stu-id="86f7b-115">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
