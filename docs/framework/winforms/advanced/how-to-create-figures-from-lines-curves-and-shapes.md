---
title: 'Nasıl yapılır: Şekil çizgiler, eğriler ve şekillerden şekiller oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- figures [Windows Forms], creating from shapes
- figures [Windows Forms], creating from lines
ms.assetid: 82fd56c7-b443-4765-9b7c-62ce030656ec
ms.openlocfilehash: 1977f1c9efe2c379ef6039870aade300efca2bdd
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709503"
---
# <a name="how-to-create-figures-from-lines-curves-and-shapes"></a>Nasıl yapılır: Şekil çizgiler, eğriler ve şekillerden şekiller oluşturma
Bir şekil oluşturmak için oluşturmak bir <xref:System.Drawing.Drawing2D.GraphicsPath>ve ardından yöntemleri çağırmak <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> ve <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>, ilkel yola ekleyin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örnekleri olan şekil yolları oluşturun:  
  
-   İlk örnek, tek bir şekil sahip bir yol oluşturur. Şekilde tek bir yay içerir. Yayı varsayılan koordinat sisteminde saatin bir tarama açısı – 180 derece vardır.  
  
-   İkinci örnek, iki şekil sahip bir yol oluşturur. İlk satır tarafından izlenen bir yay sayıdır. İkinci şekil, bir satır tarafından izlenen bir eğri arkasından bir satırdır. İlk şekil açık kalır ve ikinci şekil kapalı.  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#21)]  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#22)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örneklerde, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirdikleri <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Drawing2D.GraphicsPath>
- [Yollar Oluşturma ve Çizme](constructing-and-drawing-paths.md)
- [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](using-a-pen-to-draw-lines-and-shapes.md)
