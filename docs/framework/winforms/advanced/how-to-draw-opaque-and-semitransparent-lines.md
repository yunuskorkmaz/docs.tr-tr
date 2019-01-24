---
title: 'Nasıl yapılır: Donuk ve yarı saydam çizgiler çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- transparency [Windows Forms], lines
- lines [Windows Forms], drawing alpha blended
- alpha blending [Windows Forms], drawing lines
ms.assetid: 8f2508af-f495-4223-b5cc-646cbbb520eb
ms.openlocfilehash: 6076ebf6cb75aa4fdb5cf5798b642597d8f84c80
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559053"
---
# <a name="how-to-draw-opaque-and-semitransparent-lines"></a>Nasıl yapılır: Donuk ve yarı saydam çizgiler çizme
Bir çizgi çizdiğinizde geçmesi gereken bir <xref:System.Drawing.Pen> nesnesini <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi <xref:System.Drawing.Graphics> sınıfı. Parametrelerinden biri <xref:System.Drawing.Pen.%23ctor%2A> Oluşturucusu bir <xref:System.Drawing.Color> nesne. Donuk bir çizgi çizmek için renk alfa bileşeni 255'e ayarlayın. Yarı saydam fırçalarla çizgi çizmek için 1 ila 254 herhangi bir değere alfa bileşenini ayarlayın.  
  
 Arka plan üzerinde yarı saydam bir çizgi çizdiğinizde, çizginin rengi ile arka plan renklerini harmanlanan. Satır, arka plan renkleri nasıl karıştırılmıştır alfa bileşeni belirtir. alfa değerleri 0 yakın daha fazla ağırlık arka plan renkleriyle yerleştirin ve alfa değerleri 255 yakın çizgi rengini üzerinde daha fazla ağırlık yerleştirin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir bit eşlem çizer ve sonra da bit eşlem arka plan olarak kullanan üç satır çizer. Donuk bir alfa bileşeni, 255, ilk satırı kullanır. Yarı saydam şekilde bir alfa bileşeni 128, ikinci ve üçüncü satır kullanın. arka plandaki resmin arkasını satırları görebilirsiniz. Ayarlar deyimi <xref:System.Drawing.Graphics.CompositingQuality%2A> özelliği neden gama düzeltmesi ile birlikte yapılması için üçüncü satırı karıştırma.  
  
 Aşağıdaki kodun çıktısı aşağıdaki çizimde gösterilmektedir.  
  
 ![Donuk ve yarı saydam fırçalarla](../../../../docs/framework/winforms/advanced/media/compqualline.png "compqualline")  
  
 [!code-csharp[System.Drawing.AlphaBlending#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.AlphaBlending#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çizgi ve Dolgularda Alfa Karışım Kullanma](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
- [Nasıl yapılır: Denetiminize saydam arka plan verme](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
- [Nasıl yapılır: Donuk ve yarı saydam fırçalarla fırçaları ile çizme](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)
