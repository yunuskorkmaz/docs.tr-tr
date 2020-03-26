---
title: 'Nasıl yapilir: 3B Sahnede Malzeme Özelliklerini Animasyona'
ms.date: 03/30/2017
helpviewer_keywords:
- Material properties [WPF], animating in 3D scenes
- animation [WPF], Material properties in 3D scenes
- 3D scenes [WPF], animating Material properties
ms.assetid: 229fd6eb-7401-4992-b0c9-8b28de230c0f
ms.openlocfilehash: db59debcd7558cde52d8604cb04c8c4e68921825
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112199"
---
# <a name="how-to-animate-material-properties-in-a-3d-scene"></a>Nasıl yapilir: 3B Sahnede Malzeme Özelliklerini Animasyona
Bu örnek, <xref:System.Windows.Media.Brush.Opacity%2A> <xref:System.Windows.Media.Media3D.Material> uygulanan bir 3B modele uygulanan özelliğin nasıl canlandırılabildiğini gösterir.  
  
 Aşağıdaki kod örneği 3B nesneye <xref:System.Windows.Media.LinearGradientBrush> <xref:System.Windows.Media.Media3D.Material> uygulanan olarak kullanılır tanımlar.  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline1)]  
  
 Bunun <xref:System.Windows.Media.Brush.Opacity%2A> <xref:System.Windows.Media.LinearGradientBrush> özelliği aşağıdaki kod örneği kullanılarak animasyonludur.  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline2)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, tüm örneği gösterir.  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [3B Sahne Oluşturma](how-to-create-a-3-d-scene.md)
- [3D Grafiklere Genel Bakış](3-d-graphics-overview.md)
