---
title: 'Nasıl yapılır: Bir Windows Formunda Doldurulmuş Dikdörtgen Çizme'
description: Windows form 'da program aracılığıyla doldurulmuş bir dikdörtgen çizmeyi öğrenin. Ayrıca, kodunuzun derlenmesi hakkında bilgi edinin.
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
ms.openlocfilehash: 0ad8ec97000e29b2194a9eda713aa43d5557b44c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621645"
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a>Nasıl yapılır: Bir Windows Formunda Doldurulmuş Dikdörtgen Çizme
Bu örnek, bir form üzerinde doldurulmuş bir dikdörtgen çizer.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Olay işleyicisinde bu yöntemi çağrılamaz <xref:System.Windows.Forms.Form.Load> . Form başka bir form tarafından yeniden boyutlandırılmışsa veya gizlendiyse çizilen içerik yeniden çizilmez. İçeriğinizi otomatik olarak yeniden çizmeyi sağlamak için yöntemini geçersiz kılmanız gerekir <xref:System.Windows.Forms.Control.OnPaint%2A> .  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 <xref:System.IDisposable.Dispose%2A>Ve nesneleri gibi sistem kaynaklarını kullanan tüm nesneleri her zaman çağırmanız gerekir <xref:System.Drawing.Brush> <xref:System.Drawing.Graphics> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Graphics.FillRectangle%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Grafik Programlamaya Başlarken](getting-started-with-graphics-programming.md)
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](using-a-pen-to-draw-lines-and-shapes.md)
- [GDI+'da Fırçalar ve Dolgulu Şekiller](brushes-and-filled-shapes-in-gdi.md)
