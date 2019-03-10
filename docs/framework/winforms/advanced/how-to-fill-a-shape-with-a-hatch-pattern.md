---
title: 'Nasıl yapılır: Bir şekli tarama deseniyle doldurma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
ms.openlocfilehash: 885f0d22e83767bda3ef76c54f0857dd2a148344
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719721"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a><span data-ttu-id="f88ba-102">Nasıl yapılır: Bir şekli tarama deseniyle doldurma</span><span class="sxs-lookup"><span data-stu-id="f88ba-102">How to: Fill a Shape with a Hatch Pattern</span></span>
<span data-ttu-id="f88ba-103">Tarama deseniyle iki renkleri yapılır: arka plan ve arka plan üzerinde deseni oluşturan satırlar için.</span><span class="sxs-lookup"><span data-stu-id="f88ba-103">A hatch pattern is made from two colors: one for the background and one for the lines that form the pattern over the background.</span></span> <span data-ttu-id="f88ba-104">Kapalı bir şekli tarama deseniyle ile doldurmak için kullanmak bir <xref:System.Drawing.Drawing2D.HatchBrush> nesne.</span><span class="sxs-lookup"><span data-stu-id="f88ba-104">To fill a closed shape with a hatch pattern, use a <xref:System.Drawing.Drawing2D.HatchBrush> object.</span></span> <span data-ttu-id="f88ba-105">Aşağıdaki örnek, bir tarama deseniyle elips doldurmak gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="f88ba-105">The following example demonstrates how to fill an ellipse with a hatch pattern:</span></span>  
  
## <a name="example"></a><span data-ttu-id="f88ba-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="f88ba-106">Example</span></span>  
 <span data-ttu-id="f88ba-107"><xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> Oluşturucusu üç bağımsız değişken alır: Tarama stilini, tarama çizginin rengini ve arka plan rengi.</span><span class="sxs-lookup"><span data-stu-id="f88ba-107">The <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> constructor takes three arguments: the hatch style, the color of the hatch line, and the color of the background.</span></span> <span data-ttu-id="f88ba-108">Tarama stili bağımsız değişken, herhangi bir değer olabilir <xref:System.Drawing.Drawing2D.HatchStyle> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="f88ba-108">The hatch style argument can be any value from the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration.</span></span> <span data-ttu-id="f88ba-109">Elli'den fazla öğe içinde <xref:System.Drawing.Drawing2D.HatchStyle> numaralandırma; bunlardan birkaçını öğeler, aşağıdaki listede gösterilir:</span><span class="sxs-lookup"><span data-stu-id="f88ba-109">There are more than fifty elements in the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration; a few of those elements are shown in the following list:</span></span>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 <span data-ttu-id="f88ba-110">Dolu Elips aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f88ba-110">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="f88ba-111">![Tarama desen](./media/hatch1.png "hatch1")</span><span class="sxs-lookup"><span data-stu-id="f88ba-111">![Hatch Pattern](./media/hatch1.png "hatch1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f88ba-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f88ba-112">Compiling the Code</span></span>  
 <span data-ttu-id="f88ba-113">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="f88ba-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f88ba-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f88ba-114">See also</span></span>
- [<span data-ttu-id="f88ba-115">Şekilleri Doldurmak için Fırça Kullanma</span><span class="sxs-lookup"><span data-stu-id="f88ba-115">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
