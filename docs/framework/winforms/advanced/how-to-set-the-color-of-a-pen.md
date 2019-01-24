---
title: 'Nasıl yapılır: Bir kalemin rengini ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pens [Windows Forms], setting color
- colored pens
ms.assetid: a9df06f9-a6d5-4d9b-a2d1-583943540775
ms.openlocfilehash: d0402a7d6bb641ef6d97eb41bc25f3c59b3b4250
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569446"
---
# <a name="how-to-set-the-color-of-a-pen"></a>Nasıl yapılır: Bir kalemin rengini ayarlama
Bu örnek, önceden var olan rengini değiştirir <xref:System.Drawing.Pen> nesnesi  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#9)]
 [!code-csharp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#9)]
 [!code-vb[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#9)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Drawing.Pen> adlı nesne `myPen`.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Çağırmalısınız <xref:System.Drawing.Pen.Dispose%2A> sistem kaynaklarının kullanılmasına nesneler üzerinde (gibi <xref:System.Drawing.Pen> nesneleri) kullanmadan tamamladıktan sonra.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Pen>
- [Grafik Programlamaya Başlarken](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)
- [Nasıl yapılır: Kalem oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
- [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
- [GDI+'da Kalemler, Çizgiler ve Dikdörtgenler](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
