---
title: 'Nasıl yapılır: 3B Nesnenin Ön ve Arkasına Malzeme Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3-D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 1d3f6a0622b5e0ccccf14af99782bb78dfe87ccb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168057"
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3-d-object"></a>Nasıl yapılır: 3B Nesnenin Ön ve Arkasına Malzeme Uygulama
Aşağıdaki örnek nasıl uygulanacağını gösterir. bir <xref:System.Windows.Media.Media3D.Material> ön ve arkasına bir 3B nesne ve her iki tarafında bir nesneyi göstermek için nesneye animasyon uygulayın. <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> Özelliği bir <xref:System.Windows.Media.Media3D.GeometryModel3D> kırmızı uygulamak için kullanılan <xref:System.Windows.Media.Brush> nesne ön tarafındaki ve <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> özelliği <xref:System.Windows.Media.Media3D.GeometryModel3D> mavi uygulamak için kullanılan <xref:System.Windows.Media.Brush> nesnenin tarafı için. Aşağıdaki kod, nesneyi malzemeleri uygulamaya gösterir:  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, tüm örnek gösterir.  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [3B Görünümü Oluşturma](how-to-create-a-3-d-scene.md)
- [3B Grafiklere Genel Bakış](3-d-graphics-overview.md)
- [3B Görünümde Malzeme Özelliklerine Animasyon Ekleme](how-to-animate-material-properties-in-a-3-d-scene.md)
- [3B Nesnesine Yayımlatıcı Malzeme Uygulama](how-to-apply-emissive-material-to-a-3-d-object.md)
