---
title: 'Nasıl yapılır: Açık şekilleri doldurun'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
ms.openlocfilehash: e9743d3268a7a2acfb6266872c3346a05269c369
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702739"
---
# <a name="how-to-fill-open-figures"></a>Nasıl yapılır: Açık şekilleri doldurun
Geçirerek bir yol doldurmak için bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesnesini <xref:System.Drawing.Graphics.FillPath%2A> yöntemi. <xref:System.Drawing.Graphics.FillPath%2A> Yöntemi doldurur yolun dolgu mod (diğer veya sargı) göre şu anda yolunu ayarlayın. Yolun herhangi bir açık şekilleri varsa, bu değerleri gibi kapalıyken yolu doldurulur. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] bir şekil için başlangıç noktası, bitiş noktasından düz bir çizgi çizerek kapatır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir açık şekil (yay) ve bir kapalı şekle (bir elips) sahip bir yol oluşturur. <xref:System.Drawing.Graphics.FillPath%2A> Yöntemi olan varsayılan dolgu modda göre yolu doldurur <xref:System.Drawing.Drawing2D.FillMode.Alternate>.  
  
 Örnek kodun çıktısı aşağıdaki çizimde gösterilmektedir. Yol doldurulmuş olduğunu unutmayın (göre <xref:System.Drawing.Drawing2D.FillMode.Alternate>) alacağı bitiş noktasından düz bir çizgi, başlangıç noktası için tarafından açık şekilde kapatıldı.  
  
 ![Dolgu açma yolu](./media/fillopenpath.png "FillOpenPath")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Drawing2D.GraphicsPath>
- [GDI+'da Grafik Yolları](graphics-paths-in-gdi.md)
