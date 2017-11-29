---
title: "Nasıl yapılır: Görüntü Renklerini Çevirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], changing colors
- images [Windows Forms], changing colors
- image colors [Windows Forms]
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c21d20b631d8e0cf68e370dd43b3f5e92144b09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-translate-image-colors"></a>Nasıl yapılır: Görüntü Renklerini Çevirme
Çeviri bir veya daha fazla dört renk bileşenleri için bir değer ekler. Çeviriler temsil eden renk matrisi girişi aşağıdaki tabloda verilmiştir.  
  
|Çevrilecek bileşeni|Matris giriş|  
|--------------------------------|------------------|  
|kırmızı|[4][0]|  
|Yeşil|[4][1]|  
|Mavi|[4][2]|  
|Alfa|[4][3]|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> ColorBars.bmp dosyasından nesnesi. Ardından kod görüntüdeki her piksel kırmızı bileşeninin 0,75 ekler. Özgün görüntüsüne dönüştürülmüş yansımasının yanında çizilir.  
  
 Aşağıdaki çizimde özgün resim soldaki ve dönüştürülen görüntünün sağ tarafta gösterir.  
  
 ![Renklerini çevirme](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")  
  
 Aşağıdaki tabloda, önce ve sonra kırmızı çeviri dört Çubuklar için renk vektörlerinin listeler. Renk bileşeni için maksimum değeri 1 olduğundan, ikinci satırında kırmızı bileşen değişmeyen olduğunu unutmayın. (Benzer şekilde, bir renk bileşeni için en düşük değer 0'dır.)  
  
|Özgün|Çevrilmiş|  
|--------------|----------------|  
|Siyah (0, 0, 0, 1)|(0.75, 0, 0, 1)|  
|Kırmızı (1, 0, 0, 1)|(1, 0, 0, 1)|  
|Yeşil (0, 1, 0, 1)|(0.75, 1, 0, 1)|  
|Mavi (0, 0, 1, 1)|(0.75, 0, 1, 1)|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi. Değiştir `ColorBars.bmp` bir görüntü dosyası adı ve, sisteminizde geçerli yolu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Grafikler ve Windows Forms'ta çizme](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Görüntüleri yeniden renklendirme](../../../../docs/framework/winforms/advanced/recoloring-images.md)
