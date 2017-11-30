---
title: "Nasıl yapılır: Bir Windows Formunda Çizgi Çizme"
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
f1_keywords: Graphics.DrawLine
helpviewer_keywords:
- examples [Windows Forms], drawing lines on forms
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- drawing lines
ms.assetid: 55c1dbeb-75d0-430c-9814-a24b8971ad8c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 984cdaca14c354ca78118412911c69c282ddd1bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a>Nasıl yapılır: Bir Windows Formunda Çizgi Çizme
Bu örnek, bir form üzerinde bir çizgi çizer. Genellikle, bir form üzerinde çizerken formun işlemek <xref:System.Windows.Forms.Control.Paint> olay ve çizim gerçekleştirin ve <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> özelliği <xref:System.Windows.Forms.PaintEventArgs>, bu örnekte gösterildiği gibi  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Her zaman çağırmalıdır <xref:System.IDisposable.Dispose%2A> sistem kaynakları gibi kullanabilecek tüm nesneler üzerinde <xref:System.Drawing.Pen> nesneleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Graphics.DrawLine%2A>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [Grafik programlamaya Başlarken](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [Çizgiler ve şekiller çizmek için kalem kullanma](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [Grafikler ve Windows Forms'ta çizme](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
