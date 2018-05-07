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
ms.openlocfilehash: 57b04f7f8c9bcc21f6b970c2981c2bab51044c10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a>Nasıl yapılır: Geometriyi Parametre Olarak Kullanan Tıklama Testi
Bu örnek kullanarak visual nesne üzerinde isabet testi gerçekleştirmek nasıl gösterir bir <xref:System.Windows.Media.Geometry> parametresi isabet testi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir isabet testi kullanılarak ayarlanan gösterilmektedir <xref:System.Windows.Media.GeometryHitTestParameters> için <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi. <xref:System.Windows.Point> İçin geçirilen değer `OnMouseDown` yöntemi oluşturmak için kullanılan bir <xref:System.Windows.Media.Geometry> isabet testi aralığını genişletmek için nesne.  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> Özelliği <xref:System.Windows.Media.GeometryHitTestResult> kullanan bir isabet testi sonuçlarını hakkında bilgi sağlar bir <xref:System.Windows.Media.Geometry> parametresi isabet testi. Aşağıdaki çizimde isabet testi geometrisi (mavi daire) ve hedef görsel nesne (kırmızı kare) işlenmiş içeriği arasındaki ilişkiyi gösterir.  
  
 ![Tıklatma testinde kullanılan IntersectionDetail diyagramı isabet testi](../../../../docs/framework/wpf/graphics-multimedia/media/intersectiondetail01.png "IntersectionDetail01")  
İsabet testi geometrisi ve hedef görsel nesnesinin kesişimi  
  
 Aşağıdaki örnek, bir isabet testi geri uygulamak gösterilmektedir, bir <xref:System.Windows.Media.Geometry> isabet testi parametre olarak kullanılır. `result` Parametresi atandığında bir <xref:System.Windows.Media.GeometryHitTestResult> değerini almak için <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> özelliği. Özellik değeri, belirlemenize olanak tanır <xref:System.Windows.Media.Geometry> isabet testi parametresi tamamen veya kısmen barındırılan hedef isabet testinin işlenmiş içeriği içinde. Bu durumda, örnek kod için tam olarak hedef sınırı içinde bulunan görselleri listesine yalnızca isabet testi sonuçları eklemektir.  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
>  <xref:System.Windows.Media.HitTestResult> Geri çağırma çağrılmamalı kesişim ayrıntı olduğunda <xref:System.Windows.Media.IntersectionDetail.Empty>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görsel Katmanda Tıklama Testi](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [Görselde Tıklama Testi Geometrisi](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-geometry-in-a-visual.md)
