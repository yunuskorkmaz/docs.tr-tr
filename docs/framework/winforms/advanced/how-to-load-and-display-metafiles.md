---
title: 'Nasıl yapılır: Yük ve görüntü meta dosyaları'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
ms.openlocfilehash: 121f285a95d0169db79bdc302d80dba03b3b40c2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720049"
---
# <a name="how-to-load-and-display-metafiles"></a>Nasıl yapılır: Yük ve görüntü meta dosyaları
<xref:System.Drawing.Imaging.Metafile> Öğesinden devralan sınıf <xref:System.Drawing.Image> sınıfı, kaydı, görüntüleme ve vektör görüntüleri sınamak için yöntemlerini sağlar.  
  
## <a name="example"></a>Örnek  
 Ekranda bir vektör görüntüsü (meta dosyası) için ihtiyacınız bir <xref:System.Drawing.Imaging.Metafile> nesnesi ve bir <xref:System.Drawing.Graphics> nesne. Bir dosya (veya bir akışa) adını geçirin bir <xref:System.Drawing.Imaging.Metafile> Oluşturucusu. Oluşturduktan sonra bir <xref:System.Drawing.Imaging.Metafile> nesne, bu geçirmek <xref:System.Drawing.Imaging.Metafile> nesnesini <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi bir <xref:System.Drawing.Graphics> nesne.  
  
 Örnek bir <xref:System.Drawing.Imaging.Metafile> EMF (Gelişmiş Meta dosyası) dosyasından nesnesi ve ardından, sol üst köşede görüntüsüyle çizer (60, 10).  
  
 Belirtilen konumda çizilmiş meta dosyası aşağıda gösterilmiştir.  
  
 ![Görüntü konumu](./media/imageposition2.png "imageposition2")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](working-with-images-bitmaps-icons-and-metafiles.md)
