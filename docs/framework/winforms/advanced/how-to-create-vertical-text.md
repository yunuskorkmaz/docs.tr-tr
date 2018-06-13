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
ms.openlocfilehash: 7d66bf147a220bdcdfd32a703d3407817a184a54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521478"
---
# <a name="how-to-create-vertical-text"></a>Nasıl yapılır: Dikey Metin Oluşturma
Kullanabileceğiniz bir <xref:System.Drawing.StringFormat> nesne metin dikey yerine yatay olarak çizileceğini belirtin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek değeri atar <xref:System.Drawing.StringFormatFlags.DirectionVertical> için <xref:System.Drawing.StringFormat.FormatFlags%2A> özelliği bir <xref:System.Drawing.StringFormat> nesnesi. Olduğunu <xref:System.Drawing.StringFormat> nesne iletilir <xref:System.Drawing.Graphics.DrawString%2A> yöntemi <xref:System.Drawing.Graphics> sınıfı. Değer <xref:System.Drawing.StringFormatFlags.DirectionVertical> üyesi <xref:System.Drawing.StringFormatFlags> numaralandırması.  
  
 Dikey metin aşağıda gösterilmektedir.  
  
 ![Yazı tipleri metin](../../../../docs/framework/winforms/advanced/media/csfontstext5.png "csfontstext5")  
  
 [!code-csharp[System.Drawing.FontsAndText#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e` , parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: GDI ile Metin Çizme](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
