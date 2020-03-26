---
title: 'Nasıl yapilir: 3D Çevirileri Animate'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3D translations
- 3D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
ms.openlocfilehash: 7d4fff9c74663bd220ad5d15a983bcb639621afd
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112264"
---
# <a name="how-to-animate-3d-translations"></a>Nasıl yapilir: 3D Çevirileri Animate
Bu konu, 3B modelüzerinde ayarlanmış bir çeviri dönüşümüne nasıl animasyon yapılacağını gösterir.  
  
 Aşağıdaki kod, bir <xref:System.Windows.Media.Media3D.TranslateTransform3D> nesnenin bir <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> <xref:System.Windows.Media.Media3D.GeometryModel3D>. özelliğine uygulanmasını gösterir  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 Bu <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> <xref:System.Windows.Media.Media3D.TranslateTransform3D> nesnenin özelliği aşağıdaki kod kullanılarak animasyonludur.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, tüm örneği gösterir.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [3B Sahne Oluşturma](how-to-create-a-3-d-scene.md)
- [3D Grafiklere Genel Bakış](3-d-graphics-overview.md)
- [Dönüşümlere Genel Bakış](transforms-overview.md)
