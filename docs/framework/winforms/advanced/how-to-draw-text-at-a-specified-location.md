---
title: "Nasıl yapılır: Belirtilen bir Konuma Metin Çizme"
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
- text [Windows Forms], drawing at specified locations [Windows Forms]
- drawing text
- drawing text [Windows Forms], specified locations [Windows Forms]
- Windows Forms, drawing text a a specified location
ms.assetid: 60816423-1c38-465e-980d-2c2b64d74086
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aab9570b98caec5b3975a5b3ff6f1e62d4ad303b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-text-at-a-specified-location"></a><span data-ttu-id="8bebc-102">Nasıl yapılır: Belirtilen bir Konuma Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="8bebc-102">How to: Draw Text at a Specified Location</span></span>
<span data-ttu-id="8bebc-103">Özel çizim gerçekleştirdiğinizde, belirtilen bir noktada başlangıç tek yatay bir satırda metin çizebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bebc-103">When you perform custom drawing, you can draw text in a single horizontal line starting at a specified point.</span></span> <span data-ttu-id="8bebc-104">Kullanarak bu şekilde metin çizebilirsiniz <xref:System.Drawing.Graphics.DrawString%2A> yöntemi aşırı <xref:System.Drawing.Graphics> geçen sınıfı bir <xref:System.Drawing.Point> veya <xref:System.Drawing.PointF> parametresi.</span><span class="sxs-lookup"><span data-stu-id="8bebc-104">You can draw text in this manner by using the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method of the <xref:System.Drawing.Graphics> class that takes a <xref:System.Drawing.Point> or <xref:System.Drawing.PointF> parameter.</span></span> <span data-ttu-id="8bebc-105"><xref:System.Drawing.Graphics.DrawString%2A> Yöntemi de gerektiren bir <xref:System.Drawing.Brush> ve<xref:System.Drawing.Font></span><span class="sxs-lookup"><span data-stu-id="8bebc-105">The <xref:System.Drawing.Graphics.DrawString%2A> method also requires a <xref:System.Drawing.Brush> and <xref:System.Drawing.Font></span></span>  
  
 <span data-ttu-id="8bebc-106">Aynı zamanda <xref:System.Windows.Forms.TextRenderer.DrawText%2A> yöntemi aşırı <xref:System.Windows.Forms.TextRenderer> alan bir <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="8bebc-106">You can also use the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method of the <xref:System.Windows.Forms.TextRenderer> that takes a <xref:System.Drawing.Point>.</span></span> <span data-ttu-id="8bebc-107"><xref:System.Windows.Forms.TextRenderer.DrawText%2A>Ayrıca gerektiren bir <xref:System.Drawing.Color> ve <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="8bebc-107"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> also requires a <xref:System.Drawing.Color> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="8bebc-108">Belirtilen bir noktada kullandığınızda çizilen metin çıktısı aşağıda gösterilmiştir <xref:System.Drawing.Graphics.DrawString%2A> yöntemi aşırı yüklendi.</span><span class="sxs-lookup"><span data-stu-id="8bebc-108">The following illustration shows the output of text drawn at a specified point when you use the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method.</span></span>  
  
 <span data-ttu-id="8bebc-109">![Yazı tipleri metin](../../../../docs/framework/winforms/advanced/media/csfontstext1.png "csfontstext1")</span><span class="sxs-lookup"><span data-stu-id="8bebc-109">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext1.png "csfontstext1")</span></span>  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a><span data-ttu-id="8bebc-110">GDI + ile metnin bir çizgi çizmek için</span><span class="sxs-lookup"><span data-stu-id="8bebc-110">To draw a line of text with GDI+</span></span>  
  
1.  <span data-ttu-id="8bebc-111">Kullanım <xref:System.Drawing.Graphics.DrawString%2A> istediğiniz metin geçirerek yöntemini <xref:System.Drawing.Point> veya <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, ve <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="8bebc-111">Use the <xref:System.Drawing.Graphics.DrawString%2A> method, passing the text you want, <xref:System.Drawing.Point> or <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, and <xref:System.Drawing.Brush>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a><span data-ttu-id="8bebc-112">GDI ile metin satırının çizmek için</span><span class="sxs-lookup"><span data-stu-id="8bebc-112">To draw a line of text with GDI</span></span>  
  
1.  <span data-ttu-id="8bebc-113">Kullanım <xref:System.Windows.Forms.TextRenderer.DrawText%2A> istediğiniz metin geçirerek yöntemini <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, ve <xref:System.Drawing.Color>.</span><span class="sxs-lookup"><span data-stu-id="8bebc-113">Use the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method, passing the text you want, <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, and <xref:System.Drawing.Color>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8bebc-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8bebc-114">Compiling the Code</span></span>  
 <span data-ttu-id="8bebc-115">Önceki örneklerde gerektirir:</span><span class="sxs-lookup"><span data-stu-id="8bebc-115">The previous examples require:</span></span>  
  
-   <span data-ttu-id="8bebc-116"><xref:System.Windows.Forms.PaintEventArgs>  `e`, bir parametresi olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="8bebc-116"><xref:System.Windows.Forms.PaintEventArgs>  `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bebc-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8bebc-117">See Also</span></span>  
 [<span data-ttu-id="8bebc-118">Nasıl yapılır: GDI ile metin çizme</span><span class="sxs-lookup"><span data-stu-id="8bebc-118">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [<span data-ttu-id="8bebc-119">Yazı tipleri ve metin kullanma</span><span class="sxs-lookup"><span data-stu-id="8bebc-119">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="8bebc-120">Nasıl yapılır: yazı tipi aileleri ve yazı tipleri</span><span class="sxs-lookup"><span data-stu-id="8bebc-120">How to: Construct Font Families and Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 [<span data-ttu-id="8bebc-121">Nasıl yapılır: dikdörtgende sarmalanmış metin dikdörtgene</span><span class="sxs-lookup"><span data-stu-id="8bebc-121">How to: Draw Wrapped Text in a Rectangle</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)
