---
title: 'Nasıl yapılır: Renkleri Döndürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
ms.openlocfilehash: 258ef9cd5eb8d569b2982614e3087df730a18c57
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522401"
---
# <a name="how-to-rotate-colors"></a>Nasıl yapılır: Renkleri Döndürme
Four-dimensional renk alanını dönüş görselleştirmek zordur. Biz, sabit renk bileşenlerden biri tutmak kabul ettiğinizi belirten tarafından döndürme görselleştirmek kolaylaştırabilir. 1'den sabit alfa bileşeni (tamamıyla opak) tutmak kabul varsayalım. Sonra şu üç boyutlu renk alanını kırmızı, yeşil ve mavi eksenli aşağıdaki çizimde gösterildiği gibi görselleştirebilirsiniz.  
  
 ![Yeniden renklendirme](../../../../docs/framework/winforms/advanced/media/recoloring03.gif "recoloring03")  
  
 Bir renk, 3B nokta olarak düşünülebilir. Örneğin, kırmızı renk alanı noktasında (1, 0, 0) gösteren ve noktasını (0, 1, 0) alanı yeşil rengi temsil eder.  
  
 Aşağıdaki çizimde, 60 derece kırmızı yeşil düzlemi cinsinden açı aracılığıyla renk (1, 0, 0) döndürmek ne anlama geldiğini gösterir. Düzlemi paralel kırmızı yeşil düzlem olarak döndürme, mavi ekseni etrafında döndürme olarak düşünülebilir.  
  
 ![Yeniden renklendirme](../../../../docs/framework/winforms/advanced/media/recoloring04.gif "recoloring04")  
  
 Aşağıdaki çizimde, her üç koordinat eksen (kırmızı, yeşil, mavi) hakkında döndürmeleri gerçekleştirmek için renk matrisi başlatmak gösterilmiştir.  
  
 ![Yeniden renklendirme](../../../../docs/framework/winforms/advanced/media/recoloring05.gif "recoloring05")  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm bir renk (1, 0, 0,6) ve mavi ekseni etrafında 60 derecelik döndürme geçerlidir bir görüntü alır. Döndürme açısını çıkışı kırmızı yeşil düzlemi paralel bir düzlem olarak gözden geçirilmiştir.  
  
 Aşağıdaki çizimde, sol ve sağ taraftaki renk Döndürülmüş görüntü özgün görüntüsüne gösterir.  
  
 ![Renkleri döndürme](../../../../docs/framework/winforms/advanced/media/colortrans5.png "colortrans5")  
  
 Aşağıdaki kodda gerçekleştirilen renk döndürme görselleştirme aşağıda gösterilmektedir.  
  
 ![Yeniden renklendirme](../../../../docs/framework/winforms/advanced/media/recoloring06.gif "recoloring06")  
  
 [!code-csharp[System.Drawing.RotateColors#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi. Değiştir `RotationInput.bmp` bir görüntü dosyası adı ve yolu, sisteminizde geçerli sahip.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Windows Forms’da Grafikler ve Çizim](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Görüntüleri Yeniden Renklendirme](../../../../docs/framework/winforms/advanced/recoloring-images.md)
