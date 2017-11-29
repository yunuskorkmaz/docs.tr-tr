---
title: "Nasıl yapılır: Bir Kalemin Rengini Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pens [Windows Forms], setting color
- colored pens
ms.assetid: a9df06f9-a6d5-4d9b-a2d1-583943540775
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 452e88b4b41a22cc78f73e120e49468e4f4dad56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-color-of-a-pen"></a>Nasıl yapılır: Bir Kalemin Rengini Ayarlama
Bu örnek önceden var olan rengini değiştirir <xref:System.Drawing.Pen> nesnesi  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#9)]
 [!code-csharp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#9)]
 [!code-vb[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#9)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Drawing.Pen> adlı nesne `myPen`.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Çağırmalısınız <xref:System.Drawing.Pen.Dispose%2A> sistem kaynaklarını tüketebilir nesneler üzerinde (gibi <xref:System.Drawing.Pen> nesneler) kullanmadan tamamladıktan sonra.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Pen>  
 [Grafik programlamaya Başlarken](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [Nasıl yapılır: Kalem oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [Çizgiler ve şekiller çizmek için kalem kullanma](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [Kalemler, çizgiler ve dikdörtgenler GDI +'da](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
