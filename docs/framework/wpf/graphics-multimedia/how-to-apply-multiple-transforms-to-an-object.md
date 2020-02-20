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
# <a name="how-to-apply-multiple-transforms-to-an-object"></a><span data-ttu-id="4cc22-102">Nasıl yapılır: Nesneye Birden Çok Dönüşüm Uygulama</span><span class="sxs-lookup"><span data-stu-id="4cc22-102">How to: Apply Multiple Transforms to an Object</span></span>
<span data-ttu-id="4cc22-103">Bu örnek, iki veya daha fazla <xref:System.Windows.Media.Transform> nesnesini tek bir bileşik <xref:System.Windows.Media.Transform>içinde gruplamak için bir <xref:System.Windows.Media.TransformGroup> nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="4cc22-103">This example shows how to use a <xref:System.Windows.Media.TransformGroup> to group two or more <xref:System.Windows.Media.Transform> objects into a single composite <xref:System.Windows.Media.Transform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cc22-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="4cc22-104">Example</span></span>  
 <span data-ttu-id="4cc22-105">Aşağıdaki örnek, bir <xref:System.Windows.Controls.Button><xref:System.Windows.Media.ScaleTransform> ve <xref:System.Windows.Media.RotateTransform> uygulamak için bir <xref:System.Windows.Media.TransformGroup> kullanır.</span><span class="sxs-lookup"><span data-stu-id="4cc22-105">The following example uses a <xref:System.Windows.Media.TransformGroup> to apply a <xref:System.Windows.Media.ScaleTransform> and a <xref:System.Windows.Media.RotateTransform> to a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="4cc22-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cc22-106">See also</span></span>

- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Media.TransformGroup>
- [<span data-ttu-id="4cc22-107">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4cc22-107">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="4cc22-108">2-b dönüşümler örneği</span><span class="sxs-lookup"><span data-stu-id="4cc22-108">2-D Transforms Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
