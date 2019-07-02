---
title: 'Nasıl yapılır: Metinle Düzgünleştirme Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [Windows Forms], smoothing drawn
- antialiasing [Windows Forms], using with text
- text [Windows Forms], smoothing
- text [Windows Forms], antialiasing
- strings [Windows Forms], antialiasing when drawing
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
ms.openlocfilehash: 080d946bd72da8b76ed846efdf149eb328d66336
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505720"
---
# <a name="how-to-use-antialiasing-with-text"></a>Nasıl yapılır: Metinle Düzgünleştirme Kullanma
*Düzgünleştirme* düzensiz çizilen grafik ve bunların görünümünü ve okunabilirliğini geliştirmek için metni kenarlarına düzgünleştirme ifade eder. Yönetilen GDI +'da sahip sınıflara, daha düşük kaliteli metin yanı sıra, yüksek kaliteli antialiased metin işleyebilirsiniz. Genellikle, daha yüksek kalite işleme daha fazla işleme zaman daha düşük kaliteli işleme alır. Metin kalite düzeyini ayarlamak için ayarlayın <xref:System.Drawing.Graphics.TextRenderingHint%2A> özelliği bir <xref:System.Drawing.Graphics> öğelerinden birine <xref:System.Drawing.Text.TextRenderingHint> numaralandırması  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, iki farklı ayarlarla metin çizer.  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
 
 Örnek kodun çıktısı aşağıdaki çizimde gösterilmektedir:  
  
 ![İki farklı ayarlarla metin gösteren ekran görüntüsü.](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki kod örneğinde, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yazı Tipleri ve Metin Kullanma](using-fonts-and-text.md)
