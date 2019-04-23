---
title: 'Nasıl yapılır: Ekrana Mevcut bir Bit Eşlemi Çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], displaying in Windows Forms
- bitmaps [Windows Forms], loading in Windows Forms applications
- images [Windows Forms], displaying on Windows Forms
ms.assetid: 5bc558d7-b326-4050-a834-b8600da0de95
ms.openlocfilehash: 90511adf9caffe7952e270d6fe32dd85162a29d7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089185"
---
# <a name="how-to-draw-an-existing-bitmap-to-the-screen"></a>Nasıl yapılır: Ekrana Mevcut bir Bit Eşlemi Çizme
Bu gibi durumlarda, mevcut bir görüntüyü kolayca ekranda çizebilirsiniz. İlk oluşturmak gereken bir <xref:System.Drawing.Bitmap> nesnesi alan bir dosya adı, bit eşlem Oluşturucu <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>. Bu oluşturucu, BMP, GIF, JPEG, PNG ve TIFF gibi birçok farklı dosya biçimleri görüntülerle kabul eder. Oluşturduktan sonra <xref:System.Drawing.Bitmap> nesne, bu geçirmek <xref:System.Drawing.Bitmap> nesnesini <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi bir <xref:System.Drawing.Graphics> nesne.  
  
## <a name="example"></a>Örnek  
 Bu örnekte bir <xref:System.Drawing.Bitmap> nesneden bir JPEG dosyası ve daha sonra sol üst köşede ile bit eşlem çizer (60, 10).  
  
 Belirtilen konumda çizilmiş bit eşlem aşağıda gösterilmiştir:  
  
 ![Belirtilen konumda bir görüntü gösteren ekran görüntüsü.](./media/how-to-draw-an-existing-bitmap-to-the-screen/bitmap-specified-position.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](working-with-images-bitmaps-icons-and-metafiles.md)
