---
title: 'Nasıl yapılır: Çizgi çizmek için kalem kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
ms.assetid: 0828c331-a438-4bdd-a4d6-3ef1e59e8795
ms.openlocfilehash: 3af91611eef4b97dc3461ad8cd7e36c7aa10a16f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713377"
---
# <a name="how-to-use-a-pen-to-draw-lines"></a>Nasıl yapılır: Çizgi çizmek için kalem kullanma
Çizgi çizmek için gereken bir <xref:System.Drawing.Graphics> nesnesi ve bir <xref:System.Drawing.Pen> nesne. <xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi ve <xref:System.Drawing.Pen> nesne satır, renk ve genişlik gibi özellikleri depolar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir çizgi çizer (20, 10) için (300, 100). İlk deyim kullanır <xref:System.Drawing.Pen.%23ctor%2A> siyah kalem oluşturmak için sınıf oluşturucusu. Geçirilen bir bağımsız değişken <xref:System.Drawing.Pen.%23ctor%2A> Oluşturucusu bir <xref:System.Drawing.Color> ile oluşturulan nesne <xref:System.Drawing.Color.FromArgb%2A> yöntemi. Oluşturmak için kullanılan değerleri <xref:System.Drawing.Color> nesne — (255, 0, 0, 0) — rengi alfa, kırmızı, yeşil ve mavi bileşenlerinin karşılık gelir. Bu değerleri bir donuk siyah kalem tanımlayın.  
  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Pen>
- [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](using-a-pen-to-draw-lines-and-shapes.md)
- [GDI+'da Kalemler, Çizgiler ve Dikdörtgenler](pens-lines-and-rectangles-in-gdi.md)
