---
title: 'Nasıl yapılır: Yeniden renk eşleme tablosu kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- color tables [Windows Forms], remapping colors with
- custom colors [Windows Forms], creating with color remap table
- color remap tables [Windows Forms], using
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
ms.openlocfilehash: 06a25179a3afc004029972bbf7d4d5691d42b25b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683917"
---
# <a name="how-to-use-a-color-remap-table"></a>Nasıl yapılır: Yeniden renk eşleme tablosu kullanma
Yeniden eşleme yeniden renk eşleme tablosu göre görüntü renkleri dönüştürme işlemidir. Renk eşleme tablosu dizisidir <xref:System.Drawing.Imaging.ColorMap> nesneleri. Her <xref:System.Drawing.Imaging.ColorMap> dizi nesnesinde bir <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> özelliği ve <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> özelliği.  
  
 Zaman [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] çizer görüntü, her pikselin görüntünün bir diziye eski renk karşılaştırılır. Bir pikselin renk eski bir renk eşleşiyorsa rengini karşılık gelen yeni renge değişir. Renkleri işleme için yalnızca değiştirilen — görüntünün renk değerleri (depolanan bir <xref:System.Drawing.Image> veya <xref:System.Drawing.Bitmap> nesnesi) değiştirilmez.  
  
 Remapped resim çizmek için bir dizi başlatma <xref:System.Drawing.Imaging.ColorMap> nesneleri. Bu dizi için geçirmek <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> yöntemi bir <xref:System.Drawing.Imaging.ImageAttributes> nesnesi ve ardından geçirmek <xref:System.Drawing.Imaging.ImageAttributes> nesnesini <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi bir <xref:System.Drawing.Graphics> nesne.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, oluşturur bir <xref:System.Drawing.Image> RemapInput.bmp dosyasından nesnesi. Kod bir tek oluşur yeniden renk eşleme tablosu oluşturur <xref:System.Drawing.Imaging.ColorMap> nesne. <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> Özelliği `ColorRemap` nesnedir kırmızı ve <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> özelliktir mavi. Yeniden eşleme ile yeniden eşleme olmadan çizilmiş bir kez de görüntüsüdür. Yeniden eşleme işlemi, mavi ve kırmızı tüm pikselleri değiştirir.  
  
 Aşağıdaki çizimde, sol taraftaki özgün görüntü ve remapped görüntü sağ tarafta gösterir.  
  
 ![Renk eşleme](../../../../docs/framework/winforms/advanced/media/colortrans7.png "colortrans7")  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Görüntüleri Yeniden Renklendirme](../../../../docs/framework/winforms/advanced/recoloring-images.md)
- [Görüntüler, Bit Eşlemler ve Meta Dosyaları](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
