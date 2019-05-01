---
title: 'Nasıl yapılır: Özel Kesikli Çizgi Çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], custom
- lines [Windows Forms], drawing
- lines [Windows Forms], dashed
ms.assetid: cd0ed96a-cce4-47b9-b58a-3bae2e3d1bee
ms.openlocfilehash: 8dc1ad41cf8067bea5b811ca126ad29f5a600f69
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004373"
---
# <a name="how-to-draw-a-custom-dashed-line"></a>Nasıl yapılır: Özel Kesikli Çizgi Çizme
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] listelenen birkaç çizgi stili sağlar <xref:System.Drawing.Drawing2D.DashStyle> sabit listesi. Bu standart çizgi stilleri gereksinimlerinizi karşılamıyorsa, özel çizgi desenine oluşturabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Özel kesikli çizgi çizmek için bir dizi içinde uzunluklarını çizgi ve boşluk yerleştirin ve dizi değeri olarak atama <xref:System.Drawing.Pen.DashPattern%2A> özelliği bir <xref:System.Drawing.Pen> nesne. Aşağıdaki örnek dizisine göre özel kesikli çizgi çizer `{5, 2, 15, 4}`. Kalem genişliği 5 tarafından dizinin öğeleri çarpmak varsa `{25, 10, 75, 20}`. 25 ve 75 arasındaki uzunluğu görüntülenen tireler alternatif ve alanları, uzunluğu 10 ile 20 arasında alternatif.  
  
 Aşağıdaki çizimde, sonuçta elde edilen kesikli çizgiye gösterir. Böylece satırın son 25 birim miktarından daha kısa olacak şekilde son dash sahip unutmayın (405, 5).  
  
 ![Çizim kesikli çizgiye gösterir. ](./media/how-to-draw-a-custom-dashed-line/dashed-line-illustration.gif "pens6")  
  
 [!code-csharp[System.Drawing.UsingAPen#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bir Windows formu oluşturma ve form ele <xref:System.Windows.Forms.Control.Paint> olay. Önceki kodun içine yapıştırın <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](using-a-pen-to-draw-lines-and-shapes.md)
