---
title: "Nasıl yapılır: Metinle Düzgünleştirme Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: edd31ec5b9d94ac1791fb0f2a73522fdf4178627
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-antialiasing-with-text"></a>Nasıl yapılır: Metinle Düzgünleştirme Kullanma
*Düzgünleştirme* çizilmiş grafik ve bunların görünümünü ve okunabilirliğini artırmak için metin çentikli kenarları düzgünleştirme başvuruyor. Yönetilen ile [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sınıfları, daha düşük Kalite metin yanı sıra, yüksek kaliteli antialiased metin işleyebilirsiniz. Genellikle, daha yüksek kaliteli işleme alt kalite işleme'den daha fazla işleme zaman alır. Metin kalite düzeyini ayarlamak için ayarlayın <xref:System.Drawing.Graphics.TextRenderingHint%2A> özelliği bir <xref:System.Drawing.Graphics> öğelerinden birine <xref:System.Drawing.Text.TextRenderingHint> numaralandırması  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği iki farklı kalite ayarlarını metinle çizer.  
  
 Aşağıdaki çizimde örnek kod cod çıktısını gösterir.  
  
 ![Yazı tipleri metin](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")  
  
 [!code-csharp[System.Drawing.FontsAndText#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki kod örneğinde Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yazı Tipleri ve Metin Kullanma](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
