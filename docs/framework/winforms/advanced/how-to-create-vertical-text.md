---
title: 'Nasıl yapılır: Dikey Metin Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- Windows Forms, drawing vertical text
- strings [Windows Forms], drawing vertical
- vertical text [Windows Forms], drawing
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
ms.openlocfilehash: 75f5d8faa4dc4b7e022cd6de2e6db49f4fa9030c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190229"
---
# <a name="how-to-create-vertical-text"></a>Nasıl yapılır: Dikey Metin Oluşturma
Kullanabileceğiniz bir <xref:System.Drawing.StringFormat> metin dikey yerine yatay olarak çizilecek belirtmek için nesne.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek değeri atar <xref:System.Drawing.StringFormatFlags.DirectionVertical> için <xref:System.Drawing.StringFormat.FormatFlags%2A> özelliği bir <xref:System.Drawing.StringFormat> nesne. Olduğunu <xref:System.Drawing.StringFormat> nesnesi <xref:System.Drawing.Graphics.DrawString%2A> yöntemi <xref:System.Drawing.Graphics> sınıfı. Değer <xref:System.Drawing.StringFormatFlags.DirectionVertical> üyesi <xref:System.Drawing.StringFormatFlags> sabit listesi.  
  
 Dikey metin aşağıda gösterilmiştir: 
  
 ![Dikey yazı tipi, metin gösteren grafik.](./media/how-to-create-vertical-text/vertical-font-text-graphic.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs>`e` , parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: GDI ile Metin Çizme](how-to-draw-text-with-gdi.md)
