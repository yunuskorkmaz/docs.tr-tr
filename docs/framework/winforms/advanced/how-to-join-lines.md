---
title: 'Nasıl yapılır: Satırları birleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- miter line join style
- bevel line join style
- line join
- drawing [Windows Forms], joining lines
- GraphicsPath object
- round line join style
- lines [Windows Forms], joining
- graphics [Windows Forms], joining lines
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
ms.openlocfilehash: 55551a78f37a5179b24eda28a9fc5d0a0c640a9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543389"
---
# <a name="how-to-join-lines"></a>Nasıl yapılır: Satırları birleştirme
Satır birleştirme, sona erer karşılamak ya da üst üste iki satırla ayrılan biçimlendirilmiş ortak bir alandır. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] üç çizgi birleştirme stili sağlar: gönye, eğim ve yuvarlar. Çizgisi birleştirme stili bir özelliği olan <xref:System.Drawing.Pen> sınıfı. Bir çizgi birleştirme stili belirttiğinizde bir <xref:System.Drawing.Pen> nesnesi, birleştirme stili herhangi bağlı tüm satırlara uygulanacak <xref:System.Drawing.Drawing2D.GraphicsPath> , kalem kullanarak nesne.  
  
 Aşağıdaki çizim, eğik çizgi birleştirme örnek sonuçları gösterilmektedir.  
  
 ![Kalemler](../../../../docs/framework/winforms/advanced/media/pens5.gif "pens5")  
  
## <a name="example"></a>Örnek  
 Kullanarak çizgisi birleştirme stili belirtebilirsiniz <xref:System.Drawing.Pen.LineJoin%2A> özelliği <xref:System.Drawing.Pen> sınıfı. Örnek bir eğik çizgi birleştirme yatay çizgi dikey çizgi arasındaki gösterir. Aşağıdaki kodda, değer <xref:System.Drawing.Drawing2D.LineJoin.Bevel> atanan <xref:System.Drawing.Pen.LineJoin%2A> özelliği üyesi olduğu <xref:System.Drawing.Drawing2D.LineJoin> sabit listesi. Diğer üyeleri <xref:System.Drawing.Drawing2D.LineJoin> numaralandırma olan <xref:System.Drawing.Drawing2D.LineJoin.Miter> ve <xref:System.Drawing.Drawing2D.LineJoin.Round>.  
  
 [!code-csharp[System.Drawing.UsingAPen#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
