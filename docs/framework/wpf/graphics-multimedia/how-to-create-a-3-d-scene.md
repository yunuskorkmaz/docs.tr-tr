---
title: 'Nasıl yapılır: 3B Görünümü Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3-D
- 3-D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: e3c2ea803961ca57606f8ea8bec21d50a38dbe1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559532"
---
# <a name="how-to-create-a-3-d-scene"></a>Nasıl yapılır: 3B Görünümü Oluşturma
Bu örnek düz bir yaprak Döndürülmüş kağıt gibi görünen 3-b bir nesnesinin nasıl oluşturulacağını gösterir. A <xref:System.Windows.Controls.Viewport3D> aşağıdaki bileşenleri ile birlikte bu basit 3B görünümü oluşturmak için kullanılır:  
  
-   Kamera kullanılarak oluşturulan bir <xref:System.Windows.Media.Media3D.PerspectiveCamera>. Kamera 3B Sahne hangi kısmının görüntülenebilir olduğunu belirtir.  
  
-   Şekil 3-b nesnenin (yaprak kağıt) kullanarak belirtmek için bir kafes oluşturulur <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> özelliği <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
-   Bir malzeme nesnesi (Bu örnekte doğrusal gradyan) kullanılarak yüzey üzerinde görüntülenecek belirtilen <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> özelliği <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
-   Bir açık kullanarak nesne üzerinde görünmek için oluşturulan <xref:System.Windows.Media.Media3D.DirectionalLight>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kodu XAML'de 3B Sahne oluşturulacağını gösterir.  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kodu yordam kodda aynı 3B Sahne oluşturulacağını gösterir.  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [3B Grafiklere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
