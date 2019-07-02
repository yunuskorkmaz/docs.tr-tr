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
ms.openlocfilehash: 3d5b79e82185c044314ff8807b86835ef6a87c45
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505913"
---
# <a name="how-to-draw-text-with-gdi"></a><span data-ttu-id="5c1eb-102">Nasıl yapılır: GDI ile Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="5c1eb-102">How to: Draw Text with GDI</span></span>
<span data-ttu-id="5c1eb-103">İle <xref:System.Windows.Forms.TextRenderer.DrawText%2A> yönteminde <xref:System.Windows.Forms.TextRenderer> sınıfı, bir form veya denetim metin çizme GDI işlevselliği erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5c1eb-103">With the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method in the <xref:System.Windows.Forms.TextRenderer> class, you can access GDI functionality for drawing text on a form or control.</span></span> <span data-ttu-id="5c1eb-104">GDI metin işleme, genellikle daha iyi performans ve GDI + ' ölçmek daha doğru metin sunar.</span><span class="sxs-lookup"><span data-stu-id="5c1eb-104">GDI text rendering typically offers better performance and more accurate text measuring than GDI+.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c1eb-105"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> Yöntemlerinin <xref:System.Windows.Forms.TextRenderer> sınıf için yazdırma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="5c1eb-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of the <xref:System.Windows.Forms.TextRenderer> class are not supported for printing.</span></span> <span data-ttu-id="5c1eb-106">Yazdırma sırasında her zaman kullan <xref:System.Drawing.Graphics.DrawString%2A> yöntemlerinin <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5c1eb-106">When printing, always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c1eb-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="5c1eb-107">Example</span></span>  
 <span data-ttu-id="5c1eb-108">Aşağıdaki kod örneği kullanarak bir dikdörtgen içindeki birden fazla satır üzerinde metin Çiz gösterilmektedir <xref:System.Windows.Forms.TextRenderer.DrawText%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5c1eb-108">The following code example demonstrates how to draw text on multiple lines within a rectangle using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 <span data-ttu-id="5c1eb-109">Metin işlemek için <xref:System.Windows.Forms.TextRenderer> ihtiyacınız sınıfı, bir <xref:System.Drawing.IDeviceContext>, gibi bir <xref:System.Drawing.Graphics> ve <xref:System.Drawing.Font>, metin ve rengini, bunu çizilip çizmek için bir konum.</span><span class="sxs-lookup"><span data-stu-id="5c1eb-109">To render text with the <xref:System.Windows.Forms.TextRenderer> class, you need an <xref:System.Drawing.IDeviceContext>, such as a <xref:System.Drawing.Graphics> and a <xref:System.Drawing.Font>, a location to draw the text, and the color in which it should be drawn.</span></span> <span data-ttu-id="5c1eb-110">Metin biçimlendirme kullanarak isteğe bağlı olarak belirtebilirsiniz <xref:System.Windows.Forms.TextFormatFlags> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="5c1eb-110">Optionally, you can specify the text formatting by using the <xref:System.Windows.Forms.TextFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="5c1eb-111">Daha fazla bilgi edinmek için bir <xref:System.Drawing.Graphics>, bkz: [nasıl yapılır: Çizim için grafik nesneleri oluşturma](how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="5c1eb-111">For more information about obtaining a <xref:System.Drawing.Graphics>, see [How to: Create Graphics Objects for Drawing](how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="5c1eb-112">Oluşturma hakkında daha fazla bilgi için bir <xref:System.Drawing.Font>, bkz: [nasıl yapılır: Yazı tipi aileleri ve yazı tipleri oluşturmak](how-to-construct-font-families-and-fonts.md).</span><span class="sxs-lookup"><span data-stu-id="5c1eb-112">For more information about constructing a <xref:System.Drawing.Font>, see [How to: Construct Font Families and Fonts](how-to-construct-font-families-and-fonts.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5c1eb-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="5c1eb-113">Compiling the Code</span></span>  
 <span data-ttu-id="5c1eb-114">Yukarıdaki kod örneğinde, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="5c1eb-114">The preceding code example is designed for use with Windows Forms, and it requires the <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c1eb-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c1eb-115">See also</span></span>

- <xref:System.Windows.Forms.TextRenderer>
- <xref:System.Drawing.Font>
- <xref:System.Drawing.Color>
- [<span data-ttu-id="5c1eb-116">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="5c1eb-116">Using Fonts and Text</span></span>](using-fonts-and-text.md)
