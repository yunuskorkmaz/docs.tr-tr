---
title: 'Nasıl yapılır: Bir dokuyla doldurulmuş çizgi çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], texture
- drawing lines [Windows Forms], texture
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
ms.openlocfilehash: 82fc553e2a2fc9d1e8161c0f0dfef9190668e48c
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653762"
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a>Nasıl yapılır: Bir dokuyla doldurulmuş çizgi çizme
Düz renk ile bir çizgiyi çizmek yerine, bir çizgi bir doku ile çizebilirsiniz. Çizgiler ve eğrilerle bir doku ile çizmek için oluşturma bir <xref:System.Drawing.TextureBrush> nesne ve, geçmesi <xref:System.Drawing.TextureBrush> nesnesini bir <xref:System.Drawing.Pen.%23ctor%2A> Oluşturucusu. Doku fırça ile ilişkili bit eşlem düzlem (görünmez) döşeme için kullanılır ve Kalem bir çizgi veya eğri çizdiğinde kalemin vuruş belirli piksel döşenmiş doku açıklığa kavuşturur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, oluşturur bir <xref:System.Drawing.Bitmap> dosyasından nesnesi `Texture1.jpg`. Bit eşlem oluşturmak için kullanılan bir <xref:System.Drawing.TextureBrush> nesnesi ve <xref:System.Drawing.TextureBrush> nesne oluşturmak için kullanılan bir <xref:System.Drawing.Pen> nesne. Çağrı <xref:System.Drawing.Graphics.DrawImage%2A> bit eşlem ile sol üst köşede çizer (0, 0). Çağrı <xref:System.Drawing.Graphics.DrawEllipse%2A> kullanan <xref:System.Drawing.Pen> nesne dokulu bir elips çizin.  
  
 Bit eşlem ve dokulu elips aşağıda gösterilmiştir:  
  
 ![Bit eşlem ve dokulu elips gösteren ekran görüntüsü.](./media/how-to-draw-a-line-filled-with-a-texture/bitmap-textured-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingAPen#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bir Windows formu oluşturma ve form ele <xref:System.Windows.Forms.Control.Paint> olay. Önceki kodun içine yapıştırın <xref:System.Windows.Forms.Control.Paint> olay işleyicisi. Değiştirin `Texture.jpg` sisteminize göre geçerli görüntü ile.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](using-a-pen-to-draw-lines-and-shapes.md)
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
