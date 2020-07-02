---
title: 'Nasıl yapılır: Bir Windows Formunda Çizgi Çizme'
description: Paint olayını işleyerek form üzerinde bir çizgi çizmenizi ve sonra da PaintEventArgs 'un Graphics özelliğini kullanarak çizimi gerçekleştirmeyi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- Graphics.DrawLine
helpviewer_keywords:
- examples [Windows Forms], drawing lines on forms
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- drawing lines
ms.assetid: 55c1dbeb-75d0-430c-9814-a24b8971ad8c
ms.openlocfilehash: c8e92dc265c63413275561d0e2e3aa820eaec724
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621632"
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a>Nasıl yapılır: Bir Windows Formunda Çizgi Çizme
Bu örnek, bir form üzerinde bir çizgi çizer. Genellikle, bir form üzerinde çizim yaptığınızda formun <xref:System.Windows.Forms.Control.Paint> olayını işler ve <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> <xref:System.Windows.Forms.PaintEventArgs> Bu örnekte gösterildiği gibi, öğesinin özelliğini kullanarak çizimi gerçekleştirirsiniz  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnek, Windows Forms kullanımı için tasarlanmıştır ve <xref:System.Windows.Forms.PaintEventArgs> `e` olay işleyicisinin bir parametresi olan gerektirir <xref:System.Windows.Forms.Control.Paint> .  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 <xref:System.IDisposable.Dispose%2A>Nesneler gibi sistem kaynaklarını kullanan tüm nesneleri her zaman çağırmanız gerekir <xref:System.Drawing.Pen> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Graphics.DrawLine%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Grafik Programlamaya Başlarken](getting-started-with-graphics-programming.md)
- [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](using-a-pen-to-draw-lines-and-shapes.md)
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
