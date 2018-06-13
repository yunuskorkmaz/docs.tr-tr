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
ms.openlocfilehash: c753be6a200f166e59e1330c7dbcf1fadc7588a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524979"
---
# <a name="how-to-draw-wrapped-text-in-a-rectangle"></a>Nasıl yapılır: Dikdörtgende Sarmalanmış Metin
Kullanarak bir dikdörtgende sarmalanmış metin çizebilirsiniz <xref:System.Drawing.Graphics.DrawString%2A> yöntemi aşırı <xref:System.Drawing.Graphics> geçen sınıfı bir <xref:System.Drawing.Rectangle> veya <xref:System.Drawing.RectangleF> parametresi. Ayrıca kullanacağınız bir <xref:System.Drawing.Brush> ve <xref:System.Drawing.Font>.  
  
 Kullanarak bir dikdörtgende sarmalanmış metin çizebilirsiniz <xref:System.Windows.Forms.TextRenderer.DrawText%2A> yöntemi aşırı <xref:System.Windows.Forms.TextRenderer> alan bir <xref:System.Drawing.Rectangle> ve <xref:System.Windows.Forms.TextFormatFlags> parametresi. Ayrıca kullanacağınız bir <xref:System.Drawing.Color> ve <xref:System.Drawing.Font>.  
  
 Aşağıdaki çizimde kullandığınızda dikdörtgende çizilen metin çıktısını gösterir <xref:System.Drawing.Graphics.DrawString%2A> yöntemi.  
  
 ![Yazı tipleri metin](../../../../docs/framework/winforms/advanced/media/csfontstext2.png "csfontstext2")  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>Çizmek için GDI + ile dikdörtgene metin sarılır.  
  
1.  Kullanım <xref:System.Drawing.Graphics.DrawString%2A> istediğiniz metin geçirme yöntemi aşırı <xref:System.Drawing.Rectangle> veya <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> ve <xref:System.Drawing.Brush>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>Çizmek için bir dikdörtgen GDI ile metin sarılır.  
  
1.  Kullanım <xref:System.Windows.Forms.TextFormatFlags> numaralandırma değeri metni belirlemek için Sarmalanan ile <xref:System.Windows.Forms.TextRenderer.DrawText%2A> istediğiniz metin geçirme yöntemi aşırı <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> ve <xref:System.Drawing.Color>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örneklerde gerektirir:  
  
-   <xref:System.Windows.Forms.PaintEventArgs> `e`, bir parametresi olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: GDI ile Metin Çizme](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [Yazı Tipleri ve Metin Kullanma](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [Nasıl yapılır: Yazı Tipi Aileleri ve Yazı Tipleri Oluşturma](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 [Nasıl yapılır: Belirtilen bir Konuma Metin Çizme](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)
