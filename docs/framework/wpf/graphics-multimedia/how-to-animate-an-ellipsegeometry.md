---
title: "Nasıl yapılır: EllipseGeometry'ye Animasyon Ekleme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], EllipseGeometry objects [WPF]
- EllipseGeometry objects [WPF], animating
- graphics [WPF], animation
ms.assetid: 767b9b6e-9cb7-482e-b6c2-fee7750c3995
ms.openlocfilehash: 0f8174a2144435c9ad65904ee587355e8b38e935
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59126015"
---
# <a name="how-to-animate-an-ellipsegeometry"></a><span data-ttu-id="9f2b4-102">Nasıl yapılır: EllipseGeometry'ye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="9f2b4-102">How to: Animate an EllipseGeometry</span></span>
<span data-ttu-id="9f2b4-103">Bu örnek nasıl animasyon gösterir bir <xref:System.Windows.Media.Geometry> içinde bir <xref:System.Windows.Shapes.Path> öğesi.</span><span class="sxs-lookup"><span data-stu-id="9f2b4-103">This example shows how to animate a <xref:System.Windows.Media.Geometry> within a <xref:System.Windows.Shapes.Path> element.</span></span> <span data-ttu-id="9f2b4-104">Aşağıdaki örnekte, bir <xref:System.Windows.Media.Animation.PointAnimation> animasyon uygulamak için kullanılan <xref:System.Windows.Media.EllipseGeometry.Center%2A> , bir <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="9f2b4-104">In the following example, a <xref:System.Windows.Media.Animation.PointAnimation> is used to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> of an <xref:System.Windows.Media.EllipseGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f2b4-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f2b4-105">Example</span></span>  
 [!code-xaml[animatepath_snip_XAML#1](~/samples/snippets/csharp/VS_Snippets_Wpf/animatepath_snip_XAML/CS/EllipseGeometryExample.xaml#1)]  
  
 [!code-csharp[animatepath_snip#101](~/samples/snippets/csharp/VS_Snippets_Wpf/animatepath_snip/CSharp/EllipseGeometryExample.cs#101)]  
  
 [!code-vb[animatepath_snip#201](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animatepath_snip/VisualBasic/EllipseGeometryExample.vb#201)]  
  
## <a name="see-also"></a><span data-ttu-id="9f2b4-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f2b4-106">See also</span></span>

- [<span data-ttu-id="9f2b4-107">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="9f2b4-107">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="9f2b4-108">Geometriye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9f2b4-108">Geometry Overview</span></span>](geometry-overview.md)
