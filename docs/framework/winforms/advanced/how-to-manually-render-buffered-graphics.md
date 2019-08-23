---
title: 'Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually rendering graphics
- graphics [Windows Forms], rendering
ms.assetid: 5192295e-bd8e-45f7-8bd6-5c4f6bd21e61
ms.openlocfilehash: a6655652a7c5dedb8e183356688972c07a705cbc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931844"
---
# <a name="how-to-manually-render-buffered-graphics"></a>Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle İşleme
Kendi arabellekli grafiklerinizi yönetiyorsanız, grafik arabellekleri oluşturup işleyebilmeniz gerekecektir. Yöntemini çağırarak, <xref:System.Drawing.BufferedGraphics> <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> ekranınızda çizim yüzeyleriyle ilişkili sınıf örnekleri oluşturabilirsiniz. Bu yöntem, bir <xref:System.Drawing.BufferedGraphics> form veya denetim gibi belirli bir işleme yüzeyi ile ilişkili bir örnek oluşturur. Bir <xref:System.Drawing.BufferedGraphics> örnek oluşturduktan sonra, <xref:System.Drawing.BufferedGraphics.Graphics%2A> özelliği aracılığıyla temsil ettiği arabelleğe grafik çizebilirsiniz. Tüm grafik işlemlerini gerçekleştirdikten sonra, <xref:System.Drawing.BufferedGraphics.Render%2A> yöntemini çağırarak arabelleğin içeriğini ekrana kopyalayabilirsiniz.  
  
> [!NOTE]
> Kendi işleme gerçekleştirirseniz, bellek tüketimi artar, ancak artış yalnızca hafif olabilir.  
  
### <a name="to-manually-display-buffered-graphics"></a>Arabelleğe alınmış grafikleri el ile görüntüleme  
  
1. <xref:System.Drawing.BufferedGraphicsContext> Sınıfının bir örneğine bir başvuru alın. Daha fazla bilgi için [nasıl yapılır: Arabellekli grafikleri](how-to-manually-manage-buffered-graphics.md)el ile yönetin.  
  
2. Aşağıdaki kod örneğinde gösterildiği gibi <xref:System.Drawing.BufferedGraphics> <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> yöntemini çağırarak sınıfının bir örneğini oluşturun.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3. <xref:System.Drawing.BufferedGraphics.Graphics%2A> Özelliği ayarlayarak grafik arabelleğine grafik çizin. Örneğin:  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4. Grafik arabelleğine çizim işlemlerinizi tamamladıktan sonra, aşağıdaki kod örneğinde gösterildiği gibi, arabelleği işlemek için <xref:System.Drawing.BufferedGraphics.Render%2A> bu arabellek ile ilişkili çizim yüzeyine veya belirtilen çizim yüzeyine yönelik yöntemi çağırın.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5. Grafik oluşturmayı tamamladıktan sonra, sistem kaynaklarını serbest bırakmak `Dispose` için <xref:System.Drawing.BufferedGraphics> örneğinde yöntemi çağırın.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphics>
- [İki Kez Arabelleğe Alınan Grafikler](double-buffered-graphics.md)
- [Nasıl yapılır: Arabellekli grafikleri el ile yönetme](how-to-manually-manage-buffered-graphics.md)
