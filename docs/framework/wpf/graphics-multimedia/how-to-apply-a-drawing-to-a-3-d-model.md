---
title: 'Nasıl yapılır: 3B Modeline Çizim Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 311a3ac1d9fa219a3a365d506d9d0c3e8b6bc229
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459374"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>Nasıl yapılır: 3B Modeline Çizim Uygulama

Bu örnek, bir <xref:System.Windows.Media.DrawingBrush> bir 3-b modele uygulanan <xref:System.Windows.Media.Media3D.Material> olarak nasıl kullanılacağını gösterir.

Aşağıdaki kod, bir <xref:System.Windows.Media.DrawingBrush>içeriği olarak bir <xref:System.Windows.Media.DrawingGroup> tanımlar.  <xref:System.Windows.Media.DrawingBrush>, 3-b düzlemine uygulanan <xref:System.Windows.Media.Media3D.DiffuseMaterial> <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> özelliği olarak ayarlanır.

> [!NOTE]
> Daha önce yeniden kullanılabilen ve kodunuzu basitleştirecek kaynaklar olarak aşağıdaki çizimde gösterildiği gibi karmaşık nesne ve değerleri tanımlamak genellikle tercih edilir. Daha fazla bilgi için bkz. [xaml kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md) .

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a>Örnek

Aşağıdaki kod, tüm örneği gösterir.

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a>Ayrıca bkz.

- [XAML Kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [3B Görünümü Oluşturma](how-to-create-a-3-d-scene.md)
- [Çizim Nesnelerine Genel Bakış](drawing-objects-overview.md)
- [3B Grafiklere Genel Bakış](3-d-graphics-overview.md)
