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
ms.openlocfilehash: 0e77e4d8eeb9d7a07115b89525ac80074afeb6e8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59323277"
---
# <a name="how-to-align-drawn-text"></a>Nasıl yapılır: Çizilmiş Metni Hizalama
Özel çizim gerçekleştirmek, genellikle bir form veya denetim çizilen metni ortalayın isteyebilirsiniz. İle çizilen metni kolayca hizalayabilirsiniz <xref:System.Drawing.Graphics.DrawString%2A> veya <xref:System.Windows.Forms.TextRenderer.DrawText%2A> doğru bir biçimlendirme nesnesi oluşturma ve uygun bir biçim bayrakları ayarlayarak yöntemleri.  
  
### <a name="to-draw-centered-text-with-gdi-drawstring"></a>Ortalanmış GDI + (DrawString) ile metin çizmek için  
  
1. Kullanım bir <xref:System.Drawing.StringFormat> uygun <xref:System.Drawing.Graphics.DrawString%2A> ortalanmış metnini belirtmek için yöntemi.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#10)]
     [!code-vb[System.Drawing.AlignDrawnText#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#10)]  
  
### <a name="to-draw-centered-text-with-gdi-drawtext"></a>Ortalanmış (DrawText) GDI ile metin çizmek için  
  
1. Kullanım <xref:System.Windows.Forms.TextFormatFlags> sarmalama olarak dikey ve yatay metin uygun ortalama için numaralandırma <xref:System.Windows.Forms.TextRenderer.DrawText%2A> yöntemi.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#20)]
     [!code-vb[System.Drawing.AlignDrawnText#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#20)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki kod örnekleri Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirdikleri <xref:System.Windows.Forms.PaintEventArgs>`e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: GDI ile Metin Çizme](how-to-draw-text-with-gdi.md)
- [Yazı Tipleri ve Metin Kullanma](using-fonts-and-text.md)
- [Nasıl yapılır: Yazı Tipi Aileleri ve Yazı Tipleri Oluşturma](how-to-construct-font-families-and-fonts.md)
