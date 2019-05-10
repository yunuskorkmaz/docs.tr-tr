---
title: 'Nasıl yapılır: Bir Gradyana Gama Düzeltmesi Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gradient brushes [Windows Forms], gamma correction
- gradients [Windows Forms], gamma correction
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
ms.openlocfilehash: e812e441233c1d29a67dac639048e20a659549f0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753562"
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a>Nasıl yapılır: Bir Gradyana Gama Düzeltmesi Uygulama
Fırçanın ayarlayarak gama düzeltmesi için doğrusal gradyan fırçası etkinleştirebilirsiniz <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> özelliğini `true`. Ayarlayarak gama düzeltmesi devre dışı bırakabilirsiniz <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> özelliğini `false`. Gama düzeltmesi, varsayılan olarak devre dışıdır.  
  
## <a name="example"></a>Örnek  

Aşağıdaki örnek, bir denetimin adlı bir yöntem <xref:System.Windows.Forms.Control.Paint> olay işleyicisi. Örneğin, doğrusal gradyan fırçası oluşturur ve iki dikdörtgenler doldurmak için bu fırça kullanır. İlk dikdörtgen gama düzeltmesi doldurulur ve İkinci dikdörtgeni gama düzeltmesi ile doldurulur.  
  
 Aşağıdaki çizimde, iki Dolu Dikdörtgen gösterilir. Gama düzeltmesi yok, üst dikdörtgen, ortadaki koyu görünür. Daha fazla Tekdüzen yoğunluğu olan gama düzeltmesi varsa, alt dikdörtgen görünür.  
  
 ![İki gradyan dolgulu dikdörtgenleri olan ve olmayan gama düzeltmesi.](./media/how-to-apply-gamma-correction-to-a-gradient/two-rectangles-gamma-gradient.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [Şekilleri Doldurmak için Gradyan Fırçası Kullanma](using-a-gradient-brush-to-fill-shapes.md)
