---
title: 'Nasıl yapılır: Görselin Çizim İçeriğini Numaralandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 25aa0c3706005c1e16cedd7e06914db764545ebb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930079"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a>Nasıl yapılır: Görselin Çizim İçeriğini Numaralandırma
Nesnesi, içeriğini <xref:System.Windows.Media.Visual>listelemek için bir nesne modeli sağlar. <xref:System.Windows.Media.Drawing>  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> <xref:System.Windows.Media.DrawingGroup> değerini <xref:System.Windows.Media.Visual> almak ve numaralandırmak için yöntemini kullanır.  
  
> [!NOTE]
> Görselin içeriğini Numaralandırdığınızda, nesneleri, işleme verilerinin bir vektör grafik <xref:System.Windows.Media.Drawing> yönerge listesi olarak değil, temel gösterimini değil, alıyor olursunuz. Daha fazla bilgi için bkz. [WPF Grafik Işlemeye genel bakış](wpf-graphics-rendering-overview.md).  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [Çizim Nesnelerine Genel Bakış](drawing-objects-overview.md)
- [WPF Grafik İşlemeye Genel Bakış](wpf-graphics-rendering-overview.md)
