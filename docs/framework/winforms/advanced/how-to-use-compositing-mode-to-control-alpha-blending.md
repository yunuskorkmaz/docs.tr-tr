---
title: 'Nasıl yapılır: Alfa karışım kullanmayı denetlemek için birleştirme modunu kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- alpha blending [Windows Forms], compositing
- colors [Windows Forms], blending
- colors [Windows Forms], controlling transparency
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
ms.openlocfilehash: 1a5cf23890cd6183d92e33ec4e24f87c226e8ec3
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58462870"
---
# <a name="how-to-use-compositing-mode-to-control-alpha-blending"></a>Nasıl yapılır: Alfa karışım kullanmayı denetlemek için birleştirme modunu kullanma
Aşağıdaki özelliklere sahip çizerek bir bit eşlem oluşturmak istediğiniz zaman zamanlar olabilir:  
  
-   Renkleri 255'den küçük olan alfa değerleri var.  
  
-   Bit eşlem oluşturma gibi birbiriyle karışık özelliği renkler alfa değildir.  
  
-   Tamamlanmış bir bit eşlem görüntülediğinizde, bit eşlemde görüntü cihazı üzerinde arka plan renkleri ile karışık alfa renklerdir.  
  
 Böyle bir bit eşlem oluşturmak için boş bir oluşturmak <xref:System.Drawing.Bitmap> nesnesi ve ardından oluşturmak bir <xref:System.Drawing.Graphics> nesne tabanlı, bit eşlem. Birleştirme modunu ayarlama <xref:System.Drawing.Graphics> nesnesini <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, oluşturur bir <xref:System.Drawing.Graphics> nesnesini temel alan bir <xref:System.Drawing.Bitmap> nesne. Kod <xref:System.Drawing.Graphics> iki yarı saydam fırçalarla Fırçalar yanı sıra nesnesi (alpha 160 =) üzerinde bir bit eşlem boyamak için. Kod, kırmızı bir elips ve yarı saydam fırçalarla fırçalarını kullanma yeşil bir elipsin doldurur. Yeşil elips kırmızı elips çakışıyor, ancak yeşil kırmızı ile çünkü harmanlanan olmayan birleştirme modunu <xref:System.Drawing.Graphics> nesne ayarlandığında <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.  
  
 Ekranda bir bit eşlem kod iki kez çizer: bir kez beyaz arka plan üzerinde ve bir kez renkli arka plan üzerinde. Üç nokta simgesini ekranın arka plan renkleriyle ile karışık şekilde iki üç noktayı parçası olan bit eşlem pikselleri 160, bir alfa bileşeni vardır.  
  
 Kod örneği, çıktı aşağıda gösterilmiştir. Üç nokta arka plan ile karışık, ancak bunlar birbiriyle karışık değil unutmayın.  
  
 ![Diyagram gösteren üç nokta arka plan ile değil birbiriyle karışık.](./media/how-to-use-compositing-mode-to-control-alpha-blending/ellipses-blended-background.png)  
  
 Kod örneği, bu deyimi içerir:  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 Birbiriyle yanı sıra arka plan ile karışık için üç noktayı istiyorsanız, o ifadeyi şu şekilde değiştirin:  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 Düzeltilmiş kodun çıktısı aşağıdaki çizimde gösterilmektedir.  
  
 ![Üç nokta simgesini gösteren diyagram birbirine ve arka plan ile karışık.](./media/how-to-use-compositing-mode-to-control-alpha-blending/blend-ellipses-background.png)  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Color.FromArgb%2A>
- [Çizgi ve Dolgularda Alfa Karışım Kullanma](alpha-blending-lines-and-fills.md)
