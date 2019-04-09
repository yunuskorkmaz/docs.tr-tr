---
title: 'Nasıl yapılır: Görüntü Kırpma ve Ölçeklendirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
ms.openlocfilehash: 4257431881565f9160f45795111d374cc680dedd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189913"
---
# <a name="how-to-crop-and-scale-images"></a>Nasıl yapılır: Görüntü Kırpma ve Ölçeklendirme
<xref:System.Drawing.Graphics> Sınıfı sağlayan çeşitli <xref:System.Drawing.Graphics.DrawImage%2A> bazıları kırpma ve ölçeklendirme görüntüleri için kullanabileceğiniz kaynak ve hedef dikdörtgenin parametreleri olan yöntemleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> disk dosyasından Apple.gif nesnesi. Kod, tüm apple görüntünün özgün boyutunda çizer. Ardından kod çağırır <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi bir <xref:System.Drawing.Graphics> orijinal apple görüntüden daha büyük bir hedef dikdörtgenin içindeki bir kısmını apple görüntüsü çizmek için nesne.  
  
 <xref:System.Drawing.Graphics.DrawImage%2A> Yöntemi tarafından üçüncü, dördüncü, belirtilen kaynak dikdörtgene beşinci ve altıncı bağımsız değişkenler bakarak çizmek için apple hangi kısmının belirler. Bu durumda, apple yüzde 75'genişliğinin ve yüksekliğinin yüzde 75'kırpılır.  
  
 <xref:System.Drawing.Graphics.DrawImage%2A> Yöntemi belirler kırpılmış apple nerede ve ne kadar büyük hedef dikdörtgene bakarak kırpılmış apple yapmak için bu değer ikinci bağımsız değişkeni tarafından belirtilen. Bu durumda, hedef dikdörtgenin yüzde 30 daha geniş ve özgün resimden uzun yüzde 30 ' dir.  
  
 Apple kırpılmış orijinal apple ve genişletilmiş, aşağıdaki çizimde gösterilmektedir.  
  
 ![Özgün görüntü ve kırpılmış görüntünün ekran görüntüsü.](./media/how-to-crop-and-scale-images/original-image-cropped-image.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi. Değiştirdiğinizden emin olun `Apple.gif` bir resim dosyası adı ve sisteminize göre geçerli yolu.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Resimler, Bit Eşlemler ve Meta Dosyaları](images-bitmaps-and-metafiles.md)
- [Resimler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](working-with-images-bitmaps-icons-and-metafiles.md)
