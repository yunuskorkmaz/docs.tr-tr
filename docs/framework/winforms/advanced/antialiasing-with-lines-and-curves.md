---
title: 'Nasıl yapılır: Çizgiler ve Eğrilerle Düzgünleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- antialiasing
- antialiasing [Windows Forms], smoothing modes
- GDI+, antialiasing
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
ms.openlocfilehash: 6ea49c591b43d3f70bfd39058fd5ee256c537ec2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725018"
---
# <a name="antialiasing-with-lines-and-curves"></a>Nasıl yapılır: Çizgiler ve Eğrilerle Düzgünleştirme
Kullanırken [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] bir çizgi çizmek için başlangıç noktası ve bitiş noktasını sağlar, ancak satırda tek tek her piksel hakkında hiçbir bilgi sağlamanız gerekmez. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] özel görüntü cihazında çizgisini göstermek için hangi piksel yanar belirlemek için görüntüleme sürücü yazılım ile birlikte çalışır.  
  
## <a name="aliasing"></a>Diğer ad kullanımı  
 (4, 2) noktadan noktaya (16, 10) giden düz kırmızı çizgi göz önünde bulundurun. Koordinat sistemi sol üst köşedeki kaynağına sahip ve ölçü piksel olduğunu varsayar. X ekseni aşağı sağ ve y ekseni noktaları işaret da varsayılır. Aşağıdaki çizimde, renkli bir arka plan üzerinde kırmızı çizgi genişletilmiş bir görünümünü gösterir.  
  
 ![Satır, hiçbir düzgünleştirme](./media/aboutgdip02-art33.gif "AboutGdip02_Art33")  
  
 Satır işlemek için kullanılan kırmızı donuk pikseldir. Satırda kısmen saydam piksel vardır. Bu tür bir çizgi işleme satır pürüzlü bir görünümünü sağlar ve bir Merdiven bakıma satırı görünür. Bir Merdiven içeren bir satırı temsil eden bu tekniği yumuşatma çağrılır Merdiven, teorik satırı için bir diğer addır.  
  
## <a name="antialiasing"></a>Düzgünleştirme  
 Bir satır işlemek için daha karmaşık bir teknik, kısmen saydam piksel donuk piksel ile birlikte kullanılması gerekir. Bazı blend'e kırmızı ve arka plan rengi, bağlı olarak ne kadar yakın satırına oldukları veya piksel saf kırmızı belirlenmesi. Bu tür bir işleme düzgünleştirme olarak adlandırılır ve İnsan gözüyle daha kesintisiz olarak algılar. bir satır sonuçlanır. Aşağıdaki çizim, belirli piksel antialiased çizgi oluşturmak için arka plan ile nasıl karışık gösterir.  
  
 ![Bir satır düzgünleştirme](./media/aboutgdip02-art34.gif "AboutGdip02_Art34")  
  
 Düzgünleştirme düzgünleştirme, olarak da bilinir, ayrıca eğrilere uygulanabilir. Aşağıdaki çizim düzleştirilmiş bir elips genişletilmiş bir görünümünü gösterir.  
  
 ![Düzgünleştirme Eğriler](./media/aboutgdip02-art35.gif "AboutGdip02_Art35")  
  
 Aşağıdaki çizimde aynı elips gerçek boyutuna, düzgünleştirme olmadan bir kez ve bir kez düzgünleştirme gösterir.  
  
 ![Düzgünleştirme örnek](./media/aboutgdip02-art36.gif "AboutGdip02_Art36")  
  
 Çizgiler ve eğrilerle düzgünleştirme kullanan çizmek için bir örneğini oluşturmak <xref:System.Drawing.Graphics> ayarlayın ve sınıf kendi <xref:System.Drawing.Graphics.SmoothingMode%2A> özelliğini <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> veya <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>. Ardından, söz konusu çizim yöntemlerden birini aynı çağrı <xref:System.Drawing.Graphics> sınıfı.  
  
 [!code-csharp[LinesCurvesAndShapes#81](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=nameWithType>
- [Çizgiler, Eğriler ve Şekiller](lines-curves-and-shapes.md)
- [Nasıl yapılır: Metinle düzgünleştirme kullanma](how-to-use-antialiasing-with-text.md)
