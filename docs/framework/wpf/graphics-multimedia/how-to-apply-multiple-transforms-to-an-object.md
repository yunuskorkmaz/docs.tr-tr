---
title: 'Nasıl yapılır: Nesneye Birden Çok Dönüşüm Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- grouping Transform objects [WPF]
- Transform objects [WPF], grouping
- graphics [WPF], grouping Transform objects
- TransformGroup [WPF]
ms.assetid: 98cd1921-12bc-4bf5-8193-529228fb7402
ms.openlocfilehash: 0700a7ae3f18f745b0d479ace3acbf2d7fbd9722
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402970"
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a>Nasıl yapılır: Nesneye Birden Çok Dönüşüm Uygulama
Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.TransformGroup> iki veya daha fazla gruba <xref:System.Windows.Media.Transform> tek bileşik nesneler <xref:System.Windows.Media.Transform>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.TransformGroup> uygulamak için bir <xref:System.Windows.Media.ScaleTransform> ve <xref:System.Windows.Media.RotateTransform> için bir <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.UIElement.RenderTransform%2A>  
 <xref:System.Windows.Media.TransformGroup>  
 [Dönüşümlere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [2B dönüşümleri örneği](https://go.microsoft.com/fwlink/?LinkID=158252)
