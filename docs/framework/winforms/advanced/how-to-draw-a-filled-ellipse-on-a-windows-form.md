---
title: 'Nasıl yapılır: Bir Windows formunda doldurulmuş elips çizme'
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
ms.openlocfilehash: 09c98ec2874566cc49319d174ef7f1650a436d38
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616916"
---
# <a name="how-to-draw-a-filled-ellipse-on-a-windows-form"></a>Nasıl yapılır: Bir Windows formunda doldurulmuş elips çizme
Bu örnek, bir form üzerinde doldurulmuş bir elips çizer.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu yöntem çağıramazsınız <xref:System.Windows.Forms.Form.Load> olay işleyicisi. Formu yeniden boyutlandırılabilir veya başka bir form tarafından engellediği çizilen içeriği yeniden değil. İçeriğinizi otomatik olarak repaint yapmak için geçersiz kılmanız <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Her zaman çağırmalıdır <xref:System.IDisposable.Dispose%2A> gibi sistem kaynaklarının kullanan herhangi bir nesne üzerinde <xref:System.Drawing.Brush> ve <xref:System.Drawing.Graphics> nesneleri.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Windows Forms’da Grafikler ve Çizim](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [Grafik Programlamaya Başlarken](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)
- [Çizgi ve Dolgularda Alfa Karışım Kullanma](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
- [Şekilleri Doldurmak için Fırça Kullanma](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
