---
title: 'Nasıl yapılır: 3B Nesnenin Ön ve Arkasına Malzeme Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3-D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 0ccf0aa045886f0731cd22ecdc8e14fa6af55fd2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559740"
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3-d-object"></a>Nasıl yapılır: 3B Nesnenin Ön ve Arkasına Malzeme Uygulama
Aşağıdaki örnekte nasıl uygulanacağını gösterir bir <xref:System.Windows.Media.Media3D.Material> önüne ve 3-b arkasına nesnesi ve her iki tarafında nesne göstermek için nesnenin animasyon. <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> Özelliği bir <xref:System.Windows.Media.Media3D.GeometryModel3D> kırmızı uygulamak için kullanılan <xref:System.Windows.Media.Brush> nesne ön tarafına ve <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> özelliği <xref:System.Windows.Media.Media3D.GeometryModel3D> mavi uygulamak için kullanılan <xref:System.Windows.Media.Brush> nesnenin arka tarafına. Aşağıdaki kod, nesne malzemeleri uygulamaya gösterir:  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod tüm örneği gösterir.  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [3B Görünümü Oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [3B Grafiklere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [3B Görünümde Malzeme Özelliklerine Animasyon Ekleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)  
 [3B Nesnesine Yayımlatıcı Malzeme Uygulama](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-emissive-material-to-a-3-d-object.md)
