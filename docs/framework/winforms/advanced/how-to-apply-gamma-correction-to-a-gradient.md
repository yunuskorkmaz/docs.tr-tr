---
title: 'Nasıl yapılır: Bir Gradyana gama düzeltmesi uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gradient brushes [Windows Forms], gamma correction
- gradients [Windows Forms], gamma correction
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
ms.openlocfilehash: e7205058bc2b93ac453b8c37bfc8d5236433158d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708098"
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a>Nasıl yapılır: Bir Gradyana gama düzeltmesi uygulama
Fırçanın ayarlayarak gama düzeltmesi için doğrusal gradyan fırçası etkinleştirebilirsiniz <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> özelliğini `true`. Ayarlayarak gama düzeltmesi devre dışı bırakabilirsiniz <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> özelliğini `false`. Gama düzeltmesi, varsayılan olarak devre dışıdır.  
  
## <a name="example"></a>Örnek  
 Örneğin, doğrusal gradyan fırçası oluşturur ve iki dikdörtgenler doldurmak için bu fırça kullanır. İlk dikdörtgen gama düzeltmesi doldurulur ve İkinci dikdörtgeni gama düzeltmesi ile doldurulur.  
  
 Aşağıdaki çizimde, iki Dolu Dikdörtgen gösterilir. Gama düzeltmesi yok, üst dikdörtgen, ortadaki koyu görünür. Daha fazla Tekdüzen yoğunluğu olan gama düzeltmesi varsa, alt dikdörtgen görünür.  
  
 ![Gradyan](./media/gammagradient1.png "gammagradient1")  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Drawing2D.LinearGradientBrush>
- [Şekilleri Doldurmak için Gradyan Fırçası Kullanma](using-a-gradient-brush-to-fill-shapes.md)
