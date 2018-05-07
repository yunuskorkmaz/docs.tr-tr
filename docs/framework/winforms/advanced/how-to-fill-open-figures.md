---
title: 'Nasıl Yapılır: Açık Şekilleri Doldurma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
ms.openlocfilehash: b7422ae2a4dc4d59fd337ab2294caa0d65057bae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-fill-open-figures"></a>Nasıl Yapılır: Açık Şekilleri Doldurma
Geçirerek bir yolu doldurabilir bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesnesinin <xref:System.Drawing.Graphics.FillPath%2A> yöntemi. <xref:System.Drawing.Graphics.FillPath%2A> Yöntemi yolunu ayarlanmış yolun dolgu modunu (alternatif veya sarma) göre doldurur. Tüm açık şekilleri yol varsa, bu rakamları kapatılan gibi yolun girilir. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] bir şekil, başlangıç noktası bitiş noktasından bir çizgide çizerek kapatır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir açık şekli (yay) ve bir kapalı şekli (elips) sahip bir yol oluşturur. <xref:System.Drawing.Graphics.FillPath%2A> Yöntemi doldurur olan varsayılan doldurma modu göre yolu <xref:System.Drawing.Drawing2D.FillMode.Alternate>.  
  
 Aşağıdaki çizimde örnek kod çıktısını gösterir. Yolun girilir unutmayın (göre <xref:System.Drawing.Drawing2D.FillMode.Alternate>) sanki açık şekilde bir çizgide bitiş noktasından, başlangıç noktası tarafından kapatıldı.  
  
 ![Dolgu açma yolu](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 [GDI+'da Grafik Yolları](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)
