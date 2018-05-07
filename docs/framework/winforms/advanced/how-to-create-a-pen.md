---
title: 'Nasıl yapılır: Kalem Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating pens
- pens [Windows Forms], creating
- Pen object
ms.assetid: 7fbea8b7-7ac1-4413-9c17-733a850381e3
ms.openlocfilehash: aff1771af12a9f59127a9f21f4b692d6214c457d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-pen"></a>Nasıl yapılır: Kalem Oluşturma
Bu örnekte bir <xref:System.Drawing.Pen> nesnesi.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#3)]
 [!code-csharp[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#3)]
 [!code-vb[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#3)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Sistem kaynakları gibi kullanabilecek nesneleri kullanmayı bitirdikten sonra <xref:System.Drawing.Pen> nesneleri çağrı <xref:System.Drawing.Pen.Dispose%2A> bunlardaki.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Pen>  
 [Grafik Programlamaya Başlarken](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [GDI+'da Kalemler, Çizgiler ve Dikdörtgenler](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
