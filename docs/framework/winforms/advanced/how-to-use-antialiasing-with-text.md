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
ms.openlocfilehash: 632ed329173d134495a424b34ca7c71e402607bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182480"
---
# <a name="how-to-use-antialiasing-with-text"></a>Nasıl yapılır: Metinle Düzgünleştirme Kullanma
*Antialiasing,* görünümlerini veya okunabilirliklerini geliştirmek için çizilen grafiklerin ve metnin pürüzlü kenarlarının düzgünlemesi anlamına gelir. Yönetilen GDI+ sınıfları ile yüksek kaliteli antialiased metin ve daha düşük kaliteli metin işleyebilirsiniz. Genellikle, daha yüksek kaliteli işleme, daha düşük kaliteli işleme daha fazla işlem süresi alır. Metin kalite düzeyini ayarlamak için, a'nın <xref:System.Drawing.Graphics.TextRenderingHint%2A> <xref:System.Drawing.Graphics> özelliğini numaralandırmanın öğelerinden <xref:System.Drawing.Text.TextRenderingHint> birine ayarlayın  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, iki farklı kalite ayarı içeren metin çizer.  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  

 Aşağıdaki resimde örnek kodun çıktısı gösterilmektedir:  
  
 ![İki farklı kalite ayarı olan metni gösteren ekran görüntüsü.](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki kod örneği Windows Formlar ile kullanılmak üzere <xref:System.Windows.Forms.PaintEventArgs> `e`tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventHandler>, hangi bir parametre .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yazı Tipleri ve Metin Kullanma](using-fonts-and-text.md)
