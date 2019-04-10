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
ms.openlocfilehash: 48dd1d76a42661df6ba642c032c991be4d6a2900
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339937"
---
# <a name="how-to-manually-render-buffered-graphics"></a>Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle İşleme
Kendi arabelleğe alınan grafikleri yönetiyorsanız oluşturabilmek ve grafik arabellekleri işleme olması gerekir. Örneklerini oluşturabilirsiniz <xref:System.Drawing.BufferedGraphics> yüzeyleri ekranda çizim çağrısı yaparak ilişkili sınıf <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> yöntemi. Bu yöntem, oluşturur bir <xref:System.Drawing.BufferedGraphics> bir form veya denetim gibi bir belirli bir işleme yüzeyi ile ilişkili olan örneği. Oluşturduktan sonra bir <xref:System.Drawing.BufferedGraphics> örneğini temsil eden aracılığıyla arabelleğe grafik çizebilir <xref:System.Drawing.BufferedGraphics.Graphics%2A> özelliği. Tüm grafik işlemleri gerçekleştirdikten sonra arabellek içeriği ekrana çağırarak kopyalayabilirsiniz <xref:System.Drawing.BufferedGraphics.Render%2A> yöntemi.  
  
> [!NOTE]
>  Kendi işleme gerçekleştirirseniz artışı yalnızca hafif olabilir, ancak bellek kullanımı artacaktır.  
  
### <a name="to-manually-display-buffered-graphics"></a>Arabelleğe alınan grafikleri elle görüntülemek için  
  
1. Örneğine bir başvuru elde <xref:System.Drawing.BufferedGraphicsContext> sınıfı. Daha fazla bilgi için [nasıl yapılır: Arabelleğe alınan grafikleri elle yönetme](how-to-manually-manage-buffered-graphics.md).  
  
2. Bir örneğini oluşturmak <xref:System.Drawing.BufferedGraphics> çağırarak sınıfı <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> yöntemini aşağıdaki kod örneğinde gösterildiği gibi.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3. Ayarlayarak grafik arabelleği için grafik çizim <xref:System.Drawing.BufferedGraphics.Graphics%2A> özelliği. Örneğin:  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4. Tüm grafik arabellek çizim, işlemlerini tamamladıktan sonra çağrı <xref:System.Drawing.BufferedGraphics.Render%2A> arabellek ya da o arabelleğe veya belirtilen bir çizim yüzeyi için aşağıdaki kod örneğinde gösterildiği gibi ilişkili çizim yüzeyini işlemek için yöntemi.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5. Grafik tamamlanmış işleme olduktan sonra çağrı `Dispose` metodunda <xref:System.Drawing.BufferedGraphics> sistem kaynakları serbest örneği.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphics>
- [İki Kez Arabelleğe Alınan Grafikler](double-buffered-graphics.md)
- [Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle Yönetme](how-to-manually-manage-buffered-graphics.md)
