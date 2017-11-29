---
title: "Çizgi ve Dolgularda Alfa Karışım Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lines [Windows Forms], adding transparency
- examples [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with lines
- alpha blending
- lines [Windows Forms], alpha blending
- fills [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with fills
- shapes [Windows Forms], adding transparency
ms.assetid: 5440f48c-3ac9-44c3-b170-c1c110bdbab8
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5b3c0ee3ec82d4d8447c43b7dc9b275591ebe890
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="alpha-blending-lines-and-fills"></a>Çizgi ve Dolgularda Alfa Karışım Kullanma
İçinde [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], bir renk 32-bit 8 bit her alfa, kırmızı, yeşil ve mavi ile değerdir. Renk saydam alfa değeri gösterir — için renk karıştırılan arka plan rengiyle uzantı. Alfa değerleri aralık 0 ile 255, 0 tamamen saydam rengi temsil ettiği ile 255 arasında bir tam olarak donuk rengi temsil eder.  
  
 Alfa karıştırma piksel piksel karıştırma kaynak ve arka plan rengi verilerini olur. Belirtilen kaynak rengin üç bileşenlerinin (kırmızı, yeşil, mavi) her biri aşağıdaki formülü göre arka plan rengi karşılık gelen bileşeni ile karıştırılan:  
  
 displayColor sourceColor × alfa = / 255 + backgroundColor × (255 – alfa) / 255  
  
 Örneğin, kaynak rengi kırmızı bileşeninin 150 ve arka plan rengi kırmızı bileşeninin 100 varsayalım. Alfa değeri 200 ise, sonuç rengi kırmızı bileşeninin aşağıdaki gibi hesaplanır:  
  
 150 × 200 / 255 + 100 × (255 – 200) / 255 = 139  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: donuk ve yarı saydam çizgiler çizme](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)  
 Alfa karışık çizgiler çizme gösterilmektedir.  
  
 [Nasıl yapılır: donuk ve yarı saydam fırçalarla çizme](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 Alfa karışım fırçalar ile açıklanmaktadır.  
  
 [Nasıl yapılır: denetim Alfa karışım için birleştirme modunu kullanma](../../../../docs/framework/winforms/advanced/how-to-use-compositing-mode-to-control-alpha-blending.md)  
 Alfa karıştırma kullanarak denetlemek açıklar <xref:System.Drawing.Drawing2D.CompositingMode>.  
  
 [Nasıl yapılır: görüntüleri alfa değerleri ayarlamak için renk matrisi kullanma](../../../../docs/framework/winforms/advanced/how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 Nasıl kullanılacağı açıklanmaktadır bir <xref:System.Drawing.Imaging.ColorMatrix> Alfa karışım denetlemek için nesne.
