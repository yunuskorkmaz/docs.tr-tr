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
ms.openlocfilehash: 1e48bbd563f6377380848949325962b568fa432c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142413"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a>Nasıl yapılır: Donuk ve Yarı Saydam Fırçalarla Çizme
Bir şekli doldurduğınızda, bir <xref:System.Drawing.Brush> nesneyi <xref:System.Drawing.Graphics> sınıfın doldurma yöntemlerinden birine geçirmeniz gerekir. <xref:System.Drawing.SolidBrush.%23ctor%2A> Oluşturucunun tek parametresi <xref:System.Drawing.Color> bir nesnedir. Opak bir şekli doldurmak için rengin alfa bileşenini 255 olarak ayarlayın. Yarı saydam bir şekli doldurmak için alfa bileşenini 1'den 254'e kadar herhangi bir değere ayarlayın.  
  
 Yarı saydam bir şekli doldurduğunda, şeklin rengi arka plan daki renklerle karıştırılır. Alfa bileşeni şekil ve arka plan renklerinin nasıl karıştırıldığını belirtir; 0'a yakın alfa değerleri arka plan renklerine daha fazla ağırlık, 255'e yakın alfa değerleri ise şekil rengine daha fazla ağırlık yerleştirir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir bit eşlemi çizer ve sonra bit eşlemiyle çakışan üç elipsi doldurur. İlk elips 255 alfa bileşeni kullanır, bu yüzden opaktır. İkinci ve üçüncü elipsler 128'lik bir alfa bileşeni kullanırlar, bu yüzden yarı saydamdırlar; elipslerden arka plan görüntüsünü görebilirsiniz. <xref:System.Drawing.Graphics.CompositingQuality%2A> Özelliği ayarlayan çağrı, üçüncü elipsin karıştırmasının gama düzeltmesi ile birlikte yapılmasına neden olur.  

 [!code-csharp[System.Drawing.AlphaBlending#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  

 Aşağıdaki resimde aşağıdaki kodun çıktısı gösterilmektedir:
  
 ![Opak ve yarı saydam çıktı gösteren çizim.](./media/how-to-draw-with-opaque-and-semitransparent-brushes/compositingquality-ellipse-semitransparent.png)  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnek Windows Formlar ile kullanılmak üzere <xref:System.Windows.Forms.PaintEventArgs> `e`tasarlanmıştır ve gerektirir , <xref:System.Windows.Forms.PaintEventHandler>hangi bir parametre .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Çizgi ve Dolgularda Alfa Karışım Kullanma](alpha-blending-lines-and-fills.md)
- [Nasıl yapılır: Denetiminize Saydam Arka Plan Verme](../controls/how-to-give-your-control-a-transparent-background.md)
- [Nasıl yapılır: Donuk ve Yarı Saydam Çizgiler Çizme](how-to-draw-opaque-and-semitransparent-lines.md)
