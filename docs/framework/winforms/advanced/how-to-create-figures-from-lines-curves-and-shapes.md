---
title: 'Nasıl yapılır: Çizgiler, Eğriler ve Şekillerden Şekiller Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- figures [Windows Forms], creating from shapes
- figures [Windows Forms], creating from lines
ms.assetid: 82fd56c7-b443-4765-9b7c-62ce030656ec
ms.openlocfilehash: 222245fa4b3b593e0a38752a8cb991a12e469698
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521862"
---
# <a name="how-to-create-figures-from-lines-curves-and-shapes"></a>Nasıl yapılır: Çizgiler, Eğriler ve Şekillerden Şekiller Oluşturma
Bir şekil oluşturmak için oluşturmak bir <xref:System.Drawing.Drawing2D.GraphicsPath>ve yöntemleri gibi çağrısı <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> ve <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>, ilkel yolunu eklemek için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örnekleri rakamları sahip yolları oluşturun:  
  
-   İlk örnek tek bir şekil sahip bir yol oluşturur. Şekil, tek bir yay oluşur. Yayı varsayılan koordinat sistemi saatin tarama açısı – 180 derece vardır.  
  
-   İkinci örnekte iki şekilde sahip bir yol oluşturur. İlk satırı tarafından izlenen bir yay sayıdır. İkinci şekil satırı tarafından izlenen bir eğri arkasından bir satırdır. İlk şekil açık kalır ve ikinci şekil kapalı.  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#21)]  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#22)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örneklerde Windows Forms ile kullanılmak üzere tasarlanmıştır ve ihtiyaç <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 [Yollar Oluşturma ve Çizme](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)  
 [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
