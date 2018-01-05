---
title: "Nasıl yapılır: Donuk ve Yarı Saydam Çizgiler Çizme"
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
- drawing [Windows Forms], lines
- transparency [Windows Forms], lines
- lines [Windows Forms], drawing alpha blended
- alpha blending [Windows Forms], drawing lines
ms.assetid: 8f2508af-f495-4223-b5cc-646cbbb520eb
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a298458489968cf680a9d5f935d98afb470859ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-opaque-and-semitransparent-lines"></a>Nasıl yapılır: Donuk ve Yarı Saydam Çizgiler Çizme
Çizgi çizme zaman geçmesi gereken bir <xref:System.Drawing.Pen> nesnesini <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi <xref:System.Drawing.Graphics> sınıfı. Parametrelerden biri <xref:System.Drawing.Pen.%23ctor%2A> Oluşturucusu olan bir <xref:System.Drawing.Color> nesnesi. Opak bir çizgi çizmek için 255 rengin alfa bileşenini ayarlayın. Yarı saydam bir çizgi çizmek için 1 ile 254 arasında herhangi bir değere alfa bileşenini ayarlayın.  
  
 Arka plan üzerinde yarı saydam çizgi çizme, çizginin rengini arka plan renkleri ile karıştırılan. Alfa bileşeni, satır ve arka plan renklerini nasıl karma belirtir; alfa değerleri 0 yakın daha fazla ağırlık arka plan renkleri yerleştirin ve alfa değerleri 255 yakın çizgi rengi üzerinde daha fazla ağırlık yerleştirin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir bit eşlem çizer ve bit eşlem arka planı olarak kullanmak üç satır çizer. İlk satırı donuk 255 alfa bir bileşeninin kullanır. Yarı saydam şekilde ikinci ve üçüncü satırlarını 128, alfasayısal bir bileşeninin kullanın; arka plandaki resmin arkasını satırları görebilirsiniz. Ayarlar deyimi <xref:System.Drawing.Graphics.CompositingQuality%2A> özellik gama düzeltmesi ile birlikte yapılması üçüncü satır karıştırma eklenmesine neden olur.  
  
 Aşağıdaki çizimde, aşağıdaki kodu çıktısını gösterir.  
  
 ![Donuk ve yarı saydam](../../../../docs/framework/winforms/advanced/media/compqualline.png "compqualline")  
  
 [!code-csharp[System.Drawing.AlphaBlending#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.AlphaBlending#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çizgi ve Dolgularda Alfa Karışım Kullanma](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 [Nasıl yapılır: Denetiminize Saydam Arka Plan Verme](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 [Nasıl yapılır: Donuk ve Yarı Saydam Fırçalarla Çizme](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)
