---
title: 'Nasıl yapılır: Görüntü renklerini çevirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], changing colors
- images [Windows Forms], changing colors
- image colors [Windows Forms]
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
ms.openlocfilehash: 81aecddb28903649ff2d59e80fc90368df5e2db4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703029"
---
# <a name="how-to-translate-image-colors"></a>Nasıl yapılır: Görüntü renklerini çevirme
Bir çeviri, bir veya daha fazla dört renk bileşeni için bir değer ekler. Çevirileri temsil eden renk matrisi girişleri aşağıdaki tabloda verilmiştir.  
  
|Çevrilecek bileşeni|Matris giriş|  
|--------------------------------|------------------|  
|Kırmızı|[4][0]|  
|Yeşil|[4][1]|  
|Mavi|[4][2]|  
|Alpha|[4][3]|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> ColorBars.bmp dosyasından nesnesi. Ardından kod 0,75 görüntüde her pikselin kırmızı bileşeni ekler. Özgün resmin dönüştürülmüş görüntünün yanı sıra çizilir.  
  
 Aşağıdaki çizimde, sol taraftaki özgün görüntü ve dönüştürülen görüntü sağ tarafta gösterir.  
  
 ![Renklerini çevirme](./media/colortrans2.png "colortrans2")  
  
 Aşağıdaki tabloda dört Çubuklar için rengi vektörleri önce ve sonra kırmızı çeviri listeler. Renk bileşeni için maksimum değeri 1 olduğundan, kırmızı bileşeni ikinci satıra değil değiştiğine dikkat edin. (Benzer şekilde, bir renk bileşeni için en düşük değer 0'dır.)  
  
|Özgün|Çevrilmiş|  
|--------------|----------------|  
|Siyah (0, 0, 0, 1)|(0.75, 0, 0, 1)|  
|Kırmızı (1, 0, 0, 1)|(1, 0, 0, 1)|  
|Yeşil (0, 1, 0, 1)|(0.75, 1, 0, 1)|  
|Mavi (0, 0, 1, 1)|(0.75, 0, 1, 1)|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi. Değiştirin `ColorBars.bmp` bir resim dosyası adı ve sisteminize göre geçerli yolu.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Görüntüleri Yeniden Renklendirme](recoloring-images.md)
