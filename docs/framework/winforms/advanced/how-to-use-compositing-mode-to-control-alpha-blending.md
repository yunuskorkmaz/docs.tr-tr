---
title: 'Nasıl yapılır: Alfa Karışım Kullanmayı Denetlemek için Birleştirme Modunu Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- alpha blending [Windows Forms], compositing
- colors [Windows Forms], blending
- colors [Windows Forms], controlling transparency
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
ms.openlocfilehash: 55c6db1029c6823652ac29fca46f6f8dc4ec40d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527008"
---
# <a name="how-to-use-compositing-mode-to-control-alpha-blending"></a>Nasıl yapılır: Alfa Karışım Kullanmayı Denetlemek için Birleştirme Modunu Kullanma
Aşağıdaki özelliklere sahip bir ekran dışı bitmap oluşturmak istediğinizde zamanlar olabilir:  
  
-   Renkleri 255'den az olan alfa değerleri var.  
  
-   Bit eşlem oluşturma birbiriyle karışık özelliği renkler alfa değildir.  
  
-   Tamamlanan bit eşlem görüntülediğinizde, bit eşlem renkleri görüntüleme cihazı arka plan renkleri ile karıştırılan alfa ' dir.  
  
 Bu tür bir bitmap oluşturmak için boş bir oluşturmak <xref:System.Drawing.Bitmap> nesnesini genişletin ve ardından oluşturmak bir <xref:System.Drawing.Graphics> nesne tabanlı, bit eşlem'i. Birleştirme modunu ayarlama <xref:System.Drawing.Graphics> nesnesine <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Drawing.Graphics> nesne temel alarak bir <xref:System.Drawing.Bitmap> nesnesi. Kod kullanan <xref:System.Drawing.Graphics> iki yarı saydam Fırçalar yanı sıra nesnesi (alfa 160 =) bit eşlem'i boyamak için. Kod bir kırmızı elips ve yarı saydam fırçalarını kullanma yeşil bir elips doldurur. Yeşil elipsin kırmızı elips çakışıyor, ancak yeşil kırmızı ile çünkü karıştırılan değil birleştirme modunu <xref:System.Drawing.Graphics> nesne ayarlanmış <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.  
  
 Ekranda bit eşlem kod iki kez çizer: kez beyaz bir arka plan ve bir kez renkli arka plan üzerinde. Arka plan renklerini ekranında ile üç nokta karıştırılan şekilde iki elips parçası olan bit eşlem pikselleri 160, alfasayısal bir bileşeninin sahip.  
  
 Aşağıdaki çizimde örnek kodu çıktısını gösterir. Üç nokta arka plan karıştırılan, ancak bunlar birbiriyle karışık değil unutmayın.  
  
 ![Kaynağı Kopyala](../../../../docs/framework/winforms/advanced/media/sourcecopy.png "sourcecopy")  
  
 Kod örneği, bu deyimi içerir:  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 Birbirleriyle ve aynı zamanda arka plana sahip karıştırılan için üç nokta istiyorsanız, bu deyimi aşağıdaki gibi değiştirin:  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 Aşağıdaki çizimde düzeltilmiş kod çıktısını gösterir.  
  
 ![Kaynak üzerinde](../../../../docs/framework/winforms/advanced/media/sourceover.png "sourceover")  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Color.FromArgb%2A>  
 [Çizgi ve Dolgularda Alfa Karışım Kullanma](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
