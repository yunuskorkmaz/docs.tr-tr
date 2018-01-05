---
title: "Nasıl yapılır: Eğik bir Yolu Düzleştirerek Çizgiye Dönüştürme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 334fc0fee7166f8f8c5c1db61d3b9e370da72f87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a>Nasıl yapılır: Eğik bir Yolu Düzleştirerek Çizgiye Dönüştürme
A <xref:System.Drawing.Drawing2D.GraphicsPath> nesnesi bir dizi satırları ve Bézier eğrileri saklar. Bir yol Eğriler (üç nokta, yaylar, eğriler) çeşitli türlerde ekleyebilirsiniz ancak yolunda saklanan önce her eğri bir Bézier eğrisi dönüştürülür. Bir yol düzleştirme bir dizi düz satır yolundaki her bir Bézier eğrisi dönüştürme oluşur. Aşağıdaki çizimde, önce ve sonra düzleştirme bir yolunu gösterir.  
  
 ![Düz çizgiler ve eğrilerle](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")  
  
### <a name="to-flatten-a-path"></a>Bir yolu düzleştirerek için  
  
-   çağrı <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> yöntemi bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesnesi. <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> Yöntemi düzleştirilmiş yol ve özgün yol arasındaki maksimum mesafeyi belirtir düzlük bağımsız değişkeni alır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 [Çizgiler, Eğriler ve Şekiller](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Yollar Oluşturma ve Çizme](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
