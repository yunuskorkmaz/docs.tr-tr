---
title: 'Nasıl yapılır: Açık Şekilleri Doldurma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
ms.openlocfilehash: 6ecea7d3edb0c3e25fb4e69ff12b88019e530021
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506079"
---
# <a name="how-to-fill-open-figures"></a><span data-ttu-id="1b0aa-102">Nasıl yapılır: Açık Şekilleri Doldurma</span><span class="sxs-lookup"><span data-stu-id="1b0aa-102">How to: Fill Open Figures</span></span>
<span data-ttu-id="1b0aa-103">Geçirerek bir yol doldurmak için bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesnesini <xref:System.Drawing.Graphics.FillPath%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1b0aa-103">You can fill a path by passing a <xref:System.Drawing.Drawing2D.GraphicsPath> object to the <xref:System.Drawing.Graphics.FillPath%2A> method.</span></span> <span data-ttu-id="1b0aa-104"><xref:System.Drawing.Graphics.FillPath%2A> Yöntemi doldurur yolun dolgu mod (diğer veya sargı) göre şu anda yolunu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1b0aa-104">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the fill mode (alternate or winding) currently set for the path.</span></span> <span data-ttu-id="1b0aa-105">Yolun herhangi bir açık şekilleri varsa, bu değerleri gibi kapalıyken yolu doldurulur.</span><span class="sxs-lookup"><span data-stu-id="1b0aa-105">If the path has any open figures, the path is filled as if those figures were closed.</span></span> <span data-ttu-id="1b0aa-106">GDI +'da bir şekil için başlangıç noktası, bitiş noktasından düz bir çizgi çizerek kapatır.</span><span class="sxs-lookup"><span data-stu-id="1b0aa-106">GDI+ closes a figure by drawing a straight line from its ending point to its starting point.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b0aa-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="1b0aa-107">Example</span></span>  
 <span data-ttu-id="1b0aa-108">Aşağıdaki örnek, bir açık şekil (yay) ve bir kapalı şekle (bir elips) sahip bir yol oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1b0aa-108">The following example creates a path that has one open figure (an arc) and one closed figure (an ellipse).</span></span> <span data-ttu-id="1b0aa-109"><xref:System.Drawing.Graphics.FillPath%2A> Yöntemi olan varsayılan dolgu modda göre yolu doldurur <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span><span class="sxs-lookup"><span data-stu-id="1b0aa-109">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the default fill mode, which is <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span></span>  
  
 <span data-ttu-id="1b0aa-110">Örnek kodun çıktısı aşağıdaki çizimde gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1b0aa-110">The following illustration shows the output of the example code.</span></span> <span data-ttu-id="1b0aa-111">Yol doldurulmuş olduğunu unutmayın (göre <xref:System.Drawing.Drawing2D.FillMode.Alternate>) alacağı bitiş noktasından düz bir çizgi, başlangıç noktası için tarafından açık şekilde kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="1b0aa-111">Note that the path is filled (according to <xref:System.Drawing.Drawing2D.FillMode.Alternate>) as if the open figure were closed by a straight line from its ending point to its starting point.</span></span>  
  
 ![FillPath yöntemi çıktısını gösteren diyagram](./media/how-to-fill-open-figures/fill-path-alternate-mode.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1b0aa-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="1b0aa-113">Compiling the Code</span></span>  
 <span data-ttu-id="1b0aa-114">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="1b0aa-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b0aa-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b0aa-115">See also</span></span>

- <xref:System.Drawing.Drawing2D.GraphicsPath>
- [<span data-ttu-id="1b0aa-116">GDI+'da Grafik Yolları</span><span class="sxs-lookup"><span data-stu-id="1b0aa-116">Graphics Paths in GDI+</span></span>](graphics-paths-in-gdi.md)
