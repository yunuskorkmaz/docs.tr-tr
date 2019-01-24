---
title: 'Nasıl yapılır: Görselin Çizim İçeriğini Numaralandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: a3131b6c86b0f6a7aa79cca305b9c3b2496346f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561954"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a>Nasıl yapılır: Görselin Çizim İçeriğini Numaralandırma
<xref:System.Windows.Media.Drawing> Nesne içeriğini numaralandırma için nesne modeli sağlar bir <xref:System.Windows.Media.Visual>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> alınacak yöntemi <xref:System.Windows.Media.DrawingGroup> değerini bir <xref:System.Windows.Media.Visual> ve onu numaralandırır.  
  
> [!NOTE]
>  Görselin içeriklerini sıralanırken alınırken <xref:System.Windows.Media.Drawing> nesneleri ve vektör grafik yönerge listesi olarak işleme verileri temel alınan gösterimini değil. Daha fazla bilgi için [WPF Grafik işlemeye genel bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [Çizim Nesnelerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
- [WPF Grafik İşlemeye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
