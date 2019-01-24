---
title: 'Nasıl yapılır: Bir Windows formunda metin çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- forms [Windows Forms], drawing text
- text [Windows Forms], drawing
ms.assetid: 5d2447a9-21a1-4adc-b954-5516f2bb9b2c
ms.openlocfilehash: 07aef6619468b957d6f2aa46482be3de0411cd40
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512400"
---
# <a name="how-to-draw-text-on-a-windows-form"></a>Nasıl yapılır: Bir Windows formunda metin çizme
Aşağıdaki kod örneği kullanma işlemini gösterir <xref:System.Drawing.Graphics.DrawString%2A> yöntemi <xref:System.Drawing.Graphics> bir form üzerinde metin Çiz için. Alternatif olarak, <xref:System.Windows.Forms.TextRenderer> bir form üzerinde metin çizme. Daha fazla bilgi için [nasıl yapılır: GDI ile metin çizme](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md).  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#7)]
 [!code-csharp[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#7)]
 [!code-vb[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#7)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Çağıramazsınız <xref:System.Drawing.Graphics.DrawString%2A> yönteminde <xref:System.Windows.Forms.Form.Load> olay işleyicisi. Formu yeniden boyutlandırılabilir veya başka bir form tarafından engellediği çizilen içeriği yeniden değil. İçeriğinizi otomatik olarak repaint yapmak için geçersiz kılmanız <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Arial yazı tipi yüklü değil.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Graphics.DrawString%2A>
- <xref:System.Windows.Forms.TextRenderer.DrawText%2A>
- <xref:System.Drawing.StringFormat.FormatFlags%2A>
- <xref:System.Drawing.StringFormatFlags>
- <xref:System.Windows.Forms.TextFormatFlags>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Grafik Programlamaya Başlarken](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)
- [Nasıl yapılır: GDI ile metin çizme](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
