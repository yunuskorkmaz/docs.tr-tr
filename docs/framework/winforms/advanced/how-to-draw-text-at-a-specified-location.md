---
title: 'Nasıl yapılır: Belirtilen bir konuma metin çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing at specified locations [Windows Forms]
- drawing text
- drawing text [Windows Forms], specified locations [Windows Forms]
- Windows Forms, drawing text at a specified location
ms.assetid: 60816423-1c38-465e-980d-2c2b64d74086
ms.openlocfilehash: 3bca6cd364ed4e0d0179c13fb378449b7cf05739
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705356"
---
# <a name="how-to-draw-text-at-a-specified-location"></a><span data-ttu-id="0c643-102">Nasıl yapılır: Belirtilen bir konuma metin çizme</span><span class="sxs-lookup"><span data-stu-id="0c643-102">How to: Draw Text at a Specified Location</span></span>
<span data-ttu-id="0c643-103">Özel çizim gerçekleştirdiğinizde, tek bir yatay satırda başlayan belirli bir noktada metin çizebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c643-103">When you perform custom drawing, you can draw text in a single horizontal line starting at a specified point.</span></span> <span data-ttu-id="0c643-104">Bu şekilde kullanarak metin çizebilirsiniz <xref:System.Drawing.Graphics.DrawString%2A> yöntemi aşırı <xref:System.Drawing.Graphics> alan sınıfı bir <xref:System.Drawing.Point> veya <xref:System.Drawing.PointF> parametresi.</span><span class="sxs-lookup"><span data-stu-id="0c643-104">You can draw text in this manner by using the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method of the <xref:System.Drawing.Graphics> class that takes a <xref:System.Drawing.Point> or <xref:System.Drawing.PointF> parameter.</span></span> <span data-ttu-id="0c643-105"><xref:System.Drawing.Graphics.DrawString%2A> Yöntemi de gerektiren bir <xref:System.Drawing.Brush> ve <xref:System.Drawing.Font></span><span class="sxs-lookup"><span data-stu-id="0c643-105">The <xref:System.Drawing.Graphics.DrawString%2A> method also requires a <xref:System.Drawing.Brush> and <xref:System.Drawing.Font></span></span>  
  
 <span data-ttu-id="0c643-106">Ayrıca <xref:System.Windows.Forms.TextRenderer.DrawText%2A> yöntemi aşırı <xref:System.Windows.Forms.TextRenderer> almayan bir <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="0c643-106">You can also use the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method of the <xref:System.Windows.Forms.TextRenderer> that takes a <xref:System.Drawing.Point>.</span></span> <span data-ttu-id="0c643-107"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> Ayrıca gerektiren bir <xref:System.Drawing.Color> ve <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="0c643-107"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> also requires a <xref:System.Drawing.Color> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="0c643-108">Kullandığınızda, belirli bir noktada çizilen metin çıktısı aşağıdaki çizimde <xref:System.Drawing.Graphics.DrawString%2A> yöntemi aşırı yüklendi.</span><span class="sxs-lookup"><span data-stu-id="0c643-108">The following illustration shows the output of text drawn at a specified point when you use the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method.</span></span>  
  
 <span data-ttu-id="0c643-109">![Yazı tipleri metin](./media/csfontstext1.png "csfontstext1")</span><span class="sxs-lookup"><span data-stu-id="0c643-109">![Fonts Text](./media/csfontstext1.png "csfontstext1")</span></span>  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a><span data-ttu-id="0c643-110">GDI + ile metnin bir çizgi çizmek için</span><span class="sxs-lookup"><span data-stu-id="0c643-110">To draw a line of text with GDI+</span></span>  
  
1.  <span data-ttu-id="0c643-111">Kullanım <xref:System.Drawing.Graphics.DrawString%2A> istediğiniz metni geçirerek yöntemini <xref:System.Drawing.Point> veya <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, ve <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="0c643-111">Use the <xref:System.Drawing.Graphics.DrawString%2A> method, passing the text you want, <xref:System.Drawing.Point> or <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, and <xref:System.Drawing.Brush>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a><span data-ttu-id="0c643-112">GDI ile metin satırı çizmek için</span><span class="sxs-lookup"><span data-stu-id="0c643-112">To draw a line of text with GDI</span></span>  
  
1.  <span data-ttu-id="0c643-113">Kullanım <xref:System.Windows.Forms.TextRenderer.DrawText%2A> istediğiniz metni geçirerek yöntemini <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, ve <xref:System.Drawing.Color>.</span><span class="sxs-lookup"><span data-stu-id="0c643-113">Use the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method, passing the text you want, <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, and <xref:System.Drawing.Color>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0c643-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0c643-114">Compiling the Code</span></span>  
 <span data-ttu-id="0c643-115">Önceki örneklerde gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0c643-115">The previous examples require:</span></span>  
  
-   <span data-ttu-id="0c643-116"><xref:System.Windows.Forms.PaintEventArgs>  `e`, bir parametresi olan <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="0c643-116"><xref:System.Windows.Forms.PaintEventArgs>  `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c643-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c643-117">See also</span></span>
- [<span data-ttu-id="0c643-118">Nasıl yapılır: GDI ile metin çizme</span><span class="sxs-lookup"><span data-stu-id="0c643-118">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
- [<span data-ttu-id="0c643-119">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="0c643-119">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="0c643-120">Nasıl yapılır: Yazı tipi aileleri ve yazı tipleri</span><span class="sxs-lookup"><span data-stu-id="0c643-120">How to: Construct Font Families and Fonts</span></span>](how-to-construct-font-families-and-fonts.md)
- [<span data-ttu-id="0c643-121">Nasıl yapılır: Bir dikdörtgende sarmalanmış metin çizme</span><span class="sxs-lookup"><span data-stu-id="0c643-121">How to: Draw Wrapped Text in a Rectangle</span></span>](how-to-draw-wrapped-text-in-a-rectangle.md)
