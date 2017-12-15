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
- Windows Forms, drawing text at a specified location
ms.assetid: 60816423-1c38-465e-980d-2c2b64d74086
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fe6e8563b19ef18b89ad970f3ca35bf5f0782a32
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2017
---
# <a name="how-to-draw-text-at-a-specified-location"></a>Nasıl yapılır: Belirtilen bir Konuma Metin Çizme
Özel çizim gerçekleştirdiğinizde, belirtilen bir noktada başlangıç tek yatay bir satırda metin çizebilirsiniz. Kullanarak bu şekilde metin çizebilirsiniz <xref:System.Drawing.Graphics.DrawString%2A> yöntemi aşırı <xref:System.Drawing.Graphics> geçen sınıfı bir <xref:System.Drawing.Point> veya <xref:System.Drawing.PointF> parametresi. <xref:System.Drawing.Graphics.DrawString%2A> Yöntemi de gerektiren bir <xref:System.Drawing.Brush> ve<xref:System.Drawing.Font>  
  
 Aynı zamanda <xref:System.Windows.Forms.TextRenderer.DrawText%2A> yöntemi aşırı <xref:System.Windows.Forms.TextRenderer> alan bir <xref:System.Drawing.Point>. <xref:System.Windows.Forms.TextRenderer.DrawText%2A>Ayrıca gerektiren bir <xref:System.Drawing.Color> ve <xref:System.Drawing.Font>.  
  
 Belirtilen bir noktada kullandığınızda çizilen metin çıktısı aşağıda gösterilmiştir <xref:System.Drawing.Graphics.DrawString%2A> yöntemi aşırı yüklendi.  
  
 ![Yazı tipleri metin](../../../../docs/framework/winforms/advanced/media/csfontstext1.png "csfontstext1")  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>GDI + ile metnin bir çizgi çizmek için  
  
1.  Kullanım <xref:System.Drawing.Graphics.DrawString%2A> istediğiniz metin geçirerek yöntemini <xref:System.Drawing.Point> veya <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, ve <xref:System.Drawing.Brush>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>GDI ile metin satırının çizmek için  
  
1.  Kullanım <xref:System.Windows.Forms.TextRenderer.DrawText%2A> istediğiniz metin geçirerek yöntemini <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, ve <xref:System.Drawing.Color>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örneklerde gerektirir:  
  
-   <xref:System.Windows.Forms.PaintEventArgs>  `e`, bir parametresi olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: GDI ile Metin Çizme](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [Yazı Tipleri ve Metin Kullanma](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [Nasıl yapılır: Yazı Tipi Aileleri ve Yazı Tipleri Oluşturma](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 [Nasıl yapılır: Dikdörtgende Sarmalanmış Metin](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)
