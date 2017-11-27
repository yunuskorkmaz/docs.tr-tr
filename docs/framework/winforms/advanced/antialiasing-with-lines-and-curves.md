---
title: "Nasıl yapılır: Çizgiler ve Eğrilerle Düzgünleştirme"
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
- antialiasing
- antialiasing [Windows Forms], smoothing modes
- GDI+, antialiasing
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d69d635fbdd8720937cd189826c1496b8126ddef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="antialiasing-with-lines-and-curves"></a>Nasıl yapılır: Çizgiler ve Eğrilerle Düzgünleştirme
Kullandığınızda [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] bir çizgi çizmek için başlangıç noktası ve bitiş noktası satırının sağlar, ancak tek pikselleri hakkında hiçbir bilgi satırına sağlamak zorunda değilsiniz. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]belirli görüntü cihazında çizgisini göstermek için hangi piksel yanar belirlemek için görüntüleme sürücü yazılımı ile birlikte çalışır.  
  
## <a name="aliasing"></a>Diğer ad  
 (4, 2) noktadan noktaya (16, 10) gider düz kırmızı çizgi göz önünde bulundurun. Koordinat sistemi sol üst köşedeki kaynağına sahip ve ölçü piksel olduğunu varsayalım. Ayrıca x ekseni aşağı sağa ve y ekseni noktaları işaret varsayalım. Aşağıdaki çizimde bir renkli arka planda kırmızı çizgi büyütülmüş bir görünümünü gösterir.  
  
 ![Satır, hiçbir düzgünleştirme](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art33.gif "AboutGdip02_Art33")  
  
 Çizgiyi işlemek için kullanılan kırmızı donuk pikseldir. Satırda kısmen saydam piksel vardır. Satır bakıma bir Merdiven arar ve bu tür bir çizgi işleme satır basit bir görünüm sağlar. Bir Merdiven satırıyla temsil eden bu tekniği yumuşatma çağrılır; Merdiven teorik satırı için bir diğer ad değil.  
  
## <a name="antialiasing"></a>Düzgünleştirme  
 Bir satır işlemek için daha karmaşık bir teknik kısmen saydam piksel donuk piksel birlikte kullanılması gerekir. Piksel saf kırmızı şeklinde ayarlanır veya bazı karışım kırmızı ve arka plan rengi, bağlı olarak ne kadar yakın satırına oldukları. Bu tür bir işleme düzgünleştirme denir ve İnsan göz daha kesintisiz olarak algılar bir satır ile sonuçlanır. Aşağıdaki çizimde, belirli piksel antialiased satır üretmek için arka plan nasıl karıştırılan gösterir.  
  
 ![Çizgiyi düzgünleştirme](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art34.gif "AboutGdip02_Art34")  
  
 Yumuşatma, olarak da bilinir Düzgünleştirme eğrileri da uygulanabilir. Aşağıdaki çizimde bir düzleştirilmiş elips büyütülmüş bir görünümünü gösterir.  
  
 ![Düzgünleştirme eğrileri](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art35.gif "AboutGdip02_Art35")  
  
 Aşağıdaki çizimde aynı elips gerçek boyutuna, düzgünleştirme olmadan bir kez ve bir kez düzgünleştirme gösterir.  
  
 ![Düzgünleştirme örneği](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art36.gif "AboutGdip02_Art36")  
  
 Çizgiler ve eğrilerle düzgünleştirme kullanma çizmek için bir örneğini oluşturmak <xref:System.Drawing.Graphics> sınıfı ve ayarlayın, <xref:System.Drawing.Graphics.SmoothingMode%2A> özelliğine <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> veya <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>. Ardından çizim yöntemlerinden birini, aynı çağrı <xref:System.Drawing.Graphics> sınıfı.  
  
 [!code-csharp[LinesCurvesAndShapes#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=nameWithType>  
 [Çizgiler, eğriler ve şekiller](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Nasıl yapılır: metinle düzgünleştirme kullanma](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)
