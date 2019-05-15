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
ms.openlocfilehash: b390caf644b86de0001387b2c3f41503fd34759a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593202"
---
# <a name="how-to-shear-colors"></a>Nasıl yapılır: Renkleri Bükme
Yamultma artırır veya bir renk bileşeni için başka bir renk bileşeni orantılı bir miktar azaltır. Örneğin, kırmızı bileşeni mavi bileşeni değeriyle yarısı burada artırılır dönüştürmeyi göz önünde bulundurun. Bu tür bir dönüştürme altında (0.2, 0,5, 1) rengi (0,7, 0,5, 1) olacak. Yeni kırmızı 0.2 bileşendir + (1/2)(1) 0,7 =.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> ColorBars4.bmp dosyasından nesnesi. Ardından kod, resimdeki her piksele önceki paragrafta açıklanan kesme dönüşümü uygular.  
  
 Aşağıdaki resimde, sağ tarafta sol taraftaki özgün görüntü ve yamultulmuş görüntü gösterilmektedir: 
  
 ![İki kare renkli şeritler-özgün görüntü ve yamultulmuş görüntüyü gösteren yan ile.](./media/how-to-shear-colors/original-image-sheared-image.png)  
  
 Aşağıdaki tabloda önceki ve sonraki kesme dönüşümü dört Çubuklar için rengi vektörleri listeler.  
  
|Özgün|Yamulttuysanız|  
|--------------|-------------|  
|(0, 0, 1, 1)|(0.5, 0, 1, 1)|  
|(0.5, 1, 0.5, 1)|(0.75, 1, 0.5, 1)|  
|(1, 1, 0, 1)|(1, 1, 0, 1)|  
|(0.4, 0.4, 0.4, 1)|(0.6, 0.4, 0.4, 1)|  
  
 [!code-csharp[System.Drawing.Misc3#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi. Değiştirin `ColorBars.bmp` bir görüntü adı ve yolu sisteminize göre geçerli.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Görüntüleri Yeniden Renklendirme](recoloring-images.md)
