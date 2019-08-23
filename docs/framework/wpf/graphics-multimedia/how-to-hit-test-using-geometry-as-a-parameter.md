---
title: 'Nasıl yapılır: Geometriyi Parametre Olarak Kullanan Tıklama Testi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
ms.openlocfilehash: 8bed7784b00f49178c9a87def74b62f7ce620ec7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923401"
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a>Nasıl yapılır: Geometriyi Parametre Olarak Kullanan Tıklama Testi
Bu örnek, bir isabet testi parametresi olarak kullanarak bir <xref:System.Windows.Media.Geometry> görsel nesnesi üzerinde bir isabet testinin nasıl gerçekleştirileceğini gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.Media.GeometryHitTestParameters> <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi için kullanarak bir isabet testinin nasıl ayarlanacağını gösterir. Yönteminegeçirilen`OnMouseDown`değer, isabet testinin aralığını genişletmek için bir <xref:System.Windows.Media.Geometry> nesne oluşturmak için kullanılır. <xref:System.Windows.Point>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 Özelliği, <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> bir isabet testi parametresi olarak kullanan bir <xref:System.Windows.Media.Geometry> isabet testinin sonuçlarıyla ilgili bilgiler sağlar.<xref:System.Windows.Media.GeometryHitTestResult> Aşağıdaki çizimde, hedef görsel nesnesinin (kırmızı kare) isabet testi geometrisi (mavi daire) ve işlenmiş içeriği arasındaki ilişki gösterilmektedir.  
  
 ![İsabet testinde kullanılan IntersectionDetail gösteren diyagram.](./media/how-to-hit-test-using-geometry-as-a-parameter/intersectiondetail-hit-test.png)  
  
 Aşağıdaki örnek, bir isabet testi parametresi olarak kullanıldığında bir <xref:System.Windows.Media.Geometry> isabet testi geri çağrısının nasıl uygulanacağını gösterir. Parametresi, özelliğin değerini almak için <xref:System.Windows.Media.GeometryHitTestResult> bir olarak öğesine dönüştürüldü. <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> `result` Özellik değeri, isabet sınama parametresinin, isabet testi <xref:System.Windows.Media.Geometry> hedefinin işlenmiş içeriği içinde tam mı yoksa kısmen mi olduğunu belirlemenizi sağlar. Bu durumda, örnek kod yalnızca hedef sınırın içinde tam olarak bulunan görsellerin listesine vuruş testi sonuçları ekler.  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
> Kesişim ayrıntısı olduğunda geri çağırma çağrılmamalıdır. <xref:System.Windows.Media.IntersectionDetail.Empty> <xref:System.Windows.Media.HitTestResult>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Katmanda Tıklama Testi](hit-testing-in-the-visual-layer.md)
- [Görselde Tıklama Testi Geometrisi](how-to-hit-test-geometry-in-a-visual.md)
