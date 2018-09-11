---
title: 'Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (İşaret Etme Animasyonu)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
ms.openlocfilehash: d6dc79cd7a15aef2a4168fffb293c5e1f33cde08
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44259788"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a>Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (İşaret Etme Animasyonu)
Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.Animation.PointAnimationUsingPath> animasyon uygulamak için nesne bir <xref:System.Windows.Point> eğri yol.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek taşır bir <xref:System.Windows.Media.EllipseGeometry> tarafından tanımlanan yol bir <xref:System.Windows.Media.PathGeometry>. Elips geometrisinin <xref:System.Windows.Media.EllipseGeometry.Center%2A> alan, özelliği bir <xref:System.Windows.Point> animasyon olarak oluşturmak, elips geometrisini taşımak için; konumunu belirtir, değeri kendi <xref:System.Windows.Media.EllipseGeometry.Center%2A> özelliği. Örnekte bir <xref:System.Windows.Media.Animation.PointAnimationUsingPath> animasyon uygulamak için <xref:System.Windows.Media.EllipseGeometry> nesnenin <xref:System.Windows.Media.EllipseGeometry.Center%2A> özelliği.  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 Tam bir örnek için bkz. [yol animasyonu örneği](https://go.microsoft.com/fwlink/?LinkID=160028).  
  
 Önceki örnekte kullanılan kod sürümünü bir <xref:System.Windows.Media.Animation.Storyboard> animasyon uygulamak için <xref:System.Windows.Media.EllipseGeometry>, yalnızca bir animasyon uygulanmış olmasına rağmen. A <xref:System.Windows.Media.Animation.Storyboard> genellikle animasyonlarına aynı tarafından denetlenebilir olduğundan, birden çok animasyon uygulamak için en kolay yoludur <xref:System.Windows.Media.Animation.Storyboard>. Ancak, tek bir animasyonu kod kullanarak bir özelliğe uygulamak için daha kolay bir yolu kullanmaktır <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi. Bir örnek için bkz. [özelliği olmadan kullanarak bir görsel taslak animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yol animasyonu örneği](https://go.microsoft.com/fwlink/?LinkID=160028)  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Yol Animasyonu ile İlgili Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
