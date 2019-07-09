---
title: 'Nasıl yapılır: 3B Çevirilerine Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations
- 3-D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
ms.openlocfilehash: 6d7e0b422d6e76d5d0e25ad276550613f264e9bc
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661183"
---
# <a name="how-to-animate-3-d-translations"></a>Nasıl yapılır: 3B Çevirilerine Animasyon Ekleme
Bu konuda, bir 3B model üzerinde ayarlanmış bir çeviri dönüşümü animasyon gösterilmiştir.  
  
 Aşağıdaki kod, uygulamayı gösterir. bir <xref:System.Windows.Media.Media3D.TranslateTransform3D> nesnesini <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> özelliği bir <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> Bu özelliği <xref:System.Windows.Media.Media3D.TranslateTransform3D> nesne animasyon aşağıdaki kodu kullanarak.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, tüm örnek gösterir.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [3B Görünümü Oluşturma](how-to-create-a-3-d-scene.md)
- [3B Grafiklere Genel Bakış](3-d-graphics-overview.md)
- [Dönüşümlere Genel Bakış](transforms-overview.md)
