---
title: 'Nasıl yapılır: Dikdörtgen çizmek için kalem kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- rectangles [Windows Forms], drawing
- pens [Windows Forms], drawing rectangles
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
ms.openlocfilehash: a29cae5a360185b7fa5e70fc0181c0cfaac8fc09
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463195"
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a>Nasıl yapılır: Dikdörtgen çizmek için kalem kullanma
Dikdörtgen çizmek için ihtiyacınız bir <xref:System.Drawing.Graphics> nesnesi ve bir <xref:System.Drawing.Pen> nesne. <xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi ve <xref:System.Drawing.Pen> nesne satır, renk ve genişlik gibi özellikleri depolar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sol üst köşesinde bir dikdörtgen çizer (10, 10). Dikdörtgenin genişliği 100 ve 50 yüksekliğini sahiptir. Geçirilen ikinci bağımsız değişken <xref:System.Drawing.Pen.%23ctor%2A> Oluşturucusu kalem genişliği 5 pikselden olduğunu gösterir.  
  
 Dikdörtgen çizildiğinde kalem dikdörtgenin sınırında ortalanır. Kalem genişliği 5 olduğundan, dikdörtgen tarafının çizilen 5 piksel olan geniş, bu tür, 1 piksel artımlı çizilir sınırında kendisi, 2 piksel iç çizilir. ve 2 piksel dışarıda çizilmiştir. Kalem hizalamayı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Kalem genişliği ve hizalamasını ayarlama](how-to-set-pen-width-and-alignment.md).  
  
 Aşağıdaki çizimde, sonuçta elde edilen dikdörtgen gösterir. Kalem genişliği bir piksel olsaydı burada dikdörtgen Çekildi noktalı satırları gösterir. Kalın siyah satırları bu noktalı satırlarda ortalanır dikdörtgenin sol üst köşesinin genişletilmiş görünümünü gösterir.  
  
 ![Siyah ve noktalı çizgiler ile çizilen dikdörtgen gösteren ekran görüntüsü.](./media/how-to-use-a-pen-to-draw-rectangles/drawn-rectangle-black-lines-dotted-lines.gif)  
  
 [!code-csharp[System.Drawing.UsingAPen#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](using-a-pen-to-draw-lines-and-shapes.md)
