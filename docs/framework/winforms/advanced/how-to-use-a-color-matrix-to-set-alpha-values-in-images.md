---
title: 'Nasıl yapılır: Görüntülerdeki alfa değerleri ayarlamak için renk matrisi kullanma'
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
ms.openlocfilehash: 9e102f51d00953d05ed1d217a345e32178676ffe
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716341"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a>Nasıl yapılır: Görüntülerdeki alfa değerleri ayarlamak için renk matrisi kullanma
<xref:System.Drawing.Bitmap> Sınıfı (işlevinden devralan <xref:System.Drawing.Image> sınıfı) ve <xref:System.Drawing.Imaging.ImageAttributes> sınıfı piksel değerleri ayarlama ve alma işlevselliği sağlar. Kullanabileceğiniz <xref:System.Drawing.Imaging.ImageAttributes> alfa değiştirmek için sınıf için görüntünün değerleri veya çağırabilirsiniz <xref:System.Drawing.Bitmap.SetPixel%2A> yöntemi <xref:System.Drawing.Bitmap> bağımsız piksel değerlerini değiştirmek için sınıf.  
  
## <a name="example"></a>Örnek  
 <xref:System.Drawing.Imaging.ImageAttributes> Sınıfı görüntüleri işleme sırasında değiştirmek için kullanabileceğiniz birçok özellik vardır. Aşağıdaki örnekte, bir <xref:System.Drawing.Imaging.ImageAttributes> nesnesi 80 ne oldukları, yüzde olarak tüm alfa değerleri ayarlamak için kullanılır. Bu renk matrisi başlatma ve Alfa değerini 0,8 matrise ölçeklendirme ayarı tarafından gerçekleştirilir. Renk Matrisi adresini geçirilir <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> yöntemi <xref:System.Drawing.Imaging.ImageAttributes> nesnesi ve <xref:System.Drawing.Imaging.ImageAttributes> nesnesi <xref:System.Drawing.Graphics.DrawString%2A> yöntemi <xref:System.Drawing.Graphics> nesne.  
  
 İşleme sırasında bit eşlem alfa değerleri 80 ne oldukları, yüzde olarak dönüştürülür. Bu, bir arka plan ile karışık bir görüntü sonuçlanır. Aşağıdaki çizimde gösterildiği gibi bit eşlem resmi saydam arar; düz siyah bir çizgi geçen görebilirsiniz.  
  
 ![Alfa karıştırma kullanarak bir matrise](./media/image2.png "image2")  
  
 Görüntü, arka plan üzerinde beyaz kısmında olduğunda, görüntü beyaz ile karışık. Burada siyah bir çizgi görüntü aştığında görüntü rengi siyah harmanlanan.  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Çizgi ve Dolgularda Alfa Karışım Kullanma](alpha-blending-lines-and-fills.md)
