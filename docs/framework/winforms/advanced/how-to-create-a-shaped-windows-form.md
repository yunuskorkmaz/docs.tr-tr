---
title: 'Nasıl yapılır: Şekilli Windows Formu Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- forms [Windows Forms], rounded
- Windows Forms, custom shapes
- Windows Forms, shaped
- shaped forms
- forms [Windows Forms], changing the shape of
- forms [Windows Forms], circular
- forms [Windows Forms], nonrectangular
- Windows Forms, nonrectangular shape
- Windows Forms, rounded
- Windows Forms, circular
- forms [Windows Forms], custom shapes
ms.assetid: 6e6041e0-8e67-4487-b1e9-e410dbd1ef6c
ms.openlocfilehash: 3c90e6d5d2613239e513f8ec30d67b58084cba5e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64643492"
---
# <a name="how-to-create-a-shaped-windows-form"></a>Nasıl yapılır: Şekilli Windows Formu Oluşturma
Bu örnek ile formu boyutlandırır elips bir şekli bir form sağlar.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.Drawing.ConceptualHowTos#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#10)]
 [!code-csharp[System.Drawing.ConceptualHowTos#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#10)]
 [!code-vb[System.Drawing.ConceptualHowTos#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- Başvurular <xref:System.Windows.Forms> ve <xref:System.Drawing> ad alanları.  
  
 Bu örnek için geçersiz kılar <xref:System.Windows.Forms.Control.OnPaint%2A> formun şeklini değiştirmek için yöntemi. Bu kodu kullanmak için yöntem bildiriminde yanı sıra yöntemi içindeki çizim kodu kopyalayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Drawing.Region>
- <xref:System.Drawing>
- <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>
- <xref:System.Windows.Forms.Control.Region%2A>
- [Grafik Programlamaya Başlarken](getting-started-with-graphics-programming.md)
