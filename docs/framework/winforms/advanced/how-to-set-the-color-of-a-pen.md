---
title: 'Nasıl yapılır: Bir Kalemin Rengini Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pens [Windows Forms], setting color
- colored pens
ms.assetid: a9df06f9-a6d5-4d9b-a2d1-583943540775
ms.openlocfilehash: ee2d3f8cdf6dd10ca2a9ff0dd3e66b164c84f21b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64637010"
---
# <a name="how-to-set-the-color-of-a-pen"></a>Nasıl yapılır: Bir Kalemin Rengini Ayarlama
Bu örnek, önceden var olan rengini değiştirir <xref:System.Drawing.Pen> nesnesi  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.Drawing.ConceptualHowTos#9](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#9)]
 [!code-csharp[System.Drawing.ConceptualHowTos#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#9)]
 [!code-vb[System.Drawing.ConceptualHowTos#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#9)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- A <xref:System.Drawing.Pen> adlı nesne `myPen`.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Çağırmalısınız <xref:System.Drawing.Pen.Dispose%2A> sistem kaynaklarının kullanılmasına nesneler üzerinde (gibi <xref:System.Drawing.Pen> nesneleri) kullanmadan tamamladıktan sonra.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Pen>
- [Grafik Programlamaya Başlarken](getting-started-with-graphics-programming.md)
- [Nasıl yapılır: Kalem oluşturma](how-to-create-a-pen.md)
- [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](using-a-pen-to-draw-lines-and-shapes.md)
- [GDI+'da Kalemler, Çizgiler ve Dikdörtgenler](pens-lines-and-rectangles-in-gdi.md)
