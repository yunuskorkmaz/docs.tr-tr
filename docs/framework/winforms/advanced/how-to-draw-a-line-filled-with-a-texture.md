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
ms.openlocfilehash: 1895c752340d8d764205b5a32b9af0861303841a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a>Nasıl yapılır: Bir Dokuyla Doldurulmuş Çizgi Çizme
Düz renk ile bir satır çizim yerine bir doku ile bir çizgi çizebilirsiniz. Çizgiler ve eğrilerle bir doku ile çizmek için oluşturma bir <xref:System.Drawing.TextureBrush> nesne ve, geçirin <xref:System.Drawing.TextureBrush> nesnesine bir <xref:System.Drawing.Pen.%23ctor%2A> Oluşturucusu. Çizgi veya eğri kalem çizer, kalem vuruşun döşeli doku belirli piksel ortaya çıkardığı ve doku fırça ile ilişkili bit eşlem düzlemi (görünmez) döşeme için kullanılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Drawing.Bitmap> dosyasından nesnesi `Texture1.jpg`. Bu bit eşlem oluşturmak için kullanılan bir <xref:System.Drawing.TextureBrush> nesnesi ve <xref:System.Drawing.TextureBrush> nesnesi oluşturmak için kullanılan bir <xref:System.Drawing.Pen> nesnesi. Çağrı <xref:System.Drawing.Graphics.DrawImage%2A> , sol üst köşede bit eşlem çizer (0, 0). Çağrı <xref:System.Drawing.Graphics.DrawEllipse%2A> kullanan <xref:System.Drawing.Pen> doku Elips çizmek için nesne.  
  
 Aşağıdaki çizimde, bit eşlem ve doku elips gösterir.  
  
 ![Kalemler](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")  
  
 [!code-csharp[System.Drawing.UsingAPen#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bir Windows formu oluşturma ve form ele <xref:System.Windows.Forms.Control.Paint> olay. Önceki kod içine yapıştırma <xref:System.Windows.Forms.Control.Paint> olay işleyicisi. Değiştir `Texture.jpg` , sisteminizde geçerli bir görüntü ile.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [Windows Forms’da Grafikler ve Çizim](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
