---
title: 'Nasıl yapılır: Çizgi Uçlarıyla Çizgi Çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
- drawing lines [Windows Forms], line caps
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
ms.openlocfilehash: be492f2317d4677776cc9f89f546c935d271019b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523227"
---
# <a name="how-to-draw-a-line-with-line-caps"></a>Nasıl yapılır: Çizgi Uçlarıyla Çizgi Çizme
Başlangıç ya da bir satırın sonuna satır caps adlı birkaç şekiller birinde çizebilirsiniz. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] gidiş, kare, Karo ve Ok ucunu gibi birkaç satır caps destekler.  
  
## <a name="example"></a>Örnek  
 Satır caps başlangıç satırı (Başlangıç cap), (son cap) satırın sonuna veya kesik çizgi (tire cap) tireler belirtebilirsiniz.  
  
 Aşağıdaki örnekte bir ok ucunu bir uçta ve diğer uçtaki yuvarlak bir uç satırıyla çizilmiştir. Sonuçta elde edilen satır çizimde gösterilmektedir:  
  
 ![Kalemler](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")  
  
 [!code-csharp[System.Drawing.UsingAPen#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bir Windows formu oluşturma ve form ele <xref:System.Windows.Forms.Control.Paint> olay. Örnek kod içine yapıştırma <xref:System.Windows.Forms.Control.Paint> geçirme olay işleyicisi `e` olarak <xref:System.Windows.Forms.PaintEventArgs>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>  
 [Windows Forms’da Grafikler ve Çizim](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
