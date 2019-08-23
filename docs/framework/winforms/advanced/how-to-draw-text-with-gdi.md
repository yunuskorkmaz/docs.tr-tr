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
# <a name="how-to-draw-text-with-gdi"></a>Nasıl yapılır: GDI ile Metin Çizme
<xref:System.Windows.Forms.TextRenderer> Sınıfındaki yöntemiyle, bir form veya denetimde metin çizmek için GDI işlevlerine erişebilirsiniz. <xref:System.Windows.Forms.TextRenderer.DrawText%2A> GDI metin işleme, genellikle daha iyi performans ve GDI+ ' dan daha doğru metin ölçme sağlar.  
  
> [!NOTE]
> <xref:System.Windows.Forms.TextRenderer> Sınıfının yöntemleri yazdırma için desteklenmez. <xref:System.Windows.Forms.TextRenderer.DrawText%2A> Yazdırırken, her zaman <xref:System.Drawing.Graphics.DrawString%2A> <xref:System.Drawing.Graphics> sınıfının yöntemlerini kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, <xref:System.Windows.Forms.TextRenderer.DrawText%2A> yöntemi kullanılarak bir dikdörtgen içinde birden çok satıra nasıl metin çizileceğini gösterir.  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 <xref:System.Windows.Forms.TextRenderer> Sınıfı ile metin işlemek için bir <xref:System.Drawing.Graphics> ve <xref:System.Drawing.Font>gibi bir, <xref:System.Drawing.IDeviceContext>metin çizmek için bir konum ve çizilmesi gereken renk gerekir. İsteğe bağlı olarak, <xref:System.Windows.Forms.TextFormatFlags> numaralandırmayı kullanarak metin biçimlendirmesini belirtebilirsiniz.  
  
 Alma <xref:System.Drawing.Graphics>hakkında daha fazla bilgi için bkz [. nasıl yapılır: Çizim](how-to-create-graphics-objects-for-drawing.md)için grafik nesneleri oluşturun. Oluşturma <xref:System.Drawing.Font>hakkında daha fazla bilgi için bkz [. nasıl yapılır: Yazı tipi aileleri ve yazı](how-to-construct-font-families-and-fonts.md)tipleri oluşturun.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki kod örneği, Windows Forms ile kullanım için tasarlanmıştır ve parametresi <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.PaintEventHandler>olan `e`' ı gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.TextRenderer>
- <xref:System.Drawing.Font>
- <xref:System.Drawing.Color>
- [Yazı Tipleri ve Metin Kullanma](using-fonts-and-text.md)
