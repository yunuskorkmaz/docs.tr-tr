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
ms.openlocfilehash: e5a1791e21981f60e008b97a51d10f88b827de8d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660378"
---
# <a name="how-to-draw-text-at-a-specified-location"></a>Nasıl yapılır: Belirtilen bir konuma metin çizme
Özel çizim gerçekleştirdiğinizde, tek bir yatay satırda başlayan belirli bir noktada metin çizebilirsiniz. Bu şekilde kullanarak metin çizebilirsiniz <xref:System.Drawing.Graphics.DrawString%2A> yöntemi aşırı <xref:System.Drawing.Graphics> alan sınıfı bir <xref:System.Drawing.Point> veya <xref:System.Drawing.PointF> parametresi. <xref:System.Drawing.Graphics.DrawString%2A> Yöntemi de gerektiren bir <xref:System.Drawing.Brush> ve <xref:System.Drawing.Font>  
  
 Ayrıca <xref:System.Windows.Forms.TextRenderer.DrawText%2A> yöntemi aşırı <xref:System.Windows.Forms.TextRenderer> almayan bir <xref:System.Drawing.Point>. <xref:System.Windows.Forms.TextRenderer.DrawText%2A> Ayrıca gerektiren bir <xref:System.Drawing.Color> ve <xref:System.Drawing.Font>.  
  
 Kullandığınızda, belirli bir noktada çizilen metin çıktısı aşağıdaki çizimde <xref:System.Drawing.Graphics.DrawString%2A> yöntemi aşırı yüklendi.  
  
 ![Yazı tipleri metin](../../../../docs/framework/winforms/advanced/media/csfontstext1.png "csfontstext1")  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>GDI + ile metnin bir çizgi çizmek için  
  
1.  Kullanım <xref:System.Drawing.Graphics.DrawString%2A> istediğiniz metni geçirerek yöntemini <xref:System.Drawing.Point> veya <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, ve <xref:System.Drawing.Brush>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>GDI ile metin satırı çizmek için  
  
1.  Kullanım <xref:System.Windows.Forms.TextRenderer.DrawText%2A> istediğiniz metni geçirerek yöntemini <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, ve <xref:System.Drawing.Color>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örneklerde gerektirir:  
  
-   <xref:System.Windows.Forms.PaintEventArgs>  `e`, bir parametresi olan <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: GDI ile metin çizme](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
- [Yazı Tipleri ve Metin Kullanma](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
- [Nasıl yapılır: Yazı tipi aileleri ve yazı tipleri](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)
- [Nasıl yapılır: Bir dikdörtgende sarmalanmış metin çizme](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)
