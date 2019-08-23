---
title: 'Nasıl yapılır: Özel Dönüşümler Oluşturmak için MatrixTransform Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: 1971d5fe9422c5138f140517e6fd4c9f9b2cf48b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913912"
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a><span data-ttu-id="db26a-102">Nasıl yapılır: Özel Dönüşümler Oluşturmak için MatrixTransform Kullanma</span><span class="sxs-lookup"><span data-stu-id="db26a-102">How to: Use a MatrixTransform to Create Custom Transforms</span></span>
<span data-ttu-id="db26a-103">Bu örnek, bir <xref:System.Windows.Media.MatrixTransform> <xref:System.Windows.Controls.Button>öğesinin konumunu, uzatılmasına ve eğriliğini çevirmek (taşımak) için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="db26a-103">This example shows how to use a <xref:System.Windows.Media.MatrixTransform> to translate (move) the position, stretch, and skew of a <xref:System.Windows.Controls.Button>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db26a-104"><xref:System.Windows.Media.RotateTransform> ,,<xref:System.Windows.Media.SkewTransform>Veya sınıfları<xref:System.Windows.Media.TranslateTransform> tarafından sağlanmayan<xref:System.Windows.Media.ScaleTransform>özel dönüştürmeler oluşturmak için sınıfını kullanın. <xref:System.Windows.Media.MatrixTransform></span><span class="sxs-lookup"><span data-stu-id="db26a-104">Use the <xref:System.Windows.Media.MatrixTransform> class to create custom transformations that are not provided by the <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, or <xref:System.Windows.Media.TranslateTransform> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db26a-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="db26a-105">Example</span></span>  
 [!code-xaml[Transforms_snip#MatrixTransform](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a><span data-ttu-id="db26a-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db26a-106">See also</span></span>

- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="db26a-107">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="db26a-107">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="db26a-108">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="db26a-108">How-to Topics</span></span>](transformations-how-to-topics.md)
- [<span data-ttu-id="db26a-109">WPF’de Şekiller ve Temel Çizimlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="db26a-109">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
