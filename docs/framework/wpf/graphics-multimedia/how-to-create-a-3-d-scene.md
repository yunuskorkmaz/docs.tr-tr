---
title: Nasıl?
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3D
- 3D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: 36453894e06e7b59f339c21713449140c17f6851
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112108"
---
# <a name="how-to-create-a-3d-scene"></a>Nasıl?
Bu örnek, döndürülmüş düz bir kağıt sayfasına benzeyen bir 3B nesnenin nasıl oluşturulutamamını gösterir. Bu <xref:System.Windows.Controls.Viewport3D> basit 3B sahneyi oluşturmak için aşağıdaki bileşenlerle birlikte kullanılır:  
  
- Bir kamera kullanılarak <xref:System.Windows.Media.Media3D.PerspectiveCamera>oluşturulur. Kamera, 3B sahnenin hangi bölümünün görüntülenebilir olduğunu belirtir.  
  
- 3B nesnenin (kağıt sayfası) <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> şeklini belirtmek için bir kafes <xref:System.Windows.Media.Media3D.GeometryModel3D>oluşturulur.  
  
- Bir malzeme nesnenin yüzeyinde görüntülenecek belirtilir (bu örnekte doğrusal <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> degrade) özelliği <xref:System.Windows.Media.Media3D.GeometryModel3D>kullanılarak.  
  
- Bir ışık kullanarak <xref:System.Windows.Media.Media3D.DirectionalLight>nesne üzerinde parlamak için oluşturulur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, XAML'de nasıl bir 3B sahne oluşturulacak gösteriş gösterir.  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, yordam kodunda aynı 3B sahnenin nasıl oluşturuleceğini gösterir.  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [3D Grafiklere Genel Bakış](3-d-graphics-overview.md)
