---
title: 'Nasıl yapılır: Özel Dönüşümler Oluşturmak için MatrixTransform Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: 179c7986b6a7021f4e1245aef01eb555108ebf4f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358866"
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a><span data-ttu-id="28f71-102">Nasıl yapılır: Özel Dönüşümler Oluşturmak için MatrixTransform Kullanma</span><span class="sxs-lookup"><span data-stu-id="28f71-102">How to: Use a MatrixTransform to Create Custom Transforms</span></span>
<span data-ttu-id="28f71-103">Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.MatrixTransform> (taşıma) çevirmek için konum esnetme ve, eğme bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="28f71-103">This example shows how to use a <xref:System.Windows.Media.MatrixTransform> to translate (move) the position, stretch, and skew of a <xref:System.Windows.Controls.Button>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28f71-104">Kullanım <xref:System.Windows.Media.MatrixTransform> tarafından sağlanmayan özel dönüşümler oluşturmak için sınıf <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, veya <xref:System.Windows.Media.TranslateTransform> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="28f71-104">Use the <xref:System.Windows.Media.MatrixTransform> class to create custom transformations that are not provided by the <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, or <xref:System.Windows.Media.TranslateTransform> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28f71-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="28f71-105">Example</span></span>  
 [!code-xaml[Transforms_snip#MatrixTransform](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a><span data-ttu-id="28f71-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28f71-106">See also</span></span>
- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="28f71-107">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="28f71-107">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="28f71-108">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="28f71-108">How-to Topics</span></span>](transformations-how-to-topics.md)
- [<span data-ttu-id="28f71-109">WPF’de Şekiller ve Temel Çizimlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="28f71-109">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
