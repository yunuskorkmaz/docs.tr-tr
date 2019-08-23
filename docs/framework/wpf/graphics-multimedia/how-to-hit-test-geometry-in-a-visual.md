---
title: 'Nasıl yapılır: Görselde Tıklama Testi Geometrisi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects comprising Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], visual objects comprising
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
ms.openlocfilehash: 52b9b99b0af38d797e4a3c98dc0979211c930c1f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923374"
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a>Nasıl yapılır: Görselde Tıklama Testi Geometrisi
Bu örnek, bir veya daha fazla <xref:System.Windows.Media.Geometry> nesneden oluşan bir görsel nesne üzerinde isabet testinin nasıl gerçekleştirileceğini gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.Media.DrawingGroup> <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> yöntemini kullanan bir görsel nesneden nasıl alınacağını gösterir. Ardından, <xref:System.Windows.Media.DrawingGroup> hangi geometrinin isabet olduğunu anlamak için içindeki her çizimin işlenmiş içeriği üzerinde bir isabet testi gerçekleştirilir.  
  
> [!NOTE]
> Çoğu durumda, bir noktanın bir görselin <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> işlenmiş içeriğiyle kesişip kesişmediğini anlamak için yöntemini kullanırsınız.  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 Yöntemi, belirtilen <xref:System.Windows.Point> veya<xref:System.Windows.Media.Geometry>kullanarak test 'e isabet etmenize olanak tanıyan aşırı yüklenmiş bir yöntemdir. <xref:System.Windows.Media.Geometry.FillContains%2A> Bir geometri konturluysa, vuruş, dolgulu sınırların dışına genişletebilir. Bu durumda, öğesine <xref:System.Windows.Media.Geometry.StrokeContains%2A> <xref:System.Windows.Media.Geometry.FillContains%2A>ek olarak çağırmak isteyebilirsiniz.  
  
 Ayrıca, Bezier düzleştirme amacıyla <xref:System.Windows.Media.ToleranceType> kullanılan bir de sağlayabilirsiniz.  
  
> [!NOTE]
> Bu örnek, geometriye uygulanabilen dönüşümler veya kırpma işlemleri hesaba eklemez. Buna ek olarak, doğrudan ilişkili bir çizim olmadığından, bu örnek stilli bir denetimle çalışmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Katmanda Tıklama Testi](hit-testing-in-the-visual-layer.md)
- [Geometriyi Parametre Olarak Kullanan Tıklama Testi](how-to-hit-test-using-geometry-as-a-parameter.md)
