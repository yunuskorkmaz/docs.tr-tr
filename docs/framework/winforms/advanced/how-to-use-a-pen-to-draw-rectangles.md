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
ms.openlocfilehash: 2441687cb36d0780b7fbc935c5cb0edc74bc6ba0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712181"
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a>Nasıl yapılır: Dikdörtgen çizmek için kalem kullanma
Dikdörtgen çizmek için ihtiyacınız bir <xref:System.Drawing.Graphics> nesnesi ve bir <xref:System.Drawing.Pen> nesne. <xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi ve <xref:System.Drawing.Pen> nesne satır, renk ve genişlik gibi özellikleri depolar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sol üst köşesinde bir dikdörtgen çizer (10, 10). Dikdörtgenin genişliği 100 ve 50 yüksekliğini sahiptir. Geçirilen ikinci bağımsız değişken <xref:System.Drawing.Pen.%23ctor%2A> Oluşturucusu kalem genişliği 5 pikselden olduğunu gösterir.  
  
 Dikdörtgen çizildiğinde kalem dikdörtgenin sınırında ortalanır. Kalem genişliği 5 olduğundan, dikdörtgen tarafının çizilen 5 piksel olan geniş, bu tür, 1 piksel artımlı çizilir sınırında kendisi, 2 piksel iç çizilir. ve 2 piksel dışarıda çizilmiştir. Kalem hizalamayı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Kalem genişliği ve hizalamasını ayarlama](how-to-set-pen-width-and-alignment.md).  
  
 Aşağıdaki çizimde, sonuçta elde edilen dikdörtgen gösterir. Kalem genişliği bir piksel olsaydı burada dikdörtgen Çekildi noktalı satırları gösterir. Kalın siyah satırları bu noktalı satırlarda ortalanır dikdörtgenin sol üst köşesinin genişletilmiş görünümünü gösterir.  
  
 ![Kalemler](./media/pens1.gif "pens1")  
  
 [!code-csharp[System.Drawing.UsingAPen#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](using-a-pen-to-draw-lines-and-shapes.md)
