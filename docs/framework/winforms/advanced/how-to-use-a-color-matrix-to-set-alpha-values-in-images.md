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
ms.openlocfilehash: ed129cd9487ba1416cd69b2e13f59747856cb598
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522352"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a>Nasıl yapılır: Görüntülerdeki Alfa Değerleri Ayarlamak için Renk Matrisi Kullanma
<xref:System.Drawing.Bitmap> Sınıfı (devralan <xref:System.Drawing.Image> sınıfı) ve <xref:System.Drawing.Imaging.ImageAttributes> sınıfı piksel değerleri ayarlama ve alma için işlevsellik sağlar. Kullanabileceğiniz <xref:System.Drawing.Imaging.ImageAttributes> alfa değiştirmek için sınıf değerleri için tüm görüntü ya da çağırabilirsiniz <xref:System.Drawing.Bitmap.SetPixel%2A> yöntemi <xref:System.Drawing.Bitmap> tek tek piksel değerlerini değiştirmek için sınıf.  
  
## <a name="example"></a>Örnek  
 <xref:System.Drawing.Imaging.ImageAttributes> Sınıfın görüntüleri işleme sırasında değiştirmek için kullanabileceğiniz birçok özelliği vardır. Aşağıdaki örnekte, bir <xref:System.Drawing.Imaging.ImageAttributes> nesnesi ne oldukları, yüzde 80 için tüm alfa değerleri ayarlamak için kullanılır. Bu renk matrisi başlatma ve 0,8 matrise değerinde ölçeklendirme alfa ayarlayarak yapılır. Renk Matrisi adresini geçirilir <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> yöntemi <xref:System.Drawing.Imaging.ImageAttributes> nesnesi ve <xref:System.Drawing.Imaging.ImageAttributes> nesne iletilir <xref:System.Drawing.Graphics.DrawString%2A> yöntemi <xref:System.Drawing.Graphics> nesnesi.  
  
 İşleme sırasında yüzde 80'ne oldukları biri için bit eşlemde alfa değerleri dönüştürülür. Bu, arka plan karıştırılan görüntüyü sonuçlanır. Aşağıdaki çizimde gösterildiği gibi bit eşlem resmin saydam arar; düz siyah bir çizgi geçen görebilirsiniz.  
  
 ![Alfa karıştırma bir matris kullanarak](../../../../docs/framework/winforms/advanced/media/image2.png "image2")  
  
 Görüntü arka planı beyaz bölümü olduğunda, görüntü ile rengi beyaz karıştırılan. Burada görüntü siyah bir çizgi kestiği görüntü rengi siyah karıştırılan.  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms’da Grafikler ve Çizim](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Çizgi ve Dolgularda Alfa Karışım Kullanma](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
