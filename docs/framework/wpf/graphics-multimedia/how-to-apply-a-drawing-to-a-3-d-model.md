---
title: 'Nasıl yapılır: 3B Modeline Çizim Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: a20b89a7359fc85d9790ac02dd2b173452df8c22
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699116"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>Nasıl yapılır: 3B Modeline Çizim Uygulama
Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.DrawingBrush> olarak <xref:System.Windows.Media.Media3D.Material> uygulanan bir [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modeli.  
  
 Aşağıdaki kodu tanımlayan bir <xref:System.Windows.Media.DrawingGroup> içeriği olarak bir <xref:System.Windows.Media.DrawingBrush>.  <xref:System.Windows.Media.DrawingBrush> Olarak ayarlandığından <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> özelliği <xref:System.Windows.Media.Media3D.DiffuseMaterial> uygulanan bir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] düzlemi.  
  
 **Not:** Genellikle karmaşık nesneler ve değerleri gibi aşağıdaki çizim, kodunuzu basitleştirerek ve yeniden kullanılabilir kaynaklar olarak tanımlamak için tercih edilir. Bkz: [XAML kaynakları](../advanced/xaml-resources.md) daha fazla bilgi için.  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, tüm örnek gösterir.  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML Kaynakları](../advanced/xaml-resources.md)
- [3B Görünümü Oluşturma](how-to-create-a-3-d-scene.md)
- [Çizim Nesnelerine Genel Bakış](drawing-objects-overview.md)
- [3B Grafiklere Genel Bakış](3-d-graphics-overview.md)
