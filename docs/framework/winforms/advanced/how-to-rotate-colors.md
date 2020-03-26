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
ms.openlocfilehash: 8d2717dd7b819e963126072279b361fda02188bc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111341"
---
# <a name="how-to-rotate-colors"></a>Nasıl yapılır: Renkleri Döndürme
Dört boyutlu bir renk alanında döndürmeyi görselleştirmek zordur. Renk bileşenlerinden birini sabit tutmayı kabul ederek döndürmeyi görselleştirmeyi kolaylaştırabiliriz. Alfa bileşenini 1'de sabit tutmayı kabul ettiğimizi varsayalım (tamamen opak). Daha sonra aşağıdaki resimde gösterildiği gibi kırmızı, yeşil ve mavi eksenler ile üç boyutlu bir renk alanı görselleştirebilirsiniz.  
  
 ![Kırmızı, yeşil ve mavi eksenlerle döndürme yi gösteren çizim.](./media/how-to-rotate-colors/rotation-red-green-blue-axes.gif)  
  
 Bir renk 3B alanda bir nokta olarak düşünülebilir. Örneğin, boşluktaki nokta (1, 0, 0) kırmızı rengi, boşluktaki nokta (0, 1, 0) ise yeşil rengi temsil eder.  
  
 Aşağıdaki resimde, kırmızı-yeşil düzlemde 60 derecelik bir açı yla renk (1, 0, 0) döndürmek için ne anlama geldiğini gösterir. Kırmızı-Yeşil düzleme paralel bir düzlemde dönüş mavi eksen etrafında dönüş olarak düşünülebilir.  
  
 ![Mavi eksen hakkında döndürme gösteren çizim.](./media/how-to-rotate-colors/rotation-about-blue-axis.gif)  
  
 Aşağıdaki resimde, üç koordinat ekseninin (kırmızı, yeşil, mavi) her biri hakkında döndürmeler gerçekleştirmek için bir renk matrisinin nasıl başlağize edilebildiğini gösterir:  
  
 ![Üç eksen hakkında döndürmeler gerçekleştirmek için bir renk matrisini başlatma.](./media/how-to-rotate-colors/rotation-about-three-axes.gif)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tek renk (1, 0, 0,6) olan bir görüntü alır ve mavi eksen hakkında 60 derecelik bir döndürme uygular. Dönüş açısı kırmızı-yeşil düzleme paralel bir düzlemde süpürülür.  
  
 Aşağıdaki resimde soldaki orijinal görüntü ve sağdaki renk döndürülmüş görüntü gösterilmektedir:  
  
 ![Orijinal görüntüyü ve renk döndürülen görüntüyü gösteren çizim.](./media/how-to-rotate-colors/original-color-rotated-images.png)  
  
 Aşağıdaki resimde, aşağıdaki kodda gerçekleştirilen renk döndürmenin görselleştirilmesi gösterilmektedir:
  
 ![Renk döndürmenin görselleştirilmesini gösteren çizim.](./media/how-to-rotate-colors/visualization-color-rotation.gif)  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnek, Windows Formları ile kullanılmak üzere <xref:System.Windows.Forms.PaintEventArgs> `e`tasarlanmıştır ve <xref:System.Windows.Forms.Control.Paint> olay işleyicisinin bir parametresi olan , gerektirir. Sisteminizde geçerli bir resim dosyası adı ve yolu ile değiştirin. `RotationInput.bmp`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Görüntüleri Yeniden Renklendirme](recoloring-images.md)
