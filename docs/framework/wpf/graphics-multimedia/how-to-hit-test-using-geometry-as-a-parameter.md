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
ms.openlocfilehash: 3d6f4190a5b5c8410a6be01d2645df9c123f9ac4
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410621"
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a>Nasıl yapılır: Geometriyi Parametre Olarak Kullanan Tıklama Testi
Bu örnek gösterir kullanarak visual nesne üzerinde bir isabet testi gerçekleştirmek nasıl bir <xref:System.Windows.Media.Geometry> parametre isabet testi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir isabet sınaması kullanılarak ayarlanan gösterilmiştir <xref:System.Windows.Media.GeometryHitTestParameters> için <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi. <xref:System.Windows.Point> Geçirilen değer `OnMouseDown` yöntemi oluşturmak için kullanılan bir <xref:System.Windows.Media.Geometry> isabet sınaması aralığını genişletmek için nesne.  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> Özelliği <xref:System.Windows.Media.GeometryHitTestResult> kullanan isabet sınaması sonuçlarıyla ilgili bilgi sağlar bir <xref:System.Windows.Media.Geometry> parametre isabet testi. İsabet testi geometrisi (mavi daire) ve işlenmiş içeriği hedef visual nesnenin (kırmızı kare) arasındaki ilişki aşağıda gösterilmiştir.  
  
 ![İsabet sınaması kullanılan IntersectionDetail gösteren diyagram.](./media/how-to-hit-test-using-geometry-as-a-parameter/intersectiondetail-hit-test.png)  
  
 Aşağıdaki örnek, bir isabet sınaması geri çağırmanızı uygulamak gösterilmektedir, bir <xref:System.Windows.Media.Geometry> isabet sınaması parametre olarak kullanılır. `result` Parametre türünden bir <xref:System.Windows.Media.GeometryHitTestResult> değerini almak için <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> özelliği. Özellik değeri, belirlemenize olanak tanır <xref:System.Windows.Media.Geometry> isabet sınaması parametresi tamamen veya kısmen yer alan isabet sınaması hedef işlenmiş içeriği içinde. Bu durumda, örnek kod için tam olarak hedef sınırları içinde bulunan görselleri listesine yalnızca isabet testi sonuçlarını eklemektir.  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
>  <xref:System.Windows.Media.HitTestResult> Kesişimi ayrıntı olduğunda geri çağırma çağırılmalıdır <xref:System.Windows.Media.IntersectionDetail.Empty>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Görsel Katmanda Tıklama Testi](hit-testing-in-the-visual-layer.md)
- [Görselde Tıklama Testi Geometrisi](how-to-hit-test-geometry-in-a-visual.md)
