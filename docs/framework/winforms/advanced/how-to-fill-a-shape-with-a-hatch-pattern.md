---
title: "Nasıl yapılır: Bir Şekli Tarama Deseniyle Doldurma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 36ee5b7152dabc7dcd1e0c844e8549eb03aa0045
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a>Nasıl yapılır: Bir Şekli Tarama Deseniyle Doldurma
Tarama deseniyle iki renkten yapılır: arka plan, diğeri desen arka plan üzerinde form satırlar için için. Kapalı bir şekli tarama deseniyle ile doldurmak için kullanın bir <xref:System.Drawing.Drawing2D.HatchBrush> nesnesi. Aşağıdaki örnek, bir elips ile tarama deseniyle doldurma gösterilmiştir:  
  
## <a name="example"></a>Örnek  
 <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> Oluşturucusu üç bağımsız değişkeni alır: Tarama stilini, tarama çizginin rengini ve arka plan rengi. Tarama stili bağımsız değişken arasında bir değer olabilir <xref:System.Drawing.Drawing2D.HatchStyle> numaralandırması. İçinde birden fazla elli öğe <xref:System.Drawing.Drawing2D.HatchStyle> numaralandırma; bu birkaç öğeleri aşağıdaki listede gösterilir:  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 Aşağıdaki çizimde doldurulmuş elips gösterir.  
  
 ![Tarama deseni](../../../../docs/framework/winforms/advanced/media/hatch1.png "hatch1")  
  
 [!code-csharp[System.Drawing.UsingABrush#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şekilleri doldurmak için fırça kullanma](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
