---
title: "Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle İşleme"
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
- flicker [Windows Forms], reducing by manually rendering graphics
- graphics [Windows Forms], rendering
ms.assetid: 5192295e-bd8e-45f7-8bd6-5c4f6bd21e61
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3a5d06da3a398782b0285fb55807df5832cf771
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manually-render-buffered-graphics"></a>Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle İşleme
Kendi arabelleğe alınan grafikleri yönetiyorsanız, oluşturma ve grafik arabellekleri işlemek olması gerekir. Örneklerini oluşturabilirsiniz <xref:System.Drawing.BufferedGraphics> yüzeyleri ekranınızda çizim çağırarak ilişkili sınıfı <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> yöntemi. Bu yöntem oluşturur bir <xref:System.Drawing.BufferedGraphics> bir form veya denetim gibi belirli işleme yüzeyine ile ilişkili olan örneği. Oluşturduktan sonra bir <xref:System.Drawing.BufferedGraphics> örneği çizim grafik temsil eden aracılığıyla arabelleğine <xref:System.Drawing.BufferedGraphics.Graphics%2A> özelliği. Tüm grafik işlemleri gerçekleştirdikten sonra arabellek içeriğini ekrana çağırarak kopyalayabilirsiniz <xref:System.Drawing.BufferedGraphics.Render%2A> yöntemi.  
  
> [!NOTE]
>  Kendi işleme gerçekleştirirseniz artış yalnızca küçük olabilir ancak bellek tüketimi artacaktır.  
  
### <a name="to-manually-display-buffered-graphics"></a>El ile görüntülenecek grafik arabelleğe alındı.  
  
1.  Örneği için bir başvuru elde <xref:System.Drawing.BufferedGraphicsContext> sınıfı. Daha fazla bilgi için bkz: [nasıl yapılır: el ile arabelleğe alınan grafikleri yönetme](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).  
  
2.  Bir örneğini oluşturmak <xref:System.Drawing.BufferedGraphics> çağırarak sınıfı <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> aşağıdaki kod örneğinde gösterildiği gibi yöntemi.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3.  Grafik ayarlayarak grafik arabelleğe çizin <xref:System.Drawing.BufferedGraphics.Graphics%2A> özelliği. Örneğin:  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4.  Tüm grafik arabelleğine çizim, işlemlerini tamamladıktan sonra arama <xref:System.Drawing.BufferedGraphics.Render%2A> arabellek ya da bu arabelleği ile ya da belirtilen bir çizim yüzeyini için aşağıdaki kod örneğinde gösterildiği gibi ilişkili çizim yüzeyini işlemek için yöntem.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5.  Tamamlanan işleme grafik olduktan sonra arama `Dispose` yöntemi <xref:System.Drawing.BufferedGraphics> sistem kaynakları serbest örneği.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.BufferedGraphicsContext>  
 <xref:System.Drawing.BufferedGraphics>  
 [İki Kez Arabelleğe Alınan Grafikler](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle Yönetme](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)
