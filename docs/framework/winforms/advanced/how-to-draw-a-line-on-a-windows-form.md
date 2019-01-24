---
title: 'Nasıl yapılır: Bir Windows formunda çizgi çizme'
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
ms.openlocfilehash: 4274072b55c79cfe88e906d1401d275b414ebe97
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586754"
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a>Nasıl yapılır: Bir Windows formunda çizgi çizme
Bu örnek, bir form üzerinde bir çizgi çizer. Genellikle, bir form üzerinde çizdiğinizde, formun işlemek <xref:System.Windows.Forms.Control.Paint> olay ve çizim kullanarak gerçekleştirmek <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> özelliği <xref:System.Windows.Forms.PaintEventArgs>, bu örnekte gösterildiği gibi  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Her zaman çağırmalıdır <xref:System.IDisposable.Dispose%2A> gibi sistem kaynaklarının kullanan herhangi bir nesne üzerinde <xref:System.Drawing.Pen> nesneleri.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Graphics.DrawLine%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Grafik Programlamaya Başlarken](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)
- [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
- [Windows Forms’da Grafikler ve Çizim](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
