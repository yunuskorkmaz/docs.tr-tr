---
title: 'Nasıl yapılır: GDI ile Metin Çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing with TextRenderer
- drawing [Windows Forms], text
- Windows Forms, drawing text with GDI
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
ms.openlocfilehash: 3ed2b5c94e4a38a5873a34e61287c4038cab5cbb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956536"
---
# <a name="how-to-draw-text-with-gdi"></a><span data-ttu-id="2b3f3-102">Nasıl yapılır: GDI ile Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="2b3f3-102">How to: Draw Text with GDI</span></span>
<span data-ttu-id="2b3f3-103"><xref:System.Windows.Forms.TextRenderer> Sınıfındaki yöntemiyle, bir form veya denetimde metin çizmek için GDI işlevlerine erişebilirsiniz. <xref:System.Windows.Forms.TextRenderer.DrawText%2A></span><span class="sxs-lookup"><span data-stu-id="2b3f3-103">With the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method in the <xref:System.Windows.Forms.TextRenderer> class, you can access GDI functionality for drawing text on a form or control.</span></span> <span data-ttu-id="2b3f3-104">GDI metin işleme, genellikle daha iyi performans ve GDI+ ' dan daha doğru metin ölçme sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b3f3-104">GDI text rendering typically offers better performance and more accurate text measuring than GDI+.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b3f3-105"><xref:System.Windows.Forms.TextRenderer> Sınıfının yöntemleri yazdırma için desteklenmez. <xref:System.Windows.Forms.TextRenderer.DrawText%2A></span><span class="sxs-lookup"><span data-stu-id="2b3f3-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of the <xref:System.Windows.Forms.TextRenderer> class are not supported for printing.</span></span> <span data-ttu-id="2b3f3-106">Yazdırırken, her zaman <xref:System.Drawing.Graphics.DrawString%2A> <xref:System.Drawing.Graphics> sınıfının yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2b3f3-106">When printing, always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b3f3-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b3f3-107">Example</span></span>  
 <span data-ttu-id="2b3f3-108">Aşağıdaki kod örneği, <xref:System.Windows.Forms.TextRenderer.DrawText%2A> yöntemi kullanılarak bir dikdörtgen içinde birden çok satıra nasıl metin çizileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b3f3-108">The following code example demonstrates how to draw text on multiple lines within a rectangle using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 <span data-ttu-id="2b3f3-109"><xref:System.Windows.Forms.TextRenderer> Sınıfı ile metin işlemek için bir <xref:System.Drawing.Graphics> ve <xref:System.Drawing.Font>gibi bir, <xref:System.Drawing.IDeviceContext>metin çizmek için bir konum ve çizilmesi gereken renk gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b3f3-109">To render text with the <xref:System.Windows.Forms.TextRenderer> class, you need an <xref:System.Drawing.IDeviceContext>, such as a <xref:System.Drawing.Graphics> and a <xref:System.Drawing.Font>, a location to draw the text, and the color in which it should be drawn.</span></span> <span data-ttu-id="2b3f3-110">İsteğe bağlı olarak, <xref:System.Windows.Forms.TextFormatFlags> numaralandırmayı kullanarak metin biçimlendirmesini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b3f3-110">Optionally, you can specify the text formatting by using the <xref:System.Windows.Forms.TextFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="2b3f3-111">Alma <xref:System.Drawing.Graphics>hakkında daha fazla bilgi için bkz [. nasıl yapılır: Çizim](how-to-create-graphics-objects-for-drawing.md)için grafik nesneleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2b3f3-111">For more information about obtaining a <xref:System.Drawing.Graphics>, see [How to: Create Graphics Objects for Drawing](how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="2b3f3-112">Oluşturma <xref:System.Drawing.Font>hakkında daha fazla bilgi için bkz [. nasıl yapılır: Yazı tipi aileleri ve yazı](how-to-construct-font-families-and-fonts.md)tipleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2b3f3-112">For more information about constructing a <xref:System.Drawing.Font>, see [How to: Construct Font Families and Fonts](how-to-construct-font-families-and-fonts.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2b3f3-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2b3f3-113">Compiling the Code</span></span>  
 <span data-ttu-id="2b3f3-114">Yukarıdaki kod örneği, Windows Forms ile kullanım için tasarlanmıştır ve parametresi <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.PaintEventHandler>olan `e`' ı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2b3f3-114">The preceding code example is designed for use with Windows Forms, and it requires the <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b3f3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b3f3-115">See also</span></span>

- <xref:System.Windows.Forms.TextRenderer>
- <xref:System.Drawing.Font>
- <xref:System.Drawing.Color>
- [<span data-ttu-id="2b3f3-116">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="2b3f3-116">Using Fonts and Text</span></span>](using-fonts-and-text.md)
