---
title: 'Nasıl yapılır: Bir Windows Formunda Doldurulmuş Elips Çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.FillEllipse
helpviewer_keywords:
- ellipses [Windows Forms], drawing
- circles [Windows Forms], drawing
- circular shapes
- drawing [Windows Forms], ellipses
- shapes [Windows Forms], drawing
- forms [Windows Forms], drawing ellipses
ms.assetid: 781db806-950d-4c5b-b022-493f7fd0c4a8
ms.openlocfilehash: 2e7be3f2c4c710bb24568dd2e70f6f5cc4706c63
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59171016"
---
# <a name="how-to-draw-a-filled-ellipse-on-a-windows-form"></a>Nasıl yapılır: Bir Windows Formunda Doldurulmuş Elips Çizme
Bu örnek, bir form üzerinde doldurulmuş bir elips çizer.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu yöntem çağıramazsınız <xref:System.Windows.Forms.Form.Load> olay işleyicisi. Formu yeniden boyutlandırılabilir veya başka bir form tarafından engellediği çizilen içeriği yeniden değil. İçeriğinizi otomatik olarak repaint yapmak için geçersiz kılmanız <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Her zaman çağırmalıdır <xref:System.IDisposable.Dispose%2A> gibi sistem kaynaklarının kullanan herhangi bir nesne üzerinde <xref:System.Drawing.Brush> ve <xref:System.Drawing.Graphics> nesneleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Grafik Programlamaya Başlarken](getting-started-with-graphics-programming.md)
- [Çizgi ve Dolgularda Alfa Karışım Kullanma](alpha-blending-lines-and-fills.md)
- [Şekilleri Doldurmak için Fırça Kullanma](using-a-brush-to-fill-shapes.md)
