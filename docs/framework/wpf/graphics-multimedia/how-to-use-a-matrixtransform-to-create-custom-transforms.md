---
title: 'Nasıl yapılır: Özel Dönüşümler Oluşturmak için MatrixTransform Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: 3b5a6fbedd30c859dffadad00c8faab74fc0773b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628805"
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a><span data-ttu-id="be975-102">Nasıl yapılır: Özel Dönüşümler Oluşturmak için MatrixTransform Kullanma</span><span class="sxs-lookup"><span data-stu-id="be975-102">How to: Use a MatrixTransform to Create Custom Transforms</span></span>
<span data-ttu-id="be975-103">Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.MatrixTransform> (taşıma) çevirmek için konum esnetme ve, eğme bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="be975-103">This example shows how to use a <xref:System.Windows.Media.MatrixTransform> to translate (move) the position, stretch, and skew of a <xref:System.Windows.Controls.Button>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be975-104">Kullanım <xref:System.Windows.Media.MatrixTransform> tarafından sağlanmayan özel dönüşümler oluşturmak için sınıf <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, veya <xref:System.Windows.Media.TranslateTransform> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="be975-104">Use the <xref:System.Windows.Media.MatrixTransform> class to create custom transformations that are not provided by the <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, or <xref:System.Windows.Media.TranslateTransform> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be975-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="be975-105">Example</span></span>  
 [!code-xaml[Transforms_snip#MatrixTransform](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a><span data-ttu-id="be975-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be975-106">See also</span></span>
- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="be975-107">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="be975-107">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
- [<span data-ttu-id="be975-108">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="be975-108">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
- [<span data-ttu-id="be975-109">WPF’de Şekiller ve Temel Çizimlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="be975-109">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
