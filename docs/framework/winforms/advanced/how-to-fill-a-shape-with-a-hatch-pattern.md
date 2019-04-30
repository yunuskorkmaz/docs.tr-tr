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
ms.openlocfilehash: f5399c4151b335090f4b93be041375b8c2781afa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781353"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a>Nasıl yapılır: Bir Şekli Tarama Deseniyle Doldurma
Tarama deseniyle iki renkleri yapılır: arka plan ve arka plan üzerinde deseni oluşturan satırlar için. Kapalı bir şekli tarama deseniyle ile doldurmak için kullanmak bir <xref:System.Drawing.Drawing2D.HatchBrush> nesne. Aşağıdaki örnek, bir tarama deseniyle elips doldurmak gösterilmektedir:  
  
## <a name="example"></a>Örnek  
 <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> Oluşturucusu üç bağımsız değişken alır: Tarama stilini, tarama çizginin rengini ve arka plan rengi. Tarama stili bağımsız değişken, herhangi bir değer olabilir <xref:System.Drawing.Drawing2D.HatchStyle> sabit listesi. Elli'den fazla öğe içinde <xref:System.Drawing.Drawing2D.HatchStyle> numaralandırma; bunlardan birkaçını öğeler, aşağıdaki listede gösterilir:  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 Dolu Elips aşağıda gösterilmiştir.  
  
 ![Tarama desen](./media/hatch1.png "hatch1")  
  
 [!code-csharp[System.Drawing.UsingABrush#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şekilleri Doldurmak için Fırça Kullanma](using-a-brush-to-fill-shapes.md)
