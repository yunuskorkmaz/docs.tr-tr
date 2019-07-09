---
title: 'Nasıl yapılır: 3B Modeline Çizim Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 8ac24fdf8d7e407e10764c17fcc12121aa5f51d7
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662805"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>Nasıl yapılır: 3B Modeline Çizim Uygulama
Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.DrawingBrush> olarak <xref:System.Windows.Media.Media3D.Material> 3B modeline uygulanır.  
  
 Aşağıdaki kodu tanımlayan bir <xref:System.Windows.Media.DrawingGroup> içeriği olarak bir <xref:System.Windows.Media.DrawingBrush>.  <xref:System.Windows.Media.DrawingBrush> Olarak ayarlandığından <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> özelliği <xref:System.Windows.Media.Media3D.DiffuseMaterial> 3B düzlem için uygulanır.  
  
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
