---
title: 'Nasıl yapılır: Renkleri Bükme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
ms.openlocfilehash: 825e5a90ebb0d9df3b894ce7bd353e917b676939
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142400"
---
# <a name="how-to-shear-colors"></a>Nasıl yapılır: Renkleri Bükme
Yamultma, bir renk bileşenini başka bir renk bileşeniyle orantılı bir miktar artırır veya azaltır. Örneğin, kırmızı bileşenin mavi bileşenin yarısı kadar artırıldığı dönüşümü göz önünde bulundurun. Böyle bir dönüşüm altında renk (0.2, 0.5, 1) (0.7, 0.5, 1) olur. Yeni kırmızı bileşen 0,2 + (1/2)(1) = 0,7'dir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ColorBars4.bmp dosyasından bir <xref:System.Drawing.Image> nesne oluşturuyor. Ardından kod, önceki paragrafta açıklanan kesme dönüşümünü görüntüdeki her piksele uygular.  
  
 Aşağıdaki resimde soldaki orijinal görüntü ve sağdaki yıkıntılmış görüntü gösterilmektedir:
  
 ![Orijinal görüntüyü ve yıyıkgörüntüyü gösteren renkli çizgili iki kare yan yana.](./media/how-to-shear-colors/original-image-sheared-image.png)  
  
 Aşağıdaki tabloda, kesme dönüşümünden önce ve sonra dört çubuk için renk vektörleri listelenir.  
  
|Özgün|Sheared|  
|--------------|-------------|  
|(0, 0, 1, 1)|(0.5, 0, 1, 1)|  
|(0.5, 1, 0.5, 1)|(0.75, 1, 0.5, 1)|  
|(1, 1, 0, 1)|(1, 1, 0, 1)|  
|(0.4, 0.4, 0.4, 1)|(0.6, 0.4, 0.4, 1)|  
  
 [!code-csharp[System.Drawing.Misc3#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnek, Windows Formları ile kullanılmak üzere <xref:System.Windows.Forms.PaintEventArgs> `e`tasarlanmıştır ve <xref:System.Windows.Forms.Control.Paint> olay işleyicisinin bir parametresi olan , gerektirir. Sisteminizde geçerli bir görüntü adı ve yol ile değiştirin. `ColorBars.bmp`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Görüntüleri Yeniden Renklendirme](recoloring-images.md)
