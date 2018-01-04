---
title: "Nasıl yapılır: Dikdörtgen Çizmek için Kalem Kullanma"
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
- rectangles [Windows Forms], drawing
- pens [Windows Forms], drawing rectangles
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7257fa21432ec5d849a257f4a5e412515f474363
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a>Nasıl yapılır: Dikdörtgen Çizmek için Kalem Kullanma
Dikdörtgen çizmek için size gereken bir <xref:System.Drawing.Graphics> nesne ve <xref:System.Drawing.Pen> nesne. <xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi ve <xref:System.Drawing.Pen> nesnesi satırının renk ve genişlik gibi özellikleri saklar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sol üst köşede bir dikdörtgen çizer (10, 10). Dikdörtgen 100 genişliği ve yüksekliği 50 sahiptir. İkinci bağımsız değişkeni geçirilen <xref:System.Drawing.Pen.%23ctor%2A> Oluşturucusu kalem genişliği 5 pikselden olduğunu gösterir.  
  
 Dikdörtgen çizildiğinde kalem dikdörtgenin sınırında ortalanır. Kalem genişliği 5'tir dikdörtgen yanlarından çizilmiş 5 piksel olduklarından, o 1 piksel genişliğinde, bu tür çizilir sınırın üzerinde kendi iç 2 piksel çizilir ve 2 piksel dışarıda çizilir. Kalem hizalama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Kalem genişliği ve hizalamasını](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md).  
  
 Aşağıdaki çizimde, sonuçta elde edilen dikdörtgen gösterir. Kalem genişliği bir piksel olsaydı burada dikdörtgen Çekildi noktalı çizgiler gösterir. Kalın siyah çizgiler bu noktalı satırlarında ortalanır dikdörtgenin sol üst köşesindeki genişletilmiş görünümünü gösterir.  
  
 ![Kalemler](../../../../docs/framework/winforms/advanced/media/pens1.gif "pens1")  
  
 [!code-csharp[System.Drawing.UsingAPen#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
