---
title: "Nasıl yapılır: Bir Gradyana Gama Düzeltmesi Uygulama"
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
- gradient brushes [Windows Forms], gamma correction
- gradients [Windows Forms], gamma correction
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2721a45381f2d0befe82d6d0db2630f3eae08d51
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a>Nasıl yapılır: Bir Gradyana Gama Düzeltmesi Uygulama
Gama düzeltme doğrusal gradyan fırçası için fırça ayarlayarak etkinleştirebilirsiniz <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> özelliğine `true`. Ayarlayarak gama düzeltmesi devre dışı bırakabilirsiniz <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> özelliğine `false`. Gama düzeltme varsayılan olarak devre dışıdır.  
  
## <a name="example"></a>Örnek  
 Örnek doğrusal gradyan fırçası oluşturur ve o fırça iki dikdörtgen doldurmak için kullanır. İlk dikdörtgen gama düzeltmesi girilir ve İkinci dikdörtgeni gama düzeltmesi ile doldurulur.  
  
 Aşağıdaki çizimde iki doldurulmuş dikdörtgen gösterir. Gama düzeltme yok, üst dikdörtgen ortadaki koyu görüntülenir. Gama düzeltme varsa, alt kısımdaki dikdörtgeni daha fazla Tekdüzen yoğunluğu olan görünüyor.  
  
 ![Gradyan](../../../../docs/framework/winforms/advanced/media/gammagradient1.png "gammagradient1")  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush>  
 [Şekilleri doldurmak için gradyan fırçası kullanma](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)
