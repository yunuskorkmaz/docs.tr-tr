---
title: 'Nasıl yapılır: Dikey Metin Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- Windows Forms, drawing vertical text
- strings [Windows Forms], drawing vertical
- vertical text [Windows Forms], drawing
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
ms.openlocfilehash: 86401342625f593945b801f7619ef9ca9681317c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182556"
---
# <a name="how-to-create-vertical-text"></a>Nasıl yapılır: Dikey Metin Oluşturma
Bir <xref:System.Drawing.StringFormat> nesneyi, metnin yatay değil dikey olarak çizildiğini belirtmek için kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, değeri <xref:System.Drawing.StringFormatFlags.DirectionVertical> bir <xref:System.Drawing.StringFormat.FormatFlags%2A> <xref:System.Drawing.StringFormat> nesnenin özelliğine atar. Bu <xref:System.Drawing.StringFormat> nesne <xref:System.Drawing.Graphics> sınıfın <xref:System.Drawing.Graphics.DrawString%2A> yöntemine geçirilir. Değer <xref:System.Drawing.StringFormatFlags.DirectionVertical> numaralandırmanın <xref:System.Drawing.StringFormatFlags> bir üyesidir.  
  
 Aşağıdaki resimde dikey metin gösterilmektedir:
  
 ![Dikey yazı tipi metnini gösteren grafik.](./media/how-to-create-vertical-text/vertical-font-text-graphic.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Önceki örnek Windows Formlar ile kullanılmak üzere <xref:System.Windows.Forms.PaintEventArgs> `e` tasarlanmıştır ve gerektirir , <xref:System.Windows.Forms.PaintEventHandler>hangi bir parametre .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: GDI ile Metin Çizme](how-to-draw-text-with-gdi.md)
