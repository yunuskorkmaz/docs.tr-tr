---
title: 'Nasıl Yapılır: Çizimi 3B Modele Uygula'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3D models
- 3D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 5b10630ab674fa9489cdf7ad53516a680f19da08
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112186"
---
# <a name="how-to-apply-a-drawing-to-a-3d-model"></a>Nasıl Yapılır: Çizimi 3B Modele Uygula

Bu örnek, bir <xref:System.Windows.Media.DrawingBrush> 3B <xref:System.Windows.Media.Media3D.Material> modele uygulandığı şeklin nasıl kullanılacağını gösterir.

Aşağıdaki kod bir <xref:System.Windows.Media.DrawingGroup> . <xref:System.Windows.Media.DrawingBrush>  3B <xref:System.Windows.Media.DrawingBrush> düzleme <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> <xref:System.Windows.Media.Media3D.DiffuseMaterial> uygulanan özelliği olarak ayarlanır.

> [!NOTE]
> Genellikle, aşağıdaki çizim gibi karmaşık nesneleri ve değerleri yeniden kullanılabilecek ve kodunuzu basitleştirebilecek kaynaklar olarak tanımlamak istenir. Daha fazla bilgi için [XAML Kaynakları'na](../../../desktop-wpf/fundamentals/xaml-resources-define.md) bakın.

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a>Örnek

Aşağıdaki kod, tüm örneği gösterir.

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a>Ayrıca bkz.

- [XAML Kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [3B Sahne Oluşturma](how-to-create-a-3-d-scene.md)
- [Çizim Nesnelerine Genel Bakış](drawing-objects-overview.md)
- [3D Grafiklere Genel Bakış](3-d-graphics-overview.md)
