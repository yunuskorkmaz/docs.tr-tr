---
title: 'Nasıl yapılır: Görüntüleri Döndürme, Yansıtma ve Eğme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], reflecting
- images [Windows Forms], rotating
- images [Windows Forms], skewing
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
ms.openlocfilehash: 7f580b4d3016f1ecedc33302fe57caeec5698aeb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-rotate-reflect-and-skew-images"></a>Nasıl yapılır: Görüntüleri Döndürme, Yansıtma ve Eğme
Döndürme, yansıtma ve orijinal görüntünün sol üst, sağ üst ve alt sol köşe için hedef noktalarını belirterek bir görüntü eğme. Üç hedef noktaları bir paralel kenarı özgün dikdörtgen resmin eşleştirir bir afin dönüşümü belirler.  
  
## <a name="example"></a>Örnek  
 Örneğin, özgün resim sol üst köşede bir dikdörtgen olduğunu varsayın (0, 0), sağ üst köşede (100, 0) ve sol alt köşede (0, 50). Bu harita varsayalım artık üç hedef noktalarına gibi işaret eder.  
  
|Özgün noktası|Hedef noktası|  
|--------------------|-----------------------|  
|Sol üst (0, 0)|(200, 20)|  
|Sağ üst köşede (100, 0)|(110, 100)|  
|Sol alt (0, 50)|(250, 30)|  
  
 Aşağıdaki çizimde özgün resim ve paralel kenarı için eşlenen görüntü gösterir. Özgün görüntüsüne eğri, yansıtılan, döndürülmüş, çevrilen ve kapatıldı. Özgün görüntünün üst kenarı eksenindeki çalıştıran aracılığıyla bir satıra eşlendi (200, 20) ve (110, 100). Y ekseni boyunca özgün görüntüsüne sol kenarı çalıştıran aracılığıyla bir satıra eşlendi (200, 20) ve (250, 30).  
  
 ![Şeritler](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")  
  
 Aşağıdaki çizimde bir fotoğraf görüntüye uygulanan benzer bir dönüşüm gösterir.  
  
 ![Dönüştürülen Tırmanıcı](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")  
  
 Aşağıdaki çizimde bir meta dosyası uygulanan benzer bir dönüşüm gösterir.  
  
 ![Dönüştürülen meta dosyası](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")  
  
 Aşağıdaki örnek ilk çizimde gösterilen görüntüleri üretir.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi. Değiştirdiğinizden emin olun `Stripes.bmp` , sisteminizde geçerli bir görüntü yolu ile.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
