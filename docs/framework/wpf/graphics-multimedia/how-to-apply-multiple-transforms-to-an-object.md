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
ms.openlocfilehash: 544d0a26f24e5ad4ed7e2e3cfa25f8e15d1be446
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452837"
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a>Nasıl yapılır: Nesneye Birden Çok Dönüşüm Uygulama
Bu örnek, iki veya daha fazla <xref:System.Windows.Media.Transform> nesnesini tek bir bileşik <xref:System.Windows.Media.Transform>içinde gruplamak için bir <xref:System.Windows.Media.TransformGroup> nasıl kullanacağınızı gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir <xref:System.Windows.Controls.Button><xref:System.Windows.Media.ScaleTransform> ve <xref:System.Windows.Media.RotateTransform> uygulamak için bir <xref:System.Windows.Media.TransformGroup> kullanır.  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Media.TransformGroup>
- [Dönüşümlere Genel Bakış](transforms-overview.md)
- [2-b dönüşümler örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
