---
title: 'Nasıl yapılır: 3B Nesnesine Yayımlatıcı Malzeme Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- EmissiveMaterial [WPF], applying to 3-D objects
- 3-D objects [WPF], applying EmissiveMaterial
ms.assetid: fd442cc2-5adc-487a-ba70-e45ed54bb3b4
ms.openlocfilehash: da2c8c5d488afd02b50cfeee70048e6fa619248c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559436"
---
# <a name="how-to-apply-emissive-material-to-a-3-d-object"></a>Nasıl yapılır: 3B Nesnesine Yayımlatıcı Malzeme Uygulama
Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.Media.Media3D.EmissiveMaterial> varolan bir malzemeye EmissiveMaterial'ın fırça rengi ile eşit renk eklemek için. Aşağıdaki kodu gösterir <xref:System.Windows.Media.Media3D.DiffuseMaterial> ve <xref:System.Windows.Media.Media3D.EmissiveMaterial> mavi DiffuseMaterial'ın eklemek için bir arada uygulanır.  
  
 [!code-xaml[3DGallery_snip#EmmisiveMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emmisivematerialanimationexampleinline1)]  
  
 Yordam kod:  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexampleinline1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod tüm örnek XAML'de gösterir.  
  
 [!code-xaml[3DGallery_snip#EmissiveMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emissivematerialexamplewholepage)]  
  
## <a name="example"></a>Örnek  
 Tüm örnek yordam kodda aşağıdadır.  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [3B Görünümü Oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [3B Grafiklere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [3B Görünümde Malzeme Özelliklerine Animasyon Ekleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)  
 [3B Nesnenin Ön ve Arkasına Malzeme Uygulama](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-material-to-the-front-and-back-of-a-3-d-object.md)
