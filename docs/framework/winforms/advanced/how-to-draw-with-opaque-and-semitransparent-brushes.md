---
title: 'Nasıl yapılır: Donuk ve Yarı Saydam Fırçalarla Çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- semi-transparent shapes [Windows Forms], drawing
- transparency [Windows Forms], semi-transparent shapes
- alpha blending [Windows Forms], brush
- brushes [Windows Forms], using semi-transparent
ms.assetid: a4f6f6b8-3bc8-440a-84af-d62ef0f8ff40
ms.openlocfilehash: a302b8bf978afcead5768fadeb6336c1ece986ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100942"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a>Nasıl yapılır: Donuk ve Yarı Saydam Fırçalarla Çizme
Bir şekil doldururken geçmesi gereken bir <xref:System.Drawing.Brush> dolgu yöntemlerinden birini nesnesine <xref:System.Drawing.Graphics> sınıfı. Bir parametre <xref:System.Drawing.SolidBrush.%23ctor%2A> Oluşturucusu bir <xref:System.Drawing.Color> nesne. Donuk bir şekli doldurmak için renk alfa bileşeni 255'e ayarlayın. Yarı saydam bir şekil doldurmak için 1 ila 254 herhangi bir değere alfa bileşenini ayarlayın.  
  
 Yarı saydam bir şekil doldururken şeklin rengi ile arka plan renklerini harmanlanan. Alfa bileşeni şekli ve arka plan renkleri nasıl karıştırılır belirtir. alfa değerleri 0 yakın daha fazla ağırlık arka plan renkleriyle yerleştirin ve alfa değerleri 255 yakın şekil rengine üzerinde daha fazla ağırlık yerleştirin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir bit eşlem çizer ve sonra bit eşlem çakışma üç elips doldurur. Donuk bir alfa bileşeni, 255, ilk üç nokta kullanır. Yarı saydam şekilde bir alfa bileşeni 128, ikinci ve üçüncü üç nokta simgesini kullanın. üç nokta üzerinden arka plan resmi görebilirsiniz. Ayarlar arama <xref:System.Drawing.Graphics.CompositingQuality%2A> özelliği neden olur üçüncü bir elipsin gama düzeltmesi ile birlikte yapılması karıştırma.  

 [!code-csharp[System.Drawing.AlphaBlending#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  

 Aşağıdaki kodu çıktı aşağıda gösterilmiştir: 
  
 ![Çizim donuk ve yarı saydam fırçalarla çıktısını gösterir.](./media/how-to-draw-with-opaque-and-semitransparent-brushes/compositingquality-ellipse-semitransparent.png)  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs>`e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Formlarında Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Çizgi ve Dolgularda Alfa Karışım Kullanma](alpha-blending-lines-and-fills.md)
- [Nasıl yapılır: Denetiminize Saydam Arka Plan Verme](../controls/how-to-give-your-control-a-transparent-background.md)
- [Nasıl yapılır: Donuk ve Yarı Saydam Çizgiler Çizme](how-to-draw-opaque-and-semitransparent-lines.md)
