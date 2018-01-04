---
title: "Nasıl yapılır: Çizgi Uçlarıyla Çizgi Çizme"
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
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
- drawing lines [Windows Forms], line caps
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4048757e11724aa1e175d8b18c47f48d22d807e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-line-with-line-caps"></a>Nasıl yapılır: Çizgi Uçlarıyla Çizgi Çizme
Başlangıç ya da bir satırın sonuna satır caps adlı birkaç şekiller birinde çizebilirsiniz. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]gidiş, kare, Karo ve Ok ucunu gibi birkaç satır caps destekler.  
  
## <a name="example"></a>Örnek  
 Satır caps başlangıç satırı (Başlangıç cap), (son cap) satırın sonuna veya kesik çizgi (tire cap) tireler belirtebilirsiniz.  
  
 Aşağıdaki örnekte bir ok ucunu bir uçta ve diğer uçtaki yuvarlak bir uç satırıyla çizilmiştir. Sonuçta elde edilen satır çizimde gösterilmektedir:  
  
 ![Kalemler](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")  
  
 [!code-csharp[System.Drawing.UsingAPen#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bir Windows formu oluşturma ve form ele <xref:System.Windows.Forms.Control.Paint> olay. Örnek kod içine yapıştırma <xref:System.Windows.Forms.Control.Paint> geçirme olay işleyicisi `e` olarak <xref:System.Windows.Forms.PaintEventArgs>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>  
 [Windows Forms’da Grafikler ve Çizim](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
