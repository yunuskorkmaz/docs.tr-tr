---
title: 'Nasıl yapılır: Bir Windows Formunda Doldurulmuş Dikdörtgen Çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.FillRectangle
helpviewer_keywords:
- drawing [Windows Forms], rectangles
- rectangles [Windows Forms], drawing
- drawing rectangles
ms.assetid: d656a93c-987d-4809-aafd-493fe17450f0
ms.openlocfilehash: e551eacf0924c9bffa802fb5d2ba8bae7c1c3a98
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004308"
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a>Nasıl yapılır: Bir Windows Formunda Doldurulmuş Dikdörtgen Çizme
Bu örnek, bir form üzerinde doldurulmuş bir dikdörtgen çizer.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu yöntem çağıramazsınız <xref:System.Windows.Forms.Form.Load> olay işleyicisi. Formu yeniden boyutlandırılabilir veya başka bir form tarafından engellediği çizilen içeriği yeniden değil. İçeriğinizi otomatik olarak repaint yapmak için geçersiz kılmanız <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Her zaman çağırmalıdır <xref:System.IDisposable.Dispose%2A> gibi sistem kaynaklarının kullanan herhangi bir nesne üzerinde <xref:System.Drawing.Brush> ve <xref:System.Drawing.Graphics> nesneleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Graphics.FillRectangle%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Grafik Programlamaya Başlarken](getting-started-with-graphics-programming.md)
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](using-a-pen-to-draw-lines-and-shapes.md)
- [GDI+'da Fırçalar ve Dolgulu Şekiller](brushes-and-filled-shapes-in-gdi.md)
