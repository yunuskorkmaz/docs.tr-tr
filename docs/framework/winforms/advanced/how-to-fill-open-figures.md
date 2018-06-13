---
title: 'Nasıl Yapılır: Açık Şekilleri Doldurma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
ms.openlocfilehash: b7422ae2a4dc4d59fd337ab2294caa0d65057bae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521166"
---
# <a name="how-to-fill-open-figures"></a><span data-ttu-id="4c052-102">Nasıl Yapılır: Açık Şekilleri Doldurma</span><span class="sxs-lookup"><span data-stu-id="4c052-102">How to: Fill Open Figures</span></span>
<span data-ttu-id="4c052-103">Geçirerek bir yolu doldurabilir bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesnesinin <xref:System.Drawing.Graphics.FillPath%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4c052-103">You can fill a path by passing a <xref:System.Drawing.Drawing2D.GraphicsPath> object to the <xref:System.Drawing.Graphics.FillPath%2A> method.</span></span> <span data-ttu-id="4c052-104"><xref:System.Drawing.Graphics.FillPath%2A> Yöntemi yolunu ayarlanmış yolun dolgu modunu (alternatif veya sarma) göre doldurur.</span><span class="sxs-lookup"><span data-stu-id="4c052-104">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the fill mode (alternate or winding) currently set for the path.</span></span> <span data-ttu-id="4c052-105">Tüm açık şekilleri yol varsa, bu rakamları kapatılan gibi yolun girilir.</span><span class="sxs-lookup"><span data-stu-id="4c052-105">If the path has any open figures, the path is filled as if those figures were closed.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="4c052-106"> bir şekil, başlangıç noktası bitiş noktasından bir çizgide çizerek kapatır.</span><span class="sxs-lookup"><span data-stu-id="4c052-106"> closes a figure by drawing a straight line from its ending point to its starting point.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c052-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="4c052-107">Example</span></span>  
 <span data-ttu-id="4c052-108">Aşağıdaki örnek, bir açık şekli (yay) ve bir kapalı şekli (elips) sahip bir yol oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4c052-108">The following example creates a path that has one open figure (an arc) and one closed figure (an ellipse).</span></span> <span data-ttu-id="4c052-109"><xref:System.Drawing.Graphics.FillPath%2A> Yöntemi doldurur olan varsayılan doldurma modu göre yolu <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span><span class="sxs-lookup"><span data-stu-id="4c052-109">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the default fill mode, which is <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span></span>  
  
 <span data-ttu-id="4c052-110">Aşağıdaki çizimde örnek kod çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4c052-110">The following illustration shows the output of the example code.</span></span> <span data-ttu-id="4c052-111">Yolun girilir unutmayın (göre <xref:System.Drawing.Drawing2D.FillMode.Alternate>) sanki açık şekilde bir çizgide bitiş noktasından, başlangıç noktası tarafından kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="4c052-111">Note that the path is filled (according to <xref:System.Drawing.Drawing2D.FillMode.Alternate>) as if the open figure were closed by a straight line from its ending point to its starting point.</span></span>  
  
 <span data-ttu-id="4c052-112">![Dolgu açma yolu](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")</span><span class="sxs-lookup"><span data-stu-id="4c052-112">![Fill Open Path](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4c052-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="4c052-113">Compiling the Code</span></span>  
 <span data-ttu-id="4c052-114">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="4c052-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c052-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4c052-115">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 [<span data-ttu-id="4c052-116">GDI+'da Grafik Yolları</span><span class="sxs-lookup"><span data-stu-id="4c052-116">Graphics Paths in GDI+</span></span>](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)
