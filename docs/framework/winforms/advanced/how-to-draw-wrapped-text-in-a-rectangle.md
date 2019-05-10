---
title: 'Nasıl yapılır: Dikdörtgende Sarmalanmış Metin'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drawing text in a rectangle
- text [Windows Forms], drawing in a rectangle
- strings [Windows Forms], drawing in a rectangle
ms.assetid: e1fb432a-dc90-48b5-9b6b-acc14507133d
ms.openlocfilehash: ace79e45737a3ce26d8bdcd603e923c1e6040d4d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626157"
---
# <a name="how-to-draw-wrapped-text-in-a-rectangle"></a><span data-ttu-id="abfc6-102">Nasıl yapılır: Dikdörtgende Sarmalanmış Metin</span><span class="sxs-lookup"><span data-stu-id="abfc6-102">How to: Draw Wrapped Text in a Rectangle</span></span>
<span data-ttu-id="abfc6-103">Kullanarak bir dikdörtgende sarmalanmış metin çizebilirsiniz <xref:System.Drawing.Graphics.DrawString%2A> yöntemi aşırı <xref:System.Drawing.Graphics> alan sınıfı bir <xref:System.Drawing.Rectangle> veya <xref:System.Drawing.RectangleF> parametresi.</span><span class="sxs-lookup"><span data-stu-id="abfc6-103">You can draw wrapped text in a rectangle by using the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method of the <xref:System.Drawing.Graphics> class that takes a <xref:System.Drawing.Rectangle> or <xref:System.Drawing.RectangleF> parameter.</span></span> <span data-ttu-id="abfc6-104">Ayrıca kullanacağınız bir <xref:System.Drawing.Brush> ve <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="abfc6-104">You will also use a <xref:System.Drawing.Brush> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="abfc6-105">Kullanarak bir dikdörtgende sarmalanmış metin çizebilirsiniz <xref:System.Windows.Forms.TextRenderer.DrawText%2A> yöntemi aşırı <xref:System.Windows.Forms.TextRenderer> almayan bir <xref:System.Drawing.Rectangle> ve <xref:System.Windows.Forms.TextFormatFlags> parametresi.</span><span class="sxs-lookup"><span data-stu-id="abfc6-105">You can also draw wrapped text in a rectangle by using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method of the <xref:System.Windows.Forms.TextRenderer> that takes a <xref:System.Drawing.Rectangle> and a <xref:System.Windows.Forms.TextFormatFlags> parameter.</span></span> <span data-ttu-id="abfc6-106">Ayrıca kullanacağınız bir <xref:System.Drawing.Color> ve <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="abfc6-106">You will also use a <xref:System.Drawing.Color> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="abfc6-107">Kullanırken dikdörtgende çizilen metin çıktısı aşağıdaki çizimde <xref:System.Drawing.Graphics.DrawString%2A> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="abfc6-107">The following illustration shows the output of text drawn in the rectangle when you use the <xref:System.Drawing.Graphics.DrawString%2A> method:</span></span>
  
 ![Çıkış DrawString yöntemi kullanılırken gösteren ekran görüntüsü.](./media/how-to-draw-wrapped-text-in-a-rectangle/drawstring-method-font-text.png)  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a><span data-ttu-id="abfc6-109">Çizilecek GDI + ile bir dikdörtgen metin sarmalanmış.</span><span class="sxs-lookup"><span data-stu-id="abfc6-109">To draw wrapped text in a rectangle with GDI+</span></span>  
  
1. <span data-ttu-id="abfc6-110">Kullanım <xref:System.Drawing.Graphics.DrawString%2A> istediğiniz metni geçirerek yöntemini aşırı <xref:System.Drawing.Rectangle> veya <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> ve <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="abfc6-110">Use the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method, passing the text you want, <xref:System.Drawing.Rectangle> or <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> and <xref:System.Drawing.Brush>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a><span data-ttu-id="abfc6-111">Çizmek için dikdörtgen GDI ile metin sarmalanmış.</span><span class="sxs-lookup"><span data-stu-id="abfc6-111">To draw wrapped text in a rectangle with GDI</span></span>  
  
1. <span data-ttu-id="abfc6-112">Kullanım <xref:System.Windows.Forms.TextFormatFlags> numaralandırma değeri gösterilen yazıyı belirtmek için sarmalanmış ile <xref:System.Windows.Forms.TextRenderer.DrawText%2A> istediğiniz metni geçirerek yöntemini aşırı <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> ve <xref:System.Drawing.Color>.</span><span class="sxs-lookup"><span data-stu-id="abfc6-112">Use the <xref:System.Windows.Forms.TextFormatFlags> enumeration value to specify the text should be wrapped with the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method, passing the text you want, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> and <xref:System.Drawing.Color>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="abfc6-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="abfc6-113">Compiling the Code</span></span>  
 <span data-ttu-id="abfc6-114">Önceki örneklerde gerektirir:</span><span class="sxs-lookup"><span data-stu-id="abfc6-114">The previous examples require:</span></span>  
  
- <span data-ttu-id="abfc6-115"><xref:System.Windows.Forms.PaintEventArgs> `e`, bir parametresi olan <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="abfc6-115"><xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abfc6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abfc6-116">See also</span></span>

- [<span data-ttu-id="abfc6-117">Nasıl yapılır: GDI ile metin çizme</span><span class="sxs-lookup"><span data-stu-id="abfc6-117">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
- [<span data-ttu-id="abfc6-118">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="abfc6-118">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="abfc6-119">Nasıl yapılır: Yazı tipi aileleri ve yazı tipleri</span><span class="sxs-lookup"><span data-stu-id="abfc6-119">How to: Construct Font Families and Fonts</span></span>](how-to-construct-font-families-and-fonts.md)
- [<span data-ttu-id="abfc6-120">Nasıl yapılır: Belirtilen bir konuma metin çizme</span><span class="sxs-lookup"><span data-stu-id="abfc6-120">How to: Draw Text at a Specified Location</span></span>](how-to-draw-text-at-a-specified-location.md)
