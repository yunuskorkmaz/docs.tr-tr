---
title: 'Nasıl yapılır: Görüntülerdeki Alfa Değerleri Ayarlamak için Renk Matrisi Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using color matrices for semi-transparent
- transparency [Windows Forms], color matrices
- matrices [Windows Forms], alpha values
- bitmaps [Windows Forms], using color matrices for semi-transparent
ms.assetid: a27121e6-f7e9-4c09-84e2-f05aa9d2a1bb
ms.openlocfilehash: 73e820845d040856a0ae367da8b9371ad6afa142
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423730"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a>Nasıl yapılır: Görüntülerdeki Alfa Değerleri Ayarlamak için Renk Matrisi Kullanma
<xref:System.Drawing.Bitmap> sınıfı (<xref:System.Drawing.Image> sınıfından devralan) ve <xref:System.Drawing.Imaging.ImageAttributes> sınıfı, piksel değerlerini almak ve ayarlamak için işlevsellik sağlar. Tüm görüntünün Alfa değerlerini değiştirmek için <xref:System.Drawing.Imaging.ImageAttributes> sınıfını kullanabilir veya tek tek piksel değerlerini değiştirmek için <xref:System.Drawing.Bitmap> sınıfının <xref:System.Drawing.Bitmap.SetPixel%2A> yöntemini çağırabilirsiniz.  
  
## <a name="example"></a>Örnek  
 <xref:System.Drawing.Imaging.ImageAttributes> sınıfı, işleme sırasında görüntüleri değiştirmek için kullanabileceğiniz birçok özelliğe sahiptir. Aşağıdaki örnekte, bir <xref:System.Drawing.Imaging.ImageAttributes> nesnesi, tüm Alfa değerlerini ne gibi bir yüzde 80 ' e ayarlamak için kullanılır. Bu, bir renk matrisi başlatarak ve Matristeki Alfa ölçekleme değeri 0,8 olarak ayarlanarak yapılır. Renk matrisinin adresi <xref:System.Drawing.Imaging.ImageAttributes> nesnesinin <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> yöntemine geçirilir ve <xref:System.Drawing.Imaging.ImageAttributes> nesnesi <xref:System.Drawing.Graphics> nesnesinin <xref:System.Drawing.Graphics.DrawString%2A> yöntemine geçirilir.  
  
 Oluşturma sırasında, bit eşlemdeki alfa değerleri, ne olduğu konusunda yüzde 80 ' e dönüştürülür. Bu, arka planla karışan bir görüntüyle sonuçlanır. Aşağıdaki çizimde gösterildiği gibi, bit eşlem görüntüsü saydam görünüyor; düz siyah çizgiyi onunla görebilirsiniz.  
  
 ![Matris kullanan Alfa karıştırma ekran görüntüsü.](./media/how-to-use-a-color-matrix-to-set-alpha-values-in-images/alpha-blending-matrix.png "image2")  
  
 Görüntünün arka planın beyaz kısmının üzerinde olduğu yerlerde görüntü beyaz renkle karışmıştır. Görüntüde siyah çizgi kesiştiği yerde görüntü siyah renkle karıştırıyor.  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnek, Windows Forms kullanımı için tasarlanmıştır ve <xref:System.Windows.Forms.PaintEventHandler>parametresi olan <xref:System.Windows.Forms.PaintEventArgs> `e`gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Çizgi ve Dolgularda Alfa Karışım Kullanma](alpha-blending-lines-and-fills.md)
