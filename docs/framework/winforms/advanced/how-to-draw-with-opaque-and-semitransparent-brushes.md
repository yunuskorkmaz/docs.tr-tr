---
title: "Nasıl yapılır: Donuk ve Yarı Saydam Fırçalarla Çizme"
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
- semi-transparent shapes [Windows Forms], drawing
- transparency [Windows Forms], semi-transparent shapes
- alpha blending [Windows Forms], brush
- brushes [Windows Forms], using semi-transparent
ms.assetid: a4f6f6b8-3bc8-440a-84af-d62ef0f8ff40
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a7cae1284fbcabf70976866338ba37c6ee5710e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a>Nasıl yapılır: Donuk ve Yarı Saydam Fırçalarla Çizme
Bir şekli doldurduğunuzda geçmesi gereken bir <xref:System.Drawing.Brush> dolgu yöntemlerinden birini nesnesine <xref:System.Drawing.Graphics> sınıfı. Bir parametresinin <xref:System.Drawing.SolidBrush.%23ctor%2A> Oluşturucusu olan bir <xref:System.Drawing.Color> nesnesi. Donuk bir şekli doldurmak için 255 rengin alfa bileşenini ayarlayın. Yarı saydam bir şekli doldurmak için 1 ile 254 arasında herhangi bir değere alfa bileşenini ayarlayın.  
  
 Yarı saydam bir şekli doldurduğunuzda şeklinin rengi arka plan renkleri ile karıştırılan. Alfa bileşeni şekli ve arka plan renklerini nasıl karma belirtir; alfa değerleri 0 yakın daha fazla ağırlık arka plan renkleri yerleştirin ve alfa değerleri 255 yakın şekil rengine üzerinde daha fazla ağırlık yerleştirin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir bit eşlem çizer ve bit eşlem üst üste üç elips doldurur. İlk elipsin donuk 255 alfa bir bileşeninin kullanır. Yarı saydam şekilde ikinci ve üçüncü elipsleri 128, alfasayısal bir bileşeninin kullanın; üç nokta üzerinden arka plan görüntüsü görebilirsiniz. Ayarlar arama <xref:System.Drawing.Graphics.CompositingQuality%2A> özellik gama düzeltmesi ile birlikte yapılması üçüncü elipsin karıştırma eklenmesine neden olur.  
  
 Aşağıdaki çizimde, aşağıdaki kodu çıktısını gösterir.  
  
 ![Donuk ve yarı saydam](../../../../docs/framework/winforms/advanced/media/compqualellipse.png "compqualellipse")  
  
 [!code-csharp[System.Drawing.AlphaBlending#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms’da Grafikler ve Çizim](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Çizgi ve Dolgularda Alfa Karışım Kullanma](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 [Nasıl yapılır: Denetiminize Saydam Arka Plan Verme](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 [Nasıl yapılır: Donuk ve Yarı Saydam Çizgiler Çizme](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
