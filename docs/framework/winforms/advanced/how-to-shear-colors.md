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
ms.openlocfilehash: 204f15ce44d5ad688be0ea9ac0fa4a90781b25dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-shear-colors"></a>Nasıl yapılır: Renkleri Bükme
Yamultma artırır veya başka bir renk bileşenine orantılı bir miktar renk bileşeni azaltır. Örneğin, burada kırmızı bileşenini yarısı değerle mavi bileşeninin artırılır dönüştürme göz önünde bulundurun. Bu tür bir dönüşüm altında rengi (0.2, 0,5, 1) duruma (0,7, 0,5, 1). Yeni kırmızı 0.2 bileşendir + (1/2)(1) 0,7 =.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> ColorBars4.bmp dosyasından nesnesi. Ardından kod görüntüdeki her piksel önceki paragrafta açıklanan kesme dönüştürmesi uygular.  
  
 Aşağıdaki çizimde özgün resim soldaki ve yamultulmuş görüntü sağ tarafta gösterir.  
  
 ![Renkleri bükme](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")  
  
 Aşağıdaki tabloda, önce ve sonra kesme dönüştürme dört Çubuklar için renk vektörlerinin listeler.  
  
|Özgün|Yamultulmuş|  
|--------------|-------------|  
|(0, 0, 1, 1)|(0.5, 0, 1, 1)|  
|(0.5, 1, 0.5, 1)|(0.75, 1, 0.5, 1)|  
|(1, 1, 0, 1)|(1, 1, 0, 1)|  
|(0.4, 0.4, 0.4, 1)|(0.6, 0.4, 0.4, 1)|  
  
 [!code-csharp[System.Drawing.Misc3#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi. Değiştir `ColorBars.bmp` bir görüntü adı ve yolu, sisteminizde geçerli.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Windows Forms’da Grafikler ve Çizim](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Görüntüleri Yeniden Renklendirme](../../../../docs/framework/winforms/advanced/recoloring-images.md)
