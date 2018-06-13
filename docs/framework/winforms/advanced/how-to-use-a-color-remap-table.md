---
title: 'Nasıl yapılır: Yeniden Renk Eşleme Tablosu Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- color tables [Windows Forms], remapping colors with
- custom colors [Windows Forms], creating with color remap table
- color remap tables [Windows Forms], using
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
ms.openlocfilehash: ba763cc7960e71c6fc705d40eefdbde163d06181
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522479"
---
# <a name="how-to-use-a-color-remap-table"></a>Nasıl yapılır: Yeniden Renk Eşleme Tablosu Kullanma
Yeniden eşleme yeniden renk eşleme tablosu göre görüntüdeki renkleri dönüştürme işlemidir. Renk eşleme tablosu dizisidir <xref:System.Drawing.Imaging.ColorMap> nesneleri. Her <xref:System.Drawing.Imaging.ColorMap> dizi nesnesi bir <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> özelliği ve <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> özelliği.  
  
 Zaman [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] çizer resim, resmin her piksel bir eski renkleri dizisi karşılaştırılan. Bir piksel renk eski bir renk eşleşirse, rengini karşılık gelen yeni renge değiştirilir. Renkleri işleme için yalnızca değiştirilen — görüntü renk değerlerini (depolanan bir <xref:System.Drawing.Image> veya <xref:System.Drawing.Bitmap> nesnesi) değiştirilmez.  
  
 Remapped resim çizmek için bir dizi başlatma <xref:System.Drawing.Imaging.ColorMap> nesneleri. Bu diziye geçirmek <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> yöntemi bir <xref:System.Drawing.Imaging.ImageAttributes> nesnesini genişletin ve ardından geçirmek <xref:System.Drawing.Imaging.ImageAttributes> nesnesini <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi bir <xref:System.Drawing.Graphics> nesnesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Drawing.Image> RemapInput.bmp dosyasından nesnesi. Kod bir tek oluşur yeniden renk eşleme tablosu oluşturur <xref:System.Drawing.Imaging.ColorMap> nesnesi. <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> Özelliği `ColorRemap` nesne kırmızıdır ve <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> özelliktir mavi. Yeniden eşleme ile yeniden eşleme olmadan çizilmiş bir kez de görüntüdür. Yeniden eşleme işlemi mavi ve kırmızı tüm pikselleri değiştirir.  
  
 Aşağıdaki çizimde özgün resim soldaki ve remapped görüntü sağ tarafta gösterir.  
  
 ![Renk eşleme](../../../../docs/framework/winforms/advanced/media/colortrans7.png "colortrans7")  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görüntüleri Yeniden Renklendirme](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [Görüntüler, Bit Eşlemler ve Meta Dosyaları](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
