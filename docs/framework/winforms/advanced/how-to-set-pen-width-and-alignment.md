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
ms.openlocfilehash: 8ac125978405f39cd26680338cdabb661ad92d16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-pen-width-and-alignment"></a>Nasıl yapılır: Kalem Genişliği ve Hizalamasını Ayarlama
Oluştururken bir <xref:System.Drawing.Pen>, oluşturucu bağımsız değişkenlerinden biri olarak kalem genişliği sağlayabilir. Kalem genişliği ile de değiştirebilirsiniz <xref:System.Drawing.Pen.Width%2A> özelliği <xref:System.Drawing.Pen> sınıfı.  
  
 Teorik bir çizgi genişliği 0 sahiptir. 1 piksel genişliğinde bir çizgi çizerken piksel teorik satırında ortalanır. Birden fazla piksel genişliğinde olan çizgi çizme, piksel teorik satırında ya da ortalanır veya teorik satır bir tarafında görünür. Kalem hizalama özelliği ayarlayabileceğiniz bir <xref:System.Drawing.Pen> ile bu kalem çizilmiş piksel teorik satırları göre nasıl yerleştirileceğini belirlemek için.  
  
 Değerleri <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, ve <xref:System.Drawing.Drawing2D.PenAlignment.Inset> aşağıda görünen kod örnekleri üyeleri olan <xref:System.Drawing.Drawing2D.PenAlignment> numaralandırması.  
  
 Aşağıdaki kod örneğinde bir çizgi iki kez çizer: kez siyah kalem genişliği 1 ile bir kez yeşil kalem genişliği 10.  
  
### <a name="to-vary-the-width-of-a-pen"></a>Kalem genişliği değiştirmek için  
  
-   Değerini <xref:System.Drawing.Pen.Alignment%2A> özelliğine <xref:System.Drawing.Drawing2D.PenAlignment.Center> (yeşil kalem ile çizilmiş piksel teorik satırda ortalanmış belirtmek için varsayılan). Aşağıdaki çizimde, sonuçta elde edilen satır gösterir.  
  
     ![Kalemler](../../../../docs/framework/winforms/advanced/media/pens1a.gif "pens1A")  
  
     Aşağıdaki kod örneğinde bir dikdörtgen iki kez çizer: kez siyah kalem genişliği 1 ile bir kez yeşil kalem genişliği 10.  
  
     [!code-csharp[System.Drawing.UsingAPen#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### <a name="to-change-the-alignment-of-a-pen"></a>Kalem hizalamasını değiştirmek için  
  
-   Değerini <xref:System.Drawing.Pen.Alignment%2A> özelliğine <xref:System.Drawing.Drawing2D.PenAlignment.Center> ile yeşil kalem çizilmiş piksel dikdörtgen sınırında ortalanmış olduğunu belirtmek için.  
  
     Aşağıdaki çizimde, sonuçta elde edilen dikdörtgen gösterir.  
  
     ![Kalemler](../../../../docs/framework/winforms/advanced/media/pens2.gif "pens2")  
  
     [!code-csharp[System.Drawing.UsingAPen#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### <a name="to-create-an-inset-pen"></a>Bir iç metin kalem oluşturmak için  
  
-   Yeşil kalem hizalama önceki kod örneğinde üçüncü deyimi aşağıdaki gibi değiştirmek için:  
  
     [!code-csharp[System.Drawing.UsingAPen#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     Artık piksel geniş yeşil bir çizgi olarak aşağıdaki çizimde gösterildiği gibi dikdörtgenin iç görüntülenir.  
  
     ![Kalemler](../../../../docs/framework/winforms/advanced/media/pens3.gif "pens3")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [Windows Forms’da Grafikler ve Çizim](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
