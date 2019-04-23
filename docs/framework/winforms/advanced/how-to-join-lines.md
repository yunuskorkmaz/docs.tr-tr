---
title: 'Nasıl yapılır: Satırları Birleştirme'
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
ms.openlocfilehash: 445d7f12f57137c6b06a074eeaf0574eb027a723
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174921"
---
# <a name="how-to-join-lines"></a>Nasıl yapılır: Satırları Birleştirme
Satır birleştirme, sona erer karşılamak ya da üst üste iki satırla ayrılan biçimlendirilmiş ortak bir alandır. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] üç çizgi birleştirme stili sağlar: gönye, eğim ve yuvarlar. Çizgisi birleştirme stili bir özelliği olan <xref:System.Drawing.Pen> sınıfı. Bir çizgi birleştirme stili belirttiğinizde bir <xref:System.Drawing.Pen> nesnesi, birleştirme stili herhangi bağlı tüm satırlara uygulanacak <xref:System.Drawing.Drawing2D.GraphicsPath> , kalem kullanarak nesne.  
  
 Aşağıdaki çizim, eğik çizgi birleştirme örnek sonuçları gösterilmektedir.  
  
 ![Çizim Birleştirilmiş satırları gösterir.](./media/how-to-join-lines/joined-beveled-lines.gif)  
  
## <a name="example"></a>Örnek  
 Kullanarak çizgisi birleştirme stili belirtebilirsiniz <xref:System.Drawing.Pen.LineJoin%2A> özelliği <xref:System.Drawing.Pen> sınıfı. Örnek bir eğik çizgi birleştirme yatay çizgi dikey çizgi arasındaki gösterir. Aşağıdaki kodda, değer <xref:System.Drawing.Drawing2D.LineJoin.Bevel> atanan <xref:System.Drawing.Pen.LineJoin%2A> özelliği üyesi olduğu <xref:System.Drawing.Drawing2D.LineJoin> sabit listesi. Diğer üyeleri <xref:System.Drawing.Drawing2D.LineJoin> numaralandırma olan <xref:System.Drawing.Drawing2D.LineJoin.Miter> ve <xref:System.Drawing.Drawing2D.LineJoin.Round>.  
  
 [!code-csharp[System.Drawing.UsingAPen#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](using-a-pen-to-draw-lines-and-shapes.md)
