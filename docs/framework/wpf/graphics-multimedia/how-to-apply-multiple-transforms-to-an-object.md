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
ms.openlocfilehash: 6d6c87443b26663da20b94835f1fd6c1fb926ae4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560550"
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a><span data-ttu-id="627cf-102">Nasıl yapılır: Nesneye Birden Çok Dönüşüm Uygulama</span><span class="sxs-lookup"><span data-stu-id="627cf-102">How to: Apply Multiple Transforms to an Object</span></span>
<span data-ttu-id="627cf-103">Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Media.TransformGroup> Grup iki veya daha fazla <xref:System.Windows.Media.Transform> nesneleri tek bileşik <xref:System.Windows.Media.Transform>.</span><span class="sxs-lookup"><span data-stu-id="627cf-103">This example shows how to use a <xref:System.Windows.Media.TransformGroup> to group two or more <xref:System.Windows.Media.Transform> objects into a single composite <xref:System.Windows.Media.Transform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="627cf-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="627cf-104">Example</span></span>  
 <span data-ttu-id="627cf-105">Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.TransformGroup> uygulamak için bir <xref:System.Windows.Media.ScaleTransform> ve <xref:System.Windows.Media.RotateTransform> için bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="627cf-105">The following example uses a <xref:System.Windows.Media.TransformGroup> to apply a <xref:System.Windows.Media.ScaleTransform> and a <xref:System.Windows.Media.RotateTransform> to a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="627cf-106">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="627cf-106">See Also</span></span>  
 <xref:System.Windows.UIElement.RenderTransform%2A>  
 <xref:System.Windows.Media.TransformGroup>  
 [<span data-ttu-id="627cf-107">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="627cf-107">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="627cf-108">2-D dönüşümler örnek</span><span class="sxs-lookup"><span data-stu-id="627cf-108">2-D Transforms Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=158252)
