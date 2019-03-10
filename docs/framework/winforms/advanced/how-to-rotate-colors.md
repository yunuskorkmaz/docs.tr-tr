---
title: 'Nasıl yapılır: Renkleri döndürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
ms.openlocfilehash: cb3824d8a5a5674b83124301dbfbd5a3ba60effa
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720624"
---
# <a name="how-to-rotate-colors"></a>Nasıl yapılır: Renkleri döndürme
Four-dimensional renk alanı dönüş görselleştirmek zordur. Biz, renk bileşenlerinden sabit tutmak kabul ederek döndürme görselleştirmek kolaylaştırabilir. 1 sabit alfa bileşeni (tam opak) tutun kabul varsayalım. Ardından şu üç boyutlu renk alanı kırmızı, yeşil ve mavi eksenli aşağıdaki çizimde gösterildiği gibi görselleştirebilirsiniz.  
  
 ![Yeniden renklendirme](./media/recoloring03.gif "recoloring03")  
  
 Bir renk, 3B nokta olarak düşünülebilir. Örneğin, kırmızı renk alanı noktasında (1, 0, 0) temsil eder ve yeşil renk alanı noktasında (0, 1, 0) temsil eder.  
  
 Aşağıdaki çizimde, kırmızı-yeşil masasında 60 derecenin açı aracılığıyla rengi (1, 0, 0) döndürme ne demek gösterir. Döndürme düzlemin paralel kırmızı-yeşil düzlemine, döndürme ise mavi eksen olarak düşünülebilir.  
  
 ![Yeniden renklendirme](./media/recoloring04.gif "recoloring04")  
  
 Aşağıdaki çizimde, her üç koordinat ekseni (kırmızı, yeşil, mavi) hakkında dönüşümüne gerçekleştirmek için renk matrisi başlatmak gösterilmektedir.  
  
 ![Yeniden renklendirme](./media/recoloring05.gif "recoloring05")  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm bir renk (1, 0, 0,6) ve mavi eksen hakkında bir 60 derece döndürme uygular bir görüntü alır. Döndürme açısı kullanıma kırmızı-yeşil düzlem için paralel bir masasında gözden geçirilmiştir.  
  
 Aşağıdaki çizim özgün resmin sol ve sağ taraftaki renk Döndürülmüş görüntü gösterir.  
  
 ![Renkleri döndürme](./media/colortrans5.png "colortrans5")  
  
 Aşağıdaki kodda gerçekleştirilen renk döndürme bir görselleştirme aşağıda gösterilmiştir.  
  
 ![Yeniden renklendirme](./media/recoloring06.gif "recoloring06")  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi. Değiştirin `RotationInput.bmp` bir resim dosyası adı ve yolu sisteminize göre geçerli.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Görüntüleri Yeniden Renklendirme](recoloring-images.md)
