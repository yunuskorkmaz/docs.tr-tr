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
ms.openlocfilehash: c4a78569f6c0b14c32154611412d6b3ccd8a84ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004216"
---
# <a name="how-to-draw-a-line-with-line-caps"></a>Nasıl yapılır: Çizgi Uçlarıyla Çizgi Çizme
Satır caps adlı birkaç şekil birini başlangıç veya satırın çizebilirsiniz. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] hepsini, kare, elmas ve ok ucu gibi birkaç satır caps destekler.  
  
## <a name="example"></a>Örnek  
 İçin bir satır (Başlangıç cap), bir satır (bitiş ucu) veya tireler (dash cap) kesikli satır başı satır caps belirtebilirsiniz.  
  
 Aşağıdaki örnek, bir ucunda bir ok ucu ve diğer uçtaki yuvarlak bir uç bir çizgi çizer. Çizim, sonuçta elde edilen satırı gösterir:  
  
 ![Yuvarlak bir uç bir çizgiyle gösterildiği çizim.](./media/how-to-draw-a-line-with-line-caps/line-cap-arrowhead-example.gif)  
  
 [!code-csharp[System.Drawing.UsingAPen#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Bir Windows formu oluşturma ve form ele <xref:System.Windows.Forms.Control.Paint> olay. Örnek kodun içine yapıştırın <xref:System.Windows.Forms.Control.Paint> geçirme olay işleyicisi `e` olarak <xref:System.Windows.Forms.PaintEventArgs>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](using-a-pen-to-draw-lines-and-shapes.md)
