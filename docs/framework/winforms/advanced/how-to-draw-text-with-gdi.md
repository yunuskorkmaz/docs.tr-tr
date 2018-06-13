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
ms.openlocfilehash: e18ff96ea97eb636de8ab73aaa094c07b10fd456
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522921"
---
# <a name="how-to-draw-text-with-gdi"></a><span data-ttu-id="0e01e-102">Nasıl yapılır: GDI ile Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="0e01e-102">How to: Draw Text with GDI</span></span>
<span data-ttu-id="0e01e-103">İle <xref:System.Windows.Forms.TextRenderer.DrawText%2A> yönteminde <xref:System.Windows.Forms.TextRenderer> sınıfı, erişebilir [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] bir form veya denetim metin çizme işlevi.</span><span class="sxs-lookup"><span data-stu-id="0e01e-103">With the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method in the <xref:System.Windows.Forms.TextRenderer> class, you can access [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] functionality for drawing text on a form or control.</span></span> [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]<span data-ttu-id="0e01e-104"> metin işleme genellikle daha iyi performans ve daha ölçmek daha doğru metin sunar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0e01e-104"> text rendering typically offers better performance and more accurate text measuring than [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0e01e-105"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> Yöntemlerinin <xref:System.Windows.Forms.TextRenderer> sınıfı yazdırmak için desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="0e01e-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of the <xref:System.Windows.Forms.TextRenderer> class are not supported for printing.</span></span> <span data-ttu-id="0e01e-106">Yazdırma sırasında her zaman kullanmak <xref:System.Drawing.Graphics.DrawString%2A> yöntemlerinin <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0e01e-106">When printing, always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e01e-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e01e-107">Example</span></span>  
 <span data-ttu-id="0e01e-108">Aşağıdaki kod örneği kullanarak bir dikdörtgen içinde birden çok satıra metin çizme gösterilmiştir <xref:System.Windows.Forms.TextRenderer.DrawText%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0e01e-108">The following code example demonstrates how to draw text on multiple lines within a rectangle using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 <span data-ttu-id="0e01e-109">Metinle işlemek için <xref:System.Windows.Forms.TextRenderer> ihtiyacınız sınıfı, bir <xref:System.Drawing.IDeviceContext>, gibi bir <xref:System.Drawing.Graphics> ve <xref:System.Drawing.Font>, metin ve, bunu çizilip rengi çizmek için bir konum.</span><span class="sxs-lookup"><span data-stu-id="0e01e-109">To render text with the <xref:System.Windows.Forms.TextRenderer> class, you need an <xref:System.Drawing.IDeviceContext>, such as a <xref:System.Drawing.Graphics> and a <xref:System.Drawing.Font>, a location to draw the text, and the color in which it should be drawn.</span></span> <span data-ttu-id="0e01e-110">İsteğe bağlı olarak, metin kullanarak biçimlendirme belirtebilirsiniz <xref:System.Windows.Forms.TextFormatFlags> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="0e01e-110">Optionally, you can specify the text formatting by using the <xref:System.Windows.Forms.TextFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="0e01e-111">Edinme hakkında daha fazla bilgi için bir <xref:System.Drawing.Graphics>, bkz: [nasıl yapılır: çizim için grafik nesneleri oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="0e01e-111">For more information about obtaining a <xref:System.Drawing.Graphics>, see [How to: Create Graphics Objects for Drawing](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="0e01e-112">Oluşturma hakkında daha fazla bilgi için bir <xref:System.Drawing.Font>, bkz: [nasıl yapılır: yazı tipi aileleri oluşturmak ve yazı tipleri](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md).</span><span class="sxs-lookup"><span data-stu-id="0e01e-112">For more information about constructing a <xref:System.Drawing.Font>, see [How to: Construct Font Families and Fonts](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0e01e-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0e01e-113">Compiling the Code</span></span>  
 <span data-ttu-id="0e01e-114">Önceki kod örneğinde Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="0e01e-114">The preceding code example is designed for use with Windows Forms, and it requires the <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e01e-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e01e-115">See Also</span></span>  
 <xref:System.Windows.Forms.TextRenderer>  
 <xref:System.Drawing.Font>  
 <xref:System.Drawing.Color>  
 <xref:System.Drawing.Color>  
 [<span data-ttu-id="0e01e-116">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="0e01e-116">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
