---
title: "Nasıl yapılır: 3B Nesnenin Ön ve Arkasına Malzeme Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 3-D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3-D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ce4605208be264418088399253298798205c3f9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3-d-object"></a>Nasıl yapılır: 3B Nesnenin Ön ve Arkasına Malzeme Uygulama
Aşağıdaki örnekte nasıl uygulanacağını gösterir bir <xref:System.Windows.Media.Media3D.Material> önüne ve 3-b arkasına nesnesi ve her iki tarafında nesne göstermek için nesnenin animasyon. <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> Özelliği bir <xref:System.Windows.Media.Media3D.GeometryModel3D> kırmızı uygulamak için kullanılan <xref:System.Windows.Media.Brush> nesne ön tarafına ve <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> özelliği <xref:System.Windows.Media.Media3D.GeometryModel3D> mavi uygulamak için kullanılan <xref:System.Windows.Media.Brush> nesnenin arka tarafına. Aşağıdaki kod, nesne malzemeleri uygulamaya gösterir:  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod tüm örneği gösterir.  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [3B Sahne oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [3B Grafiklere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [3B Sahne içinde Malzeme özelliklerine animasyon ekleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)  
 [3B nesnesine Yayıcı malzeme Uygula](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-emissive-material-to-a-3-d-object.md)
