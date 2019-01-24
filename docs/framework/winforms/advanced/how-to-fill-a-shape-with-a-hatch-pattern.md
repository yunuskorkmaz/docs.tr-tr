---
title: 'Nasıl yapılır: Bir şekli tarama deseniyle doldurma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
ms.openlocfilehash: 3fb5b443aac710a5490a238e2a571ed899dec463
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512404"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a>Nasıl yapılır: Bir şekli tarama deseniyle doldurma
Tarama deseniyle iki renkleri yapılır: arka plan ve arka plan üzerinde deseni oluşturan satırlar için. Kapalı bir şekli tarama deseniyle ile doldurmak için kullanmak bir <xref:System.Drawing.Drawing2D.HatchBrush> nesne. Aşağıdaki örnek, bir tarama deseniyle elips doldurmak gösterilmektedir:  
  
## <a name="example"></a>Örnek  
 <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> Oluşturucusu üç bağımsız değişken alır: Tarama stilini, tarama çizginin rengini ve arka plan rengi. Tarama stili bağımsız değişken, herhangi bir değer olabilir <xref:System.Drawing.Drawing2D.HatchStyle> sabit listesi. Elli'den fazla öğe içinde <xref:System.Drawing.Drawing2D.HatchStyle> numaralandırma; bunlardan birkaçını öğeler, aşağıdaki listede gösterilir:  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 Dolu Elips aşağıda gösterilmiştir.  
  
 ![Tarama desen](../../../../docs/framework/winforms/advanced/media/hatch1.png "hatch1")  
  
 [!code-csharp[System.Drawing.UsingABrush#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Şekilleri Doldurmak için Fırça Kullanma](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
