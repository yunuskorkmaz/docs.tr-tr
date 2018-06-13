---
title: 'Nasıl yapılır: Özel Dönüşümler Oluşturmak için MatrixTransform Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: 4ffbefea498e9a2bdc5546d112f6ff10e12fed67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561166"
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a><span data-ttu-id="0cf1e-102">Nasıl yapılır: Özel Dönüşümler Oluşturmak için MatrixTransform Kullanma</span><span class="sxs-lookup"><span data-stu-id="0cf1e-102">How to: Use a MatrixTransform to Create Custom Transforms</span></span>
<span data-ttu-id="0cf1e-103">Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Media.MatrixTransform> (Taşı) çevirmek için konum uzatma ve, eğme bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="0cf1e-103">This example shows how to use a <xref:System.Windows.Media.MatrixTransform> to translate (move) the position, stretch, and skew of a <xref:System.Windows.Controls.Button>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0cf1e-104">Kullanım <xref:System.Windows.Media.MatrixTransform> tarafından sağlanmayan özel dönüşümleri oluşturmak için sınıfı <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, veya <xref:System.Windows.Media.TranslateTransform> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="0cf1e-104">Use the <xref:System.Windows.Media.MatrixTransform> class to create custom transformations that are not provided by the <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, or <xref:System.Windows.Media.TranslateTransform> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cf1e-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="0cf1e-105">Example</span></span>  
 [!code-xaml[Transforms_snip#MatrixTransform](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a><span data-ttu-id="0cf1e-106">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0cf1e-106">See Also</span></span>  
 <xref:System.Windows.Media.MatrixTransform>  
 <xref:System.Windows.Media.Transform>  
 [<span data-ttu-id="0cf1e-107">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0cf1e-107">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="0cf1e-108">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="0cf1e-108">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [<span data-ttu-id="0cf1e-109">WPF’de Şekiller ve Temel Çizimlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0cf1e-109">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
