---
title: 'Nasıl yapılır: Meta Dosyalarını Yükleme ve Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
ms.openlocfilehash: 6c17e0b2d023ccf80b0d32301b7ee6765edcae9f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424813"
---
# <a name="how-to-load-and-display-metafiles"></a>Nasıl yapılır: Meta Dosyalarını Yükleme ve Görüntüleme
<xref:System.Drawing.Image> sınıfından devralan <xref:System.Drawing.Imaging.Metafile> sınıfı, vektör görüntülerini kaydetme, görüntüleme ve İnceleme için yöntemler sağlar.  
  
## <a name="example"></a>Örnek  
 Ekranda bir vektör görüntüsünü (meta dosyası) göstermek için bir <xref:System.Drawing.Imaging.Metafile> nesnesi ve bir <xref:System.Drawing.Graphics> nesnesi gerekir. Bir dosyanın (veya akışın) adını <xref:System.Drawing.Imaging.Metafile> oluşturucusuna geçirin. Bir <xref:System.Drawing.Imaging.Metafile> nesnesi oluşturduktan sonra, bu <xref:System.Drawing.Imaging.Metafile> nesnesini <xref:System.Drawing.Graphics> nesnesinin <xref:System.Drawing.Graphics.DrawImage%2A> metoduna geçirin.  
  
 Örnek, bir EMF (Gelişmiş Meta dosyası) dosyasından bir <xref:System.Drawing.Imaging.Metafile> nesnesi oluşturur ve sonra görüntüyü sol üst köşesine (60, 10) çizer.  
  
 Aşağıdaki çizimde belirtilen konumda çizilen meta dosya gösterilmektedir.  
  
 ![Görüntü konumunu gösteren ekran görüntüsü.](./media/how-to-load-and-display-metafiles/metafile-drawn-specified-location.png "imageposition2")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnek, Windows Forms kullanımı için tasarlanmıştır ve <xref:System.Windows.Forms.Control.Paint> olay işleyicisinin bir parametresi olan <xref:System.Windows.Forms.PaintEventArgs> `e`gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](working-with-images-bitmaps-icons-and-metafiles.md)
