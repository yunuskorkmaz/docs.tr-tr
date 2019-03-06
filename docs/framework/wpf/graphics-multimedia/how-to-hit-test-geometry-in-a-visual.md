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
ms.openlocfilehash: e51dd73a65666ffee5958325079e8f06f13ac61b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363806"
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a>Nasıl yapılır: Görselde Tıklama Testi Geometrisi
Bu örnekte, bir veya daha fazla oluşan görsel bir nesne üzerinde bir isabet sınaması gerçekleştirmeye gösterilmektedir <xref:System.Windows.Media.Geometry> nesneleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl alınacağını gösterir <xref:System.Windows.Media.DrawingGroup> kullanan visual nesnesinden <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> yöntemi. İsabet sınaması her çizim işlenmiş içeriği gerçekleştirilir <xref:System.Windows.Media.DrawingGroup> hangi geometri isabet ettiğini belirlemek için.  
  
> [!NOTE]
>  Çoğu durumda, kullanacağınız <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> bir noktadan herhangi bir görsel işlenmiş içeriği kesişip kesişmediğini belirlemek için yöntemi.  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 <xref:System.Windows.Media.Geometry.FillContains%2A> Yöntemdir belirtilen kullanarak tıklama testi olanak tanıyan aşırı yüklü bir yönteminiz <xref:System.Windows.Point> veya <xref:System.Windows.Media.Geometry>. Geometri konturlanan, vuruş dolgu sınırları dışında genişletebilirsiniz. Bu durumda, istediğiniz arama <xref:System.Windows.Media.Geometry.StrokeContains%2A> ek olarak <xref:System.Windows.Media.Geometry.FillContains%2A>.  
  
 De sağlayabilirsiniz bir <xref:System.Windows.Media.ToleranceType> Bezier düzleştirme amacıyla kullanılır.  
  
> [!NOTE]
>  Bu örnek dönüşümleri dikkate almaz veya kırpmayı geometriye uygulanabilir. Ayrıca, bu örnek, doğrudan ilişkili tüm çizimleri sahip olmadığından, stil uygulanmış bir denetimi ile çalışmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Görsel Katmanda Tıklama Testi](hit-testing-in-the-visual-layer.md)
- [Geometriyi Parametre Olarak Kullanan Tıklama Testi](how-to-hit-test-using-geometry-as-a-parameter.md)
