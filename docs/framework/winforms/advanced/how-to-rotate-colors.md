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
ms.openlocfilehash: 241d2824fc2d87a0505eb6e790c865bfa7d8ef90
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967378"
---
# <a name="how-to-rotate-colors"></a>Nasıl yapılır: Renkleri Döndürme
Four-dimensional renk alanı dönüş görselleştirmek zordur. Biz, renk bileşenlerinden sabit tutmak kabul ederek döndürme görselleştirmek kolaylaştırabilir. 1 sabit alfa bileşeni (tam opak) tutun kabul varsayalım. Ardından şu üç boyutlu renk alanı kırmızı, yeşil ve mavi eksenli aşağıdaki çizimde gösterildiği gibi görselleştirebilirsiniz.  
  
 ![Kırmızı, yeşil ve mavi eksenli döndürme gösteren şekil.](./media/how-to-rotate-colors/rotation-red-green-blue-axes.gif)  
  
 Bir renk, 3B nokta olarak düşünülebilir. Örneğin, kırmızı renk alanı noktasında (1, 0, 0) temsil eder ve yeşil renk alanı noktasında (0, 1, 0) temsil eder.  
  
 Aşağıdaki çizimde, kırmızı-yeşil masasında 60 derecenin açı aracılığıyla rengi (1, 0, 0) döndürme ne demek gösterir. Döndürme düzlemin paralel kırmızı-yeşil düzlemine, döndürme ise mavi eksen olarak düşünülebilir.  
  
 ![Çizim hakkında mavi ekseni döndürme gösterir.](./media/how-to-rotate-colors/rotation-about-blue-axis.gif)  
  
 Aşağıdaki çizimde, her üç koordinat ekseni (kırmızı, yeşil, mavi) hakkında dönüşümüne gerçekleştirmek için renk matrisi başlatmak gösterilmektedir:  
  
 ![Üç eksen hakkında dönüşümüne gerçekleştirmek için renk matrisi başlatın.](./media/how-to-rotate-colors/rotation-about-three-axes.gif)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm bir renk (1, 0, 0,6) ve mavi eksen hakkında bir 60 derece döndürme uygular bir görüntü alır. Döndürme açısı kullanıma kırmızı-yeşil düzlem için paralel bir masasında gözden geçirilmiştir.  
  
 Aşağıdaki çizimde, özgün resmin sol ve sağ taraftaki renk Döndürülmüş görüntü gösterir:  
  
 ![Özgün resmin ve resim rengi Döndürülmüş gösteren şekil.](./media/how-to-rotate-colors/original-color-rotated-images.png)  
  
 Aşağıdaki kodda gerçekleştirilen renk döndürme bir görselleştirme aşağıda gösterilmiştir:
  
 ![Renk döndürme görselleştirmesini gösteren şekil.](./media/how-to-rotate-colors/visualization-color-rotation.gif)  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi. Değiştirin `RotationInput.bmp` bir resim dosyası adı ve yolu sisteminize göre geçerli.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Görüntüleri Yeniden Renklendirme](recoloring-images.md)
