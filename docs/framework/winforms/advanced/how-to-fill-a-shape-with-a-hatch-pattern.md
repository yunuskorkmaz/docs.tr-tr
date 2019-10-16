---
title: 'Nasıl yapılır: Bir Şekli Tarama Deseniyle Doldurma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
ms.openlocfilehash: b80708f0ce722b1809fe49190639231e7e4c8329
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320066"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a>Nasıl yapılır: Bir Şekli Tarama Deseniyle Doldurma
İki renkten bir tarama kalıbı yapılır: biri arka plan ve diğeri arka plan üzerinde model oluşturan satırlar için. Kapalı bir şekli tarama düzeniyle doldurmanız için <xref:System.Drawing.Drawing2D.HatchBrush> nesnesi kullanın. Aşağıdaki örnek, bir elipsin bir tarama düzeniyle nasıl doldurulacağını göstermektedir:  
  
## <a name="example"></a>Örnek  
 @No__t-0 Oluşturucusu üç bağımsız değişken alır: tarama stili, tarama çizgisinin rengi ve arka plan rengi. Tarama stili bağımsız değişkeni <xref:System.Drawing.Drawing2D.HatchStyle> numaralandırmasından herhangi bir değer olabilir. @No__t-0 numaralandırmasında 50 taneden fazla öğe var; Bu öğelerin bazıları aşağıdaki listede gösteriliyor:  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 Aşağıdaki çizimde doldurulmuş elips gösterilmektedir.  
  
  ![Bir tarama deseninin doldurulduğu bir elips ekran görüntüsü.](./media/how-to-fill-a-shape-with-a-hatch-pattern/ellipse-filled-hatch.png "hatch1")
  
 [!code-csharp[System.Drawing.UsingABrush#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnek, Windows Forms kullanımı için tasarlanmıştır ve <xref:System.Windows.Forms.Control.Paint> olay işleyicisinin parametresi olan <xref:System.Windows.Forms.PaintEventArgs> @ no__t-1 ' i gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şekilleri Doldurmak için Fırça Kullanma](using-a-brush-to-fill-shapes.md)
