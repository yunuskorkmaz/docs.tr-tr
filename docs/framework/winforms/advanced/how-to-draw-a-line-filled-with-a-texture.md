---
title: 'Nasıl yapılır: Bir Dokuyla Doldurulmuş Çizgi Çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], texture
- drawing lines [Windows Forms], texture
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
ms.openlocfilehash: c0f90c298f48aeb96893bb09241faddc08d8a49d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186914"
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a>Nasıl yapılır: Bir Dokuyla Doldurulmuş Çizgi Çizme
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
- [Windows Formlarında Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
