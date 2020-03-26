---
title: Nasıl? 3B Modelin Ölçeğini Dönüştürün
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3D objects
- 3D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: be41a0e10929912c1b54bf7140d743d9453199bf
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111991"
---
# <a name="how-to-transform-the-scale-of-a-3d-model"></a>Nasıl? 3B Modelin Ölçeğini Dönüştürün
Bu örnek, 3B nesnenin nasıl ölçeklendirilebildiğini gösterir. Bir 3B nesneyi ölçeklendirmek için bir <xref:System.Windows.Media.Media3D.ScaleTransform3D>. <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> ve özellikleri belirttiğiniz faktöre göre öğeyi yeniden boyutlandırmak. Örneğin, 1,5 <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> değeri bir nesneyi özgün genişliğinin yüzde 150'sine kadar uzatür. 0,5 <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> değeri bir nesnenin yüksekliğini yüzde 50 küçültür. Aşağıdaki kod, bir <xref:System.Windows.Media.Media3D.ScaleTransform3D> <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, tüm örneği gösterir.  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyon 3D Çeviriler](how-to-animate-3-d-translations.md)
- [3B Sahne Oluşturma](how-to-create-a-3-d-scene.md)
- [3D Grafiklere Genel Bakış](3-d-graphics-overview.md)
