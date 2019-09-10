---
title: 'Nasıl yapılır: 3B Modeline Çizim Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 14470d0adeb948ea46a0720b5713c20fb7d8e6d8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855873"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>Nasıl yapılır: 3B Modeline Çizim Uygulama

Bu örnek, <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.Media3D.Material> bir 3-b model için uygulanan olarak nasıl kullanılacağını gösterir.

Aşağıdaki kod, bir <xref:System.Windows.Media.DrawingGroup> <xref:System.Windows.Media.DrawingBrush>öğesinin içeriği olarak bir tanımlar.  , <xref:System.Windows.Media.DrawingBrush> 3-b düzlemi <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> için <xref:System.Windows.Media.Media3D.DiffuseMaterial> uygulanan özelliği olarak ayarlanır.

> [!NOTE]
> Daha önce yeniden kullanılabilen ve kodunuzu basitleştirecek kaynaklar olarak aşağıdaki çizimde gösterildiği gibi karmaşık nesne ve değerleri tanımlamak genellikle tercih edilir. Daha fazla bilgi için bkz. [xaml kaynakları](../advanced/xaml-resources.md) .

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a>Örnek

Aşağıdaki kod, tüm örneği gösterir.

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a>Ayrıca bkz.

- [XAML Kaynakları](../advanced/xaml-resources.md)
- [3B Görünümü Oluşturma](how-to-create-a-3-d-scene.md)
- [Çizim Nesnelerine Genel Bakış](drawing-objects-overview.md)
- [3B Grafiklere Genel Bakış](3-d-graphics-overview.md)
