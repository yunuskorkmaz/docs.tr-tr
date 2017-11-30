---
title: "Nasıl yapılır: 3B Modeline Çizim Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a44607498c6870a598122f41bf2b7ddc5968c61d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>Nasıl yapılır: 3B Modeline Çizim Uygulama
Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Media.DrawingBrush> olarak <xref:System.Windows.Media.Media3D.Material> uygulanan bir [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modeli.  
  
 Aşağıdaki kodu tanımlayan bir <xref:System.Windows.Media.DrawingGroup> içeriği olarak bir <xref:System.Windows.Media.DrawingBrush>.  <xref:System.Windows.Media.DrawingBrush> Olarak ayarlanmış olan <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> özelliği <xref:System.Windows.Media.Media3D.DiffuseMaterial> uygulanan bir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] düzlemi.  
  
 **Not:** genellikle karmaşık nesneler ve değerleri aşağıdaki çizim gibi yeniden kullanılabilir ve kodunuzu basitleştiren kaynaklar olarak tanımlamak için tercih edilir. Bkz: [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md) daha fazla bilgi için.  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod tüm örneği gösterir.  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [3B Sahne oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [Çizim nesnelerine genel bakış](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [3B Grafiklere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
