---
title: 'Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle Yönetme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually managing graphics
- graphics [Windows Forms], managing buffered
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
ms.openlocfilehash: 6010d52750b20c07db51917621f8643e9d9b47d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968599"
---
# <a name="how-to-manually-manage-buffered-graphics"></a>Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle Yönetme
Daha gelişmiş çift arabelleğe alma senaryolarında, kendi çift arabelleğe alma mantığınızı uygulamak için .NET Framework sınıflarını kullanabilirsiniz. Tek grafik arabelleklerinin <xref:System.Drawing.BufferedGraphicsContext> dağıtılmasından ve yönetiminden sorumlu sınıf, sınıftır. Her uygulamanın, bu uygulama için <xref:System.Drawing.BufferedGraphicsContext> varsayılan iki arabelleğe alma işleminin tümünü yöneten kendi varsayılanı vardır. Çağırarak, <xref:System.Drawing.BufferedGraphicsManager.Current%2A>bu örneğe bir başvuru alabilirsiniz.  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a>Varsayılan BufferedGraphicsContext öğesine bir başvuru almak için  
  
- Aşağıdaki kod örneğinde gösterildiği gibi özelliğiayarlayın.<xref:System.Drawing.BufferedGraphicsManager.Current%2A>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    > Sınıfından aldığınız <xref:System.Drawing.BufferedGraphicsContext> `Dispose` başvuruüzerindeyönteminiçağırmanızgerekmez<xref:System.Drawing.BufferedGraphicsManager> . , <xref:System.Drawing.BufferedGraphicsManager> Varsayılan<xref:System.Drawing.BufferedGraphicsContext> örnekler için tüm bellek ayırmayı ve dağıtımını işler.  
  
     Animasyon gibi grafiksel olarak yoğun uygulamalarda, bazen tarafından <xref:System.Drawing.BufferedGraphicsContext> <xref:System.Drawing.BufferedGraphicsContext> <xref:System.Drawing.BufferedGraphicsManager>sağlanması yerine adanmış bir kullanarak performansı artırabilirsiniz. Bu, uygulama tarafından tüketilen bellek daha büyük olsa da, uygulama ile ilişkili diğer tüm arabelleğe alınmış grafiklerin yönetilmesi için performans yükünü tek tek oluşturup yönetmenize olanak sağlar.  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a>Adanmış bir BufferedGraphicsContext oluşturmak için  
  
- Aşağıdaki kod örneğinde gösterildiği gibi, <xref:System.Drawing.BufferedGraphicsContext> sınıfının yeni bir örneğini bildirin ve oluşturun.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.BufferedGraphicsContext>
- [İki Kez Arabelleğe Alınan Grafikler](double-buffered-graphics.md)
- [Nasıl yapılır: Arabelleğe alınan grafikleri elle Işleme](how-to-manually-render-buffered-graphics.md)
