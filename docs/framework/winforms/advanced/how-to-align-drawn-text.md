---
title: 'Nasıl yapılır: Çizilmiş Metni Hizalama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], aligning
- Windows Forms, aligning drawn text
ms.assetid: 83c10a81-1a90-4b5c-98aa-2c6c4b280079
ms.openlocfilehash: 96e14ef510a08ed0c387733e37b6acae6cbd31cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522763"
---
# <a name="how-to-align-drawn-text"></a><span data-ttu-id="37173-102">Nasıl yapılır: Çizilmiş Metni Hizalama</span><span class="sxs-lookup"><span data-stu-id="37173-102">How to: Align Drawn Text</span></span>
<span data-ttu-id="37173-103">Özel çizim gerçekleştirdiğinizde, genellikle bir form veya denetim çizilmiş metni ortalamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37173-103">When you perform custom drawing, you may often want to center drawn text on a form or control.</span></span> <span data-ttu-id="37173-104">Kolayca ile çizilmiş metni hizalama <xref:System.Drawing.Graphics.DrawString%2A> veya <xref:System.Windows.Forms.TextRenderer.DrawText%2A> doğru biçimlendirme nesnesi oluşturma ve uygun biçimde bayrakları ayarlayarak yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="37173-104">You can easily align text drawn with the <xref:System.Drawing.Graphics.DrawString%2A> or <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods by creating the correct formatting object and setting the appropriate format flags.</span></span>  
  
### <a name="to-draw-centered-text-with-gdi-drawstring"></a><span data-ttu-id="37173-105">Ortalanmış metin GDI + (DrawString) ile çizmek için</span><span class="sxs-lookup"><span data-stu-id="37173-105">To draw centered text with GDI+ (DrawString)</span></span>  
  
1.  <span data-ttu-id="37173-106">Kullanım bir <xref:System.Drawing.StringFormat> uygun ile <xref:System.Drawing.Graphics.DrawString%2A> yöntemi ortalanmış metni belirtin.</span><span class="sxs-lookup"><span data-stu-id="37173-106">Use a <xref:System.Drawing.StringFormat> with the appropriate <xref:System.Drawing.Graphics.DrawString%2A> method to specify centered text.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#10)]
     [!code-vb[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#10)]  
  
### <a name="to-draw-centered-text-with-gdi-drawtext"></a><span data-ttu-id="37173-107">Ortalanmış (DrawText) GDI ile metin çizmek için</span><span class="sxs-lookup"><span data-stu-id="37173-107">To draw centered text with GDI (DrawText)</span></span>  
  
1.  <span data-ttu-id="37173-108">Kullanım <xref:System.Windows.Forms.TextFormatFlags> kaydırma yanı sıra dikey ve yatay olarak uygun metinle ortalama için numaralandırma <xref:System.Windows.Forms.TextRenderer.DrawText%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="37173-108">Use the <xref:System.Windows.Forms.TextFormatFlags> enumeration for wrapping as well as vertically and horizontally centering text with the appropriate <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#20)]
     [!code-vb[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#20)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="37173-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="37173-109">Compiling the Code</span></span>  
 <span data-ttu-id="37173-110">Önceki kod örnekleri Windows Forms ile kullanılmak üzere tasarlanmıştır ve ihtiyaç <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="37173-110">The preceding code examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37173-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="37173-111">See Also</span></span>  
 [<span data-ttu-id="37173-112">Nasıl yapılır: GDI ile Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="37173-112">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [<span data-ttu-id="37173-113">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="37173-113">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="37173-114">Nasıl yapılır: Yazı Tipi Aileleri ve Yazı Tipleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="37173-114">How to: Construct Font Families and Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)
