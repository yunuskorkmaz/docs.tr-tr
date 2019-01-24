---
title: 'Nasıl yapılır: Arabelleğe alınan grafikleri elle yönetme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually managing graphics
- graphics [Windows Forms], managing buffered
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
ms.openlocfilehash: b27a013d2cf66fb12365bffc35a07ed32bc25a2e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554497"
---
# <a name="how-to-manually-manage-buffered-graphics"></a>Nasıl yapılır: Arabelleğe alınan grafikleri elle yönetme
Daha gelişmiş çift arabelleğe alma senaryolar için kullanabileceğiniz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] kendi iki kez arabelleğe alma mantığını uygulamak için sınıflar. Ayırma ve tek bir grafik arabellekleri yönetmekten sorumlu bir sınıfı <xref:System.Drawing.BufferedGraphicsContext> sınıfı. Her uygulamanın kendi varsayılan sahip <xref:System.Drawing.BufferedGraphicsContext> , yöneten tüm çift bu uygulama için arabelleğe varsayılan. Çağırarak bu örneğe bir başvuru alabilirsiniz <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a>BufferedGraphicsContext varsayılan bir başvuru almak için  
  
-   Ayarlama <xref:System.Drawing.BufferedGraphicsManager.Current%2A> özelliği, aşağıdaki kod örneğinde gösterildiği gibi.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    >  Çağrı gerekmez `Dispose` metodunda <xref:System.Drawing.BufferedGraphicsContext> , alırsınız başvuru <xref:System.Drawing.BufferedGraphicsManager> sınıfı. <xref:System.Drawing.BufferedGraphicsManager> Tüm bellek ayırma ve dağıtım için varsayılan işleme <xref:System.Drawing.BufferedGraphicsContext> örnekleri.  
  
     Animasyon gibi grafik açısından yoğun uygulamalar için bazen bir adanmış kullanarak performansı artırabilir <xref:System.Drawing.BufferedGraphicsContext> yerine <xref:System.Drawing.BufferedGraphicsContext> tarafından sağlanan <xref:System.Drawing.BufferedGraphicsManager>. Bu, oluşturmak ve uygulama tarafından kullanılan bellek daha büyük olacaktır ancak uygulamanız ile ilişkili tüm diğer arabelleğe alınan grafikleri yönetme performans yükü olmaksızın grafik arabellekleri tek tek yönetmek sağlar.  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a>Adanmış BufferedGraphicsContext oluşturmak için  
  
-   Bildirme ve yeni bir örneğini oluşturma <xref:System.Drawing.BufferedGraphicsContext> , aşağıdaki kod örneğinde gösterildiği gibi sınıf.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.BufferedGraphicsContext>
- [İki Kez Arabelleğe Alınan Grafikler](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)
- [Nasıl yapılır: Arabelleğe alınan grafikleri elle işleme](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)
