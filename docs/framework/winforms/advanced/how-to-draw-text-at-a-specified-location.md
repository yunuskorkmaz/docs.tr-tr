---
title: 'Nasıl yapılır: Belirtilen bir Konuma Metin Çizme'
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
ms.openlocfilehash: f7834ea45db8dd6e971defd9c3b2b152ffddf512
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59336414"
---
# <a name="how-to-draw-text-at-a-specified-location"></a>Nasıl yapılır: Belirtilen bir Konuma Metin Çizme
Özel çizim gerçekleştirdiğinizde, tek bir yatay satırda başlayan belirli bir noktada metin çizebilirsiniz. Bu şekilde kullanarak metin çizebilirsiniz <xref:System.Drawing.Graphics.DrawString%2A> yöntemi aşırı <xref:System.Drawing.Graphics> alan sınıfı bir <xref:System.Drawing.Point> veya <xref:System.Drawing.PointF> parametresi. <xref:System.Drawing.Graphics.DrawString%2A> Yöntemi de gerektiren bir <xref:System.Drawing.Brush> ve <xref:System.Drawing.Font>  
  
 Ayrıca <xref:System.Windows.Forms.TextRenderer.DrawText%2A> yöntemi aşırı <xref:System.Windows.Forms.TextRenderer> almayan bir <xref:System.Drawing.Point>. <xref:System.Windows.Forms.TextRenderer.DrawText%2A> Ayrıca gerektiren bir <xref:System.Drawing.Color> ve <xref:System.Drawing.Font>.  
  
 Kullandığınızda, belirli bir noktada çizilen metin çıktısı aşağıdaki çizimde <xref:System.Drawing.Graphics.DrawString%2A> yöntemi aşırı yüklendi.  
  
 ![Belirli bir noktada metin çıktısını gösteren ekran görüntüsü.](./media/how-to-draw-text-at-a-specified-location/font-text-specified-point.png)  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>GDI + ile metnin bir çizgi çizmek için  
  
1. Kullanım <xref:System.Drawing.Graphics.DrawString%2A> istediğiniz metni geçirerek yöntemini <xref:System.Drawing.Point> veya <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, ve <xref:System.Drawing.Brush>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>GDI ile metin satırı çizmek için  
  
1. Kullanım <xref:System.Windows.Forms.TextRenderer.DrawText%2A> istediğiniz metni geçirerek yöntemini <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, ve <xref:System.Drawing.Color>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örneklerde gerektirir:  
  
-   <xref:System.Windows.Forms.PaintEventArgs>  `e`, bir parametresi olan <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: GDI ile metin çizme](how-to-draw-text-with-gdi.md)
- [Yazı Tipleri ve Metin Kullanma](using-fonts-and-text.md)
- [Nasıl yapılır: Yazı tipi aileleri ve yazı tipleri](how-to-construct-font-families-and-fonts.md)
- [Nasıl yapılır: Bir dikdörtgende sarmalanmış metin çizme](how-to-draw-wrapped-text-in-a-rectangle.md)
