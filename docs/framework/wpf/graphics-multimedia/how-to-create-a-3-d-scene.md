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
ms.openlocfilehash: 8e176cb437055787da86d56770dd71323134fa33
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126236"
---
# <a name="how-to-create-a-3-d-scene"></a>Nasıl yapılır: 3B Görünümü Oluşturma
Bu örnek düz bir yaprak Döndürülmüş kağıt gibi görünen bir 3B nesnesinin nasıl oluşturulacağını gösterir. A <xref:System.Windows.Controls.Viewport3D> aşağıdaki bileşenlerin yanı sıra bu basit bir 3B görünümü oluşturmak için kullanılır:  
  
-   Bir kamera kullanılarak oluşturulan bir <xref:System.Windows.Media.Media3D.PerspectiveCamera>. Kamera, 3B Sahne hangi kısmının görüntülenebilir olduğunu belirtir.  
  
-   Bir 3B nesne (kağıdın) kullanma şekli belirtmek için oluşturulan <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> özelliği <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
-   Malzeme (Bu örnekte doğrusal gradyan) nesnesini kullanarak çalışma yüzeyinde görüntülenecek belirtilen <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> özelliği <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
-   Bir ışık kullanarak nesne üzerinde görünmek için oluşturulan <xref:System.Windows.Media.Media3D.DirectionalLight>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, XAML içinde 3B görünümü oluşturma işlemi gösterilmektedir.  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, yordam kodunda aynı 3B Sahne oluşturma işlemi gösterilmektedir.  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [3B Grafiklere Genel Bakış](3-d-graphics-overview.md)
