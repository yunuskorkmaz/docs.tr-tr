---
title: 'Nasıl Yapılır: Malzemeyi 3B Nesnenin Önüne ve Arkasına Uygulayın'
ms.date: 03/30/2017
helpviewer_keywords:
- 3D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 5c24879d97e7857fb07fcef4a9ba8efa901e4a39
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112147"
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3d-object"></a>Nasıl Yapılır: Malzemeyi 3B Nesnenin Önüne ve Arkasına Uygulayın
Aşağıdaki örnek, bir 3B nesnenin önüne ve arkasına nasıl uygulanacağı <xref:System.Windows.Media.Media3D.Material> ve nesnenin her iki tarafını da göstermek için nesneyi nasıl canlandıracağı gösterilmektedir. A <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> <xref:System.Windows.Media.Media3D.GeometryModel3D> özelliği <xref:System.Windows.Media.Brush> nesnenin ön tarafına kırmızı uygulamak için kullanılır <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> ve <xref:System.Windows.Media.Media3D.GeometryModel3D> özelliği nesnenin arka <xref:System.Windows.Media.Brush> tarafına mavi uygulamak için kullanılır. Aşağıdaki kod, nesnelerin nesneye uygulanmasını gösterir:  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, tüm örneği gösterir.  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [3B Sahne Oluşturma](how-to-create-a-3-d-scene.md)
- [3D Grafiklere Genel Bakış](3-d-graphics-overview.md)
- [3B Sahnede Malzeme Özelliklerini Canlandırma](how-to-animate-material-properties-in-a-3-d-scene.md)
- [3B Nesneye Emissive Malzeme Uygulayın](how-to-apply-emissive-material-to-a-3-d-object.md)
