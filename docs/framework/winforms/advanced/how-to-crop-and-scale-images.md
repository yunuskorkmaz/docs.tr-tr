---
title: 'Nasıl yapılır: Görüntü kırpma ve ölçeklendirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
ms.openlocfilehash: 1f6d721edc4f889c2da8ece63f262c7fb55192bd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707706"
---
# <a name="how-to-crop-and-scale-images"></a>Nasıl yapılır: Görüntü kırpma ve ölçeklendirme
<xref:System.Drawing.Graphics> Sınıfı sağlayan çeşitli <xref:System.Drawing.Graphics.DrawImage%2A> bazıları kırpma ve ölçeklendirme görüntüleri için kullanabileceğiniz kaynak ve hedef dikdörtgenin parametreleri olan yöntemleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> disk dosyasından Apple.gif nesnesi. Kod, tüm apple görüntünün özgün boyutunda çizer. Ardından kod çağırır <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi bir <xref:System.Drawing.Graphics> orijinal apple görüntüden daha büyük bir hedef dikdörtgenin içindeki bir kısmını apple görüntüsü çizmek için nesne.  
  
 <xref:System.Drawing.Graphics.DrawImage%2A> Yöntemi tarafından üçüncü, dördüncü, belirtilen kaynak dikdörtgene beşinci ve altıncı bağımsız değişkenler bakarak çizmek için apple hangi kısmının belirler. Bu durumda, apple yüzde 75'genişliğinin ve yüksekliğinin yüzde 75'kırpılır.  
  
 <xref:System.Drawing.Graphics.DrawImage%2A> Yöntemi belirler kırpılmış apple nerede ve ne kadar büyük hedef dikdörtgene bakarak kırpılmış apple yapmak için bu değer ikinci bağımsız değişkeni tarafından belirtilen. Bu durumda, hedef dikdörtgenin yüzde 30 daha geniş ve özgün resimden uzun yüzde 30 ' dir.  
  
 Apple kırpılmış orijinal apple ve genişletilmiş, aşağıdaki çizimde gösterilmektedir.  
  
 ![Kırpma ve ölçeklendirme](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi. Değiştirdiğinizden emin olun `Apple.gif` bir resim dosyası adı ve sisteminize göre geçerli yolu.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Görüntüler, Bit Eşlemler ve Meta Dosyaları](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
- [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
