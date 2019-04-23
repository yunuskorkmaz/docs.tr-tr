---
title: 'Nasıl yapılır: Kalem Genişliği ve Hizalamasını Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [Windows Forms], setting width
- pens [Windows Forms], setting alignment
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
ms.openlocfilehash: bc2ac2587554215ef3b2c2580413fbbb894aa687
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074982"
---
# <a name="how-to-set-pen-width-and-alignment"></a>Nasıl yapılır: Kalem Genişliği ve Hizalamasını Ayarlama
Oluştururken bir <xref:System.Drawing.Pen>, kalem genişliği oluşturucusuna bağımsız değişkenlerden biri olarak sağlayabilirsiniz. Kalem genişliği ile de değiştirebileceğiniz <xref:System.Drawing.Pen.Width%2A> özelliği <xref:System.Drawing.Pen> sınıfı.  
  
 Teorik bir çizgi genişliği 0 ' var. 1 piksel genişliğinde bir çizgi çizdiğinizde, piksel teorik satırında ortalanır. Birden fazla piksel genişliğinde bir çizgi çizin, piksel teorik satırında ya da ortalanır veya teorik satırın bir tarafında görünür. Kalem hizalamayı özelliğini ayarlayabilirsiniz bir <xref:System.Drawing.Pen> teorik satırlara, kalem ile çizilen piksel nasıl yerleştirileceğini belirlemek için.  
  
 Değerleri <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, ve <xref:System.Drawing.Drawing2D.PenAlignment.Inset> aşağıda görünen kod örnekleri üyeleridir <xref:System.Drawing.Drawing2D.PenAlignment> sabit listesi.  
  
 Aşağıdaki kod örneği iki kez bir çizgi çizer: siyah kalem genişliği 1 ile bir kez ve yeşil bir kalem genişliği 10 ile bir kez.  
  
### <a name="to-vary-the-width-of-a-pen"></a>Kalem genişliği değiştirmek için  
  
-   Değerini <xref:System.Drawing.Pen.Alignment%2A> özelliğini <xref:System.Drawing.Drawing2D.PenAlignment.Center> (yeşil kalem ile çizilen piksel teorik satırında ortalanacağını belirtmek için varsayılan). Sonuçta elde edilen satırı aşağıda gösterilmiştir.  
  
     ![Yeşil vurgu ile siyah bir ölçülü kaynak satırı.](./media/how-to-set-pen-width-and-alignment/green-pixels-centered-line.gif)  
  
     Aşağıdaki kod örneği iki kez bir dikdörtgen çizer: siyah kalem genişliği 1 ile bir kez ve yeşil bir kalem genişliği 10 ile bir kez.  
  
     [!code-csharp[System.Drawing.UsingAPen#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### <a name="to-change-the-alignment-of-a-pen"></a>Kalem hizalamayı değiştirmek için  
  
-   Değerini <xref:System.Drawing.Pen.Alignment%2A> özelliğini <xref:System.Drawing.Drawing2D.PenAlignment.Center> yeşil kalem ile çizilen piksel dikdörtgenin sınırında ortalanacağını belirtmek için.  
  
     Sonuçta elde edilen dikdörtgen aşağıda gösterilmiştir:
  
     ![Yeşil vurgu siyah ölçülü kaynak satırıyla ile çizilen bir dikdörtgen.](./media/how-to-set-pen-width-and-alignment/green-pixels-centered-rectangle.gif)  
  
     [!code-csharp[System.Drawing.UsingAPen#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### <a name="to-create-an-inset-pen"></a>Bir iç kalem oluşturmak için  
  
-   Yukarıdaki kod örneğinde üçüncü deyim şu şekilde değiştirerek yeşil kalem hizalamayı değiştirin:  
  
     [!code-csharp[System.Drawing.UsingAPen#43](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     Artık geniş yeşil çizginin piksellerde dikdörtgenin iç aşağıdaki çizimde gösterildiği gibi görünür:
  
     ![Siyah satır içinde geniş yeşil bir çizgi ile çizilen bir dikdörtgen.](./media/how-to-set-pen-width-and-alignment/green-pixels-inside-rectangle.gif)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](using-a-pen-to-draw-lines-and-shapes.md)
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
