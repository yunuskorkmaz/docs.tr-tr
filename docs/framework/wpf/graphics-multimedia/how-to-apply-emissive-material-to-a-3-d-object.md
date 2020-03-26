---
title: 'Nasıl Yapılır: 3B Nesneye Emissive Malzeme Uygulayın'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- EmissiveMaterial [WPF], applying to 3D objects
- 3D objects [WPF], applying EmissiveMaterial
ms.assetid: fd442cc2-5adc-487a-ba70-e45ed54bb3b4
ms.openlocfilehash: bf32b41ec2410c01ad137ec0ca9311f7c2b70061
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112160"
---
# <a name="how-to-apply-emissive-material-to-a-3d-object"></a>Nasıl Yapılır: 3B Nesneye Emissive Malzeme Uygulayın
Aşağıdaki örnek, EmissiveMaterial fırçasının rengine eşit olan varolan bir Malzemeye renk eklemek için nasıl kullanılacağını <xref:System.Windows.Media.Media3D.EmissiveMaterial> gösterir. Aşağıdaki kod, <xref:System.Windows.Media.Media3D.DiffuseMaterial> <xref:System.Windows.Media.Media3D.EmissiveMaterial> DiffuseMaterial'ın görünümüne mavi eklemek için birlikte uygulanır.  
  
 [!code-xaml[3DGallery_snip#EmmisiveMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emmisivematerialanimationexampleinline1)]  
  
 Usul kodunda:  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexampleinline1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod XAML'deki tüm örneği gösterir.  
  
 [!code-xaml[3DGallery_snip#EmissiveMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emissivematerialexamplewholepage)]  
  
## <a name="example"></a>Örnek  
 Aşağıda usul kodunda tüm örnektir.  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [3B Sahne Oluşturma](how-to-create-a-3-d-scene.md)
- [3D Grafiklere Genel Bakış](3-d-graphics-overview.md)
- [3B Sahnede Malzeme Özelliklerini Canlandırma](how-to-animate-material-properties-in-a-3-d-scene.md)
- [3B Nesnenin Önüne ve Arkasına Malzeme Uygulayın](how-to-apply-material-to-the-front-and-back-of-a-3-d-object.md)
